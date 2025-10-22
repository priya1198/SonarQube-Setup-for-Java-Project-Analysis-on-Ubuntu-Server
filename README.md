# SonarQube-Setup-for-Java-Project-Analysis-on-Ubuntu-Server
SonarQube Setup for Java Project Analysis on Ubuntu Server
This guide walks you through the process of installing SonarQube on an Ubuntu server, setting up Java & Maven, preparing your Java project for analysis, and running a full static code analysis with SonarQube. 


Prerequisites
Hardware Requirements:

Operating System: Ubuntu 22.04 LTS (or compatible)

RAM: 4GB minimum (8GB recommended)

Disk Space: Sufficient for SonarQube and project files (at least 10GB free)

Software Requirements:

Java: OpenJDK 17 (required by SonarQube)

Maven: Latest stable version

Git: For version control (optional for pulling Java projects from GitHub)

<img width="1199" height="101" alt="Image" src="https://github.com/user-attachments/assets/f0aed6bf-eb25-428c-81d1-2ad45b2e7902" />

Network:

Port 9000 should be open for accessing SonarQube's web interface.

User Privileges:

You need sudo privileges for installing software and managing configurations.



### Install a sonarcube server

<img width="1203" height="736" alt="Image" src="https://github.com/user-attachments/assets/43a8ae77-9a10-4476-a1ef-3fb41568f0b1" />

Step 1: Install Java, Maven, and Dependencies

Update your system and install the required packages:

sudo apt update -y



<img width="1027" height="314" alt="Image" src="https://github.com/user-attachments/assets/7adcfb1d-ba1f-4bbb-af3f-d2c4d92aba52" />
<img width="1091" height="715" alt="Image" src="https://github.com/user-attachments/assets/3bd15c0e-ff98-4cfe-83ce-207296f5ec27" />



Verify the installations:
java -version      # Should show OpenJDK 17
mvn -v             # Should show Maven version
git --version      # Should show Git version

<img width="1067" height="196" alt="Image" src="https://github.com/user-attachments/assets/dc3da470-abcb-4bc5-8a8d-c1eb4924cd3e" />

Step 2: Install SonarQube
Step 2.1 — Create a sonar user

<img width="1879" height="753" alt="Image" src="https://github.com/user-attachments/assets/1cf5c818-9cb5-4b4e-b524-e9046348511f" />

Create a dedicated user for running SonarQube:

sudo useradd -m -d /opt/sonarqube -r -s /bin/bash sonar


Step 3.2 — Download and Extract SonarQube

Navigate to the /opt directory and download SonarQube:

cd /opt
sudo wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-10.6.0.92116.zip
sudo unzip sonarqube-10.6.0.92116.zip




Step 4: Configure SonarQube

Edit the sonar.properties file to adjust the web access settings:

sudo nano /opt/sonarqube/conf/sonar.properties


Set the following properties:

sonar.web.host=0.0.0.0       # Allow connections from all IPs
sonar.web.port=9000          # Default port




Step 5: Start SonarQube
Option 1: Run SonarQube directly as the sonar user:
sudo -u sonar /opt/sonarqube/bin/linux-x86-64/sonar.sh start
sudo -u sonar /opt/sonarqube/bin/linux-x86-64/sonar.sh status




Option 2: Switch to the sonar user shell (optional):
sudo su - sonar
cd /opt/sonarqube/bin/linux-x86-64
./sonar.sh start
exit

<img width="1296" height="655" alt="Image" src="https://github.com/user-attachments/assets/508cb521-bee7-4ec3-a8eb-5a327ad1b6eb" />




Step 6: Access the SonarQube Dashboard

Open a web browser and go to:

http://<your-server-ip>:9000

<img width="1005" height="361" alt="Image" src="https://github.com/user-attachments/assets/918488e0-0e2a-4fd1-b98c-46312660f227" />

<img width="858" height="130" alt="Image" src="https://github.com/user-attachments/assets/2f48dfcd-ba73-4690-a970-3189a0e609e6" />

<img width="1914" height="861" alt="Image" src="https://github.com/user-attachments/assets/5769ec87-82b6-43b6-8a39-2eb17d4c06d2" />

<img width="1875" height="308" alt="Image" src="https://github.com/user-attachments/assets/1b20bd19-c944-4245-9281-9a926517473c" />

<img width="1451" height="312" alt="Image" src="https://github.com/user-attachments/assets/35448af2-b309-40b6-a18e-486d62408bc7" />

<img width="689" height="548" alt="Image" src="https://github.com/user-attachments/assets/917e3b13-dea2-4b6b-a015-f0b8c204337b" />

Login with default credentials:

Username: admin

Password: admin

You will be prompted to change the password upon first login.







