# LAMPP Ubuntu

## Install Apache
sudo apt install apache2

### Check Apache version using the below command:
sudo apachectl -v

sudo systemctl status apache2

## Install MySQL
sudo apt install mysql-server

### Verify that the MySQL server is running:
sudo service mysql status

### Check MySQl version using the below command:
sudo mysql -V

### Secure MySQL
sudo mysql_secure_installation

## Install PHP
sudo apt install php8.1-fpm php8.1 libapache2-mod-php8.1 php8.1-common php8.1-mysql php8.1-xml php8.1-xmlrpc php8.1-curl php8.1-gd php8.1-imagick php8.1-cli php8.1-imap php8.1-mbstring php8.1-opcache php8.1-soap php8.1-zip php8.1-intl php8.1-bcmath unzip -y

### Once PHP is installed you can check the version:
php -v

### Configure PHP:
sudo nano /etc/php/8.1/apache2/php.ini

upload_max_filesize = 32M

post_max_size = 48M 

memory_limit = 256M 

max_execution_time = 600 

max_input_vars = 3000 

max_input_time = 1000

### Restart Apache for the changes to take effect:
sudo service apache2 restart

## Install PhpMyAdmin
sudo apt install phpmyadmin

### Copy PhpMyAdmin configuration for Apache:
sudo cp /etc/phpmyadmin/apache.conf /etc/apache2/conf-available/phpmyadmin.conf

### Enable the configuration:
sudo a2enconf phpmyadmin.conf

### Restart Apache:
sudo service apache2 restart

## User and Folders Permissions

### Add user to www-data group
sudo usermod -a -G www-data $USER

### Verify it with the help of id and groups command:
id MY_USER

groups MY_USER

### Folder Permissions:

sudo chown -R MY_USER /var/www/html/

chgrp -R www-data /var/www/html/

sudo chmod -R 755 /var/www/html/
