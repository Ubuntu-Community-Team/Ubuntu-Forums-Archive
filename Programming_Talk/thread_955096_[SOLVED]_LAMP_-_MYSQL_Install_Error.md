---
title: "[SOLVED] LAMP - MYSQL Install Error"
date: 2008-10-21
forum: Programming Talk
---

### Post by TekNullOG on 2008-10-21
OK, I hate to post my problem and to answer it myself but I wanted to share a problem that annoyed me for a long time and I finally got it to work so I decided to share with all in hopes it helps someone else.

Basically, I had to install LAMP for my PHP class.

I fallowed detailed steps in the Ubuntu Wiki but I kept getting the same problem.

After Installation I would read:
```

 * /etc/init.d/mysql: WARNING: /etc/mysql/my.cnf cannot be read. See README.Debian.gz
 * Starting MySQL database server mysqld                              [fail] 

```

So many people recommended removing with Purge and Reinstalling but this did not help. It almost made it worst because then it wouldn't even finish the installation and every time I did system updates (even once uninstalled), I would get this message:

```

E: mysql-server-5.0: subprocesE: mysql-server-5.0: subprocess post-installation script returned error exit status 1

```

Tonight, I decided to reinstall again because the error message was annoying and I need LAMP working for my next homework.

Again, I got the same problem and did a lot of research. So many solutions out there but none worked for me.

The one that worked for the most people is the fallowing:

> 
This should fix your MYSQL installation / reinstallation issues, if your getting "dpkg: error processing mysql-server-5.0 (--configure):
" or other similar error.

If you have downloaded an already tried to install make sure all your mysql packages are removed. This step can be skipped, but I found when I had this issue I tried many different installation commands and wanted to remove all. The following command will remove MYSQL and MYSQL 5.0.

sudo apt-get autoremove --purge mysql-server mysql-server-5.0
(^if root remove sudo)

Now reinstall with the following command, which will install the latest MYSQL

sudo apt-get install mysql-server
(^if root remove sudo)

You will probably get the same error again, but don't dispair. Change to directory /etc/mysql/ and edit the my.cnf file by doing the following.

cp my.cnf my.cnf.bak
vi my.cnf

Once you have the file open navigate down till you see the bind-address setting. You may see two but only one should be un-commented. Change the bind-address setting so it looks like bind-address = 0.0.0.0 and save the file.

Now we will finish configuration of MYSQL by using the following command.

sudo dpkg --configure -a
(^if root remove sudo)

This command will continue all unfinished software auto configurations, in this case MYSQL. The database should start this time.

Edit the my.cnf file again to change the bind-address to the IP address of choice (127.0.0.0 for local only) or external interface IP address. Issue command to restart MYSQL and you should be good to go.

sudo /etc/init.d/mysql restart
(^if root remove sudo)


Obviously, with my luck, I didn't even have a **my.cnf** file so my installation is really quiting before the end of the install.

Then I fell on someone that asked a really simple question to another user so I humored him and tried it out myself:

[http://ubuntuforums.org/archive/index.php/t-434491.html](http://ubuntuforums.org/archive/index.php/t-434491.html)

[QUOTE=taurus]
What happens when you run these commands from a terminal?

Applications -> Accessories -> Terminal
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude upgrade
[/QUOTE]


My results were the fallowing:

sudo dpkg --configure -a  -->  Didn't solve the problem.
sudo aptitude update --> All my packages were up to date
sudo aptitude upgrade --> **Voila!!! Aptitude Upgraded and it immediately began to complete the installation of MySQL**

```

**user@computer:**/etc/mysql/conf.d$ sudo aptitude upgrade
W: The "upgrade" command is deprecated; use "safe-upgrade" instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following partially installed packages will be configured:
  mysql-server mysql-server-5.0 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up mysql-server-5.0 (5.0.51a-3ubuntu5.1) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
Reloading AppArmor profiles : done.
 * /etc/init.d/mysql: WARNING: /etc/mysql/my.cnf cannot be read. See README.Debian.gz
 * Starting MySQL database server mysqld                                 [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.

Setting up mysql-server (5.0.51a-3ubuntu5.1) ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      


```

This solution seems really easy, especially when I compare to the dozens of other solutions that I tried but it is funny how the most obviously problems are sometimes the hardest to solve. LAMP finally works!

---

