---
title: "MySQL on Ubuntu 10.04"
date: 2010-08-01
forum: Programming Talk
---

### Post by rensell on 2010-08-01
Hi all, I've recently posted about using my ubuntu server to host MySQL. It currently serves as a file\print and Media Server. I installed MySQL on it. It dual boots with XP pro - no issue with that. 
I have also installed MySQL on the XPpro hard drive. I've noticed extreme lags when I'm running MySQL on the Linux machine. The specs are 1.7 GB and P4 2.8 GHz. I know it's not "super" but I don't have any lag when running the XP machine. Comparing the XP "server" as when I use localhost, the speed seems the same. But, when Linux is running MySQL is to slow to even support the application.

does anyone have any suggestions? When I use Workbench, connected to Linux the Memory stays at about 24%. So it seems MySQL is not getting enough resource from the OS, but I'm far to new to Linux.

Thank you for all help.

-R

---

### Post by rensell on 2010-08-01
Now that I'm working on this tonight, I'm having further issue with not even connecting to the SQL server. When attempting to open my connection I get an "Unable to connect to connect to to any of specified MySQL Hosts" I'm connecting with a User that I know has access, the UN and Password are correct, I've tried multiple time. Sometimes a restart will fix the problem, sometimes it does not. Any ideas? I've attempted to uninstall MySQL and the system just "hangs" during the process, but I was able to reinstall all the MySQL packages (using snaptic), but did not fix it at all. I'm tempted for a complete reinstall - OS and everything. Think it'd help?

-R

---

### Post by iMisspell on 2010-08-01
_[mysqltuner]("http://www.ubuntugeek.com/mysqltuner-check-your-mysql-server-performance.html")_ helped me out in the past.

[edit]
The mysqltuner suggestion was for your main post, not your second post here.

_

---

### Post by evstevemd on 2010-08-02
> **rensell said:**
> Now that I'm working on this tonight, I'm having further issue with not even connecting to the SQL server. When attempting to open my connection I get an "Unable to connect to connect to to any of specified MySQL Hosts" I'm connecting with a User that I know has access, the UN and Password are correct, I've tried multiple time. Sometimes a restart will fix the problem, sometimes it does not. Any ideas? I've attempted to uninstall MySQL and the system just "hangs" during the process, but I was able to reinstall all the MySQL packages (using snaptic), but did not fix it at all. I'm tempted for a complete reinstall - OS and everything. Think it'd help?

-R
Reinstall after removing all config stuffs.
**sudo apt-get purge [COLOR=Red]package_name_goes_here[/COLOR]**

---

### Post by rensell on 2010-08-02
I've tried ```
sudo apt-get purge mysql-server-5.1
```, but it seems to be "stuck" on "Removing mysql-server-5.1

```
User@Computer:~$ sudo apt-get purge mysql-server-5.1
[sudo] password for User:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libcurses-perl libnet-daemon-perl libhtml-template-perl libdbi-perl
  mysql-client-core-5.1 libdbd-mysql-perl libvncserver0 mysql-client-5.1
  mysql-common tk libcurses-ui-perl libplrpc-perl mysql-server-core-5.1
  libmysqlclient16
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  mysql-server-5.1*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 15.0MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 115439 files and directories currently installed.)
Removing mysql-server-5.1 ...

```

been sitting there for about 45 minutes now. Is that normal? I know when I've installed stuff in the past, it was always displaying something whether it's information or percentage(s).

-R

---

### Post by Hellkeepa on 2010-08-02
HELLo!

Seems like it has trouble with shutting down the server. You can either wait, and see if it manages to do this, or shut it down manually by using "kill -9 <pid>".

Happy codin'!

---

### Post by rensell on 2010-08-02
Thanks for all your help. I now got mysql completely reinstalled, and it seems to be working consistently. So, now I'm back to my original post, it is still painfully slow - I can't stress how slow the connection is. Workbench still pegs the memory at 14%. I've run mysqltuner and made the suggested changes, I added skip-innodb to the conf file and increased my query_cache - but have noticed NO difference. I just took my XP conf and edited the paths and still have to wait a long time for the connection(s).

I am using the EXACT same setting on the EXACT same system - just using Ubuntu vs XP - same version of MySQL (with the exception of windos\linux)

Any other ideas? I'd really like to continue replacing my windows servers with linux, but I can't with this speed.

-R

---

### Post by rensell on 2010-08-02
To quantify the speed difference, I timed my login script that uses the entered username and password to connect to MySQL and get a row of data from a database using the given U\N that includes First and Last Name, a color code, and 7 boolean variables and stores them in the program variables.

From the time I click "Play" in visual basic 2010 to the time I'm logged in:

Ubuntu: 12 seconds
XP: 2 Seconds

10 second difference just for login - with only about 5 usernames on each machine and no one else connected.

---

### Post by iMisspell on 2010-08-03
> **rensell said:**
> From the time I click "Play" in visual basic 2010 to the time I'm logged in:

Ubuntu: 12 seconds
XP: 2 Seconds

Im no SQL pro by any means, but maybe more is going on here.
How are you running a VB app from inside Ubuntu ?
I dont think wine or vbox would cause a 10 sec delay, but they are another obstacle/variable to consider.

Maybe trying to narrow down the problem and test with only the bare-bones would be better.

Can you run the tests, on both machines from the MySQL command line ?

_

---

### Post by Some Penguin on 2010-08-03
You should enable any slow-query logging first to determine where the time is actually being spent.  Also, verify that you have ported not only the schema but all relevant indices.

---

### Post by rensell on 2010-08-03
I'm running VB from my Laptop - I program using Visual Studio 2010 on XP Pro. But my server that hosts mySQL is linux (I hope - pending this issue is resolved) I've enabled slow query queue but it doesn't seem to catch anything. Is there a setting to set somewhere that give Mysql more system resources? That is what it seems like is the issue. I'm running workbench on my XP laptop and it says the linux memory is about 15% and when I boot my server with XP it stays in the 90% range.

running query from terminal (using putty) takes 0.02 seconds to return the same exact query ```
SELECT * FROM Credentials WHERE UName ='myuname';
```

---

### Post by rensell on 2010-08-04
Tried some further testing tonight. I created a virtual box VM running Ubuntu Server 10.04 (Hosted on my XP Pro laptop) and my program was quick - like it should be. I did a clean install of server 10.04 on my server box and used the same settings that were used on the VM and it has the same lag as originally. I'm confused as to why Linux is taking such a long time. I've run my code step-by-step and have found that it is the connect command that seems to take a while.

-R

---

### Post by Some Penguin on 2010-08-04
Hmmm.  This is ancient, but possibly relevant:

[http://bugs.mysql.com/bug.php?id=10461]("http://bugs.mysql.com/bug.php?id=10461")

---

### Post by rensell on 2010-08-04
That seems to have fixed my issue. However, workbench still pegs the memory at 37%. I don't want to deploy this is my actually working environment and not be able to handle the work load. Any input on the accuracy of the memory graph of Workbench?

Thanks again everyone - it's always something so simple to fix such "big" issues.

-R

---

### Post by fungiblename on 2010-11-23
> **Some Penguin said:**
> Hmmm.  This is ancient, but possibly relevant:

[http://bugs.mysql.com/bug.php?id=10461]("http://bugs.mysql.com/bug.php?id=10461")

Thanks! That actually sped things up a bit for my on my local 10.04 development box. I still don't understand why I can access my remote (by several hundred miles) 8.04 box dramatically faster than I can access my local box from itself (everything is set to run from 127.0.0.1, as my PHP-based CMS seems to need an IP address for the MySQL server), but at least the local box has somewhat tolerable performance now.

Was there some big performance regression from mysql 5.0 to 5.1 (at least in the versions that are installed by default on 8.04 and 10.04)?

I read in another thread something about compiling a custom kernel to get better mysql performance, but that seems a bit extreme to me, particularly for a local development machine that is also used for other things....

---

### Post by MJae on 2011-05-16
> **evstevemd said:**
> Reinstall after removing all config stuffs.
**sudo apt-get purge [COLOR=Red]package_name_goes_here[/COLOR]**

Thank you much. This is my first time with MySQL and I immediately had a problem - with the 'root' password. It wasn't my root password that I forgot but the root password for MySQL. I tried reinstalling but it didn't work. Apparently, I had to use purge. Thanks a lot. I was almost ready to stop trying.

This is why I love Ubuntu Forums.

---

