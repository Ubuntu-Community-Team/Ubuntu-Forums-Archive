---
title: "HOWTO: Fedora DS 1.04 on UB8.04"
date: 2008-06-03
forum: Outdated Tutorials &amp; Tips
---

### Post by sangamc on 2008-06-03
i have succefully installed Fedora DS on Hardy Heron with all the updates and packages

Some preparation
```

cd /home/<user>
mkdir fds
cd fds


sudo apt-get install ssh
```

Download Fedora Directory Server Pre-built rpm
```
wget -c http://directory.fedoraproject.org/download/fedora-ds-1.0.4-1.FC6.i386.opt.rpm
```
	
Installing Alien Package
	```
sudo apt-get install alien
```
	
Convert .rpm Package to .deb Package
	 ```
sudo alien --scripts fedora-ds-1.0.4-1.FC6.i386.opt.rpm
```

Install Dependencies
	```
wget http://mirrors.kernel.org/debian/pool/main/t/termcap-compat/termcap-compat_1.2.3_i386.deb
wget  http://mirrors.kernel.org/debian/pool/main/libc/libc/libc5_5.4.46-15_i386.deb
wget  http://mirrors.kernel.org/debian/pool/main/l/ld.so/ldso_1.9.11-15_i386.deb
	
sudo dpkg --install ldso_1.9.11-15_i386.deb
sudo dpkg --install libc5_5.4.46-15_i386.deb
sudo dpkg --install termcap-compat_1.2.3_i386.deb
```
	
Installing Java Run Time Environment
	```
sudo apt-get install sun-java6-bin
```
	
	
Installing Apache2-mpm-worker
	```
sudo apt-get install apache2-mpm-worker
sudo ln -s /usr/sbin/apache2 /usr/sbin/httpd
```
	
Installing .deb package
	```
sudo dpkg -i fedora-ds_1.0.4-2_i386.deb
``` 
	
Creating a user and group for the daemon
	```
sudo groupadd fds
sudo useradd -s /bin/false -g fds fds
```

Running Fedora-ds Setup Program
	 ```
sudo /opt/fedora-ds/setup/setup -k
```
	
		Please select the install mode:
		  1 - Express - minimal questions
		  2 - Typical - some customization (default)
		  3 - Custom - lots of customization
		Please select 1, 2, or 3 (default: 2) 1
		
		Hostname to use (default: facility-srv1.it-mgt.com) 
		Server user ID to use (default: nobody) fds
		Server group ID to use (default: nobody) fds
		
		Fedora configuration directory server
		administrator ID [admin]: 
		Directory Manager DN [cn=Directory Manager]:
		
	```
sudo cp /opt/fedora-ds/setup/install.inf /opt
sudo chmod 640 /opt/install.inf
sudo pico /opt/install.inf
```
	
Add the directive for ApacheRoot at the end of the file 
	 ...
	 [admin]
	 SysUser=   root
	 Port= 16000  
	 ServerIpAddress=
	 ServerAdminID=   admin
	 ServerAdminPwd=   dsadmin
	 ApacheDir=   /usr/sbin
	 ApacheRoot=   /usr/lib/apache2
	
Rerun the setup script with the new ApacheRoot directive
	```
sudo /opt/fedora-ds/setup/setup -s -f /opt/install.inf
```
	
You can now use the console.  Here is the command to use to start the console:
	```
cd /opt/fedora-ds
./startconsole -u admin -a http://facility-srv1.it-mgt.com:<port number>/
```
	
Adjusting the admin-server's httpd.conf file
	 ```
sudo pico /opt/fedora-ds/admin-serv/config/httpd.conf
``` 
		Comment out the following apache module
		
		#LoadModule log_config_module /usr/lib/apache2/modules/mod_log_config.so
		
Starting the admin-server
	 ```
sudo /opt/fedora-ds/start-admin
```
	
Persistent startup
	```
sudo pico /etc/inti.d/local
	
		#! /bin/sh
		/opt/fedora-ds/slapd-fossedu/start-slapd
		/opt/fedora-ds/start-admin
		
sudo chmod +x /etc/init.d/local
sudo update-rc.d local defaults 80
```

---

