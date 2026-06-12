---
title: "HowTo: Install Oracle Application Server 10g Release 2"
date: 2006-05-10
forum: Outdated Tutorials &amp; Tips
---

### Post by dirkoneill on 2006-05-10
I had a little bit of trouble installing the oracle application server release 2 so I thought that I would share my install process.

1. Create an 'oracle' user and 'oracle' group.
2. For user 'oracle' add 'root' to secondary list of groups
3. ```
sudo chmod 775 /opt 
```
4. Log out and log back in as oracle user
5. To fix a missing 'ntcontab.o', do the following:```
sudo apt-get install gcc make manpages-dev autoconf automake libtool flex bison gdb gcc-2.95-doc binutils 
```
6. ```
sudo apt-get install libdb1-compat
```
7. Download the Oracle Application file 'as_linux_x86_core_101202.cpio' from oracle
8. Extract in local user directory ```
 cpio -i --file=/<path>/as_linux_x86_core_101202.cpio -d
```
9. ```
 cd Disk1
```
10. ```
./runInstaller -ignoreSysPrereqs
```
11. At the end of the install near 95% if is says that it cannot verify that the instance is running(message: <path>/opmn/bin/opmnctl start), hit continue.
12. That's it. Let it do it's initialization process. When it is finished exit.
13. Go to [http://localhost:1156](http://localhost:1156) for the admin console.
14. There still needs to be an entry in /etc/intit.d but I have not done that yet. Soon, I will update the post with the file.

---

### Post by GhodMode on 2007-01-24
If you think that it'll be this easy to install Oracle 10g Application Server  on Ubuntu Linux you're crazy!  Oracle 10g Application Server is a complex product and there's a good reason that's it's only certified on...

... Oh! ... wait a minute ... It's done... Never mind :D

Dude, you Rock! :)

Success using this method with Oracle Application Server 10g v10.1.2.0.2 on Kubuntu Edgy (6.10).

--Ghodmode

---

### Post by dirkoneill on 2007-01-24
I am glad that I could give something back to the community and more immportantly, that it worked for someone else. It is also good to see that this method is still working in 6.10.

---

### Post by philh99 on 2007-02-28
Hi, 

Unfortunately, this didn't work for me.
Basically, I'm trying to get the http server for oracle going for huse with htmldb.
The installer for http and htmldb stops at 38% and the last message in the log file is the fast copy on oracle.jdk.1.4.2.0.2.

Any ideas????

I tried the standalone http from the companion CD as well and this stops at this message also.

Ta.

---

### Post by bodhi.zazen on 2007-03-02
Nice How-to

This thread has been added to the UDSF wiki.

[Oracle_Application_Server_10g](http://doc.gwos.org/index.php/Oracle_Application_Server_10g)

---

### Post by benjaminzsj on 2007-03-11
Do I have to add a new user "oracle"? If so, can I access Oracle db with my everyday account?

---

### Post by megazayed on 2008-07-23
plz i want to know how can i do this step : 



2- For user 'oracle' add 'root' to secondary list of groups



plz help me  
  

thanks

---

### Post by Iftikhar on 2010-02-19
I got into trouble with reports server, all other services are and remain up except the reports server. Here's the remedy:
Quick Fix:

Ubuntu 9.10
download xorg-x11-libs-compat-6.8.2-1.EL.33.0.1.i386.rpm & install with rpm -ivf --nodeps
cp -rv /usr/X11 R6/lib/* /usr/lib/
cp -rv /usr/X11 R6/lib/* /lib/

Crude but works

---

