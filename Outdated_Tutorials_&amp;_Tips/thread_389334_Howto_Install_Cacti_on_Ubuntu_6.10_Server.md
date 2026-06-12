---
title: "Howto: Install Cacti on Ubuntu 6.10 Server"
date: 2007-03-20
forum: Outdated Tutorials &amp; Tips
---

### Post by Linuturk on 2007-03-20
I've attached a howto on installing Cacti (the network monitoring tool at [www.cacti.net](www.cacti.net)) on a fresh install of Ubuntu 6.10 Edgy Eft Server.

---

### Post by airtonix on 2007-04-13
um why did you use a bloated piece of software to create a simple howto?

here it is for normal web users...

  	 	 	 	 	 	 	> _**Installing Cacti on Ubuntu Server 6.10 (Edgy Eft)**_
 

 	These instructions are produced from my experiences in installing and configuring Cacti to run on a fresh install of Ubuntu Server 6.10 (Edgy Eft). Needless to say, if your configuration is modified from previous installations, these instructions should be adopted to these changes.
 	I've pulled some material from the slightly dated wiki page at [https://help.ubuntu.com/community/Cacti](https://help.ubuntu.com/community/Cacti) and from several posts on the Ubuntu forums.
 

 [LIST]
[*]Install the 	LAMP server via the alternate installation disk
[*]Setup the 	following partitions
[LIST]
[*]Swap &#8211; 1 		GB and first on second drive
[*]/ - On hda
[*]/home &#8211; 		the remainder of hdb
[/LIST] 	
[*]On first 	boot, edit the sources.list file to include the universe and 	multiverse.
[*]Configure 	/etc/network/interfaces if the installer did not configure it 	automatically
[*]Edit/create 	/etc/resolv.conf with the DNS information for the network if you are 	configuring the server with a static IP.
[LIST]
[*]nameserver 		192.168.1.1
[/LIST] 	
[*]Optional: 	Install *openssh-server* for remote access to complete the 	configurations away from the server.
[*]Apply all 	upgrades, including kernel upgrades. Kernel upgrades will require a 	reboot of the server. You may have to open the graphical component 	of Aptitude and force certain meta packages.
[*]Install 	*screen *package
[*] 	Edit /etc/apache2/apache2.conf and add in support for the .php file 	extension. Restart Apache.
[LIST]
[*] 		grep for AddType in this file and uncomment the two lines you find
[/LIST] 	
[*]Create 	info.php file under /var/www (the web root) to make sure the LAMP is 	correctly working.  	
[LIST]
[*]<?php 		phpinfo() ?>
[/LIST] 	
[*]Remove the 	Apache default page.
[*]Install 	*phpmyadmin* to give a graphical interface to the database
[*]Make sure 	the root access on the MySQL database is NOT password protected.
[*]Create the 	cacti database
[LIST]
[*]*mysqladmin --user=root create cacti*[/LIST] 	
[*]Install the *snmpd* and *php5-cli* packages
[*]Run *php 	-m | grep mysql* If nothing is returned, run this command
[LIST]
[*] 		*sudo dpkg-reconfigure php5-mysql* and answer yes to all three 		questions
[/LIST] 	
[*]Install the 	*cacti* package.
[LIST]
[*]Auto 		configure when prompted
[*]Leave the 		&#8220;Password of your database's administrative user&#8221; prompt empty
[*]Leave the 		&#8220;MySQL application password for Cacti&#8221; prompt empty.
[*]Select 		&#8220;Apache2&#8221; for the &#8220;Web server type&#8221;
[/LIST] 	
[*]Visit 	[http://server.ip.address/cacti/](http://server.ip.address/cacti/) 	to finish the installation
[LIST]
[*]Confirm 		there aren't any missing binaries
[*]Login with 		&#8220;admin&#8221; and &#8220;admin&#8221; the first time.
[*]Change the 		password to match the local administrative password.
[*]**Be 		patient when waiting for the graphs to show up. It usually takes up 		to 5 minutes.**
[/LIST] 	
[*]Create a 	password for the MySQL administrative account
[LIST]
[*]sudo 		mysqladmin -u root password &#8220;password&#8221;
[/LIST] [/LIST] 

---

### Post by marcin_ant on 2007-05-06
In my opinion this "howto" should be considered as a bug report. Because I think that it's just a bug that dbconfig-common cannot create database for cacti and requires user activity to work properly.

It's also unacceptable behaviour because user has no way to choose mysql server (local or remote) or even database name with installation procedure.

And more there are also problems when trying to upgrade or reinstall cacti while it's 'rules' script cannot remove and then create empty database for cacti properly.

---

### Post by Linuturk on 2007-05-06
I would have to disagree. 

If you check Cacti's main site, you still have to follow these basic steps to get it installed.

There are times when you might be migrating cacti off another database, and you don't want the databases erased/created automatically.

---

### Post by marcin_ant on 2007-05-06
And now I will have to disagree.

Ubuntu mission is to provide software that "just work".
And after 'apt-get install cacti' cacti should just work on [http://localhost/cacti](http://localhost/cacti).
But instead of we got information that database configuration failed. And user has to investigate why and needs to know how and where create empty database (also needs to know that this database has to be named 'cacti').

In my opinion this situation is not acceptable. Especially because debconf asks user if should configure database for cacti - and then fails.

It's just a bug for me.

---

### Post by Linuturk on 2007-05-07
Well, I had forgotten about that little gem of the setup. I have to agree with you now.

---

### Post by marcin_ant on 2007-05-07
That's good that you agree with me.

Now, maybe we could find some solution? I did a little investigation and I know that we got a problem in file:

/usr/share/dbconfig-common/internal/mysql

and in function called: dbc_mysql_createuser (line 239)

This function fails to create user and then we also cannot create database because db is not created by root user but by cacti user.

Problem is in line 271

	if dbc_mysql_check_user; then
		dbc_status=nothing
		dbc_logline "already exists"
	else
		l_dbname=$dbc_dbname
-> problem here -> _dbc_nodb="yes" dbc_mysql_exec_file "$l_sqlfile"
		l_ret=$?
		_dbc_nodb=""

		if [ "$l_ret" = "0" ]; then
			dbc_logline "success"
			dbc_logpart "verifying access for $dbc_dbuser@$l_dballow:"
			if ! dbc_mysql_check_user ; then
				l_ret=1
				dbc_logline "failed"
			else
				dbc_status=create
				dbc_logline "success"
			fi
		else
			dbc_logline "failed"
		fi
	fi

we got function dbc_check_user and because we don't have user yet then line marked with "problem here" should be executed. But unfortunately it is not.

If you know how to patch this then please help me to fix this bug.

---

### Post by marcin_ant on 2007-05-27
This howto is outdated.

Currently all these steps mentioned in this howto are not necessary with dbconfig-common 1.8.33 and above which has fix for bug #113310 and now can create database for cacti properly.

So, currently to install cacti you just need to:

apt-get install mysql-server-5.0 (if it's not installed already)

apt-get install cacti

and follow screen instructions. Then go to [http://localhost/cacti](http://localhost/cacti) and enjoy.



Marcin

---

### Post by tehlotus on 2007-06-26
I recognize this thread is a tad old, but I am trying to run apt-get install cacti on edgy 6.10 and the package does not exist.  I also went through several repositories and could not find it.

Anyone have insight to this issue?

$ sudo apt-get install cacti
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package cacti

---

### Post by Linuturk on 2007-06-26
Make sure your extra repositories are enabled.

[https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)

---

### Post by tehlotus on 2007-06-26
My bad, I actually did not apt-get update after I modified my changes.  Found what I was looking for but I do appreciate the URL for Repositories.

---

### Post by Linuturk on 2007-06-27
~$ sudo aptitude search cacti
Password:
p   cacti                                                                        - Frontend to rrdtool for monitoring systems and services                                
p   cacti-cactid                                                                 - Multi-Threading poller for cacti

---

