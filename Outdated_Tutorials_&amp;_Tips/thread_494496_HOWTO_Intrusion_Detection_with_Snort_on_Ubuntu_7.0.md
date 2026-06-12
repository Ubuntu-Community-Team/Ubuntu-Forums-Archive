---
title: "HOWTO: Intrusion Detection with Snort on Ubuntu 7.04(Feisty) - Part I"
date: 2007-07-06
forum: Outdated Tutorials &amp; Tips
---

### Post by darkog on 2007-07-06
**_Introduction_**
This document describes the procedures involved in how to install, setup, and 
compile the latest version of Snort intrusion detection software on Ubuntu 
GNU/Linux 7.04. Based on the current version of Snort 2.6.1.5.

It is assumed that the user is competent with basic GNU/Linux Unix commands, 
basic mySql commands, and is capable of installing Ubuntu Linux on a computer.

**_A) Ubuntu Installation, Disk Partitioning, & User Setup_**
Download the current version of Ubuntu 7.04 ISO image. Burn the ISO to CD 
media. Set your computer BIOS to boot from CD-ROM first and boot the computer. 

Select "Start or install Ubuntu" and press [Enter] and follow the on screen 
instructions until you get to the hard drive partitioning screen.

Once you get to the partitioning menu, select "Manual" and click "Forward".

Click "New partition table" and click "Continue" to delete all existing 
partitions.

Create the following partitions manually:

[HTML]
Size        Type        Mount point
-------     --------     ----------
100mb        ext3       /boot
1024mb       swap      none
10240mb      ext3      /var
10240mb      ext3      /
[/HTML]

Leave everything else unused. The goal here is to separate your 
/var partition from the rest of the file system so that the snort logs don't 
eat up all your disk space.

For this document, we are going to keep it simple and use "snort" as the user 
name and password. 

**** DO NOT DO THIS IF THIS MACHINE WILL BE EXPOSED TO THE INTERNET ** **

For obvious reasons. Use a complex password. I would also change the user name
to something less obvious. 

For username, type "snort" without quotes.
For password, type "snort"  without quotes.

Click forward to continue and complete the Ubuntu OS install.

**_B) Install Pre-requisites_**
Login to the computer and open a Terminal window. From here on end, all lines 
starting with $ are typed by user.

Install C compiler prerequisites
```
$ sudo apt-get install gcc g++ -y
```

Install libpcap prerequisites
```
$ sudo apt-get install libpcap-dev libpcre3 libpcre3-dev -y
```

Install MySQL prerequisites
```
$ sudo apt-get install mysql-server libmysqlclient-dev -y
```

**_C) Download Snort & Snort Rules_**
Create a new folder in your home folder called "temp".
```
$ mkdir /home/snort/temp
```

Download the latest version of Snort and Snort rules from [www.snort.org](www.snort.org). Just 
register -- you will need it to get the rules anyway. The latest versions 
are snort-2.6.1.5.tar.gz and snortrules-snapshot-CURRENT.tar.gz.

Place both files into the temp folder and un-tar them.
```
$ tar -xzvf snort-2.6.1.5.tar.gz
$ tar -xzvf snortrules-snapshot-CURRENT.tar.gz
$ mv snort-2.6.1.5 snort

```
Remove unneeded files.
```
$ rm snort-2.6.1.5.tar.gz
$ rm snortrules-snapshot-CURRENT.tar.gz

```
You should have a clean folder structure with the following folders:
[i]
/home/snort/temp/snort
/home/snort/temp/so_rules
/home/snort/temp/doc
/home/snort/temp/rules
[/i]

**_Setup mySQL Database_**
Create the snort database.
```
$ sudo mysql
$ mysql> create database snort;
$ mysql> grant CREATE,INSERT,UPDATE,DELETE,SELECT on snort.* to snort@localhost;

```
Set the user name and password we used earlier. Once again, you have to change this to 
something complex if this is going on the net.

```
$ mysql> set password for snort@localhost = password('snort'); 
```

Check that the database exists and check that the tables are empty.
```
$ mysql> show databases;
$ mysql> use snort;
$ mysql> status;
$ mysql> show tables;
$ mysql> exit;

```
Populate the snort database with the correct mySQL table layout.
```
$ cd /home/snort/temp/snort/schemas
$ mysql -p snort < create_msql
[enter password]

```

Check to that there are tables are in the database.
```
$ mysql -p
$ [enter password]
$ mysql> use snort;
$ mysql> show tables;
$ mysql> exit;

```
You should see new database tables. You are now ready to compile, install, and configure snort.

**_Snort compilation, installation, and configuration_**
Configure snort. You are going to install it in the traditional /opt folder. 
```
$ cd /home/snort/temp/snort
$ ./configure --with-mysql --prefix=/opt/snort
$ sudo make
$ sudo make install

```

** Optional: Install tree program. I like it and think it's useful.
```
$ sudo apt-get install tree 
```

Check to see that snort is installed.
```
$ tree /opt/snort
```

Create the folders where to store the configs, rules, logs.
```
$ sudo mkdir /etc/snort
$ sudo chown snort:snort /etc/snort
$ sudo mkdir /var/log/snort
$ sudo chown snort:snort /var/log/snort
$ mkdir /etc/snort/rules
$ cd /home/snort/temp/snort

```
Copy the necessary etc files.
```
$ cd /home/snort/temp/snort/etc
$ cp *.config *.conf *.map sid generators /etc/snort

```
Copy the rules and docs.
```
$ mv doc rules /etc/snort
```

Setup the conf file
```
$ cd /etc/snort
$ nano snort.conf

```
Setup you home network. Use CIDR. 
```
$ var HOME_NET [your subnet]
```

Setup your external network.
```
$ var EXTERTNAL_NET !$HOME_NET
```

Specify the path to rules.
```
$ var RULE_PATH	/etc/snort/rules
```

Fix the dynamic engine and processor paths.
```
$ dynamicpreprocessor directory /opt/snort/lib/snort_dynamicpreprocessor/
$ dynamicengine /opt/snort/lib/snort_dynamicengine/libsf_engine.so

```
Setup the mysql and logging options.
```
$ output database: alert, mysql, user=snort, password=snort, dbname=snort host=localhost
```


**_Testing_**
You want to test to make sure that your have installed and configured Snort 
correctly.

Open two terminal windows. In one you will look at the log files and 
in the other you will launch and test the sort.

```
$ ls /var/log/snort -la
```

You should see nothing in that folder.

```
$ sudo /opt/snort/bin/snort -c /etc/snort/snort.conf -i eth0
```

Check that new log files are created. You should see the files alert 
and snort.log.something..something..
```
$ ls /var/log/snort -la
```

Watch the alert files in real time as you attach the machine. 
```
$ sudo tail -f /var/log/snort/alert
```

From a second machine, launch a port scan using Nmap or some other scanning tool. 
You should see the alert log populate with your attack.

Remove C compilers
```
$ sudo apt-get remove gcc g++ -y
```

**_Conclusion_**
You have compiled, installed and configured the latest version of Snort on 
Ubuntu. You can launch as a daemon manually or via start up script by running:
```
$ sudo /opt/snort/bin/snort -c /etc/snort/snort.conf -i eth0 -D
```

If there is interest, I can do a Part 2 on how to setup the web based display 
console BASE so that you can look at the logs from a nicer interface. 

Snort isn't going to do much without proper rules and making it do something 
when it does detect something. Things it can do is send you e-mail messages, 
make changes to other devices via SNMP, and other things. These topics 
are beyond the scope of this HOWTO. You should check the documentation at 
[http://www.snort.org](http://www.snort.org) and books that focus on Snort.

---

### Post by tegwilym on 2007-07-10
Thanks for the guide!  I seem to have gotten it running without much trouble.  Yes, please do post a guide for BASE.  I'll try that on my own for now, but yours worked well.  :)

Tom

---

### Post by n_dimos on 2007-07-16
Great guide. Thanks, please continue with the BASE system setup.

---

### Post by mikka_22 on 2007-07-19
hi..please i need your help...i followed your instructions..but i get this error when i did make:

make[3]: se sale del directorio `/usr/local/src/snort-2.6.0/src'
make[2]: se sale del directorio `/usr/local/src/snort-2.6.0/src'
Making all in doc
make[2]: se ingresa al directorio `/usr/local/src/snort-2.6.0/doc'
make[2]: No se hace nada para `all'.
make[2]: se sale del directorio `/usr/local/src/snort-2.6.0/doc'
Making all in etc
make[2]: se ingresa al directorio `/usr/local/src/snort-2.6.0/etc'
make[2]: No se hace nada para `all'.
make[2]: se sale del directorio `/usr/local/src/snort-2.6.0/etc'
Making all in templates
make[2]: se ingresa al directorio `/usr/local/src/snort-2.6.0/templates'
make[2]: No se hace nada para `all'.
make[2]: se sale del directorio `/usr/local/src/snort-2.6.0/templates'
Making all in contrib
make[2]: se ingresa al directorio `/usr/local/src/snort-2.6.0/contrib'
make[2]: No se hace nada para `all'.
make[2]: se sale del directorio `/usr/local/src/snort-2.6.0/contrib'
Making all in schemas
make[2]: se ingresa al directorio `/usr/local/src/snort-2.6.0/schemas'
make[2]: No se hace nada para `all'.
make[2]: se sale del directorio `/usr/local/src/snort-2.6.0/schemas'
Making all in rpm
make[2]: se ingresa al directorio `/usr/local/src/snort-2.6.0/rpm'
make[2]: No se hace nada para `all'.
make[2]: se sale del directorio `/usr/local/src/snort-2.6.0/rpm'
Making all in m4
make[2]: se ingresa al directorio `/usr/local/src/snort-2.6.0/m4'
make[2]: No se hace nada para `all'.
make[2]: se sale del directorio `/usr/local/src/snort-2.6.0/m4'
make[2]: se ingresa al directorio `/usr/local/src/snort-2.6.0'
make[2]: No se hace nada para `all-am'.
make[2]: se sale del directorio `/usr/local/src/snort-2.6.0'
make[1]: se sale del directorio `/usr/local/src/snort-2.6.0'

i have ubuntu feisty, are those errors?? what can i do? please help me!! thanks a lot!

---

### Post by tegwilym on 2007-07-23
I'll admit that I'm a newbie to this intrusion detection stuff.  I have Snort, Oinkmaster, BASE, Nessus and Ntop up and running on my server.  My computer is exposed to the raw and filthy internet through a DMZ port on the router.  I should see some action on the BASE application, but there isn't anything going on.  Is this correct?  Or what should I be seeing or looking for next?

I once had Windows 2000 pro installed on this computer doing the same thing on the DMZ port.  After a day, the thing was totally choked with viruses - even with a current anti-virus application running, that I had to format it and start over.   I know there should be something going on out there, but just not sure where to g next with this.

Tips? Suggestions?  Ideas? 
...or just point and laugh since I mentioned "Windows",  I'm laughing with you!  :)

Tom

---

### Post by darkog on 2007-07-23
> **tegwilym said:**
> I'll admit that I'm a newbie to this intrusion detection stuff.  I have Snort, Oinkmaster, BASE, Nessus and Ntop up and running on my server.  My computer is exposed to the raw and filthy internet through a DMZ port on the router.  I should see some action on the BASE application, but there isn't anything going on.  Is this correct?  Or what should I be seeing or looking for next?


nope. does not sound correct. make sure snort is actually logging. do the simple ICMP traffic test from one of your other machines to the snort machine -- make sure it's logging. 

if test passes, then check to see what your nic is actually seeing. use [tcpdump]("http://www.owlriver.com/tips/tcpdump-tech/") or ethereal.

---

### Post by tegwilym on 2007-07-24
It is putting a bunch of stuff in the /var/log/snort/alert file that looks like this - 
[[INDENT]**] [116:4:1] (snort_decoder): Ipv4 Options found with bad lengths [**]
[Priority: 3] 
07/24-10:15:38.869768 192.168.5.23 -> 224.0.0.22
IGMP TTL:1 TOS:0xC0 ID:23717 IpLen:24 DgmLen:40

[**] [116:4:1] (snort_decoder): Ipv4 Options found with bad lengths [**]
[Priority: 3] 
07/24-10:15:39.389724 192.168.5.23 -> 224.0.0.22
IGMP TTL:[/INDENT]1 TOS:0xC0 ID:23718 IpLen:24 DgmLen:40

So it appears to be doing something.  On my computer at home, I have a much larger list of things like this since it's exposed to the internet directly through the DMZ.

I just don't see anything through the BASE application though.

T.

---

### Post by darkog on 2007-07-24
> **tegwilym said:**
> It is putting a bunch of stuff in the /var/log/snort/alert file that looks like this - 
[[INDENT]**] [116:4:1] (snort_decoder): Ipv4 Options found with bad lengths [**]
[Priority: 3] 
07/24-10:15:38.869768 192.168.5.23 -> 224.0.0.22
IGMP TTL:1 TOS:0xC0 ID:23717 IpLen:24 DgmLen:40

[**] [116:4:1] (snort_decoder): Ipv4 Options found with bad lengths [**]
[Priority: 3] 
07/24-10:15:39.389724 192.168.5.23 -> 224.0.0.22
IGMP TTL:[/INDENT]1 TOS:0xC0 ID:23718 IpLen:24 DgmLen:40

So it appears to be doing something.  On my computer at home, I have a much larger list of things like this since it's exposed to the internet directly through the DMZ.

I just don't see anything through the BASE application though.

T.

did you setup BASE? are you logging to a db? 

here is the snip from another HOWTO i am working on. It's not  ready yet. But perhaps it will help.

```

Setup BASE
==========

Install php graphing prerequisites.
$ sudo apt-get install php-pear php-image-graph -y

Setup and enable Image-Color
$ sudo pear install Image_Color

Configure the base_conf.php file.
$cd /var/www/base
$ cp base_config.php.dist base_config.php

$ set baseurl path to ''
$ set dblib path to '/var/www/adodb'

$ alert_dbname to 'snort'
$ alert_user to 'snort'
$ alert_password to 'snort' 

$ sudo /etc/init.d/apache2 restart

Open web browser and goto http://<snort_ip_address> and type your user name 
and password to enter the site.

- Click &#8220;setup_page&#8221;
- Click "Create "BASE AG"
- Click to go back to main page



```

---

### Post by tegwilym on 2007-07-24
Yeah, I do have BASE installed and running.  I'm just confused (or don't know what I'm doing more likely) since I don't see anything happening when look at BASE with the browser.   0% on all the things on the first page.  But there is some stuff getting logged though.  I figured there should b more action going on in BASE rather than sitting there at 0 all the time. 
I do have MySQL set up with a Snort database running.  

Tom

---

### Post by darkog on 2007-07-24
try an nmap scan against the snort box. you should see entries in the port scan section.

---

### Post by dynamethod on 2007-09-27
when trying this command:

```
mysql -p snort < create_mysql
```

i get this:

```
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

```

i dont understand, im putting in the correct password yet it doesnt give me access?

---

