---
title: "HOWTO: Snort Mysql Base"
date: 2006-03-16
forum: Outdated Tutorials &amp; Tips
---

### Post by djhedges on 2006-03-16
I finally created a new guide for Feisty which is very similar but if anything easier.
[http://ubuntuforums.org/showthread.php?t=483488]("http://ubuntuforums.org/showthread.php?t=483488")

This guide will show you how to install the IDS system snort.  Have snort log to a mysql database.  Then be able to access the information in that database with Base which you can access through apache. 

Most of the information from this guide I learned from Patrick Harper's Centos guide.  I would recommend taking a look at it even if your installing snort on Ubuntu.  [http://www.snort.org/docs/setup_guides/snort_base_SSL.pdf](http://www.snort.org/docs/setup_guides/snort_base_SSL.pdf)

First edit /etc/apt/sources.list and Uncomment these 2 lines.  (My file actually has more uncommented so I'm not sure which sources you'll actually need.  If you run into problems try uncommenting more.  You can always change it back when your done.)

> deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

Next update
> sudo apt-get update

Install snort with mysql support
> sudo apt-get install snort-mysql

The ubuntu will bring up a configuration dialog and a network that you can use.  I replaced this with any so it will log all traffic.  Next it'll ask if you want to set snort to log to a mysql server.  For now we'll say no because we haven't set mysql up yet.  

Before testing snort I'm going to go ahead and install oinkmaster and get the latest rules.  Oinkmaster is a program that you can use to automatically fetch snort rules.

> sudo apt-get install oinkmaster

Now you'll need to edit the oinkmaster config file which is located /etc/oinkmaster.conf  I would recommend going to s[nort.org]("https://www.snort.org/pub-bin/register.cgi") and registering so you can obtain an oinkcode.

Replace
> url = [http://www.snort.org/dl/rules/snortrules-snapshot-2_2.tar.gz](http://www.snort.org/dl/rules/snortrules-snapshot-2_2.tar.gz)
with
> url =http://www.snort.org/pub-bin/oinkmaster.cgi/5a08f649c16a278e1012e1c84bdc8fab9a70e2a4/snortrules-snapshot-2.3.tar.gz
just make sure you replace 5a08f649c16a278e1012e1c84bdc8fab9a70e2a4 with your oink code.  Pay attention to the version of snort your using.  To find out type snort -V.  My example above is version 2.3.

Now to test oinkmastser
> sudo oinkmaster -o /tmp/
ls /tmp
The -o switch is for output directory.  You should see several .rules files in /tmp now.

If everything works out alright then update your snort rules
> sudo oinkmaster -o /etc/snort/rules/
A good idea is to add oinkmaster to a cron job to update your rules automaticlly.  I'm a bit rusty with crons so I'm gona leave that out of this how to until I read up on them again.  ;) 

Now edit the snort config file
> sudo vi /etc/snort/snort.conf
In the begging there are a couple of variable you should check on.  The default should work fine.  Read over the config file, the comments provide more information about the preprocessors and other snort options.
> var HOME_NET any

var RULE_PATH /etc/snort/rules
At the very end you'll find the rules list.  Here you can uncomment additional rule sets depending on what rules you want to monitor.

Nows the time to fire snort up using the snort config file.
> sudo snort -c /etc/snort/snort.conf
By default snort logs alerts to /var/log/snort/alert

To test snort I used another computer and did a scan with nmap.
> sudo nmap -sS Your_IP_Address
If you look through /var/log/snort/alert you should see some port can activity.  Do a search on the file.  If its empty then something is wrong.
> sudo cat /var/log/snort/alert

Now to install mysql
> sudo apt-get install mysql-server
Theres a couple of questions apt asks for and I just used the default by pressing enter a couple of times.

Edit the snort config file again so we can change where snort logs its outputs
> sudo vi /etc/snort/snort.conf
Comment out so it looks like the following.  Mine was line 512.
> # output log_tcpdump: tcpdump.log
Uncomment, line 529
> output database: log, mysql, user=root password=test dbname=db host=localhost
For this guide I'm going to use snort as my user, password and database.  I would recommend you use something different, just note what it is.  If you are logging to aother mysql server then change localhost to what ever ip the server is.
> output database: log, mysql, user=snort password=snot dbname=snort host=localhost

I don't know anything about mysql.  I followed Patrick's guide word for word.  Download snort from snort.org and extract it.  Since my version of snort was 2.3.2 thats what I downloaded from snort.org.  Then we'll set up a database for snort.
> mysql -u root
set password for root@localhost=password('PICK_A_PASSWORD');
create database snort;
grant insert,select on root.* to snort@localhost;
set password for snort@localhost=password('PASSWORD_SNORT_CONF');
grant create,delete,insert,select,update on snort.* to snort@localhost;
grant create,delete,insert,select,update on snort.* to snort;
exit
Pay attention to the semicolons ;

Create the tables
> mysql -u root -p < ~/snort-2.3.2/schemas/create_mysql snort

Check the database
> mysql -u root -p
show databases;
use snort
show tables;
exit

You should be able to fire up snort with no problems.
> sudo snort -c /etc/snort/snort.conf

*I Updated this section and found adodb in the repository
Install apache our webserver and php with mysql & adodb
> sudo apt-get install apache2 php5-mysql libphp-adodb

Download base
[http://sourceforge.net/project/showfiles.php?group_id=103348&package_id=128846&release_id=384975](http://sourceforge.net/project/showfiles.php?group_id=103348&package_id=128846&release_id=384975)
Move base to /var/www, extract and delete the archive.
> sudo mv base-1.2.2.tar.gz
cd /var/www
sudo tar -xvzf base-1.2.2.tar.gz
sudo rm base-1.2.2.tar.gz
mv base-1.2.2 base


Edit the base configuration
> sudo cp base/base_conf.php.dist base/base_conf.php
sudo vi base/base_conf.php
$Base_urlpath = &#8220;/base&#8221;
$Dblib_path = &#8220;/usr/share/adodb/&#8221;;
Change line 85 and so on to match your mysql database.  Such as the username, password etc.

I was expecting this to work but for some reason it didn't.  I fired up firefox and went to localhost and when I clicked the folder base it kept trying to download a file.  I tried restarting apache but the only thing that actually worked was a reboot.  Go figure.

If you goto [http://localhost/base](http://localhost/base) you should see a link to the setup page.  Click it and then click Setup Base AG.  Now click home and Base should be up an running.  

Now in order to get the graph to work
> sudo apt-get install php5-gd php-pear
sudo pear install Image_Color
pear install Image_Canvas-alpha
pear install Image_Graph-alpha

Restart Apache and make sure snort is running
> sudo /etc/init.d/apache2 restart
sudo /etc/init.d/snort start

For some reason when I was trying to install Image_Color it was missing a dependency that was already installed.  If you get the same error try the following.
> sudo apt-get remove php5-gd
sudo apt-get install php5-gd

This is my first HOWTO.  Good luck & have fun.

---

### Post by bond00 on 2006-03-29
Thanks for the great tut...I've been looking for a good Snort tutorial for quite a while and this one hits the spot. One question though. 

My router/gateway is configured to forward traffic to the internal server running http, ssh, etc. Whenever an alert from the outside is triggered in Base, the source address is always the router/gateway. This is not extremely helpful for me know who is attacking me. Is there a way to change this? I use awstats and it is able to record the REAL source address of visitors so why should base/snort be able to as well? Thanks for the help.

---

### Post by djhedges on 2006-03-29
It should log outside sources.  If I were you I would look at trying to trip the snort sensor from the outside and see if it only shows your router.  I know when I first setup my sensor up the routers upnp forwarding was logging a lot.  When I ran bit torrent it was logging the external IPs.  I'm assuming your router is using NAT.

You could try creating a simple rule to log ssh connections.  
> sudo vi /etc/snort/local.rules
Make sure local.rules isn't commented in the snort.conf and add the following:  
> alert tcp any 22 <> any any (msg:"SSH Traffic";)
Just be careful because I believe this rule will log each tcp packet that matches port 22.  

After that just connect from an outside IP and see if it's in the log.

---

### Post by bond00 on 2006-03-30
Thanks for the tip.  I just have a few other questions on locking it down a bit more. 

1. - Can I restrict access to only localhost or a certain ip address?
2. - I get alot of alerts that I don't care about. Can I make snort ignore those alerts? My thinking is maybe go into the rules files and comment out lines with rules I don't want. Is that correct?
3. - When I try to start snort from /etc/init.d/snort I get an error saying 

/etc/snort/snort.conf: line 44: var: command not found

I think it's because I installed snort first and then removed it and installed snort-mysql. Snort-mysql's snort.conf has a format of 'var HOME_NET any'. The snort.conf for the original snort has 'DEBIAN_SNORT_HOME_NET=ANY'. I'm assuming the /etc/init.d/snort is from the original snort and not snort-mysql. 

Maybe if someone else is not having this problem, you can checkout the init script and post it so I can copy it. I've looked through the init script and it calls for variables in the original snort format (DEBIAN_SNORT_HOME_NET)...so I'm guessing that's where the error originates because it works fine to start it with

#snort -c /etc/snort/snort.conf
 
Thanks again for the tutorial and help.

---

### Post by djhedges on 2006-04-01
1-Yes you can but I've never really done it myself and I don't exactly know how.  There are two possiblities that you can use though.  Either setup a firewall using Firestarter or Iptables and allow access to port 80 by certian IP addresses.  I googled and found some sites mentioning setting access to apache by IP addresses.  If you read Patrick's Guide he has a section at the end where he demonstrates adding a username and password to the base folder.

2-A problem with any IDS system is false positivies.  You can go in and uncomment rules that you don't want snort to check for.  Something like ICMP maybe a bit useless.  You can also go into the specific rule files themselves.  This gets a little bit more advanced but it'll allow you to comment out specific signatures.  One more option that I know if at the beginning of the snort.conf file.  There a variables which you define your servers such as dns.  By default it's using the $HOME_NET variable.

3-I got some ideas on how to fix let me test somethings.  I did try removing snort-mysql and installing snort.  I couldn't start it w/ the init.d script.  I remove snort and the init.d script was still there.  I then put snort-mysql back on and everything still worked.  It does contain some of those DEBIAN_SNORT_HOME_NET that you mentioned.  

I just removed snort-mysql and delted my script which I recomend you don't do because I can't get it installed again :)  I'm working on it though

---

### Post by djhedges on 2006-04-01
I think I know what broke my snort.  I was trying to find a way to get the latest version of it installed on my server but with no luck.  After removing snort-mysql and I did snort -V and Snort 2.4.4 showed up even though it won't work.  I got back on my laptop and I think I have a fix for ya.  If you do apt-get remove snort-mysql it'll still leave the init script there and if you delete it you won't be able to reinstall snort.

Open synaptic and do a search for snort.  Back up your config file first though.  Mark snort-common and snort-mysql for complete removal.  This will remove the init script and snort config.  Then just install snort-mysql again and you should be good go.  Let me know how it turns out.

---

### Post by bond00 on 2006-04-02
[QUOTE=djhedges]I think I know what broke my snort.  I was trying to find a way to get the latest version of it installed on my server but with no luck.  After removing snort-mysql and I did snort -V and Snort 2.4.4 showed up even though it won't work.  I got back on my laptop and I think I have a fix for ya.  If you do apt-get remove snort-mysql it'll still leave the init script there and if you delete it you won't be able to reinstall snort.

Open synaptic and do a search for snort.  Back up your config file first though.  Mark snort-common and snort-mysql for complete removal.  This will remove the init script and snort config.  Then just install snort-mysql again and you should be good go.  Let me know how it turns out.[/QUOTE]


Thanks! That worked. After completely removing I also had to run "update-rc.d -n -f snort remove" That removed all symlinks. Then a reinstall worked. Thanks again for the great tut.

---

### Post by djhedges on 2006-04-24
threshold.conf is neat config located under /etc/snort that will limit the number of logs snort generates.  This is probably better then commenting out rules because oinkmaster automatically uncomments them.

Its pretty self explanitory.  I just fired up Base in firefox and found a rule that was generating too much traffic such as samba connects.  I'd like to know if someone from the outside was connecting but locally I wasn't worried about this kind of traffic tripping the sensor.  Heres what I added to the config.

> suppress gen_id 1 sig_id 2466, track by_src, ip 192.168.1.0/25

192.168.1.0 covers my network.  Most networks will probably have a 24bit mask instead of 25 though.

---

### Post by stock99 on 2006-06-22
> grant insert,select on root.* to snort@localhost;


there seems sth wrong with this statement. I thought all we ever create is a snort database. root.* seems refer to root database? I don't know much of mysql but quick google give me the syntax :

GRANT priv_type [(column_list)] [, priv_type [(column_list)]] ...
    ON {tbl_name | * | *.* | *db_name.**}
    TO user [IDENTIFIED BY [PASSWORD] 'password']
        [, user [IDENTIFIED BY [PASSWORD] 'password']] ...

can someone verify this?

---

### Post by djhedges on 2006-06-25
[QUOTE=stock99]there seems sth wrong with this statement. I thought all we ever create is a snort database. root.* seems refer to root database? I don't know much of mysql but quick google give me the syntax :

GRANT priv_type [(column_list)] [, priv_type [(column_list)]] ...
    ON {tbl_name | * | *.* | *db_name.**}
    TO user [IDENTIFIED BY [PASSWORD] 'password']
        [, user [IDENTIFIED BY [PASSWORD] 'password']] ...

can someone verify this?[/QUOTE]

I see what your saying but I think line is giving permission to the user snort, how do I put this.  Kinda of like permission to a root directory not so much a root database.  I'm never very good with mysql commands myself but think of it kinda like directories & permissions.

root
|---snort
___|----various tables

If you had no permissions to root then you wouldn't be able to access the sub directories.

---

### Post by stock99 on 2006-06-25
hmm, i follow the instruction but i miss 2 tables 
| base_roles        |
| base_users       |

And this cause me problem when rinning [http://localhost/base](http://localhost/base) , where i got error message :

Database ERROR:Database ERROR:Table 'snort.base_users' doesn't exist


---------------I do have the rest of table after runnung create_mysql-------

+------------------+
| Tables_in_snort  |
+------------------+
| data             |
| detail           |
| encoding         |
| event            |
| icmphdr          |
| iphdr            |
| opt              |
| reference        |
| reference_system |
| schema           |
| sensor           |
| sig_class        |
| sig_reference    |
| signature        |
| tcphdr           |
| udphdr           |
+------------------+
16 rows in set (0.01 sec)


I think there is probably sth wrong with permission setting somehow the base setup script isn't able to create the 2 tables..

---

### Post by stock99 on 2006-06-25
problem solved. I am downloading the lastest base tar.gz file so it has little changes. I need to use the sql file come with the basexxx.tar.gz instead of the one supplied by snort. Plus it doesn't seem to require me to add tose acid_ag table via browser but done via the sql-table-creation script.

---

### Post by Tifred on 2006-06-26
> 
Create the tables

mysql -u root -p < ~/snort-2.3.2/schemas/create_mysql snort

sorry but this command not working for me, anyone to help me ?
```
tifred@ubuntu:~$ sudo mysql -u root -p < ~/snort-2.3.2/schemas/create_mysql snort
bash: /home/tifred/snort-2.3.2/schemas/create_mysql: Aucun fichier ou répertoire de ce type

```
(in english: no such file or directory)

[edit] ok answer is in /usr/share/doc/snort-mysql/Readme-database.deb

---

### Post by antilog on 2006-08-03
Thanks for the How-To.  I got everything installed and running, checked BASE, and it is pristine, no alerts.  I have it installed on a gateway/router/server PC, one nic on a cable modem and another connected to a switch for the internal network.  I tried using nmap to do port scans, tried RDP'ing into a local machine from outside, nothing shows up.

Any ideas?

Thanks again, this community is great.

---

### Post by antilog on 2006-08-04
> **antilog said:**
> Thanks for the How-To.  I got everything installed and running, checked BASE, and it is pristine, no alerts.  I have it installed on a gateway/router/server PC, one nic on a cable modem and another connected to a switch for the internal network.  I tried using nmap to do port scans, tried RDP'ing into a local machine from outside, nothing shows up.

Any ideas?

Thanks again, this community is great.

It looks like it is working.  It is show all kinds of interesting activity that I now get to investigate.

---

### Post by antilog on 2006-08-05
Every time a Windows machine on my network does a Send/Receive for Outlook, it is showing up in the logs as

(portscan) Open Port:

with my gateway as the source and the mail server as the destination, although I don't recognize some of the destinations.

Any ideas

---

### Post by djhedges on 2006-08-05
> **antilog said:**
> Every time a Windows machine on my network does a Send/Receive for Outlook, it is showing up in the logs as

(portscan) Open Port:

with my gateway as the source and the mail server as the destination, although I don't recognize some of the destinations.

Any ideas

I don't know how Outlook works but you could look into it using a port scanner.  I'll give you an example how a port scan works and it might be why snort is picking it up.

If you understand the TCP handshake it'll make sense.  If not google it.  Basicly you send a SYN packet to machine on a specific port.  That machine will usually respond back if its open w/ SYN/ACK or a RST if it's closed.  Normally a computer will finish after the SYN/ACK by sending data and requesting or what ever it needs to do.  A port scan however just stops after the first SYN and never sends anything else.  There are many differnt types of port scans.  If you ever look at how many options nmap has you'll realize this.

As far as the random destinations, I have no idea.  Try googling some of the IPs or do a whois.  It might be something like MSN messenger trying to talk to a server.  If I remember right that silly thing always came on when I use to use outlook express.

---

### Post by djhedges on 2006-08-05
I don't know why I wasn't recieving a e-mail for some of the posts in this thread.  Please make sure that the snort you download is the same version as the one installed.  For example you don't want to try to use snort 2.4 database script while having 2.3 installed.  Or using rules from 2.4 if your snort version is 2.3.

---

### Post by dmccarney on 2006-08-08
I've followed the guide up until the BASE installation, however like you I have run into the problem where it attempts to DOWNLOAD the files when I visit [http://localhost/base/](http://localhost/base/)

Unfortunately reboot has not solved the problem (I have tried several times).  I can't seem to fix it and I have followed the guide to the letter. All PHP files just ask to download.

Any help would be much appreciated. I'm at my wits end.

- Dan

---

### Post by djhedges on 2006-08-08
> **dmccarney said:**
> I've followed the guide up until the BASE installation, however like you I have run into the problem where it attempts to DOWNLOAD the files when I visit [http://localhost/base/](http://localhost/base/)

Unfortunately reboot has not solved the problem (I have tried several times).  I can't seem to fix it and I have followed the guide to the letter. All PHP files just ask to download.

Any help would be much appreciated. I'm at my wits end.

- Dan

It's been awhile since I've messed with snort & base but I remember having a similiar problem.  I don't remember how I fixed it but it does have something to do with your php.  When the php files try to download then it means the server doesn't have php quite working yet.  Trying looking for a similar problem.

---

### Post by dmccarney on 2006-08-09
Problem solved.

I nuked the install and then started fresh. I installed the LAMP bits before I even moved on to the Snort, Oinkmaster and BASE stuff and this time it worked flawlessly.

However, I'd like to point out that you should probably update the bits of your guide pertaining to the ADODB install. The ADODB package that is found in Synaptic for Dapper Drake now installs the package to:

```
/usr/share/php/adodb 
```

Instead of 

```
/usr/share/adodb
```

As found in the guide at the moment.

Thanks for a good Howto!

- Dan

---

### Post by antilog on 2006-08-09
> **dmccarney said:**
> Problem solved.

I nuked the install and then started fresh. I installed the LAMP bits before I even moved on to the Snort, Oinkmaster and BASE stuff and this time it worked flawlessly.

However, I'd like to point out that you should probably update the bits of your guide pertaining to the ADODB install. The ADODB package that is found in Synaptic for Dapper Drake now installs the package to:

```
/usr/share/php/adodb 
```

Instead of 

```
/usr/share/adodb
```

As found in the guide at the moment.

Thanks for a good Howto!

- Dan


Yeah that path tripped me up too.  There were a couple spots where I had to find the proper path.

It is really interesting to see details on the activity hitting my network, worms poking around etc....

---

### Post by djhedges on 2006-08-09
> **dmccarney said:**
> Problem solved.

I nuked the install and then started fresh. I installed the LAMP bits before I even moved on to the Snort, Oinkmaster and BASE stuff and this time it worked flawlessly.

However, I'd like to point out that you should probably update the bits of your guide pertaining to the ADODB install. The ADODB package that is found in Synaptic for Dapper Drake now installs the package to:

```
/usr/share/php/adodb 
```

Instead of 

```
/usr/share/adodb
```

As found in the guide at the moment.

Thanks for a good Howto!

- Dan

When I get some time I'll probably make one for Dapper.  I really want to get a newer snort working though like 2.4 or 2.6.  This guide was done in Hoary Hedgehog.

---

### Post by shimmyt on 2006-08-18
Great How-To! Just to let you know I did it with all of the new packages, so it's working with Snort 2.6. One thing you might want to mention though if you are on the server that you're working on this document is great. If you're on another box just SSH'ing in though you might want to remind people to download snort on their machine so they can get the SQL script to run against the database on the mysql box. Also PHPMyAdmin is another great way of running the script against the database. I just opened the file copied and pasted it into run SQL in phpMyAdmin and it worked flawlessly. Once again an awesome write up.

---

### Post by mitjab on 2006-08-28
when i want to restart snort i get this warning

WARN: /etc/snort/db-pending-config file found
WARN: Snort will not start as its database is not yet configured.
WARN: Please configure the database as described in
WARN: /usr/share/doc/snort-{pgsql,mysql}/README-database.Debian
WARN: and remove /etc/snort/db-pending-config

if i want to do
   $ cd /usr/share/doc/snort-mysql/
   $ zcat create_mysql.gz | mysql -u <user> -h <host> -p <databasename>

i get error that schema table already exist. I import table snort_mysql.sql from snort-2.4.5/schemas which i download it from snort.

Can i then just delete the db-pending-config? Are this two DB the same?

and why when i look in [http://localhost/base](http://localhost/base) nothing is logged?

---

### Post by mitjab on 2006-08-31
anyone?

---

### Post by djhedges on 2006-09-03
> **mitjab said:**
> when i want to restart snort i get this warning

WARN: /etc/snort/db-pending-config file found
WARN: Snort will not start as its database is not yet configured.
WARN: Please configure the database as described in
WARN: /usr/share/doc/snort-{pgsql,mysql}/README-database.Debian
WARN: and remove /etc/snort/db-pending-config

if i want to do
   $ cd /usr/share/doc/snort-mysql/
   $ zcat create_mysql.gz | mysql -u <user> -h <host> -p <databasename>

i get error that schema table already exist. I import table snort_mysql.sql from snort-2.4.5/schemas which i download it from snort.

Can i then just delete the db-pending-config? Are this two DB the same?

and why when i look in [http://localhost/base](http://localhost/base) nothing is logged?


I'm not sure.  I'm kinda confused why your using the 2.4.5.  Last time I checked Ubuntu still had snort 2.3 listed.  It looks to me like your using the database that the repositories installed and what you downloaded.  I'm just really confused on what exactly your doing.

Did you try removing the config like the warn message stated?  Thats where I where I would start.

---

### Post by whatalotta on 2006-09-07
Hi all,
 
I was able to get make this howto work with a little modification. 
 
First, as the above post points out, you have to download the right version of snort. It is not on the downloads page, you have to poke around on the Snort.org site a little to find the legacy versions (but they are there).
 
Second, from the packages I installed a few days ago when installing Kubuntu and setting up my servers, I ended up with the Apache, CGI and CLI versions of PHP 4, and only the CGI and CLI versions of PHP 5 installed. 
 
This caused a problem when I tried the graph alert data function in base. I would get basically a blank page saying that I needed to recomplie PHP --with-gd. After noticing the PHP version and type issue above, I found libapache2-mod-php5 in the repository. A quick:
 
[html]apt-get install libapache2-mod-php5[/html]
 
and uncommenting the extension gd and extension mysql and adding an extenstion mysqli to the new /etc/php5/apache2/php.ini got everything up and running.
 
Hope this helps someone.
 
-whata

---

### Post by shahin on 2007-04-18
> **dmccarney said:**
> Problem solved.

I nuked the install and then started fresh. I installed the LAMP bits before I even moved on to the Snort, Oinkmaster and BASE stuff and this time it worked flawlessly.

However, I'd like to point out that you should probably update the bits of your guide pertaining to the ADODB install. The ADODB package that is found in Synaptic for Dapper Drake now installs the package to:

```
/usr/share/php/adodb 
```

Instead of 

```
/usr/share/adodb
```

As found in the guide at the moment.

Thanks for a good Howto!

- Dan

Apparently the vendor is aware of this error by now.  When I downloaded php I got the following message:

********************************************************************************************
WARNING: include path for php has changed!                                      &#9474;
 &#9474;                                                                                 &#9474;
 &#9474; libphp-adodb is no longer installed in /usr/share/adodb. New installation path  &#9474;  
 &#9474; is now /usr/share/php/adodb.                                                    &#9474;  
 &#9474;                                                                                 &#9474;  
 &#9474; Please update your php.ini file. Maybe you must also change your web-server     &#9474;  
 &#9474; configuraton.
**********************************************************************************************
I went to update php.ini file in:
/etc/php5/apache2
But I do not see the directories for adodb stated above.  Anyone know what to do?

---

### Post by ireblue on 2007-05-10
I hope someone can help me here, I've been messing with snort, Base & apache2 for over a week now. After finally getting Snort to work I now get a blank main page when I try to log on to htp://localhost/base. I have reinstalled snort and base no less than 5 times in the past week starting with the latest version from snorts website which would not compile w/ the --mysql option so i am now using ver 2.3.3 from the repo. Ive followed this how-to as well as several others to no avail. Also if I install lighttpd instead of a blank page I get a popup to download a file. Any help will be appreciated.

---

### Post by djhedges on 2007-05-13
Base will not work without msql.  Base reads the mysql database and find the alerts from the database.

If you a downloading a file when you visit a site which has php then your php isn't working.

Keep in mind this how to was created in breezy badger and I don't run ubuntu anymore.

---

### Post by ireblue on 2007-05-14
I am running mysql also, i followed the HOW-TO to the letter, but just as in the how-to where you also had the prob of a file download when u went to localhost/base, thats my problem but it doesnt go away with any amount of rebooting.

---

### Post by djhedges on 2007-05-16
Without the mysql option snort isn't going to log to mysql.  Thats where base isn't going to work.

If your going to site that has php and it trys to download the file instead of display it that means something is wrong with either php or apache.  It's been so long I can't remember how to fix it.  Have you tried reinstalling php/apache?

---

### Post by djhedges on 2007-05-16
Even though this post is about fiesty this may work for you.


[http://ubuntuforums.org/showthread.php?t=433626&highlight=php+problem+download](http://ubuntuforums.org/showthread.php?t=433626&highlight=php+problem+download)

---

### Post by kristopher_d on 2007-06-21
It doesn't seem to be using my snort db user password.

The password is in snort.conf, but when I run
```
sudo snort -c /etc/snort/snort.conf
```
I get
```
ERROR: database: mysql_error: Access denied for user 'snort'@'localhost' (using password: NO)
```

---

### Post by kristopher_d on 2007-06-21
Never mind, had it configured the wrong place.

---

### Post by griggsy21 on 2007-06-22
Kristopher...I am having the same problem. But I believe I have the password configured in the right place in the snort.conf file. Out of curiosity, I tried mysql -u snort -p, and I got the same error. I followed the script word for word, but just not having any luck. Any ideas?

---

### Post by djhedges on 2007-06-24
> **griggsy21 said:**
> Kristopher...I am having the same problem. But I believe I have the password configured in the right place in the snort.conf file. Out of curiosity, I tried mysql -u snort -p, and I got the same error. I followed the script word for word, but just not having any luck. Any ideas?

Sounds like you might have a different password for the snort user.  Try the following but change PASSWORD_SNORT_CONF to your snort.conf password
```
mysql -u root -p
set password for snort@localhost=password('PASSWORD_SNORT_CONF');
```

Then you should be able to do mysql -u snort -p

---

### Post by sirmarsh on 2007-09-26
Hey all.

Need some help.

Got snort running and loggin to mysql.

The issue is base. I go the mydomain.com/base and login with user/pass, but then I get the following screen. Can anyone help out?

Fatal error: Call to undefined function mysql_pconnect() in /usr/share/adodb5/drivers/adodb-mysql.inc.php on line 381


I looked in there, but don't see the issue.

Thanks

---

### Post by djhedges on 2007-09-27
> **sirmarsh said:**
> Hey all.

Need some help.

Got snort running and loggin to mysql.

The issue is base. I go the mydomain.com/base and login with user/pass, but then I get the following screen. Can anyone help out?

Fatal error: Call to undefined function mysql_pconnect() in /usr/share/adodb5/drivers/adodb-mysql.inc.php on line 381


I looked in there, but don't see the issue.

Thanks
base/base.conf
$Dblib_path = “/usr/share/adodb/”;

This is how I configured adodb for Fiesty when I made this guide, not sure if adodb has changed it's location because I don't have ubuntu installed atm.

---

### Post by clev8ubn on 2007-11-05
Hello, thanks for the great tutorial, but I am having some problems with snort can you please help.  I can NOT seem to get snort alerts to trigger no matter what I do.  I have used nmap, I have used fragmented ICMP packets, nothing.  I set the local rules as you suggested.  Please help.  I know that I am not giving very much detail as to my actual problem, maybe if you could point me in the right direction.

---

### Post by djhedges on 2007-11-06
> **clev8ubn said:**
> Hello, thanks for the great tutorial, but I am having some problems with snort can you please help.  I can NOT seem to get snort alerts to trigger no matter what I do.  I have used nmap, I have used fragmented ICMP packets, nothing.  I set the local rules as you suggested.  Please help.  I know that I am not giving very much detail as to my actual problem, maybe if you could point me in the right direction.

Are you doing a nmap scan from another computer?
```
nmap -sS *target*
```

Does your snort box have a firewall?
```
iptables -L
```

Is snort running?
```
pgrep -l snort
```

---

### Post by Sarmacid on 2008-07-18
Great guide, thanks a lot, although I had to make a little change

instead of ```
$Dblib_path = “/usr/share/adodb/”;
```
I had to put ```
$Dblib_path = “/usr/share/php/adodb/”;
```

Using Ubuntu 8.04

---

### Post by danuk88 on 2008-09-21
I have followed this tutorial and i have got Snort Mysql & Base installed i am using hardy 8.04 but how can get snort to load on boot? because after I reboot and run a port scan off another pc on my network nothing gets logged in base

Thank

Dan

---

### Post by djhedges on 2008-09-21
> **danuk88 said:**
> I have followed this tutorial and i have got Snort Mysql & Base installed i am using hardy 8.04 but how can get snort to load on boot? because after I reboot and run a port scan off another pc on my network nothing gets logged in base

Thank

Dan

To start snort
```
sudo /etc/init.d/snort restart
```

If the above doesn't do anything
```
sudo snort -c /etc/snort/snort.conf
```

Quick way to look for snort processes
```
pgrep -l snort
```

---

### Post by danuk88 on 2008-09-22
Hi and thanks for the response, great tutorial,

when I re-boot I can put the following command in the terminal -

sudo snort -c /etc/snort/snort.conf

and snort will start with no problems but is there a way to get snort to start up automatic or do you have to issue the above command every time you boot up / re-boot?

Thank You

Dan

---

### Post by Sarmacid on 2008-09-22
Try with
```
update-rc.d snort
```

---

### Post by danuk88 on 2008-09-22
When I run the command

update-rc.d snort

snort is still not running after I re-boot.

Thanks

Dan

---

### Post by Sarmacid on 2008-09-23
Oops, only gave you half the command, sorry ^^;

Try with

```
sudo update-rc.d snort defaults
```

If that still doesn't work, you may wanna install the boot up manager. It has a GUI and you can configure all the services you want up or down when you boot.

```
sudo apt-get install bum
```

---

### Post by garymc1 on 2008-09-23
To get snort running on boot,

1, run "which snort" in terminal and this will return /usr/sbin/snort 
(if you are using ubuntu 8.04)

2, edit your rc.local file found in /etc to look like this

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

/usr/sbin/snort -c /etc/snort/snort.conf

exit 0


Hope this helps 

Cheers

Gary

---

### Post by djhedges on 2008-09-23
> **danuk88 said:**
> Hi and thanks for the response, great tutorial,

when I re-boot I can put the following command in the terminal -

sudo snort -c /etc/snort/snort.conf

and snort will start with no problems but is there a way to get snort to start up automatic or do you have to issue the above command every time you boot up / re-boot?

Thank You

Dan

Sounds like the init script isn't working.  I think on page 1 of this thread there were some other guys that had the same problem.

---

### Post by djhedges on 2008-09-23
> **garymc1 said:**
> To get snort running on boot,

1, run "which snort" in terminal and this will return /usr/sbin/snort 
(if you are using ubuntu 8.04)

2, edit your rc.local file found in /etc to look like this

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

/usr/sbin/snort -c /etc/snort/snort.conf

exit 0


Hope this helps 

Cheers

Gary

I think this needs an -D for daemon otherwise it'll spit it's output and cause problems.
```
/usr/sbin/snort -cD /etc/snort/snort.conf
```

---

### Post by garymc1 on 2008-09-24
Hi

I have just checked my rc.local file and you do need the (-D) sorry. I have the following entry in my rc.local file,

/usr/sbin/snort -c /etc/snort/snort.conf -i eth0 -D

Cheers

Gary

---

### Post by danuk88 on 2008-09-24
I have got snort loading on boot. Thank you, the only thing I had to change was eth0 to eth1

/usr/sbin/snort -c /etc/snort/snort.conf -i eth1 -D

Thanks for the help

Dan

---

### Post by MoonPhoenix on 2008-10-01
I've now done this a slightly different way, by adding the following to my rc.local...

...
service snort start
...

Then running 'sudo dpkg-reconfigure snort' and placing -D in the additional options screen. And of course setting startup to manual in there.

This keeps control of the process under the 'init' and 'service' commands. Makes for a tidy shutdown.
I'm still unsure why it fails earlier in the boot process and works via the same script at the end. Maybe a race condition? (is that the correct term?)

---

### Post by MoonPhoenix on 2008-10-03
Amedment to that last post. I left snort to autostart.
It seems to be the first attempt it fails to start. But on a second the init script starts it fine

---

