##MESS Work In Progress

# 14.04-ubuntu-post-install
##Notes on what will be in this script

#configure bash history timestamp


#install the following packages
lamp openssh uptimed git lets-encyrpt screen pv

INSTALL_PKGS="pk1 pk2 pk3 pk4 pk5 ... and so ... on ..pk_gogol"
for i in $INSTALL_PKGS; do
  sudo apt-get install -y $i
done


#remove MySQL and install mariadb

#sudo apt-get remove --purge mysql-server mysql-client mysql-common
#sudo apt-get autoremove
#sudo apt-get autoclean



#Install PHP 5.5
sudo apt-get install php5 libapache2-mod-php5 php5-mcrypt


$ sudo apt-get install python-software-properties
$ sudo add-apt-repository ppa:ondrej/php5
$ sudo apt-get update
$ sudo apt-get install -y php5

php -v

#Install Apache2
sudo apt-get install apache2 libapache2-mod-php5

#Install MariaDB and secure install
sudo apt-get install mariadb-server
sudo mysql_secure_installation

#Restart Apache2 and MariaDB
sudo service apache2 restart
sudo service mysql restart


#Open Firewall to port 80 to firewall users
sudo iptables -A INPUT -m state --state NEW -p tcp --dport 80 -j ACCEPT
sudo ufw allow 80/tcp

#All in one
sudo apt-get -y install apache2 mysql-server php5-mysql php5 libapache2-mod-php5 php5-mcrypt

#Install PHPMyAdmin
sudo apt-get install phpmyadmin apache2-utils

#Install Let's Encrypt
apt-get install git
git clone https://github.com/letsencrypt/letsencrypt /opt/letsencrypt

#Backup sources list and add in Webmid repository
down vote
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak

echo "deb http://download.webmin.com/download/repository sarge contrib" | sudo tee -a /etc/apt/sources.list && sudo apt-get update

wget -q http://www.webmin.com/jcameron-key.asc -O- | sudo apt-key add -

sudo apt-get update

sudo apt-get install webmin

