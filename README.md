# VProfile Web Application (AWS Lift-and-Shift Migration) 🚀

A robust Java-based web application for user profile management, migrated to **AWS Cloud** using a **lift-and-shift** strategy for improved scalability, security, and automation.

## Architectural Design on AWS 📐

![Screenshot 2025-02-02 171012](https://github.com/user-attachments/assets/dc34ff51-6f7b-47b2-b887-521a461d1faf)

## Flow of Execution➡️
1. Login to AWS Account
2. Create Key Pairs
3. Create Security Groups
4. Launch Instances with User Data [BASH SCRIPTS]
5. Update IP to Name Mapping in Route 53
6. Build Application from Source Code
7. Upload to S3 Bucket
8. Download Artifact to Tomcat EC2 Instance
9. Setup ELB with HTTPS [Cert from Amazon Certificate Manager]
10. Map ELB Endpoint to Website Name in GoDaddy DNS
11. Verify
12. Build Auto Scaling Group for Tomcat Instances


## Technologies Used 🛠️

### Backend
- Java 17
- Spring MVC
- Spring Security
- Spring Data JPA
- Hibernate
- Maven

### Frontend
- JSP (JavaServer Pages)
- HTML/CSS
- JavaScript

### Database & Storage 📦
- MySQL 8 (AWS RDS)
- Memcached (for caching)
- Amazon S3 (for artifact storage)

### Message Queue 📩
- RabbitMQ (AWS EC2)

### Search 🔍
- Elasticsearch

### Server
- Apache Tomcat 8.5 (AWS EC2)

## AWS Cloud Infrastructure ☁️

- **Amazon EC2** - Hosts Tomcat, RabbitMQ, Memcached, and MySQL instances.
- **Elastic Load Balancer (ELB)** - Distributes traffic to Tomcat instances.
- **Auto Scaling Group** - Manages EC2 instance scaling based on load.
- **Amazon S3** - Stores application artifacts and static resources.
- **Amazon Route 53** - Manages private DNS for backend services.
- **Amazon Certificate Manager (ACM)** - Provides SSL/TLS certificates for HTTPS.
- **IAM & Security Groups** - Implements access control and security best practices.

## Features ✨

- **Lift-and-Shift Migration** - Seamlessly migrated from on-premises to AWS Cloud.
- **Scalability** - Auto Scaling ensures high availability and cost optimization.
- **User Authentication & Authorization**
- **Profile Management**
  - Personal Information
  - Contact Details
  - Professional Information
  - Skills Management
- **File Upload (Profile Images)**
- **Caching with Memcached**
- **Message Queue Integration (RabbitMQ on EC2)**
- **Elasticsearch Integration**
- **RESTful API Endpoints**

## Prerequisites 🔧

- AWS Account
- AWS CLI & SDK
- Terraform/CloudFormation (optional for Infrastructure as Code)
- JDK 17
- Maven 3.x
- MySQL 8 (AWS RDS)
- Memcached (AWS EC2)
- RabbitMQ (AWS EC2)
- Elasticsearch (AWS EC2)
- Tomcat 8.5 (AWS EC2)

## Configuration ⚙️

### AWS Setup
- Create an **EC2 key pair** for SSH access.
- Configure **Security Groups** for Load Balancer, Tomcat, and backend services.
- Set up **IAM roles** for resource access.

### Application Configuration
- Configure MySQL connection in `application.properties` (AWS RDS endpoint)
- Import database schema: `src/main/resources/db_backup.sql`
- Update **Memcached, RabbitMQ, and Elasticsearch** endpoints in `application.properties`

## Deployment 🚀

### AWS Deployment Steps
1. **Launch EC2 Instances**
   - Provision EC2 instances for Tomcat, RabbitMQ, Memcached, and Elasticsearch.
2. **Set Up Load Balancer & Auto Scaling**
   - Deploy an **Application Load Balancer (ALB)** to distribute traffic.
   - Configure **Auto Scaling** for Tomcat instances.
3. **Deploy Application**
   - Build project: `mvn clean install`
   - Upload WAR file to **Amazon S3**.
   - Deploy to EC2 Tomcat instances using a script or Ansible.
4. **Configure Route 53 & SSL**
   - Set up **Route 53** for internal service discovery.
   - Provision **SSL certificates** via Amazon Certificate Manager (ACM).
5. **Validate Deployment**
   - Verify application functionality through the Load Balancer endpoint.
   
### Automated Deployment (Ansible & CI/CD) 🤖
1. **Ansible Playbooks**
   - Provision EC2 instances, install dependencies, deploy application.
2. **Jenkins CI/CD Pipeline**
   - **Stages:** Build, Unit Tests, Integration Tests, SonarQube Analysis, Deploy to AWS.

## Security 🔐

- Enforced **IAM roles** and **Security Groups** for restricted access.
- Implemented **Spring Security** for authentication and authorization.
- Encrypted **database credentials** and **sensitive configurations**.
- Configured **HTTPS with SSL/TLS** using ACM.

## Contributing 🤝

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## License 📜

MIT Licensed



