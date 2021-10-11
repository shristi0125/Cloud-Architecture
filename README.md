# Cloud-Architecture
🔅 Create an AWS EC2 instance
🔅 Configure the instance with Apache Webserver.
🔅 Download php application name “WordPress”.
🔅 As wordpress stores data at the backend in MySQL Database server Therefore, you need to setup a MySQL server using AWS RDS service using Free Tier.
🔅 Provide the endpoint/connection string to the WordPress application to make it work.

WHAT IS AWS RDS?

Amazon Relational Database Service (Amazon RDS) makes it easy to set up, operate, and scale a relational database in the cloud. It provides cost-efficient and resizable capacity while automating time-consuming administration tasks such as hardware provisioning, database setup, patching and backups. It frees you to focus on your applications so you can give them the fast performance, high availability, security and compatibility they need.
Amazon RDS is available on several database instance types — optimized for memory, performance or I/O — and provides you with six familiar database engines to choose from, including Amazon Aurora, PostgreSQL, MySQL, MariaDB, Oracle Database, and SQL Server. You can use the AWS Database Migration Service to easily migrate or replicate your existing databases to Amazon RDS
What is WordPress?
![image](https://user-images.githubusercontent.com/73373261/136796517-7bb18937-234d-4ae8-b4fe-e7cdafef4944.png)

The simplest answer is this:
WordPress is your website’s operating system.
Think of it this way, just like your smartphone needs either iOS or Android to work, your “smart-website” needs WordPress. While WordPress is certainly not the only website operating system around, it is the unquestionable leader in this space. At the time of writing, WordPress runs 32% of all websites. Again, that is *all* websites
Steps 1:
Launch an EC2 instance For Deploying WordPress.


Steps 2:
Connect to EC2 Instance using Putty and install necessary libraries.
dnf update -y
dnf install httpd -y
dnf install wget
vim -y
dnf install https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm

dnf install https://rpms.remirepo.net/enterprise/remi-release-8.rpm
dnf module install php:remi-7.4

![image](https://user-images.githubusercontent.com/73373261/136797145-ca15963b-509f-485a-803f-787d104aaa13.png)

dnf install php-mysqlnd -y

![image](https://user-images.githubusercontent.com/73373261/136797169-ddcb77f1-73e3-4d5f-a3c8-beb6749f7b6b.png)


systemctl start httpd
dnf update -y (To check the latest update of packages)
![image](https://user-images.githubusercontent.com/73373261/136797041-4ba94448-5d44-409c-a69f-35f14be4b93e.png)


dnf install httpd -y (To install Apache webserver)
![image](https://user-images.githubusercontent.com/73373261/136797084-a9eb3217-3a49-4577-bb1b-39ce10d1112d.png)


dnf install vim wget -y (To install vim editor and wget cmd)



dnf module install php:remi-7.4 (To install PHP)

dnf install php-mysqlnd (To install MYSQL Server)

wget htttps://wordpress.org/latest.tar.gz (It will download a installation file on wordpress in ZIP format)

tar xf latest.tar.gz -C /var/www/html (It will unzip wordpress installtion file and copy it to /var/www/html/ directory)

systemctl start httpd (To start Apache Webserver)
Verify that your apache is working or not.
Enter your Public IP to Web browser.
![image](https://user-images.githubusercontent.com/73373261/136797246-39130044-dc38-4f0c-930b-cd96442d33a4.png)


Step 3:Launch RDS database For WordPress
Open Amazon RDS and click on Create Database
Select MySQL as database type
In the Templates section, choose the Free tier.
DB instance identifier — default
Master username — admin
Master password — Choose a password.
Confirm password — Confirm the password
Availiability Zone — us-east-1
Initial Database Name — database-2
👉 Click on Create Database
![image](https://user-images.githubusercontent.com/73373261/136797304-96205b02-da82-43d7-a630-74386e5cccf6.png)


👉 Select MySQL

👉 Select Version & Template as Free Tier

![image](https://user-images.githubusercontent.com/73373261/136797331-5f200999-dd26-4724-a178-78d9221fd7ee.png)
![image](https://user-images.githubusercontent.com/73373261/136797377-7fdb953c-a6bf-4a3d-9886-71deeb906a13.png)
![image](https://user-images.githubusercontent.com/73373261/136797416-4e1bff52-0912-4de9-bc20-f117be3d11b9.png)
![image](https://user-images.githubusercontent.com/73373261/136797451-ed825c44-ea45-47db-a8a5-8f2073cb0799.png)
![image](https://user-images.githubusercontent.com/73373261/136797478-368b662e-6f37-4a90-8240-228d0247dbd0.png)










👉 Click On Create DataBase.

![image](https://user-images.githubusercontent.com/73373261/136797513-3d6a1ace-30aa-418b-91a0-1a04464fa73d.png)

👉 Here we see our RDS DataBase is successfully created.
![image](https://user-images.githubusercontent.com/73373261/136797550-fbcd89b7-5cb7-43cb-a6f0-1d54a525f7ad.png)


👉 Now if we wants to connect our database so we need the EndPoint URL.
![image](https://user-images.githubusercontent.com/73373261/136797584-164b7cd8-c05a-44f0-a5f3-61c41149c018.png)

👉 Go to your instance and type this command to connect.
mysql -h endpoint url -u admin -p

Final Step: Let’sConnect to WordPress.
wordpress/IP

![image](https://user-images.githubusercontent.com/73373261/136797656-2594bd45-5d48-46e7-84b8-565d65fc98ef.png)


👉 Provide Databse Name,UserName,Password,Endpoint Url.
![image](https://user-images.githubusercontent.com/73373261/136797697-68d103dd-63cf-45e1-aa18-4373c06c8d38.png)


👉 Click on Run the installation.
![image](https://user-images.githubusercontent.com/73373261/136797739-9bb13201-f088-40a0-bf0c-5b702407e4d7.png)


Yeah WordPress with MySQL Connection established successfully.�
![image](https://user-images.githubusercontent.com/73373261/136797784-54a093c3-a054-4da8-a4b6-bd6a12fe200b.png)
![image](https://user-images.githubusercontent.com/73373261/136797820-881a8bc0-f7a5-4d43-9e54-37436571b3df.png)


