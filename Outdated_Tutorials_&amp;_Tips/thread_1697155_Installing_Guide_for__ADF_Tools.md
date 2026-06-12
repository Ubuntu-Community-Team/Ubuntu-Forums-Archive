---
title: "Installing Guide for  ADF Tools"
date: 2011-02-28
forum: Outdated Tutorials &amp; Tips
---

### Post by ALGHABBAn on 2011-02-28
Hi , since tow weeks ago I was trying to install Oracle 11g and ADF tun tiem tools that Contain also weblogic and jdevevloper  , will after so much of Pain I'm now running all those tools together    and it work like charm so let's start . 

**Installing Jdeveloper** 
**•Start Installing Wizard** 

After downloading Jdeveloper from Oracle , that file will have .bin Extension , .bin it's just a Compressed file like zip or RAR or ISO . 

To start install Jdeveloper just click right and choose properties  down of the menu , you will see Properties window be sure to make every access option in that windows as read and write . and check the Allow exciting file as program . 

When you done open the terminal  from Applications > Accessories > Terminal 

First you will need to login as root user to be able install Jdeveloper , just type 

$ sudo su 

Inter your password and click enter know you login as root user , so just drag and drop Jdeveloper.bin file into the terminal this move will type the Jdeveloper.bin file path , know click enter and you will see the file exciting . 
 

**•Run Jdeveloper** 

Unlike windows in Ubuntu you need to create the a Shortcut to the desktop or the Application menu  by Manually so let's do that .  
when you install Jdeveloper it install on /root/oracle/ so you don't have any permission in that folder ,  you will need to take the Powers for the root folder . open the terminal and type : 

chown -R username /root/ 


Those command will change the owner for this folder from root to you .

Jdeveloper are located in the path :  
/root/oracle/Middleware/Jdeveloper/jdev/bin/jdev.sh

you can create lancher by right click in the desktop and insert the path 
u .
 
**Things may happen during the installation process ( the most error common ) :**
• Permission denied for /root/ , if you see this when you try run the wizard that mean you run Jdeveloper.bin as normal user , you need to be a root user , but if you see this error after install Jdeveloper , and when you try to open Jdeveloper that mean you need to be the owner for /root/ folder < see run Jdeveloper > 

=================================================================

**•Start Installing Wizard** 
After downloading WebLogic  from Oracle , that file will have .bin Extension , .bin it's just a Compressed file like zip or RAR or ISO . 

To start install WebLogic  just click right and choose properties  down of the menu , you will see Properties window be sure to make every access option in that windows as read and write . and check the Allow exciting file as program . drag and drop WebLogic.bin file into the terminal this move will type the WebLogic.bin file path , know click enter and you will see the file exciting . 
 
**•Run WebLogic**
 WebLogic are located in this bath 
/root/oracle/Middleware/wlserver_10_3 /common /bin/config.sh

you can do the same thing we did't with Jdeveloper 

**Things may happen during the installation process ( the most error common ) :**
•Permission denied for /root/ , if you see this when you try run the wizard that mean you run WebLogic.bin as normal user , you need to be a root user , but if you see this error after install WebLogic, and when you try to open Jdeveloper that mean you need to be the owner for that folder . 

**•Start Installing Wizard **

After downloading ADF RunTime  from Oracle , that file has zip Extension click right in that file end extract to anywhere you want Open the firs folder that have name 1_of_1 and drag runInstaller file and drop it into the terminal be sure that you're  in the normal user not in the root user . 

When you drop that file in terminal it will ask you about the JDK6 folder if you following the same guide from the first it will be in 
/root/oracle/middleware/jdk160_21 Press Inter the wizard will start .

Things may happen during the installation process ( the most error common )
•No such file or folder Permission denied , you run this shill as normal user you need to run it as root user . 
•You can't run this file as root , please run it as normal user , you need to get out from root user and be root user .

=================================================================

Installing Oracle 11g Database 

•Start installing 
To make all the install step so easy on you , we make just 7 shill file . you tell that there are 7 step to install oracle Database 11g R2 on Ubnutn . 

1.Install require package : you can do this by yourself go to the terminal and type the following  :

apt-get install elfutils
apt-get install libaio1
apt-get install libaio-dev
apt-get install libstdc++6-4.4-dev
apt-get install numactl
apt-get install pdksh
apt-get install sysstat
apt-get install unixODBC-dev
apt-get install unixODBC

2.The second step creating group and oracle user on the system : 

groupadd oinstall
useradd -s /bin/bash -m -g oinstall oracle
passwd oracle
xhost local:oracle

3.The next two pieces of work will change various kernel settings and limits to be able to run database instances locally if you desire: 

cp /etc/security/limits.conf /etc/security/limits.conf.bak
cat >> /etc/security/limits.conf
oracle              soft    nproc   2047
oracle              hard    nproc   16384
oracle              soft    nofile  1024
oracle              hard    nofile  65536
<Ctrl-C>

cp /etc/sysctl.conf /etc/sysctl.conf.bak
cat >> /etc/sysctl.conf
fs.aio-max-nr = 1048576
fs.file-max = 6815744
kernel.shmall = 2097152
kernel.shmmax = 536870912
kernel.shmmni = 4096
kernel.sem = 250 32000 100 128
net.ipv4.ip_local_port_range = 9000 65500
net.core.rmem_default = 262144
net.core.rmem_max = 4194304
net.core.wmem_default = 262144
net.core.wmem_max = 1048586
net.ipv4.tcp_wmem = 262144 262144 262144
net.ipv4.tcp_rmem = 4194304 4194304 4194304
<Ctrl-C>

4.The below directories are the Oracle recommended Optimal Flexible Architecture (besides all the separation of physical devices):

mkdir -p /u01/app/oracle
chown -R oracle:oinstall /u01/app/oracle
chmod -R 775 /u01/app/oracle
mkdir -p /u01/app/oraInventory
chown -R oracle:oinstall /u01/app/oraInventory
chmod -R 775 /u01/app/oraInventory
ln -s /usr/bin/awk /bin/awk

5.Unzip the files and move it to /home/oracle :
mv /home/alghabbn/Downloads/linux_11gR2_database_* /home/oracle/
su - oracle
unzip linux_11gR2_database_1of2.zip
rm linux_11gR2_database_1of2.zip
unzip linux_11gR2_database_2of2.zip
rm linux_11gR2_database_2of2.zip

6.Here is the where the actual installation begins. You will get a nice GUI for this part. Run Database installing wizard :

cd database
./runInstaller

7. Edit /etc/oratab and change the line :

sid:/u01/app/oracle/product/11.2.0/dbhome_1:N
to :

sid:/u01/app/oracle/product/11.2.0/dbhome_1:Y

8. Next, we want to create a script to execute on startup to start the database and the listener :

cd /etc/init.d
sudo vi oracledb

The script should be as follows :

#!/bin/bash
#
# Run-level Startup script for the Oracle Listener and Instances
# It relies on the information on /etc/oratab
# Based on script listing at
# [http://www.pythian.com/news/1355/installing-oracle-11gr1-on-ubuntu-810-intrepid-ibex/](http://www.pythian.com/news/1355/installing-oracle-11gr1-on-ubuntu-810-intrepid-ibex/)
# Mike 7/3/10
#
export ORACLE_BASE=/u01/app/oracle
export ORACLE_HOME=/u01/app/oracle/product/11.2.0/dbhome_1
export ORACLE_OWNR=oracle
export PATH=$PATH:$ORACLE_HOME/bin 

if [ ! -f $ORACLE_HOME/bin/dbstart -o ! -d $ORACLE_HOME ]
then
    echo "Oracle startup: cannot start"
    exit 1
fi 

case "$1" in
    start)
        # Oracle listener and instance startup
        echo -n "Starting Oracle: "
        su $ORACLE_OWNR -c "$ORACLE_HOME/bin/lsnrctl start"
        su $ORACLE_OWNR -c "$ORACLE_HOME/bin/dbstart $ORACLE_HOME"
        touch /var/lock/oracle
        echo "OK"
        ;;
    stop)
        # Oracle listener and instance shutdown
        echo -n "Shutdown Oracle: "
        su $ORACLE_OWNR -c "$ORACLE_HOME/bin/lsnrctl stop"
        su $ORACLE_OWNR -c "$ORACLE_HOME/bin/dbshut $ORACLE_HOME"
        rm -f /var/lock/oracle
        echo "OK"
        ;;
    reload|restart)
        $0 stop
        $0 start
        ;;
    *)
        echo "Usage: `basename $0` start|stop|restart|reload"
        exit 1
esac 

exit 0
Now make the script executable and set it to run at boot time :

chmod a+x /etc/init.d/oracledb
update-rc.d oracledb defaults 99


**Things may happen during the installation process ( the most error common ) :**

•Oracle User Doesn't have access in sudoer group . go to System > admonitions  > user and group , click on manger group , choose from the list in the left sudo and add oracle user . 

•This program can't run as root , type exit to run the script as normal user .

•Can't run the wizard in this display color error , will there's a fast solution for this error just type " # export DISPLAY = :0.0" and start the wizard .

•During installation wizard  you may  see some error come up , don’t worry and click continue .

---

