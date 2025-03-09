🚀 WordPress Setup on macOS M1 using Ubuntu VM

Easily set up WordPress on an Ubuntu VM running on macOS M2 using Vagrant.

![image alt](https://github.com/rajatrajat0210/Wordpress-Ubuntu-Deployment/blob/main/WordpressVM.png?raw=true)

📌 Prerequisites

✅ macOS M1/M2 system

✅ Virtualization software (e.g., UTM, Multipass, Vagrant)

✅ Ubuntu ARM-based image

✅ Basic familiarity with Linux commands

🔧 Step 1: Setting Up the Ubuntu VM

Follow the detailed PDF guide for setting up the Ubuntu VM:📄 Apache-HTTPD-Deployment

⚡ Using Vagrantfile for Quick Setup if you want to manually
⚡ Using VagrantfileIAC for Automated provisioning using Inline Shell scripting


To simplify the process, use Vagrantfile to set up your Ubuntu VM which has been attached.


🔥 Run the following commands:
```bash
vagrant up
vagrant ssh
```

🌍 Step 2: Installing and Configuring WordPress

Once the Ubuntu VM is ready, follow this official guide to install WordPress:
📖 Ubuntu WordPress Setup Guide

🛠️ Troubleshooting for macOS M1 Users

❗ "Error Establishing a Database Connection"

If you see this error, follow these steps:

🔹 1. Verify MySQL is Running
```bash
sudo systemctl status mysql
```
If not active, start it:
```bash
sudo systemctl start mysql
```
🔹 2. Check wp-config.php Database Credentials

sudo nano /var/www/html/wordpress/wp-config.php

Ensure the following values are set:

define('DB_NAME', 'wordpress');
define('DB_USER', 'wordpress');
define('DB_PASSWORD', 'yourpassword');
define('DB_HOST', '127.0.0.1');

🔹 3. Grant MySQL User Permissions
```bash
mysql -u root -p
```
Then execute:

ALTER USER 'wordpress'@'localhost' IDENTIFIED BY 'yourpassword';
GRANT ALL PRIVILEGES ON wordpress.* TO 'wordpress'@'localhost';
FLUSH PRIVILEGES;
EXIT;

🔹 4. Restart Services
```bash
sudo systemctl restart mysql
sudo systemctl restart apache2
```
🌐 Step 3: Accessing WordPress

Once everything is set up, open your browser and go to:

http://your-server-ip/wordpress

Follow the on-screen instructions to complete the setup! 🎉

🤝 Contributing

Feel free to open an issue or submit a pull request for improvements! 🚀

💡 Maintained by: @rajatrajat0210
