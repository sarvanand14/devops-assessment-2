# Devops-assessment


 1.Deploy postgres as statefulset in kubernetes

  Created the postgres statefulset using helm from scratch
  the postgres-statefulset files are defined in the postgres-statefulset directory
  installed the postgres-statefulset using the below command 

    - helm upgrade --install postgres postgres-statefulset -n default

##


2. Deploy Postgresexporter to export postgres metrics to prometheus for monitoring it

   Have added the postgres-exporter details in the prometheus-postgres-exporter directory after adding the details deployed the postgres-exporter using the below command

       helm upgrade --install postgres-exporter prometheus-postgres-exporter -n default


3. Deploy prometheus and expose it to external users so that we can run promql for monitoring prometheus

   Deployed prometheus by adding the image name and no of replicas in the values.yaml file of the prometheus directory 
after adding the details deploy the prometheus using the below command
  
        helm upgrade --install prometheus prometheus -n default


After deploying all the components i.e the postgres-statefulset, postgres-exporter and prometheus 
we can check if the postgres metrics is present in the prometheus promql for monitoring 

To do the above step i have first port-forwarded the prometheus service using the below command 

        kubectl port-forward svc/prometheus 9090:9090

#

After port-forwarding the prometheus serivce we can check in browser using localhost:9090/ and in the targets section we can see that the postgres-exporter is up  as shown in the below screenshot.

 
![Screenshot from 2023-12-14 23-27-54](https://github.com/sarvanand14/devops-assessment-2/assets/142403605/016f0ca3-84f3-4fdf-be68-e3a38870b4bb)


Later after the checking the targets section we can go to the graph section and check if the postgres query are present in the prometheus.  
Below 2 screenshots shows the postgres and pg queries in the prometheus


1.
![Screenshot from 2023-12-14 23-29-05](https://github.com/sarvanand14/devops-assessment-2/assets/142403605/ffad2c70-ce41-4bd1-820a-2a35629bf541)



2.

![Screenshot from 2023-12-14 23-31-10](https://github.com/sarvanand14/devops-assessment-2/assets/142403605/c4d6274e-0104-4b3c-8453-31f387e7407a)




## Doubt 

Manage Postgres credentials in secrets manager.

We can manage postgres credentials  using secrets in Kubernetes where we can create a secret object file and specify the username and password in the file in the encoded form.

OR

We can manage the postgres credentials using the secret managers like Hashicorp Vault or AWS secret manager and so on.
In this assessment if i am using the secret  managers like Vault how can i submit the details with you while submitting the assessment. 








