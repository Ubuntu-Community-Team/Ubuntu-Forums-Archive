---
title: "HowTo: LAMP server w/ SSH, Samba, Torrentflux, phpMyAdmin and some security"
date: 2009-05-27
forum: Outdated Tutorials &amp; Tips
---

### Post by hellarough on 2009-05-27
After reading many, many HowTo's I have finally gotten my LAMP server in a satisfactory state. It has been one of the most rewarding projects that I have ever taken on. In the future, I plan to edit this tutorial to reflect the positive changes that I make to my platform as my contribution to the forums (you guys/gals have helped me a whole lot). 

**Disclaimer(s):** This is not the only way it is simply my way. Since I am still a fairly big "noob", constructive input is always valued along with new discussions beyond the scope of what I offer here. 

**Back Up any files before you edit them** so they can be easily restored! I have one example below but the basic commands should look like this:
```
sudo cp -v /source_file.whatever /destination_file.whatever.original
```
```
sudo cp -v /backup_2_be_restored.whatever.original /file_you_are_copying_over.whatever
```

Now to the fun part....

Since my system is quite old and only has 128mb of ram I opted to use [ubuntu 8.04lts]("http://www.ubuntu.com/getubuntu/download-server") (server edition).   

**1. Start by installing the server OS to your project computer.** You will want it connected to your network during the installation. [Here is a nice LAMP installation tutorial w/ tons of pics]("http://www.howtoforge.com/ubuntu-home-fileserver").  Keep in mind that the options below are important during installation. 
     A. *hostname* - whatever you are gonna call this machine
     B. *full name for new user* - I recommend administrator
     C. *user name for new user* - once again administrator (don't use admin as I have heard that it is reserved)
     D. *password for new user* - use a strong password that you will remember, include at least one number and one special character
     E. *proxy* - if you go through a proxy enter it here otherwise leave it blank, if unsure chances are you should leave it blank
     F. *software selection* - use the space bar to select highlighted options, for this tutorial we will select LAMP server, OpenSSH server, and Samba file server 
     G. *database admin password* - create a strong password for the MySQL database
 
**2. Secure the root account.**
     A. In the terminal type the command below and enter another strong password like the one created for the user above.
```
sudo passwd root
```
**3. Configure the network interfaces.**
     A. Assign a static IP address to your server from your router's admin page. Since it is connected to your network (and powered on) you should be able to see an attached device and reserve an IP for it. This will ensure that each time it restarts it is automagically assigned the same IP. You will want to write the IP down along with the netmask.
     B. In the terminal type the command below
```
sudo nano /etc/network/interfaces
```
You want to edit the file to look like the one below but in place of the numbers you will put your network info.
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1

```
     C. edit the hosts file
```
sudo nano /etc/hosts
```
        edit the file to look something like this (substituting in your specific values)
```

127.0.0.1       localhost.localdomain   localhost
server_ip_address   server1.example.com     your_hostname_here

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts#

```
    D. Restart the network by typing in a terminal
```
sudo /etc/init.d/networking restart
```

**4. Restart the computer and unplug the monitor and mouse.** This is your chance to stash it away. As long at the power cord, network cable, and keyboard stay attached then you are good to go. 
     A. Restart your system
```
 sudo shutdown -r now
``` 

**5. Use putty or some other ssh client to connect to your new server from any computer on your network.**
     A. Hostname is the IP address of your server
     B. Port - 22
     C. Username - the user you set up during installation along with the password (in this tutorial it would be administrator).

**6. Edit your package sources.** Comment out (place a # sign in front of) the cdrom and uncomment the universe and multiverse repos.
```
sudo nano /etc/apt/sources.list
```
     Below are the lines in the file you should pay attention to
```
#
#deb cdrom:[Ubuntu-Server 8.04 _Hardy Heron_ - Release i386 (20080423.2)]/ hardy main restricted
#deb cdrom:[Ubuntu-Server 8.04 _Hardy Heron_ - Release i386 (20080423.2)]/ hardy main restricted

deb http://de.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ hardy main restricted

deb http://de.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
  
deb http://de.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://de.archive.ubuntu.com/ubuntu/ hardy universe
deb http://de.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://de.archive.ubuntu.com/ubuntu/ hardy-updates universe

deb http://de.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://de.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

```

     Now is a good time to update your system:
```
sudo apt-get update
sudo apt-get upgrade
```

**7. Set up your Samba Share(s)** These files shares will be accessible to anyone on your home network. They are not secured with any usernames or passwords. If you would like to further secure your samba share I recommend that you start at the [samba web-site.]("http://us6.samba.org/samba/")  
     A. Create the directory for the share and change permissions
```
sudo mkdir /home/your_username_here/fileserver
sudo chmod 777 -Rv /home/your_username_here/fileserver 
```
     B. Backup the samba config file
```
sudo cp -v /etc/samba/smb.conf /etc/samba/smb.conf.original
```
to restore a back up simply use this command
```
sudo cp -v /etc/samba/smb.conforiginal /etc/samba/smb.conf
```
     C. Edit the samba config file
```
sudo nano /etc/samba/smb.conf
```
keep in mind that this share is NOT secured so many things regarding passwords and users are commented out. Below are the important lines to pay attention to. If you really want to, in the name of simplicity, you can clear the entire file and only write the lines in that are not commented. I should also mention that [SWAT]("http://en.wikipedia.org/wiki/Samba_(software)") may be a good tool for you to use ([here is a server install with SWAT configuration]("http://jonpeck.blogspot.com/2006/11/how-to-configure-80-fileserver-in-45.html") if you choose to do that). Originally I tried using SWAT but everytime I edited the config file my shares would disappear because of some options that were automatically written to the config file. Now, I just edit the config file myself. This route has taught me a few things and made it easier to edit the apache config files. 
```

[global]
	server string = samba server
#	map to guest = Bad User
#	obey pam restrictions = Yes
#	passdb backend = tdbsam
#	pam password change = Yes
#	passwd program = /usr/bin/passwd %u
#	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
#	unix password sync = Yes
	security = share
	name resolve order = hosts lmhosts
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
#	panic action = /usr/share/samba/panic-action %d
#	invalid users = root

```
        At the bottom of the same smb.conf file add the following for each unique share (substituting when necessary)
```

[insert_your_share_name_here]
	path = /home/your_username_here/fileserver  # or path to share directory
	read only = No
	guest ok = Yes

```
     D. Save the changes to smb.conf and restart samba. When you find a configuration that you like you can back it up with the same command as earlier.
```
sudo /etc/init.d/samba restart
```

**8. Install phpMyAdmin**
     A. Install - be sure to select apache2 and MySQL with the space bar when asked about configuration
```
sudo apt-get install phpmyadmin
```
     B. Secure the database by opening a web-browser and pointing it to [http://server_ip_address/phpmyadmin](http://server_ip_address/phpmyadmin) - the login should be root with the password that you created for the MySQL Database. Here you will want to click the privileges link and be sure that all root accounts are password protected (if not add a password). 

**9. Install torrentflux**
     A. Installation - ignore the libphp-adodb message and answer yes to configure with dbconfig-common. Leave the password prompt blank so a random one is generated and answer yes to restart apache.
```
sudo apt-get install torrentflux
```
     B. Configuration - point a web-browser to [http://server_ip_address/torrentflux](http://server_ip_address/torrentflux) - the login and password should be root. Click the admin tab then settings to change the share path to /home/your_username_here/fileserver/ - you can also use the new user link to add new users (you can create a user for each person on your network!). I recommend that you also use the admin tab to change the root account password (for security's sake dont use a password that you have used above).

*You should now have a fully functional file server that allows you to remotely download torrents (so you dont tie up your machine). You can also administer your MySQL DB via a web-browser and phpMyAdmin. However, as we all know this is just the basics and I like many others wanted added security and something better. Continue below for a few special configurations.* 

**1. OpenSSH and Security through Obscurity** - you can change the port that OpenSSH listens to so that it will only accept incoming connections from a port that you know. Here I use 36000 as an example, feel free to use a port that is not reserved or commonly used...If I tell you what I actually use then it would defeat the purpose.
     A. Change the port that OpenSSH listens to
```
sudo nano /etc/ssh/sshd_config
```
Change the line that reads:
```
Port 22
```
to:
```
Port 36000
```
     B. Restart the service - you should get disconnected. Open a new instance of Putty or whatever you use and re-connect but be sure to use the port you just specified.
```
sudo /etc/init.d/ssh restart
```

**2. A nice homepage**
     A. Get rid of the default index.
```
sudo rm -v /var/www/index.html
```
     B. Make your own index.
```
sudo nano /var/www/index.php
```
        My file looks very similar to this; However, if you know html/css and php you options are nearly limitless.  
```

<?php $hostname = $_SERVER['HTTP_HOST']; ?>
<html><head>
<meta content="text/html; charset=ISO-8859-1" http-equiv="content-type"><title>index.php</title>

</head><body style="color: white; background-color: rgb(83, 108, 86);" alink="#7fb883" link="#a0e9bb" vlink="#c7fdae">
<br>
<br>Admin Pages:
<br>
<hr style="width: 99%; height: 2px;">
<a href="http://<?php echo $hostname; ?>/torrentflux">Torrentflux</a><br>
<a href="http://<?php echo $hostname; ?>/phpmyadmin">phpMyAdmin</a><br>
<br>
<hr style="width: 99%; height: 2px;">
</body></html>

```

**3. Apache2 Security** - Securing /var/www/ - use a username and password different from you system username(s) and password(s). [This is a nice blog about creating sites within apache.]("http://www.tbaumi.de/blog/?p=72")
     A. Create a user/password file
```
sudo htpasswd -c /etc/apache2/htpasswd new_username_here
```
        if, after creating the file above, you want to add additional users use this command
```
sudo htpasswd /etc/apache2/htpasswd another_new_username_here
``` 
     B. Editing the sites-available
```
sudo nano /etc/apache2/sites-available/default
```
        Near the top of the file you need to change the document root and directory section to look like this (substitute values when necessary)
```

DocumentRoot /var/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all

		AuthType Basic
		AuthName "your_own_security_message_goes_in_these_quotes"
		AuthUserFile /etc/apache2/htpasswd
		Require valid-user
	</Directory>

```
      C. Reload apache2
```
sudo /etc/init.d/apache2 reload
```

**4. Your Router and home network** - The final stretch of this tutorial.
      A. Things you should do to your router (you may have to consult the manual): use WPA encryption instead of WEP if possible, block all incoming traffic (close all ports), and use a very strong password
      B. If you want to be able to access your torrentflux and phpmyadmin pages from the web then you should forward port 80 to the server's ip address. keep in mind that your login info for apache is sent plain text so it is important that the users do not match system users. You also should look into setting up secured web-pages (beyond my knowledge for now). For external access via SSH (or SFTP, thanks filezilla!) forward port 36000 (or what ever you decided earlier).


In conclusion, here are the sites I used to build my server, they are great references and good starting places to learn more:
1. [Dissension - configuring and $80 file server]("http://jonpeck.blogspot.com/2006/11/how-to-configure-80-fileserver-in-45.html")
2. [How To Forge: Simple Home File Server]("http://www.howtoforge.com/ubuntu-home-fileserver")
3. [Some Blog about vhosts in apache2]("http://www.tbaumi.de/blog/?p=72")
4. [Some Blog about SSL and security in apache]("http://www.tbaumi.de/blog/?p=60")

---

