---
title: "How-to: Installing Torrent-Flux"
date: 2006-10-01
forum: Outdated Tutorials &amp; Tips
---

### Post by kebes on 2006-10-01
[SIZE="2"]**Important Note:**[/SIZE]
This how-to was written for Ubuntu 6.06 (Dapper Drake), for manually installing torrentflux.

However, torrentflux has since been [added to the repositories]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=torrentflux&searchon=names&subword=1&version=all&release=all"). Thus, installation should now be much simpler. You can just go to the Synaptic package manager (Applications > Add/Remove) and install it. (Use Adept on Kubuntu.) On the commandline, you can go:

```
sudo aptitude install torrentflux
```

That replaces steps 3 and 4a from the guide. The rest of the guide details other aspects of getting torrentflux installed and working. You can also use the entire guide (including steps 3 and 4a) if you want to do a manual install for some reason.







I've had several friends ask about how to get torrentflux working, so I'm posting this how-to to in case anyone else finds it useful.

**[SIZE="4"]Introduction[/SIZE]**
Torrentflux is a neat open-source bit-torrent application. The interesting thing about it is that it runs entirely as a web-application. This means that you can access it remotely, from anywhere, using a web-browser. You can initiate, monitor, and manage your bit-torrent downloads while away from your computer.

The only 'catch' is that you need to be running a full webserver (including PHP and MySQL) for this to work. Luckily it's rather simple to get this working in Linux. If you're running Ubuntu, you should have no problem getting this to work.

It may seem like 'overkill' to install a whole LAMP environment just for torrentflux, however you may soon discover that there are many neat things you can do with a functional LAMP stack. Torrent-flux is only one example.


**[SIZE="4"]Step 1: Get a functional LAMP stack.[/SIZE]**

To get a 'LAMP' stack running (Linux Apache Mysql Php), you just install the packages "apache2", "php5" and "mysql-server". You can do this using Synaptic (Ubuntu) or Adept (Kubuntu), or on the command line:
```

$ sudo aptitude install apache2
$ sudo aptitude install php5
$ sudo aptitude install mysql-server
$ sudo aptitude install php5-mysql

```

Once these are installed, you should be able to test it by pointing your web-browser to:
[http://localhost/](http://localhost/)

You should see a web-page, not an error message. (You may see a simple web-dir listing with "apache2-default" in it... that's normal.) To test if PHP is working properly, just create a simple test page. For instance, create a file:
```

$ sudo nano /var/www/test.php

```

And put in this text:
```

<html>
<head>
  <title>Test Page</title>
</head>
<body>
Test page<br />
<?php 
	echo 'If you can see this text, then PHP is working.';
?>
</body>
</html>

```

Then go to [http://localhost/test.php](http://localhost/test.php)
If you see the "...then PHP is working" message then all is well.

Since your PHP/MySQL interface will eventually be world-accessible, it makes sense to put some security in place. By default MySQL starts with no password, so you should certainly set one:
```

$ mysqladmin -uroot password 'new-password'

```

(Note: if you're ever having trouble coming up with good passwords, install and run a simple commandline program called "pwgen" ... it will suggest strong passwords that are reasonably easy to remember.)


**[SIZE="4"]Step 2: Make sure you can access your webserver.[/SIZE]**

A common stumbling block in getting a LAMP stack fully functional is that port 80 is blocked. This may be because the Internet Service Provider (ISP) is blocking it, or because your router's firewall is blocking it. To test whether or not you are blocked, first find out your world-facing ("external") IP address. You can do this in any number of ways, such as visiting sites like:
[http://www.ipaddressworld.com/](http://www.ipaddressworld.com/)

Then test your setup by using a web browser to check:
[http://localhost/](http://localhost/)
[http://xxx.xxx.xxx.xxx/](http://xxx.xxx.xxx.xxx/)

(Where the x's are your IP address, of course.) If you see the same apache page in both cases, then everything is working. If in the second case you get an erorrt, then somewhere along the line port 80 is being blocked. It could be your ISP, or the firewall in your router (if any).


**[SIZE="2"]2.a Opening up port 80 on a router.[/SIZE]**

If you have a router, you should log into it and open up port 80. First find out your local IP address (the one inside your local network). To do this just type:
```

$ ifconfig

```

Among other things, you should see something like "inet addr:192.168.1.101" (usually in the first block of output, marked "eth0"). That is your internal IP address.

Then access your router's administration mode. Typically you access your router by using a web-browser and going to "http://192.168.1.1/" or "http://192.168.15.1/" or some other "special address" like that. You will need to find the documentation for your specific router. You will probably also have to enter a username and password to get access to the router admin page.

Once there, you will need to find a section marked "Application & Gaming" or "Port Forwarding" or something similar. In this section, you should set up a new rule along the lines of:
```

name: http
port start: 80
port end: 80
type (TCP/UDP/Both): Both
Forward to: 192.168.1.101
Enabled: Yes

```

Needless to say, you should replace the "192.168.1.101" in the above example with the internal IP address you determined previously. You may need to restart the router for changes to take effect (simply unplugging it for a few seconds should work).

Then you should test again by visiting your *external* IP address:
[http://xxx.xxx.xxx.xxx/](http://xxx.xxx.xxx.xxx/)


**[SIZE="2"]2.b Using a non-standard port.[/SIZE]**
If the above did not work, then it is likely that port 80 is being blocked by your ISP. Many residential ISPs will block port 80 (the standard port for http web requests), so you may need to use a non-standard port. Doing so is relatively simple, however. First edit the configuration for your webserver:
```

$ sudo nano /etc/apache2/apache2.conf

```
And add a line that says:
```

Listen 8080

```

The "8080" is the non-standard port we will use. You can pick any port you want, as long as it is greater than 1024 (low ports are reserved and probably also blocked). You need to restart apache for hte change to take effect:
```

$ sudo /etc/init.d/apache2 restart

```

Then modify your router to allow port 8080 to be forwarded to your computer. Use the guidelines given above (section 2.a), except put "8080" instead of "80".

After doing this, test your webserver by going to:
[http://localhost:8080/](http://localhost:8080/)
[http://xxx.xxx.xxx.xxx:8080/](http://xxx.xxx.xxx.xxx:8080/)

In both cases you should get to your apache page, like before. If this doesn't work then go back over the steps and double-check what you've done. It may also be that your router doesn't support port-forwarding properly. In some cases you can "flash the firmware" on your router to fix the problem.


**[SIZE="4"]Step 3: Get Torrent-Flux[/SIZE]**

Now you can go download torrentflux:
[http://www.torrentflux.com/](http://www.torrentflux.com/)

The files are hosted by SourceForge:
[http://prdownloads.sourceforge.net/torrentflux/torrentflux_2.1.tar.gz?download](http://prdownloads.sourceforge.net/torrentflux/torrentflux_2.1.tar.gz?download)

Once the file is downloaded, you can untar it in the usual way:
```

$ tar -xvzf torrentflux_2.1.tar.gz

```

Inside the newly-created "torrentflux_2.1/" directory, you will find a file called "INSTALL" with detailed instructions of what to do next. We'll now go through those steps.


**[SIZE="4"]Step 4: Install Torrent-Flux[/SIZE]**

**[SIZE="2"]4.a Copy files.[/SIZE]**
Torrent-flux is 'simply' a bunch of PHP files (server-interpreted web-files). For them to work, all you really need to do is copy them into your web-folder:
```

$ sudo mkdir /var/www/torrentflux/
$ sudo chown user:user /var/www/torrentflux/
$ cd ~/Desktop/torrentflux_2.1/html/
$ cp -r * /var/www/torrentflux/
```

Instead of user:user you should put your username and group. (They are usually the same, and are simply the name you login with.) The above "cd" command will vary depending on where you untared the files.

**[SIZE="2"]4.b MySQL.[/SIZE]**
We also need MySQL setup properly. Create a database for torrentflux:
```

$ mysqladmin -uroot -p create torrentflux

```
(You'll need to enter the MySQL password you set previously.) Now go into the "sql" sub-directory in torrentflux (depends on where you untared torrentflux, of course):
```

$ cd ~/Desktop/torrentflux_2.1/sql

```
And upload the torrentflux structure to MySQL:
```

$ mysql -uroot -p torrentflux < mysql_torrentflux.sql

```

If you don't like using MySQL on the commandline, you can install a program called "phpmyadmin" that gives you easy web-browser access to all of the functionality in MySQL. Once installed, you access it by pointing your web-browser to: [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)

Now you need to tell torrentflux the password you set for your MySQL system. So you edit the file:
```

$ sudo nano /var/www/torrentflux/config.php

```

Near the top of the file, you'll see lines that read:
```

$cfg["db_user"] = "root";        // username for your MySQL database
$cfg["db_pass"] = "";            // password for database

```
You can modify the "db_pass" line with the password you selected before.

**[SIZE="2"]4.c New MySQL User[/SIZE]**
For added security/control, you may prefer to give torrentflux a "non-root" MySQL access. This can be important if you have lots of different applications all using MySQL. To do this, you can use "phpmyadmin" or enter these commands one at a time:
```

$ mysql -uroot -p
mysql> use mysql;
mysql> INSERT INTO user (Host,User,Password) VALUES('localhost','torfluxuser',PASSWORD('secret'));
mysql> FLUSH PRIVILEGES;
mysql> GRANT SELECT,INSERT,UPDATE,DELETE,CREATE,DROP ON torrentflux.* TO 'torfluxuser'@'localhost';
mysql> exit;

```

Of course instead of 'secret' you should use better password. Now you edit the torrentflux configuration:
```

$ sudo nano /var/www/torrentflux/config.php

```

And update the lines:
```

$cfg["db_user"] = "torfluxuser";        // username for your MySQL database
$cfg["db_pass"] = "secret";            // password for database

```
Obviously you can call your torrentflux user whatever you want, and set the password to whatever you like. Just make sure that the entry in MySQL and in torrentflux match!


**[SIZE="2"]4.d First login.[/SIZE]**
Now you can go to your torrentflux page, using a web-browser:
[http://localhost/torrentflux/](http://localhost/torrentflux/)

On your first login you the username and password you supply will be the "administrator account" for torrentflux. Make sure you rememeber the password! (It doesn't have to match the MySQL password you created before.)

You should then be taken to a page where you can configure torrentflux. In particular, the first line (path) will be marked with an error:
"Path is not Writable -- make sure you chmod +w this path"
You need to change permissions on the download folder:
```

$ sudo chmod 777 /var/www/torrentflux/downloads/

```

You should look over the rest of the settings too. Note that "Port Range" is an important parameter for efficient bit-torrent. You should pick some range (like 45000-46000), and then open up the corresponding range on your router (if any). By allowing connections on that range, you will be able to connect to a larger swarm during downloading, which increases download speed considerably.

**[SIZE="4"]Step 5: Dynamic IP[/SIZE]**

If you have a static IP address, you can skip this step. However most home users have a dynamic IP, meaning that it changes every so often (whenever your ISP feels like it, which may be every day or every couple of months). Thus to connect to your torrentflux remotely, you won't know what IP address to go to. A convenient solution is to use a "domain redirect" service. Basically this service will give you an easy to remember alias, like "user.example.com" which will get you to your machine. In order to have the IP conveniently updated, there are programs that can update your domain redirect automatically.

There are companies that offer free domain redirection services. An extensive list can be found here:
[http://www.technopagan.org/dynamic/#TheList](http://www.technopagan.org/dynamic/#TheList)
The two most popular are DynDNS:
[http://www.dyndns.com/services/dns/dyndns/](http://www.dyndns.com/services/dns/dyndns/)
and noip:
[http://www.no-ip.com/services/managed_dns/free_dynamic_dns.html](http://www.no-ip.com/services/managed_dns/free_dynamic_dns.html)

This tutorial will use "noip" as an example. Similar procedures would apply to other services. I've used noip for quite awhile now, and their service is excellent. You can create a new account:
[http://www.no-ip.com/newUser.php](http://www.no-ip.com/newUser.php)

Then you can login to "Your No-IP" and go "Add" to create a new host. You get to select the prefix (whatever you want) and select a list of domains from those that No-IP manages. You can then enter your current IP address (usually auto-detected). Let's say you selected "user.no-ip.info". After adding the new host (and waiting a few minutes), you should be able to access your torrentflux using:
[http://user.no-ip.info/torrentflux/](http://user.no-ip.info/torrentflux/)
or
[http://user.no-ip.info:8080/torrentflux/](http://user.no-ip.info:8080/torrentflux/)
(if you used a custom port, above).

Of course the real problem with a dynamic IP is that it changes without notice. For this, No-IP provides a piece of software (go to the "Download" section and select "Linux/BSD/Unix"):
[http://www.no-ip.com/client/linux/noip-duc-linux.tar.gz](http://www.no-ip.com/client/linux/noip-duc-linux.tar.gz)
As before, you need to untar the file, and enter the new directory:
```

$ tar -xvzf noip-duc-linux.tar.gz
$ cd noip-2.1.3/

```
If you are running an "i686 machine" (i.e.: any recent standard desktop PC), then do this:
```

$ cp binaries/noip2-Linux noip2
$ sudo make install

```
And answer the questions (using the email/password that you created the noip account with). The update interval is in minutes (default 30 minutes is fine).

If you are not running an i686 machine (PowerPC, etc.) then you will need to compile the program. If you don't have compilers installed, then install them:
```

$ sudo aptitude install build-essential

```
To compile, while in the "noip2-2.1.3/" direction, just do:
```

$ make
$ sudo make install

```

In either case, you can now run noip by typing:
```

$ sudo noip2

```

To make sure that noip starts everytime the computer boots, edit the file "rc.local" in the "/etc/" directory (note that there is another version of rc.local in "/etc/init.d" but that's not the one you want to edit!):
```

$ sudo nano /etc/rc.local

```

And add a line:
```

/usr/local/bin/noip2 &

```
Be sure to put this line *before* the "exit 0" line at the end!

Now noip will always be running when the computer is turned on, and it will update the your domain name frequently, so that when you go to "http://user.no-ip.info/torrentflux/" you get to your own pesonal torrentflux application.


**[SIZE="4"]Step 6: Adding Search Modules[/SIZE]**
Another neat feature of torrentflux is that it centralizes your torrent searching. You can add modules to torrentflux that enable it to use the search facilities on a number of different trackers. A few modules are given as examples. Other modules are are available on the torrentflux forums:
[http://www.torrentflux.com/forum/](http://www.torrentflux.com/forum/)

To add a new module, simply download the file, and move it into the "searchEngines" folder:
```
$ mv module.php /var/www/searchEngines/
```

**[SIZE="4"]Conclusion[/SIZE]**
Hopefully this how-to will be of use to others. I followed these steps on a fresh install of Kubuntu 6.06 and it worked fine.

---

### Post by honeydew on 2006-10-18
I get this error, after doing this howto, I am using the dapper server edition, 

[HTML]Fatal error: Call to undefined function mysql_connect() in /var/www/adodb/drivers/adodb-mysql.inc.php on line 354[/HTML]

---

### Post by ToonArmy on 2006-10-18
```
$ sudo aptitude install php5-mysql
```

Should sort you out.

---

### Post by StormNet on 2006-10-23
Hmmm... I am getting the same error, and i made sure that i have all necessary components
> **Fatal error: **Call to undefined function mysql_connect() in
**/var/www/torrentflux/adodb/drivers/adodb-mysql.inc.php** on line **354**

I am running PHP5 and Apache2, I am sure that mysql can be accessed (i am also running Gallery1 so i am sure that it is running fine.)

Anyone have any ideas what i may be forgetting?

---

### Post by StormNet on 2006-10-23
Problem solved, I did a little digging around and found this:
> **Fatal error: Call to undefined function: mysql_connect() in /var/www/html/adodb/drivers/adodb-mysql.inc.php on line 354**
This means that your version of php can't connect to the mysql database. Usually installing a package like php-mysql will solve this although if it doesn't then open your php.ini file and find the line like extension=mysql.so, remove the comment from in front, and then restart your webserver.from the official FAQ which can be found here:

[http://www.torrentflux.com/forum/index.php/topic,1451.0.html]("http://www.torrentflux.com/forum/index.php/topic,1451.0.html")

So i did the following:
> sudo gedit /etc/php5/apache2/php.ini
to remove the comment from the **extension=mysql.so** (line 565) and restart apache.
> sudo /etc/init.d/apache2 restart

---

### Post by rigor on 2006-11-01
if i try do go to [http://localhost/test.php]("http://localhost/test.php"), obtain this message

```
 Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0
 
 Warning: Unknown: Failed opening '/var/www/test.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0


```

if i try
```

sudo /etc/init.d/apache2 start
* Starting apache 2.0 web server...                                   
apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd (pid 6243) already running
                                                                                                                       [ ok ]


```

please, i'm very newbie, any ideas???

tks a lot

---

### Post by phunkycow on 2006-11-01
Thanks for this How-To. Works like a charm :)

---

### Post by PoLiSonTe on 2006-11-10
Hi another newb here, everything worked fine for me until after the login page i get this error

> Debug SQL is on. 

SQL: INSERT INTO tf_log ( USER_ID, FILE, ACTION, IP, IP_RESOLVED, USER_AGENT, TIME ) VALUES ( 'usernamehere', '/torrentflux/index.php', 'HIT', '::1', 'ip6-localhost', null, '1163138870' )


Database error: Column 'user_agent' cannot be null

Always check your database variables in the config.php file.

Any ideas?

---

### Post by tee2 on 2006-11-30
Hi all, I have a problem.

When I browse to [http://localhost/test.php](http://localhost/test.php), firefox tries to save the php file and doesn't load it in the browser like it should. What could be the problem? I installed php5 and php5-mysql so I don't know why things won't work. :confused:

---

### Post by jbtito03 on 2006-11-30
There is a problem with your apache modules config or something.

Post your /var/log/apache2/error.log

:D

JB

---

### Post by tee2 on 2006-11-30
> **jbtito03 said:**
> There is a problem with your apache modules config or something.

Post your /var/log/apache2/error.log

:D

JB
```
[Wed Nov 29 20:10:16 2006] [notice] Apache/2.0.55 (Ubuntu) configured -- resuming normal operations
[Wed Nov 29 20:10:46 2006] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Wed Nov 29 21:03:40 2006] [notice] caught SIGTERM, shutting down
[Wed Nov 29 21:03:41 2006] [notice] Apache/2.0.55 (Ubuntu) configured -- resuming normal operations
[Wed Nov 29 21:50:55 2006] [notice] caught SIGTERM, shutting down
[Wed Nov 29 21:50:56 2006] [notice] Apache/2.0.55 (Ubuntu) configured -- resuming normal operations
[Wed Nov 29 23:38:03 2006] [notice] Apache/2.0.55 (Ubuntu) configured -- resuming normal operations

```

No mention of anything php related.

---

### Post by tee2 on 2006-12-01
bump

---

### Post by tee2 on 2006-12-01
Hi I fixed my php problem but I have a new one. When I browse to [http://localhost/torrentflux/html/](http://localhost/torrentflux/html/) (my files are located there, don't know why) I get a 404 even thhough the files ARE there. ](*,)

---

### Post by simao on 2006-12-01
Hi,

I installed torrentflux on my Ubuntu Server machine but I can't get my torrent downloads to get some speed.

I'm using the default port range 49160-49300 but when I try to connect by telnet to test if those ports are open, I get a connection refused error.

So I assume it's a port related problem.

I'm not using any firewall, and I have apache and sshd running successfully, which is even more strange.

Thank you for your help.

---

### Post by tee2 on 2006-12-02
bump

---

### Post by tee2 on 2006-12-02
bump

---

### Post by Cancel on 2006-12-02
Great tutorial!! I have always wanted to do this. The only thing different for me was everything was in the torrentflux.html folder. Other than that it works perfect. Thank-you!!!

---

### Post by kebes on 2006-12-03
> **tee2 said:**
> Hi I fixed my php problem but I have a new one. When I browse to [http://localhost/torrentflux/html/](http://localhost/torrentflux/html/) (my files are located there, don't know why) I get a 404 even thhough the files ARE there. ](*,)

First check the permissions on your files, and the directory containing them:
```

$ ls /var/www/ -laF
$ ls /var/www/torrentflux/ -laF

```

The files should have the world read bit set (the permissions should be something like -rwxr--r--). If they are not set right use:
```

$ sudo chmod 744 /var/www/torrentflux/ -R

```


If that's not the problem, then post more information about your setup. Are you operating on a non-standard port? (In which case, don't forget to put it in the URL, like [http://localhost:8000/torrentflux/html/](http://localhost:8000/torrentflux/html/) or whatever.) Also, does [http://localhost/test.php](http://localhost/test.php) work now? If so, does [http://localhost/torrentflux/html/index.php](http://localhost/torrentflux/html/index.php) work? (i.e.: explicitly go to the index.php file, instead of just going to the directory).

---

### Post by kebes on 2006-12-03
> **simao said:**
> Hi,

I installed torrentflux on my Ubuntu Server machine but I can't get my torrent downloads to get some speed.

I'm using the default port range 49160-49300 but when I try to connect by telnet to test if those ports are open, I get a connection refused error.

So I assume it's a port related problem.

I'm not using any firewall, and I have apache and sshd running successfully, which is even more strange.

Thank you for your help.


Try using a different port range. Some ISPs may be blocking port ranges typically used for bit-torrent. So try a different range (remember it has to be greater than 1024), like 21000-22000 or whatever.

You said you don't have a router, but perhaps you do? Some DSL modems, for instance, have internal router-like functions, complete with configuration panels that you can access in the usual way (often by navigating to a page like [http://192.168.0.1/)](http://192.168.0.1/)). Check out your hardware.

If it's not an ISP issue, and not a router issue, it's possible that it's an iptables issue (the internal Linux firewall system). In a default Ubuntu install, this shouldn't be a problem, though (unless you installed additional packages? SELinux or something?).

Lastly, are you sure that the port problem is really the problem? When you run torrentflux, do the "indicating dots" to the left of downloading torrents turn green... or do they stay red/yellow?

Hope that helps.

---

### Post by kebes on 2006-12-03
> **rigor said:**
> if i try do go to [http://localhost/test.php]("http://localhost/test.php"), obtain this message

```
 Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0
 
 Warning: Unknown: Failed opening '/var/www/test.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0


```

if i try
```

sudo /etc/init.d/apache2 start
* Starting apache 2.0 web server...                                   
apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd (pid 6243) already running
                                                                                                                       [ ok ]


```

please, i'm very newbie, any ideas???

tks a lot

Not sure if this query is still relevant, but here's some advice:

Instead of doing "sudo /etc/init.d/apache2 start" you should use "sudo /etc/init.d/apache2 restart" to re-initialize the server (i.e.: shut it down and start a new instance). If this also gives an error then it's an apache-level issue to be fixed. If apache loads properly but you still get the above error when going to "test.php" then take a look at my recent post (above) where I mention file permissions. It may simply be that the file in question is not "world readable" ... which you need for web pages.

Hope that helps.

---

### Post by tee2 on 2006-12-04
> **kebes said:**
> First check the permissions on your files, and the directory containing them:
```

$ ls /var/www/ -laF
$ ls /var/www/torrentflux/ -laF

```

The files should have the world read bit set (the permissions should be something like -rwxr--r--). If they are not set right use:
```

$ sudo chmod 744 /var/www/torrentflux/ -R

```


If that's not the problem, then post more information about your setup. Are you operating on a non-standard port? (In which case, don't forget to put it in the URL, like [http://localhost:8000/torrentflux/html/](http://localhost:8000/torrentflux/html/) or whatever.) Also, does [http://localhost/test.php](http://localhost/test.php) work now? If so, does [http://localhost/torrentflux/html/index.php](http://localhost/torrentflux/html/index.php) work? (i.e.: explicitly go to the index.php file, instead of just going to the directory).

I just tried to browse to [http://localhost/torrentflux/html/index.php](http://localhost/torrentflux/html/index.php) like you suggested and things worked...as does just browsing to [http://localhost/torrentflux/html/](http://localhost/torrentflux/html/). Weird. Well, whatever. Thanks though. :)

---

### Post by det0r on 2007-01-05
Hey, I'm having a few issues. I tried to install torrentflux last night and it borked out during the installation at the process of setting up the SQL database. I hadn't really thuoght about it and I just did:
sudo aptitude install torrentflux

and let it run etc. But yeah, it didn't finish, gave me some error which I should have, but didn't copy. I thought I would have a look for a readme such as this one and I started doing the instructions to install apache:
sudo aptitude install apache2

and I get:
The following packages have been automatically kept back:
  beryl-core beryl-manager beryl-plugins beryl-plugins-data beryl-settings 
  emerald 
The following NEW packages will be automatically installed:
  apache2-common apache2-mpm-worker apache2-utils libapr0 libpcre3 
The following packages will be automatically REMOVED:
  torrentflux 
The following packages have been kept back:
  dbus dbus-1-utils libdbus-1-3 libglu1-mesa libwnck-common libwnck18 
  libxss1 mesa-utils xserver-xgl 
The following NEW packages will be installed:
  apache2 apache2-common apache2-mpm-worker apache2-utils libapr0 libpcre3 
The following packages will be REMOVED:
  torrentflux 
0 packages upgraded, 6 newly installed, 1 to remove and 15 not upgraded.
Need to get 0B/1457kB of archives. After unpacking 1962kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 91618 files and directories currently installed.)
Removing torrentflux ...
.: 7: Can't open /usr/share/dbconfig-common/dpkg/prerm.mysql
dpkg: error processing torrentflux (--remove):
 subprocess pre-removal script returned error exit status 2
.: 7: Can't open /usr/share/dbconfig-common/dpkg/config.mysql
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 torrentflux
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:


So, I figured maybe I should manually remove torrentflux first:
sudo aptitude remove torrentflux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  beryl-core beryl-manager beryl-plugins beryl-plugins-data beryl-settings 
  emerald 
The following packages have been kept back:
  dbus dbus-1-utils libdbus-1-3 libglu1-mesa libwnck-common libwnck18 
  libxss1 mesa-utils xserver-xgl 
The following packages will be REMOVED:
  torrentflux 
0 packages upgraded, 0 newly installed, 1 to remove and 15 not upgraded.
Need to get 0B of archives. After unpacking 2753kB will be freed.
Writing extended state information... Done
(Reading database ... 91618 files and directories currently installed.)
Removing torrentflux ...
.: 7: Can't open /usr/share/dbconfig-common/dpkg/prerm.mysql
dpkg: error processing torrentflux (--remove):
 subprocess pre-removal script returned error exit status 2
.: 7: Can't open /usr/share/dbconfig-common/dpkg/config.mysql
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 torrentflux
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

and I get the same error :|. Any ideas?

---

### Post by kebes on 2007-01-05
> **det0r said:**
> and I get the same error :|. Any ideas?

First thing to try:
sudo dpkg --purge torrentflux
sudo aptitude remove torrentflux

You can also check on package status:
dpkg -l torrentflux

(might give a clue as to the state the package is in...)

---

### Post by Tyr_7BE on 2007-02-06
When I go to localhost/torrentflux, I get the following:

"Database error: Access denied for user 'torrentflux'@'localhost' (using password: YES)

Always check your database variables in the config.php file."

However, in my config.php file:
```

$cfg["db_type"] = "mysql";       // mysql, postgres7 view adodb/drivers/
$cfg["db_host"] = "localhost";   // DB host computer name or IP
$cfg["db_name"] = "torrentflux"; // Name of the Database
$cfg["db_user"] = "root";        // username for your MySQL database
$cfg["db_pass"] = "root";            // password for database

```

I know that the username/pass 'root'/'root' works for mysql.
```

$mysql -u root -p
<enter 'root'>

mysql> use torrentflux;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> show tables;
+-----------------------+
| Tables_in_torrentflux |
+-----------------------+
| tf_cookies            | 
| tf_links              | 
| tf_log                | 
| tf_messages           | 
| tf_rss                | 
| tf_settings           | 
| tf_users              | 
+-----------------------+
7 rows in set (0.01 sec)

mysql> 

```

So root/root can access the torrentflux database just fine, but it seems that torrentflux is trying to log in as database user torrentflux, instead of using database torrentflux?

Any ideas?

---

### Post by kebes on 2007-02-07
Very strange. It looks to me like you're doing everything right... just to confirm, the file you are changing/viewing is:
/var/www/torrentflux/config.php

Right? (You are not viewing the copy of "config.php" in the untarred directory.... you are really editing the one in the web-server directory?)


I can't understand why torrentflux wouldn't be seeing the changes you make in that file. If I were you, I would do a test and make sure that torrentflux is really accessing your "config.php" file. Like rename it to "x_config.php" so that torrentflux can't find it. Then when you go to the torrentflux page you should get a ton of weird errors. (You can change the name back to normal afterwards.)

This test will tell you whether torrentflux is even loading the "config.php" file you think it is. Also I would try changing the lines in config.php to something wrong, like:
$cfg["db_user"] = "wrong";        // username for your MySQL database
$cfg["db_pass"] = "wrong";            // password for database

What does the error look like then? Does it say "denied for user wrong" or does it still say "denied for user torrentflux" ?

---

### Post by ubuman on 2007-02-07
When I go to  [http://locahost/torrentfluxi](http://locahost/torrentfluxi) I get error like this 
Warning: include_once(adodb/adodb.inc.php) [function.include-once]: failed to open stream: Permission denied in /var/www/torrentflux/db.php on line 5

Warning: include_once() [function.include]: Failed opening 'adodb/adodb.inc.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/torrentflux/db.php on line 5

Fatal error: Call to undefined function NewADOConnection() in /var/www/torrentflux/db.php on line 12

please help me, Any ideas?

---

### Post by kebes on 2007-02-07
> **ubuman said:**
> Warning: include_once(adodb/adodb.inc.php) [function.include-once]: failed to open stream: Permission denied in /var/www/torrentflux/db.php on line 5

It might be a permissions problem. Go to your torrentflux directory and check what the permissions are:

```

cd /var/www/torrentflux/
ls -laF

```

The files should be owned by some user and group (not root:root), and the files should be world readable. So it should look like this:
```

bob@computer:/var/www/torrentflux$ ls -laF
total 568
-rwxr--r--  1 bob bob 83995 2006-09-30 23:38 admin.php*
drwxr-xr-x 11 bob bob 4096 2006-09-30 23:38 adodb/
-rwxr--r--  1 bob bob 5471 2006-09-30 23:38 AliasFile.php*
etc....

```

If you instead see something like:
```
-rwx------  1 bob bob 83995 2006-09-30 23:38 admin.php*
drwx------ 11 bob bob 4096 2006-09-30 23:38 adodb/
-rwx------  1 bob bob 5471 2006-09-30 23:38 AliasFile.php*

```

Notice the "-rwx------". The last three positions specify world-privileges. Then that means that the permissions are too strict (the web browser cannot read the files). You can change them by going:

```

chomod 744 * -R

```

...which will make all the files (and sub-dirs) world-readable.


If that's not the problem, then maybe when you copied the torrentflux files over, you didn't copy sub-directories? Go check the directory "/var/www/torrentflux/adodb", by going:
```

cd /var/www/torrentflux/adodb/
ls -laF

```

Do you see any files? If not, then when you did the copy command to put the files there, you forgot the "-r" that makes it recursive! Go back a few steps and make sure you've copied everything!

Good luck!

---

### Post by kebes on 2007-02-07
[SIZE="2"]**Important Note:**[/SIZE]
This how-to was written for Ubuntu 6.06 (Dapper Drake), for manually installing torrentflux.

However, torrentflux has since been [added to the repositories]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=torrentflux&searchon=names&subword=1&version=all&release=all"). Thus, installation should now be much simpler. You can just go to the Synaptic package manager (Applications > Add/Remove) and install it. (Use Adept on Kubuntu.) On the commandline, you can go:

sudo aptitude install torrentflux



The guide might still be useful for troubleshooting or if you want to do a manual install for some reason.

---

### Post by Tyr_7BE on 2007-02-07
> **kebes said:**
> [SIZE="2"]**Important Note:**[/SIZE]
This how-to was written for Ubuntu 6.06 (Dapper Drake), for manually installing torrentflux.

However, torrentflux has since been [added to the repositories]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=torrentflux&searchon=names&subword=1&version=all&release=all"). Thus, installation should now be much simpler. You can just go to the Synaptic package manager (Applications > Add/Remove) and install it. (Use Adept on Kubuntu.) On the commandline, you can go:

sudo aptitude install torrentflux



The guide might still be useful for troubleshooting or if you want to do a manual install for some reason.

That was my first course of action, but apt did something horrible and completely wrecked my first try (maybe that's why I'm having problems now?).  Basically, it didn't install mysql, php, or apache, but it tried to configure torrentflux just the same as if they were present.  Fresh install of edgy.

But thank you for your suggestion.  It gave me an idea that seems to have solved the problem.  Apparently apt created /etc/torrentflux that has its own config file, and that's what it was using.  It tried to create the torrentflux user and database in mysql, but since it didn't install mysql it didn't work.  After modifying that file I get a login/password prompt :D

---

### Post by kanenas on 2007-04-29
torrentflux is amazing and this how to is very useful,
but  i was wondering if the author can expand this how to
include how to install tf-b4rt [http://tf-b4rt.berlios.de/](http://tf-b4rt.berlios.de/)

This is based on torrentflux  but with many more options e.g. supports azureus
and transmission

thanks in advance

---

### Post by kebes on 2007-04-29
I've never used torrentflux-b4rt, but it looks like quite a nice extension of the torrentflux code. It looks like it's easier to install than normal torrentflux, because it includes a "setup.php" script that you can run (it appears in a web-browser) to guide you through many of the install steps.

Or, you can install it manually. Inside the tarball that you download from [http://tf-b4rt.berlios.de/](http://tf-b4rt.berlios.de/) there is a file called "INSTALL" that gives brief instructions. As you'll see, this how-to is still mostly applicable. So I would say if you use this how-to and the provided INSTALL file, you should be able to install it easily.

(The file also has instructions for upgrading a standard torrentflux install.)

If you run into any problems, I'd be happy to make suggestions, but like I said I've never actually tried using torrentflux-b4rt.

---

### Post by guysmiley25 on 2007-05-11
I am getting this error during install!

```

Package configuration                                                           
                                                                                
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring torrentflux &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                           &#9474;  
 &#9474; of any help, this was the error encountered:                              &#8593;  
 &#9474;                                                                           &#9618;  
 &#9474; ERROR 2002 (HY000): Can't connect to local MySQL server through socket    &#9618;  
 &#9474; '/var/run/mysqld/mysqld.sock' (2)                                         &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; At this point, you have the option to retry or abort the operation. If    &#9618;  
 &#9474; you choose "retry", you will be prompted with all the configuration       &#9618;  
 &#9474; questions once more and another attempt will be made at performing the    &#9618;  
 &#9474; operation. "retry (skip questions)" will immediately attempt the          &#9618;  
 &#9474; operation again, skipping all questions.  If you choose "abort", the      &#9618;  
 &#9474; operation will fail and you will need to downgrade, reinstall,            &#9618;  
 &#9474; reconfigure this package, or otherwise manually intervene to continue     &#9618;  
 &#9474; using it.  If you choose "ignore", the operation will continue, ignoring  &#9646;  
 &#9474; further errors from dbconfig-common.                                      &#8595;  
 &#9474;                                                                              
 &#9474;                                  <Ok>                                        
 &#9474;                                                                           &#9474;  
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;                                 

```

Can anyone help?

---

### Post by guysmiley25 on 2007-05-11
Ok so I think I'm getting somewhere but could still use some assistance.

I started again, From a command line system.

```

sudo aptitude install torrentflux mysql-server

```

At this screen go ok:
```

 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring libphp-adodb &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;     
     &#9474;                                                                    &#9474;     
     &#9474; WARNING: include path for php has changed!                         &#9474;     
     &#9474;                                                                    &#9474;     
     &#9474; libphp-adodb is no longer installed in /usr/share/adodb. New       &#9474;     
     &#9474; installation path is now /usr/share/php/adodb.                     &#9474;     
     &#9474;                                                                    &#9474;     
     &#9474; Please update your php.ini file. Maybe you must also change your   &#9474;     
     &#9474; web-server configuraton.                                           &#9474;     
     &#9474;                                                                    &#9474;     
     &#9474;                               <Ok>                                 &#9474;     
     &#9474;                                                                    &#9474;     
     &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;     

```

Now this bit is what seems to be the headache:
```

 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring torrentflux &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                           &#9474;  
 &#9474; torrentflux must have a database installed and configured before it can   &#9474;  
 &#9474; be used.  If you like, this can be handled with dbconfig-common.          &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; If you are an advanced database administrator and know that you want to   &#9474;  
 &#9474; perform this configuration manually, or if your database has already      &#9474;  
 &#9474; been installed and configured, you should refuse this option.  Details    &#9474;  
 &#9474; on what needs to be done should most likely be provided in                &#9474;  
 &#9474; /usr/share/doc/torrentflux.                                               &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Otherwise, you should probably choose this option.                        &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Configure database for torrentflux with dbconfig-common?                  &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474;                    <Yes>                       <No>                       &#9474;  
 &#9474;                                                                           &#9474;  
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;  

```

Selecting Yes ends up with an error??? So I carry on with No. 

Then here select yes:
```

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring torrentflux &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                           &#9474;  
 &#9474; Remember that in order to activate the new configuration apache2 has to   &#9474;  
 &#9474; be restarted. You can also restart apache2 by manually executing          &#9474;  
 &#9474; invoke-rc.d apache2 restart.                                              &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Should apache2 be restarted?                                              &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474;                    <Yes>                       <No>                       &#9474;  
 &#9474;                                                                           &#9474;  
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;  

```

Now it does not work. I guested that this was because I had to select no to dbconfig-common. So based on the instructions from this guide I tried this:
```

mysql -uroot -p
 mysql> use mysql;
 mysql > INSERT INTO user (Host,User,Password) VALUES('localhost','torrentflux',PASSWORD('yourpassword'));
 mysql > GRANT SELECT,INSERT,UPDATE,DELETE,CREATE,DROP ON torrentflux.* TO 'torrentflux'@'localhost';
 mysql > exit;

```

And then:
```

mysqladmin -utorrentflux -p create torrentflux
mysql -uroot -p torrentflux < mysql_torrentflux.sql

```

And then;
```

sudo nano /etc/torrentflux/config-db.php

```

And put in the username, password, and database.
```

$dbuser='torrentflux';
$dbpass='yourpassword';
$dbname='torrentflux';
$dbtype='mysq

```

And now if works!!! It was not before!!! oh well if anyone else if having problems thats how I got around it.

This was Ubuntu Feisty - Command Line System Only.

Thanks

---

### Post by Diaz on 2007-05-20
I installed torrentflux, everything seems fine except that when i try to view the page, it downloads the php file... how do i fix this...?

Thanks.

---

### Post by kebes on 2007-05-20
> **Diaz said:**
> I installed torrentflux, everything seems fine except that when i try to view the page, it downloads the php file... how do i fix this...?

Typically the problem is that you do not have php installed, or perhaps not activated. Make sure you have the packages "php5" and "php5-mysql" installed. Once they are installed, you need to reload apache for this to take effect. You can either reboot your computer, or just type this in a terminal:
```

sudo /etc/init.d/apache2 restart

```
(enter your passwrod when prompted)

If you go to the first post in this thread ([the howto]("http://ubuntuforums.org/showthread.php?t=268985")), go to step 1. Make sure you have those packages installed, and try that test page I suggested.

---

### Post by Diaz on 2007-05-20
I just tried your suggestion, but the test.php page tries to download the php file, and the torrentflux page still tries to make me download the file, so I assume php is not installing correctly...

Also, when I go to remove torrent flux, and it asks to remove the torrentflux database, it gives an error that says the torrentflux database does not exist...

---

### Post by Diaz on 2007-05-22
...bump, any chance of help?

---

### Post by kebes on 2007-05-22
> **Diaz said:**
> ...bump, any chance of help?

Just to be sure: You made sure that the "php5" package was installed, right? And then you restarted apache:
sudo /etc/init.d/apache2 restart


And yet PHP pages still do not parse?


If it's still not working, even with php5 installed, then you could try uninstalling and reinstalling php5. Any other details you could tell me about your setup might help (Ubuntu version? Apache 1.3 or 2? Does apache work at serving up normal HTML pages? etc.)

---

### Post by Diaz on 2007-05-22
Yes, I installed php5 and restarted apache, I am using ubuntu 7.04 fiesty server, Apache 2, and Apache serves up normal http pages fine.

I'm thinking I might just go for a clean install and try again if it makes no sense.

---

### Post by kebes on 2007-05-22
> **Diaz said:**
> Yes, I installed php5 and restarted apache, I am using ubuntu 7.04 fiesty server, Apache 2, and Apache serves up normal http pages fine.

I'm thinking I might just go for a clean install and try again if it makes no sense.

A clean install is certainly an option. Removing and re-installing apache2 and php5 is also worth a try. Did you install php using the repositories (apt-get or synaptic or whatever)?

Check in the directory:
/etc/apache2/mods-available
Make sure you have:
php5.conf
php5.load

On my system these files look like:
php5.conf
```
<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>

```
php5.load
```

LoadModule php5_module /usr/lib/apache2/modules/libphp5.so

```

Then check in:
/etc/apache2/mods-enabled/
And make sure there are symlinks to those two files.

If those files exist, then I can't see why apache wouldn't be loading php (unless you changed the default search path apache uses...).

---

### Post by guysmiley25 on 2007-05-22
It does indeed seem like php is not working, however you also said that the database did not exist. That sounds like the problem I had.

When I installed in feisty using aptitude, It did not create a database in mysql. To fix, I downloaded torrentflux from torrentflux, I had to get the database file and the scripts as well. I think this is a bug in feisty.

---

### Post by Diaz on 2007-05-22
> **kebes said:**
> A clean install is certainly an option. Removing and re-installing apache2 and php5 is also worth a try. Did you install php using the repositories (apt-get or synaptic or whatever)?

Check in the directory:
/etc/apache2/mods-available
Make sure you have:
php5.conf
php5.load

On my system these files look like:
php5.conf
```
<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>

```
php5.load
```

LoadModule php5_module /usr/lib/apache2/modules/libphp5.so

```

Then check in:
/etc/apache2/mods-enabled/
And make sure there are symlinks to those two files.

If those files exist, then I can't see why apache wouldn't be loading php (unless you changed the default search path apache uses...).

All that is in my apache folder, seems very weird... I'll try a clean install and see if it fixes it. Thanks for the help, I will get back when I finish the re-install.

---

### Post by hobs0n on 2007-07-01
First I wanna say: thank you all for this great guide! :)

This is my first Linux server Im using and I got the tip to use torrentflux. I checked your guide so I could get the latest version instead of the version that comes with synaptic. I followed your guide and it all worked well, untill the hend. At the part 4. d first login and I go to "http://localhost/torrentflux/" nothing happens, no errors but there is no page, just a white page with nothing in it. Any idea what might be wrong?

---

### Post by kebes on 2007-07-01
> **hobs0n said:**
> At the part 4. d first login and I go to "http://localhost/torrentflux/" nothing happens, no errors but there is no page, just a white page with nothing in it.

Hmm... That's strange. Normally there would be an error. What web browser are you using? When you get to that "white page," try looking at the source for the page. In Firefox, this would be View > Page Source (or do Ctrl+U). The source may hint at what's going on. Is the document empty? Does it contain any messages? If you don't know how to read HTML, you can post the source to this thread.

My best guess is that you have PHP installed but it isn't working properly. A default PHP install will deliver error messages, but there is a flag that suppresses these errors, so if a page render encounters and error, it displays a blank page instead.

When you were doing "Step 1: Get a LAMP Stack" did all the tests work? Did the simple PHP page show up properly?

If so, modify that test page like so:

```
$ sudo nano /var/www/test.php
```

And put this php code:
```

<html>
<head>
  <title>Test Page</title>
</head>
<body>
Test page<br />
<?php 
	echo 'If you can see this text, then PHP is working.';
        phpinfo();
?>
</body>
</html>

```

Then go to [http://localhost/test.php](http://localhost/test.php)
You should see the "...then PHP is working" message, plus a long listing of your PHP install. If this doesn't work, then your PHP is not working. If this listing does show up, you'll have all kinds of version information. See if it reports any errors.

Also, look through that and make sure that it has the mysql module installed. Also look for a line that says "display_errors" and see if that is "On" or "Off"... if it's "Off" then you should change your PHP config file so that it displays errors. This will help alot with getting things working.


Good luck! Let me know how it works out!

---

### Post by hobs0n on 2007-07-02
I use Firefox. I right clicked and clicked on View Page Source and the only thing that the page showed was: "<html></html>"

Yes, both the first and the test.php pages showed up correctly. 

The PHP info page from your PHP code all showed up normal I think, I dont know how errors would look tho.

Display errors was ON in both the categories.


> **kebes said:**
> Hmm... That's strange. Normally there would be an error. What web browser are you using? When you get to that "white page," try looking at the source for the page. In Firefox, this would be View > Page Source (or do Ctrl+U). The source may hint at what's going on. Is the document empty? Does it contain any messages? If you don't know how to read HTML, you can post the source to this thread.

My best guess is that you have PHP installed but it isn't working properly. A default PHP install will deliver error messages, but there is a flag that suppresses these errors, so if a page render encounters and error, it displays a blank page instead.

When you were doing "Step 1: Get a LAMP Stack" did all the tests work? Did the simple PHP page show up properly?

If so, modify that test page like so:

```
$ sudo nano /var/www/test.php
```

And put this php code:
```

<html>
<head>
  <title>Test Page</title>
</head>
<body>
Test page<br />
<?php 
	echo 'If you can see this text, then PHP is working.';
        phpinfo();
?>
</body>
</html>

```

Then go to [http://localhost/test.php](http://localhost/test.php)
You should see the "...then PHP is working" message, plus a long listing of your PHP install. If this doesn't work, then your PHP is not working. If this listing does show up, you'll have all kinds of version information. See if it reports any errors.

Also, look through that and make sure that it has the mysql module installed. Also look for a line that says "display_errors" and see if that is "On" or "Off"... if it's "Off" then you should change your PHP config file so that it displays errors. This will help alot with getting things working.


Good luck! Let me know how it works out!

---

### Post by kebes on 2007-07-02
Hmm... And you do indeed have the php-mysql module installed? (It should be listed on the php test page.)

I assume you are using apache as your webserver (version 1 or 2?). Have you made any custom changes to your apache configuration? (e.g. changed the file /etc/apache2/sites-available/default ) The next test I would do is to put that test file into the torrentflux directory:
```

cp /var/www/test.php /var/www/torrentflux/

```

Then go to that copy of the test page:
[http://localhost/torrentflux/test.php](http://localhost/torrentflux/test.php)

What happens then? Does the test page work? If it doesn't work, it means that apache is configured to ignore that directory, or maybe you didn't set permissions properly, so apache can't read the contents of that directory. 

If that test copy does work properly, try going to specific torrentflux php pages:
[http://localhost/torrentflux/index.php](http://localhost/torrentflux/index.php)
[http://localhost/torrentflux/login.php](http://localhost/torrentflux/login.php)
[http://localhost/torrentflux/admin.php](http://localhost/torrentflux/admin.php)

What do you get in those cases? An error? A white page? Does it redirect you before giving a white page? (e.g. you try to go to admin.php, it redirects you to login.php which is blank?)



As you can see, I really don't know what the problem is... but hopefully one of these tests will provide new insight into the problem.

---

### Post by hobs0n on 2007-07-03
Copying the test.php to the torrentlux dir worked. 

[http://localhost/torrentflux/index.php](http://localhost/torrentflux/index.php) shows nothing.

[http://localhost/torrentflux/login.php](http://localhost/torrentflux/login.php) and [http://localhost/torrentflux/admin.php](http://localhost/torrentflux/admin.php) shows:

[I]"Warning: include_once(adodb/adodb.inc.php) [function.include-once]: failed to open stream: No such file or directory in /var/www/torrentflux/db.php on line 5

Warning: include_once() [function.include]: Failed opening 'adodb/adodb.inc.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/torrentflux/db.php on line 5

Fatal error: Call to undefined function NewADOConnection() in /var/www/torrentflux/db.php on line 12"[/I]

Thank you for helping me so much :)

---

### Post by kebes on 2007-07-03
That's a good clue...

Check that those files exist:
```

cd /var/www/torrentflux/
ls -laF

```
should return a bunch of files... and one of them should be "config.php" Moreover "config.php" should be readable by the server (permissions should be something like -rwxr--r--). Then make sure that the directory "adodb" exists, and has read permissions. Then check what is inside that directory:
```

cd adodb
ls -laF

```

 There should be ~36 files (and "adodb.inc.php" should be one of them), with permissions like "-rw-r--r--". If this directory is empty, probably means that when you did the copy operation, you didn't copy recursively. (In the [instructions]("http://ubuntuforums.org/showthread.php?t=268985"), step 4.a. did you put the "-r" switch on the copy operation?)


If all of the files are present and have proper permissions, then it may mean that your PHP-mysql config is the problem. The most common problem is the mysql modules being installed but not activated. To do so you edit the file "/etc/php5/apache2/php.ini" (assuming you are using PHP 5.x and apache 2.x):
```

sudo nano /etc/php5/apache2/php.ini

```
And make sure that you have lines that look like:
```

extension=mysql.so
extension=mysqli.so

```
(The lines may already have been added, so do a quick search. It is likely that they (also) appear in the file, commented out with a ; in front of them. If they don't appear elsewhere, you can remove the ; and save the file.) Remember you need to restart apache after making any change to that file. (Reboot computer or just do "sudo /etc/init.d/apache2 restart".)


> **hobs0n said:**
> Thank you for helping me so much :)

You're very welcome. Let me know whether those suggestions work out...

---

### Post by hobs0n on 2007-07-04
Hm the directory adodb doesnt exist, I even searched the whole computer for it and it didnt exist. I guess this means that something went wrong with the installation of Torrentflux?

---

### Post by kebes on 2007-07-04
> **hobs0n said:**
> Hm the directory adodb doesnt exist, I even searched the whole computer for it and it didnt exist. I guess this means that something went wrong with the installation of Torrentflux?

Indeed. I believe you said you manually downloaded the tarball from the torrentflux website? Then you presumably extracted it and copied the files to /var/www/torrentflux

Is that correct?

You should go back to those steps. Re-download the tarball, and extract it to a temporary directory. Make sure it contains all the subdirectories and files therein. Then copy all of that to your web directory. Maybe your download was corrupt or the extraction didn't work the first time around...?

---

### Post by hobs0n on 2007-07-06
I want to thank you for all help but I will not use Torrentflux since the torrent sites I download stuff from dont have a module for it so it feels a bit too much work. Ill use Azuerus instead :)

Thank you again for all your help, its ppl like you that make ppl want to use Linux :)

---

### Post by arrrghhh on 2007-07-07
nvm, got it to work... i LOVE this!

question: can i setup multiple computers to download the same file?  ie, use 2 completely separate computers (on different connections) to pool bandwidth?  my comp @ work has all kindsa b/w...  thanks again for the tut!

that probably wouldn't work as well as i would hope... it would probably work if they were on the same local network... but across the internet it would be like my work computer is just another peer in the pool...

---

### Post by kebes on 2007-07-08
> **arrrghhh said:**
> question: can i setup multiple computers to download the same file?  ie, use 2 completely separate computers (on different connections) to pool bandwidth?  my comp @ work has all kindsa b/w...  thanks again for the tut!

that probably wouldn't work as well as i would hope... it would probably work if they were on the same local network... but across the internet it would be like my work computer is just another peer in the pool...

Yes if both computers join the same torrent then they become peers. This doesn't help for download speed much, but it at least decreases the chance that the torrent dies without you getting all of it, because you will have two computers downloading and hopefully they will together have the entire file.

In principle you could have both of them downloading the file, and sending each other the bits they download. But no torrent downloader I'm aware of supports this... and besides it's not clear that this would actually speed anything up.

If you have two computers, and one is on a faster connection, it can sometimes be faster to let it download the entire file (via bittorrent) and then copy it to the second computer via FTP. Even though it's a two-step process, the faster connection can make a big difference for well-seeded files.

---

### Post by arrrghhh on 2007-07-08
> **kebes said:**
> Yes if both computers join the same torrent then they become peers. This doesn't help for download speed much, but it at least decreases the chance that the torrent dies without you getting all of it, because you will have two computers downloading and hopefully they will together have the entire file.

In principle you could have both of them downloading the file, and sending each other the bits they download. But no torrent downloader I'm aware of supports this... and besides it's not clear that this would actually speed anything up.

If you have two computers, and one is on a faster connection, it can sometimes be faster to let it download the entire file (via bittorrent) and then copy it to the second computer via FTP. Even though it's a two-step process, the faster connection can make a big difference for well-seeded files.

yea, pretty much what i was thinkin after i asked the question.  thanks for the info!

---

### Post by deezay on 2007-07-12
i get this error...

Warning: mysql_connect() [function.mysql-connect]: Access denied for user 'www-data'@'localhost' (using password: NO) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 354

when trying [http://localhost/torrentflux/](http://localhost/torrentflux/)

any help would be appreciated.

---

### Post by kebes on 2007-07-12
> **deezay said:**
> i get this error...

Warning: mysql_connect() [function.mysql-connect]: Access denied for user 'www-data'@'localhost' (using password: NO) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 354

when trying [http://localhost/torrentflux/](http://localhost/torrentflux/)

any help would be appreciated.

Probably you need to complete Step 4c of the [how-to]("http://ubuntuforums.org/showthread.php?t=268985"). Basically you need to edit the file "/var/www/torrentflux/config.php", and input the username and password for the MySQL database that you set up for torrentflux.

(This is assuming you've already set up a torrentflux user in MySQL... if not, see the steps previous to that one...)

---

### Post by deezay on 2007-07-13
nope i;ve followed all of the steps up until that point. when i add in the user for step 4c it doesn't show up in the config file. there is another config file in the /var/www/torrentflux/html folder. i copied the contents of that one into the file in the main dir. and it does still not get updated with the mysql commands. any other ideas why this isn't working??

---

### Post by deezay on 2007-07-13
Not Found

The requested URL /torrentflux/function.mysql-connect was not found on this server

is one of the errors. where is this file?

---

### Post by kebes on 2007-07-13
> **deezay said:**
> there is another config file in the /var/www/torrentflux/html folder. i copied the contents of that one into the file in the main dir. 

I don't know why you have a "html" directory in the torrentflux directory. When you initially extracted the torrentflux files, did you copy the html directory to /var/www/torrentflux/ or did you copy the *contents* of the html directory to /var/www/torrentflux ??

Perhaps you could post the output of these commands:
ls -laF /var/www/torrentflux/
ls -laF /var/www/torrentflux/html/



> **deezay said:**
> when i add in the user for step 4c it doesn't show up in the config file. ... and it does still not get updated with the mysql commands.

The MySQL commands update the MySQL database, but you have to **manually** update the file /var/www/torrentflux/config.php

So, you need to open that file, config.php, and change the lines so that they match the username, password, and database name you decided to use in the previous step. Then save the file.

---

### Post by deezay on 2007-07-13
i appreciate all the help. i copied the config.php from /var/www/torrentflux/html and put it into var/www/torrentflux. i'm also using the newest copy.. 2.3.2 i think. maybe this makes a difference? 

outputs as requested...

> andrew@andrew-linux:~$ ls -laF /var/www/torrentflux/
total 88
drwxr-xr-x 5 andrew andrew  4096 2007-07-13 17:37 ./
drwxr-xr-x 4 root   root    4096 2007-07-13 07:14 ../
-rwxr--r-- 1 andrew andrew  6773 2007-07-12 21:03 CHANGELOG*
-rwxr--r-- 1 andrew andrew  3878 2007-07-13 17:37 config.php*
-rw-r--r-- 1 andrew andrew  3872 2007-07-13 17:36 config.php~
-rwxr--r-- 1 andrew andrew 15237 2007-07-12 21:03 COPYING*
drwxr-xr-x 9 andrew andrew  4096 2007-07-13 17:37 html/
-rwxr--r-- 1 andrew andrew 10695 2007-07-12 21:03 INSTALL*
-rwxr--r-- 1 andrew andrew  6092 2007-07-12 21:03 mysql_torrentflux.sql*
-rwxr--r-- 1 andrew andrew   290 2007-07-12 21:03 pgsql_01_create_db_and_user.sql*
-rwxr--r-- 1 andrew andrew  5507 2007-07-12 21:03 pgsql_02_create_tables.sql*
-rwxr--r-- 1 andrew andrew   822 2007-07-12 21:03 README*
drwxr-xr-x 2 andrew andrew  4096 2007-07-12 21:03 sql/
drwxr-xr-x 2 andrew andrew  4096 2007-07-12 21:03 upgrades/

and...


> andrew@andrew-linux:~$ ls -laF /var/www/torrentflux/html/
total 596
drwxr-xr-x  9 andrew andrew  4096 2007-07-13 17:37 ./
drwxr-xr-x  5 andrew andrew  4096 2007-07-13 17:37 ../
-rwxr--r--  1 andrew andrew 90289 2007-07-12 21:03 admin.php*
drwxr-xr-x 11 andrew andrew  4096 2007-07-12 21:03 adodb/
-rwxr--r--  1 andrew andrew  5471 2007-07-12 21:03 AliasFile.php*
-rwxr--r--  1 andrew andrew  1958 2007-07-12 21:03 all_services.php*
-rwxr--r--  1 andrew andrew  7199 2007-07-12 21:03 BDecode.php*
-rwxr--r--  1 andrew andrew    70 2007-07-12 21:03 blank.html*
-rwxr--r--  1 andrew andrew  3878 2007-07-13 17:37 config.php*
-rw-r--r--  1 andrew andrew  3872 2007-07-13 17:37 config.php~
-rwxr--r--  1 andrew andrew  2623 2007-07-12 21:03 cookiehelp.php*
-rwxr--r--  1 andrew andrew  2958 2007-07-12 21:03 db.php*
-rwxr--r--  1 andrew andrew  1808 2007-07-12 21:03 details.php*
-rwxr--r--  1 andrew andrew 18689 2007-07-12 21:03 dir.php*
-rwxr--r--  1 andrew andrew  6723 2007-07-12 21:03 downloaddetails.php*
drwxr-xr-x  2 andrew andrew  4096 2007-07-12 21:03 downloads/
-rwxr--r--  1 andrew andrew  1726 2007-07-12 21:03 drivespace.php*
-rwxr--r--  1 andrew andrew   794 2007-07-12 21:03 dtree.css*
-rwxr--r--  1 andrew andrew 13523 2007-07-12 21:03 dtree.js*
-rwxr--r--  1 andrew andrew  2238 2007-07-12 21:03 favicon.ico*
-rwxr--r--  1 andrew andrew 86831 2007-07-12 21:03 functions.php*
-rwxr--r--  1 andrew andrew  5993 2007-07-12 21:03 history.php*
drwxr-xr-x  4 andrew andrew  4096 2007-07-12 21:03 images/
-rwxr--r--  1 andrew andrew 34943 2007-07-12 21:03 index.php*
drwxr-xr-x  2 andrew andrew  4096 2007-07-12 21:03 language/
-rwxr--r--  1 andrew andrew  8440 2007-07-12 21:03 lastRSS.php*
-rwxr--r--  1 andrew andrew 11652 2007-07-12 21:03 login.php*
-rwxr--r--  1 andrew andrew  1625 2007-07-12 21:03 logout.php*
-rwxr--r--  1 andrew andrew 25368 2007-07-12 21:03 maketorrent.php*
-rwxr--r--  1 andrew andrew  3948 2007-07-12 21:03 message.php*
-rwxr--r--  1 andrew andrew  8417 2007-07-12 21:03 metaInfo.php*
-rwxr--r--  1 andrew andrew  5186 2007-07-12 21:03 multi.php*
-rwxr--r--  1 andrew andrew 44818 2007-07-12 21:03 overlib.js*
-rwxr--r--  1 andrew andrew 17756 2007-07-12 21:03 profile.php*
-rwxr--r--  1 andrew andrew  6000 2007-07-12 21:03 readmsg.php*
-rwxr--r--  1 andrew andrew  7649 2007-07-12 21:03 readrss.php*
-rwxr--r--  1 andrew andrew  4773 2007-07-12 21:03 RunningTorrent.php*
drwxr-xr-x  2 andrew andrew  4096 2007-07-12 21:03 searchEngines/
-rwxr--r--  1 andrew andrew  3055 2007-07-12 21:03 setpriority.php*
-rwxr--r--  1 andrew andrew  5672 2007-07-12 21:03 settingsfunctions.php*
-rwxr--r--  1 andrew andrew  8939 2007-07-12 21:03 startpop.php*
drwxr-xr-x  4 andrew andrew  4096 2007-07-12 21:03 TF_BitTornado/
drwxr-xr-x 17 andrew andrew  4096 2007-07-12 21:03 themes/
-rwxr--r--  1 andrew andrew 17889 2007-07-12 21:03 tooltip.js*
-rwxr--r--  1 andrew andrew  7465 2007-07-12 21:03 torrentSearch.php*
-rwxr--r--  1 andrew andrew  2756 2007-07-12 21:03 viewnfo.php*
-rwxr--r--  1 andrew andrew  1813 2007-07-12 21:03 who.php*


---

### Post by kebes on 2007-07-14
Aha! So if you open a web-browser and go to:
[http://localhost/torrentflux/html/](http://localhost/torrentflux/html/)

Does it work, or do you get an error?

Apparently you copied the entire install folder to /var/www/ (instead of just the contents of the html sub-directory). This means that your installation of torrentflux will appear on the webserver at [http://localhost/torrentflux/html/](http://localhost/torrentflux/html/) instead of just [http://localhost/torrentflux/](http://localhost/torrentflux/)

But it should still work from that location. If you really don't like having the "html" in the web-address, you can move all the files.

So, if [http://localhost/torrentflux/html/](http://localhost/torrentflux/html/) works properly, you're done. If it doesn't work perfectly, make sure the config file [http://localhost/torrentflux/html/config.php](http://localhost/torrentflux/html/config.php) has the correct values, and try again!

---

### Post by deezay on 2007-07-14
ok i moved all the files from the html directory into the main /var/www/torrentflux one. everything looks right in the config file but it's still giving me the www-data user error. i'm pretty much handicapped in this department (php, apache,mysql) i added the myphpadmin program but have no idea how to use it. i really do appreciate alll the help

---

### Post by kebes on 2007-07-15
> **deezay said:**
> ok i moved all the files from the html directory into the main /var/www/torrentflux one. everything looks right in the config file but it's still giving me the www-data user error. i'm pretty much handicapped in this department (php, apache,mysql) i added the myphpadmin program but have no idea how to use it. i really do appreciate alll the help

You're very welcome for the help. However I'm going to need more information to figure this out.

First, it would help if you posted the contents of the file "/var/www/torrentflux/config.php" You can change the password string to something else (like *****) before posting, so as to not reveal your password.

Then, go into phpmyadmin:
[http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)
Click "Databases". Make sure there is a database called "torrentflux"... then click on it. It should list these tables:
```

| tf_cookies            |
| tf_links              |
| tf_log                |
| tf_messages           |
| tf_rss                |
| tf_settings           |
| tf_users 

```
If it doesn't list that, post what it shows you. Then in phpmyadmin click the home icon (little house in the left panel), and then click "Privileges". You should have a line like:
```

torfluxuser  	localhost  	Yes  	 USAGE   	No  	

```
(Again, if you don't have that line, let me know.) Click on the "Edit" icon (on the far right) for that user. Then, in the section "Database-specific privileges" it should list something like:
```

torrentflux  	 SELECT, INSERT, UPDATE, DELETE, CREATE, DROP   	No  	No

```


If any of the above things look different in your installation (name different, or something is missing), describe it in your follow-up post.

> Warning: mysql_connect() [function.mysql-connect]: Access denied for user 'www-data'@'localhost' (using password: NO) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 354

Torrentflux should not be trying to use "www-data" as the username. So either the config.php file isn't specifying a username/password, or the username doesn't exist in MySQL. The above steps should let us know which one is the case.

---

### Post by deezay on 2007-07-15
everything in myphpadmin looks correct to what you posted. and here is my config file..

> <?php



/*************************************************************

*  TorrentFlux PHP Torrent Manager

*  [www.torrentflux.com](www.torrentflux.com)

**************************************************************/

/*

    This file is part of TorrentFlux.



    TorrentFlux is free software; you can redistribute it and/or modify

    it under the terms of the GNU General Public License as published by

    the Free Software Foundation; either version 2 of the License, or

    (at your option) any later version.



    TorrentFlux is distributed in the hope that it will be useful,

    but WITHOUT ANY WARRANTY; without even the implied warranty of

    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the

    GNU General Public License for more details.



    You should have received a copy of the GNU General Public License

    along with TorrentFlux; if not, write to the Free Software

    Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA  02111-1307  USA

*/





/**************************************************************************/

// YOUR DATABASE CONNECTION INFORMATION

/**************************************************************************/

// Check the adodb/drivers/ directory for support for your database

// you may choose from many (mysql is the default)

$cfg["db_type"] = "mysql";       // mysql, postgres7 view adodb/drivers/

$cfg["db_host"] = "localhost";   // DB host computer name or IP

$cfg["db_name"] = "torrentflux"; // Name of the Database

$cfg["db_user"] = "root";        // username for your MySQL database

$cfg["db_pass"] = "***************";            // password for database

$cfg["db_user"] = "andrew-linux";        // username for your MySQL database

$cfg["db_pass"] = "*************";            // password for database

$cfg["db_user"] = "torfluxuser";        // username for your MySQL database

$cfg["db_pass"] = "**********";            // password for database

/**************************************************************************/





/*****************************************************************************

    TorrentFlux

    Torrent (n.) A violent or rapid flow; a strong current; a flood;

            as, a torrent vices; a torrent of eloquence.

    Flux    (n.) The act of flowing; a continuous moving on or passing by,

            as of a flowing stream; constant succession; change.

*****************************************************************************/







// ***************************************************************************

// ***************************************************************************

// DO NOT Edit below this line unless you know what you're doing.

// ***************************************************************************

// ***************************************************************************



$cfg["pagetitle"] = "TorrentFlux";



// TorrentFlux Version

$cfg["version"] = "2.3";



// CONSTANTS

$cfg["constants"] = array();

$cfg["constants"]["url_upload"] = "URL Upload";

$cfg["constants"]["reset_owner"] = "Reset Owner";

$cfg["constants"]["start_torrent"] = "Started Torrent";

$cfg["constants"]["queued_torrent"] = "Queued Torrent";

$cfg["constants"]["unqueued_torrent"] = "Removed from Queue";

$cfg["constants"]["QManager"] = "QManager";

$cfg["constants"]["access_denied"] = "ACCESS DENIED";

$cfg["constants"]["delete_torrent"] = "Delete Torrent";

$cfg["constants"]["fm_delete"] = "File Manager Delete";

$cfg["constants"]["fm_download"] = "File Download";

$cfg["constants"]["kill_torrent"] = "Kill Torrent";

$cfg["constants"]["file_upload"] = "File Upload";

$cfg["constants"]["error"] = "ERROR";

$cfg["constants"]["hit"] = "HIT";

$cfg["constants"]["update"] = "UPDATE";

$cfg["constants"]["admin"] = "ADMIN";



asort($cfg["constants"]);



// Add file extensions here that you will allow to be uploaded

$cfg["file_types_array"] = array("torrent");



// Capture username

$cfg["user"] = "";

// Capture ip

$cfg["ip"] = $_SERVER['REMOTE_ADDR'];



?>



and all of this looks correct too. i'm at a complete loss.

---

### Post by kebes on 2007-07-15
You shouldn't have multiple user/password declarations. The section where it says:
```

$cfg["db_type"] = "mysql"; // mysql, postgres7 view adodb/drivers/
$cfg["db_host"] = "localhost"; // DB host computer name or IP
$cfg["db_name"] = "torrentflux"; // Name of the Database
$cfg["db_user"] = "root"; // username for your MySQL database
$cfg["db_pass"] = "***************"; // password for database
$cfg["db_user"] = "andrew-linux"; // username for your MySQL database
$cfg["db_pass"] = "*************"; // password for database
$cfg["db_user"] = "torfluxuser"; // username for your MySQL database
$cfg["db_pass"] = "**********"; // password for database

```

Should just be:
```

$cfg["db_type"] = "mysql"; // mysql, postgres7 view adodb/drivers/
$cfg["db_host"] = "localhost"; // DB host computer name or IP
$cfg["db_name"] = "torrentflux"; // Name of the Database
$cfg["db_user"] = "torfluxuser"; // username for your MySQL database
$cfg["db_pass"] = "**********"; // password for database

```

Still, I doubt that will fix this problem. But with that correction, when you go to the page:
[http://localhost/torrentflux/](http://localhost/torrentflux/)
Do you get the error:
> 
Warning: mysql_connect() [function.mysql-connect]: Access denied for user 'www-data'@'localhost' (using password: NO) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 354


?? Does the error really say "user 'www-data@localhost (using password:NO)" ??

Also, now that you've moved the files, what do these command return:
ls -laF /var/www/torrentflux/
ls -laF /var/www/torrentflux/adodb/

---

### Post by deezay on 2007-07-15
ok, changed the config. localhost/torrentflux still gives the same error. and yes it really does say www-data. thats what i can't figure out since NOTHING i have says www-data. but here's the results of the commands you listed...

ls -laF /var/www/torrentflux/
> andrew@andrew-linux:~$ ls -laF /var/www/torrentflux/
total 596
drwxr-xr-x  9 andrew andrew  4096 2007-07-15 19:50 ./
drwxr-xr-x  4 root   root    4096 2007-07-13 07:14 ../
-rwxr--r--  1 andrew andrew 90289 2006-12-12 22:29 admin.php*
drwxr-xr-x 11 andrew andrew  4096 2006-12-12 23:56 adodb/
-rwxr--r--  1 andrew andrew  5471 2006-10-19 09:54 AliasFile.php*
-rwxr--r--  1 andrew andrew  1958 2006-10-19 09:54 all_services.php*
-rwxr--r--  1 andrew andrew  7199 2006-10-19 09:54 BDecode.php*
-rwxr--r--  1 andrew andrew    70 2006-10-19 09:54 blank.html*
-rwxr--r--  1 andrew andrew  3743 2007-07-15 19:50 config.php*
-rw-r--r--  1 andrew andrew  4023 2007-07-15 11:21 config.php~
-rwxr--r--  1 andrew andrew  2623 2006-10-19 09:54 cookiehelp.php*
-rwxr--r--  1 andrew andrew  2958 2006-10-19 09:54 db.php*
-rwxr--r--  1 andrew andrew  1808 2006-12-11 22:28 details.php*
-rwxr--r--  1 andrew andrew 18689 2006-12-12 00:37 dir.php*
-rwxr--r--  1 andrew andrew  6723 2006-12-11 22:28 downloaddetails.php*
drwxr-xr-x  2 andrew andrew  4096 2006-12-12 23:56 downloads/
-rwxr--r--  1 andrew andrew  1726 2006-10-19 09:54 drivespace.php*
-rwxr--r--  1 andrew andrew   794 2006-10-19 09:54 dtree.css*
-rwxr--r--  1 andrew andrew 13523 2006-10-19 09:54 dtree.js*
-rwxr--r--  1 andrew andrew  2238 2006-10-19 09:54 favicon.ico*
-rwxr--r--  1 andrew andrew 86831 2006-12-12 00:07 functions.php*
-rwxr--r--  1 andrew andrew  5993 2006-10-19 09:54 history.php*
drwxr-xr-x  4 andrew andrew  4096 2006-12-12 23:56 images/
-rwxr--r--  1 andrew andrew 34943 2006-12-12 00:48 index.php*
drwxr-xr-x  2 andrew andrew  4096 2006-12-12 23:56 language/
-rwxr--r--  1 andrew andrew  8440 2006-10-19 09:54 lastRSS.php*
-rwxr--r--  1 andrew andrew 11652 2006-12-12 22:32 login.php*
-rwxr--r--  1 andrew andrew  1625 2006-10-19 09:54 logout.php*
-rwxr--r--  1 andrew andrew 25368 2006-12-12 01:00 maketorrent.php*
-rwxr--r--  1 andrew andrew  3948 2006-10-19 09:54 message.php*
-rwxr--r--  1 andrew andrew  8417 2006-12-12 01:00 metaInfo.php*
-rwxr--r--  1 andrew andrew  5186 2006-10-19 09:54 multi.php*
-rwxr--r--  1 andrew andrew 44818 2006-10-19 09:54 overlib.js*
-rwxr--r--  1 andrew andrew 17756 2006-10-19 09:54 profile.php*
-rwxr--r--  1 andrew andrew  6000 2006-11-15 23:26 readmsg.php*
-rwxr--r--  1 andrew andrew  7649 2006-10-19 09:54 readrss.php*
-rwxr--r--  1 andrew andrew  4773 2006-10-19 09:54 RunningTorrent.php*
drwxr-xr-x  2 andrew andrew  4096 2006-12-12 23:56 searchEngines/
-rwxr--r--  1 andrew andrew  3055 2006-10-19 09:54 setpriority.php*
-rwxr--r--  1 andrew andrew  5672 2006-12-12 00:17 settingsfunctions.php*
-rwxr--r--  1 andrew andrew  8939 2006-12-11 22:29 startpop.php*
drwxr-xr-x  4 andrew andrew  4096 2006-12-12 23:56 TF_BitTornado/
drwxr-xr-x 17 andrew andrew  4096 2006-12-12 23:56 themes/
-rwxr--r--  1 andrew andrew 17889 2006-10-19 09:54 tooltip.js*
-rwxr--r--  1 andrew andrew  7465 2006-10-19 09:54 torrentSearch.php*
-rwxr--r--  1 andrew andrew  2756 2006-11-22 09:11 viewnfo.php*
-rwxr--r--  1 andrew andrew  1813 2006-10-19 09:54 who.php*

and ls -laF /var/www/torrentflux/adodb/

> andrew@andrew-linux:~$ ls -laF /var/www/torrentflux/adodb/
total 580
drwxr-xr-x 11 andrew andrew   4096 2006-12-12 23:56 ./
drwxr-xr-x  9 andrew andrew   4096 2007-07-15 19:51 ../
-rwxr--r--  1 andrew andrew  12993 2006-10-19 09:54 adodb-active-record.inc.php*
-rwxr--r--  1 andrew andrew   8615 2006-10-19 09:54 adodb-csvlib.inc.php*
-rwxr--r--  1 andrew andrew  21824 2006-10-19 09:54 adodb-datadict.inc.php*
-rwxr--r--  1 andrew andrew   2827 2006-10-19 09:54 adodb-errorhandler.inc.php*
-rwxr--r--  1 andrew andrew   8798 2006-10-19 09:54 adodb-error.inc.php*
-rwxr--r--  1 andrew andrew   2362 2006-10-19 09:54 adodb-errorpear.inc.php*
-rwxr--r--  1 andrew andrew   2295 2006-10-19 09:54 adodb-exceptions.inc.php*
-rwxr--r--  1 andrew andrew 118558 2006-10-19 09:54 adodb.inc.php*
-rwxr--r--  1 andrew andrew   1680 2006-10-19 09:54 adodb-iterator.inc.php*
-rwxr--r--  1 andrew andrew  32748 2006-10-19 09:54 adodb-lib.inc.php*
-rwxr--r--  1 andrew andrew   8406 2006-10-19 09:54 adodb-pager.inc.php*
-rwxr--r--  1 andrew andrew   9935 2006-10-19 09:54 adodb-pear.inc.php*
-rwxr--r--  1 andrew andrew  31744 2006-10-19 09:54 adodb-perf.inc.php*
-rwxr--r--  1 andrew andrew    334 2006-10-19 09:54 adodb-php4.inc.php*
-rwxr--r--  1 andrew andrew  40685 2006-10-19 09:54 adodb-time.inc.php*
-rwxr--r--  1 andrew andrew  64757 2006-10-19 09:54 adodb-xmlschema03.inc.php*
-rwxr--r--  1 andrew andrew  57552 2006-10-19 09:54 adodb-xmlschema.inc.php*
drwxr-xr-x  2 andrew andrew   4096 2006-12-12 23:56 contrib/
drwxr-xr-x  2 andrew andrew   4096 2006-12-12 23:56 datadict/
drwxr-xr-x  2 andrew andrew   4096 2006-12-12 23:56 docs/
drwxr-xr-x  2 andrew andrew   4096 2006-12-12 23:56 drivers/
-rwxr--r--  1 andrew andrew     13 2006-10-19 09:54 index.html*
drwxr-xr-x  2 andrew andrew   4096 2006-12-12 23:56 lang/
-rwxr--r--  1 andrew andrew  26079 2006-10-19 09:54 license.txt*
drwxr-xr-x  3 andrew andrew   4096 2006-12-12 23:56 pear/
drwxr-xr-x  2 andrew andrew   4096 2006-12-12 23:56 perf/
-rwxr--r--  1 andrew andrew   6493 2006-10-19 09:54 pivottable.inc.php*
-rwxr--r--  1 andrew andrew   1731 2006-10-19 09:54 readme.txt*
-rwxr--r--  1 andrew andrew   1574 2006-10-19 09:54 rsfilter.inc.php*
-rwxr--r--  1 andrew andrew   2398 2006-10-19 09:54 server.php*
drwxr-xr-x  3 andrew andrew   4096 2006-12-12 23:56 session/
-rwxr--r--  1 andrew andrew   3473 2006-10-19 09:54 toexport.inc.php*
-rwxr--r--  1 andrew andrew   5718 2006-10-19 09:54 tohtml.inc.php*
-rwxr--r--  1 andrew andrew   1719 2006-10-19 09:54 xmlschema03.dtd*
-rwxr--r--  1 andrew andrew   1491 2006-10-19 09:54 xmlschema.dtd*
drwxr-xr-x  2 andrew andrew   4096 2006-12-12 23:56 xsl/


---

### Post by kebes on 2007-07-15
> **deezay said:**
> ok, changed the config. localhost/torrentflux still gives the same error. and yes it really does say www-data. thats what i can't figure out since NOTHING i have says www-data. but here's the results of the commands you listed...

ls -laF /var/www/torrentflux/


and ls -laF /var/www/torrentflux/adodb/

Hmm... "www-data" is the username that the web-server runs as. Getting the error "denied for user 'www-data'@'localhost' (using password: NO)" means that the username and password for the MySQL connection are not being set... which is weird because you obviously have them set in the config file.


I'm not sure what the problem is. These are the only options I can think of:


1. Start over
Did you install torrentflux from the repositories? (e.g. using Synaptic or apt-get) ...or did you download the torrentflux files manually? Did you try both?

You could delete the torrentflux folder from /var/www/ ... download and unpack the files again, and go through the steps again. Or, if you downloaded the files before, try using Synaptic or apt-get to install it automatically.


2. Diagnostics
You could try various tests to locate the problem... but this may get tedious. For instance, in the config.php file, change the line
$cfg["db_host"] = "localhost";
to
$cfg["db_host"] = "www.example.com";

This will not work, of course... but the important thing is to see if the error changes to:
...denied for user 'www-data'@'www.example.com' (using password: NO)...
Or whether it stays the same. This may be a clue. Also try changing the username or password to incorrect values, and see if that changes the error.

Also, I would try manually going to certain torrentflux pages and see what happens:
[http://localhost/torrentflux/](http://localhost/torrentflux/)
[http://localhost/torrentflux/index.php](http://localhost/torrentflux/index.php)
[http://localhost/torrentflux/login.php](http://localhost/torrentflux/login.php)
[http://localhost/torrentflux/admin.php](http://localhost/torrentflux/admin.php)

Depending on what the errors are, we may get a clue.

---

### Post by deezay on 2007-07-15
ok i did sudo apt-remove torrentflux and deleted the files and redownloaded the source. went through everything again. now it gives me a slightly different error. but i've double checked and all my passwords are correct.. below is the error..

Warning: mysql_connect() [function.mysql-connect]: Access denied for user 'andrew'@'localhost' (using password: YES) in /var/www/torrentflux/adodb/drivers/adodb-mysql.inc.php on line 355

so atleast we are getting somewhere.

---

### Post by kebes on 2007-07-16
> **deezay said:**
> ok i did sudo apt-remove torrentflux 
So was your previous installation done via apt-get or manually?

> now it gives me a slightly different error. but i've double checked and all my passwords are correct.. below is the error..

The error is for user "andrew" ... but presumably in your torrentflux config.php file you set the user to "torfluxuser" right?

So what's in your config.php file?
$cfg["db_user"] = "torfluxuser";
or
$cfg["db_user"] = "andrew";


When you went through the install steps again, did you delete and recreate the MySQL database and a MySQL user?

---

### Post by uncleant on 2007-07-16
I'm having a problem with step 4a.  Everything to this point works as it should.  
When I input this:
$ sudo chown user:user /var/www/torrentflux/ 
I get this error message:
chown: `user:user': invalid user
I've tried using my user name and that doesn't work either.  It's probably something I've over looked.  Any help would be appreciated.

---

### Post by uncleant on 2007-07-16
Yep, it was my own stupidity.  The answer was right there.  I just didn't read further.
On with the install.

---

### Post by bren21 on 2007-07-22
I'm having a weird problem, and I don't know why. For some reason, when I go to localhost/torrentflux I get a 404 not found. I triple checked and made sure the folder was in var/www and I just can't understand why this would happen. I copied all the files from the html folder and put them in torrentflux folder, so I know that's not the problem, and I checked the webserver by creating a directory named test in the root, and putting a simple test file in it. I also checked to see if php worked, and everything else. It is just acting as if the directory doesn't exist.




EDIT: I fixed the problem by renaming the folder, though I still don't know why that happened.

---

### Post by dsewell on 2007-07-27
Hi guys, and MANY THANKS for a very detailed How-to.

I have read this thread start to finish, and have made progress, but...

I am running Ubuntu Edgy and TorrentFlux 2.3.  I have followed this How-to and performed a manual install, along with PHP, mysql, Apache2, etc...

I can access TorrentFlux when I go to [http://localhost/torrentflux/](http://localhost/torrentflux/) but there are 2 problems: 

1) When I click "Run Torrent" nothing happens.  The status stays at 0.0% and the Estimated Time shows Starting.  And, I can see the .torrent and .stat files in the /,torrents/ directory, but they are not starting to download!

2) Not all of the web-pages are loading.  For example, most of the buttons are missing the images.  See attached.

Any ideas whats going on?

Cheers.

---

### Post by kebes on 2007-07-27
> **dsewell said:**
> 1) When I click "Run Torrent" nothing happens.  The status stays at 0.0% and the Estimated Time shows Starting.  And, I can see the .torrent and .stat files in the /,torrents/ directory, but they are not starting to download!

2) Not all of the web-pages are loading.  For example, most of the buttons are missing the images.  See attached.

One explanation would be missing/corrupted files/directories from the install. If you go into your torrentflux folder, do you have an "images" folder with images in it?
cd /var/www/torrentflux/images/
ls -laF

Also the permissions on the images directory must have "read" and "execute" set for the web-server. So you should see something like:
cd /var/www/torrentflux/
ls -laF

...
drwxr-xr-x  4 user user  4096 2006-09-30 23:38 images/
...

Notice that in the "drwxr-xr-x" the last three flags are "r-x" which means that anyone (in particular the web-server) can read and execute (enter) that directory. If those are not set properly use chmod to change them. If that directory was not set right, then your other problems are probably similar permissions issues.


If you want, you can print your entire directory listing to a file by doing:
ls -laF -R /var/www/torrentflux > ~/tmp/listing_output.txt

You can then post the contents of that file to this thread... maybe there are files missing or files with incorrect permissions.


Hope that helps.

---

### Post by beerfan on 2007-07-29
I just tried installing torrentflux from the repository and I had some of the same issues people have mentioned. A gui dbconfig came up after the package was installed but dbconfig would not accept my mysql root password (I use mysql daily so I'm quite certain the problem is not with mysql). I closed that out and dug into /etc/torrentflug/config-db.php and etc/dbconfig-common/torrentflux.conf to see if I could manually install it. I tried reinstalling it with "dpkg-reconfigure torrentflux" as suggested which uses the curses based dbconfig-common but this worked no better than the gnome version. Oddly, sometimes it fails saying it cannot connect with 'root'@'localhost' password no but it never asks for a password and other times it goes through as if successful and asks if apache should be restarted but after its all done the config-db.php is not changed and the database is never created.

Giving up on that, I figured I could just manually create the database so I created the database and user account and set up the tables with the sql file in /usr/share/doc/torrentflux/dbfiles/mysql.gz. I get the torrentflux login screen when I browse [http://localhost/torrentflux/](http://localhost/torrentflux/) but...there are no user accounts to login with. The tf_users table is empty so I assume that the install process must create that and I'm out of luck since I created the database manually. I tried inserting a user account but if was not accepted for any number of possible reasons (password not hashed, invalid value in some other field). I may break down and examine the code but so far I'm pretty annoyed.

I don't know how dbconfig-common is supposed to work, never having used that before. Perhaps it is that fault here. Still, torrentflux should have a better installation process. Googling for help troubleshooting dbconfig-common doesn't turn up much either.

---

### Post by kebes on 2007-07-29
> **beerfan said:**
> Giving up on that, I figured I could just manually create the database so I created the database and user account and set up the tables with the sql file in /usr/share/doc/torrentflux/dbfiles/mysql.gz. I get the torrentflux login screen when I browse [http://localhost/torrentflux/](http://localhost/torrentflux/) but...there are no user accounts to login with. The tf_users table is empty so I assume that the install process must create that and I'm out of luck since I created the database manually. I tried inserting a user account but if was not accepted for any number of possible reasons (password not hashed, invalid value in some other field). I may break down and examine the code but so far I'm pretty annoyed.

I've only tried an install from repositories once, but I didn't find the the curses config program worked: in the end I had to do it manually.

It sounds like you managed to find the MySQL script that is provided with torrentflux. This sets up the database structure but does not create any new users.

What is supposed to happen is that on your first login to torrentflux ([http://localhost/torrentflux/](http://localhost/torrentflux/)), you are given the chance to enter a username and password. This user/pass becomes the admin account and is inserted into the database for you.

So, basically, on that login-screen, enter the user/pass that you want torrentflux to use! (I agree that it is highly non-obvious that this initial login is actually **creating** the admin account.) After that you'll be brought to a settings screen, which will complete the install process.


I hope that works.

---

### Post by p-stone on 2007-08-09
I messed up :(
Whenever I open up torrentflux I get the error:

Warning: mysql_connect() [function.mysql-connect]: Access denied for user 'www-data'@'localhost' (using password: NO) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 358



TorrentFlux Database/SQL Error
Database error: Access denied for user 'www-data'@'localhost' (using password: NO)

Always check your database variables in the config.php file.

I´ve checked my config.php and it has the username and password I´d swear I set. I´m wondering if maybe I should just delete the sql database I made and try again. 

thanks in advance for the advice

---

### Post by kebes on 2007-08-09
> **p-stone said:**
> 
Warning: mysql_connect() [function.mysql-connect]: Access denied for user 'www-data'@'localhost' (using password: NO) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 358


Unfortunately that error is quite generic so it's tough to say what the problem is. Take a look at some of the other problems/solutions on this thread and see if they match your situation.

Recreating the SQL database is an option, but I doubt that's the problem. First of all, the error is for user 'www-data' but that's probably not the user you set in MySQL. You can of course use mysql on the commandline (or a GUI like phpmyadmin or MySQL Browser) to check that the database exists and is formatted properly.



Did you install torrentflux using the repositories or did you manually download it? If you installed it from repositories, that may be the problem. A repository install stores the settings differently. (It's something like "/etc/torrentflux/config-db.php" or "/usr/share/torrentflux/www/config.php".) In this case, you could remove the torrentflux install and try installing it manually, by using this how-to and downloading the latest version from the torrent-flux site.



If you did a manual download and install, then as a diagnostic try going to these links:
[http://localhost/torrentflux/](http://localhost/torrentflux/)
[http://localhost/torrentflux/index.php](http://localhost/torrentflux/index.php)
[http://localhost/torrentflux/login.php](http://localhost/torrentflux/login.php)
[http://localhost/torrentflux/admin.php](http://localhost/torrentflux/admin.php)

Do they all give the same error? This may give a hint about what's going wrong...


Hope that helps.

---

### Post by p-stone on 2007-08-09
Kebes:
Thanks for the reply, I did install the way the howto suggested, by downloading the latest version so I don't think that would be the problem.
All of those php pages you suggested display the exact same error. 
You're right www-data is not the username I set, searching for a resolution to such an error is a real pain though, you generally just get other pages having the same error :@

Here's what my torrentflux folder looks like if that helps. Any other info I can provide to help just let me know, Thanks again

cornucrapia@cornucrapia:/var/www/torrentflux$ ls
admin.php         dir.php              lastRSS.php      readrss.php
AliasFile.php     downloaddetails.php  login.php        RunningTorrent.php
all_services.php  drivespace.php       logout.php       setpriority.php
BDecode.php       dtree.css            maketorrent.php  settingsfunctions.php
blank.html        dtree.js             message.php      sql
CHANGELOG         favicon.ico          metaInfo.php     startpop.php
config.php        functions.php        multi.php        tooltip.js
cookiehelp.php    history.php          overlib.js       torrentSearch.php
COPYING           html                 profile.php      upgrades
db.php            index.php            README           viewnfo.php
details.php       INSTALL              readmsg.php      who.php

---

### Post by kebes on 2007-08-09
Okay, I see the problem. When you downloaded the tar from the torrentflux site, you copied all the contents of the extracted directory into "/var/www/torrentflux/". In fact, you should only copy the contents of the "html" sub-folder into "/var/www/torrentflux". This is actually a mistake in the how-to... which I will now correct. (Either they changed the way it's packaged since the first version of the how-to, or I made a mistake when first writing it... in either case: sorry!)


To fix your current problem, clear out everything from /var/www/torrentflux/ and copy the contents of the "html" sub-folder (from the extracted tar file) into that location instead. Then make your database edit to the file at /var/www/torrentflux/config.php

I hope that makes sense. Let me know how it goes.

---

### Post by p-stone on 2007-08-09
Hmmm, I´m afraid I´m getting the same issue still. Here´s my torrentflux directory now


> cornucrapia@cornucrapia:/var/www/torrentflux$ ls
admin.php         downloaddetails.php  lastRSS.php      RunningTorrent.php
adodb             downloads            login.php        searchEngines
AliasFile.php     drivespace.php       logout.php       setpriority.php
all_services.php  dtree.css            maketorrent.php  settingsfunctions.php
BDecode.php       dtree.js             message.php      startpop.php
blank.html        favicon.ico          metaInfo.php     TF_BitTornado
config.php        functions.php        multi.php        themes
cookiehelp.php    history.php          overlib.js       tooltip.js
db.php            images               profile.php      torrentSearch.php
details.php       index.php            readmsg.php      viewnfo.php
dir.php           language             readrss.php      who.php
 

I think I put the right username and password in config.php but I´m not 100% sure and I don´t know enough sql to know how to check :(

Any more assistance would be greatly appreciated, thanks again for the help so far.

---

### Post by kebes on 2007-08-09
> **p-stone said:**
> I think I put the right username and password in config.php but I´m not 100% sure and I don´t know enough sql to know how to check

Does the error still say "user 'www-data'" and state "using password: NO" ? (Copy the error again if it's changed at all...)


Double-check that you've installed the "php-mysql" module. (Use aptitude or Synaptic or whatever.) Then, make sure that the extension is enabled in your php.ini file:

```

sudo nano /etc/php5/apache2/php.ini

```
Find a line that says:
```

;extension=mysql.so

```
and change it to:
```

extension=msyql.so

```
(Or just add the line "extension=mysql.so" to the end of the file...)

For that change to take effect, you need to restart your web server:
```

sudo /etc/init.d/apache2 restart

```



If not, then check your MySQL settings. You can install a program called phpmyadmin to give you a GUI interface to MySQL (or a program called "MySQL Browser"). Or, you can use the commandline and go:
```

mysql -uroot -p

```
(and enter your **MySQL root** password, which is not necessarily the same as your Ubuntu/Linux root password! ... if you never set your root password then don't put the "-p") Then go:
```

mysql> use mysql;
mysql> SELECT Host, User, Password from user;
mysql> exit;

```
This will show the MySQL users that exist. The passwords are encrypted, so they won't make much sense. You can reset the password for a particular user if you suspect you've lost it... but the main thing is to make sure that the user you want is actually there.

Also, make sure the MySQL server is running. On a commandline:
```

pgrep mysql -l

```
Should return something like:
```

4995 mysqld_safe
5044 mysqld

```

---

### Post by kebes on 2007-08-09
Another thought: are you trying to use the root MySQL account in the config.php file? If so, try creating a MySQL user for torrentflux, and make the username different from the name of the torrentflux database you made.

(It shoudn't make any difference... but you never know...)

---

### Post by p-stone on 2007-08-09
Still nothing I´m afraid Here´s some outputs in case they help. How do I reset the password? Maybe that is my problem, although I tried all the likely ones.

```

mysql> SELECT Host, User, Password from user;
-------------+------------------+-------------------------------------------+
| Host        | User             | Password                                  |
+-------------+------------------+-------------------------------------------+
| localhost   | root             | *75B620842EEB7D80181708FE54962B9F0A9B31D8 | 
| cornucrapia | root             |                                           | 
| 127.0.0.1   | root             |                                           | 
| localhost   | debian-sys-maint | *73A13AE9BB29606DB0FF08F8B9C0731EA900954D | 
| localhost   | torfluxuser      | *14E65567ABDB5135D0CFD9A70B3032C179A49EE7 | 
+-------------+------------------+-------------------------------------------+
5 rows in set (0.00 sec)

```

```

/**************************************************************************/
// YOUR DATABASE CONNECTION INFORMATION
/**************************************************************************/
// Check the adodb/drivers/ directory for support for your database
// you may choose from many (mysql is the default)
$cfg["db_type"] = "mysql";       // mysql, postgres7 view adodb/drivers/
$cfg["db_host"] = "localhost";   // DB host computer name or IP
$cfg["db_name"] = "torrentflux"; // Name of the Database
$cfg["db_user"] = "torfluxuser";        // username for your MySQL database
$cfg["db_pass"] = "secret";            // password for database
/**************************************************************************/

```

---

### Post by kebes on 2007-08-09
To change a MySQL user password:
```

mysql -uroot -p
mysql> SET PASSWORD FOR 'torfluxuser'@'localhost' = PASSWORD('newpasswordhere');

```


Also, you should edit your post and remove the hashed passwords for your users. Even though they are hashed, it's still best to remove or modify them. (Which maybe you did already.)

I don't think that it's a problem with your MySQL user, however. For some strange reason it's ignoring your config.php user/password entirely when connecting to MySQL.

I will think about it some more and post again if I get any other ideas. You may also want to post your problem on the torrentflux forum:
[http://www.torrentflux.com/forum/](http://www.torrentflux.com/forum/)

---

### Post by kebes on 2007-08-10
p-stone,

Here are some more ideas:


1. You said this was a manual install, but did you previously try to
install it with apt-get or Synaptic or whatever? If so, make sure you
fully uninstall that version. (Using Sypatic or apt-get remove or
whatever.) A previous poster on this thread had the same error message
as you, and it went away (well, changed anyways) after he removed the
auto install and downloaded torrentflux again.

2. In your error message it tries to access the file:
/usr/share/php/adodb/drivers/adodb-mysql.inc.php

But it really shouldn't. It should be using the file
/var/www/torrentflux/adodb/drivers/adodb-mysql.inc.php

On my systems with torrentflux, I don't even have that first file...
which makes me think that perhaps it was put there from a manual
install, or perhaps the install of some other piece of software.

So, check whether those two files exist:
```

ls /var/www/torrentflux/adodb/drivers/adodb-mysql.inc.php -laF
ls /usr/share/php/adodb/drivers/adodb-mysql.inc.php -laF

```


3. Actually, it might be useful to double-check that you have all the
required files in your /var/www/torrentflux/adodb/drivers/ folder. If
you want you can actually post the entire file structure of your
torrentflux install and I will compare it to mine...
```

ls /var/www/flux/ -laF -R

```


4. What versions of MySQL and php are you using?
```

php --version
mysql --version

```


5. Create a test file inside the torrentflux folder, and make sure you
can access it. While you're at it, output some php setup info. So edit
the file:
```

sudo /var/www/torrentflux/test.php

```
and in the file put this:
```

<html>
<head>
  <title>Test Page</title>
</head>
<body>
Test page<br />
<?php
        echo 'If you can see this text, then PHP is working.';
        phpinfo();
?>
</body>
</html>

```

Then go to the page:
[http://localhost/torrentflux/test.php](http://localhost/torrentflux/test.php)

You should see the text "If you can see this..." and you should also see
a very long listing of php internal setup information. Check through
that quickly and make sure it doesn't list any errors. Also go to the
mysql section, and make sure it's installed.


6. If the above worked, then try a simple MySQL connect test and see
whether it works. So now create the file:
```

nano /var/www/torrentflux/test2.php

```
and make it look like this:
```

<html>
<head>
  <title>Test Page</title>
</head>
<body>
Test page<br />
<?php


        $username = 'torfluxuser';
        $password = 'secret';
        $host = 'localhost';
        $database = 'torrentflux';



        // Connect to MySQL server
        $link = mysql_connect($host, $username, $password);
        if (!$link) {
                die('Could not connect to '.$host.': ' . mysql_error());
        }
        // Open the database
        $db_selected=@mysql_select_db($database,$link);
        if (!$db_selected) {
                die('Could not open database '.$database.': ' . mysql_error());
        }


		$query="SELECT * FROM tf_settings";
		$result=mysql_query($query, $link);
		if (!$result) {
						echo 'Query failed.<br>';
		} else {
				$num_rows = mysql_numrows($result);
				$i=0;
				while($i<$num_rows) {
						$key = mysql_result($result,$i,"tf_key");
						$value = mysql_result($result,$i,"tf_value");

						echo $key.' = '.$value.'<br/>';
						$i++;
				}
		}


?>
</body>
</html>

```

Make sure that you change the values of username and password in the above code to match what you're using. Then go to the page:
[http://localhost/torrentflux/test3.php](http://localhost/torrentflux/test3.php)

Does it work? You should get a page like:
```

Test page
path = /var/www/torrentflux/downloads/
btphpbin = /var/www/torrentflux/TF_BitTornado/btphptornado.py
btshowmetainfo = /var/www/torrentflux/TF_BitTornado/btshowmetainfo.py
advanced_start = 1
...lots more stuff...

```

If you instead get an error instead... what error do you get? (And, what error do you get if you change the username or password to an incorrect value?)




Hopefully one of these tests will give us a hint...

---

### Post by p-stone on 2007-08-11
Kebes,

Thanks so much for your help! Removing torrentflux and recopying the folder over turned out to be the solution!

---

### Post by kebes on 2007-08-11
> **p-stone said:**
> Thanks so much for your help! Removing torrentflux and recopying the folder over turned out to be the solution!
I'm glad you got it working! Enjoy!

---

### Post by arrrghhh on 2007-08-19
yea i had to reload mine... something in mysql got screwed up.  i got it workin great, but i had a question about my /downloads folder.  last time i installed torrentflux, i moved my /var/www/torrentflux/downloads to /var/www/downloads - so it could be easily accessed & served up by apache!  well it worked last time, but this time it didn't and i don't know why.  when i try to go to the page, it's completely blank.

i'll show you - goto [http://arrrghhh.gotdns.com](http://arrrghhh.gotdns.com)
there's a downloads folder there, and it goes to nothing... it used to go to a folder listing of what was in there, and allow me to download it anywhere!  it also made it easy for my roommate to access his stuff here.... at any rate, why would it work before and not now?  

thanks!

---

### Post by kebes on 2007-08-19
> **arrrghhh said:**
> when i try to go to the page, it's completely blank.

There are a couple of reasons why this might happen.

1. You need to turn on directory listing in your apache config. The apache FAQ explains how to enable/disable directory listing:
[http://httpd.apache.org/docs/1.3/misc/FAQ.html#indexes](http://httpd.apache.org/docs/1.3/misc/FAQ.html#indexes)

Basically what you would do is edit the config file responsible for your "arrrghhh.gotdns.com" host. If you have not changed the default behavior, then this means editing the file:
```

sudo nano /etc/apache2/sites-available/default

```

Then go into the virtual host that handles "arrrghhh.gotdns.com" (again, if you've never changed the default behaivor, there will be only one big VirualHost section). So in that VirtualHost, place this code:
```

        <Directory /var/www/downloads/>
                Options +Index
        </Directory>

```

Save the file, and restart apache:
```

sudo /etc/init.d/apache2 restart

```

Then check if it now works.


2. The permissions are set such that the webserver can't read the directory.
```

cd /var/www/
ls -laF

```
The directory "downloads" should have a permission like "-rwxr--r--". If not, use "chmod" to change it:
```

sudo chmod 744 downloads

```


3. You have an "index.htm" file (or index.html or index.php) in the downloads directory. If such a file exists, apache will automatically parse and display it, instead of showing a raw directory listing.
```

cd /var/www/downloads/
ls -laF

```


4. If #1 didn't work, it's possible that you have a conflicting setting somewhere else. There are many ways to activate this mode (for the entire webserver or only specific directories), so you may need to check multiple locations:

a.
/etc/apache2/apache2.conf

b.
/etc/apache2/sites-available/default

c.
If you have any ".htaccess" files in your webserver directories, those can activate/deactive directory listing mode. In particular, check if you have:
```

ls /var/www/.htaccess
ls /var/www/downloads/.htaccess

```
If those files exist, then you can modify them to turn on/off indexing.



Hope that helps.

---

### Post by kebes on 2007-08-19
Oh, by the way... torrentflux itself gives you access to the downloads folder. When logged in, just click on the "Directory" tab, and then you can browse the download directories, and can click on files to download them.

This has the advantage of being password-protected. You can set up  torrentflux accounts for friends to give them access, too.

---

### Post by arrrghhh on 2007-08-21
yea, i know torrentflux has that directory listing... the problem i had with it was redownloading the file on my desktop on my localmachine for no reason... yea.

at any rate, thank you for that extremely thorough response!  i'm a retard, should've looked for an index.html file... that was it!

i went thru and configured my permissions with gksudo thunar... so hopefully that is all good now (read only access to /downloads, but evidently torrentflux folder needs read & write... d'oh!)

thanks again for the help, next time i'll look out for silly things like index.html files sitting around doin nothing but causing trouble!

---

### Post by kebes on 2007-08-22
> **arrrghhh said:**
> thanks again for the help, next time i'll look out for silly things like index.html files sitting around doin nothing but causing trouble!

You're very welcome. Glad you got it working (and that it was a fairly easy fix!).

---

### Post by mcdeath on 2007-08-26
Guys I have read this thread from go to woe and I can't seem to find any help regarding my issue.

PHP seems to be working so are my permissions but for some reason I keep getting these errors (see below)when I connect to my page. [http://192.168.1.2/tf](http://192.168.1.2/tf)
I know they state what the issue is but my knowledge of SQL and web servers is minimal.

Any idea what needs to be fixed, oh BTW as you can guess I very new to all this so forgive my ignorance

```
Warning: session_start() [function.session-start]: Cannot send session cookie - headers already sent by (output started at /var/www/tf/config.php:93) in /var/www/tf/functions.php on line 26

Warning: session_start() [function.session-start]: Cannot send session cache limiter - headers already sent (output started at /var/www/tf/config.php:93) in /var/www/tf/functions.php on line 26

Warning: Cannot modify header information - headers already sent by (output started at /var/www/tf/config.php:93) in /var/www/tf/functions.php on line 99

```

---

### Post by mcdeath on 2007-08-26
**Bump**:)

---

### Post by mcdeath on 2007-08-27
**Double Bump** sorry guys but I'm really stuck here.
Any suggestions?

---

### Post by Dark Star on 2007-08-27
Thanks for such a nice guide :)

---

### Post by mcdeath on 2007-08-27
**Bump** see last question above \\:D/

---

### Post by kebes on 2007-08-27
> **mcdeath said:**
> ```
Warning: session_start() [function.session-start]: Cannot send session cookie - headers already sent by (output started at /var/www/tf/config.php:93) in /var/www/tf/functions.php on line 26

Warning: session_start() [function.session-start]: Cannot send session cache limiter - headers already sent (output started at /var/www/tf/config.php:93) in /var/www/tf/functions.php on line 26

Warning: Cannot modify header information - headers already sent by (output started at /var/www/tf/config.php:93) in /var/www/tf/functions.php on line 99

```

This is probably because you have a newline character (or other whitespace) in your config.php file, outside of the PHP tags. So edit your config file:
/var/www/tf/config.php

Go to the very top and very bottom of the file, and make sure there is not "whitespace" (spaces, tabs, and newlines) before the "<?php" opening-tag or after the "?>" closing-tag.

If that file looks okay, check the file "/var/www/tf/functions.php" ... but I'm pretty sure it's the config.php file that you need to fix.

(If you're interested, the reason this happens is that the PHP page is processed by the server to generate HTML. If the entire PHP file is only PHP code, it just gets executed. If there is whitespace outside the PHP tags, this gets turned into an HTML page (an empty page) and passed along, which produces unexpected behavior.)

Let me know if that works. Sorry I didn't reply sooner, I was out of town for the weekend.

---

### Post by mcdeath on 2007-08-27
Kebes thank you very much for your input I will try this tonight and let you know how it goes.

Where would this forum be without people such as yourself :KS

---

### Post by mcdeath on 2007-08-28
it worked! many thanks.
Now I just have an issue with my initial login, I seem to have not entered a username a pwd it liked.
Basically it either hangs or tells me 'login failed please try again'

Any thoughts?

---

### Post by kebes on 2007-08-28
> **mcdeath said:**
> it worked! many thanks.
Now I just have an issue with my initial login, I seem to have not entered a username a pwd it liked.
Basically it either hangs or tells me 'login failed please try again'

Any thoughts?

Hmm... the primary user account is generated on your initial login. Maybe this got messed up because of the other error.

You could probably go into MySQL and delete the user profile from the torrentflux database. Then go to the page and it will probably re-prompt you. To do so, access your database in phpmyadmin, find the "tf_users" table, and delete the user that is there. (Also, by looking at the user_id field you can see what the username is set to.)

If you don't have phpmyadmin installed, you can do the same thing on the commandline like so:

```

mysql -uroot -p

```
(then enter your **MySQL root** password). Then go:
```

mysql> USE torrentflux;
mysql> SELECT uid, user_id, password FROM tf_users;
+-----+---------+----------------------------------+
| uid | user_id | password                         |
+-----+---------+----------------------------------+
|   1 | kebes     | xliufejs90v8jsf2jfs9084j09fj93 |
+-----+---------+----------------------------------+
1 row in set (0.00 sec)

```
The password is encrypted, so it won't look like anything. But you can at least see what usernames exist ("kebes" in the above example). Then if you want to try deleting the user you can just go:
```

mysql> DELETE FROM tf_users WHERE uid = 1 LIMIT 1;

```
Then go back to torrentflux and invent a new user/pass:
[http://localhost/torrentflux/](http://localhost/torrentflux/)

You can also erase the entire torrentflux database and re-create it. (Go back to the step of the guide where you run the MySQL script that generates the database.) Or create a second database (torflux2 or whatever) and update your "config.php" file accordingly.

---

### Post by mcdeath on 2007-08-30
Just to let you know Kebes all went well, I'm now 100% up and running.
Thank you very much my friend.

---

### Post by Jordanwb on 2007-09-02
After getting it installed I got to [http://192.168.1.4/torrentflux](http://192.168.1.4/torrentflux) and I get this error: "Database error: Access denied for user 'torrentflux'@'localhost' to database 'torrentflux'" I go into my FTP client and go into the torrentflux folder and there's nothing there.

---

### Post by kebes on 2007-09-02
> **Jordanwb said:**
> After getting it installed I got to [http://192.168.1.4/torrentflux](http://192.168.1.4/torrentflux) and I get this error: "Database error: Access denied for user 'torrentflux'@'localhost' to database 'torrentflux'" I go into my FTP client and go into the torrentflux folder and there's nothing there.

This error usually means that the username/password that you set in your MySQL database isn't the same username/password that you have set in your config file.

Check the file:

/var/www/torrentflux/config.php

and make sure you update the lines:
```

$cfg["db_type"] = "mysql";       // mysql, postgres7 view adodb/drivers/
$cfg["db_host"] = "localhost";   // DB host computer name or IP
$cfg["db_name"] = "torrentflux"; // Name of the Database
$cfg["db_user"] = "torrentflux";        // username for your MySQL database
$cfg["db_pass"] = "secret";            // password for database

```


The user "torfluxuser" and password ("secret" in the above example), must be the same as what you created in the MySQL database. Check out the steps outlined in part 4.b. and 4.c. of this how-to, and see if you skipped a step somehow.

You can check to see if the database "torrentflux" exists, and whether the MySQL user "torrentflux" exists by using phpmyadmin. If you don't have phpmyadmin installed, you can also check using the commandline:
```

$ mysql -uroot -p

```
(Enter your **MySQL root** password, which is probably not the same as your login password.) You can list the databases that exist by going:
```

mysql> show databases;

```
It should list "torrentflux" (or whatever you decided to call it) among them. Then check that you have a torrentflux user:
```

mysql> use mysql;
mysql> SELECT user FROM user;

```
It will list the users. Make sure "torrentflux" is among them. If not, then add the necessary user. If the user exists, then you need to update the password or privileges (again, see the how-to).



I hope that helps. If anything requires clarification, let me know.

---

### Post by Jordanwb on 2007-09-02
> **Jordanwb said:**
>  I go into my FTP client and go into the torrentflux folder and there's nothing there.

So...

I was able to get passed that error by setting the config manually in /etc/torrentflux/config-db.php but now it's saying it can't find a a table: "Database error: Table 'torrentflux.tf_settings' doesn't exist" I know what that means I know how to use MySQL (to some extent) but shouldn't Torrentflux create those tables on installation?

---

### Post by kebes on 2007-09-02
> **Jordanwb said:**
> So...

I was able to get passed that error by setting the config manually in /etc/torrentflux/config-db.php but now it's saying it can't find a a table: "Database error: Table 'torrentflux.tf_settings' doesn't exist" I know what that means I know how to use MySQL (to some extent) but shouldn't Torrentflux create those tables on installation?

If you installed torrentflux using apt-get (or Synaptic), then yes it should be automatically created.

If you installed manually (just copying the php files to the directory /var/www/torrentflux/) then, no, you have to manually create the database. In this case you just use a MySQL script that is included in tar file for torrentflux. (See step 4.b. in the [how-to]("http://ubuntuforums.org/showthread.php?t=268985").)

In either case, you can use the MySQL commands I mentioned in my last post to figure out if the database actually exists. If not, then create it!

---

### Post by Jordanwb on 2007-09-02
I'll try everything from the beginning. It'll probably work this time. It always works that way for me.

---

### Post by mcdeath on 2007-09-03
Oh noes I've broken my torrentflux, basically all I'm getting now when I connect to my web page is.

You don't have permission to access /torrentflux/ on this server

Also when I did have it running every time I aadded a new torrent it would say torrent failed?

Have I messed up my permissions somewhere?

Any input here is appricated.

```
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20051025/msql.so' - /usr/lib/php5/20051025/msql.so: cannot$
[Mon Sep 03 21:57:21 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.6 configured -- resuming normal operations
[Mon Sep 03 21:57:45 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.html denied
[Mon Sep 03 21:57:45 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.cgi denied
[Mon Sep 03 21:57:45 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.pl denied
[Mon Sep 03 21:57:45 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.php denied
[Mon Sep 03 21:57:45 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.xhtml denied
[Mon Sep 03 21:58:10 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.html denied
[Mon Sep 03 21:58:10 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.cgi denied
[Mon Sep 03 21:58:10 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.pl denied
[Mon Sep 03 21:58:10 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.php denied
[Mon Sep 03 21:58:10 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.xhtml denied
[Mon Sep 03 21:58:11 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.html denied
[Mon Sep 03 21:58:11 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.cgi denied
[Mon Sep 03 21:58:11 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.pl denied
[Mon Sep 03 21:58:11 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.php denied
[Mon Sep 03 21:58:11 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.xhtml denied
[Mon Sep 03 22:00:05 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.html denied
[Mon Sep 03 22:00:05 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.cgi denied
[Mon Sep 03 22:00:05 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.pl denied
[Mon Sep 03 22:00:05 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.php denied
[Mon Sep 03 22:00:05 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.xhtml denied
[Mon Sep 03 22:00:12 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.html denied
[Mon Sep 03 22:00:12 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.cgi denied
[Mon Sep 03 22:00:12 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.pl denied
[Mon Sep 03 22:00:12 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.php denied
[Mon Sep 03 22:00:12 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.xhtml denied
[Mon Sep 03 22:01:56 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.html denied
[Mon Sep 03 22:01:56 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.cgi denied
[Mon Sep 03 22:01:56 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.pl denied
[Mon Sep 03 22:01:56 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.php denied
[Mon Sep 03 22:01:56 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.xhtml denied
[Mon Sep 03 22:02:05 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.html denied
[Mon Sep 03 22:02:05 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.cgi denied
[Mon Sep 03 22:02:05 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.pl denied
[Mon Sep 03 22:02:05 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.php denied
[Mon Sep 03 22:02:05 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.xhtml denied
[Mon Sep 03 22:03:13 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.html denied
[Mon Sep 03 22:03:13 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.cgi denied
[Mon Sep 03 22:03:13 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.pl denied
[Mon Sep 03 22:03:13 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.php denied
[Mon Sep 03 22:03:13 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.xhtml denied
[Mon Sep 03 22:03:14 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.html denied
[Mon Sep 03 22:03:14 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.cgi denied
[Mon Sep 03 22:03:14 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.pl denied
[Mon Sep 03 22:03:14 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.php denied
[Mon Sep 03 22:03:14 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.xhtml denied
[Mon Sep 03 22:06:20 2007] [notice] caught SIGTERM, shutting down
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20051025/msql.so' - /usr/lib/php5/20051025/msql.so: cannot$
[Mon Sep 03 22:06:21 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.6 configured -- resuming normal operations
[Mon Sep 03 22:06:33 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.html denied
[Mon Sep 03 22:06:33 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.cgi denied
[Mon Sep 03 22:06:33 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.pl denied
[Mon Sep 03 22:06:33 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.php denied
[Mon Sep 03 22:06:33 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.xhtml denied
[Mon Sep 03 22:06:40 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.html denied
[Mon Sep 03 22:06:40 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.cgi denied
[Mon Sep 03 22:06:40 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.pl denied
[Mon Sep 03 22:06:40 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.php denied
[Mon Sep 03 22:06:40 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.xhtml denied
[Mon Sep 03 22:08:07 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.html denied
[Mon Sep 03 22:08:07 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.cgi denied
[Mon Sep 03 22:08:07 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.pl denied
[Mon Sep 03 22:08:07 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.php denied
[Mon Sep 03 22:08:07 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.xhtml denied
[Mon Sep 03 22:08:13 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.html denied
[Mon Sep 03 22:08:13 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.cgi denied
[Mon Sep 03 22:08:13 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.pl denied
[Mon Sep 03 22:08:13 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.php denied
[Mon Sep 03 22:08:13 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.xhtml denied
[Mon Sep 03 22:09:17 2007] [notice] caught SIGTERM, shutting down
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20051025/msql.so' - /usr/lib/php5/20051025/msql.so: cannot$
[Mon Sep 03 22:09:19 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.6 configured -- resuming normal operations
[Mon Sep 03 22:09:26 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.html denied
[Mon Sep 03 22:09:26 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.cgi denied
[Mon Sep 03 22:09:26 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.pl denied
[Mon Sep 03 22:09:26 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.php denied
[Mon Sep 03 22:09:26 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.xhtml denied
[Mon Sep 03 22:15:36 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.html denied
[Mon Sep 03 22:15:40 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.html denied
[Mon Sep 03 22:15:40 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.cgi denied
[Mon Sep 03 22:15:40 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.pl denied
  GNU nano 1.3.12                         File: /var/log/apache2/error.log                                                          

[Mon Sep 03 22:15:40 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.php denied
[Mon Sep 03 22:15:40 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.xhtml denied
[Mon Sep 03 22:15:42 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.html denied
[Mon Sep 03 22:15:42 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.cgi denied
[Mon Sep 03 22:15:42 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.pl denied
[Mon Sep 03 22:15:42 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.php denied
[Mon Sep 03 22:15:42 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.xhtml denied
[Mon Sep 03 22:24:17 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.html denied
[Mon Sep 03 22:24:17 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.cgi denied
[Mon Sep 03 22:24:17 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.pl denied
[Mon Sep 03 22:24:17 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.php denied
[Mon Sep 03 22:24:17 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.xhtml denied
[Mon Sep 03 22:24:25 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.html denied
[Mon Sep 03 22:24:27 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.html denied
[Mon Sep 03 22:24:27 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.cgi denied
[Mon Sep 03 22:24:27 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.pl denied
[Mon Sep 03 22:24:27 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.php denied
[Mon Sep 03 22:24:27 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.xhtml denied
[Mon Sep 03 22:33:55 2007] [notice] caught SIGTERM, shutting down
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20051025/msql.so' - /usr/lib/php5/20051025/msql.so: cannot$
[Mon Sep 03 22:33:56 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.6 configured -- resuming normal operations
[Mon Sep 03 22:35:15 2007] [notice] caught SIGTERM, shutting down
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20051025/msql.so' - /usr/lib/php5/20051025/msql.so: cannot$
[Mon Sep 03 22:36:05 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.6 configured -- resuming normal operations
[Mon Sep 03 22:40:32 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.html denied
[Mon Sep 03 22:40:32 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.cgi denied
[Mon Sep 03 22:40:32 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.pl denied
[Mon Sep 03 22:40:32 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.php denied
[Mon Sep 03 22:40:32 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.xhtml denied
[Mon Sep 03 22:40:54 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.html denied
[Mon Sep 03 22:40:54 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.cgi denied
[Mon Sep 03 22:40:54 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.pl denied
[Mon Sep 03 22:40:54 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.php denied
[Mon Sep 03 22:40:54 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.xhtml denied
[Mon Sep 03 22:41:03 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.html denied
[Mon Sep 03 22:41:03 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.cgi denied
[Mon Sep 03 22:41:03 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.pl denied
[Mon Sep 03 22:41:03 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.php denied
[Mon Sep 03 22:41:03 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.xhtml denied
[Mon Sep 03 22:41:33 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.php denied
[Mon Sep 03 22:41:39 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.html denied
[Mon Sep 03 22:41:39 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.cgi denied
[Mon Sep 03 22:41:39 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.pl denied
[Mon Sep 03 22:41:39 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.php denied
[Mon Sep 03 22:41:39 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.xhtml denied
[Mon Sep 03 22:42:10 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.html denied
[Mon Sep 03 22:42:10 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.cgi denied
[Mon Sep 03 22:42:10 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.pl denied
[Mon Sep 03 22:42:10 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.php denied
[Mon Sep 03 22:42:10 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.xhtml denied
[Mon Sep 03 22:42:11 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.html denied
[Mon Sep 03 22:42:11 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.cgi denied
[Mon Sep 03 22:42:11 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.pl denied
[Mon Sep 03 22:42:11 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.php denied
[Mon Sep 03 22:42:11 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.xhtml denied
[Mon Sep 03 22:42:12 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.html denied
[Mon Sep 03 22:42:12 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.cgi denied
[Mon Sep 03 22:42:12 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.pl denied
[Mon Sep 03 22:42:12 2007] [error] [client 192.168.1.7] (13): access to /torrentflux/index.php denied

^G Get Help           ^O WriteOut           ^R Read File          ^Y Prev Page          ^K Cut Text           ^C Cur Pos
^X Exit               ^J Justify            ^W Where Is           ^V Next Page        
```

---

### Post by kebes on 2007-09-03
> **mcdeath said:**
> You don't have permission to access /torrentflux/ on this server


That's alot of errors! Did you change anything recently?



Yes, first thing to check is permissions. The webserver (which usually runs as user "www-data" needs to be able to read the torrentflux directory, and needs write access to the directory where the files are supposed to be written.

So:

```

cd /var/www/
ls -laF

```
Make sure your torrentflux directory has permissions "drwxr-xr-x" so that the webserver can read it. (Alternately you can set permissions "drwx------" if the directory is owned by "www-data".) Use the command "chmod" to alter permissions and "chown" to alter ownership. For example:
```

chmod 755 torrentflux

```
Should fix it.

The files contained within the torrentflux folder should similarly have read permission:
```

cd /var/www/torrentflux/
ls -laF

```
If they don't have "-rwxr--r--" then fix it:
```

chmod +r * -R

```

And, as I said, make sure the "downloads" directory has write permission for "www-data":
```

chmod 777 downloads

```

---

### Post by DarkDancer on 2007-09-03
I'm at this step:

> (You'll need to enter the MySQL password you set previously.) Now go into the "sql" sub-directory in torrentflux (depends on where you untared torrentflux, of course):
Code:

$ cd ~/Desktop/torrentflux_2.1/sql



I installed with synaptec. I can't find torrentflux_2.1/sql.

---

### Post by kebes on 2007-09-03
> **DarkDancer said:**
> I installed with synaptec. I can't find torrentflux_2.1/sql.

Yeah, the how-to was written for a manual installation. With an automatic installation, the sql script is supposed to be run automatically. So, the database should be created.

Having said that, I have found that the automatic install doesn't always do that step properly. You can obtain the "mysql_torrentflux.sql" script by downloading the torrentflux installation files from:
[http://sourceforge.net/project/showfiles.php?group_id=123961](http://sourceforge.net/project/showfiles.php?group_id=123961)

You can follow the steps in the how-to for untarring that file, and running the MySQL script.

Hope that helps.

---

### Post by kebes on 2007-09-03
> **DarkDancer said:**
> 
I installed with synaptec. I can't find torrentflux_2.1/sql.

By the way, you only need to run that sql script if the automatic installation didn't create the MySQL database for you. You can check if the MySQL database exists in two different ways.

Method one:
Check the directory "/var/lib/mysql/" and see if it contains "torrentflux" (and make sure it's not empty):
```

cd /var/lib/mysql/
ls -laF
cd torrentflux
ls -laF

```


Method two:
Use MySQL itself:
```

mysql -uroot -p
mysql> show databases;
mysql> use torrentflux;
mysql> show tables;
mysql> quit;

```
Make sure that it listed "torrentflux" among the databases, and that it contained the right tables:
```

+-----------------------+
| Tables_in_torrentflux |
+-----------------------+
| tf_cookies            |
| tf_links              |
| tf_log                |
| tf_messages           |
| tf_rss                |
| tf_settings           |
| tf_users              |
+-----------------------+


```

---

### Post by DarkDancer on 2007-09-03
Ok, thanks, I think it worked, but I also think I may be in over my head....

I fail at step 4d. 

[http://localhost/torrentflux/](http://localhost/torrentflux/)

I get a 404 not found error.....

What I did was uninstalled from synaptec and downloaded the tarball and followed the instructions from there.

---

### Post by kebes on 2007-09-03
> **DarkDancer said:**
> Ok, thanks, I think it worked, but I also think I may be in over my head....

I fail at step 4d. 

[http://localhost/torrentflux/](http://localhost/torrentflux/)

I get a 404 not found error.....

What I did was uninstalled from synaptec and downloaded the tarball and followed the instructions from there.

If you uninstalled using Synaptic, then you need go back through all the steps of the how-to. In particular, a 404 error probably means that you didn't copy the contents of the "html" directory form the downloaded tar-file into the directory "/var/www/torrentflux/" (step 4.a).

---

### Post by DarkDancer on 2007-09-03
Ok, I went back through all the instructions starting with 4a and I still get the 404 error. The only errors during the steps were errors saying that the database could not be created because it already exists....

---

### Post by kebes on 2007-09-03
> **DarkDancer said:**
> Ok, I went back through all the instructions starting with 4a and I still get the 404 error. The only errors during the steps were errors saying that the database could not be created because it already exists....

Confirm that the files got copied:
```

ls /var/www/torrentflux/ -laF

```
It should lists a bunch of files (46 files and dirs, I think). You can post the output of that command to the thread.

---

### Post by DarkDancer on 2007-09-03
> drwxr-xr-x  9 darkdancer darkdancer  4096 2007-09-03 15:10 ./
drwxr-xr-x  4 root       root        4096 2007-09-03 14:27 ../
-rwxr-x---  1 darkdancer darkdancer 90289 2007-09-03 14:43 admin.php*
drwxr-x--- 11 darkdancer darkdancer  4096 2007-09-03 14:21 adodb/
-rwxr-x---  1 darkdancer darkdancer  5471 2007-09-03 14:43 AliasFile.php*
-rwxr-x---  1 darkdancer darkdancer  1958 2007-09-03 14:43 all_services.php*
-rwxr-x---  1 darkdancer darkdancer  7199 2007-09-03 14:43 BDecode.php*
-rwxr-x---  1 darkdancer darkdancer    70 2007-09-03 14:43 blank.html*
-rwxr-x---  1 darkdancer darkdancer  3742 2007-09-03 15:10 config.php*
-rw-r-----  1 darkdancer darkdancer  3743 2007-09-03 14:53 config.php~
-rwxr-x---  1 darkdancer darkdancer  2623 2007-09-03 14:43 cookiehelp.php*
-rwxr-x---  1 darkdancer darkdancer  2958 2007-09-03 14:43 db.php*
-rwxr-x---  1 darkdancer darkdancer  1808 2007-09-03 14:43 details.php*
-rwxr-x---  1 darkdancer darkdancer 18689 2007-09-03 14:43 dir.php*
-rwxr-x---  1 darkdancer darkdancer  6723 2007-09-03 14:43 downloaddetails.php*
drwxr-x---  2 darkdancer darkdancer  4096 2007-09-03 14:21 downloads/
-rwxr-x---  1 darkdancer darkdancer  1726 2007-09-03 14:43 drivespace.php*
-rwxr-x---  1 darkdancer darkdancer   794 2007-09-03 14:43 dtree.css*
-rwxr-x---  1 darkdancer darkdancer 13523 2007-09-03 14:43 dtree.js*
-rwxr-x---  1 darkdancer darkdancer  2238 2007-09-03 14:43 favicon.ico*
-rwxr-x---  1 darkdancer darkdancer 86831 2007-09-03 14:43 functions.php*
-rwxr-x---  1 darkdancer darkdancer  5993 2007-09-03 14:43 history.php*
drwxr-x---  4 darkdancer darkdancer  4096 2007-09-03 14:21 images/
-rwxr-x---  1 darkdancer darkdancer 34943 2007-09-03 14:43 index.php*
drwxr-x---  2 darkdancer darkdancer  4096 2007-09-03 14:21 language/
-rwxr-x---  1 darkdancer darkdancer  8440 2007-09-03 14:43 lastRSS.php*
-rwxr-x---  1 darkdancer darkdancer 11652 2007-09-03 14:43 login.php*
-rwxr-x---  1 darkdancer darkdancer  1625 2007-09-03 14:43 logout.php*
-rwxr-x---  1 darkdancer darkdancer 25368 2007-09-03 14:43 maketorrent.php*
-rwxr-x---  1 darkdancer darkdancer  3948 2007-09-03 14:43 message.php*
-rwxr-x---  1 darkdancer darkdancer  8417 2007-09-03 14:43 metaInfo.php*
-rwxr-x---  1 darkdancer darkdancer  5186 2007-09-03 14:43 multi.php*
-rwxr-x---  1 darkdancer darkdancer 44818 2007-09-03 14:43 overlib.js*
-rwxr-x---  1 darkdancer darkdancer 17756 2007-09-03 14:43 profile.php*
-rwxr-x---  1 darkdancer darkdancer  6000 2007-09-03 14:43 readmsg.php*
-rwxr-x---  1 darkdancer darkdancer  7649 2007-09-03 14:43 readrss.php*
-rwxr-x---  1 darkdancer darkdancer  4773 2007-09-03 14:43 RunningTorrent.php*
drwxr-x---  2 darkdancer darkdancer  4096 2007-09-03 14:21 searchEngines/
-rwxr-x---  1 darkdancer darkdancer  3055 2007-09-03 14:43 setpriority.php*
-rwxr-x---  1 darkdancer darkdancer  5672 2007-09-03 14:43 settingsfunctions.php*
-rwxr-x---  1 darkdancer darkdancer  8939 2007-09-03 14:43 startpop.php*
drwxr-x---  4 darkdancer darkdancer  4096 2007-09-03 14:21 TF_BitTornado/
drwxr-x--- 17 darkdancer darkdancer  4096 2007-09-03 14:21 themes/
-rwxr-x---  1 darkdancer darkdancer 17889 2007-09-03 14:43 tooltip.js*
-rwxr-x---  1 darkdancer darkdancer  7465 2007-09-03 14:43 torrentSearch.php*
-rwxr-x---  1 darkdancer darkdancer  2756 2007-09-03 14:43 viewnfo.php*
-rwxr-x---  1 darkdancer darkdancer  1813 2007-09-03 14:43 who.php*


Something like that?

---

### Post by kebes on 2007-09-03
> **DarkDancer said:**
> Something like that?

Okay, all the files are there, but the webserver doesn't have permission to read them. The bit that says "-rwxr-x---" needs to be updated:
```

cd /var/www/torrentflux/
chmod +r * -R
chmod 777 downloads

```

The first chmod adds "read" capability to all the files, so the webserver can access them. The second "chmod" gives full permissions to the downloads directory, so that the webserver can create new files in that directory. Once done, if you do "ls -laF" again you should get files with "-rwxr--r--" listed instead, meaning that the webserver can read them.


Note:
An alternate way to accomplish this would be to make the webserver user, "www-data", own all the files:
```

cd /var/www/torrentflux/
chown www-data:www-data * -R

```

---

### Post by DarkDancer on 2007-09-03
Tried both, one, tested then the other. Still getting the 404 error.

---

### Post by kebes on 2007-09-03
> **DarkDancer said:**
> Tried both, one, tested then the other. Still getting the 404 error.

Okay. First, double check that you are spelling the name of the directory correctly. Make sure that "/var/www/**torrentflux**/" matches "http://localhost/**torrentflux**/"

Probably that's not the problem, but it's always good to double-check these things!

Now, try renaming that directory and see if it works with the new name:
```

cd /var/www/
mv torrentflux flux

```
Then go to:
[http://localhost/flux/](http://localhost/flux/)

If the above change fixes your problem, then good! What it may mean is that the torrentflux install you did before (via Synaptic) put a redirect into the apache webserver, telling it (for instance) to link "/var/www/torrentflux/" to some other directory (like "/usr/share/torrentflux/" or whatever it is).

(You can then either use the new name, "flux" or whatever, or find the config line in apache, probably in "/etc/apache2/", and change it.)

---

### Post by DarkDancer on 2007-09-03
That got it, I will continue from there...Thanks!

---

### Post by DarkDancer on 2007-09-03
Ok, wow! IT really works, I made one mistake on first log in though, Can I change the login and password in some file some where?

---

### Post by kebes on 2007-09-03
> **DarkDancer said:**
> Ok, wow! IT really works, I made one mistake on first log in though, Can I change the login and password in some file some where?

You can change your login password by logging into torrentflux with the admin account (the first one you made), then going to "admin" and then "my profile". You can create new users by going to "admin", then "new user".



If you're lost/forgotten the admin username/password, it gets more tricky.


The initial login/password become the admin username/password for torrentflux. It's stored in the MySQL database "torrentflux" in a table called "tf_uses". The password is stored in the database encrypted, so extracting it or changing it isn't really easy.


To reset the admin account, you can probably delete the one user from the tf_uses table, and then login again to torrentflux. (I've never tried this: I'm just guessing that it would work.)


Or, since you've just installed, you can delete the entire torrentflux database and re-create it using the script mentioned before.

---

### Post by kebes on 2007-09-03
Addendum:

I think it's not too difficult to change the password in the torrentflux MySQL database. Torrentflux uses the "md5" command in PHP to generate an md5 hash of the password you supply. So you can do the same thing.

Let's say you want your new password to be "secret" (without the quotes). This is what you do. First create a php file like this:
```

cd /var/www/
nano md5.php

```
In the file, put this simple code:
```

<?php
print md5("secret")
?>

```
Then when you check the page [http://localhost/md5.php](http://localhost/md5.php) you'll see the hash:
```

5ebe2294ecd0e0f08eab7690d2a6ee69

```
Copy that hash string and save it somewhere. (For security reasons, you should promptly delete the md5.php file.)

Now update the database, and put that new hash in place of the old one. This is very easy to do with the web-based "phpmyadmin" utility. If you don't have phpmyadmin, you can do it the commandline way:
```

mysql -uroot -p

```
(Enter your **MySQL root** password.) Then enter these MySQL commands:
```

mysql> USE torrentflux;
mysql> UPDATE tf_users SET password="5ebe2294ecd0e0f08eab7690d2a6ee69" WHERE uid=1;
mysql> quit;

```

This changes the password of the first torrentflux user (uid 1) to what you've chosen.

Obviously, instead of "secret" you put the password you want, and instead of the hash "5ebe..." you put the one that you got from the md5.php page you made.

---

### Post by DarkDancer on 2007-09-03
Oh I think I give up, the webserver end is working but I can't get the torrent end going, nor find any info, I guess I'll go a different way....

---

### Post by mcdeath on 2007-09-04
Kebes thanks for all your help so far, you make using the Ubuntu forums a pleasure.

Played with the permissions and I can now log back in 755 did the trick, now my last issue is......

I added another drive to my machine and mounted it as

/media/torrentdrive 

Which holds the following directories

drwxrwxrwx 5   root root  4096 2007-08-30 22:12   active
drwxr-xr-x 2     root root   4096 2007-08-30 21:36   complete
drwx------ 2      root root   16384 2007-08-30 21:27  lost+found

The active directory is of course where I point my Torrentflux to for active torrents.
Now what happens is that every time I upload a new torrent then try to activate it it simply fails. (Download Failed!)

Being I know little about sql etc... does it matter that the Data Base is located on one drive and the download (in my case 'Active') directory lives on another?

What could be causing this.

---

### Post by kebes on 2007-09-04
> **mcdeath said:**
> Kebes thanks for all your help so far, you make using the Ubuntu forums a pleasure.
Thanks for the compliment! And, of course, you're welcome!

> Now what happens is that every time I upload a new torrent then try to activate it it simply fails. (Download Failed!)

Having the MySQL and data directories on separate drives should make no difference.

I suspect it's more of a mounting problem. I notice that the directories are owned by "root" ... I'm guessing that your mounted drive is owned by root, which makes it difficult for other programs to have permission to access it (even though you correctly set the directory to be world-writeable).

How is it mounted? Are you doing it manually (via "sudo mount") or did you add the drive to "/etc/fstab" ?



Try this test: go into the directory "/media/torrentdrive/active" and make a new file. Are you able to create a file without using "sudo" or your admin password?
```

cd /media/torrentdrive/active
touch testfile.txt

```


If you are not able to do that, then you need to change mounting permissions. If you are mounting manually, switch instead to using "fstab" to mount. (Either by using the mounting GUI tool in Ubuntu, or by carefully editing the file "/etc/fstab" and reboot or do "sudo mount -a" for changes to take effect.)


If you're already using fstab:
Check your "/etc/fstab" file and see what it says. You probably have a line like:
```

/dev/hdb1    /media/torrentdrive  ext3  defaults  0    2

```
You can try changing the mount options from "defaults" (which normally work fine...) to "auto,users,rw,exec,uid=mcdeath,gid=mcdeath"
```

/dev/hdb1    /media/torrentdrive  ext3  auto,users,rw,exec,uid=mcdeath,gid=mcdeath  0    0

```
What this is doing is letting users mount the drive as read-write, and moreover is setting the owner of the mounted partition as user "mcdeath". This way, it acts like a "normal" directory in your filesystem, rather than being a "root protected" directory.

---

### Post by DarkDancer on 2007-09-04
Ok, I changed my mind and am giving up on giving up. I seem to have hosed things though, is there any way to delete everything and start over?

---

### Post by kebes on 2007-09-04
> **DarkDancer said:**
> Ok, I changed my mind and am giving up on giving up. I seem to have hosed things though, is there any way to delete everything and start over?

Starting fresh is quite easy. Just delete the contents of the torrentflux directory ("/var/www/torrentflux" or "/var/www/flux" if you renamed it), and delete the MySQL table for torrentflux.
```

cd /var/www/flux/
rm * -r

```
then
```

mysql -uroot -p
mysql> DROP DATABASE torrentflux;
mysql> quit;

```


Then go back to how-to and start at the beginning.


(Actually, you can start entirely fresh by just using new names, like "tflux" instead of "torrentflux" for both the directory and the MySQL database...)

---

### Post by DarkDancer on 2007-09-04
Thanks, I'll work on that tomorrow... ;)

---

### Post by mcdeath on 2007-09-05
> **kebes said:**
> Thanks for the compliment! And, of course, you're welcome!
 
 
 
Having the MySQL and data directories on separate drives should make no difference.
 
I suspect it's more of a mounting problem. I notice that the directories are owned by "root" ... I'm guessing that your mounted drive is owned by root, which makes it difficult for other programs to have permission to access it (even though you correctly set the directory to be world-writeable).
 
How is it mounted? Are you doing it manually (via "sudo mount") or did you add the drive to "/etc/fstab" ?
 
 
 
Try this test: go into the directory "/media/torrentdrive/active" and make a new file. Are you able to create a file without using "sudo" or your admin password?
```

cd /media/torrentdrive/active
touch testfile.txt

```
 
 
If you are not able to do that, then you need to change mounting permissions. If you are mounting manually, switch instead to using "fstab" to mount. (Either by using the mounting GUI tool in Ubuntu, or by carefully editing the file "/etc/fstab" and reboot or do "sudo mount -a" for changes to take effect.)
 
 
If you're already using fstab:
Check your "/etc/fstab" file and see what it says. You probably have a line like:
```

/dev/hdb1    /media/torrentdrive  ext3  defaults  0    2

```
You can try changing the mount options from "defaults" (which normally work fine...) to "auto,users,rw,exec,uid=mcdeath,gid=mcdeath"
```

/dev/hdb1    /media/torrentdrive  ext3  auto,users,rw,exec,uid=mcdeath,gid=mcdeath  0    0

```
What this is doing is letting users mount the drive as read-write, and moreover is setting the owner of the mounted partition as user "mcdeath". This way, it acts like a "normal" directory in your filesystem, rather than being a "root protected" directory.
 
**I have followed your instructions to no avail, what seems to be the issue oddly enough is that I can add 1 torrent but if I try to add more than one it fails. I guess it can't be a permission thing if it lets me start and maintain the first torrent downloading.**
 
**I'm starting to feel a little lost here kebes. (sorry to dump on you)**
 
FYI here is my fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/Ubuntu-root /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=609d5c70-abfe-4f4d-a7e8-9b587f90dbe5 /boot           ext3    defaults        0       2
# /dev/hda5
UUID=dc114874-2763-4eab-b1b7-56a945f2b1f3 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd     /media/torrentdrive  ext3  auto,users,rw,exec,uid=plucker,gid=plucker  0    0

```

When I use sudo mount -a I get

mount: wrong fs type, bad option, bad superblock on /dev/hdd,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Not sure what thats about, all I can say is the drive is there and working.

---

### Post by kebes on 2007-09-05
> **mcdeath said:**
> I'm starting to feel a little lost here kebes. (sorry to dump on you)
Sorry this is so frustrating. If your new drive is working with everything except torrentflux, maybe you should consider putting the torrentflux "active" directory on the main hard drive, and then keeping the "complete" torrents on this new drive (manually moving them there).

Would that work for you?


 
> FYI here is my fstab
Is that your fstab after you made manual changes, or was it like that automatically?


When I use sudo mount -a I get

> 
mount: wrong fs type, bad option, bad superblock on /dev/hdd,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Not sure what thats about, all I can say is the drive is there and working.

So, when you use the drive manually, you can make files, delete files, and all that, without error? (And without using sudo...)

When I posted those instructions, I just assumed you had formatted this new drive as "ext3" ... was that right? Maybe you formatted it as ext2 or JFS or something?

Also, if you want, post the output of:
```

sudo mount -a
dmesg | tail

```
It could provide clues to why that error is being generated.

---

### Post by mcdeath on 2007-09-05
**Hey kebes we are on at the same time for a change. Okay here is the output you wanted.**

plucker@mcdeath:/$ sudo mount -a
dmesg | tailplucker@mcdeath:/$ dmesg | tail
[42951568.990000] hdc: tray open
[42951568.990000] end_request: I/O error, dev hdc, sector 0
[42951568.990000] hdc: tray open
[42951568.990000] end_request: I/O error, dev hdc, sector 4
[42951569.200000] SCSI subsystem initialized
[42951756.690000]  hdd: hdd1
[42951758.710000]  hdd: hdd1
[42951939.730000] kjournald starting.  Commit interval 5 seconds
[42951939.730000] EXT3 FS on hdd, internal journal
[42951939.730000] EXT3-fs: mounted filesystem with ordered data mode.
plucker@mcdeath:/$ 

**Also I think I got a little muddled so I have setup the drive again (Prt, format and mounted) as per this guide**

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

**My Fstab now**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/Ubuntu-root /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=609d5c70-abfe-4f4d-a7e8-9b587f90dbe5 /boot           ext3    defaults        0       2
# /dev/hda5
UUID=dc114874-2763-4eab-b1b7-56a945f2b1f3 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd    /media/torrentdrive   ext3    defaults     0        0

**My drive permissions** (I haven't yet tried going back to setup Fstab again as per your suggestion, I will in a few mins though)

lrwxrwxrwx 1 root    root       6 2007-08-21 22:53 cdrom -> cdrom0
drwxr-xr-x 2 root    root    4096 2007-08-21 22:53 cdrom0
drwxr-xr-x 4 plucker plucker 4096 2007-09-05 22:35 torrentdrive

**And of course now the folder within my 'torrentdrive' I created 'torrents' which of course contains the plucker folder that torrentflux creates when I upload my first torrent **

plucker@mcdeath:/media/torrentdrive$ cd torrents/
plucker@mcdeath:/media/torrentdrive/torrents$ ls -l
total 4
drwxr-xr-x 2 www-data www-data 4096 2007-09-05 22:38 plucker
plucker@mcdeath:/media/torrentdrive/torrents$ 

[B]I think your right here being the first torrent gets created when I have global drive permissions but once it creates the plucker sub folder with the www-data owner I get kicked as I have to sudo to create anything in that folder.

I did follow your first instructions with fstab but I didn't see any difference, maybe I did something wrong.[/B]

---

### Post by kebes on 2007-09-05
Your fstab and everything looks fine.

You may aswell revert to the default fstab line that was generated for you. It was obviously working fine since, as you pointed out, torrentflux is able to create the directory "plucker" inside "torrents."

So, torrentflux is able to read/write the drive. That's not the problem.


If you leave the directory "/media/torrentdrive/torrents/plucker/" the way that torrentflux set it (owned by "www-data"), it makes sense that you can't write in it (without using sudo), but you can still read from it. So that's fine, too.


But, you are still experiencing the same problem as before? If you leave the directory the way torrentflux wants it (owned by "www-data"), what happens?

It creates the first torrent properly, and then it can't create a second or third torrent?

---

### Post by mcdeath on 2007-09-05
**Yeah thats it, leaving it the way torrentflux wants only allows the first torrent to be uploaded all others fail.**
**FYI I just changed fstab**

/dev/hdd    /media/torrentdrive   ext3    auto,users,rw,exec,uid=plucker,gid=plucker  0    0

**and now I get this when I try and sudo mount -a**
mount: wrong fs type, bad option, bad superblock on /dev/hdd,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

As you say maybe I should leave it as is, I'll change it back now.

Wow this is a fun one yeah?

---

### Post by kebes on 2007-09-05
> As you say maybe I should leave it as is, I'll change it back now.
Yes, change your fstab back to the other way, since obviously one of the options isn't working properly anyway.

> Wow this is a fun one yeah?
Yes, this is weird! I can't imagine why the first torrent would work but then other ones don't! Is the first torrent that it downloads "proper" (the entire file, not corrupted, etc.).

If you delete that first torrent, is it able to create another one to replace it? I mean, is it limited to only one downloaded file at a time?

If you delete the "plucker" directory in "/media/torrentdrive/torrents/", what happens? Does it correctly create the directory again, and download a new torrent?


Obviously I have no clue what's going wrong here... so these are just random suggestions in order to hopefully get a hint.

---

### Post by mcdeath on 2007-09-05
Okay changed back fstab and I nolonger get that error. What is really baking my noodle is that changing all of that never changes the fact that Torrentflux only excepts the first upload.

Sorry kebes you probably have better things to do.......

Just saw your reply I'll try deleting etc...as per your suggestion.

---

### Post by mcdeath on 2007-09-05
yep it recreated the plucker folder and allowed me to upload the torrent (well the first one at least) I guess that the clincher.

Why does it allow the first torrent and no others, a torrent flux setting?
maybe we are looking at the wrong end of things here.....

---

### Post by mcdeath on 2007-09-05
Sorry I just realised I've been using the term upload.  I can upload the torrent its just when I go to start it it fails but I guess you knew what i meant.
Is there a system log or something in Ubuntu I should be looking at?

---

### Post by kebes on 2007-09-05
Just to confirm: the directory "/media/torrentdrive/torrents/" is set to 777 right? If you do:
```

cd /media/torrentdrive/
ls -laF

```
you should get the directory "torrents" as having permission "drwxrwxrwx". If not, then go:
```

cd /media/torrentdrive/
chmod 777 torrents

```



Also, check your torrentflux settings. Log in, go to "admin", "settings", and check that the Path is set to "/media/torrentdrive/torrents/" (**make sure that it ends with a slash!**).


I'll keep thinking about it... Can you post the output of these commands:
```

ls -laF /media/torrentdrive/
ls -laF -R /media/torrentdrive/torrents/

```
(This will generate a long listing of files... be sure to remove or alter any files that may reveal personal information... my intention here is only to see what all the permissions are. For instance torrentflux generates a hidden directory called ".torrents" in the download folder, and I'm wondering if it did so on your setup...)

---

### Post by mcdeath on 2007-09-05
As per your request, bedtime now buddy but I'll pop in tomorrow to see if you had any luck. cheers

**plucker@mcdeath:/media/torrentdrive$ ls -laF /media/torrentdrive/**
total 28
drwxr-xr-x 4 plucker plucker  4096 2007-09-05 22:35 ./
drwxr-xr-x 4 root    root     4096 2007-08-30 21:29 ../
drwx------ 2 plucker plucker 16384 2007-09-05 22:28 lost+found/
drwxrwxrwx 5 plucker plucker  4096 2007-09-05 23:18 torrents/
plucker@mcdeath:/media/torrentdrive$ 


and 


**plucker@mcdeath:/media/torrentdrive$ ls -laF -R /media/torrentdrive/torrents/**
/media/torrentdrive/torrents/:
total 20
drwxrwxrwx 5 plucker  plucker  4096 2007-09-05 23:18 ./
drwxr-xr-x 4 plucker  plucker  4096 2007-09-05 22:35 ../
drwx------ 6 www-data www-data 4096 2007-09-05 22:36 .BitTornado/
drwxr-xr-x 3 www-data www-data 4096 2007-09-05 23:39 plucker/
drwxr-xr-x 2 www-data www-data 4096 2007-09-05 23:41 .torrents/
ls: /media/torrentdrive/torrents/.BitTornado: Permission denied

/media/torrentdrive/torrents/plucker:
total 12
drwxr-xr-x 3 www-data www-data 4096 2007-09-05 23:39 ./
drwxrwxrwx 5 plucker  plucker  4096 2007-09-05 23:18 ../
drwxr-xr-x 6 www-data www-data 4096 2007-09-05 23:39 chemical tools/

/media/torrentdrive/torrents/plucker/chemical tools:
total 24
drwxr-xr-x 6 www-data www-data 4096 2007-09-05 23:39 ./
drwxr-xr-x 3 www-data www-data 4096 2007-09-05 23:39 ../
drwxr-xr-x 2 www-data www-data 4096 2007-09-05 23:39 Accelrys DS Visualizer/
drwxr-xr-x 2 www-data www-data 4096 2007-09-05 23:39 argus lab/
drwxr-xr-x 2 www-data www-data 4096 2007-09-05 23:39 chemsketch/
drwxr-xr-x 2 www-data www-data 4096 2007-09-05 23:39 Rasmol/

/media/torrentdrive/torrents/plucker/chemical tools/Accelrys DS Visualizer:
total 3348
drwxr-xr-x 2 www-data www-data    4096 2007-09-05 23:39 ./
drwxr-xr-x 6 www-data www-data    4096 2007-09-05 23:39 ../
-rw-r--r-- 1 www-data www-data  865661 2007-09-05 23:41 DS_visualizer_0407.pdf
-rw-r--r-- 1 www-data www-data 2542211 2007-09-05 23:41 setupdsv17.exe
-rw-r--r-- 1 www-data www-data       0 2007-09-05 23:39 setupdsvax17.exe

/media/torrentdrive/torrents/plucker/chemical tools/argus lab:
total 8
drwxr-xr-x 2 www-data www-data 4096 2007-09-05 23:39 ./
drwxr-xr-x 6 www-data www-data 4096 2007-09-05 23:39 ../
-rw-r--r-- 1 www-data www-data    0 2007-09-05 23:39 readme.txt
-rw-r--r-- 1 www-data www-data    0 2007-09-05 23:39 ReleaseNotes.txt
-rw-r--r-- 1 www-data www-data    0 2007-09-05 23:39 setup.exe

/media/torrentdrive/torrents/plucker/chemical tools/chemsketch:
total 8
drwxr-xr-x 2 www-data www-data 4096 2007-09-05 23:39 ./
drwxr-xr-x 6 www-data www-data 4096 2007-09-05 23:39 ../
-rw-r--r-- 1 www-data www-data    0 2007-09-05 23:39 chemsk10_.exe
-rw-r--r-- 1 www-data www-data    0 2007-09-05 23:39 chemsk.pdf
-rw-r--r-- 1 www-data www-data    0 2007-09-05 23:39 chemsk_r10.pdf
-rw-r--r-- 1 www-data www-data    0 2007-09-05 23:39 chemsk_t10.pdf

/media/torrentdrive/torrents/plucker/chemical tools/Rasmol:
total 8
drwxr-xr-x 2 www-data www-data 4096 2007-09-05 23:39 ./
drwxr-xr-x 6 www-data www-data 4096 2007-09-05 23:39 ../
-rw-r--r-- 1 www-data www-data    0 2007-09-05 23:39 RasWin_2_7_3_1_Install.exe

/media/torrentdrive/torrents/.torrents:
total 92
drwxr-xr-x 2 www-data www-data  4096 2007-09-05 23:41 ./
drwxrwxrwx 5 plucker  plucker   4096 2007-09-05 23:18 ../
-rw-r--r-- 1 www-data www-data    76 2007-09-05 23:41 mininova_org_chemical_and_biological_software_tools.stat
-rw-r--r-- 1 www-data www-data 63959 2007-09-05 23:39 mininova.org_Chemical_and_Biological_software_tools.torrent
-rw-r--r-- 1 www-data www-data 11636 2007-09-05 23:34 rsscache_b18a4a3b5a4dfc0c15c4e7223250174d
plucker@mcdeath:/media/torrentdrive$

---

### Post by kebes on 2007-09-05
Your directory structure looks almost identical to what I see on my install. Except for one thing... I have a directory called "queue" in the ".torrents" folder. It's a long-shot, but maybe if you manually create it...?

```

cd /media/torrentdrive/.torrents/
sudo mkdir queue
sudo chown www-data:www-data queue
sudo chmod 755 queue

```

---

### Post by mcdeath on 2007-09-05
hmmmmm it won't let me nav to that directory

plucker@mcdeath:~$ cd /media/torrentdrive/.torrents/
-bash: cd: /media/torrentdrive/.torrents/: No such file or directory
plucker@mcdeath:~$ sudo cd /media/torrentdrive/.torrents/
Password:
sudo: cd: command not found
plucker@mcdeath:~$ sudo cd /media/torrentdrive/.torrents/
sudo: cd: command not found

---

### Post by kebes on 2007-09-05
> **mcdeath said:**
> hmmmmm it won't let me nav to that directory

Oops. I meant "/media/torrentdrive/torrents/.torrents":
```

cd /media/torrentdrive/torrents/.torrents
sudo mkdir queue
sudo chown www-data:www-data queue
sudo chmod 755 queue

```

---

### Post by mcdeath on 2007-09-05
no luck kebes it still fails, let me know if you get any other ideas.

---

### Post by kebes on 2007-09-05
> **mcdeath said:**
> no luck kebes it still fails, let me know if you get any other ideas.

New idea. Use a symlink for the directory.

Log into torrentflux, go to "admin" then "settings". Change the value of "Path" (the first item) to:
/var/www/torrentflux/downloads/

(I'm assuming your install of TorrentFlux is at /var/www/torrentflux/)

Then, make a symlink:
```

cd /var/www/torrentflux/
mv downloads old-downloads
ln -s /media/torrentdrive/torrents/ downloads

```

Then open up torrentflux and see if it works better than it did before. (I'm trying to trick torrentflux into accepting the save path you want.)

---

### Post by DarkDancer on 2007-09-07
> 
Quote:
Originally Posted by DarkDancer View Post
Ok, I changed my mind and am giving up on giving up. I seem to have hosed things though, is there any way to delete everything and start over?
Starting fresh is quite easy. Just delete the contents of the torrentflux directory ("/var/www/torrentflux" or "/var/www/flux" if you renamed it), and delete the MySQL table for torrentflux.
Code:

cd /var/www/flux/
rm * -r

then
Code:

mysql -uroot -p
mysql> DROP DATABASE torrentflux;
mysql> quit;


Then go back to how-to and start at the beginning.

That doesn't seem to get rid of all of it, because certain steps tell me that I am trying to use a duplicate id, and when I get to step 4d, the first log in, it only shows me the files that are in that particular folder (torrentflux).

---

### Post by kebes on 2007-09-07
> **DarkDancer said:**
> That doesn't seem to get rid of all of it, because certain steps tell me that I am trying to use a duplicate id, and when I get to step 4d, the first log in, it only shows me the files that are in that particular folder (torrentflux).

Hmm... if you can give me more information about what steps are giving errors, and exactly what the errors say, I might be able to figure it out.


Another option, as I said before, is to create a new installation using different names for the installation directory and the MySQL database. You can have two independent torrentflux installs side-by-side, so by using a new set of names you can avoid any potential conflict with the last install.

---

### Post by DarkDancer on 2007-09-07
Ok, I am trying to create the new installation, but when I get to:

> Since your PHP/MySQL interface will eventually be world-accessible, it makes sense to put some security in place. By default MySQL starts with no password, so you should certainly set one:
Code:

$ mysqladmin -uroot password 'new-password'



I get:

> mysqladmin: connect to server at 'localhost' failederror: 'Access denied for user 'root'@'localhost' (using password: NO)'

---

### Post by mcdeath on 2007-09-07
> **kebes said:**
> New idea. Use a symlink for the directory.

Log into torrentflux, go to "admin" then "settings". Change the value of "Path" (the first item) to:
/var/www/torrentflux/downloads/

(I'm assuming your install of TorrentFlux is at /var/www/torrentflux/)

Then, make a symlink:
```

cd /var/www/torrentflux/
mv downloads old-downloads
ln -s /media/torrentdrive/torrents/ downloads

```

Then open up torrentflux and see if it works better than it did before. (I'm trying to trick torrentflux into accepting the save path you want.)

Hey kebes sorry got busy for a couple of days.  Mate I tried your suggestion with no success.
I think its time to use something else.

BTW I'm using ver2.1 should I try 2.3?

---

### Post by kebes on 2007-09-07
> **DarkDancer said:**
> mysqladmin: connect to server at 'localhost' failederror: 'Access denied for user 'root'@'localhost' (using password: NO)'

You're probably getting that error because you already set a password for MySQL root. So in fact you can just skip that step. (But, of course, you have to know what your MySQL root password is for later steps.)

---

### Post by kebes on 2007-09-07
> **mcdeath said:**
> Hey kebes sorry got busy for a couple of days.  Mate I tried your suggestion.

Now I'm getting this error when I try to queue a torrent.


Okay... so my symlink idea didn't help (you can revert your torrentflux settings). You said that torrentflux works properly when you just download to the default directory (/var/www/torrentflux/downloads/), which is on the same partition as torrentflux and mysql. Is that correct?


So you can download unlimited torrents to that default location, and then move them elsewhere... but it won't let you change the download directory?

---

### Post by DarkDancer on 2007-09-07
I have another question (sorry to be a pain....) the first time I went through this it was there, but now everytime I go to the step where you do $ sudo nano /var/www/torrentflux/config.php, that file does not exist there. There is one in the html folder, that seems like it looks like what I recall from the first one, so I have been copying it to the torrentflux folder, is that ok?

---

### Post by kebes on 2007-09-07
> **DarkDancer said:**
> I have another question (sorry to be a pain....) the first time I went through this it was there, but now everytime I go to the step where you do $ sudo nano /var/www/torrentflux/config.php, that file does not exist there. There is one in the html folder, that seems like it looks like what I recall from the first one, so I have been copying it to the torrentflux folder, is that ok?

Yes! In fact, make sure you copy **everything** from the "html" sub-folder into "/var/www/torrentflux/" (all files, all sub-folders).

In step 4.a. you are supposed to copy the contents of the html folder from the download into "/var/www/torrentflux/"...

---

### Post by DarkDancer on 2007-09-07
I must have missed that step, thanks.. ;)

---

### Post by DarkDancer on 2007-09-07
Ok, got past that, I tried the instructions, but the file was still not there, so I just hand copied everything out of the directory.

However, now when I get to:

> 4.d First login.
Now you can go to your torrentflux page, using a web-browser:
[http://localhost/torrentflux/](http://localhost/torrentflux/)

I get:

> Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Fatal error: Unknown: Failed opening required '/var/www/torrentflux2/index.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 

---

### Post by kebes on 2007-09-07
> **DarkDancer said:**
> Ok, got past that, I tried the instructions, but the file was still not there, so I just hand copied everything out of the directory.:

1. When you hand-copied the files, you made sure to copy all directories and sub-directories, right? There are many files that need to be available.

2. Depending how you did the copy, maybe the permissions are not matching up. The various files should all have world read permission... you can set it by going:
```

cd /var/www/torrentflux2/
sudo chmod +r -R

```

3. If you want, post the output of this command:
ls -laF -R /var/www/torrentflux2/
This outputs a full list of the files along with their owner/permissions.... just to make sure some files didn't get lost or whatever...

4. In the error message you posted, did that second error have a line number after the "on line" part? That might help.

---

### Post by DarkDancer on 2007-09-08
Ok, darkdancer@darkdancers:/var/www/torrentflux2$ sudo chmod +r -R yields:

> chmod: missing operand after `+r'
Try `chmod --help' for more information.

and  ls -laF -R /var/www/torrentflux2/ gives:

> -rwxr-x--- 1 darkdancer darkdancer    51 2007-09-07 21:45 .cvsignore*
-rwxr-x--- 1 darkdancer darkdancer  5310 2007-09-07 21:45 DownloaderFeedback.py*
-rwxr-x--- 1 darkdancer darkdancer 22608 2007-09-07 21:45 Downloader.py*
-rwxr-x--- 1 darkdancer darkdancer 10227 2007-09-07 21:45 Encrypter.py*
-rwxr-x--- 1 darkdancer darkdancer  2240 2007-09-07 21:45 fakeopen.py*
-rwxr-x--- 1 darkdancer darkdancer  8479 2007-09-07 21:45 FileSelector.py*
-rwxr-x--- 1 darkdancer darkdancer   298 2007-09-07 21:45 Filter.py*
-rwxr-x--- 1 darkdancer darkdancer  8461 2007-09-07 21:45 HTTPDownloader.py*
-rwxr-x--- 1 darkdancer darkdancer    13 2007-09-07 21:45 __init__.py*
-rwxr-x--- 1 darkdancer darkdancer  9038 2007-09-07 21:45 makemetafile.py*
-rwxr-x--- 1 darkdancer darkdancer  2731 2007-09-07 21:45 NatCheck.py*
-rwxr-x--- 1 darkdancer darkdancer 11915 2007-09-07 21:45 PiecePicker.py*
-rwxr-x--- 1 darkdancer darkdancer 14089 2007-09-07 21:45 Rerequester.py*
-rwxr-x--- 1 darkdancer darkdancer  6581 2007-09-07 21:45 Statistics.py*
-rwxr-x--- 1 darkdancer darkdancer 20368 2007-09-07 21:45 Storage.py*
-rwxr-x--- 1 darkdancer darkdancer 37256 2007-09-07 21:45 StorageWrapper.py*
-rwxr-x--- 1 darkdancer darkdancer  3757 2007-09-07 21:45 StreamCheck.py*
-rwxr-x--- 1 darkdancer darkdancer  7244 2007-09-07 21:45 T2T.py*
-rwxr-x--- 1 darkdancer darkdancer 46229 2007-09-07 21:45 track.py*
-rwxr-x--- 1 darkdancer darkdancer  4789 2007-09-07 21:45 Uploader.py*

/var/www/torrentflux2/TF_BitTornado/BitTornado/bt1/cvs:
total 32
drwxr-x--- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-x--- 3 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-x--- 1 darkdancer darkdancer 1060 2007-09-07 21:45 Entries*
-rwxr-x--- 1 darkdancer darkdancer  515 2007-09-07 21:45 Entries.Extra*
-rwxr-x--- 1 darkdancer darkdancer  515 2007-09-07 21:45 Entries.Extra.Old*
-rwxr-x--- 1 darkdancer darkdancer 1060 2007-09-07 21:45 Entries.Old*
-rwxr-x--- 1 darkdancer darkdancer   26 2007-09-07 21:45 Repository*
-rwxr-x--- 1 darkdancer darkdancer   40 2007-09-07 21:45 Root*

/var/www/torrentflux2/TF_BitTornado/BitTornado/cvs:
total 36
drwxr-x--- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-x--- 4 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-x--- 1 darkdancer darkdancer 1375 2007-09-07 21:45 Entries*
-rwxr-x--- 1 darkdancer darkdancer  700 2007-09-07 21:45 Entries.Extra*
-rwxr-x--- 1 darkdancer darkdancer  700 2007-09-07 21:45 Entries.Extra.Old*
-rwxr-x--- 1 darkdancer darkdancer   12 2007-09-07 21:45 Entries.Log*
-rwxr-x--- 1 darkdancer darkdancer 1375 2007-09-07 21:45 Entries.Old*
-rwxr-x--- 1 darkdancer darkdancer   22 2007-09-07 21:45 Repository*
-rwxr-x--- 1 darkdancer darkdancer   40 2007-09-07 21:45 Root*

/var/www/torrentflux2/TF_BitTornado/original_src:
total 400
drwxr-x--- 2 darkdancer darkdancer   4096 2007-09-07 21:06 ./
drwxr-x--- 4 darkdancer darkdancer   4096 2007-09-07 21:06 ../
-rwxr-x--- 1 darkdancer darkdancer 189992 2007-09-07 21:45 BitTornado-0.3.15.tar.gz*
-rwxr-x--- 1 darkdancer darkdancer 194718 2007-09-07 21:45 BitTornado-0.3.17.tar.gz*
-rwxr-x--- 1 darkdancer darkdancer     13 2007-09-07 21:45 index.html*

/var/www/torrentflux2/themes:
total 72
drwxr-x--- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-x 12 darkdancer darkdancer 4096 2007-09-07 23:23 ../
drwxr-x---  4 darkdancer darkdancer 4096 2007-09-07 21:06 BlueFlux/
drwxr-x---  3 darkdancer darkdancer 4096 2007-09-07 21:06 chrome/
drwxr-x---  3 darkdancer darkdancer 4096 2007-09-07 21:06 command/
drwxr-x---  3 darkdancer darkdancer 4096 2007-09-07 21:06 g4e/
drwxr-x---  3 darkdancer darkdancer 4096 2007-09-07 21:06 glass/
drwxr-x---  3 darkdancer darkdancer 4096 2007-09-07 21:06 glyphic/
drwxr-x---  3 darkdancer darkdancer 4096 2007-09-07 21:06 hornet/
-rwxr-x---  1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*
drwxr-x---  3 darkdancer darkdancer 4096 2007-09-07 21:06 mape/
drwxr-x---  3 darkdancer darkdancer 4096 2007-09-07 21:06 matrix/
drwxr-x---  3 darkdancer darkdancer 4096 2007-09-07 21:06 matrix_chinese/
drwxr-x---  3 darkdancer darkdancer 4096 2007-09-07 21:06 midnight/
drwxr-x---  3 darkdancer darkdancer 4096 2007-09-07 21:06 minimal/
drwxr-x---  3 darkdancer darkdancer 4096 2007-09-07 21:06 mint/
drwxr-x---  3 darkdancer darkdancer 4096 2007-09-07 21:06 rust/
drwxr-x---  3 darkdancer darkdancer 4096 2007-09-07 21:06 slate/

/var/www/torrentflux2/themes/BlueFlux:
total 28
drwxr-x---  4 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-x--- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-x---  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-x---  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
drwxr-x---  2 darkdancer darkdancer 4096 2007-09-07 21:06 main-icons/
-rwxr-x---  1 darkdancer darkdancer 1801 2007-09-07 21:45 readme.txt*
-rwxr-x---  1 darkdancer darkdancer 3954 2007-09-07 21:45 style.css*

/var/www/torrentflux2/themes/BlueFlux/images:
total 60
drwxr-x--- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-x--- 4 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-x--- 1 darkdancer darkdancer   98 2007-09-07 21:45 admin.gif*
-rwxr-x--- 1 darkdancer darkdancer   43 2007-09-07 21:45 bar.gif*
-rwxr-x--- 1 darkdancer darkdancer  113 2007-09-07 21:45 directory.gif*
-rwxr-x--- 1 darkdancer darkdancer  108 2007-09-07 21:45 history.gif*
-rwxr-x--- 1 darkdancer darkdancer   94 2007-09-07 21:45 home.gif*
-rwxr-x--- 1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*
-rwxr-x--- 1 darkdancer darkdancer  112 2007-09-07 21:45 messages_off.gif*
-rwxr-x--- 1 darkdancer darkdancer  541 2007-09-07 21:45 messages_on.gif*
-rwxr-x--- 1 darkdancer darkdancer   77 2007-09-07 21:45 noglass.gif*
-rwxr-x--- 1 darkdancer darkdancer  105 2007-09-07 21:45 profile.gif*
-rwxr-x--- 1 darkdancer darkdancer 4650 2007-09-07 21:45 proglass.gif*
-rwxr-x--- 1 darkdancer darkdancer   58 2007-09-07 21:45 progressbar.gif*

/var/www/torrentflux2/themes/BlueFlux/main-icons:
total 88
drwxr-x--- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-x--- 4 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-x--- 1 darkdancer darkdancer  318 2007-09-07 21:45 black.gif*
-rwxr-x--- 1 darkdancer darkdancer  933 2007-09-07 21:45 compressed.gif*
-rwxr-x--- 1 darkdancer darkdancer   95 2007-09-07 21:45 delete_off.gif*
-rwxr-x--- 1 darkdancer darkdancer   95 2007-09-07 21:45 delete_on.gif*
-rwxr-x--- 1 darkdancer darkdancer   92 2007-09-07 21:45 download.gif*
-rwxr-x--- 1 darkdancer darkdancer   92 2007-09-07 21:45 download_on.gif*
-rwxr-x--- 1 darkdancer darkdancer   92 2007-09-07 21:45 download_owner.gif*
-rwxr-x--- 1 darkdancer darkdancer 3128 2007-09-07 21:45 favicon.ico*
-rwxr-x--- 1 darkdancer darkdancer 1010 2007-09-07 21:45 folder.gif*
-rwxr-x--- 1 darkdancer darkdancer  319 2007-09-07 21:45 green.gif*
-rwxr-x--- 1 darkdancer darkdancer   91 2007-09-07 21:45 kill.gif*
-rwxr-x--- 1 darkdancer darkdancer  988 2007-09-07 21:45 locked.gif*
-rwxr-x--- 1 darkdancer darkdancer   80 2007-09-07 21:45 logout.gif*
-rwxr-x--- 1 darkdancer darkdancer  318 2007-09-07 21:45 red.gif*
-rwxr-x--- 1 darkdancer darkdancer   92 2007-09-07 21:45 run_on.gif*
-rwxr-x--- 1 darkdancer darkdancer   91 2007-09-07 21:45 seed_on.gif*
-rwxr-x--- 1 darkdancer darkdancer  960 2007-09-07 21:45 tar_down.gif*
-rwxr-x--- 1 darkdancer darkdancer  210 2007-09-07 21:45 user.gif*
-rwxr-x--- 1 darkdancer darkdancer  596 2007-09-07 21:45 user_group.gif*
-rwxr-x--- 1 darkdancer darkdancer  318 2007-09-07 21:45 yellow.gif*

/var/www/torrentflux2/themes/chrome:
total 20
drwxr-x---  3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-x--- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-x---  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-x---  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
-rwxr-x---  1 darkdancer darkdancer 3871 2007-09-07 21:45 style.css*

/var/www/torrentflux2/themes/chrome/images:
total 64
drwxr-x--- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-x--- 3 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-x--- 1 darkdancer darkdancer  418 2007-09-07 21:45 admin.gif*
-rwxr-x--- 1 darkdancer darkdancer 6795 2007-09-07 21:45 bar.gif*
-rwxr-x--- 1 darkdancer darkdancer  480 2007-09-07 21:45 directory.gif*
-rwxr-x--- 1 darkdancer darkdancer  450 2007-09-07 21:45 history.gif*
-rwxr-x--- 1 darkdancer darkdancer  420 2007-09-07 21:45 home.gif*
-rwxr-x--- 1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*
-rwxr-x--- 1 darkdancer darkdancer  488 2007-09-07 21:45 messages_off.gif*
-rwxr-x--- 1 darkdancer darkdancer 1357 2007-09-07 21:45 messages_on.gif*
-rwxr-x--- 1 darkdancer darkdancer  623 2007-09-07 21:45 noglass.gif*
-rwxr-x--- 1 darkdancer darkdancer  474 2007-09-07 21:45 profile.gif*
-rwxr-x--- 1 darkdancer darkdancer 2577 2007-09-07 21:45 proglass.gif*
-rwxr-x--- 1 darkdancer darkdancer  146 2007-09-07 21:45 progressbar.gif*
-rwxr-x--- 1 darkdancer darkdancer  454 2007-09-07 21:45 torrents.gif*

/var/www/torrentflux2/themes/command:
total 24
drwxr-x---  3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-x--- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-x---  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-x---  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
-rwxr-x---  1 darkdancer darkdancer 4145 2007-09-07 21:45 style.css*

/var/www/torrentflux2/themes/command/images:
total 60
drwxr-x--- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-x--- 3 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-x--- 1 darkdancer darkdancer  418 2007-09-07 21:45 admin.gif*
-rwxr-x--- 1 darkdancer darkdancer 2924 2007-09-07 21:45 bar.gif*
-rwxr-x--- 1 darkdancer darkdancer  480 2007-09-07 21:45 directory.gif*
-rwxr-x--- 1 darkdancer darkdancer  450 2007-09-07 21:45 history.gif*
-rwxr-x--- 1 darkdancer darkdancer  420 2007-09-07 21:45 home.gif*
-rwxr-x--- 1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*
-rwxr-x--- 1 darkdancer darkdancer  488 2007-09-07 21:45 messages_off.gif*
-rwxr-x--- 1 darkdancer darkdancer 1357 2007-09-07 21:45 messages_on.gif*
-rwxr-x--- 1 darkdancer darkdancer  623 2007-09-07 21:45 noglass.gif*
-rwxr-x--- 1 darkdancer darkdancer  474 2007-09-07 21:45 profile.gif*
-rwxr-x--- 1 darkdancer darkdancer 3449 2007-09-07 21:45 proglass.gif*
-rwxr-x--- 1 darkdancer darkdancer  146 2007-09-07 21:45 progressbar.gif*
-rwxr-x--- 1 darkdancer darkdancer  454 2007-09-07 21:45 torrents.gif*

/var/www/torrentflux2/themes/g4e:
total 24
drwxr-x---  3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-x--- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-x---  1 darkdancer darkdancer 3128 2007-09-07 21:45 favicon.ico*
drwxr-x---  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-x---  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
-rwxr-x---  1 darkdancer darkdancer 3971 2007-09-07 21:45 style.css*

/var/www/torrentflux2/themes/g4e/images:
total 76
drwxr-x--- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-x--- 3 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-x--- 1 darkdancer darkdancer  893 2007-09-07 21:45 admin.gif*
-rwxr-x--- 1 darkdancer darkdancer 1684 2007-09-07 21:45 bar.gif*
-rwxr-x--- 1 darkdancer darkdancer  913 2007-09-07 21:45 directory.gif*
-rwxr-x--- 1 darkdancer darkdancer 5736 2007-09-07 21:45 gentoo2.jpg*
-rwxr-x--- 1 darkdancer darkdancer 4324 2007-09-07 21:45 gentoo2.png*
-rwxr-x--- 1 darkdancer darkdancer  322 2007-09-07 21:45 gentoo.jpg*
-rwxr-x--- 1 darkdancer darkdancer  108 2007-09-07 21:45 history.gif*
-rwxr-x--- 1 darkdancer darkdancer  888 2007-09-07 21:45 home.gif*
-rwxr-x--- 1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*
-rwxr-x--- 1 darkdancer darkdancer  112 2007-09-07 21:45 messages_off.gif*
-rwxr-x--- 1 darkdancer darkdancer  112 2007-09-07 21:45 messages_on.gif*
-rwxr-x--- 1 darkdancer darkdancer   77 2007-09-07 21:45 noglass.gif*
-rwxr-x--- 1 darkdancer darkdancer  901 2007-09-07 21:45 profile.gif*
-rwxr-x--- 1 darkdancer darkdancer 2726 2007-09-07 21:45 proglass.gif*
-rwxr-x--- 1 darkdancer darkdancer 1224 2007-09-07 21:45 progressbar.gif*

/var/www/torrentflux2/themes/glass:
total 20
drwxr-x---  3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-x--- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-x---  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-x---  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
-rwxr-x---  1 darkdancer darkdancer 3852 2007-09-07 21:45 style.css*

/var/www/torrentflux2/themes/glass/images:
total 56
drwxr-x--- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-x--- 3 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-x--- 1 darkdancer darkdancer  508 2007-09-07 21:45 admin.gif*
-rwxr-x--- 1 darkdancer darkdancer 3169 2007-09-07 21:45 bar.gif*
-rwxr-x--- 1 darkdancer darkdancer  562 2007-09-07 21:45 directory.gif*
-rwxr-x--- 1 darkdancer darkdancer  533 2007-09-07 21:45 history.gif*
-rwxr-x--- 1 darkdancer darkdancer  511 2007-09-07 21:45 home.gif*
-rwxr-x--- 1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*
-rwxr-x--- 1 darkdancer darkdancer  588 2007-09-07 21:45 messages_off.gif*
-rwxr-x--- 1 darkdancer darkdancer 1812 2007-09-07 21:45 messages_on.gif*
-rwxr-x--- 1 darkdancer darkdancer  348 2007-09-07 21:45 noglass.gif*
-rwxr-x--- 1 darkdancer darkdancer  558 2007-09-07 21:45 profile.gif*
-rwxr-x--- 1 darkdancer darkdancer 1760 2007-09-07 21:45 proglass.gif*
-rwxr-x--- 1 darkdancer darkdancer  319 2007-09-07 21:45 progressbar.gif*

/var/www/torrentflux2/themes/glyphic:
total 20
drwxr-x---  3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-x--- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-x---  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-x---  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
-rwxr-x---  1 darkdancer darkdancer 3854 2007-09-07 21:45 style.css*

/var/www/torrentflux2/themes/glyphic/images:
total 64
drwxr-x--- 2 darkdancer darkdancer  4096 2007-09-07 21:06 ./
drwxr-x--- 3 darkdancer darkdancer  4096 2007-09-07 21:06 ../
-rwxr-x--- 1 darkdancer darkdancer   508 2007-09-07 21:45 admin.gif*
-rwxr-x--- 1 darkdancer darkdancer 11035 2007-09-07 21:45 bar.gif*
-rwxr-x--- 1 darkdancer darkdancer   562 2007-09-07 21:45 directory.gif*
-rwxr-x--- 1 darkdancer darkdancer   533 2007-09-07 21:45 history.gif*
-rwxr-x--- 1 darkdancer darkdancer   511 2007-09-07 21:45 home.gif*
-rwxr-x--- 1 darkdancer darkdancer    13 2007-09-07 21:45 index.html*
-rwxr-x--- 1 darkdancer darkdancer   588 2007-09-07 21:45 messages_off.gif*
-rwxr-x--- 1 darkdancer darkdancer  1812 2007-09-07 21:45 messages_on.gif*
-rwxr-x--- 1 darkdancer darkdancer   623 2007-09-07 21:45 noglass.gif*
-rwxr-x--- 1 darkdancer darkdancer   558 2007-09-07 21:45 profile.gif*
-rwxr-x--- 1 darkdancer darkdancer  2577 2007-09-07 21:45 proglass.gif*
-rwxr-x--- 1 darkdancer darkdancer   146 2007-09-07 21:45 progressbar.gif*

/var/www/torrentflux2/themes/hornet:
total 20
drwxr-x---  3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-x--- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-x---  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-x---  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
-rwxr-x---  1 darkdancer darkdancer 3455 2007-09-07 21:45 style.css*

/var/www/torrentflux2/themes/hornet/images:
total 60
drwxr-x--- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-x--- 3 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-x--- 1 darkdancer darkdancer  424 2007-09-07 21:45 admin.gif*
-rwxr-x--- 1 darkdancer darkdancer 1710 2007-09-07 21:45 bar.gif*
-rwxr-x--- 1 darkdancer darkdancer  480 2007-09-07 21:45 directory.gif*
-rwxr-x--- 1 darkdancer darkdancer  449 2007-09-07 21:45 history.gif*
-rwxr-x--- 1 darkdancer darkdancer  420 2007-09-07 21:45 home.gif*
-rwxr-x--- 1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*
-rwxr-x--- 1 darkdancer darkdancer  489 2007-09-07 21:45 messages_off.gif*
-rwxr-x--- 1 darkdancer darkdancer 1507 2007-09-07 21:45 messages_on.gif*
-rwxr-x--- 1 darkdancer darkdancer  623 2007-09-07 21:45 noglass.gif*
-rwxr-x--- 1 darkdancer darkdancer  472 2007-09-07 21:45 profile.gif*
-rwxr-x--- 1 darkdancer darkdancer 2569 2007-09-07 21:45 proglass.gif*
-rwxr-x--- 1 darkdancer darkdancer  138 2007-09-07 21:45 progressbar.gif*
-rwxr-x--- 1 darkdancer darkdancer  454 2007-09-07 21:45 torrents.gif*

/var/www/torrentflux2/themes/mape:
total 20
drwxr-x---  3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-x--- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-x---  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-x---  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
-rwxr-x---  1 darkdancer darkdancer 3662 2007-09-07 21:45 style.css*

/var/www/torrentflux2/themes/mape/images:
total 76
drwxr-x--- 2 darkdancer darkdancer  4096 2007-09-07 21:06 ./
drwxr-x--- 3 darkdancer darkdancer  4096 2007-09-07 21:06 ../
-rwxr-x--- 1 darkdancer darkdancer  1420 2007-09-07 21:45 admin.gif*
-rwxr-x--- 1 darkdancer darkdancer  1081 2007-09-07 21:45 bar.gif*
-rwxr-x--- 1 darkdancer darkdancer  1465 2007-09-07 21:45 directory.gif*
-rwxr-x--- 1 darkdancer darkdancer  1432 2007-09-07 21:45 history.gif*
-rwxr-x--- 1 darkdancer darkdancer  1425 2007-09-07 21:45 home.gif*
-rwxr-x--- 1 darkdancer darkdancer    13 2007-09-07 21:45 index.html*
-rwxr-x--- 1 darkdancer darkdancer  1465 2007-09-07 21:45 messages_off.gif*
-rwxr-x--- 1 darkdancer darkdancer  1460 2007-09-07 21:45 messages_on.gif*
-rwxr-x--- 1 darkdancer darkdancer    83 2007-09-07 21:45 noglass.gif*
-rwxr-x--- 1 darkdancer darkdancer  1472 2007-09-07 21:45 profile.gif*
-rwxr-x--- 1 darkdancer darkdancer  1760 2007-09-07 21:45 proglass.gif*
-rwxr-x--- 1 darkdancer darkdancer   319 2007-09-07 21:45 progressbar.gif*
-rwxr-x--- 1 darkdancer darkdancer 16896 2007-09-07 21:45 Thumbs.db*

/var/www/torrentflux2/themes/matrix:
total 20
drwxr-x---  3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-x--- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-x---  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-x---  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
-rwxr-x---  1 darkdancer darkdancer 3852 2007-09-07 21:45 style.css*

/var/www/torrentflux2/themes/matrix/images:
total 56
drwxr-x--- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-x--- 3 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-x--- 1 darkdancer darkdancer  418 2007-09-07 21:45 admin.gif*
-rwxr-x--- 1 darkdancer darkdancer 1718 2007-09-07 21:45 bar.gif*
-rwxr-x--- 1 darkdancer darkdancer  480 2007-09-07 21:45 directory.gif*
-rwxr-x--- 1 darkdancer darkdancer  450 2007-09-07 21:45 history.gif*
-rwxr-x--- 1 darkdancer darkdancer  420 2007-09-07 21:45 home.gif*
-rwxr-x--- 1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*
-rwxr-x--- 1 darkdancer darkdancer  488 2007-09-07 21:45 messages_off.gif*
-rwxr-x--- 1 darkdancer darkdancer 1357 2007-09-07 21:45 messages_on.gif*
-rwxr-x--- 1 darkdancer darkdancer  623 2007-09-07 21:45 noglass.gif*
-rwxr-x--- 1 darkdancer darkdancer  474 2007-09-07 21:45 profile.gif*
-rwxr-x--- 1 darkdancer darkdancer 2577 2007-09-07 21:45 proglass.gif*
-rwxr-x--- 1 darkdancer darkdancer  146 2007-09-07 21:45 progressbar.gif*

/var/www/torrentflux2/themes/matrix_chinese:
total 20
drwxr-x---  3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-x--- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-x---  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-x---  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
-rwxr-x---  1 darkdancer darkdancer 3455 2007-09-07 21:45 style.css*

/var/www/torrentflux2/themes/matrix_chinese/images:
total 56
drwxr-x--- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-x--- 3 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-x--- 1 darkdancer darkdancer  287 2007-09-07 21:45 admin.gif*
-rwxr-x--- 1 darkdancer darkdancer 1718 2007-09-07 21:45 bar.gif*
-rwxr-x--- 1 darkdancer darkdancer  281 2007-09-07 21:45 directory.gif*
-rwxr-x--- 1 darkdancer darkdancer  286 2007-09-07 21:45 history.gif*
-rwxr-x--- 1 darkdancer darkdancer  283 2007-09-07 21:45 home.gif*
-rwxr-x--- 1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*
-rwxr-x--- 1 darkdancer darkdancer  283 2007-09-07 21:45 messages_off.gif*
-rwxr-x--- 1 darkdancer darkdancer  283 2007-09-07 21:45 messages_on.gif*
-rwxr-x--- 1 darkdancer darkdancer  623 2007-09-07 21:45 noglass.gif*
-rwxr-x--- 1 darkdancer darkdancer  309 2007-09-07 21:45 profile.gif*
-rwxr-x--- 1 darkdancer darkdancer 2577 2007-09-07 21:45 proglass.gif*
-rwxr-x--- 1 darkdancer darkdancer  146 2007-09-07 21:45 progressbar.gif*

/var/www/torrentflux2/themes/midnight:
total 20
drwxr-x---  3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-x--- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-x---  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-x---  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
-rwxr-x---  1 darkdancer darkdancer 3940 2007-09-07 21:45 style.css*

/var/www/torrentflux2/themes/midnight/images:
total 56
drwxr-x--- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-x--- 3 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-x--- 1 darkdancer darkdancer  276 2007-09-07 21:45 admin.gif*
-rwxr-x--- 1 darkdancer darkdancer  453 2007-09-07 21:45 bar.gif*
-rwxr-x--- 1 darkdancer darkdancer  326 2007-09-07 21:45 directory.gif*
-rwxr-x--- 1 darkdancer darkdancer  306 2007-09-07 21:45 history.gif*
-rwxr-x--- 1 darkdancer darkdancer  259 2007-09-07 21:45 home.gif*
-rwxr-x--- 1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*
-rwxr-x--- 1 darkdancer darkdancer  344 2007-09-07 21:45 messages_off.gif*
-rwxr-x--- 1 darkdancer darkdancer 1003 2007-09-07 21:45 messages_on.gif*
-rwxr-x--- 1 darkdancer darkdancer   72 2007-09-07 21:45 noglass.gif*
-rwxr-x--- 1 darkdancer darkdancer  331 2007-09-07 21:45 profile.gif*
-rwxr-x--- 1 darkdancer darkdancer 2132 2007-09-07 21:45 proglass.gif*
-rwxr-x--- 1 darkdancer darkdancer   58 2007-09-07 21:45 progressbar.gif*

/var/www/torrentflux2/themes/minimal:
total 20
drwxr-x---  3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-x--- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-x---  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-x---  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
-rwxr-x---  1 darkdancer darkdancer 3854 2007-09-07 21:45 style.css*

/var/www/torrentflux2/themes/minimal/images:
total 56
drwxr-x--- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-x--- 3 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-x--- 1 darkdancer darkdancer  508 2007-09-07 21:45 admin.gif*
-rwxr-x--- 1 darkdancer darkdancer  799 2007-09-07 21:45 bar.gif*
-rwxr-x--- 1 darkdancer darkdancer  562 2007-09-07 21:45 directory.gif*
-rwxr-x--- 1 darkdancer darkdancer  533 2007-09-07 21:45 history.gif*
-rwxr-x--- 1 darkdancer darkdancer  511 2007-09-07 21:45 home.gif*
-rwxr-x--- 1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*
-rwxr-x--- 1 darkdancer darkdancer  588 2007-09-07 21:45 messages_off.gif*
-rwxr-x--- 1 darkdancer darkdancer 1812 2007-09-07 21:45 messages_on.gif*
-rwxr-x--- 1 darkdancer darkdancer  809 2007-09-07 21:45 noglass.gif*
-rwxr-x--- 1 darkdancer darkdancer  558 2007-09-07 21:45 profile.gif*
-rwxr-x--- 1 darkdancer darkdancer 3010 2007-09-07 21:45 proglass.gif*
-rwxr-x--- 1 darkdancer darkdancer  154 2007-09-07 21:45 progressbar.gif*

/var/www/torrentflux2/themes/mint:
total 20
drwxr-x---  3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-x--- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-x---  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-x---  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
-rwxr-x---  1 darkdancer darkdancer 3852 2007-09-07 21:45 style.css*

/var/www/torrentflux2/themes/mint/images:
total 60
drwxr-x--- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-x--- 3 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-x--- 1 darkdancer darkdancer  426 2007-09-07 21:45 admin.gif*
-rwxr-x--- 1 darkdancer darkdancer 1710 2007-09-07 21:45 bar.gif*
-rwxr-x--- 1 darkdancer darkdancer  482 2007-09-07 21:45 directory.gif*
-rwxr-x--- 1 darkdancer darkdancer  450 2007-09-07 21:45 history.gif*
-rwxr-x--- 1 darkdancer darkdancer  422 2007-09-07 21:45 home.gif*
-rwxr-x--- 1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*
-rwxr-x--- 1 darkdancer darkdancer  492 2007-09-07 21:45 messages_off.gif*
-rwxr-x--- 1 darkdancer darkdancer 1616 2007-09-07 21:45 messages_on.gif*
-rwxr-x--- 1 darkdancer darkdancer  623 2007-09-07 21:45 noglass.gif*
-rwxr-x--- 1 darkdancer darkdancer  477 2007-09-07 21:45 profile.gif*
-rwxr-x--- 1 darkdancer darkdancer 2569 2007-09-07 21:45 proglass.gif*
-rwxr-x--- 1 darkdancer darkdancer  138 2007-09-07 21:45 progressbar.gif*
-rwxr-x--- 1 darkdancer darkdancer  454 2007-09-07 21:45 torrents.gif*

/var/www/torrentflux2/themes/rust:
total 20
drwxr-x---  3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-x--- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-x---  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-x---  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
-rwxr-x---  1 darkdancer darkdancer 3871 2007-09-07 21:45 style.css*

/var/www/torrentflux2/themes/rust/images:
total 76
drwxr-x--- 2 darkdancer darkdancer  4096 2007-09-07 21:06 ./
drwxr-x--- 3 darkdancer darkdancer  4096 2007-09-07 21:06 ../
-rwxr-x--- 1 darkdancer darkdancer   956 2007-09-07 21:45 admin.gif*
-rwxr-x--- 1 darkdancer darkdancer 12948 2007-09-07 21:45 bar.gif*
-rwxr-x--- 1 darkdancer darkdancer   971 2007-09-07 21:45 directory.gif*
-rwxr-x--- 1 darkdancer darkdancer   969 2007-09-07 21:45 history.gif*
-rwxr-x--- 1 darkdancer darkdancer   961 2007-09-07 21:45 home.gif*
-rwxr-x--- 1 darkdancer darkdancer    13 2007-09-07 21:45 index.html*
-rwxr-x--- 1 darkdancer darkdancer   985 2007-09-07 21:45 messages_off.gif*
-rwxr-x--- 1 darkdancer darkdancer  2294 2007-09-07 21:45 messages_on.gif*
-rwxr-x--- 1 darkdancer darkdancer  1372 2007-09-07 21:45 noglass.gif*
-rwxr-x--- 1 darkdancer darkdancer   974 2007-09-07 21:45 profile.gif*
-rwxr-x--- 1 darkdancer darkdancer  8245 2007-09-07 21:45 proglass.gif*
-rwxr-x--- 1 darkdancer darkdancer   835 2007-09-07 21:45 progressbar.gif*

/var/www/torrentflux2/themes/slate:
total 20
drwxr-x---  3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-x--- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-x---  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-x---  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
-rwxr-x---  1 darkdancer darkdancer 3852 2007-09-07 21:45 style.css*

/var/www/torrentflux2/themes/slate/images:
total 60
drwxr-x--- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-x--- 3 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-x--- 1 darkdancer darkdancer  508 2007-09-07 21:45 admin.gif*
-rwxr-x--- 1 darkdancer darkdancer   69 2007-09-07 21:45 bar.gif*
-rwxr-x--- 1 darkdancer darkdancer  562 2007-09-07 21:45 directory.gif*
-rwxr-x--- 1 darkdancer darkdancer  533 2007-09-07 21:45 history.gif*
-rwxr-x--- 1 darkdancer darkdancer  511 2007-09-07 21:45 home.gif*
-rwxr-x--- 1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*
-rwxr-x--- 1 darkdancer darkdancer  588 2007-09-07 21:45 messages_off.gif*
-rwxr-x--- 1 darkdancer darkdancer 1812 2007-09-07 21:45 messages_on.gif*
-rwxr-x--- 1 darkdancer darkdancer  553 2007-09-07 21:45 noglass.gif*
-rwxr-x--- 1 darkdancer darkdancer  558 2007-09-07 21:45 profile.gif*
-rwxr-x--- 1 darkdancer darkdancer 5909 2007-09-07 21:45 proglass.gif*
-rwxr-x--- 1 darkdancer darkdancer  791 2007-09-07 21:45 progressbar.gif*

/var/www/torrentflux2/upgrades:
total 44
drwxr-x---  2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-x 12 darkdancer darkdancer 4096 2007-09-07 23:23 ../
-rwxr-x---  1 darkdancer darkdancer 2515 2007-09-07 21:45 upgrade11_12.php*
-rwxr-x---  1 darkdancer darkdancer 2065 2007-09-07 21:45 upgrade12_13.php*
-rwxr-x---  1 darkdancer darkdancer 1555 2007-09-07 21:45 upgrade13_14.php*
-rwxr-x---  1 darkdancer darkdancer 1561 2007-09-07 21:45 upgrade14_15.php*
-rwxr-x---  1 darkdancer darkdancer 1957 2007-09-07 21:45 upgrade15_20.php*
-rwxr-x---  1 darkdancer darkdancer 4664 2007-09-07 21:45 upgrade20_21.php*
-rwxr-x---  1 darkdancer darkdancer 2212 2007-09-07 21:45 upgrade21_22.php*
-rwxr-x---  1 darkdancer darkdancer 1595 2007-09-07 21:45 upgrade22_23.php*


Though that may not be all of it, it seems to extend off the top of my terminal.

---

### Post by kebes on 2007-09-08
> **DarkDancer said:**
> Ok, darkdancer@darkdancers:/var/www/torrentflux2$ sudo chmod +r -R yields:
Oops. I meant:
```

cd /var/www/torrentflux2/
sudo chmod +r -R *

```
(I forgot to put the * ... Time for bed I guess!)



> Though that may not be all of it, it seems to extend off the top of my terminal.
You can do something like:
```

cd /var/www/torrentflux2/
ls -laF -R > filelist.txt

```
This will make a file called "filelist.txt" that has the output of the "ls" command (so that it won't scroll off the top of your terminal window).


In any case, I can see that you need to run the command I mentioned above to give read permission to the webserver.

---

### Post by DarkDancer on 2007-09-08
Ok, that worked much better thanks... ;)

The error changed to:

> Warning: include(themes/matrix/index.php) [function.include]: failed to open stream: Permission denied in /var/www/torrentflux2/db.php on line 26

Warning: include() [function.include]: Failed opening 'themes/matrix/index.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/torrentflux2/db.php on line 26



TorrentFlux Database/SQL Error
Database error: Unknown database 'torrentflux'

Always check your database variables in the config.php file.


---

### Post by DarkDancer on 2007-09-08
Oh, and the filelist.txt:

> .:
total 648
drwxr-xr-x 12 darkdancer darkdancer  4096 2007-09-08 00:40 ./
drwxr-xr-x  3 root       root        4096 2007-09-07 21:04 ../
-rwxr-xr--  1 darkdancer darkdancer 90289 2007-09-07 21:45 admin.php*
drwxr-xr-- 11 darkdancer darkdancer  4096 2007-09-07 21:06 adodb/
-rwxr-xr--  1 darkdancer darkdancer  5471 2007-09-07 21:45 AliasFile.php*
-rwxr-xr--  1 darkdancer darkdancer  1958 2007-09-07 21:45 all_services.php*
-rwxr-xr--  1 darkdancer darkdancer  7199 2007-09-07 21:45 BDecode.php*
-rwxr-xr--  1 darkdancer darkdancer    70 2007-09-07 21:45 blank.html*
-rwxr-xr--  1 darkdancer darkdancer  6773 2007-09-07 21:45 CHANGELOG*
-rwxr-xr--  1 darkdancer darkdancer  3742 2007-09-07 23:23 config.php*
-rw-r--r--  1 darkdancer darkdancer  3736 2007-09-07 21:54 config.php~
-rwxr-xr--  1 darkdancer darkdancer  2623 2007-09-07 21:45 cookiehelp.php*
-rwxr-xr--  1 darkdancer darkdancer 15237 2007-09-07 21:45 copying*
-rwxr-xr--  1 darkdancer darkdancer  2958 2007-09-07 21:45 db.php*
-rwxr-xr--  1 darkdancer darkdancer  1808 2007-09-07 21:45 details.php*
-rwxr-xr--  1 darkdancer darkdancer 18689 2007-09-07 21:45 dir.php*
-rwxr-xr--  1 darkdancer darkdancer  6723 2007-09-07 21:45 downloaddetails.php*
drwxr-xr--  2 darkdancer darkdancer  4096 2007-09-07 21:06 downloads/
-rwxr-xr--  1 darkdancer darkdancer  1726 2007-09-07 21:45 drivespace.php*
-rwxr-xr--  1 darkdancer darkdancer   794 2007-09-07 21:45 dtree.css*
-rwxr-xr--  1 darkdancer darkdancer 13523 2007-09-07 21:45 dtree.js*
-rwxr-xr--  1 darkdancer darkdancer  2238 2007-09-07 21:45 favicon.ico*
-rw-r--r--  1 darkdancer darkdancer     0 2007-09-08 00:40 filelist.txt
-rwxr-xr--  1 darkdancer darkdancer 86831 2007-09-07 21:45 functions.php*
-rwxr-xr--  1 darkdancer darkdancer  5993 2007-09-07 21:45 history.php*
drwxr-xr--  9 darkdancer darkdancer  4096 2007-09-07 21:06 html/
drwxr-xr--  4 darkdancer darkdancer  4096 2007-09-07 21:06 images/
-rwxr-xr--  1 darkdancer darkdancer 34943 2007-09-07 21:45 index.php*
-rwxr-xr--  1 darkdancer darkdancer 10695 2007-09-07 21:45 install*
drwxr-xr--  2 darkdancer darkdancer  4096 2007-09-07 21:06 language/
-rwxr-xr--  1 darkdancer darkdancer  8440 2007-09-07 21:45 lastRSS.php*
-rwxr-xr--  1 darkdancer darkdancer 11652 2007-09-07 21:45 login.php*
-rwxr-xr--  1 darkdancer darkdancer  1625 2007-09-07 21:45 logout.php*
-rwxr-xr--  1 darkdancer darkdancer 25368 2007-09-07 21:45 maketorrent.php*
-rwxr-xr--  1 darkdancer darkdancer  3948 2007-09-07 21:45 message.php*
-rwxr-xr--  1 darkdancer darkdancer  8417 2007-09-07 21:45 metaInfo.php*
-rwxr-xr--  1 darkdancer darkdancer  5186 2007-09-07 21:45 multi.php*
-rwxr-xr--  1 darkdancer darkdancer 44818 2007-09-07 21:45 overlib.js*
-rwxr-xr--  1 darkdancer darkdancer 17756 2007-09-07 21:45 profile.php*
-rwxr-xr--  1 darkdancer darkdancer   822 2007-09-07 21:45 readme*
-rwxr-xr--  1 darkdancer darkdancer  6000 2007-09-07 21:45 readmsg.php*
-rwxr-xr--  1 darkdancer darkdancer  7649 2007-09-07 21:45 readrss.php*
-rwxr-xr--  1 darkdancer darkdancer  4773 2007-09-07 21:45 RunningTorrent.php*
drwxr-xr--  2 darkdancer darkdancer  4096 2007-09-07 21:06 searchEngines/
-rwxr-xr--  1 darkdancer darkdancer  3055 2007-09-07 21:45 setpriority.php*
-rwxr-xr--  1 darkdancer darkdancer  5672 2007-09-07 21:45 settingsfunctions.php*
drwxr-xr--  2 darkdancer darkdancer  4096 2007-09-07 21:06 sql/
-rwxr-xr--  1 darkdancer darkdancer  8939 2007-09-07 21:45 startpop.php*
drwxr-xr--  4 darkdancer darkdancer  4096 2007-09-07 21:06 TF_BitTornado/
drwxr-xr-- 17 darkdancer darkdancer  4096 2007-09-07 21:06 themes/
-rwxr-xr--  1 darkdancer darkdancer 17889 2007-09-07 21:45 tooltip.js*
-rwxr-xr--  1 darkdancer darkdancer  7465 2007-09-07 21:45 torrentSearch.php*
drwxr-xr--  2 darkdancer darkdancer  4096 2007-09-07 21:06 upgrades/
-rwxr-xr--  1 darkdancer darkdancer  2756 2007-09-07 21:45 viewnfo.php*
-rwxr-xr--  1 darkdancer darkdancer  1813 2007-09-07 21:45 who.php*

./adodb:
total 580
drwxr-xr-- 11 darkdancer darkdancer   4096 2007-09-07 21:06 ./
drwxr-xr-x 12 darkdancer darkdancer   4096 2007-09-08 00:40 ../
-rwxr-xr--  1 darkdancer darkdancer  12993 2007-09-07 21:45 adodb-active-record.inc.php*
-rwxr-xr--  1 darkdancer darkdancer   8615 2007-09-07 21:45 adodb-csvlib.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  21824 2007-09-07 21:45 adodb-datadict.inc.php*
-rwxr-xr--  1 darkdancer darkdancer   2827 2007-09-07 21:45 adodb-errorhandler.inc.php*
-rwxr-xr--  1 darkdancer darkdancer   8798 2007-09-07 21:45 adodb-error.inc.php*
-rwxr-xr--  1 darkdancer darkdancer   2362 2007-09-07 21:45 adodb-errorpear.inc.php*
-rwxr-xr--  1 darkdancer darkdancer   2295 2007-09-07 21:45 adodb-exceptions.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 118558 2007-09-07 21:45 adodb.inc.php*
-rwxr-xr--  1 darkdancer darkdancer   1680 2007-09-07 21:45 adodb-iterator.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  32748 2007-09-07 21:45 adodb-lib.inc.php*
-rwxr-xr--  1 darkdancer darkdancer   8406 2007-09-07 21:45 adodb-pager.inc.php*
-rwxr-xr--  1 darkdancer darkdancer   9935 2007-09-07 21:45 adodb-pear.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  31744 2007-09-07 21:45 adodb-perf.inc.php*
-rwxr-xr--  1 darkdancer darkdancer    334 2007-09-07 21:45 adodb-php4.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  40685 2007-09-07 21:45 adodb-time.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  64757 2007-09-07 21:45 adodb-xmlschema03.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  57552 2007-09-07 21:45 adodb-xmlschema.inc.php*
drwxr-xr--  2 darkdancer darkdancer   4096 2007-09-07 21:06 contrib/
drwxr-xr--  2 darkdancer darkdancer   4096 2007-09-07 21:06 datadict/
drwxr-xr--  2 darkdancer darkdancer   4096 2007-09-07 21:06 docs/
drwxr-xr--  2 darkdancer darkdancer   4096 2007-09-07 21:06 drivers/
-rwxr-xr--  1 darkdancer darkdancer     13 2007-09-07 21:45 index.html*
drwxr-xr--  2 darkdancer darkdancer   4096 2007-09-07 21:06 lang/
-rwxr-xr--  1 darkdancer darkdancer  26079 2007-09-07 21:45 license.txt*
drwxr-xr--  3 darkdancer darkdancer   4096 2007-09-07 21:06 pear/
drwxr-xr--  2 darkdancer darkdancer   4096 2007-09-07 21:06 perf/
-rwxr-xr--  1 darkdancer darkdancer   6493 2007-09-07 21:45 pivottable.inc.php*
-rwxr-xr--  1 darkdancer darkdancer   1731 2007-09-07 21:45 readme.txt*
-rwxr-xr--  1 darkdancer darkdancer   1574 2007-09-07 21:45 rsfilter.inc.php*
-rwxr-xr--  1 darkdancer darkdancer   2398 2007-09-07 21:45 server.php*
drwxr-xr--  3 darkdancer darkdancer   4096 2007-09-07 21:06 session/
-rwxr-xr--  1 darkdancer darkdancer   3473 2007-09-07 21:45 toexport.inc.php*
-rwxr-xr--  1 darkdancer darkdancer   5718 2007-09-07 21:45 tohtml.inc.php*
-rwxr-xr--  1 darkdancer darkdancer   1719 2007-09-07 21:45 xmlschema03.dtd*
-rwxr-xr--  1 darkdancer darkdancer   1491 2007-09-07 21:45 xmlschema.dtd*
drwxr-xr--  2 darkdancer darkdancer   4096 2007-09-07 21:06 xsl/

./adodb/contrib:
total 16
drwxr-xr--  2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 11 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr--  1 darkdancer darkdancer 6787 2007-09-07 21:45 toxmlrpc.inc.php*

./adodb/datadict:
total 84
drwxr-xr--  2 darkdancer darkdancer  4096 2007-09-07 21:06 ./
drwxr-xr-- 11 darkdancer darkdancer  4096 2007-09-07 21:06 ../
-rwxr-xr--  1 darkdancer darkdancer  2096 2007-09-07 21:45 datadict-access.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  4077 2007-09-07 21:45 datadict-db2.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  3961 2007-09-07 21:45 datadict-firebird.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  2638 2007-09-07 21:45 datadict-generic.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  1434 2007-09-07 21:45 datadict-ibase.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  1793 2007-09-07 21:45 datadict-informix.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  7673 2007-09-07 21:45 datadict-mssql.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  4845 2007-09-07 21:45 datadict-mysql.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  7502 2007-09-07 21:45 datadict-oci8.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 12431 2007-09-07 21:45 datadict-postgres.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  3292 2007-09-07 21:45 datadict-sapdb.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  6019 2007-09-07 21:45 datadict-sybase.inc.php*

./adodb/docs:
total 460
drwxr-xr--  2 darkdancer darkdancer   4096 2007-09-07 21:06 ./
drwxr-xr-- 11 darkdancer darkdancer   4096 2007-09-07 21:06 ../
-rwxr-xr--  1 darkdancer darkdancer  19499 2007-09-07 21:45 docs-active-record.htm*
-rwxr-xr--  1 darkdancer darkdancer 230072 2007-09-07 21:45 docs-adodb.htm*
-rwxr-xr--  1 darkdancer darkdancer  23274 2007-09-07 21:45 docs-datadict.htm*
-rwxr-xr--  1 darkdancer darkdancer  27344 2007-09-07 21:45 docs-oracle.htm*
-rwxr-xr--  1 darkdancer darkdancer  32515 2007-09-07 21:45 docs-perf.htm*
-rwxr-xr--  1 darkdancer darkdancer  13232 2007-09-07 21:45 docs-session.htm*
-rwxr-xr--  1 darkdancer darkdancer     13 2007-09-07 21:45 index.html*
-rwxr-xr--  1 darkdancer darkdancer  53084 2007-09-07 21:45 old-changelog.htm*
-rwxr-xr--  1 darkdancer darkdancer   3230 2007-09-07 21:45 readme.htm*
-rwxr-xr--  1 darkdancer darkdancer  20183 2007-09-07 21:45 tips_portable_sql.htm*
-rwxr-xr--  1 darkdancer darkdancer  16137 2007-09-07 21:45 tute.htm*

./adodb/drivers:
total 556
drwxr-xr--  2 darkdancer darkdancer  4096 2007-09-07 21:06 ./
drwxr-xr-- 11 darkdancer darkdancer  4096 2007-09-07 21:06 ../
-rwxr-xr--  1 darkdancer darkdancer  2240 2007-09-07 21:45 adodb-access.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 16270 2007-09-07 21:45 adodb-ado5.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  1478 2007-09-07 21:45 adodb-ado_access.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 16127 2007-09-07 21:45 adodb-ado.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  2820 2007-09-07 21:45 adodb-ado_mssql.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  2336 2007-09-07 21:45 adodb-borland_ibase.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  5066 2007-09-07 21:45 adodb-csv.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 18169 2007-09-07 21:45 adodb-db2.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  6775 2007-09-07 21:45 adodb-fbsql.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  1989 2007-09-07 21:45 adodb-firebird.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 25414 2007-09-07 21:45 adodb-ibase.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 13978 2007-09-07 21:45 adodb-informix72.inc.php*
-rwxr-xr--  1 darkdancer darkdancer   911 2007-09-07 21:45 adodb-informix.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 12387 2007-09-07 21:45 adodb-ldap.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 31111 2007-09-07 21:45 adodb-mssql.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  1586 2007-09-07 21:45 adodb-mssqlpo.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 26325 2007-09-07 21:45 adodb-mysqli.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 21251 2007-09-07 21:45 adodb-mysql.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  3357 2007-09-07 21:45 adodb-mysqlt.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  5327 2007-09-07 21:45 adodb-netezza.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  1636 2007-09-07 21:45 adodb-oci805.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 43981 2007-09-07 21:45 adodb-oci8.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  5716 2007-09-07 21:45 adodb-oci8po.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  9389 2007-09-07 21:45 adodb-odbc_db2.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 20244 2007-09-07 21:45 adodb-odbc.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  7726 2007-09-07 21:45 adodb-odbc_mssql.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  3298 2007-09-07 21:45 adodb-odbc_oracle.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 21408 2007-09-07 21:45 adodb-odbtp.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  1172 2007-09-07 21:45 adodb-odbtp_unicode.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  9303 2007-09-07 21:45 adodb-oracle.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 13841 2007-09-07 21:45 adodb-pdo.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  1054 2007-09-07 21:45 adodb-pdo_mssql.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  4230 2007-09-07 21:45 adodb-pdo_mysql.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  2709 2007-09-07 21:45 adodb-pdo_oci.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  8668 2007-09-07 21:45 adodb-pdo_pgsql.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 32261 2007-09-07 21:45 adodb-postgres64.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  7190 2007-09-07 21:45 adodb-postgres7.inc.php*
-rwxr-xr--  1 darkdancer darkdancer   362 2007-09-07 21:45 adodb-postgres8.inc.php*
-rwxr-xr--  1 darkdancer darkdancer   531 2007-09-07 21:45 adodb-postgres.inc.php*
-rwxr-xr--  1 darkdancer darkdancer   840 2007-09-07 21:45 adodb-proxy.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  5276 2007-09-07 21:45 adodb-sapdb.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  4402 2007-09-07 21:45 adodb-sqlanywhere.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 10829 2007-09-07 21:45 adodb-sqlite.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  1923 2007-09-07 21:45 adodb-sqlitepo.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  3321 2007-09-07 21:45 adodb-sybase_ase.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 12942 2007-09-07 21:45 adodb-sybase.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  2588 2007-09-07 21:45 adodb-vfp.inc.php*
-rwxr-xr--  1 darkdancer darkdancer    13 2007-09-07 21:45 index.html*

./adodb/lang:
total 92
drwxr-xr--  2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 11 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr--  1 darkdancer darkdancer 1541 2007-09-07 21:45 adodb-ar.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 2073 2007-09-07 21:45 adodb-bg.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 2507 2007-09-07 21:45 adodb-bgutf8.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 2027 2007-09-07 21:45 adodb-ca.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 1796 2007-09-07 21:45 adodb-cn.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 2099 2007-09-07 21:45 adodb-cz.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 1975 2007-09-07 21:45 adodb-da.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 2104 2007-09-07 21:45 adodb-de.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 1790 2007-09-07 21:45 adodb-en.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 1953 2007-09-07 21:45 adodb-es.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 1941 2007-09-07 21:45 adodb-esperanto.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 1751 2007-09-07 21:45 adodb-fr.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 1978 2007-09-07 21:45 adodb-hu.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 2026 2007-09-07 21:45 adodb-it.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 1926 2007-09-07 21:45 adodb-nl.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 1940 2007-09-07 21:45 adodb-pl.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 1970 2007-09-07 21:45 adodb-pt-br.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 1931 2007-09-07 21:45 adodb-ro.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 1988 2007-09-07 21:45 adodb-ru1251.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 1860 2007-09-07 21:45 adodb-sv.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 1938 2007-09-07 21:45 adodb-uk1251.inc.php*

./adodb/pear:
total 16
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 11 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 Auth/
-rwxr-xr--  1 darkdancer darkdancer  570 2007-09-07 21:45 readme.Auth.txt*

./adodb/pear/Auth:
total 12
drwxr-xr-- 3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 3 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-xr-- 2 darkdancer darkdancer 4096 2007-09-07 21:06 Container/

./adodb/pear/Auth/Container:
total 24
drwxr-xr-- 2 darkdancer darkdancer  4096 2007-09-07 21:06 ./
drwxr-xr-- 3 darkdancer darkdancer  4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer 12769 2007-09-07 21:45 ADOdb.php*

./adodb/perf:
total 64
drwxr-xr--  2 darkdancer darkdancer  4096 2007-09-07 21:06 ./
drwxr-xr-- 11 darkdancer darkdancer  4096 2007-09-07 21:06 ../
-rwxr-xr--  1 darkdancer darkdancer  3107 2007-09-07 21:45 perf-db2.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  2166 2007-09-07 21:45 perf-informix.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  4983 2007-09-07 21:45 perf-mssql.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  8742 2007-09-07 21:45 perf-mysql.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 16998 2007-09-07 21:45 perf-oci8.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  4733 2007-09-07 21:45 perf-postgres.inc.php*

./adodb/session:
total 92
drwxr-xr--  3 darkdancer darkdancer  4096 2007-09-07 21:06 ./
drwxr-xr-- 11 darkdancer darkdancer  4096 2007-09-07 21:06 ../
-rwxr-xr--  1 darkdancer darkdancer  2173 2007-09-07 21:45 adodb-compress-bzip2.php*
-rwxr-xr--  1 darkdancer darkdancer  1600 2007-09-07 21:45 adodb-compress-gzip.php*
-rwxr-xr--  1 darkdancer darkdancer   613 2007-09-07 21:45 adodb-cryptsession.php*
-rwxr-xr--  1 darkdancer darkdancer  1936 2007-09-07 21:45 adodb-encrypt-mcrypt.php*
-rwxr-xr--  1 darkdancer darkdancer   794 2007-09-07 21:45 adodb-encrypt-md5.php*
-rwxr-xr--  1 darkdancer darkdancer  1053 2007-09-07 21:45 adodb-encrypt-secret.php*
-rwxr-xr--  1 darkdancer darkdancer   407 2007-09-07 21:45 adodb-encrypt-sha1.php*
-rwxr-xr--  1 darkdancer darkdancer   537 2007-09-07 21:45 adodb-session-clob.php*
-rwxr-xr--  1 darkdancer darkdancer 21470 2007-09-07 21:45 adodb-session.php*
-rwxr-xr--  1 darkdancer darkdancer   412 2007-09-07 21:45 adodb-sessions.mysql.sql*
-rwxr-xr--  1 darkdancer darkdancer   296 2007-09-07 21:45 adodb-sessions.oracle.clob.sql*
-rwxr-xr--  1 darkdancer darkdancer   329 2007-09-07 21:45 adodb-sessions.oracle.sql*
-rwxr-xr--  1 darkdancer darkdancer  3913 2007-09-07 21:45 adodb-sess.txt*
-rwxr-xr--  1 darkdancer darkdancer  2974 2007-09-07 21:45 crypt.inc.php*
drwxr-xr--  2 darkdancer darkdancer  4096 2007-09-07 21:06 old/
-rwxr-xr--  1 darkdancer darkdancer   563 2007-09-07 21:45 session_schema.xml*

./adodb/session/old:
total 56
drwxr-xr-- 2 darkdancer darkdancer  4096 2007-09-07 21:06 ./
drwxr-xr-- 3 darkdancer darkdancer  4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer  9309 2007-09-07 21:45 adodb-cryptsession.php*
-rwxr-xr-- 1 darkdancer darkdancer 14664 2007-09-07 21:45 adodb-session-clob.php*
-rwxr-xr-- 1 darkdancer darkdancer 14006 2007-09-07 21:45 adodb-session.php*
-rwxr-xr-- 1 darkdancer darkdancer  1489 2007-09-07 21:45 crypt.inc.php*

./adodb/xsl:
total 48
drwxr-xr--  2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 11 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr--  1 darkdancer darkdancer 5802 2007-09-07 21:45 convert-0.1-0.2.xsl*
-rwxr-xr--  1 darkdancer darkdancer 6380 2007-09-07 21:45 convert-0.1-0.3.xsl*
-rwxr-xr--  1 darkdancer darkdancer 5865 2007-09-07 21:45 convert-0.2-0.1.xsl*
-rwxr-xr--  1 darkdancer darkdancer 7991 2007-09-07 21:45 convert-0.2-0.3.xsl*
-rwxr-xr--  1 darkdancer darkdancer 1532 2007-09-07 21:45 remove-0.2.xsl*
-rwxr-xr--  1 darkdancer darkdancer 1532 2007-09-07 21:45 remove-0.3.xsl*

./downloads:
total 12
drwxr-xr--  2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-x 12 darkdancer darkdancer 4096 2007-09-08 00:40 ../
-rwxr-xr--  1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*

./html:
total 592
drwxr-xr--  9 darkdancer darkdancer  4096 2007-09-07 21:06 ./
drwxr-xr-x 12 darkdancer darkdancer  4096 2007-09-08 00:40 ../
-rwxr-xr--  1 darkdancer darkdancer 90289 2007-09-07 21:45 admin.php*
drwxr-xr-- 11 darkdancer darkdancer  4096 2007-09-07 21:06 adodb/
-rwxr-xr--  1 darkdancer darkdancer  5471 2007-09-07 21:45 AliasFile.php*
-rwxr-xr--  1 darkdancer darkdancer  1958 2007-09-07 21:45 all_services.php*
-rwxr-xr--  1 darkdancer darkdancer  7199 2007-09-07 21:45 BDecode.php*
-rwxr-xr--  1 darkdancer darkdancer    70 2007-09-07 21:45 blank.html*
-rwxr-xr--  1 darkdancer darkdancer  3729 2007-09-07 21:45 config.php*
-rwxr-xr--  1 darkdancer darkdancer  2623 2007-09-07 21:45 cookiehelp.php*
-rwxr-xr--  1 darkdancer darkdancer  2958 2007-09-07 21:45 db.php*
-rwxr-xr--  1 darkdancer darkdancer  1808 2007-09-07 21:45 details.php*
-rwxr-xr--  1 darkdancer darkdancer 18689 2007-09-07 21:45 dir.php*
-rwxr-xr--  1 darkdancer darkdancer  6723 2007-09-07 21:45 downloaddetails.php*
drwxr-xr--  2 darkdancer darkdancer  4096 2007-09-07 21:06 downloads/
-rwxr-xr--  1 darkdancer darkdancer  1726 2007-09-07 21:45 drivespace.php*
-rwxr-xr--  1 darkdancer darkdancer   794 2007-09-07 21:45 dtree.css*
-rwxr-xr--  1 darkdancer darkdancer 13523 2007-09-07 21:45 dtree.js*
-rwxr-xr--  1 darkdancer darkdancer  2238 2007-09-07 21:45 favicon.ico*
-rwxr-xr--  1 darkdancer darkdancer 86831 2007-09-07 21:45 functions.php*
-rwxr-xr--  1 darkdancer darkdancer  5993 2007-09-07 21:45 history.php*
drwxr-xr--  4 darkdancer darkdancer  4096 2007-09-07 21:06 images/
-rwxr-xr--  1 darkdancer darkdancer 34943 2007-09-07 21:45 index.php*
drwxr-xr--  2 darkdancer darkdancer  4096 2007-09-07 21:06 language/
-rwxr-xr--  1 darkdancer darkdancer  8440 2007-09-07 21:45 lastRSS.php*
-rwxr-xr--  1 darkdancer darkdancer 11652 2007-09-07 21:45 login.php*
-rwxr-xr--  1 darkdancer darkdancer  1625 2007-09-07 21:45 logout.php*
-rwxr-xr--  1 darkdancer darkdancer 25368 2007-09-07 21:45 maketorrent.php*
-rwxr-xr--  1 darkdancer darkdancer  3948 2007-09-07 21:45 message.php*
-rwxr-xr--  1 darkdancer darkdancer  8417 2007-09-07 21:45 metaInfo.php*
-rwxr-xr--  1 darkdancer darkdancer  5186 2007-09-07 21:45 multi.php*
-rwxr-xr--  1 darkdancer darkdancer 44818 2007-09-07 21:45 overlib.js*
-rwxr-xr--  1 darkdancer darkdancer 17756 2007-09-07 21:45 profile.php*
-rwxr-xr--  1 darkdancer darkdancer  6000 2007-09-07 21:45 readmsg.php*
-rwxr-xr--  1 darkdancer darkdancer  7649 2007-09-07 21:45 readrss.php*
-rwxr-xr--  1 darkdancer darkdancer  4773 2007-09-07 21:45 RunningTorrent.php*
drwxr-xr--  2 darkdancer darkdancer  4096 2007-09-07 21:06 searchEngines/
-rwxr-xr--  1 darkdancer darkdancer  3055 2007-09-07 21:45 setpriority.php*
-rwxr-xr--  1 darkdancer darkdancer  5672 2007-09-07 21:45 settingsfunctions.php*
-rwxr-xr--  1 darkdancer darkdancer  8939 2007-09-07 21:45 startpop.php*
drwxr-xr--  4 darkdancer darkdancer  4096 2007-09-07 21:06 TF_BitTornado/
drwxr-xr-- 17 darkdancer darkdancer  4096 2007-09-07 21:06 themes/
-rwxr-xr--  1 darkdancer darkdancer 17889 2007-09-07 21:45 tooltip.js*
-rwxr-xr--  1 darkdancer darkdancer  7465 2007-09-07 21:45 torrentSearch.php*
-rwxr-xr--  1 darkdancer darkdancer  2756 2007-09-07 21:45 viewnfo.php*
-rwxr-xr--  1 darkdancer darkdancer  1813 2007-09-07 21:45 who.php*

./html/adodb:
total 580
drwxr-xr-- 11 darkdancer darkdancer   4096 2007-09-07 21:06 ./
drwxr-xr--  9 darkdancer darkdancer   4096 2007-09-07 21:06 ../
-rwxr-xr--  1 darkdancer darkdancer  12993 2007-09-07 21:45 adodb-active-record.inc.php*
-rwxr-xr--  1 darkdancer darkdancer   8615 2007-09-07 21:45 adodb-csvlib.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  21824 2007-09-07 21:45 adodb-datadict.inc.php*
-rwxr-xr--  1 darkdancer darkdancer   2827 2007-09-07 21:45 adodb-errorhandler.inc.php*
-rwxr-xr--  1 darkdancer darkdancer   8798 2007-09-07 21:45 adodb-error.inc.php*
-rwxr-xr--  1 darkdancer darkdancer   2362 2007-09-07 21:45 adodb-errorpear.inc.php*
-rwxr-xr--  1 darkdancer darkdancer   2295 2007-09-07 21:45 adodb-exceptions.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 118558 2007-09-07 21:45 adodb.inc.php*
-rwxr-xr--  1 darkdancer darkdancer   1680 2007-09-07 21:45 adodb-iterator.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  32748 2007-09-07 21:45 adodb-lib.inc.php*
-rwxr-xr--  1 darkdancer darkdancer   8406 2007-09-07 21:45 adodb-pager.inc.php*
-rwxr-xr--  1 darkdancer darkdancer   9935 2007-09-07 21:45 adodb-pear.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  31744 2007-09-07 21:45 adodb-perf.inc.php*
-rwxr-xr--  1 darkdancer darkdancer    334 2007-09-07 21:45 adodb-php4.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  40685 2007-09-07 21:45 adodb-time.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  64757 2007-09-07 21:45 adodb-xmlschema03.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  57552 2007-09-07 21:45 adodb-xmlschema.inc.php*
drwxr-xr--  2 darkdancer darkdancer   4096 2007-09-07 21:06 contrib/
drwxr-xr--  2 darkdancer darkdancer   4096 2007-09-07 21:06 datadict/
drwxr-xr--  2 darkdancer darkdancer   4096 2007-09-07 21:06 docs/
drwxr-xr--  2 darkdancer darkdancer   4096 2007-09-07 21:06 drivers/
-rwxr-xr--  1 darkdancer darkdancer     13 2007-09-07 21:45 index.html*
drwxr-xr--  2 darkdancer darkdancer   4096 2007-09-07 21:06 lang/
-rwxr-xr--  1 darkdancer darkdancer  26079 2007-09-07 21:45 license.txt*
drwxr-xr--  3 darkdancer darkdancer   4096 2007-09-07 21:06 pear/
drwxr-xr--  2 darkdancer darkdancer   4096 2007-09-07 21:06 perf/
-rwxr-xr--  1 darkdancer darkdancer   6493 2007-09-07 21:45 pivottable.inc.php*
-rwxr-xr--  1 darkdancer darkdancer   1731 2007-09-07 21:45 readme.txt*
-rwxr-xr--  1 darkdancer darkdancer   1574 2007-09-07 21:45 rsfilter.inc.php*
-rwxr-xr--  1 darkdancer darkdancer   2398 2007-09-07 21:45 server.php*
drwxr-xr--  3 darkdancer darkdancer   4096 2007-09-07 21:06 session/
-rwxr-xr--  1 darkdancer darkdancer   3473 2007-09-07 21:45 toexport.inc.php*
-rwxr-xr--  1 darkdancer darkdancer   5718 2007-09-07 21:45 tohtml.inc.php*
-rwxr-xr--  1 darkdancer darkdancer   1719 2007-09-07 21:45 xmlschema03.dtd*
-rwxr-xr--  1 darkdancer darkdancer   1491 2007-09-07 21:45 xmlschema.dtd*
drwxr-xr--  2 darkdancer darkdancer   4096 2007-09-07 21:06 xsl/

./html/adodb/contrib:
total 16
drwxr-xr--  2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 11 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr--  1 darkdancer darkdancer 6787 2007-09-07 21:45 toxmlrpc.inc.php*

./html/adodb/datadict:
total 84
drwxr-xr--  2 darkdancer darkdancer  4096 2007-09-07 21:06 ./
drwxr-xr-- 11 darkdancer darkdancer  4096 2007-09-07 21:06 ../
-rwxr-xr--  1 darkdancer darkdancer  2096 2007-09-07 21:45 datadict-access.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  4077 2007-09-07 21:45 datadict-db2.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  3961 2007-09-07 21:45 datadict-firebird.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  2638 2007-09-07 21:45 datadict-generic.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  1434 2007-09-07 21:45 datadict-ibase.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  1793 2007-09-07 21:45 datadict-informix.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  7673 2007-09-07 21:45 datadict-mssql.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  4845 2007-09-07 21:45 datadict-mysql.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  7502 2007-09-07 21:45 datadict-oci8.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 12431 2007-09-07 21:45 datadict-postgres.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  3292 2007-09-07 21:45 datadict-sapdb.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  6019 2007-09-07 21:45 datadict-sybase.inc.php*

./html/adodb/docs:
total 460
drwxr-xr--  2 darkdancer darkdancer   4096 2007-09-07 21:06 ./
drwxr-xr-- 11 darkdancer darkdancer   4096 2007-09-07 21:06 ../
-rwxr-xr--  1 darkdancer darkdancer  19499 2007-09-07 21:45 docs-active-record.htm*
-rwxr-xr--  1 darkdancer darkdancer 230072 2007-09-07 21:45 docs-adodb.htm*
-rwxr-xr--  1 darkdancer darkdancer  23274 2007-09-07 21:45 docs-datadict.htm*
-rwxr-xr--  1 darkdancer darkdancer  27344 2007-09-07 21:45 docs-oracle.htm*
-rwxr-xr--  1 darkdancer darkdancer  32515 2007-09-07 21:45 docs-perf.htm*
-rwxr-xr--  1 darkdancer darkdancer  13232 2007-09-07 21:45 docs-session.htm*
-rwxr-xr--  1 darkdancer darkdancer     13 2007-09-07 21:45 index.html*
-rwxr-xr--  1 darkdancer darkdancer  53084 2007-09-07 21:45 old-changelog.htm*
-rwxr-xr--  1 darkdancer darkdancer   3230 2007-09-07 21:45 readme.htm*
-rwxr-xr--  1 darkdancer darkdancer  20183 2007-09-07 21:45 tips_portable_sql.htm*
-rwxr-xr--  1 darkdancer darkdancer  16137 2007-09-07 21:45 tute.htm*

./html/adodb/drivers:
total 556
drwxr-xr--  2 darkdancer darkdancer  4096 2007-09-07 21:06 ./
drwxr-xr-- 11 darkdancer darkdancer  4096 2007-09-07 21:06 ../
-rwxr-xr--  1 darkdancer darkdancer  2240 2007-09-07 21:45 adodb-access.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 16270 2007-09-07 21:45 adodb-ado5.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  1478 2007-09-07 21:45 adodb-ado_access.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 16127 2007-09-07 21:45 adodb-ado.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  2820 2007-09-07 21:45 adodb-ado_mssql.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  2336 2007-09-07 21:45 adodb-borland_ibase.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  5066 2007-09-07 21:45 adodb-csv.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 18169 2007-09-07 21:45 adodb-db2.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  6775 2007-09-07 21:45 adodb-fbsql.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  1989 2007-09-07 21:45 adodb-firebird.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 25414 2007-09-07 21:45 adodb-ibase.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 13978 2007-09-07 21:45 adodb-informix72.inc.php*
-rwxr-xr--  1 darkdancer darkdancer   911 2007-09-07 21:45 adodb-informix.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 12387 2007-09-07 21:45 adodb-ldap.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 31111 2007-09-07 21:45 adodb-mssql.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  1586 2007-09-07 21:45 adodb-mssqlpo.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 26325 2007-09-07 21:45 adodb-mysqli.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 21251 2007-09-07 21:45 adodb-mysql.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  3357 2007-09-07 21:45 adodb-mysqlt.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  5327 2007-09-07 21:45 adodb-netezza.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  1636 2007-09-07 21:45 adodb-oci805.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 43981 2007-09-07 21:45 adodb-oci8.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  5716 2007-09-07 21:45 adodb-oci8po.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  9389 2007-09-07 21:45 adodb-odbc_db2.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 20244 2007-09-07 21:45 adodb-odbc.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  7726 2007-09-07 21:45 adodb-odbc_mssql.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  3298 2007-09-07 21:45 adodb-odbc_oracle.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 21408 2007-09-07 21:45 adodb-odbtp.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  1172 2007-09-07 21:45 adodb-odbtp_unicode.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  9303 2007-09-07 21:45 adodb-oracle.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 13841 2007-09-07 21:45 adodb-pdo.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  1054 2007-09-07 21:45 adodb-pdo_mssql.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  4230 2007-09-07 21:45 adodb-pdo_mysql.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  2709 2007-09-07 21:45 adodb-pdo_oci.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  8668 2007-09-07 21:45 adodb-pdo_pgsql.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 32261 2007-09-07 21:45 adodb-postgres64.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  7190 2007-09-07 21:45 adodb-postgres7.inc.php*
-rwxr-xr--  1 darkdancer darkdancer   362 2007-09-07 21:45 adodb-postgres8.inc.php*
-rwxr-xr--  1 darkdancer darkdancer   531 2007-09-07 21:45 adodb-postgres.inc.php*
-rwxr-xr--  1 darkdancer darkdancer   840 2007-09-07 21:45 adodb-proxy.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  5276 2007-09-07 21:45 adodb-sapdb.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  4402 2007-09-07 21:45 adodb-sqlanywhere.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 10829 2007-09-07 21:45 adodb-sqlite.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  1923 2007-09-07 21:45 adodb-sqlitepo.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  3321 2007-09-07 21:45 adodb-sybase_ase.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 12942 2007-09-07 21:45 adodb-sybase.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  2588 2007-09-07 21:45 adodb-vfp.inc.php*
-rwxr-xr--  1 darkdancer darkdancer    13 2007-09-07 21:45 index.html*

./html/adodb/lang:
total 92
drwxr-xr--  2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 11 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr--  1 darkdancer darkdancer 1541 2007-09-07 21:45 adodb-ar.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 2073 2007-09-07 21:45 adodb-bg.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 2507 2007-09-07 21:45 adodb-bgutf8.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 2027 2007-09-07 21:45 adodb-ca.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 1796 2007-09-07 21:45 adodb-cn.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 2099 2007-09-07 21:45 adodb-cz.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 1975 2007-09-07 21:45 adodb-da.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 2104 2007-09-07 21:45 adodb-de.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 1790 2007-09-07 21:45 adodb-en.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 1953 2007-09-07 21:45 adodb-es.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 1941 2007-09-07 21:45 adodb-esperanto.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 1751 2007-09-07 21:45 adodb-fr.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 1978 2007-09-07 21:45 adodb-hu.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 2026 2007-09-07 21:45 adodb-it.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 1926 2007-09-07 21:45 adodb-nl.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 1940 2007-09-07 21:45 adodb-pl.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 1970 2007-09-07 21:45 adodb-pt-br.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 1931 2007-09-07 21:45 adodb-ro.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 1988 2007-09-07 21:45 adodb-ru1251.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 1860 2007-09-07 21:45 adodb-sv.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 1938 2007-09-07 21:45 adodb-uk1251.inc.php*

./html/adodb/pear:
total 16
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 11 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 Auth/
-rwxr-xr--  1 darkdancer darkdancer  570 2007-09-07 21:45 readme.Auth.txt*

./html/adodb/pear/Auth:
total 12
drwxr-xr-- 3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 3 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-xr-- 2 darkdancer darkdancer 4096 2007-09-07 21:06 Container/

./html/adodb/pear/Auth/Container:
total 24
drwxr-xr-- 2 darkdancer darkdancer  4096 2007-09-07 21:06 ./
drwxr-xr-- 3 darkdancer darkdancer  4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer 12769 2007-09-07 21:45 ADOdb.php*

./html/adodb/perf:
total 64
drwxr-xr--  2 darkdancer darkdancer  4096 2007-09-07 21:06 ./
drwxr-xr-- 11 darkdancer darkdancer  4096 2007-09-07 21:06 ../
-rwxr-xr--  1 darkdancer darkdancer  3107 2007-09-07 21:45 perf-db2.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  2166 2007-09-07 21:45 perf-informix.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  4983 2007-09-07 21:45 perf-mssql.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  8742 2007-09-07 21:45 perf-mysql.inc.php*
-rwxr-xr--  1 darkdancer darkdancer 16998 2007-09-07 21:45 perf-oci8.inc.php*
-rwxr-xr--  1 darkdancer darkdancer  4733 2007-09-07 21:45 perf-postgres.inc.php*

./html/adodb/session:
total 92
drwxr-xr--  3 darkdancer darkdancer  4096 2007-09-07 21:06 ./
drwxr-xr-- 11 darkdancer darkdancer  4096 2007-09-07 21:06 ../
-rwxr-xr--  1 darkdancer darkdancer  2173 2007-09-07 21:45 adodb-compress-bzip2.php*
-rwxr-xr--  1 darkdancer darkdancer  1600 2007-09-07 21:45 adodb-compress-gzip.php*
-rwxr-xr--  1 darkdancer darkdancer   613 2007-09-07 21:45 adodb-cryptsession.php*
-rwxr-xr--  1 darkdancer darkdancer  1936 2007-09-07 21:45 adodb-encrypt-mcrypt.php*
-rwxr-xr--  1 darkdancer darkdancer   794 2007-09-07 21:45 adodb-encrypt-md5.php*
-rwxr-xr--  1 darkdancer darkdancer  1053 2007-09-07 21:45 adodb-encrypt-secret.php*
-rwxr-xr--  1 darkdancer darkdancer   407 2007-09-07 21:45 adodb-encrypt-sha1.php*
-rwxr-xr--  1 darkdancer darkdancer   537 2007-09-07 21:45 adodb-session-clob.php*
-rwxr-xr--  1 darkdancer darkdancer 21470 2007-09-07 21:45 adodb-session.php*
-rwxr-xr--  1 darkdancer darkdancer   412 2007-09-07 21:45 adodb-sessions.mysql.sql*
-rwxr-xr--  1 darkdancer darkdancer   296 2007-09-07 21:45 adodb-sessions.oracle.clob.sql*
-rwxr-xr--  1 darkdancer darkdancer   329 2007-09-07 21:45 adodb-sessions.oracle.sql*
-rwxr-xr--  1 darkdancer darkdancer  3913 2007-09-07 21:45 adodb-sess.txt*
-rwxr-xr--  1 darkdancer darkdancer  2974 2007-09-07 21:45 crypt.inc.php*
drwxr-xr--  2 darkdancer darkdancer  4096 2007-09-07 21:06 old/
-rwxr-xr--  1 darkdancer darkdancer   563 2007-09-07 21:45 session_schema.xml*

./html/adodb/session/old:
total 56
drwxr-xr-- 2 darkdancer darkdancer  4096 2007-09-07 21:06 ./
drwxr-xr-- 3 darkdancer darkdancer  4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer  9309 2007-09-07 21:45 adodb-cryptsession.php*
-rwxr-xr-- 1 darkdancer darkdancer 14664 2007-09-07 21:45 adodb-session-clob.php*
-rwxr-xr-- 1 darkdancer darkdancer 14006 2007-09-07 21:45 adodb-session.php*
-rwxr-xr-- 1 darkdancer darkdancer  1489 2007-09-07 21:45 crypt.inc.php*

./html/adodb/xsl:
total 48
drwxr-xr--  2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 11 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr--  1 darkdancer darkdancer 5802 2007-09-07 21:45 convert-0.1-0.2.xsl*
-rwxr-xr--  1 darkdancer darkdancer 6380 2007-09-07 21:45 convert-0.1-0.3.xsl*
-rwxr-xr--  1 darkdancer darkdancer 5865 2007-09-07 21:45 convert-0.2-0.1.xsl*
-rwxr-xr--  1 darkdancer darkdancer 7991 2007-09-07 21:45 convert-0.2-0.3.xsl*
-rwxr-xr--  1 darkdancer darkdancer 1532 2007-09-07 21:45 remove-0.2.xsl*
-rwxr-xr--  1 darkdancer darkdancer 1532 2007-09-07 21:45 remove-0.3.xsl*

./html/downloads:
total 12
drwxr-xr-- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 9 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*

./html/images:
total 244
drwxr-xr-- 4 darkdancer darkdancer  4096 2007-09-07 21:06 ./
drwxr-xr-- 9 darkdancer darkdancer  4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer   909 2007-09-07 21:45 admin_user.gif*
-rwxr-xr-- 1 darkdancer darkdancer   635 2007-09-07 21:45 all.gif*
-rwxr-xr-- 1 darkdancer darkdancer    62 2007-09-07 21:45 arrow.gif*
-rwxr-xr-- 1 darkdancer darkdancer   994 2007-09-07 21:45 black.gif*
-rwxr-xr-- 1 darkdancer darkdancer    43 2007-09-07 21:45 blank.gif*
-rwxr-xr-- 1 darkdancer darkdancer   939 2007-09-07 21:45 code_bg.jpg*
-rwxr-xr-- 1 darkdancer darkdancer   646 2007-09-07 21:45 delete_off.gif*
-rwxr-xr-- 1 darkdancer darkdancer   644 2007-09-07 21:45 delete_on.gif*
-rwxr-xr-- 1 darkdancer darkdancer   234 2007-09-07 21:45 delete.png*
-rwxr-xr-- 1 darkdancer darkdancer 12630 2007-09-07 21:45 delete.psd*
-rwxr-xr-- 1 darkdancer darkdancer  2954 2007-09-07 21:45 downarrow.png*
-rwxr-xr-- 1 darkdancer darkdancer    48 2007-09-07 21:45 down.gif*
-rwxr-xr-- 1 darkdancer darkdancer   577 2007-09-07 21:45 download.gif*
-rwxr-xr-- 1 darkdancer darkdancer   373 2007-09-07 21:45 download_owner.gif*
drwxr-xr-- 2 darkdancer darkdancer  4096 2007-09-07 21:06 dtree/
-rwxr-xr-- 1 darkdancer darkdancer   348 2007-09-07 21:45 edit.png*
-rwxr-xr-- 1 darkdancer darkdancer   643 2007-09-07 21:45 error.gif*
-rwxr-xr-- 1 darkdancer darkdancer  2238 2007-09-07 21:45 favicon.ico*
drwxr-xr-- 2 darkdancer darkdancer  4096 2007-09-07 21:06 files/
-rwxr-xr-- 1 darkdancer darkdancer   594 2007-09-07 21:45 folder2.gif*
-rwxr-xr-- 1 darkdancer darkdancer   639 2007-09-07 21:45 folder.gif*
-rwxr-xr-- 1 darkdancer darkdancer   533 2007-09-07 21:45 folder.png*
-rwxr-xr-- 1 darkdancer darkdancer  1035 2007-09-07 21:45 green.gif*
-rwxr-xr-- 1 darkdancer darkdancer   649 2007-09-07 21:45 hdd.gif*
-rwxr-xr-- 1 darkdancer darkdancer  1182 2007-09-07 21:45 help.gif*
-rwxr-xr-- 1 darkdancer darkdancer    13 2007-09-07 21:45 index.html*
-rwxr-xr-- 1 darkdancer darkdancer   947 2007-09-07 21:45 info.gif*
-rwxr-xr-- 1 darkdancer darkdancer   387 2007-09-07 21:45 kill.gif*
-rwxr-xr-- 1 darkdancer darkdancer   565 2007-09-07 21:45 locked.gif*
-rwxr-xr-- 1 darkdancer darkdancer   554 2007-09-07 21:45 logout.gif*
-rwxr-xr-- 1 darkdancer darkdancer   646 2007-09-07 21:45 make.gif*
-rwxr-xr-- 1 darkdancer darkdancer   115 2007-09-07 21:45 new_message.gif*
-rwxr-xr-- 1 darkdancer darkdancer   112 2007-09-07 21:45 old_message.gif*
-rwxr-xr-- 1 darkdancer darkdancer 20369 2007-09-07 21:45 progress_bar.gif*
-rwxr-xr-- 1 darkdancer darkdancer   279 2007-09-07 21:45 properties.png*
-rwxr-xr-- 1 darkdancer darkdancer   392 2007-09-07 21:45 queued.gif*
-rwxr-xr-- 1 darkdancer darkdancer  1038 2007-09-07 21:45 red.gif*
-rwxr-xr-- 1 darkdancer darkdancer   216 2007-09-07 21:45 reply.gif*
-rwxr-xr-- 1 darkdancer darkdancer   395 2007-09-07 21:45 run_off.gif*
-rwxr-xr-- 1 darkdancer darkdancer   604 2007-09-07 21:45 run_on.gif*
-rwxr-xr-- 1 darkdancer darkdancer  1000 2007-09-07 21:45 seed_on.gif*
-rwxr-xr-- 1 darkdancer darkdancer   909 2007-09-07 21:45 superadmin.gif*
-rwxr-xr-- 1 darkdancer darkdancer   649 2007-09-07 21:45 tar_down.gif*
-rwxr-xr-- 1 darkdancer darkdancer   609 2007-09-07 21:45 time.gif*
-rwxr-xr-- 1 darkdancer darkdancer  2941 2007-09-07 21:45 uparrow.png*
-rwxr-xr-- 1 darkdancer darkdancer   592 2007-09-07 21:45 up_dir.gif*
-rwxr-xr-- 1 darkdancer darkdancer   909 2007-09-07 21:45 user.gif*
-rwxr-xr-- 1 darkdancer darkdancer   996 2007-09-07 21:45 user_group.gif*
-rwxr-xr-- 1 darkdancer darkdancer   146 2007-09-07 21:45 user_offline.gif*
-rwxr-xr-- 1 darkdancer darkdancer   659 2007-09-07 21:45 view_nfo.gif*
-rwxr-xr-- 1 darkdancer darkdancer   682 2007-09-07 21:45 who.gif*
-rwxr-xr-- 1 darkdancer darkdancer  1037 2007-09-07 21:45 yellow.gif*

./html/images/dtree:
total 64
drwxr-xr-- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 4 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer 1040 2007-09-07 21:45 base.gif*
-rwxr-xr-- 1 darkdancer darkdancer   62 2007-09-07 21:45 empty.gif*
-rwxr-xr-- 1 darkdancer darkdancer  372 2007-09-07 21:45 folder.gif*
-rwxr-xr-- 1 darkdancer darkdancer  376 2007-09-07 21:45 folderopen.gif*
-rwxr-xr-- 1 darkdancer darkdancer   66 2007-09-07 21:45 joinbottom.gif*
-rwxr-xr-- 1 darkdancer darkdancer   69 2007-09-07 21:45 join.gif*
-rwxr-xr-- 1 darkdancer darkdancer   66 2007-09-07 21:45 line.gif*
-rwxr-xr-- 1 darkdancer darkdancer   85 2007-09-07 21:45 minusbottom.gif*
-rwxr-xr-- 1 darkdancer darkdancer   86 2007-09-07 21:45 minus.gif*
-rwxr-xr-- 1 darkdancer darkdancer  861 2007-09-07 21:45 nolines_minus.gif*
-rwxr-xr-- 1 darkdancer darkdancer  870 2007-09-07 21:45 nolines_plus.gif*
-rwxr-xr-- 1 darkdancer darkdancer  582 2007-09-07 21:45 page.gif*
-rwxr-xr-- 1 darkdancer darkdancer   88 2007-09-07 21:45 plusbottom.gif*
-rwxr-xr-- 1 darkdancer darkdancer   89 2007-09-07 21:45 plus.gif*

./html/images/files:
total 188
drwxr-xr-- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 4 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer 1054 2007-09-07 21:45 ac3.png*
-rwxr-xr-- 1 darkdancer darkdancer 1069 2007-09-07 21:45 avi.png*
-rwxr-xr-- 1 darkdancer darkdancer  839 2007-09-07 21:45 bin.png*
-rwxr-xr-- 1 darkdancer darkdancer 1086 2007-09-07 21:45 bmp.png*
-rwxr-xr-- 1 darkdancer darkdancer  753 2007-09-07 21:45 cab.png*
-rwxr-xr-- 1 darkdancer darkdancer  829 2007-09-07 21:45 c.png*
-rwxr-xr-- 1 darkdancer darkdancer 1046 2007-09-07 21:45 cue.png*
-rwxr-xr-- 1 darkdancer darkdancer  855 2007-09-07 21:45 doc.png*
-rwxr-xr-- 1 darkdancer darkdancer  711 2007-09-07 21:45 exe.png*
-rwxr-xr-- 1 darkdancer darkdancer  824 2007-09-07 21:45 gif.png*
-rwxr-xr-- 1 darkdancer darkdancer 1126 2007-09-07 21:45 gz.png*
-rwxr-xr-- 1 darkdancer darkdancer  829 2007-09-07 21:45 h.png*
-rwxr-xr-- 1 darkdancer darkdancer  951 2007-09-07 21:45 html.png*
-rwxr-xr-- 1 darkdancer darkdancer 1046 2007-09-07 21:45 img.png*
-rwxr-xr-- 1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*
-rwxr-xr-- 1 darkdancer darkdancer 1046 2007-09-07 21:45 iso.png*
-rwxr-xr-- 1 darkdancer darkdancer 1169 2007-09-07 21:45 jar.png*
-rwxr-xr-- 1 darkdancer darkdancer 1169 2007-09-07 21:45 java.png*
-rwxr-xr-- 1 darkdancer darkdancer  824 2007-09-07 21:45 jpg.png*
-rwxr-xr-- 1 darkdancer darkdancer  820 2007-09-07 21:45 log.png*
-rwxr-xr-- 1 darkdancer darkdancer  955 2007-09-07 21:45 man.png*
-rwxr-xr-- 1 darkdancer darkdancer  779 2007-09-07 21:45 midi.png*
-rwxr-xr-- 1 darkdancer darkdancer  931 2007-09-07 21:45 mov.png*
-rwxr-xr-- 1 darkdancer darkdancer  910 2007-09-07 21:45 mp3.png*
-rwxr-xr-- 1 darkdancer darkdancer  767 2007-09-07 21:45 mpeg.png*
-rwxr-xr-- 1 darkdancer darkdancer  767 2007-09-07 21:45 mpg.png*
-rwxr-xr-- 1 darkdancer darkdancer  956 2007-09-07 21:45 nfo.png*
-rwxr-xr-- 1 darkdancer darkdancer  910 2007-09-07 21:45 ogg.png*
-rwxr-xr-- 1 darkdancer darkdancer 1069 2007-09-07 21:45 ogm.png*
-rwxr-xr-- 1 darkdancer darkdancer  857 2007-09-07 21:45 pdf.png*
-rwxr-xr-- 1 darkdancer darkdancer  980 2007-09-07 21:45 php.png*
-rwxr-xr-- 1 darkdancer darkdancer  865 2007-09-07 21:45 py.png*
-rwxr-xr-- 1 darkdancer darkdancer  740 2007-09-07 21:45 rar.png*
-rwxr-xr-- 1 darkdancer darkdancer 2567 2007-09-07 21:45 readme.txt*
-rwxr-xr-- 1 darkdancer darkdancer  924 2007-09-07 21:45 rm.png*
-rwxr-xr-- 1 darkdancer darkdancer 1123 2007-09-07 21:45 rpm.png*
-rwxr-xr-- 1 darkdancer darkdancer  823 2007-09-07 21:45 sh.png*
-rwxr-xr-- 1 darkdancer darkdancer 1050 2007-09-07 21:45 tar.png*
-rwxr-xr-- 1 darkdancer darkdancer  643 2007-09-07 21:45 txt.png*
-rwxr-xr-- 1 darkdancer darkdancer  767 2007-09-07 21:45 vob.png*
-rwxr-xr-- 1 darkdancer darkdancer  910 2007-09-07 21:45 wav.png*
-rwxr-xr-- 1 darkdancer darkdancer  910 2007-09-07 21:45 wma.png*
-rwxr-xr-- 1 darkdancer darkdancer  767 2007-09-07 21:45 wmv.png*
-rwxr-xr-- 1 darkdancer darkdancer  990 2007-09-07 21:45 xls.png*
-rwxr-xr-- 1 darkdancer darkdancer  753 2007-09-07 21:45 zip.png*

./html/language:
total 184
drwxr-xr-- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 9 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer   13 2007-09-07 21:45 .htaccess*
-rwxr-xr-- 1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*
-rwxr-xr-- 1 darkdancer darkdancer 7282 2007-09-07 21:45 lang-chinese.php*
-rwxr-xr-- 1 darkdancer darkdancer 7696 2007-09-07 21:45 lang-dutch.php*
-rwxr-xr-- 1 darkdancer darkdancer 7264 2007-09-07 21:45 lang-english.php*
-rwxr-xr-- 1 darkdancer darkdancer 7980 2007-09-07 21:45 lang-estonian.php*
-rwxr-xr-- 1 darkdancer darkdancer 7464 2007-09-07 21:45 lang-finnish.php*
-rwxr-xr-- 1 darkdancer darkdancer 7840 2007-09-07 21:45 lang-french.php*
-rwxr-xr-- 1 darkdancer darkdancer 8524 2007-09-07 21:45 lang-galician.php*
-rwxr-xr-- 1 darkdancer darkdancer 7657 2007-09-07 21:45 lang-german.php*
-rwxr-xr-- 1 darkdancer darkdancer 7840 2007-09-07 21:45 lang-hungarian.php*
-rwxr-xr-- 1 darkdancer darkdancer 7527 2007-09-07 21:45 lang-italian.php*
-rwxr-xr-- 1 darkdancer darkdancer 7414 2007-09-07 21:45 lang-norwegian.php*
-rwxr-xr-- 1 darkdancer darkdancer 7531 2007-09-07 21:45 lang-polish.php*
-rwxr-xr-- 1 darkdancer darkdancer 8102 2007-09-07 21:45 lang-portuguese.php*
-rwxr-xr-- 1 darkdancer darkdancer 6503 2007-09-07 21:45 lang-redneck.php*
-rwxr-xr-- 1 darkdancer darkdancer 7608 2007-09-07 21:45 lang-russian.php*
-rwxr-xr-- 1 darkdancer darkdancer 6771 2007-09-07 21:45 lang-slovenian.php*
-rwxr-xr-- 1 darkdancer darkdancer 8844 2007-09-07 21:45 lang-spanish.php*
-rwxr-xr-- 1 darkdancer darkdancer 7598 2007-09-07 21:45 lang-svenska.php*
-rwxr-xr-- 1 darkdancer darkdancer 7268 2007-09-07 21:45 lang-taiwanese.php*
-rwxr-xr-- 1 darkdancer darkdancer 7531 2007-09-07 21:45 lang-turkish.php*

./html/searchEngines:
total 136
drwxr-xr-- 2 darkdancer darkdancer  4096 2007-09-07 21:06 ./
drwxr-xr-- 9 darkdancer darkdancer  4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer  9404 2007-09-07 21:45 GoogleEngine.php*
-rwxr-xr-- 1 darkdancer darkdancer  3381 2007-09-07 21:45 GoogleFunctions.php*
-rwxr-xr-- 1 darkdancer darkdancer 16188 2007-09-07 21:45 isoHuntEngine.php*
-rwxr-xr-- 1 darkdancer darkdancer 10846 2007-09-07 21:45 mininovaEngine.php*
-rwxr-xr-- 1 darkdancer darkdancer 17374 2007-09-07 21:45 PirateBayEngine.php*
-rwxr-xr-- 1 darkdancer darkdancer 10321 2007-09-07 21:45 SearchEngineBase.php*
-rwxr-xr-- 1 darkdancer darkdancer 13520 2007-09-07 21:45 TorrentBoxEngine.php*
-rwxr-xr-- 1 darkdancer darkdancer 15685 2007-09-07 21:45 TorrentPortalEngine.php*
-rwxr-xr-- 1 darkdancer darkdancer 20207 2007-09-07 21:45 TorrentSpyEngine.php*

./html/TF_BitTornado:
total 60
drwxr-xr-- 4 darkdancer darkdancer  4096 2007-09-07 21:06 ./
drwxr-xr-- 9 darkdancer darkdancer  4096 2007-09-07 21:06 ../
drwxr-xr-- 4 darkdancer darkdancer  4096 2007-09-07 21:06 BitTornado/
-rwxr-xr-- 1 darkdancer darkdancer  1169 2007-09-07 21:45 btmakemetafile.py*
-rwxr-xr-- 1 darkdancer darkdancer 15601 2007-09-07 21:45 btphptornado.py*
-rwxr-xr-- 1 darkdancer darkdancer  2570 2007-09-07 21:45 btshowmetainfo.py*
-rwxr-xr-- 1 darkdancer darkdancer    13 2007-09-07 21:45 index.html*
drwxr-xr-- 2 darkdancer darkdancer  4096 2007-09-07 21:06 original_src/
-rwxr-xr-- 1 darkdancer darkdancer 14767 2007-09-07 21:45 tfQManager.py*

./html/TF_BitTornado/BitTornado:
total 296
drwxr-xr-- 4 darkdancer darkdancer  4096 2007-09-07 21:06 ./
drwxr-xr-- 4 darkdancer darkdancer  4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer  7600 2007-09-07 21:45 bencode.py*
-rwxr-xr-- 1 darkdancer darkdancer  4058 2007-09-07 21:45 bitfield.py*
drwxr-xr-- 3 darkdancer darkdancer  4096 2007-09-07 21:06 bt1/
-rwxr-xr-- 1 darkdancer darkdancer   595 2007-09-07 21:45 clock.py*
-rwxr-xr-- 1 darkdancer darkdancer 10786 2007-09-07 21:45 ConfigDir.py*
-rwxr-xr-- 1 darkdancer darkdancer 51250 2007-09-07 21:45 ConfigReader.py*
-rwxr-xr-- 1 darkdancer darkdancer  1112 2007-09-07 21:45 ConnChoice.py*
-rwxr-xr-- 1 darkdancer darkdancer  5369 2007-09-07 21:45 CreateIcons.py*
-rwxr-xr-- 1 darkdancer darkdancer  1029 2007-09-07 21:45 CurrentRateMeasure.py*
drwxr-xr-- 2 darkdancer darkdancer  4096 2007-09-07 21:06 cvs/
-rwxr-xr-- 1 darkdancer darkdancer    27 2007-09-07 21:45 .cvsignore*
-rwxr-xr-- 1 darkdancer darkdancer 33558 2007-09-07 21:45 download_bt1.py*
-rwxr-xr-- 1 darkdancer darkdancer  5553 2007-09-07 21:45 HTTPHandler.py*
-rwxr-xr-- 1 darkdancer darkdancer  4464 2007-09-07 21:45 inifile.py*
-rwxr-xr-- 1 darkdancer darkdancer  1434 2007-09-07 21:45 __init__.py*
-rwxr-xr-- 1 darkdancer darkdancer  5161 2007-09-07 21:45 iprangeparse.py*
-rwxr-xr-- 1 darkdancer darkdancer 12499 2007-09-07 21:45 launchmanycore.py*
-rwxr-xr-- 1 darkdancer darkdancer  7675 2007-09-07 21:45 natpunch.py*
-rwxr-xr-- 1 darkdancer darkdancer  4230 2007-09-07 21:45 parseargs.py*
-rwxr-xr-- 1 darkdancer darkdancer  4854 2007-09-07 21:45 parsedir.py*
-rwxr-xr-- 1 darkdancer darkdancer  1878 2007-09-07 21:45 piecebuffer.py*
-rwxr-xr-- 1 darkdancer darkdancer    99 2007-09-07 21:45 PSYCO.py*
-rwxr-xr-- 1 darkdancer darkdancer  4728 2007-09-07 21:45 RateLimiter.py*
-rwxr-xr-- 1 darkdancer darkdancer  2002 2007-09-07 21:45 RateMeasure.py*
-rwxr-xr-- 1 darkdancer darkdancer  6532 2007-09-07 21:45 RawServer.py*
-rwxr-xr-- 1 darkdancer darkdancer  2337 2007-09-07 21:45 selectpoll.py*
-rwxr-xr-- 1 darkdancer darkdancer  5647 2007-09-07 21:45 ServerPortHandler.py*
-rwxr-xr-- 1 darkdancer darkdancer 12823 2007-09-07 21:45 SocketHandler.py*
-rwxr-xr-- 1 darkdancer darkdancer  5247 2007-09-07 21:45 subnetparse.py*
-rwxr-xr-- 1 darkdancer darkdancer   852 2007-09-07 21:45 torrentlistparse.py*
-rwxr-xr-- 1 darkdancer darkdancer  3167 2007-09-07 21:45 zurllib.py*

./html/TF_BitTornado/BitTornado/bt1:
total 300
drwxr-xr-- 3 darkdancer darkdancer  4096 2007-09-07 21:06 ./
drwxr-xr-- 4 darkdancer darkdancer  4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer  3827 2007-09-07 21:45 btformats.py*
-rwxr-xr-- 1 darkdancer darkdancer  4268 2007-09-07 21:45 Choker.py*
-rwxr-xr-- 1 darkdancer darkdancer  8847 2007-09-07 21:45 Connecter.py*
drwxr-xr-- 2 darkdancer darkdancer  4096 2007-09-07 21:06 cvs/
-rwxr-xr-- 1 darkdancer darkdancer    51 2007-09-07 21:45 .cvsignore*
-rwxr-xr-- 1 darkdancer darkdancer  5310 2007-09-07 21:45 DownloaderFeedback.py*
-rwxr-xr-- 1 darkdancer darkdancer 22608 2007-09-07 21:45 Downloader.py*
-rwxr-xr-- 1 darkdancer darkdancer 10227 2007-09-07 21:45 Encrypter.py*
-rwxr-xr-- 1 darkdancer darkdancer  2240 2007-09-07 21:45 fakeopen.py*
-rwxr-xr-- 1 darkdancer darkdancer  8479 2007-09-07 21:45 FileSelector.py*
-rwxr-xr-- 1 darkdancer darkdancer   298 2007-09-07 21:45 Filter.py*
-rwxr-xr-- 1 darkdancer darkdancer  8461 2007-09-07 21:45 HTTPDownloader.py*
-rwxr-xr-- 1 darkdancer darkdancer    13 2007-09-07 21:45 __init__.py*
-rwxr-xr-- 1 darkdancer darkdancer  9038 2007-09-07 21:45 makemetafile.py*
-rwxr-xr-- 1 darkdancer darkdancer  2731 2007-09-07 21:45 NatCheck.py*
-rwxr-xr-- 1 darkdancer darkdancer 11915 2007-09-07 21:45 PiecePicker.py*
-rwxr-xr-- 1 darkdancer darkdancer 14089 2007-09-07 21:45 Rerequester.py*
-rwxr-xr-- 1 darkdancer darkdancer  6581 2007-09-07 21:45 Statistics.py*
-rwxr-xr-- 1 darkdancer darkdancer 20368 2007-09-07 21:45 Storage.py*
-rwxr-xr-- 1 darkdancer darkdancer 37256 2007-09-07 21:45 StorageWrapper.py*
-rwxr-xr-- 1 darkdancer darkdancer  3757 2007-09-07 21:45 StreamCheck.py*
-rwxr-xr-- 1 darkdancer darkdancer  7244 2007-09-07 21:45 T2T.py*
-rwxr-xr-- 1 darkdancer darkdancer 46229 2007-09-07 21:45 track.py*
-rwxr-xr-- 1 darkdancer darkdancer  4789 2007-09-07 21:45 Uploader.py*

./html/TF_BitTornado/BitTornado/bt1/cvs:
total 32
drwxr-xr-- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 3 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer 1060 2007-09-07 21:45 Entries*
-rwxr-xr-- 1 darkdancer darkdancer  515 2007-09-07 21:45 Entries.Extra*
-rwxr-xr-- 1 darkdancer darkdancer  515 2007-09-07 21:45 Entries.Extra.Old*
-rwxr-xr-- 1 darkdancer darkdancer 1060 2007-09-07 21:45 Entries.Old*
-rwxr-xr-- 1 darkdancer darkdancer   26 2007-09-07 21:45 Repository*
-rwxr-xr-- 1 darkdancer darkdancer   40 2007-09-07 21:45 Root*

./html/TF_BitTornado/BitTornado/cvs:
total 36
drwxr-xr-- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 4 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer 1375 2007-09-07 21:45 Entries*
-rwxr-xr-- 1 darkdancer darkdancer  700 2007-09-07 21:45 Entries.Extra*
-rwxr-xr-- 1 darkdancer darkdancer  700 2007-09-07 21:45 Entries.Extra.Old*
-rwxr-xr-- 1 darkdancer darkdancer   12 2007-09-07 21:45 Entries.Log*
-rwxr-xr-- 1 darkdancer darkdancer 1375 2007-09-07 21:45 Entries.Old*
-rwxr-xr-- 1 darkdancer darkdancer   22 2007-09-07 21:45 Repository*
-rwxr-xr-- 1 darkdancer darkdancer   40 2007-09-07 21:45 Root*

./html/TF_BitTornado/original_src:
total 400
drwxr-xr-- 2 darkdancer darkdancer   4096 2007-09-07 21:06 ./
drwxr-xr-- 4 darkdancer darkdancer   4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer 189992 2007-09-07 21:45 BitTornado-0.3.15.tar.gz*
-rwxr-xr-- 1 darkdancer darkdancer 194718 2007-09-07 21:45 BitTornado-0.3.17.tar.gz*
-rwxr-xr-- 1 darkdancer darkdancer     13 2007-09-07 21:45 index.html*

./html/themes:
total 72
drwxr-xr-- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr--  9 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-xr--  4 darkdancer darkdancer 4096 2007-09-07 21:06 BlueFlux/
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 chrome/
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 command/
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 g4e/
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 glass/
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 glyphic/
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 hornet/
-rwxr-xr--  1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 mape/
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 matrix/
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 matrix_chinese/
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 midnight/
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 minimal/
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 mint/
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 rust/
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 slate/

./html/themes/BlueFlux:
total 28
drwxr-xr--  4 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-xr--  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-xr--  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
drwxr-xr--  2 darkdancer darkdancer 4096 2007-09-07 21:06 main-icons/
-rwxr-xr--  1 darkdancer darkdancer 1801 2007-09-07 21:45 readme.txt*
-rwxr-xr--  1 darkdancer darkdancer 3954 2007-09-07 21:45 style.css*

./html/themes/BlueFlux/images:
total 60
drwxr-xr-- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 4 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer   98 2007-09-07 21:45 admin.gif*
-rwxr-xr-- 1 darkdancer darkdancer   43 2007-09-07 21:45 bar.gif*
-rwxr-xr-- 1 darkdancer darkdancer  113 2007-09-07 21:45 directory.gif*
-rwxr-xr-- 1 darkdancer darkdancer  108 2007-09-07 21:45 history.gif*
-rwxr-xr-- 1 darkdancer darkdancer   94 2007-09-07 21:45 home.gif*
-rwxr-xr-- 1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*
-rwxr-xr-- 1 darkdancer darkdancer  112 2007-09-07 21:45 messages_off.gif*
-rwxr-xr-- 1 darkdancer darkdancer  541 2007-09-07 21:45 messages_on.gif*
-rwxr-xr-- 1 darkdancer darkdancer   77 2007-09-07 21:45 noglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer  105 2007-09-07 21:45 profile.gif*
-rwxr-xr-- 1 darkdancer darkdancer 4650 2007-09-07 21:45 proglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer   58 2007-09-07 21:45 progressbar.gif*

./html/themes/BlueFlux/main-icons:
total 88
drwxr-xr-- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 4 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer  318 2007-09-07 21:45 black.gif*
-rwxr-xr-- 1 darkdancer darkdancer  933 2007-09-07 21:45 compressed.gif*
-rwxr-xr-- 1 darkdancer darkdancer   95 2007-09-07 21:45 delete_off.gif*
-rwxr-xr-- 1 darkdancer darkdancer   95 2007-09-07 21:45 delete_on.gif*
-rwxr-xr-- 1 darkdancer darkdancer   92 2007-09-07 21:45 download.gif*
-rwxr-xr-- 1 darkdancer darkdancer   92 2007-09-07 21:45 download_on.gif*
-rwxr-xr-- 1 darkdancer darkdancer   92 2007-09-07 21:45 download_owner.gif*
-rwxr-xr-- 1 darkdancer darkdancer 3128 2007-09-07 21:45 favicon.ico*
-rwxr-xr-- 1 darkdancer darkdancer 1010 2007-09-07 21:45 folder.gif*
-rwxr-xr-- 1 darkdancer darkdancer  319 2007-09-07 21:45 green.gif*
-rwxr-xr-- 1 darkdancer darkdancer   91 2007-09-07 21:45 kill.gif*
-rwxr-xr-- 1 darkdancer darkdancer  988 2007-09-07 21:45 locked.gif*
-rwxr-xr-- 1 darkdancer darkdancer   80 2007-09-07 21:45 logout.gif*
-rwxr-xr-- 1 darkdancer darkdancer  318 2007-09-07 21:45 red.gif*
-rwxr-xr-- 1 darkdancer darkdancer   92 2007-09-07 21:45 run_on.gif*
-rwxr-xr-- 1 darkdancer darkdancer   91 2007-09-07 21:45 seed_on.gif*
-rwxr-xr-- 1 darkdancer darkdancer  960 2007-09-07 21:45 tar_down.gif*
-rwxr-xr-- 1 darkdancer darkdancer  210 2007-09-07 21:45 user.gif*
-rwxr-xr-- 1 darkdancer darkdancer  596 2007-09-07 21:45 user_group.gif*
-rwxr-xr-- 1 darkdancer darkdancer  318 2007-09-07 21:45 yellow.gif*

./html/themes/chrome:
total 20
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-xr--  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-xr--  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
-rwxr-xr--  1 darkdancer darkdancer 3871 2007-09-07 21:45 style.css*

./html/themes/chrome/images:
total 64
drwxr-xr-- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 3 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer  418 2007-09-07 21:45 admin.gif*
-rwxr-xr-- 1 darkdancer darkdancer 6795 2007-09-07 21:45 bar.gif*
-rwxr-xr-- 1 darkdancer darkdancer  480 2007-09-07 21:45 directory.gif*
-rwxr-xr-- 1 darkdancer darkdancer  450 2007-09-07 21:45 history.gif*
-rwxr-xr-- 1 darkdancer darkdancer  420 2007-09-07 21:45 home.gif*
-rwxr-xr-- 1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*
-rwxr-xr-- 1 darkdancer darkdancer  488 2007-09-07 21:45 messages_off.gif*
-rwxr-xr-- 1 darkdancer darkdancer 1357 2007-09-07 21:45 messages_on.gif*
-rwxr-xr-- 1 darkdancer darkdancer  623 2007-09-07 21:45 noglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer  474 2007-09-07 21:45 profile.gif*
-rwxr-xr-- 1 darkdancer darkdancer 2577 2007-09-07 21:45 proglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer  146 2007-09-07 21:45 progressbar.gif*
-rwxr-xr-- 1 darkdancer darkdancer  454 2007-09-07 21:45 torrents.gif*

./html/themes/command:
total 24
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-xr--  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-xr--  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
-rwxr-xr--  1 darkdancer darkdancer 4145 2007-09-07 21:45 style.css*

./html/themes/command/images:
total 60
drwxr-xr-- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 3 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer  418 2007-09-07 21:45 admin.gif*
-rwxr-xr-- 1 darkdancer darkdancer 2924 2007-09-07 21:45 bar.gif*
-rwxr-xr-- 1 darkdancer darkdancer  480 2007-09-07 21:45 directory.gif*
-rwxr-xr-- 1 darkdancer darkdancer  450 2007-09-07 21:45 history.gif*
-rwxr-xr-- 1 darkdancer darkdancer  420 2007-09-07 21:45 home.gif*
-rwxr-xr-- 1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*
-rwxr-xr-- 1 darkdancer darkdancer  488 2007-09-07 21:45 messages_off.gif*
-rwxr-xr-- 1 darkdancer darkdancer 1357 2007-09-07 21:45 messages_on.gif*
-rwxr-xr-- 1 darkdancer darkdancer  623 2007-09-07 21:45 noglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer  474 2007-09-07 21:45 profile.gif*
-rwxr-xr-- 1 darkdancer darkdancer 3449 2007-09-07 21:45 proglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer  146 2007-09-07 21:45 progressbar.gif*
-rwxr-xr-- 1 darkdancer darkdancer  454 2007-09-07 21:45 torrents.gif*

./html/themes/g4e:
total 24
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr--  1 darkdancer darkdancer 3128 2007-09-07 21:45 favicon.ico*
drwxr-xr--  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-xr--  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
-rwxr-xr--  1 darkdancer darkdancer 3971 2007-09-07 21:45 style.css*

./html/themes/g4e/images:
total 76
drwxr-xr-- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 3 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer  893 2007-09-07 21:45 admin.gif*
-rwxr-xr-- 1 darkdancer darkdancer 1684 2007-09-07 21:45 bar.gif*
-rwxr-xr-- 1 darkdancer darkdancer  913 2007-09-07 21:45 directory.gif*
-rwxr-xr-- 1 darkdancer darkdancer 5736 2007-09-07 21:45 gentoo2.jpg*
-rwxr-xr-- 1 darkdancer darkdancer 4324 2007-09-07 21:45 gentoo2.png*
-rwxr-xr-- 1 darkdancer darkdancer  322 2007-09-07 21:45 gentoo.jpg*
-rwxr-xr-- 1 darkdancer darkdancer  108 2007-09-07 21:45 history.gif*
-rwxr-xr-- 1 darkdancer darkdancer  888 2007-09-07 21:45 home.gif*
-rwxr-xr-- 1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*
-rwxr-xr-- 1 darkdancer darkdancer  112 2007-09-07 21:45 messages_off.gif*
-rwxr-xr-- 1 darkdancer darkdancer  112 2007-09-07 21:45 messages_on.gif*
-rwxr-xr-- 1 darkdancer darkdancer   77 2007-09-07 21:45 noglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer  901 2007-09-07 21:45 profile.gif*
-rwxr-xr-- 1 darkdancer darkdancer 2726 2007-09-07 21:45 proglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer 1224 2007-09-07 21:45 progressbar.gif*

./html/themes/glass:
total 20
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-xr--  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-xr--  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
-rwxr-xr--  1 darkdancer darkdancer 3852 2007-09-07 21:45 style.css*

./html/themes/glass/images:
total 56
drwxr-xr-- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 3 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer  508 2007-09-07 21:45 admin.gif*
-rwxr-xr-- 1 darkdancer darkdancer 3169 2007-09-07 21:45 bar.gif*
-rwxr-xr-- 1 darkdancer darkdancer  562 2007-09-07 21:45 directory.gif*
-rwxr-xr-- 1 darkdancer darkdancer  533 2007-09-07 21:45 history.gif*
-rwxr-xr-- 1 darkdancer darkdancer  511 2007-09-07 21:45 home.gif*
-rwxr-xr-- 1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*
-rwxr-xr-- 1 darkdancer darkdancer  588 2007-09-07 21:45 messages_off.gif*
-rwxr-xr-- 1 darkdancer darkdancer 1812 2007-09-07 21:45 messages_on.gif*
-rwxr-xr-- 1 darkdancer darkdancer  348 2007-09-07 21:45 noglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer  558 2007-09-07 21:45 profile.gif*
-rwxr-xr-- 1 darkdancer darkdancer 1760 2007-09-07 21:45 proglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer  319 2007-09-07 21:45 progressbar.gif*

./html/themes/glyphic:
total 20
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-xr--  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-xr--  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
-rwxr-xr--  1 darkdancer darkdancer 3854 2007-09-07 21:45 style.css*

./html/themes/glyphic/images:
total 64
drwxr-xr-- 2 darkdancer darkdancer  4096 2007-09-07 21:06 ./
drwxr-xr-- 3 darkdancer darkdancer  4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer   508 2007-09-07 21:45 admin.gif*
-rwxr-xr-- 1 darkdancer darkdancer 11035 2007-09-07 21:45 bar.gif*
-rwxr-xr-- 1 darkdancer darkdancer   562 2007-09-07 21:45 directory.gif*
-rwxr-xr-- 1 darkdancer darkdancer   533 2007-09-07 21:45 history.gif*
-rwxr-xr-- 1 darkdancer darkdancer   511 2007-09-07 21:45 home.gif*
-rwxr-xr-- 1 darkdancer darkdancer    13 2007-09-07 21:45 index.html*
-rwxr-xr-- 1 darkdancer darkdancer   588 2007-09-07 21:45 messages_off.gif*
-rwxr-xr-- 1 darkdancer darkdancer  1812 2007-09-07 21:45 messages_on.gif*
-rwxr-xr-- 1 darkdancer darkdancer   623 2007-09-07 21:45 noglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer   558 2007-09-07 21:45 profile.gif*
-rwxr-xr-- 1 darkdancer darkdancer  2577 2007-09-07 21:45 proglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer   146 2007-09-07 21:45 progressbar.gif*

./html/themes/hornet:
total 20
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-xr--  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-xr--  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
-rwxr-xr--  1 darkdancer darkdancer 3455 2007-09-07 21:45 style.css*

./html/themes/hornet/images:
total 60
drwxr-xr-- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 3 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer  424 2007-09-07 21:45 admin.gif*
-rwxr-xr-- 1 darkdancer darkdancer 1710 2007-09-07 21:45 bar.gif*
-rwxr-xr-- 1 darkdancer darkdancer  480 2007-09-07 21:45 directory.gif*
-rwxr-xr-- 1 darkdancer darkdancer  449 2007-09-07 21:45 history.gif*
-rwxr-xr-- 1 darkdancer darkdancer  420 2007-09-07 21:45 home.gif*
-rwxr-xr-- 1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*
-rwxr-xr-- 1 darkdancer darkdancer  489 2007-09-07 21:45 messages_off.gif*
-rwxr-xr-- 1 darkdancer darkdancer 1507 2007-09-07 21:45 messages_on.gif*
-rwxr-xr-- 1 darkdancer darkdancer  623 2007-09-07 21:45 noglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer  472 2007-09-07 21:45 profile.gif*
-rwxr-xr-- 1 darkdancer darkdancer 2569 2007-09-07 21:45 proglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer  138 2007-09-07 21:45 progressbar.gif*
-rwxr-xr-- 1 darkdancer darkdancer  454 2007-09-07 21:45 torrents.gif*

./html/themes/mape:
total 20
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-xr--  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-xr--  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
-rwxr-xr--  1 darkdancer darkdancer 3662 2007-09-07 21:45 style.css*

./html/themes/mape/images:
total 76
drwxr-xr-- 2 darkdancer darkdancer  4096 2007-09-07 21:06 ./
drwxr-xr-- 3 darkdancer darkdancer  4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer  1420 2007-09-07 21:45 admin.gif*
-rwxr-xr-- 1 darkdancer darkdancer  1081 2007-09-07 21:45 bar.gif*
-rwxr-xr-- 1 darkdancer darkdancer  1465 2007-09-07 21:45 directory.gif*
-rwxr-xr-- 1 darkdancer darkdancer  1432 2007-09-07 21:45 history.gif*
-rwxr-xr-- 1 darkdancer darkdancer  1425 2007-09-07 21:45 home.gif*
-rwxr-xr-- 1 darkdancer darkdancer    13 2007-09-07 21:45 index.html*
-rwxr-xr-- 1 darkdancer darkdancer  1465 2007-09-07 21:45 messages_off.gif*
-rwxr-xr-- 1 darkdancer darkdancer  1460 2007-09-07 21:45 messages_on.gif*
-rwxr-xr-- 1 darkdancer darkdancer    83 2007-09-07 21:45 noglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer  1472 2007-09-07 21:45 profile.gif*
-rwxr-xr-- 1 darkdancer darkdancer  1760 2007-09-07 21:45 proglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer   319 2007-09-07 21:45 progressbar.gif*
-rwxr-xr-- 1 darkdancer darkdancer 16896 2007-09-07 21:45 Thumbs.db*

./html/themes/matrix:
total 20
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-xr--  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-xr--  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
-rwxr-xr--  1 darkdancer darkdancer 3852 2007-09-07 21:45 style.css*

./html/themes/matrix/images:
total 56
drwxr-xr-- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 3 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer  418 2007-09-07 21:45 admin.gif*
-rwxr-xr-- 1 darkdancer darkdancer 1718 2007-09-07 21:45 bar.gif*
-rwxr-xr-- 1 darkdancer darkdancer  480 2007-09-07 21:45 directory.gif*
-rwxr-xr-- 1 darkdancer darkdancer  450 2007-09-07 21:45 history.gif*
-rwxr-xr-- 1 darkdancer darkdancer  420 2007-09-07 21:45 home.gif*
-rwxr-xr-- 1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*
-rwxr-xr-- 1 darkdancer darkdancer  488 2007-09-07 21:45 messages_off.gif*
-rwxr-xr-- 1 darkdancer darkdancer 1357 2007-09-07 21:45 messages_on.gif*
-rwxr-xr-- 1 darkdancer darkdancer  623 2007-09-07 21:45 noglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer  474 2007-09-07 21:45 profile.gif*
-rwxr-xr-- 1 darkdancer darkdancer 2577 2007-09-07 21:45 proglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer  146 2007-09-07 21:45 progressbar.gif*

./html/themes/matrix_chinese:
total 20
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-xr--  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-xr--  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
-rwxr-xr--  1 darkdancer darkdancer 3455 2007-09-07 21:45 style.css*

./html/themes/matrix_chinese/images:
total 56
drwxr-xr-- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 3 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer  287 2007-09-07 21:45 admin.gif*
-rwxr-xr-- 1 darkdancer darkdancer 1718 2007-09-07 21:45 bar.gif*
-rwxr-xr-- 1 darkdancer darkdancer  281 2007-09-07 21:45 directory.gif*
-rwxr-xr-- 1 darkdancer darkdancer  286 2007-09-07 21:45 history.gif*
-rwxr-xr-- 1 darkdancer darkdancer  283 2007-09-07 21:45 home.gif*
-rwxr-xr-- 1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*
-rwxr-xr-- 1 darkdancer darkdancer  283 2007-09-07 21:45 messages_off.gif*
-rwxr-xr-- 1 darkdancer darkdancer  283 2007-09-07 21:45 messages_on.gif*
-rwxr-xr-- 1 darkdancer darkdancer  623 2007-09-07 21:45 noglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer  309 2007-09-07 21:45 profile.gif*
-rwxr-xr-- 1 darkdancer darkdancer 2577 2007-09-07 21:45 proglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer  146 2007-09-07 21:45 progressbar.gif*

./html/themes/midnight:
total 20
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-xr--  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-xr--  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
-rwxr-xr--  1 darkdancer darkdancer 3940 2007-09-07 21:45 style.css*

./html/themes/midnight/images:
total 56
drwxr-xr-- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 3 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer  276 2007-09-07 21:45 admin.gif*
-rwxr-xr-- 1 darkdancer darkdancer  453 2007-09-07 21:45 bar.gif*
-rwxr-xr-- 1 darkdancer darkdancer  326 2007-09-07 21:45 directory.gif*
-rwxr-xr-- 1 darkdancer darkdancer  306 2007-09-07 21:45 history.gif*
-rwxr-xr-- 1 darkdancer darkdancer  259 2007-09-07 21:45 home.gif*
-rwxr-xr-- 1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*
-rwxr-xr-- 1 darkdancer darkdancer  344 2007-09-07 21:45 messages_off.gif*
-rwxr-xr-- 1 darkdancer darkdancer 1003 2007-09-07 21:45 messages_on.gif*
-rwxr-xr-- 1 darkdancer darkdancer   72 2007-09-07 21:45 noglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer  331 2007-09-07 21:45 profile.gif*
-rwxr-xr-- 1 darkdancer darkdancer 2132 2007-09-07 21:45 proglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer   58 2007-09-07 21:45 progressbar.gif*

./html/themes/minimal:
total 20
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-xr--  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-xr--  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
-rwxr-xr--  1 darkdancer darkdancer 3854 2007-09-07 21:45 style.css*

./html/themes/minimal/images:
total 56
drwxr-xr-- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 3 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer  508 2007-09-07 21:45 admin.gif*
-rwxr-xr-- 1 darkdancer darkdancer  799 2007-09-07 21:45 bar.gif*
-rwxr-xr-- 1 darkdancer darkdancer  562 2007-09-07 21:45 directory.gif*
-rwxr-xr-- 1 darkdancer darkdancer  533 2007-09-07 21:45 history.gif*
-rwxr-xr-- 1 darkdancer darkdancer  511 2007-09-07 21:45 home.gif*
-rwxr-xr-- 1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*
-rwxr-xr-- 1 darkdancer darkdancer  588 2007-09-07 21:45 messages_off.gif*
-rwxr-xr-- 1 darkdancer darkdancer 1812 2007-09-07 21:45 messages_on.gif*
-rwxr-xr-- 1 darkdancer darkdancer  809 2007-09-07 21:45 noglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer  558 2007-09-07 21:45 profile.gif*
-rwxr-xr-- 1 darkdancer darkdancer 3010 2007-09-07 21:45 proglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer  154 2007-09-07 21:45 progressbar.gif*

./html/themes/mint:
total 20
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-xr--  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-xr--  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
-rwxr-xr--  1 darkdancer darkdancer 3852 2007-09-07 21:45 style.css*

./html/themes/mint/images:
total 60
drwxr-xr-- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 3 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer  426 2007-09-07 21:45 admin.gif*
-rwxr-xr-- 1 darkdancer darkdancer 1710 2007-09-07 21:45 bar.gif*
-rwxr-xr-- 1 darkdancer darkdancer  482 2007-09-07 21:45 directory.gif*
-rwxr-xr-- 1 darkdancer darkdancer  450 2007-09-07 21:45 history.gif*
-rwxr-xr-- 1 darkdancer darkdancer  422 2007-09-07 21:45 home.gif*
-rwxr-xr-- 1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*
-rwxr-xr-- 1 darkdancer darkdancer  492 2007-09-07 21:45 messages_off.gif*
-rwxr-xr-- 1 darkdancer darkdancer 1616 2007-09-07 21:45 messages_on.gif*
-rwxr-xr-- 1 darkdancer darkdancer  623 2007-09-07 21:45 noglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer  477 2007-09-07 21:45 profile.gif*
-rwxr-xr-- 1 darkdancer darkdancer 2569 2007-09-07 21:45 proglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer  138 2007-09-07 21:45 progressbar.gif*
-rwxr-xr-- 1 darkdancer darkdancer  454 2007-09-07 21:45 torrents.gif*

./html/themes/rust:
total 20
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-xr--  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-xr--  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
-rwxr-xr--  1 darkdancer darkdancer 3871 2007-09-07 21:45 style.css*

./html/themes/rust/images:
total 76
drwxr-xr-- 2 darkdancer darkdancer  4096 2007-09-07 21:06 ./
drwxr-xr-- 3 darkdancer darkdancer  4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer   956 2007-09-07 21:45 admin.gif*
-rwxr-xr-- 1 darkdancer darkdancer 12948 2007-09-07 21:45 bar.gif*
-rwxr-xr-- 1 darkdancer darkdancer   971 2007-09-07 21:45 directory.gif*
-rwxr-xr-- 1 darkdancer darkdancer   969 2007-09-07 21:45 history.gif*
-rwxr-xr-- 1 darkdancer darkdancer   961 2007-09-07 21:45 home.gif*
-rwxr-xr-- 1 darkdancer darkdancer    13 2007-09-07 21:45 index.html*
-rwxr-xr-- 1 darkdancer darkdancer   985 2007-09-07 21:45 messages_off.gif*
-rwxr-xr-- 1 darkdancer darkdancer  2294 2007-09-07 21:45 messages_on.gif*
-rwxr-xr-- 1 darkdancer darkdancer  1372 2007-09-07 21:45 noglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer   974 2007-09-07 21:45 profile.gif*
-rwxr-xr-- 1 darkdancer darkdancer  8245 2007-09-07 21:45 proglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer   835 2007-09-07 21:45 progressbar.gif*

./html/themes/slate:
total 20
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-xr--  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-xr--  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
-rwxr-xr--  1 darkdancer darkdancer 3852 2007-09-07 21:45 style.css*

./html/themes/slate/images:
total 60
drwxr-xr-- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 3 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer  508 2007-09-07 21:45 admin.gif*
-rwxr-xr-- 1 darkdancer darkdancer   69 2007-09-07 21:45 bar.gif*
-rwxr-xr-- 1 darkdancer darkdancer  562 2007-09-07 21:45 directory.gif*
-rwxr-xr-- 1 darkdancer darkdancer  533 2007-09-07 21:45 history.gif*
-rwxr-xr-- 1 darkdancer darkdancer  511 2007-09-07 21:45 home.gif*
-rwxr-xr-- 1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*
-rwxr-xr-- 1 darkdancer darkdancer  588 2007-09-07 21:45 messages_off.gif*
-rwxr-xr-- 1 darkdancer darkdancer 1812 2007-09-07 21:45 messages_on.gif*
-rwxr-xr-- 1 darkdancer darkdancer  553 2007-09-07 21:45 noglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer  558 2007-09-07 21:45 profile.gif*
-rwxr-xr-- 1 darkdancer darkdancer 5909 2007-09-07 21:45 proglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer  791 2007-09-07 21:45 progressbar.gif*

./images:
total 244
drwxr-xr--  4 darkdancer darkdancer  4096 2007-09-07 21:06 ./
drwxr-xr-x 12 darkdancer darkdancer  4096 2007-09-08 00:40 ../
-rwxr-xr--  1 darkdancer darkdancer   909 2007-09-07 21:45 admin_user.gif*
-rwxr-xr--  1 darkdancer darkdancer   635 2007-09-07 21:45 all.gif*
-rwxr-xr--  1 darkdancer darkdancer    62 2007-09-07 21:45 arrow.gif*
-rwxr-xr--  1 darkdancer darkdancer   994 2007-09-07 21:45 black.gif*
-rwxr-xr--  1 darkdancer darkdancer    43 2007-09-07 21:45 blank.gif*
-rwxr-xr--  1 darkdancer darkdancer   939 2007-09-07 21:45 code_bg.jpg*
-rwxr-xr--  1 darkdancer darkdancer   646 2007-09-07 21:45 delete_off.gif*
-rwxr-xr--  1 darkdancer darkdancer   644 2007-09-07 21:45 delete_on.gif*
-rwxr-xr--  1 darkdancer darkdancer   234 2007-09-07 21:45 delete.png*
-rwxr-xr--  1 darkdancer darkdancer 12630 2007-09-07 21:45 delete.psd*
-rwxr-xr--  1 darkdancer darkdancer  2954 2007-09-07 21:45 downarrow.png*
-rwxr-xr--  1 darkdancer darkdancer    48 2007-09-07 21:45 down.gif*
-rwxr-xr--  1 darkdancer darkdancer   577 2007-09-07 21:45 download.gif*
-rwxr-xr--  1 darkdancer darkdancer   373 2007-09-07 21:45 download_owner.gif*
drwxr-xr--  2 darkdancer darkdancer  4096 2007-09-07 21:06 dtree/
-rwxr-xr--  1 darkdancer darkdancer   348 2007-09-07 21:45 edit.png*
-rwxr-xr--  1 darkdancer darkdancer   643 2007-09-07 21:45 error.gif*
-rwxr-xr--  1 darkdancer darkdancer  2238 2007-09-07 21:45 favicon.ico*
drwxr-xr--  2 darkdancer darkdancer  4096 2007-09-07 21:06 files/
-rwxr-xr--  1 darkdancer darkdancer   594 2007-09-07 21:45 folder2.gif*
-rwxr-xr--  1 darkdancer darkdancer   639 2007-09-07 21:45 folder.gif*
-rwxr-xr--  1 darkdancer darkdancer   533 2007-09-07 21:45 folder.png*
-rwxr-xr--  1 darkdancer darkdancer  1035 2007-09-07 21:45 green.gif*
-rwxr-xr--  1 darkdancer darkdancer   649 2007-09-07 21:45 hdd.gif*
-rwxr-xr--  1 darkdancer darkdancer  1182 2007-09-07 21:45 help.gif*
-rwxr-xr--  1 darkdancer darkdancer    13 2007-09-07 21:45 index.html*
-rwxr-xr--  1 darkdancer darkdancer   947 2007-09-07 21:45 info.gif*
-rwxr-xr--  1 darkdancer darkdancer   387 2007-09-07 21:45 kill.gif*
-rwxr-xr--  1 darkdancer darkdancer   565 2007-09-07 21:45 locked.gif*
-rwxr-xr--  1 darkdancer darkdancer   554 2007-09-07 21:45 logout.gif*
-rwxr-xr--  1 darkdancer darkdancer   646 2007-09-07 21:45 make.gif*
-rwxr-xr--  1 darkdancer darkdancer   115 2007-09-07 21:45 new_message.gif*
-rwxr-xr--  1 darkdancer darkdancer   112 2007-09-07 21:45 old_message.gif*
-rwxr-xr--  1 darkdancer darkdancer 20369 2007-09-07 21:45 progress_bar.gif*
-rwxr-xr--  1 darkdancer darkdancer   279 2007-09-07 21:45 properties.png*
-rwxr-xr--  1 darkdancer darkdancer   392 2007-09-07 21:45 queued.gif*
-rwxr-xr--  1 darkdancer darkdancer  1038 2007-09-07 21:45 red.gif*
-rwxr-xr--  1 darkdancer darkdancer   216 2007-09-07 21:45 reply.gif*
-rwxr-xr--  1 darkdancer darkdancer   395 2007-09-07 21:45 run_off.gif*
-rwxr-xr--  1 darkdancer darkdancer   604 2007-09-07 21:45 run_on.gif*
-rwxr-xr--  1 darkdancer darkdancer  1000 2007-09-07 21:45 seed_on.gif*
-rwxr-xr--  1 darkdancer darkdancer   909 2007-09-07 21:45 superadmin.gif*
-rwxr-xr--  1 darkdancer darkdancer   649 2007-09-07 21:45 tar_down.gif*
-rwxr-xr--  1 darkdancer darkdancer   609 2007-09-07 21:45 time.gif*
-rwxr-xr--  1 darkdancer darkdancer  2941 2007-09-07 21:45 uparrow.png*
-rwxr-xr--  1 darkdancer darkdancer   592 2007-09-07 21:45 up_dir.gif*
-rwxr-xr--  1 darkdancer darkdancer   909 2007-09-07 21:45 user.gif*
-rwxr-xr--  1 darkdancer darkdancer   996 2007-09-07 21:45 user_group.gif*
-rwxr-xr--  1 darkdancer darkdancer   146 2007-09-07 21:45 user_offline.gif*
-rwxr-xr--  1 darkdancer darkdancer   659 2007-09-07 21:45 view_nfo.gif*
-rwxr-xr--  1 darkdancer darkdancer   682 2007-09-07 21:45 who.gif*
-rwxr-xr--  1 darkdancer darkdancer  1037 2007-09-07 21:45 yellow.gif*

./images/dtree:
total 64
drwxr-xr-- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 4 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer 1040 2007-09-07 21:45 base.gif*
-rwxr-xr-- 1 darkdancer darkdancer   62 2007-09-07 21:45 empty.gif*
-rwxr-xr-- 1 darkdancer darkdancer  372 2007-09-07 21:45 folder.gif*
-rwxr-xr-- 1 darkdancer darkdancer  376 2007-09-07 21:45 folderopen.gif*
-rwxr-xr-- 1 darkdancer darkdancer   66 2007-09-07 21:45 joinbottom.gif*
-rwxr-xr-- 1 darkdancer darkdancer   69 2007-09-07 21:45 join.gif*
-rwxr-xr-- 1 darkdancer darkdancer   66 2007-09-07 21:45 line.gif*
-rwxr-xr-- 1 darkdancer darkdancer   85 2007-09-07 21:45 minusbottom.gif*
-rwxr-xr-- 1 darkdancer darkdancer   86 2007-09-07 21:45 minus.gif*
-rwxr-xr-- 1 darkdancer darkdancer  861 2007-09-07 21:45 nolines_minus.gif*
-rwxr-xr-- 1 darkdancer darkdancer  870 2007-09-07 21:45 nolines_plus.gif*
-rwxr-xr-- 1 darkdancer darkdancer  582 2007-09-07 21:45 page.gif*
-rwxr-xr-- 1 darkdancer darkdancer   88 2007-09-07 21:45 plusbottom.gif*
-rwxr-xr-- 1 darkdancer darkdancer   89 2007-09-07 21:45 plus.gif*

./images/files:
total 188
drwxr-xr-- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 4 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer 1054 2007-09-07 21:45 ac3.png*
-rwxr-xr-- 1 darkdancer darkdancer 1069 2007-09-07 21:45 avi.png*
-rwxr-xr-- 1 darkdancer darkdancer  839 2007-09-07 21:45 bin.png*
-rwxr-xr-- 1 darkdancer darkdancer 1086 2007-09-07 21:45 bmp.png*
-rwxr-xr-- 1 darkdancer darkdancer  753 2007-09-07 21:45 cab.png*
-rwxr-xr-- 1 darkdancer darkdancer  829 2007-09-07 21:45 c.png*
-rwxr-xr-- 1 darkdancer darkdancer 1046 2007-09-07 21:45 cue.png*
-rwxr-xr-- 1 darkdancer darkdancer  855 2007-09-07 21:45 doc.png*
-rwxr-xr-- 1 darkdancer darkdancer  711 2007-09-07 21:45 exe.png*
-rwxr-xr-- 1 darkdancer darkdancer  824 2007-09-07 21:45 gif.png*
-rwxr-xr-- 1 darkdancer darkdancer 1126 2007-09-07 21:45 gz.png*
-rwxr-xr-- 1 darkdancer darkdancer  829 2007-09-07 21:45 h.png*
-rwxr-xr-- 1 darkdancer darkdancer  951 2007-09-07 21:45 html.png*
-rwxr-xr-- 1 darkdancer darkdancer 1046 2007-09-07 21:45 img.png*
-rwxr-xr-- 1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*
-rwxr-xr-- 1 darkdancer darkdancer 1046 2007-09-07 21:45 iso.png*
-rwxr-xr-- 1 darkdancer darkdancer 1169 2007-09-07 21:45 jar.png*
-rwxr-xr-- 1 darkdancer darkdancer 1169 2007-09-07 21:45 java.png*
-rwxr-xr-- 1 darkdancer darkdancer  824 2007-09-07 21:45 jpg.png*
-rwxr-xr-- 1 darkdancer darkdancer  820 2007-09-07 21:45 log.png*
-rwxr-xr-- 1 darkdancer darkdancer  955 2007-09-07 21:45 man.png*
-rwxr-xr-- 1 darkdancer darkdancer  779 2007-09-07 21:45 midi.png*
-rwxr-xr-- 1 darkdancer darkdancer  931 2007-09-07 21:45 mov.png*
-rwxr-xr-- 1 darkdancer darkdancer  910 2007-09-07 21:45 mp3.png*
-rwxr-xr-- 1 darkdancer darkdancer  767 2007-09-07 21:45 mpeg.png*
-rwxr-xr-- 1 darkdancer darkdancer  767 2007-09-07 21:45 mpg.png*
-rwxr-xr-- 1 darkdancer darkdancer  956 2007-09-07 21:45 nfo.png*
-rwxr-xr-- 1 darkdancer darkdancer  910 2007-09-07 21:45 ogg.png*
-rwxr-xr-- 1 darkdancer darkdancer 1069 2007-09-07 21:45 ogm.png*
-rwxr-xr-- 1 darkdancer darkdancer  857 2007-09-07 21:45 pdf.png*
-rwxr-xr-- 1 darkdancer darkdancer  980 2007-09-07 21:45 php.png*
-rwxr-xr-- 1 darkdancer darkdancer  865 2007-09-07 21:45 py.png*
-rwxr-xr-- 1 darkdancer darkdancer  740 2007-09-07 21:45 rar.png*
-rwxr-xr-- 1 darkdancer darkdancer 2567 2007-09-07 21:45 readme.txt*
-rwxr-xr-- 1 darkdancer darkdancer  924 2007-09-07 21:45 rm.png*
-rwxr-xr-- 1 darkdancer darkdancer 1123 2007-09-07 21:45 rpm.png*
-rwxr-xr-- 1 darkdancer darkdancer  823 2007-09-07 21:45 sh.png*
-rwxr-xr-- 1 darkdancer darkdancer 1050 2007-09-07 21:45 tar.png*
-rwxr-xr-- 1 darkdancer darkdancer  643 2007-09-07 21:45 txt.png*
-rwxr-xr-- 1 darkdancer darkdancer  767 2007-09-07 21:45 vob.png*
-rwxr-xr-- 1 darkdancer darkdancer  910 2007-09-07 21:45 wav.png*
-rwxr-xr-- 1 darkdancer darkdancer  910 2007-09-07 21:45 wma.png*
-rwxr-xr-- 1 darkdancer darkdancer  767 2007-09-07 21:45 wmv.png*
-rwxr-xr-- 1 darkdancer darkdancer  990 2007-09-07 21:45 xls.png*
-rwxr-xr-- 1 darkdancer darkdancer  753 2007-09-07 21:45 zip.png*

./language:
total 184
drwxr-xr--  2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-x 12 darkdancer darkdancer 4096 2007-09-08 00:40 ../
-rwxr-xr--  1 darkdancer darkdancer   13 2007-09-07 21:45 .htaccess*
-rwxr-xr--  1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*
-rwxr-xr--  1 darkdancer darkdancer 7282 2007-09-07 21:45 lang-chinese.php*
-rwxr-xr--  1 darkdancer darkdancer 7696 2007-09-07 21:45 lang-dutch.php*
-rwxr-xr--  1 darkdancer darkdancer 7264 2007-09-07 21:45 lang-english.php*
-rwxr-xr--  1 darkdancer darkdancer 7980 2007-09-07 21:45 lang-estonian.php*
-rwxr-xr--  1 darkdancer darkdancer 7464 2007-09-07 21:45 lang-finnish.php*
-rwxr-xr--  1 darkdancer darkdancer 7840 2007-09-07 21:45 lang-french.php*
-rwxr-xr--  1 darkdancer darkdancer 8524 2007-09-07 21:45 lang-galician.php*
-rwxr-xr--  1 darkdancer darkdancer 7657 2007-09-07 21:45 lang-german.php*
-rwxr-xr--  1 darkdancer darkdancer 7840 2007-09-07 21:45 lang-hungarian.php*
-rwxr-xr--  1 darkdancer darkdancer 7527 2007-09-07 21:45 lang-italian.php*
-rwxr-xr--  1 darkdancer darkdancer 7414 2007-09-07 21:45 lang-norwegian.php*
-rwxr-xr--  1 darkdancer darkdancer 7531 2007-09-07 21:45 lang-polish.php*
-rwxr-xr--  1 darkdancer darkdancer 8102 2007-09-07 21:45 lang-portuguese.php*
-rwxr-xr--  1 darkdancer darkdancer 6503 2007-09-07 21:45 lang-redneck.php*
-rwxr-xr--  1 darkdancer darkdancer 7608 2007-09-07 21:45 lang-russian.php*
-rwxr-xr--  1 darkdancer darkdancer 6771 2007-09-07 21:45 lang-slovenian.php*
-rwxr-xr--  1 darkdancer darkdancer 8844 2007-09-07 21:45 lang-spanish.php*
-rwxr-xr--  1 darkdancer darkdancer 7598 2007-09-07 21:45 lang-svenska.php*
-rwxr-xr--  1 darkdancer darkdancer 7268 2007-09-07 21:45 lang-taiwanese.php*
-rwxr-xr--  1 darkdancer darkdancer 7531 2007-09-07 21:45 lang-turkish.php*

./searchEngines:
total 136
drwxr-xr--  2 darkdancer darkdancer  4096 2007-09-07 21:06 ./
drwxr-xr-x 12 darkdancer darkdancer  4096 2007-09-08 00:40 ../
-rwxr-xr--  1 darkdancer darkdancer  9404 2007-09-07 21:45 GoogleEngine.php*
-rwxr-xr--  1 darkdancer darkdancer  3381 2007-09-07 21:45 GoogleFunctions.php*
-rwxr-xr--  1 darkdancer darkdancer 16188 2007-09-07 21:45 isoHuntEngine.php*
-rwxr-xr--  1 darkdancer darkdancer 10846 2007-09-07 21:45 mininovaEngine.php*
-rwxr-xr--  1 darkdancer darkdancer 17374 2007-09-07 21:45 PirateBayEngine.php*
-rwxr-xr--  1 darkdancer darkdancer 10321 2007-09-07 21:45 SearchEngineBase.php*
-rwxr-xr--  1 darkdancer darkdancer 13520 2007-09-07 21:45 TorrentBoxEngine.php*
-rwxr-xr--  1 darkdancer darkdancer 15685 2007-09-07 21:45 TorrentPortalEngine.php*
-rwxr-xr--  1 darkdancer darkdancer 20207 2007-09-07 21:45 TorrentSpyEngine.php*

./sql:
total 28
drwxr-xr--  2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-x 12 darkdancer darkdancer 4096 2007-09-08 00:40 ../
-rwxr-xr--  1 darkdancer darkdancer 6092 2007-09-07 21:45 mysql_torrentflux.sql*
-rwxr-xr--  1 darkdancer darkdancer  290 2007-09-07 21:45 pgsql_01_create_db_and_user.sql*
-rwxr-xr--  1 darkdancer darkdancer 5507 2007-09-07 21:45 pgsql_02_create_tables.sql*

./TF_BitTornado:
total 60
drwxr-xr--  4 darkdancer darkdancer  4096 2007-09-07 21:06 ./
drwxr-xr-x 12 darkdancer darkdancer  4096 2007-09-08 00:40 ../
drwxr-xr--  4 darkdancer darkdancer  4096 2007-09-07 21:06 BitTornado/
-rwxr-xr--  1 darkdancer darkdancer  1169 2007-09-07 21:45 btmakemetafile.py*
-rwxr-xr--  1 darkdancer darkdancer 15601 2007-09-07 21:45 btphptornado.py*
-rwxr-xr--  1 darkdancer darkdancer  2570 2007-09-07 21:45 btshowmetainfo.py*
-rwxr-xr--  1 darkdancer darkdancer    13 2007-09-07 21:45 index.html*
drwxr-xr--  2 darkdancer darkdancer  4096 2007-09-07 21:06 original_src/
-rwxr-xr--  1 darkdancer darkdancer 14767 2007-09-07 21:45 tfQManager.py*

./TF_BitTornado/BitTornado:
total 296
drwxr-xr-- 4 darkdancer darkdancer  4096 2007-09-07 21:06 ./
drwxr-xr-- 4 darkdancer darkdancer  4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer  7600 2007-09-07 21:45 bencode.py*
-rwxr-xr-- 1 darkdancer darkdancer  4058 2007-09-07 21:45 bitfield.py*
drwxr-xr-- 3 darkdancer darkdancer  4096 2007-09-07 21:06 bt1/
-rwxr-xr-- 1 darkdancer darkdancer   595 2007-09-07 21:45 clock.py*
-rwxr-xr-- 1 darkdancer darkdancer 10786 2007-09-07 21:45 ConfigDir.py*
-rwxr-xr-- 1 darkdancer darkdancer 51250 2007-09-07 21:45 ConfigReader.py*
-rwxr-xr-- 1 darkdancer darkdancer  1112 2007-09-07 21:45 ConnChoice.py*
-rwxr-xr-- 1 darkdancer darkdancer  5369 2007-09-07 21:45 CreateIcons.py*
-rwxr-xr-- 1 darkdancer darkdancer  1029 2007-09-07 21:45 CurrentRateMeasure.py*
drwxr-xr-- 2 darkdancer darkdancer  4096 2007-09-07 21:06 cvs/
-rwxr-xr-- 1 darkdancer darkdancer    27 2007-09-07 21:45 .cvsignore*
-rwxr-xr-- 1 darkdancer darkdancer 33558 2007-09-07 21:45 download_bt1.py*
-rwxr-xr-- 1 darkdancer darkdancer  5553 2007-09-07 21:45 HTTPHandler.py*
-rwxr-xr-- 1 darkdancer darkdancer  4464 2007-09-07 21:45 inifile.py*
-rwxr-xr-- 1 darkdancer darkdancer  1434 2007-09-07 21:45 __init__.py*
-rwxr-xr-- 1 darkdancer darkdancer  5161 2007-09-07 21:45 iprangeparse.py*
-rwxr-xr-- 1 darkdancer darkdancer 12499 2007-09-07 21:45 launchmanycore.py*
-rwxr-xr-- 1 darkdancer darkdancer  7675 2007-09-07 21:45 natpunch.py*
-rwxr-xr-- 1 darkdancer darkdancer  4230 2007-09-07 21:45 parseargs.py*
-rwxr-xr-- 1 darkdancer darkdancer  4854 2007-09-07 21:45 parsedir.py*
-rwxr-xr-- 1 darkdancer darkdancer  1878 2007-09-07 21:45 piecebuffer.py*
-rwxr-xr-- 1 darkdancer darkdancer    99 2007-09-07 21:45 PSYCO.py*
-rwxr-xr-- 1 darkdancer darkdancer  4728 2007-09-07 21:45 RateLimiter.py*
-rwxr-xr-- 1 darkdancer darkdancer  2002 2007-09-07 21:45 RateMeasure.py*
-rwxr-xr-- 1 darkdancer darkdancer  6532 2007-09-07 21:45 RawServer.py*
-rwxr-xr-- 1 darkdancer darkdancer  2337 2007-09-07 21:45 selectpoll.py*
-rwxr-xr-- 1 darkdancer darkdancer  5647 2007-09-07 21:45 ServerPortHandler.py*
-rwxr-xr-- 1 darkdancer darkdancer 12823 2007-09-07 21:45 SocketHandler.py*
-rwxr-xr-- 1 darkdancer darkdancer  5247 2007-09-07 21:45 subnetparse.py*
-rwxr-xr-- 1 darkdancer darkdancer   852 2007-09-07 21:45 torrentlistparse.py*
-rwxr-xr-- 1 darkdancer darkdancer  3167 2007-09-07 21:45 zurllib.py*

./TF_BitTornado/BitTornado/bt1:
total 300
drwxr-xr-- 3 darkdancer darkdancer  4096 2007-09-07 21:06 ./
drwxr-xr-- 4 darkdancer darkdancer  4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer  3827 2007-09-07 21:45 btformats.py*
-rwxr-xr-- 1 darkdancer darkdancer  4268 2007-09-07 21:45 Choker.py*
-rwxr-xr-- 1 darkdancer darkdancer  8847 2007-09-07 21:45 Connecter.py*
drwxr-xr-- 2 darkdancer darkdancer  4096 2007-09-07 21:06 cvs/
-rwxr-xr-- 1 darkdancer darkdancer    51 2007-09-07 21:45 .cvsignore*
-rwxr-xr-- 1 darkdancer darkdancer  5310 2007-09-07 21:45 DownloaderFeedback.py*
-rwxr-xr-- 1 darkdancer darkdancer 22608 2007-09-07 21:45 Downloader.py*
-rwxr-xr-- 1 darkdancer darkdancer 10227 2007-09-07 21:45 Encrypter.py*
-rwxr-xr-- 1 darkdancer darkdancer  2240 2007-09-07 21:45 fakeopen.py*
-rwxr-xr-- 1 darkdancer darkdancer  8479 2007-09-07 21:45 FileSelector.py*
-rwxr-xr-- 1 darkdancer darkdancer   298 2007-09-07 21:45 Filter.py*
-rwxr-xr-- 1 darkdancer darkdancer  8461 2007-09-07 21:45 HTTPDownloader.py*
-rwxr-xr-- 1 darkdancer darkdancer    13 2007-09-07 21:45 __init__.py*
-rwxr-xr-- 1 darkdancer darkdancer  9038 2007-09-07 21:45 makemetafile.py*
-rwxr-xr-- 1 darkdancer darkdancer  2731 2007-09-07 21:45 NatCheck.py*
-rwxr-xr-- 1 darkdancer darkdancer 11915 2007-09-07 21:45 PiecePicker.py*
-rwxr-xr-- 1 darkdancer darkdancer 14089 2007-09-07 21:45 Rerequester.py*
-rwxr-xr-- 1 darkdancer darkdancer  6581 2007-09-07 21:45 Statistics.py*
-rwxr-xr-- 1 darkdancer darkdancer 20368 2007-09-07 21:45 Storage.py*
-rwxr-xr-- 1 darkdancer darkdancer 37256 2007-09-07 21:45 StorageWrapper.py*
-rwxr-xr-- 1 darkdancer darkdancer  3757 2007-09-07 21:45 StreamCheck.py*
-rwxr-xr-- 1 darkdancer darkdancer  7244 2007-09-07 21:45 T2T.py*
-rwxr-xr-- 1 darkdancer darkdancer 46229 2007-09-07 21:45 track.py*
-rwxr-xr-- 1 darkdancer darkdancer  4789 2007-09-07 21:45 Uploader.py*

./TF_BitTornado/BitTornado/bt1/cvs:
total 32
drwxr-xr-- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 3 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer 1060 2007-09-07 21:45 Entries*
-rwxr-xr-- 1 darkdancer darkdancer  515 2007-09-07 21:45 Entries.Extra*
-rwxr-xr-- 1 darkdancer darkdancer  515 2007-09-07 21:45 Entries.Extra.Old*
-rwxr-xr-- 1 darkdancer darkdancer 1060 2007-09-07 21:45 Entries.Old*
-rwxr-xr-- 1 darkdancer darkdancer   26 2007-09-07 21:45 Repository*
-rwxr-xr-- 1 darkdancer darkdancer   40 2007-09-07 21:45 Root*

./TF_BitTornado/BitTornado/cvs:
total 36
drwxr-xr-- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 4 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer 1375 2007-09-07 21:45 Entries*
-rwxr-xr-- 1 darkdancer darkdancer  700 2007-09-07 21:45 Entries.Extra*
-rwxr-xr-- 1 darkdancer darkdancer  700 2007-09-07 21:45 Entries.Extra.Old*
-rwxr-xr-- 1 darkdancer darkdancer   12 2007-09-07 21:45 Entries.Log*
-rwxr-xr-- 1 darkdancer darkdancer 1375 2007-09-07 21:45 Entries.Old*
-rwxr-xr-- 1 darkdancer darkdancer   22 2007-09-07 21:45 Repository*
-rwxr-xr-- 1 darkdancer darkdancer   40 2007-09-07 21:45 Root*

./TF_BitTornado/original_src:
total 400
drwxr-xr-- 2 darkdancer darkdancer   4096 2007-09-07 21:06 ./
drwxr-xr-- 4 darkdancer darkdancer   4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer 189992 2007-09-07 21:45 BitTornado-0.3.15.tar.gz*
-rwxr-xr-- 1 darkdancer darkdancer 194718 2007-09-07 21:45 BitTornado-0.3.17.tar.gz*
-rwxr-xr-- 1 darkdancer darkdancer     13 2007-09-07 21:45 index.html*

./themes:
total 72
drwxr-xr-- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-x 12 darkdancer darkdancer 4096 2007-09-08 00:40 ../
drwxr-xr--  4 darkdancer darkdancer 4096 2007-09-07 21:06 BlueFlux/
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 chrome/
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 command/
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 g4e/
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 glass/
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 glyphic/
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 hornet/
-rwxr-xr--  1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 mape/
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 matrix/
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 matrix_chinese/
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 midnight/
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 minimal/
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 mint/
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 rust/
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 slate/

./themes/BlueFlux:
total 28
drwxr-xr--  4 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-xr--  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-xr--  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
drwxr-xr--  2 darkdancer darkdancer 4096 2007-09-07 21:06 main-icons/
-rwxr-xr--  1 darkdancer darkdancer 1801 2007-09-07 21:45 readme.txt*
-rwxr-xr--  1 darkdancer darkdancer 3954 2007-09-07 21:45 style.css*

./themes/BlueFlux/images:
total 60
drwxr-xr-- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 4 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer   98 2007-09-07 21:45 admin.gif*
-rwxr-xr-- 1 darkdancer darkdancer   43 2007-09-07 21:45 bar.gif*
-rwxr-xr-- 1 darkdancer darkdancer  113 2007-09-07 21:45 directory.gif*
-rwxr-xr-- 1 darkdancer darkdancer  108 2007-09-07 21:45 history.gif*
-rwxr-xr-- 1 darkdancer darkdancer   94 2007-09-07 21:45 home.gif*
-rwxr-xr-- 1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*
-rwxr-xr-- 1 darkdancer darkdancer  112 2007-09-07 21:45 messages_off.gif*
-rwxr-xr-- 1 darkdancer darkdancer  541 2007-09-07 21:45 messages_on.gif*
-rwxr-xr-- 1 darkdancer darkdancer   77 2007-09-07 21:45 noglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer  105 2007-09-07 21:45 profile.gif*
-rwxr-xr-- 1 darkdancer darkdancer 4650 2007-09-07 21:45 proglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer   58 2007-09-07 21:45 progressbar.gif*

./themes/BlueFlux/main-icons:
total 88
drwxr-xr-- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 4 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer  318 2007-09-07 21:45 black.gif*
-rwxr-xr-- 1 darkdancer darkdancer  933 2007-09-07 21:45 compressed.gif*
-rwxr-xr-- 1 darkdancer darkdancer   95 2007-09-07 21:45 delete_off.gif*
-rwxr-xr-- 1 darkdancer darkdancer   95 2007-09-07 21:45 delete_on.gif*
-rwxr-xr-- 1 darkdancer darkdancer   92 2007-09-07 21:45 download.gif*
-rwxr-xr-- 1 darkdancer darkdancer   92 2007-09-07 21:45 download_on.gif*
-rwxr-xr-- 1 darkdancer darkdancer   92 2007-09-07 21:45 download_owner.gif*
-rwxr-xr-- 1 darkdancer darkdancer 3128 2007-09-07 21:45 favicon.ico*
-rwxr-xr-- 1 darkdancer darkdancer 1010 2007-09-07 21:45 folder.gif*
-rwxr-xr-- 1 darkdancer darkdancer  319 2007-09-07 21:45 green.gif*
-rwxr-xr-- 1 darkdancer darkdancer   91 2007-09-07 21:45 kill.gif*
-rwxr-xr-- 1 darkdancer darkdancer  988 2007-09-07 21:45 locked.gif*
-rwxr-xr-- 1 darkdancer darkdancer   80 2007-09-07 21:45 logout.gif*
-rwxr-xr-- 1 darkdancer darkdancer  318 2007-09-07 21:45 red.gif*
-rwxr-xr-- 1 darkdancer darkdancer   92 2007-09-07 21:45 run_on.gif*
-rwxr-xr-- 1 darkdancer darkdancer   91 2007-09-07 21:45 seed_on.gif*
-rwxr-xr-- 1 darkdancer darkdancer  960 2007-09-07 21:45 tar_down.gif*
-rwxr-xr-- 1 darkdancer darkdancer  210 2007-09-07 21:45 user.gif*
-rwxr-xr-- 1 darkdancer darkdancer  596 2007-09-07 21:45 user_group.gif*
-rwxr-xr-- 1 darkdancer darkdancer  318 2007-09-07 21:45 yellow.gif*

./themes/chrome:
total 20
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-xr--  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-xr--  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
-rwxr-xr--  1 darkdancer darkdancer 3871 2007-09-07 21:45 style.css*

./themes/chrome/images:
total 64
drwxr-xr-- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 3 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer  418 2007-09-07 21:45 admin.gif*
-rwxr-xr-- 1 darkdancer darkdancer 6795 2007-09-07 21:45 bar.gif*
-rwxr-xr-- 1 darkdancer darkdancer  480 2007-09-07 21:45 directory.gif*
-rwxr-xr-- 1 darkdancer darkdancer  450 2007-09-07 21:45 history.gif*
-rwxr-xr-- 1 darkdancer darkdancer  420 2007-09-07 21:45 home.gif*
-rwxr-xr-- 1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*
-rwxr-xr-- 1 darkdancer darkdancer  488 2007-09-07 21:45 messages_off.gif*
-rwxr-xr-- 1 darkdancer darkdancer 1357 2007-09-07 21:45 messages_on.gif*
-rwxr-xr-- 1 darkdancer darkdancer  623 2007-09-07 21:45 noglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer  474 2007-09-07 21:45 profile.gif*
-rwxr-xr-- 1 darkdancer darkdancer 2577 2007-09-07 21:45 proglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer  146 2007-09-07 21:45 progressbar.gif*
-rwxr-xr-- 1 darkdancer darkdancer  454 2007-09-07 21:45 torrents.gif*

./themes/command:
total 24
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-xr--  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-xr--  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
-rwxr-xr--  1 darkdancer darkdancer 4145 2007-09-07 21:45 style.css*

./themes/command/images:
total 60
drwxr-xr-- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 3 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer  418 2007-09-07 21:45 admin.gif*
-rwxr-xr-- 1 darkdancer darkdancer 2924 2007-09-07 21:45 bar.gif*
-rwxr-xr-- 1 darkdancer darkdancer  480 2007-09-07 21:45 directory.gif*
-rwxr-xr-- 1 darkdancer darkdancer  450 2007-09-07 21:45 history.gif*
-rwxr-xr-- 1 darkdancer darkdancer  420 2007-09-07 21:45 home.gif*
-rwxr-xr-- 1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*
-rwxr-xr-- 1 darkdancer darkdancer  488 2007-09-07 21:45 messages_off.gif*
-rwxr-xr-- 1 darkdancer darkdancer 1357 2007-09-07 21:45 messages_on.gif*
-rwxr-xr-- 1 darkdancer darkdancer  623 2007-09-07 21:45 noglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer  474 2007-09-07 21:45 profile.gif*
-rwxr-xr-- 1 darkdancer darkdancer 3449 2007-09-07 21:45 proglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer  146 2007-09-07 21:45 progressbar.gif*
-rwxr-xr-- 1 darkdancer darkdancer  454 2007-09-07 21:45 torrents.gif*

./themes/g4e:
total 24
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr--  1 darkdancer darkdancer 3128 2007-09-07 21:45 favicon.ico*
drwxr-xr--  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-xr--  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
-rwxr-xr--  1 darkdancer darkdancer 3971 2007-09-07 21:45 style.css*

./themes/g4e/images:
total 76
drwxr-xr-- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 3 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer  893 2007-09-07 21:45 admin.gif*
-rwxr-xr-- 1 darkdancer darkdancer 1684 2007-09-07 21:45 bar.gif*
-rwxr-xr-- 1 darkdancer darkdancer  913 2007-09-07 21:45 directory.gif*
-rwxr-xr-- 1 darkdancer darkdancer 5736 2007-09-07 21:45 gentoo2.jpg*
-rwxr-xr-- 1 darkdancer darkdancer 4324 2007-09-07 21:45 gentoo2.png*
-rwxr-xr-- 1 darkdancer darkdancer  322 2007-09-07 21:45 gentoo.jpg*
-rwxr-xr-- 1 darkdancer darkdancer  108 2007-09-07 21:45 history.gif*
-rwxr-xr-- 1 darkdancer darkdancer  888 2007-09-07 21:45 home.gif*
-rwxr-xr-- 1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*
-rwxr-xr-- 1 darkdancer darkdancer  112 2007-09-07 21:45 messages_off.gif*
-rwxr-xr-- 1 darkdancer darkdancer  112 2007-09-07 21:45 messages_on.gif*
-rwxr-xr-- 1 darkdancer darkdancer   77 2007-09-07 21:45 noglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer  901 2007-09-07 21:45 profile.gif*
-rwxr-xr-- 1 darkdancer darkdancer 2726 2007-09-07 21:45 proglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer 1224 2007-09-07 21:45 progressbar.gif*

./themes/glass:
total 20
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-xr--  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-xr--  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
-rwxr-xr--  1 darkdancer darkdancer 3852 2007-09-07 21:45 style.css*

./themes/glass/images:
total 56
drwxr-xr-- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 3 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer  508 2007-09-07 21:45 admin.gif*
-rwxr-xr-- 1 darkdancer darkdancer 3169 2007-09-07 21:45 bar.gif*
-rwxr-xr-- 1 darkdancer darkdancer  562 2007-09-07 21:45 directory.gif*
-rwxr-xr-- 1 darkdancer darkdancer  533 2007-09-07 21:45 history.gif*
-rwxr-xr-- 1 darkdancer darkdancer  511 2007-09-07 21:45 home.gif*
-rwxr-xr-- 1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*
-rwxr-xr-- 1 darkdancer darkdancer  588 2007-09-07 21:45 messages_off.gif*
-rwxr-xr-- 1 darkdancer darkdancer 1812 2007-09-07 21:45 messages_on.gif*
-rwxr-xr-- 1 darkdancer darkdancer  348 2007-09-07 21:45 noglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer  558 2007-09-07 21:45 profile.gif*
-rwxr-xr-- 1 darkdancer darkdancer 1760 2007-09-07 21:45 proglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer  319 2007-09-07 21:45 progressbar.gif*

./themes/glyphic:
total 20
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-xr--  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-xr--  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
-rwxr-xr--  1 darkdancer darkdancer 3854 2007-09-07 21:45 style.css*

./themes/glyphic/images:
total 64
drwxr-xr-- 2 darkdancer darkdancer  4096 2007-09-07 21:06 ./
drwxr-xr-- 3 darkdancer darkdancer  4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer   508 2007-09-07 21:45 admin.gif*
-rwxr-xr-- 1 darkdancer darkdancer 11035 2007-09-07 21:45 bar.gif*
-rwxr-xr-- 1 darkdancer darkdancer   562 2007-09-07 21:45 directory.gif*
-rwxr-xr-- 1 darkdancer darkdancer   533 2007-09-07 21:45 history.gif*
-rwxr-xr-- 1 darkdancer darkdancer   511 2007-09-07 21:45 home.gif*
-rwxr-xr-- 1 darkdancer darkdancer    13 2007-09-07 21:45 index.html*
-rwxr-xr-- 1 darkdancer darkdancer   588 2007-09-07 21:45 messages_off.gif*
-rwxr-xr-- 1 darkdancer darkdancer  1812 2007-09-07 21:45 messages_on.gif*
-rwxr-xr-- 1 darkdancer darkdancer   623 2007-09-07 21:45 noglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer   558 2007-09-07 21:45 profile.gif*
-rwxr-xr-- 1 darkdancer darkdancer  2577 2007-09-07 21:45 proglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer   146 2007-09-07 21:45 progressbar.gif*

./themes/hornet:
total 20
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-xr--  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-xr--  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
-rwxr-xr--  1 darkdancer darkdancer 3455 2007-09-07 21:45 style.css*

./themes/hornet/images:
total 60
drwxr-xr-- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 3 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer  424 2007-09-07 21:45 admin.gif*
-rwxr-xr-- 1 darkdancer darkdancer 1710 2007-09-07 21:45 bar.gif*
-rwxr-xr-- 1 darkdancer darkdancer  480 2007-09-07 21:45 directory.gif*
-rwxr-xr-- 1 darkdancer darkdancer  449 2007-09-07 21:45 history.gif*
-rwxr-xr-- 1 darkdancer darkdancer  420 2007-09-07 21:45 home.gif*
-rwxr-xr-- 1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*
-rwxr-xr-- 1 darkdancer darkdancer  489 2007-09-07 21:45 messages_off.gif*
-rwxr-xr-- 1 darkdancer darkdancer 1507 2007-09-07 21:45 messages_on.gif*
-rwxr-xr-- 1 darkdancer darkdancer  623 2007-09-07 21:45 noglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer  472 2007-09-07 21:45 profile.gif*
-rwxr-xr-- 1 darkdancer darkdancer 2569 2007-09-07 21:45 proglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer  138 2007-09-07 21:45 progressbar.gif*
-rwxr-xr-- 1 darkdancer darkdancer  454 2007-09-07 21:45 torrents.gif*

./themes/mape:
total 20
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-xr--  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-xr--  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
-rwxr-xr--  1 darkdancer darkdancer 3662 2007-09-07 21:45 style.css*

./themes/mape/images:
total 76
drwxr-xr-- 2 darkdancer darkdancer  4096 2007-09-07 21:06 ./
drwxr-xr-- 3 darkdancer darkdancer  4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer  1420 2007-09-07 21:45 admin.gif*
-rwxr-xr-- 1 darkdancer darkdancer  1081 2007-09-07 21:45 bar.gif*
-rwxr-xr-- 1 darkdancer darkdancer  1465 2007-09-07 21:45 directory.gif*
-rwxr-xr-- 1 darkdancer darkdancer  1432 2007-09-07 21:45 history.gif*
-rwxr-xr-- 1 darkdancer darkdancer  1425 2007-09-07 21:45 home.gif*
-rwxr-xr-- 1 darkdancer darkdancer    13 2007-09-07 21:45 index.html*
-rwxr-xr-- 1 darkdancer darkdancer  1465 2007-09-07 21:45 messages_off.gif*
-rwxr-xr-- 1 darkdancer darkdancer  1460 2007-09-07 21:45 messages_on.gif*
-rwxr-xr-- 1 darkdancer darkdancer    83 2007-09-07 21:45 noglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer  1472 2007-09-07 21:45 profile.gif*
-rwxr-xr-- 1 darkdancer darkdancer  1760 2007-09-07 21:45 proglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer   319 2007-09-07 21:45 progressbar.gif*
-rwxr-xr-- 1 darkdancer darkdancer 16896 2007-09-07 21:45 Thumbs.db*

./themes/matrix:
total 20
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-xr--  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-xr--  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
-rwxr-xr--  1 darkdancer darkdancer 3852 2007-09-07 21:45 style.css*

./themes/matrix/images:
total 56
drwxr-xr-- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 3 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer  418 2007-09-07 21:45 admin.gif*
-rwxr-xr-- 1 darkdancer darkdancer 1718 2007-09-07 21:45 bar.gif*
-rwxr-xr-- 1 darkdancer darkdancer  480 2007-09-07 21:45 directory.gif*
-rwxr-xr-- 1 darkdancer darkdancer  450 2007-09-07 21:45 history.gif*
-rwxr-xr-- 1 darkdancer darkdancer  420 2007-09-07 21:45 home.gif*
-rwxr-xr-- 1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*
-rwxr-xr-- 1 darkdancer darkdancer  488 2007-09-07 21:45 messages_off.gif*
-rwxr-xr-- 1 darkdancer darkdancer 1357 2007-09-07 21:45 messages_on.gif*
-rwxr-xr-- 1 darkdancer darkdancer  623 2007-09-07 21:45 noglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer  474 2007-09-07 21:45 profile.gif*
-rwxr-xr-- 1 darkdancer darkdancer 2577 2007-09-07 21:45 proglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer  146 2007-09-07 21:45 progressbar.gif*

./themes/matrix_chinese:
total 20
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-xr--  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-xr--  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
-rwxr-xr--  1 darkdancer darkdancer 3455 2007-09-07 21:45 style.css*

./themes/matrix_chinese/images:
total 56
drwxr-xr-- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 3 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer  287 2007-09-07 21:45 admin.gif*
-rwxr-xr-- 1 darkdancer darkdancer 1718 2007-09-07 21:45 bar.gif*
-rwxr-xr-- 1 darkdancer darkdancer  281 2007-09-07 21:45 directory.gif*
-rwxr-xr-- 1 darkdancer darkdancer  286 2007-09-07 21:45 history.gif*
-rwxr-xr-- 1 darkdancer darkdancer  283 2007-09-07 21:45 home.gif*
-rwxr-xr-- 1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*
-rwxr-xr-- 1 darkdancer darkdancer  283 2007-09-07 21:45 messages_off.gif*
-rwxr-xr-- 1 darkdancer darkdancer  283 2007-09-07 21:45 messages_on.gif*
-rwxr-xr-- 1 darkdancer darkdancer  623 2007-09-07 21:45 noglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer  309 2007-09-07 21:45 profile.gif*
-rwxr-xr-- 1 darkdancer darkdancer 2577 2007-09-07 21:45 proglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer  146 2007-09-07 21:45 progressbar.gif*

./themes/midnight:
total 20
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-xr--  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-xr--  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
-rwxr-xr--  1 darkdancer darkdancer 3940 2007-09-07 21:45 style.css*

./themes/midnight/images:
total 56
drwxr-xr-- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 3 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer  276 2007-09-07 21:45 admin.gif*
-rwxr-xr-- 1 darkdancer darkdancer  453 2007-09-07 21:45 bar.gif*
-rwxr-xr-- 1 darkdancer darkdancer  326 2007-09-07 21:45 directory.gif*
-rwxr-xr-- 1 darkdancer darkdancer  306 2007-09-07 21:45 history.gif*
-rwxr-xr-- 1 darkdancer darkdancer  259 2007-09-07 21:45 home.gif*
-rwxr-xr-- 1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*
-rwxr-xr-- 1 darkdancer darkdancer  344 2007-09-07 21:45 messages_off.gif*
-rwxr-xr-- 1 darkdancer darkdancer 1003 2007-09-07 21:45 messages_on.gif*
-rwxr-xr-- 1 darkdancer darkdancer   72 2007-09-07 21:45 noglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer  331 2007-09-07 21:45 profile.gif*
-rwxr-xr-- 1 darkdancer darkdancer 2132 2007-09-07 21:45 proglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer   58 2007-09-07 21:45 progressbar.gif*

./themes/minimal:
total 20
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-xr--  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-xr--  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
-rwxr-xr--  1 darkdancer darkdancer 3854 2007-09-07 21:45 style.css*

./themes/minimal/images:
total 56
drwxr-xr-- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 3 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer  508 2007-09-07 21:45 admin.gif*
-rwxr-xr-- 1 darkdancer darkdancer  799 2007-09-07 21:45 bar.gif*
-rwxr-xr-- 1 darkdancer darkdancer  562 2007-09-07 21:45 directory.gif*
-rwxr-xr-- 1 darkdancer darkdancer  533 2007-09-07 21:45 history.gif*
-rwxr-xr-- 1 darkdancer darkdancer  511 2007-09-07 21:45 home.gif*
-rwxr-xr-- 1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*
-rwxr-xr-- 1 darkdancer darkdancer  588 2007-09-07 21:45 messages_off.gif*
-rwxr-xr-- 1 darkdancer darkdancer 1812 2007-09-07 21:45 messages_on.gif*
-rwxr-xr-- 1 darkdancer darkdancer  809 2007-09-07 21:45 noglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer  558 2007-09-07 21:45 profile.gif*
-rwxr-xr-- 1 darkdancer darkdancer 3010 2007-09-07 21:45 proglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer  154 2007-09-07 21:45 progressbar.gif*

./themes/mint:
total 20
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-xr--  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-xr--  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
-rwxr-xr--  1 darkdancer darkdancer 3852 2007-09-07 21:45 style.css*

./themes/mint/images:
total 60
drwxr-xr-- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 3 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer  426 2007-09-07 21:45 admin.gif*
-rwxr-xr-- 1 darkdancer darkdancer 1710 2007-09-07 21:45 bar.gif*
-rwxr-xr-- 1 darkdancer darkdancer  482 2007-09-07 21:45 directory.gif*
-rwxr-xr-- 1 darkdancer darkdancer  450 2007-09-07 21:45 history.gif*
-rwxr-xr-- 1 darkdancer darkdancer  422 2007-09-07 21:45 home.gif*
-rwxr-xr-- 1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*
-rwxr-xr-- 1 darkdancer darkdancer  492 2007-09-07 21:45 messages_off.gif*
-rwxr-xr-- 1 darkdancer darkdancer 1616 2007-09-07 21:45 messages_on.gif*
-rwxr-xr-- 1 darkdancer darkdancer  623 2007-09-07 21:45 noglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer  477 2007-09-07 21:45 profile.gif*
-rwxr-xr-- 1 darkdancer darkdancer 2569 2007-09-07 21:45 proglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer  138 2007-09-07 21:45 progressbar.gif*
-rwxr-xr-- 1 darkdancer darkdancer  454 2007-09-07 21:45 torrents.gif*

./themes/rust:
total 20
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-xr--  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-xr--  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
-rwxr-xr--  1 darkdancer darkdancer 3871 2007-09-07 21:45 style.css*

./themes/rust/images:
total 76
drwxr-xr-- 2 darkdancer darkdancer  4096 2007-09-07 21:06 ./
drwxr-xr-- 3 darkdancer darkdancer  4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer   956 2007-09-07 21:45 admin.gif*
-rwxr-xr-- 1 darkdancer darkdancer 12948 2007-09-07 21:45 bar.gif*
-rwxr-xr-- 1 darkdancer darkdancer   971 2007-09-07 21:45 directory.gif*
-rwxr-xr-- 1 darkdancer darkdancer   969 2007-09-07 21:45 history.gif*
-rwxr-xr-- 1 darkdancer darkdancer   961 2007-09-07 21:45 home.gif*
-rwxr-xr-- 1 darkdancer darkdancer    13 2007-09-07 21:45 index.html*
-rwxr-xr-- 1 darkdancer darkdancer   985 2007-09-07 21:45 messages_off.gif*
-rwxr-xr-- 1 darkdancer darkdancer  2294 2007-09-07 21:45 messages_on.gif*
-rwxr-xr-- 1 darkdancer darkdancer  1372 2007-09-07 21:45 noglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer   974 2007-09-07 21:45 profile.gif*
-rwxr-xr-- 1 darkdancer darkdancer  8245 2007-09-07 21:45 proglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer   835 2007-09-07 21:45 progressbar.gif*

./themes/slate:
total 20
drwxr-xr--  3 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 17 darkdancer darkdancer 4096 2007-09-07 21:06 ../
drwxr-xr--  2 darkdancer darkdancer 4096 2007-09-07 21:06 images/
-rwxr-xr--  1 darkdancer darkdancer  342 2007-09-07 21:45 index.php*
-rwxr-xr--  1 darkdancer darkdancer 3852 2007-09-07 21:45 style.css*

./themes/slate/images:
total 60
drwxr-xr-- 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-- 3 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr-- 1 darkdancer darkdancer  508 2007-09-07 21:45 admin.gif*
-rwxr-xr-- 1 darkdancer darkdancer   69 2007-09-07 21:45 bar.gif*
-rwxr-xr-- 1 darkdancer darkdancer  562 2007-09-07 21:45 directory.gif*
-rwxr-xr-- 1 darkdancer darkdancer  533 2007-09-07 21:45 history.gif*
-rwxr-xr-- 1 darkdancer darkdancer  511 2007-09-07 21:45 home.gif*
-rwxr-xr-- 1 darkdancer darkdancer   13 2007-09-07 21:45 index.html*
-rwxr-xr-- 1 darkdancer darkdancer  588 2007-09-07 21:45 messages_off.gif*
-rwxr-xr-- 1 darkdancer darkdancer 1812 2007-09-07 21:45 messages_on.gif*
-rwxr-xr-- 1 darkdancer darkdancer  553 2007-09-07 21:45 noglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer  558 2007-09-07 21:45 profile.gif*
-rwxr-xr-- 1 darkdancer darkdancer 5909 2007-09-07 21:45 proglass.gif*
-rwxr-xr-- 1 darkdancer darkdancer  791 2007-09-07 21:45 progressbar.gif*

./upgrades:
total 44
drwxr-xr--  2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-x 12 darkdancer darkdancer 4096 2007-09-08 00:40 ../
-rwxr-xr--  1 darkdancer darkdancer 2515 2007-09-07 21:45 upgrade11_12.php*
-rwxr-xr--  1 darkdancer darkdancer 2065 2007-09-07 21:45 upgrade12_13.php*
-rwxr-xr--  1 darkdancer darkdancer 1555 2007-09-07 21:45 upgrade13_14.php*
-rwxr-xr--  1 darkdancer darkdancer 1561 2007-09-07 21:45 upgrade14_15.php*
-rwxr-xr--  1 darkdancer darkdancer 1957 2007-09-07 21:45 upgrade15_20.php*
-rwxr-xr--  1 darkdancer darkdancer 4664 2007-09-07 21:45 upgrade20_21.php*
-rwxr-xr--  1 darkdancer darkdancer 2212 2007-09-07 21:45 upgrade21_22.php*
-rwxr-xr--  1 darkdancer darkdancer 1595 2007-09-07 21:45 upgrade22_23.php*

---

### Post by kebes on 2007-09-08
You have two different things going wrong...
> **DarkDancer said:**
> Warning: include(themes/matrix/index.php) [function.include]: failed to open stream: Permission denied in /var/www/torrentflux2/db.php on line 26

Warning: include() [function.include]: Failed opening 'themes/matrix/index.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/torrentflux2/db.php on line 26

I see from your filelist that the directories don't have access set (so the webserver cannot enter into any sub-directories). To add that permission:
```

cd /var/www/torrentflux2/
chmod +X -R *

```
Take note that in the above code that's **+X** (a capital X) not +x ...

> 
TorrentFlux Database/SQL Error
Database error: Unknown database 'torrentflux'

Always check your database variables in the config.php file.

This means that in your config file (/var/www/torrentflux2/config.php) you have set the username and password correctly, but whatever you specified for $cfg["db_name"] is wrong.

You set it to "torrentflux" ... but that database doesn't exist. Either you created it already, but under a different name... or you have not created the database yet.

Step 4.b. in the how-to explains how to create the database. You just need to know your MySQL password, and know where the torrentflux MySQL script is. It was included in the tar file you downloaded, and it's called "mysql_torrentflux.sql"

---

### Post by DarkDancer on 2007-09-08
Ok, I did the chmod, then went into /var/www/torrentflux2/config.php and changed the database name from torrentflux to torrentflux2 ( the correct name), and now the error message says this:

> TorrentFlux Database/SQL Error
Database error: Access denied for user 'darkdancer'@'localhost' to database 'torrentflux2'

Always check your database variables in the config.php file.

---

### Post by kebes on 2007-09-08
> **DarkDancer said:**
> Ok, I did the chmod, then went into /var/www/torrentflux2/config.php and changed the database name from torrentflux to torrentflux2 ( the correct name), and now the error message says this:

Okay, so in the file "/var/www/torrentflux2/config.php you set the following:
```

$cfg["db_type"] = "mysql";       // mysql, postgres7 view adodb/drivers/
$cfg["db_host"] = "localhost";   // DB host computer name or IP
$cfg["db_name"] = "torrentflux2"; // Name of the Database
$cfg["db_user"] = "darkdancer";        // username for your MySQL database
$cfg["db_pass"] = "secret";            // password for database

```
Where "secret" is the password for the **MySQL user** "darkdancer" (remember, the MySQL user darkdancer is different from your normal login user, so it may have a different password, depending on what you set previously).

So far so good. Now you need to make sure that MySQL user "darkdancer" has access to the MySQL database "torrentflux2". This is done in step 4.c. of the how-to. Like so:
```

$ mysql -uroot -p
mysql> use mysql;
mysql> GRANT SELECT,INSERT,UPDATE,DELETE,CREATE,DROP ON torrentflux2.* TO 'darkdancer'@'localhost';
mysql> FLUSH PRIVILEGES;
mysql> exit;

```
Notice that in the above code I'm using "torrentflux2" and "darkdancer" for the database and MySQL user, respectively.

---

### Post by DarkDancer on 2007-09-08
That's got it, thanks! ;)

---

### Post by DarkDancer on 2007-09-08
Oh, one more thing, to change the path where it downloads tooo, do I just need to change the path there on that page or do I need to do something else?

'Cause if I do that it tells me the path is not valid (it is).
/media/hda7/downloads/video/

---

### Post by kebes on 2007-09-08
Glad it's working! (Sorry that took so long...)

> **DarkDancer said:**
> Oh, one more thing, to change the path where it downloads tooo, do I just need to change the path there on that page or do I need to do something else?

'Cause if I do that it tells me the path is not valid (it is).
/media/hda7/downloads/video/

In principle you just need to log into torrentflux, click "admin" and then "settings" and set the path to what you want. Be sure the path ends with a slash (so "/media/hda7/downloads/video" is wrong, but "/media/hda7/downloads/video/" is correct).

The path you select must be **writeable** by the webserver. Which means doing something like:
```

cd /media/hda7/downloads/
chmod 777 video

```

That should fix it.


(Note, however, that another user posting in this thread has been having some issues with changing the path away from the default. There might be a bug in torrentflux...)

---

### Post by DarkDancer on 2007-09-08
Thanks, I tried that, I still get the path not valid. Here is exactly how I have it under paths:

> /media/hda7/downloads/video/ (I copied and pasted). I actually even repasted it from the terminal window to make sure that I didn't make any mistakes on getting to the path (adding the / at the end of course).

---

### Post by kebes on 2007-09-08
> **DarkDancer said:**
> Thanks, I tried that, I still get the path not valid. Here is exactly how I have it under paths:

 (I copied and pasted). I actually even repasted it from the terminal window to make sure that I didn't make any mistakes on getting to the path (adding the / at the end of course).

Okay I just did some tests with one of my torrentflux installs, and I can confirm the problem you're seeing. I'm pretty sure this is the problem:

You're trying to use a directory that the webserver can't see. Even though the directory "video" is viewable to the webserver, the parent directory isn't.

This should fix it:
```

cd /media/
chmod o+x hda7
cd hda7
chmod o+x downloads

```

This means that the webserver (and any other user, of course) can access (e**x**ecute) those directories.

---

### Post by DarkDancer on 2007-09-08
Oh, hey, that's a fat 32 drive, would that cause any problems?

---

### Post by kebes on 2007-09-08
> **mcdeath said:**
> no luck kebes it still fails, let me know if you get any other ideas.

mcdeath, in thinking about darkdancer's problem, I think your install could be fixed in the same way. You want to use the directory "/media/torrentdrive/torrents/" for your torrents, so you need to go:

```

cd media
chmod o+x torrentdrive
cd torrentdrive
chmod 777 torrents

```

---

### Post by kebes on 2007-09-08
> **DarkDancer said:**
> Oh, hey, that's a fat 32 drive, would that cause any problems?

Oh, I didn't know it was a fat32. It does cause some differences, yeah. Still, my suggestion might still work:
```

cd /media/
chmod o+x hda7
cd hda7
chmod o+x downloads

```

That 2nd chmod might fail (fat32 doesn't understand unix permissions), but the 1st one might be all that's needed to get it working for you.

---

### Post by DarkDancer on 2007-09-08
That got it! Thanks! Woohoo! Now all I have to do is figure out the redirect...but that's not your problem ;)

---

### Post by kebes on 2007-09-08
> **DarkDancer said:**
> That got it! Thanks! Woohoo! Now all I have to do is figure out the redirect...but that's not your problem ;)

You're welcome! Finally you can actually enjoy using it!

---

### Post by DarkDancer on 2007-09-08
Dang, I spoke too soon. When I try to actually grab a torrent, I get this:

Warning: fopen(/media/hda7/.torrents/Text.fil) [function.fopen]: failed to open stream: Permission denied in /var/www/torrentflux2/index.php on line 405

Warning: fwrite(): supplied argument is not a valid stream resource in /var/www/torrentflux2/index.php on line 406

Warning: fclose(): supplied argument is not a valid stream resource in /var/www/torrentflux2/index.php on line 407

Warning: Cannot modify header information - headers already sent by (output started at /var/www/torrentflux2/index.php:405) in /var/www/torrentflux2/index.php on line 418

---

### Post by kebes on 2007-09-08
> **DarkDancer said:**
> Dang, I spoke too soon. When I try to actually grab a torrent, I get this:

Warning: fopen(/media/hda7/.torrents/Text.fil) [function.fopen]: failed to open stream: Permission denied in /var/www/torrentflux2/index.php on line 405

Warning: fwrite(): supplied argument is not a valid stream resource in /var/www/torrentflux2/index.php on line 406

Warning: fclose(): supplied argument is not a valid stream resource in /var/www/torrentflux2/index.php on line 407

Warning: Cannot modify header information - headers already sent by (output started at /var/www/torrentflux2/index.php:405) in /var/www/torrentflux2/index.php on line 418


From the error, it looks like you are now using the directory "/media/hda7/" for your downloads (previously you mentiond using "/media/hda7/video/"). Is that right?

If you've switched directory, did you update the permission on the new download directory:
```

cd /media/
chmod 777 hda7

```

---

### Post by mcdeath on 2007-09-08
> **kebes said:**
> mcdeath, in thinking about darkdancer's problem, I think your install could be fixed in the same way. You want to use the directory "/media/torrentdrive/torrents/" for your torrents, so you need to go:

```

cd media
chmod o+x torrentdrive
cd torrentdrive
chmod 777 torrents

```

No luck kebes, thanks for trying. I'm really at a loss here.

---

### Post by DarkDancer on 2007-09-08
Oh, apparently I hadn't put the /dowloads/video/back at the end in the torrentflux settings, when I do, it says that the path is not valid again.

---

### Post by DarkDancer on 2007-09-08
Well, I did a lot of work since we last talked, installed a small Sata drive (I had an 80 gig lieing around in my closet) and formatted it to ext 3. Got it mounted (that was a chore) and eventually got the permissions set, though not totally (torrentflux can write to it, but I can't, not without sudoing), it all seems to work now, though I picked out a torrent with a bunch of seeders and it has been nearly 10 minutes now and no data has flowed, so not sure about that......

---

### Post by DarkDancer on 2007-09-09
Hmmm, still no data, and it hasn't put anything at all on that drive, except a folder named darkdancer.

---

### Post by disk11 on 2007-09-09
I'm having the same problem as mcdeath, only one torrent runs at a time.  Running torrentflux 2.3 and followed the directions in the OP to the letter, Xubuntu 7.04.

Does torrentflux generate an log besides the one Admin->Activity?

---

### Post by mcdeath on 2007-09-09
kebes it's fixed, well sort of.  I had to rebuild the server and start from scratch which ironically to 45mins.  Came up first time no problems.

Disk11 maybe starting over again may work for you.

The shame in my case is that the issue returned after I re-booted my router.

---

### Post by DarkDancer on 2007-09-10
Hey Kebes,

     I am hoping you will come back tomorrow, 'cause I think I just about have this thing taken care of. I'm attaching a screenshot (if I have the redirect set up right this should work fine) of what I have so that you can see what I am talking about. 

[IMG]http://nightsinger.no-ip.biz/Screenshot-TorrentFlux%20-%20Swiftfox.png[/IMG]

The problem is no matter what I do, I cannot get them to start. I click on the little green download arrorw and tell it to run torrent, the arrow will go red (stop torrent) until the next page refresh. It then turns back to green and nothing happens. I picked Torrents with a nice beefy nu,mber of both seeds and peers and it has been over a day for two of the, and no start..... what am I missing?

---

### Post by mcdeath on 2007-09-10
kebes just a little follow-up to let you know what resolved my issue.
First of all I never mentioned this fact because I didn't think it was related being other torrent clients do not behave in this manner.

Basically when first setup torrentflux (the both times I've installed it) I change it from using a port range to a single port.

This is not an unusual thing to do as most clients simply use one port.
For some reason (in my case) torrentflux no likey...

As soon as I put back a small range of ports and made the necessary adjustments to my router up she came with no problems.

I can add more than one torrent etc...

I'm kicking myself for not checking this sooner. (lol I'm a network tech by trade)

Be well my friend.

---

### Post by kebes on 2007-09-10
> **DarkDancer said:**
> The problem is no matter what I do, I cannot get them to start. I click on the little green download arrorw and tell it to run torrent, the arrow will go red (stop torrent) until the next page refresh. It then turns back to green and nothing happens. I picked Torrents with a nice beefy nu,mber of both seeds and peers and it has been over a day for two of the, and no start..... what am I missing?

Hmm... Is this a problem only with Torrentflux, or with all torrent programs? If it's a problem with all torrent programs, then you need to double-check your router settings and/or firewall settings. (It's also possible that your ISP is blocking you...)


Assuming it's a problem with torrentflux specifically, these are my best guesses:

1. The ".BitTornado" directory is broken. There is a hidden directory called ".BitTornado" in your download folder, and it's permissions have to be set right. To check what's going on:
```

cd /var/www/torrentflux/downloads/
ls -laF

```
(Instead of "/var/www/torrentflux/downloads/", put whatever your download directory is...)

The "ls -laF" should return something like:
```

drwxrwxrwx  6 darkdancer    darkdancer    4096 2007-09-10 20:30 ./
drwxr-xr-x 12 darkdancer    darkdancer    4096 2007-09-08 16:23 ../
drwxr-xr-x  4 www-data www-data 4096 2007-09-10 20:32 bit/
drwx------  6 www-data www-data 4096 2007-09-10 20:30 .BitTornado/
-rwxr-xr-x  1 darkdancer    darkdancer      13 2007-08-09 21:57 index.html*
drwxr-xr-x  2 www-data www-data 4096 2007-09-10 20:32 .torrents/

```

The thing to note here is that the ".BitTornado" and ".torrents" directories are owned by "www-data" and is set as with read permission. If they are not, fix them:
```

sudo chown www-data:www-data .BitTornado
sudo chmod 700 .BitTornado
sudo chown www-data:www-data .torrents
sudo chmod 755 .torrents

```



2. Something else about your BitTornado install (which torrentflux is trying to use) is broken.


3. Outgoing ports are restricted. It could be that your router, or the firewall in  Linux is blocking access. (Do you have a router? Did you modify the software firewall?) Depending on whether or not other torrent applications are affected, this will let you track down a possible source to the problem.


4. Receive port blocked. There is an option in Torrentflux to control the port range it uses (Admin > Settings > Port Range). By opening up the selected port range on your router (and other firewalls) you can usually increase torrent efficiency considerably. (This is probably not the problem, though, because you should still be able to start a torrent, albeit more slowly.)





If you want, you can post information about the downloads directory:
```

cd /var/www/torrentflux/downloads/
ls -laF -R

```
(This will list all kinds of files and permissions... you may need to remove lines before posting the output, since it will include details about your download history.)

---

### Post by kebes on 2007-09-10
> **mcdeath said:**
> kebes just a little follow-up to let you know what resolved my issue.


Thanks for the update! I definitely didn't think about that. That's no doubt a bug in torrentflux, and I'll be sure to let others know if they run into it!

Happy torrenting!

---

### Post by kebes on 2007-09-10
> **disk11 said:**
> I'm having the same problem as mcdeath, only one torrent runs at a time.  Running torrentflux 2.3 and followed the directions in the OP to the letter, Xubuntu 7.04.

Does torrentflux generate an log besides the one Admin->Activity?

As far as I know, Torrentflux doesn't generate a log besides the one you see in the admin panel. However you can get a bit of information about what it is doing by manually inspecting the files in:
/var/www/torrentflux/downloads/
(or whatever you set the download folder to be)

There are hidden directories called ".torrents" and ".BitTornado" that contain information that torrentflux uses to keep track of what it is doing. It's mostly cryptic, however.



If your problem is the same thing that mcdeath was seeing, then try his fix and see what happens:
Go to "Admin" > "Settings" and make sure that "Port Range" is not set to a single value, but rather a range of ports (which you must then open up on your router)...

---

### Post by DarkDancer on 2007-09-10
Hey Kebes? Any more ideas for me?

Never mind, didn't even see that post! Sorry!

---

### Post by DarkDancer on 2007-09-10
> drwxrwxrwx 4 root       root       4096 2007-09-08 23:53 ./
drwxrwxrwx 6 darkdancer darkdancer 4096 2007-09-09 00:15 ../
drwxrwxrwx 2 www-data   www-data   4096 2007-09-10 00:03 darkdancer/
drwxrwxrwx 2 www-data   www-data   4096 2007-09-09 23:55 .torrents/


There is no .bittornado subdirectory......this might be the problem... ;)

bittornado is installed, (actually I just uninstalled and reinmstalled then pulled that data there). Is there something special I need to do to get it threre?

Oh, other torrent clients do work, though they have started slowing my computer down (some more than others) and I have no idea why. I opened up the suggested port range (the one in torrentflux) in my router.

---

### Post by kebes on 2007-09-10
> **DarkDancer said:**
> There is no .bittornado subdirectory......this might be the problem... ;)

bittornado is installed, (actually I just uninstalled and reinmstalled then pulled that data there). Is there something special I need to do to get it threre?

Oh, other torrent clients do work, though they have started slowing my computer down (some more than others) and I have no idea why. I opened up the suggested port range (the one in torrentflux) in my router.

On my installation, if I delete the ".BitTornado" directory, it recreates it. So the fact that it doesn't exist (and isn't being created) leads me to believe that something is wrong at the BitTornado level.

In your torrentflux main directory (/var/www/torrentflux/ by default), do you have the "TF_BitTornaod" directory? And is it set with sufficient permissions, like "drwxr-xr-x"?


Also, what do you get when you run:
```

locate bittornado

```
(It should list a bunch of files in /var/lib/, /usr/bin, and /usr/share/ ...)

You could try using the bittornado command-line downloader, and see if it works. (If it doesn't, then perhaps that's the source of the problem...) The binary is /usr/bin/btdownloadcurses.bittornado
I think.

---

### Post by DarkDancer on 2007-09-10
Ok, let's see what we have...

> darkdancer@darkdancers:/var/www/torrentflux2$ ls -laF -R TF_BitTornado
TF_BitTornado:
total 60
drwxr-xr-x  4 darkdancer darkdancer  4096 2007-09-07 21:06 ./
drwxr-xr-x 12 darkdancer darkdancer  4096 2007-09-08 13:13 ../
drwxr-xr-x  4 darkdancer darkdancer  4096 2007-09-07 21:06 BitTornado/
-rwxr-xr-x  1 darkdancer darkdancer  1169 2007-09-07 21:45 btmakemetafile.py*
-rwxr-xr-x  1 darkdancer darkdancer 15601 2007-09-07 21:45 btphptornado.py*
-rwxr-xr-x  1 darkdancer darkdancer  2570 2007-09-07 21:45 btshowmetainfo.py*
-rwxr-xr-x  1 darkdancer darkdancer    13 2007-09-07 21:45 index.html*
drwxr-xr-x  2 darkdancer darkdancer  4096 2007-09-07 21:06 original_src/
-rwxr-xr-x  1 darkdancer darkdancer 14767 2007-09-07 21:45 tfQManager.py*

TF_BitTornado/BitTornado:
total 296
drwxr-xr-x 4 darkdancer darkdancer  4096 2007-09-07 21:06 ./
drwxr-xr-x 4 darkdancer darkdancer  4096 2007-09-07 21:06 ../
-rwxr-xr-x 1 darkdancer darkdancer  7600 2007-09-07 21:45 bencode.py*
-rwxr-xr-x 1 darkdancer darkdancer  4058 2007-09-07 21:45 bitfield.py*
drwxr-xr-x 3 darkdancer darkdancer  4096 2007-09-07 21:06 bt1/
-rwxr-xr-x 1 darkdancer darkdancer   595 2007-09-07 21:45 clock.py*
-rwxr-xr-x 1 darkdancer darkdancer 10786 2007-09-07 21:45 ConfigDir.py*
-rwxr-xr-x 1 darkdancer darkdancer 51250 2007-09-07 21:45 ConfigReader.py*
-rwxr-xr-x 1 darkdancer darkdancer  1112 2007-09-07 21:45 ConnChoice.py*
-rwxr-xr-x 1 darkdancer darkdancer  5369 2007-09-07 21:45 CreateIcons.py*
-rwxr-xr-x 1 darkdancer darkdancer  1029 2007-09-07 21:45 CurrentRateMeasure.py*
drwxr-xr-x 2 darkdancer darkdancer  4096 2007-09-07 21:06 cvs/
-rwxr-xr-x 1 darkdancer darkdancer    27 2007-09-07 21:45 .cvsignore*
-rwxr-xr-x 1 darkdancer darkdancer 33558 2007-09-07 21:45 download_bt1.py*
-rwxr-xr-x 1 darkdancer darkdancer  5553 2007-09-07 21:45 HTTPHandler.py*
-rwxr-xr-x 1 darkdancer darkdancer  4464 2007-09-07 21:45 inifile.py*
-rwxr-xr-x 1 darkdancer darkdancer  1434 2007-09-07 21:45 __init__.py*
-rwxr-xr-x 1 darkdancer darkdancer  5161 2007-09-07 21:45 iprangeparse.py*
-rwxr-xr-x 1 darkdancer darkdancer 12499 2007-09-07 21:45 launchmanycore.py*
-rwxr-xr-x 1 darkdancer darkdancer  7675 2007-09-07 21:45 natpunch.py*
-rwxr-xr-x 1 darkdancer darkdancer  4230 2007-09-07 21:45 parseargs.py*
-rwxr-xr-x 1 darkdancer darkdancer  4854 2007-09-07 21:45 parsedir.py*
-rwxr-xr-x 1 darkdancer darkdancer  1878 2007-09-07 21:45 piecebuffer.py*
-rwxr-xr-x 1 darkdancer darkdancer    99 2007-09-07 21:45 PSYCO.py*
-rwxr-xr-x 1 darkdancer darkdancer  4728 2007-09-07 21:45 RateLimiter.py*
-rwxr-xr-x 1 darkdancer darkdancer  2002 2007-09-07 21:45 RateMeasure.py*
-rwxr-xr-x 1 darkdancer darkdancer  6532 2007-09-07 21:45 RawServer.py*
-rwxr-xr-x 1 darkdancer darkdancer  2337 2007-09-07 21:45 selectpoll.py*
-rwxr-xr-x 1 darkdancer darkdancer  5647 2007-09-07 21:45 ServerPortHandler.py*
-rwxr-xr-x 1 darkdancer darkdancer 12823 2007-09-07 21:45 SocketHandler.py*
-rwxr-xr-x 1 darkdancer darkdancer  5247 2007-09-07 21:45 subnetparse.py*
-rwxr-xr-x 1 darkdancer darkdancer   852 2007-09-07 21:45 torrentlistparse.py*
-rwxr-xr-x 1 darkdancer darkdancer  3167 2007-09-07 21:45 zurllib.py*

TF_BitTornado/BitTornado/bt1:
total 300
drwxr-xr-x 3 darkdancer darkdancer  4096 2007-09-07 21:06 ./
drwxr-xr-x 4 darkdancer darkdancer  4096 2007-09-07 21:06 ../
-rwxr-xr-x 1 darkdancer darkdancer  3827 2007-09-07 21:45 btformats.py*
-rwxr-xr-x 1 darkdancer darkdancer  4268 2007-09-07 21:45 Choker.py*
-rwxr-xr-x 1 darkdancer darkdancer  8847 2007-09-07 21:45 Connecter.py*
drwxr-xr-x 2 darkdancer darkdancer  4096 2007-09-07 21:06 cvs/
-rwxr-xr-x 1 darkdancer darkdancer    51 2007-09-07 21:45 .cvsignore*
-rwxr-xr-x 1 darkdancer darkdancer  5310 2007-09-07 21:45 DownloaderFeedback.py*
-rwxr-xr-x 1 darkdancer darkdancer 22608 2007-09-07 21:45 Downloader.py*
-rwxr-xr-x 1 darkdancer darkdancer 10227 2007-09-07 21:45 Encrypter.py*
-rwxr-xr-x 1 darkdancer darkdancer  2240 2007-09-07 21:45 fakeopen.py*
-rwxr-xr-x 1 darkdancer darkdancer  8479 2007-09-07 21:45 FileSelector.py*
-rwxr-xr-x 1 darkdancer darkdancer   298 2007-09-07 21:45 Filter.py*
-rwxr-xr-x 1 darkdancer darkdancer  8461 2007-09-07 21:45 HTTPDownloader.py*
-rwxr-xr-x 1 darkdancer darkdancer    13 2007-09-07 21:45 __init__.py*
-rwxr-xr-x 1 darkdancer darkdancer  9038 2007-09-07 21:45 makemetafile.py*
-rwxr-xr-x 1 darkdancer darkdancer  2731 2007-09-07 21:45 NatCheck.py*
-rwxr-xr-x 1 darkdancer darkdancer 11915 2007-09-07 21:45 PiecePicker.py*
-rwxr-xr-x 1 darkdancer darkdancer 14089 2007-09-07 21:45 Rerequester.py*
-rwxr-xr-x 1 darkdancer darkdancer  6581 2007-09-07 21:45 Statistics.py*
-rwxr-xr-x 1 darkdancer darkdancer 20368 2007-09-07 21:45 Storage.py*
-rwxr-xr-x 1 darkdancer darkdancer 37256 2007-09-07 21:45 StorageWrapper.py*
-rwxr-xr-x 1 darkdancer darkdancer  3757 2007-09-07 21:45 StreamCheck.py*
-rwxr-xr-x 1 darkdancer darkdancer  7244 2007-09-07 21:45 T2T.py*
-rwxr-xr-x 1 darkdancer darkdancer 46229 2007-09-07 21:45 track.py*
-rwxr-xr-x 1 darkdancer darkdancer  4789 2007-09-07 21:45 Uploader.py*

TF_BitTornado/BitTornado/bt1/cvs:
total 32
drwxr-xr-x 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-x 3 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr-x 1 darkdancer darkdancer 1060 2007-09-07 21:45 Entries*
-rwxr-xr-x 1 darkdancer darkdancer  515 2007-09-07 21:45 Entries.Extra*
-rwxr-xr-x 1 darkdancer darkdancer  515 2007-09-07 21:45 Entries.Extra.Old*
-rwxr-xr-x 1 darkdancer darkdancer 1060 2007-09-07 21:45 Entries.Old*
-rwxr-xr-x 1 darkdancer darkdancer   26 2007-09-07 21:45 Repository*
-rwxr-xr-x 1 darkdancer darkdancer   40 2007-09-07 21:45 Root*

TF_BitTornado/BitTornado/cvs:
total 36
drwxr-xr-x 2 darkdancer darkdancer 4096 2007-09-07 21:06 ./
drwxr-xr-x 4 darkdancer darkdancer 4096 2007-09-07 21:06 ../
-rwxr-xr-x 1 darkdancer darkdancer 1375 2007-09-07 21:45 Entries*
-rwxr-xr-x 1 darkdancer darkdancer  700 2007-09-07 21:45 Entries.Extra*
-rwxr-xr-x 1 darkdancer darkdancer  700 2007-09-07 21:45 Entries.Extra.Old*
-rwxr-xr-x 1 darkdancer darkdancer   12 2007-09-07 21:45 Entries.Log*
-rwxr-xr-x 1 darkdancer darkdancer 1375 2007-09-07 21:45 Entries.Old*
-rwxr-xr-x 1 darkdancer darkdancer   22 2007-09-07 21:45 Repository*
-rwxr-xr-x 1 darkdancer darkdancer   40 2007-09-07 21:45 Root*

TF_BitTornado/original_src:
total 400
drwxr-xr-x 2 darkdancer darkdancer   4096 2007-09-07 21:06 ./
drwxr-xr-x 4 darkdancer darkdancer   4096 2007-09-07 21:06 ../
-rwxr-xr-x 1 darkdancer darkdancer 189992 2007-09-07 21:45 BitTornado-0.3.15.tar.gz*
-rwxr-xr-x 1 darkdancer darkdancer 194718 2007-09-07 21:45 BitTornado-0.3.17.tar.gz*
-rwxr-xr-x 1 darkdancer darkdancer     13 2007-09-07 21:45 index.html*


and...

> darkdancer@darkdancers:/var/www/torrentflux2$ locate bittornado
/usr/share/python-support/bittornado
/usr/share/python-support/bittornado/BitTornado
/usr/share/python-support/bittornado/BitTornado/launchmanycore.py
/usr/share/python-support/bittornado/BitTornado/parsedir.py
/usr/share/python-support/bittornado/BitTornado/subnetparse.py
/usr/share/python-support/bittornado/BitTornado/ConnChoice.py
/usr/share/python-support/bittornado/BitTornado/ServerPortHandler.py
/usr/share/python-support/bittornado/BitTornado/torrentlistparse.py
/usr/share/python-support/bittornado/BitTornado/btmakemetafile.py
/usr/share/python-support/bittornado/BitTornado/iprangeparse.py
/usr/share/python-support/bittornado/BitTornado/__init__.py
/usr/share/python-support/bittornado/BitTornado/inifile.py
/usr/share/python-support/bittornado/BitTornado/download_bt1.py
/usr/share/python-support/bittornado/BitTornado/bitfield.py
/usr/share/python-support/bittornado/BitTornado/RawServer.py
/usr/share/python-support/bittornado/BitTornado/HTTPHandler.py
/usr/share/python-support/bittornado/BitTornado/ConfigReader.py
/usr/share/python-support/bittornado/BitTornado/parseargs.py
/usr/share/python-support/bittornado/BitTornado/ConfigDir.py
/usr/share/python-support/bittornado/BitTornado/RateLimiter.py
/usr/share/python-support/bittornado/BitTornado/zurllib.py
/usr/share/python-support/bittornado/BitTornado/RateMeasure.py
/usr/share/python-support/bittornado/BitTornado/SocketHandler.py
/usr/share/python-support/bittornado/BitTornado/bencode.py
/usr/share/python-support/bittornado/BitTornado/natpunch.py
/usr/share/python-support/bittornado/BitTornado/clock.py
/usr/share/python-support/bittornado/BitTornado/piecebuffer.py
/usr/share/python-support/bittornado/BitTornado/CurrentRateMeasure.py
/usr/share/python-support/bittornado/BitTornado/selectpoll.py
/usr/share/python-support/bittornado/BitTornado/btcompletedir.py
/usr/share/python-support/bittornado/BitTornado/PSYCO.py
/usr/share/python-support/bittornado/BitTornado/CreateIcons.py
/usr/share/python-support/bittornado/BitTornado/BT1
/usr/share/python-support/bittornado/BitTornado/BT1/FileSelector.py
/usr/share/python-support/bittornado/BitTornado/BT1/Storage.py
/usr/share/python-support/bittornado/BitTornado/BT1/track.py
/usr/share/python-support/bittornado/BitTornado/BT1/Rerequester.py
/usr/share/python-support/bittornado/BitTornado/BT1/makemetafile.py
/usr/share/python-support/bittornado/BitTornado/BT1/Statistics.py
/usr/share/python-support/bittornado/BitTornado/BT1/DownloaderFeedback.py
/usr/share/python-support/bittornado/BitTornado/BT1/__init__.py
/usr/share/python-support/bittornado/BitTornado/BT1/T2T.py
/usr/share/python-support/bittornado/BitTornado/BT1/StorageWrapper.py
/usr/share/python-support/bittornado/BitTornado/BT1/Uploader.py
/usr/share/python-support/bittornado/BitTornado/BT1/Filter.py
/usr/share/python-support/bittornado/BitTornado/BT1/Encrypter.py
/usr/share/python-support/bittornado/BitTornado/BT1/NatCheck.py
/usr/share/python-support/bittornado/BitTornado/BT1/Connecter.py
/usr/share/python-support/bittornado/BitTornado/BT1/PiecePicker.py
/usr/share/python-support/bittornado/BitTornado/BT1/btformats.py
/usr/share/python-support/bittornado/BitTornado/BT1/HTTPDownloader.py
/usr/share/python-support/bittornado/BitTornado/BT1/Downloader.py
/usr/share/python-support/bittornado/BitTornado/BT1/Choker.py
/usr/share/python-support/bittornado/BitTornado/BT1/StreamCheck.py
/usr/share/python-support/bittornado/BitTornado/BT1/fakeopen.py
/usr/share/doc/bittornado
/usr/share/doc/bittornado/copyright
/usr/share/doc/bittornado/FAQ.txt
/usr/share/doc/bittornado/multitracker-spec.txt
/usr/share/doc/bittornado/credits.txt
/usr/share/doc/bittornado/webseed-spec.txt.gz
/usr/share/doc/bittornado/ipranges.portugal.txt.gz
/usr/share/doc/bittornado/NEWS.Debian.gz
/usr/share/doc/bittornado/README.txt.gz
/usr/share/doc/bittornado/README-Psyco.txt
/usr/share/doc/bittornado/changelog.Debian.gz
/usr/share/doc/bittornado/IMPORTANT-multitracker-readme.txt
/usr/share/doc/bittornado/README.Debian
/usr/share/icons/bittornado
/usr/share/app-install/desktop/bittornado.desktop
/usr/share/app-install/icons/_usr_share_pixmaps_bittornado.xpm
/usr/share/man/man1/btlaunchmanycurses.bittornado.1.gz
/usr/share/man/man1/btlaunchmany.bittornado.1.gz
/usr/share/man/man1/btrename.bittornado.1.gz
/usr/share/man/man1/btmakemetafile.bittornado.1.gz
/usr/share/man/man1/bittorrent-multi-downloader.bittornado.1.gz
/usr/share/man/man1/btcompletedir.bittornado.1.gz
/usr/share/man/man1/bittorrent-downloader.bittornado.1.gz
/usr/share/man/man1/btdownloadheadless.bittornado.1.gz
/usr/share/man/man1/btdownloadcurses.bittornado.1.gz
/usr/share/man/man1/bttrack.bittornado.1.gz
/usr/share/man/man1/btreannounce.bittornado.1.gz
/usr/share/man/man1/btshowmetainfo.bittornado.1.gz
/usr/lib/mime/packages/bittornado
/usr/bin/btreannounce.bittornado
/usr/bin/btcompletedir.bittornado
/usr/bin/bttrack.bittornado
/usr/bin/btshowmetainfo.bittornado
/usr/bin/btmakemetafile.bittornado
/usr/bin/btdownloadheadless.bittornado
/usr/bin/btdownloadcurses.bittornado
/usr/bin/btlaunchmanycurses.bittornado
/usr/bin/btlaunchmany.bittornado
/usr/bin/btrename.bittornado
/var/cache/apt/archives/bittornado_0.3.17-1_all.deb
/var/cache/apt/archives/bittornado-gui_0.3.17-1_all.deb
/var/lib/dpkg/info/bittornado.md5sums
/var/lib/dpkg/info/bittornado.prerm
/var/lib/dpkg/info/bittornado.postinst
/var/lib/dpkg/info/bittornado-gui.postrm
/var/lib/dpkg/info/bittornado-gui.list
/var/lib/dpkg/info/bittornado.list
/var/lib/dpkg/info/bittornado.postrm
/var/lib/menu-xdg/applications/menu-xdg/X-Debian-Apps-Net-bittornado_client.desktop


and if I do this:

> /usr/bin/btdownloadcurses.bittornado

it gives me arguments (--max_uploads etc.).

Oh wait, I think I see what you were trying to get me to do.....how do I know if it's doing anything since it works on the command line? I guess I could donwload the gui fromt end but.....

---

### Post by go_dragons on 2007-09-11
I already had my lamp server set up and since i will be going away for a while I decided to setup torrentflux for remote administration.

I first tried to install it using the traditional apt method, but after that did not work I consulted the forums and found this howto. This is no doubt a deicent howto for setting up torrentflux manually and it did help me edit some configuration files (although they were in a different location than in this tutorial), but I have reached a point where I am stuck. 

when I type 127.0.0.1/torrentflux into my browser I recieve the following error 

"Database error: Table 'torrentflux.tf_settings' doesn't exist"
I checked the directory cd /var/lib/mysql/torrentflux and found that it contains a file called db.opt. However you do have to be root to open the directory if that makes any differance.

To the best of my abilities I have completed all of the steps except for the one labled "And upload the torrentflux structure to MySQL" under step 4. I was unable to find the sql file using the locate command and I do not know where I need to go to get this. do I need to download the entire tarball and install it how it is written in this tutorial or is there any way of fixing what I have so far? Thanks in advance for any help!

---

### Post by mcdeath on 2007-09-11
> **kebes said:**
> Thanks for the update! I definitely didn't think about that. That's no doubt a bug in torrentflux, and I'll be sure to let others know if they run into it!

Happy torrenting!

Hey kebes me again, nothing serious so don't worry.
I'm just wondering why I can't get my torrents to obey the upload limit I'm placing on them.

Torrentflux is swamping my upload bandwidth.

I'm setting it to 1kb per torrent but it simply ignores whatever I put as a limit.

Bug?

---

### Post by kebes on 2007-09-11
> **go_dragons said:**
> "Database error: Table 'torrentflux.tf_settings' doesn't exist"

To the best of my abilities I have completed all of the steps except for the one labled "And upload the torrentflux structure to MySQL" under step 4. I was unable to find the sql file using the locate command and I do not know where I need to go to get this. do I need to download the entire tarball and install it how it is written in this tutorial or is there any way of fixing what I have so far? Thanks in advance for any help!

Yes, the problem is that you have a MySQL database called "torrentflux" but there is nothing in it! You need to generate the tables, as described in step 4.b "upload the torrentflux structure to MySQL". To get a copy of the file "mysql_torrentflux.sql" you can download a copy of torrentflux ([from here]("http://sourceforge.net/project/showfiles.php?group_id=123961")), untar it, and go into the "sql" subdirectory. There you will find the file you need.

Then go to the how-to and complete that step.


Actually, the file is just a text file of MySQL statements. I've copied it here (from the torrentflux 2.3 tarball) for your convenience. You can either download it as explained above, or save this code to a text file called "mysql_torrentflux.sql"
```

-- phpMyAdmin SQL Dump
-- --------------------------------------------------------

--
-- Table structure for table `tf_links`
--

CREATE TABLE `tf_links` (
  `lid` int(10) NOT NULL auto_increment,
  `url` varchar(255) NOT NULL default '',
  `sitename` varchar(255) NOT NULL default 'Old Link',
  `sort_order` tinyint(3) unsigned default '0',
  PRIMARY KEY  (`lid`)
) TYPE=MyISAM;

--
-- Dumping data for table `tf_links`
--

INSERT INTO `tf_links` VALUES (1, 'http://www.torrentflux.com', 'TorrentFlux.com', 0);

-- --------------------------------------------------------

--
-- Table structure for table `tf_log`
--

CREATE TABLE `tf_log` (
  `cid` int(14) NOT NULL auto_increment,
  `user_id` varchar(32) NOT NULL default '',
  `file` varchar(200) NOT NULL default '',
  `action` varchar(200) NOT NULL default '',
  `ip` varchar(15) NOT NULL default '',
  `ip_resolved` varchar(200) NOT NULL default '',
  `user_agent` varchar(200) NOT NULL default '',
  `time` varchar(14) NOT NULL default '0',
  PRIMARY KEY  (`cid`)
) TYPE=MyISAM AUTO_INCREMENT=1 ;

-- --------------------------------------------------------

--
-- Table structure for table `tf_messages`
--

CREATE TABLE `tf_messages` (
  `mid` int(10) NOT NULL auto_increment,
  `to_user` varchar(32) NOT NULL default '',
  `from_user` varchar(32) NOT NULL default '',
  `message` text,
  `IsNew` int(11) default NULL,
  `ip` varchar(15) NOT NULL default '',
  `time` varchar(14) NOT NULL default '0',
  `force_read` tinyint(1) default '0',
  PRIMARY KEY  (`mid`)
) TYPE=MyISAM AUTO_INCREMENT=1 ;


-- --------------------------------------------------------

--
-- Table structure for table `tf_rss`
--

CREATE TABLE `tf_rss` (
  `rid` int(10) NOT NULL auto_increment,
  `url` varchar(255) NOT NULL default '',
  PRIMARY KEY  (`rid`)
) TYPE=MyISAM AUTO_INCREMENT=1 ;

--
-- Dumping data for table `tf_rss`
--



-- --------------------------------------------------------

--
-- Table structure for table `tf_settings`
--

CREATE TABLE `tf_settings` (
  `tf_key` varchar(255) NOT NULL default '',
  `tf_value` text NOT NULL,
  PRIMARY KEY  (`tf_key`)
) TYPE=MyISAM;

--
-- Dumping data for table `tf_settings`
--

INSERT INTO `tf_settings` VALUES ('path', '/usr/local/torrent/');
INSERT INTO `tf_settings` VALUES ('btphpbin', '/var/www/TF_BitTornado/btphptornado.py');
INSERT INTO `tf_settings` VALUES ('btshowmetainfo', '/var/www/TF_BitTornado/btshowmetainfo.py');
INSERT INTO `tf_settings` VALUES ('advanced_start', '1');
INSERT INTO `tf_settings` VALUES ('max_upload_rate', '10');
INSERT INTO `tf_settings` VALUES ('max_download_rate', '0');
INSERT INTO `tf_settings` VALUES ('max_uploads', '4');
INSERT INTO `tf_settings` VALUES ('minport', '49160');
INSERT INTO `tf_settings` VALUES ('maxport', '49300');
INSERT INTO `tf_settings` VALUES ('rerequest_interval', '1800');
INSERT INTO `tf_settings` VALUES ('cmd_options', '');
INSERT INTO `tf_settings` VALUES ('enable_search', '1');
INSERT INTO `tf_settings` VALUES ('enable_file_download', '1');
INSERT INTO `tf_settings` VALUES ('enable_view_nfo', '1');
INSERT INTO `tf_settings` VALUES ('package_type', 'zip');
INSERT INTO `tf_settings` VALUES ('show_server_load', '1');
INSERT INTO `tf_settings` VALUES ('loadavg_path', '/proc/loadavg');
INSERT INTO `tf_settings` VALUES ('days_to_keep', '30');
INSERT INTO `tf_settings` VALUES ('minutes_to_keep', '3');
INSERT INTO `tf_settings` VALUES ('rss_cache_min', '20');
INSERT INTO `tf_settings` VALUES ('page_refresh', '60');
INSERT INTO `tf_settings` VALUES ('default_theme', 'matrix');
INSERT INTO `tf_settings` VALUES ('default_language', 'lang-english.php');
INSERT INTO `tf_settings` VALUES ('debug_sql', '1');
INSERT INTO `tf_settings` VALUES ('torrent_dies_when_done', 'False');
INSERT INTO `tf_settings` VALUES ('sharekill', '150');
INSERT INTO `tf_settings` VALUES ('tfQManager', '/var/www/TF_BitTornado/tfQManager.py');
INSERT INTO `tf_settings` VALUES ('AllowQueing', '0');
INSERT INTO `tf_settings` VALUES ('maxServerThreads', '5');
INSERT INTO `tf_settings` VALUES ('maxUserThreads', '2');
INSERT INTO `tf_settings` VALUES ('sleepInterval', '10');
INSERT INTO `tf_settings` VALUES ('debugTorrents', '0');
INSERT INTO `tf_settings` VALUES ('pythonCmd', '/usr/bin/python');
INSERT INTO `tf_settings` VALUES ('searchEngine', 'TorrentSpy');
INSERT INTO `tf_settings` VALUES ('TorrentSpyGenreFilter', 'a:3:{i:0;s:2:"11";i:1;s:1:"6";i:2;s:1:"7";}');
INSERT INTO `tf_settings` VALUES ('TorrentBoxGenreFilter', 'a:3:{i:0;s:1:"0";i:1;s:1:"9";i:2;s:2:"10";}');
INSERT INTO `tf_settings` VALUES ('TorrentPortalGenreFilter', 'a:3:{i:0;s:1:"0";i:1;s:1:"6";i:2;s:2:"10";}');
INSERT INTO `tf_settings` VALUES ('enable_maketorrent','0');
INSERT INTO `tf_settings` VALUES ('btmakemetafile','/var/www/TF_BitTornado/btmakemetafile.py');
INSERT INTO `tf_settings` VALUES ('enable_torrent_download','1');
INSERT INTO `tf_settings` VALUES ('enable_file_priority','1');
INSERT INTO `tf_settings` VALUES ('security_code','0');



-- --------------------------------------------------------

--
-- Table structure for table `tf_users`
--

CREATE TABLE `tf_users` (
  `uid` int(10) NOT NULL auto_increment,
  `user_id` varchar(32) NOT NULL default '',
  `password` varchar(34) NOT NULL default '',
  `hits` int(10) NOT NULL default '0',
  `last_visit` varchar(14) NOT NULL default '0',
  `time_created` varchar(14) NOT NULL default '0',
  `user_level` tinyint(1) NOT NULL default '0',
  `hide_offline` tinyint(1) NOT NULL default '0',
  `theme` varchar(100) NOT NULL default 'mint',
  `language_file` varchar(60) default 'lang-english.php',
  PRIMARY KEY  (`uid`)
) TYPE=MyISAM AUTO_INCREMENT=1 ;



--
-- Table structure for table `tf_cookies`
--

CREATE TABLE `tf_cookies` (
  `cid` int(10) NOT NULL auto_increment,
  `uid` int(10) NOT NULL,
  `host` varchar(255) default NULL,
  `data` varchar(255) default NULL,
  PRIMARY KEY  (`cid`)
) TYPE=MyISAM ;

```

---

### Post by kebes on 2007-09-11
> **mcdeath said:**
> Torrentflux is swamping my upload bandwidth.

I'm setting it to 1kb per torrent but it simply ignores whatever I put as a limit.

Bug?

Could be a bug. Try setting the value higher. I've used that limit in the past and it's always worked for me, but I've never tried using a value less than 10 kb ...

(Maybe even just using "2" or "1.1" will fix it?)

---

### Post by kebes on 2007-09-11
> **DarkDancer said:**
> I think I see what you were trying to get me to do.....how do I know if it's doing anything since it works on the command line? I guess I could donwload the gui fromt end but.....
You can download torrents from the commandline using that binary. It will show you a progress bar in the terminal and everything! If you have a torrent, like "file.torrent" then you just go:

```
btdownloadcurses.bittornado file.torrent
```

Then it will start torrenting that file. In the terminal, it will show you some stats, like peers, seeds, % complete, and upload/download speeds. You can also use:
```
btdownloadheadless.bittornado file.torrent
```
Which has a more minimal display.


Anyways, perhaps using the commandline version will provide some insight (maybe it will throw an error that is somehow useful).


I looked over your BitTornado files, and they look fine. It actually looks like you have the full BitTornado client installed (is that true?), which you don't need to make torrentflux work (it only needs some libraries). Still, they shouldn't interfere with each other, so I'm not sure what the problem is...

---

### Post by DarkDancer on 2007-09-11
Yes, I have the whole bittornado loaded. I tried out the command line and it works. It starts FAST too! No errors.

---

### Post by go_dragons on 2007-09-11
Thank you kebes! you have been overly helpful. Everything is working now and I am ready to start configuring. Thanks a lot.

---

### Post by kebes on 2007-09-14
> **DarkDancer said:**
> Yes, I have the whole bittornado loaded. I tried out the command line and it works. It starts FAST too! No errors.

Just to let you know: I tried a few different things but wasn't able to come up with a solution for you. I was looking at the torrenflux code, trying to reproduce the error you're seeing, but was not able to.

If you have any new information about the problem, let me know.

---

### Post by DarkDancer on 2007-09-14
No, nothing new to add.... I guess maybe I will try the install one more time.....later this evening or sunday or something....

---

### Post by DarkDancer on 2007-09-20
Well, I'm at a loss, I went through and reinstalled it one more time, same results. I even created the .BitTornado folder and gave www-data ownership, no chan ges, I think that unless you (or anyone) have any suggestions for me, I give up (at least for now...

---

### Post by kebes on 2007-09-20
> **DarkDancer said:**
> Well, I'm at a loss, I went through and reinstalled it one more time, same results. I even created the .BitTornado folder and gave www-data ownership, no chan ges, I think that unless you (or anyone) have any suggestions for me, I give up (at least for now...

No. I'm out of ideas on this one. I guess you could try installing [different versions]("http://sourceforge.net/project/showfiles.php?group_id=123961&package_id=135423") of torrentflux (v.2.1. instead of v.2.3.?). There's also a fork of torrentflux called [torrentflux-b4rt]("http://tf-b4rt.berlios.de/") that might work. The members of [that forum]("http://tf-b4rt.berlios.de/forum/") might be able to offer more expertise to get it working.

---

### Post by Akula on 2007-09-23
I'm having a problem after installing torrentflux:

First when trying to get into localhost/torrentflux I got not found error. I tried to fix it by restarting apache2. Now I'm getting FORBIDDEN error when trying to get into localhost/torrentflux with my browser. I checked permissions and all files under torrentflux folder on my server are owned by me (akula:akula) and files have permissions line like -rwxr--r-- and directories drwxr--r-- . does anyone have idea what is wrong here?

---

### Post by kebes on 2007-09-23
> **Akula said:**
> I'm having a problem after installing torrentflux:

First when trying to get into localhost/torrentflux I got not found error. I tried to fix it by restarting apache2. Now I'm getting FORBIDDEN error when trying to get into localhost/torrentflux with my browser. I checked permissions and all files under torrentflux folder on my server are owned by me (akula:akula) and files have permissions line like -rwxr--r-- and directories drwxr--r-- . does anyone have idea what is wrong here?

The directories need permissions like "drwxr--r-**x**". That final "x" means that anyone can "execute" the directory. For directories, you need execute permission in order to go inside them.

So you need to add that permission to the appropriate directories, so that the webserver can see the files. Probably something like:
```

cd /var/www/
chmod +x torrentflux
cd torrentflux
chmod +X -R *

```

---

### Post by Akula on 2007-09-23
Thank you, works now =)

---

### Post by mcdeath on 2007-09-28
File deletions, Kebes I have old torrents left over in my torrent directory I wish to delete but because the file names have spaces in them it tells me it cannot find the directory.

using command 'sudo rm -r'

Files with no spaces in their names delete just fine.

Help, I'm running out of drive space :-)

---

### Post by kebes on 2007-09-28
> **mcdeath said:**
> File deletions, Kebes I have old torrents left over in my torrent directory I wish to delete but because the file names have spaces in them it tells me it cannot find the directory.

using command 'sudo rm -r'

Files with no spaces in their names delete just fine.

Help, I'm running out of drive space :-)

You can delete files with spaces in their names in a couple of ways:

1. Open a file browser (Nautilus on Gnome, Konqueror on KDE), browse to the directory, and delete them with the GUI. If the directory in question is not owned by your user (and so you need higher privilege to delete them), you can open a root browser using "gksudo nautilus" or "kdesu konqueror".

Actually, it can be dangerous to open a root file browser (you might accidentally delete the wrong thing!) so it might be a better idea to change permissions so that your normal user account has write privilege...

2. You can delete the downloaded files from within TorrentFlux. Login, go to the "directory" tab at the top, navigate to the file you want, and click the red X for delete. Because TorrentFlux (user "www-data") made the files, it can delete them.

3. On the commandline, spaces are used to separate arguments, so you need to do something "special" to let the shell know what you mean. You can either use quotes around the file name, or use an "escape sequence"... So let's say you have a file called "file name" that you want to delete, you type:
```
rm "file name"
```
The quotes tell the shell that this is a single item. Alternately you could type:
```
rm file\ name
```
Where the "\ " means "a literal space"...

4. A neat trick for deleting files with spaces without worrying about the details is to use autocomplete. On a Linux shell, you can press the "tab" button and the shell will try to autocomplete the name for you... so if you type:
```
rm fil
```
and then press tab, the shell will complete it for you:
```
rm file\ name
```
(If there are multiple files that start the same way, the shell doesn't know which one you mean, so you have to type enough of it for it to know what you want. You can double-tap tab to force it to list possible matches.)


Hope that helps.

---

### Post by mcdeath on 2007-09-28
Thanks Kebes I'm freeing up space as we speak.  Have a great weekend.

---

### Post by don_poky on 2007-10-05
Hi,

I was installing torrentflux-b4rt 1.0beta1 on my site, the setup was
 smooth until the last step. screenshot linked...

[IMG]http://www.fillhd.com/2007-10-05_183414.jpg[/IMG]

I had to ignore that warnings coz i didnt know wot to do...
well, my next step was the First Login screen. I logged in then again a
 ERROR displayed as -

[COLOR="Blue"][IMG]http://www.fillhd.com/2007-10-05_190557.jpg[/IMG]

[B][COLOR="DarkRed"]{
allow_url_fopen disabled

tf-b4rt will not run flawless with this setting
PHP-setting : allow_url_fopen

}[/COLOR][/B]

[COLOR="Sienna"]Am hosting on DREAMHOST and read in many forums that they have disabled
 it for security issues.[/COLOR]

Then next... The script was ON i was glad, but the main problem am
 facing is while entering a URL of the .torrent file in the " URL for the
 Torrent File:" field and letting it to START its job.

[COLOR="Red"]Start failed[/COLOR]

transfer : Babylon_6.torrent

messages :
path for tftornado.py is not valid
tornadoBin : /var/www/bin/clients/tornado/tftornado.py[/COLOR]

I checked the files are there in their resp. places, i just extracted
 the file I got from the SOUNDFORGE site as .tar file.

How to rectify that problem. Please some1 help!!
I even used other clients from the drop-list......... NO LUCK!!

thanks!

---

### Post by kebes on 2007-10-05
> **don_poky said:**
> How to rectify that problem. Please some1 help!!

torrentflux-b4rt is somewhat different from torrentflux. I've never used torrentflux-b4rt so I have not seen the error messages you reported. Still, I'll give you my thoughts on the issue...

The first few errors are not critical. As the message says, those are just advanced features that are disabled. If you want to enable them, you can just install those missing packages. (You can install unrar and VLC and so on in the usual ways: use the "Add/Remove" function or Synaptic or aptitude.)


The other error is a switch in your PHP configuration. To change it, you need to edit the file "/etc/php5/apache2/php.ini" (this is assuming you are using PHP 5 and Apache 2, obviously...). Then in the file you need to search for the line that starts "allow_url_fopen" and make sure it reads:
```
allow_url_fopen = On
```
(If this line is entirely missing from the file, just add it.)


You mentioned "Dreamhost" which I guess means that you're trying to run Torrentflux off of a web hosting provider ([that doesn't allow that option to be set?]("http://wiki.dreamhost.com/index.php/Allow_url_fopen")). If you cannot access the php.ini file yourself, then you'll have to ask them to modify it for you. If they are not willing to do so, then there's not much that can be done (it would require significantly altering the PHP code).


You might get more precise info by posting your question to the b4rt forum:

[http://tf-b4rt.berlios.de/forum/](http://tf-b4rt.berlios.de/forum/)


I hope that helps.

---

### Post by dark_king on 2007-10-24
**[COLOR="Red"]hey people i am facing problem in downloading files larger than 2 gb on torrentflux . can any one help ?[/COLOR]**

---

### Post by kebes on 2007-10-24
> **dark_king said:**
> hey people i am facing problem in downloading files larger than 2 gb on torrentflux . can any one help ?
Additional details about your issue would help.

What do you mean by "problem"? Is the download slow? Is the final file corrupted? Will the download not start at all? What happens when you download smaller files?

Does the problem occur when you are downloading a single >2 Gb file, or when the total torrent size is >2 Gb (for example, you might be downloading a torrent that is >2 Gb but is internal split into separate rar files, or whatever), or both?

It might also be relevant to know what filesystem type you have running on the partition where you download the torrent files to (ext2? ext3? fat32?).

Are you able to create >2 Gb files on that partition in other ways? (What happens if you copy a large file onto that partition?)

---

### Post by dark_king on 2007-10-24
> **kebes said:**
> Additional details about your issue would help.

What do you mean by "problem"? Is the download slow? Is the final file corrupted? Will the download not start at all? What happens when you download smaller files?

Does the problem occur when you are downloading a single >2 Gb file, or when the total torrent size is >2 Gb (for example, you might be downloading a torrent that is >2 Gb but is internal split into separate rar files, or whatever), or both?

It might also be relevant to know what filesystem type you have running on the partition where you download the torrent files to (ext2? ext3? fat32?).

Are you able to create >2 Gb files on that partition in other ways? (What happens if you copy a large file onto that partition?)

thanks dude for replying .
when ever the size of the file is >2GB i face problem . for example i am downloading aa game of >2Gb .but it runs smoothly when it was internally spited (rar) but when ever i download the same file as .ISO then it shows that the file is downloading and uploading but when i check the file in directory it says the size of the file is 0.
i first thought that its the problem with iso but then i triex to download .exe file >2 Gb ... and the same problem. (ex americasarmy game )

---

### Post by kebes on 2007-10-24
> **dark_king said:**
> when ever the size of the file is >2GB i face problem . for example i am downloading aa game of >2Gb .but it runs smoothly when it was internally spited (rar) but when ever i download the same file as .ISO then it shows that the file is downloading and uploading but when i check the file in directory it says the size of the file is 0.

Hmm... Unfortunately I don't think there is a simple fix for this. Torrentflux is written in PHP. It appears that the default configuration of PHP doesn't support files over 2 Gb.

Some things to try:
-It is possible to recompile PHP to enable large file support (using 64-bit file offsets). This [PHP forum comment]("http://us3.php.net/manual/en/function.fopen.php#37791") explains briefly how to do that. But if you're not comfortable compiling software from source, this is not a good option.

-Make sure that your version of PHP, Apache, etc. are all up-to-date.

-There is a variant of Torrentflux called "b4rt", available here:
[http://tf-b4rt.berlios.de/](http://tf-b4rt.berlios.de/)
It seems that they might have fixed this error. You could post in their forums and see if anyone know whether tf-b4rt solves the >2 Gb filesize issue.

-A workaround, I guess, would be to use some other torrent program just for those big files, or to seek out torrents where the content has been sub-divided already.



Sorry that I can't offer a simple solution to this one. Good luck.

---

### Post by averagebeatboy on 2007-10-24
Worked beautifully, my friend.  A Huge Thank You!

I installed it on Ubuntu "Gutsy Ribbon" 7.10

Thanks again,

Averagebeatboy


[SIZE="2"]**Failure is not an option -- it comes with Windows**[/SIZE]

---

### Post by kebes on 2007-10-24
> **averagebeatboy said:**
> Worked beautifully, my friend.  A Huge Thank You!
Awesome! It's always nice to hear that things work! (Since most of the posts are related to the times when things don't work... :) ) Enjoy!

---

### Post by dark_king on 2007-10-25
is it necessery to instal python to run torrentflux on ubantu ?

---

### Post by kebes on 2007-10-25
> **dark_king said:**
> is it necessery to instal python to run torrentflux on ubantu ?

Yes, Python needs to be installed. (Torrenflux accesses BitTornado via Python scripts to do the actual downloading.)

Python is installed by default in Ubuntu.

---

### Post by Ian-on-the-Trent on 2007-10-26
Hey Kebes.  

Great job and effort sticking with this thread. **[A large round of applause =D>]**  You've been at it for quite a while and must be the *torrentflux guru* by now. Btw, I followed your steps to the letter on an old box with Dapper (650mhz Duron, 64mb RAM, 80GB HDD) and it worked like a charm. *(Now, if I could only figure out Apache and make this personal "server" functional and secure.)*

A question for all: Is there a way to pause and/or restart an upload/download with *torrentflux*?  Sometimes my kids want to play intensive online games on their computer but are getting booted because of competing bandwidth usage. (BF2...high ping.)  I really don't want to kill a 2GB download nor upload midstream.

Thanks.

---

### Post by kebes on 2007-10-26
> **Ian-on-the-Trent said:**
> Hey Kebes. Great job and effort sticking with this thread. ...  You've been at it for quite a while and must be the *torrentflux guru* by now.
Thanks! Yeah when I initially wrote this how-to, I never thought that I would end up being the "maintainer" for this topic... but it seems to be working out!

> A question for all: Is there a way to pause and/or restart an upload/download with *torrentflux*?

Basically yes. When a torrent is running, you can click "stop torrent" (red downward-facing arrow). The torrent will then be marked as "incomplete" but none of the data-so-far is deleted. If you later click "run torrent" (green downward-facing arrow), it will verify existing data and continue building the file from where it left off. It will just take a few moments for it to re-connect to the peers.

(Of course, this is assuming that the torrent you were previously using has not died in the meantime...)

---

### Post by Ian-on-the-Trent on 2007-10-26
LOL...thanks for the super-quick response.  You must live here. ;)

---

### Post by Ian-on-the-Trent on 2007-10-26
And on another function . . . can you make the user directory private so no-one other than the user can see what's inside?

Yet another question: how hack-proof is* torrentflux*?

---

### Post by kebes on 2007-10-26
> **Ian-on-the-Trent said:**
> can you make the user directory private so no-one other than the user can see what's inside?
When you say "user directory" do you mean your user home folder (/home/user/ or whatever) or do you mean the contents of each torrentflux user?

Assuming you mean the torrentflux user folders, it's not easy to keep them hidden/private. If you have multiple users in torrentflux, they can all see what the others have downloaded.

It's possible to have two (or more) different installations of torrentflux on the same machine (just put them in different folders and create distinct databases for each). So you could have a public copy that most people use, and keep a separate copy running for private/sensitive things.

On the Linux side, the directory where the downloads get stored (/var/www/torrentflux/downloads/ or whatever) will typically be readable by everyone. However if you want to make it less visible, you can set it (and all sub-dirs) to be owned by "www-data" using the "chown" command (this is probably already the case), and then set the permissions to be restrictive as well using "chmod". Something like:
```
cd /var/www/torrentflux
sudo chown www-data:www-data downloads -R
sudo chmod 600 downloads -R
sudo chmod u+X downloads -R
```

Once this is done, only the user "www-data" (the webserver) will be able to read or write into that directory. So to check the contents or copy a file out, you will have to use admin power via "sudo" (obviously anyone with sudo-power will be able to find the files).

You'll also need to secure apache a bit to prevent someone from browsing those directories (since the apache webserver can browse them). There is a directive you can set in apache's config to suppress listing directory contents.


> Yet another question: how hack-proof is* torrentflux*?

Interesting question. Torrentflux is a 'small-target' so it's unlikely many people are trying to hack it. I'm not aware of any major vulnerability in it, but it's entirely possible someone could exploit a flaw in it (true of all net-facing apps). Since torrentflux is run by the webserver, most hacks would be isolated to whatever directories the webserver can read/write.

So, I don't think it's a major worry, but you should in general not put important/sensitive files into directories that the webserver can read.

---

### Post by Ian-on-the-Trent on 2007-10-28
Thanks for all of your help Kebes.  Cheers!

---

### Post by cox377 on 2007-11-15
Hey All,

Been running a torrentflux box for about 9 months, however changed the password yesterday and somehow cannot remember it - this is the main password for geting into tflux

Does this relate anyway to the database password?

Basically, is there anyway of changing / resetting the password without having to reinstall the whole thing

Many Thanks

CoXen

---

### Post by kebes on 2007-11-15
> **cox377 said:**
>  is there anyway of changing / resetting the password without having to reinstall the whole thing

Yes, it can be done. Basically you just use the PHP function "md5" to create a hash of your new password, and manually copy this into the torrentflux MySQL database for that username.

For detailed instructions see this previous post:
[http://ubuntuforums.org/showpost.php?p=3305731&postcount=125](http://ubuntuforums.org/showpost.php?p=3305731&postcount=125)


If you have any questions about those steps, feel free to ask. Hope that works!

---

### Post by cox377 on 2007-11-15
> **kebes said:**
> Yes, it can be done. Basically you just use the PHP function "md5" to create a hash of your new password, and manually copy this into the torrentflux MySQL database for that username.

For detailed instructions see this previous post:
[http://ubuntuforums.org/showpost.php?p=3305731&postcount=125](http://ubuntuforums.org/showpost.php?p=3305731&postcount=125)


If you have any questions about those steps, feel free to ask. Hope that works!


If you could provide step by step that would be greatly appreciative

---

### Post by 3ntity on 2007-11-15
Hey,
I have torrentflux running on my server and was wondering whether there's any way of enabling downloading for a certain period of time, in my case from 2am-8am [due to stupid download limits imposed by ISP]. I was thinking of a cronjob or suchlike, but haven't found anything that does the job...

Thanks in advance,
3ntity

---

### Post by cox377 on 2007-11-15
Many thanks for that, was at work originally thus the reason why I didn't read your msg properly with the link

Much appreciated

CoXen

---

### Post by kebes on 2007-11-15
> **3ntity said:**
> Hey,
I have torrentflux running on my server and was wondering whether there's any way of enabling downloading for a certain period of time, in my case from 2am-8am [due to stupid download limits imposed by ISP]. I was thinking of a cronjob or suchlike, but haven't found anything that does the job...

Thanks in advance,
3ntity

The short answer is: No, there's no easy way to schedule that.


However, if you know how to code in PHP, you could write a simple PHP file to start all the downloads, and another one to stop all active downloads. Then you could have a cron job that activates the two PHP scripts.


An easier way might be to use the commandline version of BitTornado (the command is "btdownloadheadless", once you have it installed). You could write a simple shell script (that gets called by cron at 2am) that scans through a particular directory and launches instances of btdownload for each .torrent file.

Then cron could, at 8am, run something like "killall btdownloadheadless"...

---

### Post by 3ntity on 2007-11-19
> **kebes said:**
> The short answer is: No, there's no easy way to schedule that.


However, if you know how to code in PHP, you could write a simple PHP file to start all the downloads, and another one to stop all active downloads. Then you could have a cron job that activates the two PHP scripts.


An easier way might be to use the commandline version of BitTornado (the command is "btdownloadheadless", once you have it installed). You could write a simple shell script (that gets called by cron at 2am) that scans through a particular directory and launches instances of btdownload for each .torrent file.

Then cron could, at 8am, run something like "killall btdownloadheadless"...Thanks for the answer  :), i'll look into BitTornado when i have some time.

2 more questions: Does BitTornado allow selection of individual files to download from a .torrent, and is there something like a WebGUI available for it?
Thanks again,
3ntity

---

### Post by kebes on 2007-11-19
> **3ntity said:**
> Does BitTornado allow selection of individual files to download from a .torrent
Not that I know of. (You can search for info on "btdownloadcurses", "btdownloadheadless", and "btlaunchmany" but from the commandline options I don't see a way to select files.)

> is there something like a WebGUI available for it?
Well... that's exactly what Torrentflux is! :) 


I know your overall problem is you want some way to control the time-of-day when torrents run. But to get Torrentflux to do this will require some PHP or Python programming.

---

### Post by ronaldor9 on 2007-11-23
hey i got it all running up exect to online part  i already have apache and all that but i also want to use apache for anotehr website so how would i direct phpflux to a certain domain such as mmmmm.myvnc.com   without messing up my other sites
by the way what should i have in my apache2.conf file and ports to make this online

---

### Post by kebes on 2007-11-25
> **ronaldor9 said:**
> i also want to use apache for anotehr website so how would i direct phpflux to a certain domain such as mmmmm.myvnc.com   without messing up my other sites
You can control Apache's resolving of domain names by using Virtual Hosts. The exact details depend on exactly what you're trying to do, but if you search for "apache virtual hosts" you will get some good sites with explanations (e.g. [official docs]("http://httpd.apache.org/docs/1.3/vhosts/"), or [this one]("http://www.linux.com/feature/118471"), or [this one]("http://plone.org/documentation/tutorial/plone-apache/virtualhost")...). Again, it depends on your setup, but a typical thing to do would be to edit the file "/etc/apache2/sites-available/default". In that file, you can create different VirtualHost sections that catch different domain names, like so:
```

<VirtualHost *>
        ServerName mmmmm.myvnc.com
        ServerAlias mmmmm.myvnc.com
        DocumentRoot /var/www/some_directory/

        CustomLog /var/log/apache2/some_log_name.log combined
</VirtualHost>

```
Each VirtualHost section can be set to catch a different server name, and redirect to the appropriate web directory.

> by the way what should i have in my apache2.conf file and ports to make this online
Your apache configuration should be "visible" ... but you have to make sure that you unblock ("allow connections from") **port 80** in your Linux firewall and any hardware routers you are using. If you have apache installed, then your Linux firewall is probably not blocking port 80 (but if you've installed something like Firestarter, then you will have to use it to unblock port 80).

Routers will block all ports by default, so you will have to configure it to allow port 80 (it may be listed as something like "Application Forwarding" in the router interface).

Hope that helps.

---

### Post by 3ntity on 2007-11-30
> **kebes said:**
> [QUOTE=3ntity]2 more questions: Does BitTornado allow selection of individual files to download from a .torrent, and is there something like a WebGUI available for it?Well... that's exactly what Torrentflux is! :)[/QUOTE]LOL, that was stupid on my behalf ;) I didn't set up torrentflux on the server here at home, which i hope is at least some excuse for my ignorance, hehe...

---

### Post by 3ntity on 2007-12-01
Concerning scheduling, i found this [found [here]("http://forums.whirlpool.net.au/forum-replies-archive.cfm/835490.html")]:
> As for scheduling, I put this in the apache user's crontab:

```
crontab -e -u apache
30 2 * * * cd /var/www/html/torrentflux/bin && php fluxcli.php resume-all
30 12 * * * cd /var/www/html/torrentflux/bin && php fluxcli.php stop-all
```

Obviously update it to your times and torrentflux path.This seems like an easy solution, but: i can't find either torrentflux/bin OR fluxcli.php on the server... I typed:
```
$ sudo find / -name torrentflux
Password:
./var/lib/mysql/torrentflux
./files/web/torrentflux
$
```and```
$ sudo find / -name fluxcli.php
$ 
```Is this normal? Is there any way i could use abovementioned cronjobs for scheduling? 
Thx in advance... As soon as i get scheduling, it's torrentflux ftw...

**Edit:** Could it be above cronjobs only work with [Torrentflux-b4rt](http://tf-b4rt.berlios.de/)?

---

### Post by kebes on 2007-12-01
> **3ntity said:**
> Could it be above cronjobs only work with [Torrentflux-b4rt](http://tf-b4rt.berlios.de/)?

Yes, that appears to be a feature added in the b4rt version. I don't have any "fluxcli.php" file in my Torrentflux install, but I see that file is included in the torrentflux-b4rt release. So, it would seem that the b4rt version of torrentflux does what you want!

I'm pretty sure you can install that version in much the same way as regular Torrentflux (just put the files in a web sub-directory).

Good luck!

---

### Post by 3ntity on 2007-12-01
> **kebes said:**
> Yes, that appears to be a feature added in the b4rt version. I don't have any "fluxcli.php" file in my Torrentflux install, but I see that file is included in the torrentflux-b4rt release. So, it would seem that the b4rt version of torrentflux does what you want!

I'm pretty sure you can install that version in much the same way as regular Torrentflux (just put the files in a web sub-directory).

Good luck!Thx for the help :)
I'll give that a shot one of these days [when i have more time :/]... Sounds like the torrent-client seeking days for the server are counted! :P


**Update:** I succesfully installed Torrentflux-b4rt, which, in my opinion, seems quite a bit more developed/advanced than Torrentflux [i like, for instance, it's Ajax page refresh :D]. I haven't *actually* tried running a cronjob, but this should be no issue since
```
php /path/to/tf-b4rt/bin fluxcli.php stop-all
```and ```
php /path/to/tf-b4rt/bin fluxcli.php stop-all
``` do what they suggest. 
:D Great success!
Thanks for the help, kebes!

**YAUpdate:** The cronjob works without any issues; It has to be run as root tho...

---

### Post by 449 on 2008-01-07
> 4.d First login.
Now you can go to your torrentflux page, using a web-browser:
[http://localhost/torrentflux/](http://localhost/torrentflux/)


When I click the link at this point I get the this. 

[IMG]http://img410.imageshack.us/img410/6590/screenshot1wf0.png[/IMG]

Could someone help me sort this out please? :confused:

Thanks for your time and patience.

---

### Post by brago on 2008-01-08
Hi,
Hope that someone can help me with some issues I have with my torrentflux installation.

I did a clean installation of 7.10 server the other day. I had torrentflux working on my last installation and reused that database in the installation.

Installed torrentflux via sudo apt-get install torrentflux. During installation I got the message of libphp-adodb beeing moved from /usr/share/adodb to /usr/share/php/adodb and that I sould update any references to that in php.ini or the webserver config files. Don't know if this is what makes my installation not working. Because when I go to my torrentfluxsite, I get the following error message:

```
Warning: session_start() [function.session-start]: Cannot send session cache limiter - headers already sent (output started at /etc/torrentflux/config-db.php:2) in /usr/share/torrentflux/www/functions.php on line 27

Warning: Cannot modify header information - headers already sent by (output started at /etc/torrentflux/config-db.php:2) in /usr/share/torrentflux/www/functions.php on line 113
```

Any ideas of what I have done wrong?

Thanks
Stefan

---

### Post by kebes on 2008-01-08
> **449 said:**
> When I click the link at this point I get the this. 

At step 4a, it seems that you copied all the files in the torrentflux install folder, whereas you only need the files from the "html" sub-folder. There are two ways to fix this. First, you could just use this web-address instead:

[http://localhost/torrentflux/html/](http://localhost/torrentflux/html/)

This should work, since that's where you put the files.

Or, you could go to /var/www/torrentflux/ and move the files from the "html" sub-folder into /var/www/torrentflux/ (and get rid of the sql and upgrades sub-folders).

I hope that helps

---

### Post by kebes on 2008-01-08
> **brago said:**
> I get the following error message:

```
Warning: session_start() [function.session-start]: Cannot send session cache limiter - headers already sent (output started at /etc/torrentflux/config-db.php:2) in /usr/share/torrentflux/www/functions.php on line 27

Warning: Cannot modify header information - headers already sent by (output started at /etc/torrentflux/config-db.php:2) in /usr/share/torrentflux/www/functions.php on line 113
```

The "headers already sent" error message is almost always caused by having whitespace inside a PHP file outside of the delimiters. Check any files you've edited (like config-db.php) and make sure there is no whitespace (spaces, tabs, returns) before the "<?php" at the top, or after the final "?>".

For example this file would cause an error because of the spaces before the "<?php" at the top:
```
  <?php
   // A bunch of code...
?>

```
Just remove the whitespace and save the file.

---

### Post by brago on 2008-01-08
Brilliant! That worked! Thank you thank you thank you!

I had some spaces in the beginning of the config file, deleting them made everything work again.

/Stefan

---

### Post by 449 on 2008-01-08
> **kebes said:**
> At step 4a, it seems that you copied all the files in the torrentflux install folder, whereas you only need the files from the "html" sub-folder. There are two ways to fix this. First, you could just use this web-address instead:

[http://localhost/torrentflux/html/](http://localhost/torrentflux/html/)

This should work, since that's where you put the files.

Or, you could go to /var/www/torrentflux/ and move the files from the "html" sub-folder into /var/www/torrentflux/ (and get rid of the sql and upgrades sub-folders).

I hope that helps
Thanks that fixed it. But now I'm getting this:

Warning: mysql_connect() [function.mysql-connect]: Access denied for user 'www-data'@'localhost' (using password: NO) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 358

Database error: Access denied for user 'www-data'@'localhost' (using password: NO)

---

### Post by kebes on 2008-01-08
> **449 said:**
> Thanks that fixed it. But now I'm getting this:

Warning: mysql_connect() [function.mysql-connect]: Access denied for user 'www-data'@'localhost' (using password: NO) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 358

Database error: Access denied for user 'www-data'@'localhost' (using password: NO)

This is a very strange error.

Did you use the address [http://localhost/torrentflux/html/](http://localhost/torrentflux/html/) or did you move the files out of the html sub-folder?


First thing to double-check is that your config file has the correct information for the MySQL database that you've created (username, password, database name).

If you moved the files out of the html folder, try moving them back in (and use the [http://localhost/torrentflux/html/](http://localhost/torrentflux/html/) path) and see if that fixes it.


It's also possible that your database somehow was broken because you moved files. If you know how to use MySQL, check the entries in the tf_settings table that have paths in them, and make sure they are right.

If you don't know much about MySQL, you could try deleting the entire torrentflux database and recreating it (using the script file, just like you did before), and see if that fixes it.

---

### Post by 449 on 2008-01-08
> **kebes said:**
> This is a very strange error.

Did you use the address [http://localhost/torrentflux/html/](http://localhost/torrentflux/html/) or did you move the files out of the html sub-folder?


First thing to double-check is that your config file has the correct information for the MySQL database that you've created (username, password, database name).

If you moved the files out of the html folder, try moving them back in (and use the [http://localhost/torrentflux/html/](http://localhost/torrentflux/html/) path) and see if that fixes it.


It's also possible that your database somehow was broken because you moved files. If you know how to use MySQL, check the entries in the tf_settings table that have paths in them, and make sure they are right.

If you don't know much about MySQL, you could try deleting the entire torrentflux database and recreating it (using the script file, just like you did before), and see if that fixes it.

The first time I tried the link and it didn't work so I moved the to where you said. I guess I'll just start it over then.

Didn't work.

---

### Post by 449 on 2008-01-08
Just a thought, does the fact that I use Swiftweasel have anything to do with it? :confused:

---

### Post by brago on 2008-01-09
Hi again,
all looked great with my installation after the previous help, until I tried download. And got som error message in the admin page.

I can not find the btphptornado.py, btshowmetainfo.py and btmakemetafile.py. Are they supposed to be installed with torrentflux or do I need to be installed seperately?

/Stefan

---

### Post by kebes on 2008-01-09
> **449 said:**
> Just a thought, does the fact that I use Swiftweasel have anything to do with it? :confused:

No, I doubt it.

> **449 said:**
> The first time I tried the link and it didn't work so I moved the to where you said. I guess I'll just start it over then.

Didn't work.

The error you're getting is quite strange. If you search back through this thread, you'll see someone else had it. You can try the various suggestions that were mentioned there... but I think it might actually have to do PHP or MySQL's configuration.

If you haven't already, you should try starting from scratch: delete the torrentflux folder and the MySQL database, and start back at step 1.

---

### Post by kebes on 2008-01-09
> **brago said:**
> And got som error message in the admin page.
Knowing the exact error message would help.

> I can not find the btphptornado.py, btshowmetainfo.py and btmakemetafile.py. Are they supposed to be installed with torrentflux or do I need to be installed seperately?

They should be included in the installation. Specifically in the "TF_BitTornado" sub-directory. When you copied the torrentflux files to /var/www/ did you make sure to do a recursive copy (copy the contents of all sub-directories!)?

If you find that the directory /var/www/torrentflux/TF_BitTornado is empty, you should go back to the "file copying" step and make sure that you copy everything, including sub-directories.

---

### Post by freymann on 2008-01-23
I thought I would give Torrent-Flux I try. I am running ubuntu 7.10. I used synaptic package manager to do the installation, and I already had a working LAMP system.

The system "works" as long as I download and save the *.torrent file and then manually upload it to the web interface. After that is shows up in the queue, I activate it, it downloads and seeds fine.

I can't do any searches at PirateBay without an error:

Parse error: syntax error, unexpected T_CLASS expecting T_FUNCTION in /usr/share/torrentflux/www/searchEngines/PirateBayEngine.php on line 833

Searching at the other sites produces results, but I am unable to download ANY torrent, all I get is:

Error getting the file (download.asp.torrent), Could be a Dead URL

I went to the forums and downloaded the latest torrentspy search engine script, same thing. Downloaded the latest piratebay search engine php script, still has same error.

My search engine scripts had the same version number as those in the forums.

I decided this system wasn't for me and completely uninstalled the thing this morning. I'll continue to use uTorrent on my Vista box for torrent downloading.

I thought you may be interested in my experience. As I say, if I wanted to manually feed it the *.torrent file it works but that kinda takes away from the 'ease of use' when you can't utilize the built-in search and download functions.

---

### Post by datablitz7 on 2008-01-26
This is one amazing How-To. I'm a total noob at linux and managed to make it work with this excellent tutorial. 

Thank you so much for your help!

---

### Post by nazeemlinux on 2008-01-27
> **tee2 said:**
> Hi all, I have a problem.

When I browse to [http://localhost/test.php](http://localhost/test.php), firefox tries to save the php file and doesn't load it in the browser like it should. What could be the problem? I installed php5 and php5-mysql so I don't know why things won't work. :confused:

There have been a mistyping while entering the PHP codes for test.php.Re-check the codes and try!

---

### Post by Loetje on 2008-01-29
Thanks for the great how-to, really usefull.
I got really far, but the last problem i can't fix is executing the mysql_torrentflux.sql command. I installed the file using aptitude install torrentflux but now I can't find the sql file. Since I am somehow not able tot install phpmyadmin and i'm installing on a remote server using SSH i have to use command line.

---

### Post by kebes on 2008-01-29
> **Loetje said:**
> Thanks for the great how-to, really usefull.
I got really far, but the last problem i can't fix is executing the mysql_torrentflux.sql command. I installed the file using aptitude install torrentflux but now I can't find the sql file. Since I am somehow not able tot install phpmyadmin and i'm installing on a remote server using SSH i have to use command line.

If you install using aptitude, I think the MySQL database is created automatically (working from memory here...).

If you need to get the "mysql_torrentflux.sql" file, you can extract it from the manual install file, which is [here]("http://sourceforge.net/project/showfiles.php?group_id=123961").

Or, just check out [this previous comment]("http://ubuntuforums.org/showpost.php?p=3348034&postcount=195") I wrote, where I put a copy of the file.

Hope that helps.

---

### Post by Loetje on 2008-01-30
Thanks for the reply.
I finally managed to figure it out using a different php admin program.
You were right about the fact that aptitude install torrentflux already loads the mysql_torrentflux.sql but this part of the installation failed because 'root@localhost' didn't have permissions. Maybe anyone can explain what to do about that, in case somebody else comes across this problem...

---

### Post by MarkyMarc on 2008-02-02
I've finally gotten Torrentflux running (it took almost 2 weeks).
Once I got it running I was directed to the setting page where I'm asked to define the path where my downloads will go. 
So I enter ```
chmod 777 /var/torrentflux/downloads
```
just as it should be. 

I keep getting the error message:"path is not valid"
I've tried different variations, different folders. Nothing changes.

I checked to see if this folder existed, sure enough, it does.
I've also gone through Terminal and chmod'd this folder from there.
It still won't go through on Torrentflux's end.

I know absolutely nothing about Linux (hence, 2 week installation).
Any help is **unbelievably** appreciated!!

---

### Post by kebes on 2008-02-03
> **MarkyMarc said:**
> 
So I enter ```
chmod 777 /var/torrentflux/downloads
```
just as it should be. 

I keep getting the error message:"path is not valid"
I've tried different variations, different folders. Nothing changes.

A couple different things could be causing the error. First off, are you entering the path properly. You wrote "/var/torrentflux/downloads" but it should be "/var/**www**/torrentflux/downloads**/**".

I'm assuming your torrentflux directory is in /var/www/ (otherwise you wouldn't be able to reach it at all), but perhaps you just entered the wrong path in the settings?



If that's not the problem, then try creating another directory (e.g. /var/www/torrentflux/files/) and see if it will accept that. Again, make sure that this directory is "chmod 777"... and you can also make it "chown www-data:www-data" as well. See if that works.

---

### Post by MarkyMarc on 2008-02-03
> **kebes said:**
> A couple different things could be causing the error. First off, are you entering the path properly. You wrote "/var/torrentflux/downloads" but it should be "/var/**www**/torrentflux/downloads**/**".

I'm assuming your torrentflux directory is in /var/www/ (otherwise you wouldn't be able to reach it at all), but perhaps you just entered the wrong path in the settings?



If that's not the problem, then try creating another directory (e.g. /var/www/torrentflux/files/) and see if it will accept that. Again, make sure that this directory is "chmod 777"... and you can also make it "chown www-data:www-data" as well. See if that works.

First of all, thank you very much for the punctual response!

So, I actually had it as /var/www/torrentflux/. I forgot to write that in my post.

I made a new directory:
```
 mkdir /var/www/torrentflux/downloads/files/
```

The problem persists. 

I'd love to try you second suggestion but I'm not sure how to implement the 'chown' command as described.

Thanks again!

Any ideas?

---

### Post by kebes on 2008-02-03
> **MarkyMarc said:**
> 
I made a new directory:
```
 mkdir /var/www/torrentflux/downloads/files/
```

The problem persists. 



Try something like:
```

cd /var/www/torrentflux/
mkdir files
chmod 777 files
sudo chown www-data:www-data files

```
And see if torrentflux will accept the path "/var/www/torrentflux/files/" (don't forget that trailing slash!).

If that doesn't work, then check the parent directories and make sure they are accessible by torrentflux, too:
```

cd /var/www/
ls -laF | grep "torrentflux"
cd /var/
ls -laF | grep "www"

```
The above commands should return something like:
```

drwxr-xr-x 12 username username 4096 2007-09-08 16:23 torrentflux/
drwxr-xr-x 12 root root 4096 2007-09-08 16:23 www/

```
The important part is that those directories are readable and executable by everyone. Notice that they are set "drwxr-xr-x". If they are set to something wrong, like "drwxr-x---" then you need to fix that with "chmod" like:
```

cd /var/www/
chmod 755 torrentflux

```

(I doubt this is the problem, since it seems like you can access torrentflux... but you never know...) If this isn't working, then post the results of the above commands to this thread.

---

### Post by MarkyMarc on 2008-02-03
Ok, here's what I entered:
```

cd /var/www/torrentflux/
mkdir files
chmod 777 files
chown www-data:www-data files

```
and as far as I can tell, it went according to plan. No error messages.

Next:
```

cd /var/www/
ls -laF | grep "torrentflux"
```
This was the response:
```
drwxr-xr-x 10 root     root     4096 2008-02-03 08:42 torrentflux/
```

I then entered:
```
cd /var/
ls -laF | grep "www"

```
To this response:
```
drwxr-xr-x  4 root root  4096 2008-01-27 20:47 www/

```


I then went to check Torrentflux; it still doesn't work.
Quite strange.

---

### Post by kebes on 2008-02-03
And so, just to be clear, you then went to torrentflux > admin > settings, and set path to "/var/www/torrentflux/files/" and clicked "Update Settings", right?

And it still says "Path is not Valid" ?? I would double-check that you're entering the path properly (even a space at the beginning or end, that you might not immediately notice, could break it). You can post a screenshot if you want.

You could also double-check that your new setting is actually being properly written into the MySQL database. If you have PHPMyAdmin installed, just check the "tf_settings" table in the database "torrentflux". On the commandline, this will also work (assuming you've used the default names for all the MySQL stuff):
```

echo "SELECT tf_value FROM tf_settings WHERE tf_key='path';" | mysql -uroot -p torrentflux
```
(You will have to enter your MySQL root password; which may not be the same as your Linux root password.) That command should return:
```

tf_value
/var/www/torrentflux/downloads/

```
If not, then there's a problem!



Also note that there can be problems if you try to put the download directory on a Windows partition (FAT32 or NTFS) or redirect it using symlinks. It sounds like you're not doing anything like that, though...

---

### Post by MarkyMarc on 2008-02-03
I clicked on 'update setting', of course.
I entered:
```

echo "SELECT tf_value FROM tf_settings WHERE tf_key='path';" | mysql -uroot -p torrentflux
```
This was the response:
```
tf_value
chmod 777 /var/www/torrentflux/downloads/files/

```


Here's a screen shot:
[img]http://img338.imageshack.us/img338/156/torrentfluxya4.png[/img]


Thanks again for all you patience and hard work!!!!

---

### Post by kebes on 2008-02-03
Ah! I see the problem. You set the path to:
```

chmod 777 /var/www/torrentflux/downloads/files/

```

But the path should be:
```

/var/www/torrentflux/downloads/files/

```

(The "chmod 777" is only what you would write on the Linux commandline to change the mode of the directory... it is not part of the path name.)

Try changing that and see if it works.

---

### Post by MarkyMarc on 2008-02-03
> **kebes said:**
> Ah! I see the problem. You set the path to:
```

chmod 777 /var/www/torrentflux/downloads/files/

```

But the path should be:
```

/var/www/torrentflux/downloads/files/

```

(The "chmod 777" is only what you would write on the Linux commandline to change the mode of the directory... it is not part of the path name.)

Try changing that and see if it works.
How do I do that? LOL

---

### Post by kebes on 2008-02-03
> **MarkyMarc said:**
> How do I do that? LOL

Which part?

First, in Torrentflux, go to Admin > Settings and change the path to "/var/www/torrentflux/downloads/" and click "Update Settings."

Does it still give an error? It should be ok. If it says "Path is not writeable" then in a terminal, do this:
```

cd /var/www/torrentflux/
chmod 777 downloads

```
And it should work.

---

### Post by MarkyMarc on 2008-02-03
> **kebes said:**
> Which part?

First, in Torrentflux, go to Admin > Settings and change the path to "/var/www/torrentflux/downloads/" and click "Update Settings."

Does it still give an error? It should be ok. If it says "Path is not writeable" then in a terminal, do this:
```

cd /var/www/torrentflux/
chmod 777 downloads

```
And it should work.
I still get "Path is not Valid"

The part I didn't understand was, how to change the path from
```
chmod 777 /var/www/torrentflux/downloads/files/
```

to:
```
/var/www/torrentflux/downloads/files/
```

---

### Post by kebes on 2008-02-03
> **MarkyMarc said:**
> I still get "Path is not Valid"

The part I didn't understand was, how to change the path from
```
chmod 777 /var/www/torrentflux/downloads/files/
```

to:
```
/var/www/torrentflux/downloads/files/
```
In the torrentflux web-admin panel, clear all the text from the path textbox (select everything "chmod...files/" and press delete). Then enter the correct path, "/var/www/torrentflux/downloads/files/" and click "Update Settings".

Does that answer your question or am I missing the mark?

---

### Post by MarkyMarc on 2008-02-03
> **kebes said:**
> In the torrentflux web-admin panel, clear all the text from the path textbox (select everything "chmod...files/" and press delete). Then enter the correct path, "/var/www/torrentflux/downloads/files/" and click "Update Settings".

Does that answer your question or am I missing the mark?

I changed it to:
```
/var/www/torrentflux/downloads/
```

AND NOW IT WORKS!!!!!!!!!! AAAHAHAHAHAHAHA!
:guitar:

You are the man! 
I'd give you a tip if i could!

---

### Post by kebes on 2008-02-03
> **MarkyMarc said:**
> 
AND NOW IT WORKS!!!!!!!!!! AAAHAHAHAHAHAHA!

Awesome! Glad it's fixed now!

> 
I'd give you a tip if i could!
Ha! The closest thing is clicking on the "thank" link! :)

Anyways, have fun with torrentflux!

---

### Post by MarkyMarc on 2008-02-03
One last thing, sir:

Any advice on tweaking upload speeds?
My download speeds are unbelievable, but my upload speed isn't much better than dial up.

---

### Post by kebes on 2008-02-03
> **MarkyMarc said:**
> One last thing, sir:

Any advice on tweaking upload speeds?
My download speeds are unbelievable, but my upload speed isn't much better than dial up.

First thing is to go into torrentflux settings (Admin > Settings), and there is an option for "Max Upload Rate." You can set that higher if you need to (10-30 KB/s is pretty low... depending on your net connection you might want to increase it to 80-200 KB/s).


If that's not enough, then this usually means that the router on your home network has a firewall that is blocking ports. The fix for this depends on your exact router, but here's an outline:
1. Go into torrentflux, Admin > Settings and set "Port Range" to some range above 1024 (for example 35000 to 36000).

2. Log into your router admin panel. This depends on the router (check your manual), but usually involves going to a special web address like [http://192.168.0.1/](http://192.168.0.1/) and then entering the username/password for the router (again check the docs).

3. Find an option for "Advanced Networking" or "Port Forwarding" or "Application Firewall Rules" or something like that. Then, set a "port forward" by opening the port range you've chosen (35000-36000 or whatever) and set the "destination IP address" to the internal IP of your computer (which will be something like 192.168.0.100 or whatever... you can use the linux command "ifconfig" to find out your internal IP).



That's it. With the ports open, bit-torrent will be much, much faster. If you need more info, let me know or do a web-search for "bittorrent port open" and you'll find various guides.

Good luck!

---

### Post by MarkyMarc on 2008-02-03
> **kebes said:**
> First thing is to go into torrentflux settings (Admin > Settings), and there is an option for "Max Upload Rate." You can set that higher if you need to (10-30 KB/s is pretty low... depending on your net connection you might want to increase it to 80-200 KB/s).


If that's not enough, then this usually means that the router on your home network has a firewall that is blocking ports. The fix for this depends on your exact router, but here's an outline:
1. Go into torrentflux, Admin > Settings and set "Port Range" to some range above 1024 (for example 35000 to 36000).

2. Log into your router admin panel. This depends on the router (check your manual), but usually involves going to a special web address like [http://192.168.0.1/](http://192.168.0.1/) and then entering the username/password for the router (again check the docs).

3. Find an option for "Advanced Networking" or "Port Forwarding" or "Application Firewall Rules" or something like that. Then, set a "port forward" by opening the port range you've chosen (35000-36000 or whatever) and set the "destination IP address" to the internal IP of your computer (which will be something like 192.168.0.100 or whatever... you can use the linux command "ifconfig" to find out your internal IP).



That's it. With the ports open, bit-torrent will be much, much faster. If you need more info, let me know or do a web-search for "bittorrent port open" and you'll find various guides.

Good luck!
I'm actually renting a dedicated server from Leaseweb. So I'm not so sure that a router would apply. Am I wrong?

---

### Post by kebes on 2008-02-03
> **MarkyMarc said:**
> I'm actually renting a dedicated server from Leaseweb. So I'm not so sure that a router would apply. Am I wrong?

You're right, a dedicated host won't have a simple router, and in any case shouldn't be blocking ports (but it might depend on the plan you have with them).

You can check with your server provider and see if they have any suggestions. Is it possible that whatever torrent you were using just wasn't in high demand?

Another thing to note: In torrentflux there is a little "light" to the left of a torrent that is downloading. If it is green, this means you are not being port-blocked, and everything is okay. If it is red or yellow, this means that the torrent/swarm is bad, or that your ISP is blocking ports from you.

---

### Post by MarkyMarc on 2008-02-03
> **kebes said:**
> You're right, a dedicated host won't have a simple router, and in any case shouldn't be blocking ports (but it might depend on the plan you have with them).

You can check with your server provider and see if they have any suggestions. Is it possible that whatever torrent you were using just wasn't in high demand?

Another thing to note: In torrentflux there is a little "light" to the left of a torrent that is downloading. If it is green, this means you are not being port-blocked, and everything is okay. If it is red or yellow, this means that the torrent/swarm is bad, or that your ISP is blocking ports from you.

Ok, so I'm going to assume that it's because that no one is leaching it from me.

Strange though, that when I do get leachers, it goes so slow.

---

### Post by mikwig on 2008-02-03
I found the easiest way to install it (providing you already have a working mysql)
is to download the archive from the torrentflux site ([www.torrentflux.com](www.torrentflux.com)) and
extract it to a subfolder of your apache webserver folder (/var/www by default).

it is slightly more work than the deb, but maintenance is much easier

---

### Post by Ahmedmb on 2008-03-02
THX
Very good tutorial

But i have proplim

php files not open it start download

i flow ur replay ro Deiz

Then check in:
/etc/apache2/mods-enabled/
And make sure there are symlinks to those two files.

i cant find this files how to creat Thim??

THX

---

### Post by kebes on 2008-03-02
> **Ahmedmb said:**
> php files not open it start download

Then check in:
/etc/apache2/mods-enabled/

i cant find this files
The problem you describe means that PHP5 for Apache2 is not installed properly. Take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=236721"), which gives suggestions and fixes.

To summarize some things to try:
1. Make sure PHP5 is installed:
```
sudo aptitude install php5
sudo /etc/init.d/apache2 restart
```

2. If PHP5 was already installed, try uninstalling and reinstalling.
```
sudo aptitude remove php5
sudo aptitude install php5
sudo /etc/init.d/apache2 restart
```

3. Explicitly install the PHP5 module for Apache2:
```
sudo aptitude install libapache2-mod-php5
sudo /etc/init.d/apache2 restart
```


A very important thing to remember is that Apache and/or your web-browsing might be caching pages, so even after it is fixed it might still seem "wrong." Each time you change something, you should restart Apache, and reload your browser. Also try forcing your browser to refresh (in Firefox, hold SHIFT while clicking the refresh button).

---

### Post by bwisdom on 2008-03-08
Hello,

I have done torentflux before an a previous server install, but I had to reinstall to fix a different problem (connection issues) anyway the reinstall didnt fix any problems because its turned out to not be a server problem. That isn't the problem (nor the scope of this thread) the problem is that now that I try to reinstall torrentflux via sudo aptitude it give me this error:


Warning: mysql_connect() [function.mysql-connect]: Access denied for user 'www-data'@'localhost' (using password: NO) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 358

TorrentFlux Database/SQL Error
Database error: Access denied for user 'www-data'@'localhost' (using password: NO)

Always check your database variables in the config.php file.

Now this is strange because when I installed it before I used to sudo aptitude method and it worked just fine. I had ubuntu 7.10 lamp fresh install when I had set it up the first time and I have the same setup now and it doesnt work. Hopefully someone knows or has had this error before? I can dl torrents on my comp and ftp to my server but thats getting old.

---

### Post by kebes on 2008-03-09
> **bwisdom said:**
> Warning: mysql_connect() [function.mysql-connect]: Access denied for user 'www-data'@'localhost' (using password: NO) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 358

TorrentFlux Database/SQL Error
Database error: Access denied for user 'www-data'@'localhost' (using password: NO)

Hopefully someone knows or has had this error before?

I've never had this error myself, but two other users have posted to this thread with that same error. You can check back through the thread history, and try the various suggestions... but I don't know if those users were ever able to fix the problem.

You may end up having to completely remove the install and re-install it. If that doesn't work, you can also try uninstalling it and doing a manual install (see the first post in this thread, which is a how-to).

You could also post a question to the [TorrentFlux forums]("http://www.torrentflux.com/forum/index.php"). They may have seen the problem already.

Sorry I don't have a good answer for you.

---

### Post by rakudave on 2008-03-18
i ran into the same problem, reinstalled everything, modified configs etc, etc...
the 'solution' was quite simple though: 'malicious' torrents

perhaps malicious is the wrong word, but one torrent made with azureus always killed my torrentflux-home (fored php-file download). after deleting the torrent in question (your_download_dir/.torrent) everything was fine again...

hope this helps

---

### Post by PurposeOfReason on 2008-03-20
I'm having a bit of trouble with the no-ip part. Because I'm cursed with a DSL gateway connected to a router, all the IP's come up the same. Now I didn't think that would cause a problem as I can connect to it through LAN fine and in theory, only one of the computers has the /torrentflux at the end of the IP. But when I run http://<snip>.com/torrentflux, I get nothing. Just
404 Not Found
The requested URL '/torrentflux' was not found on this server.

---

### Post by freymann on 2008-03-20
> **PurposeOfReason said:**
> I'm having a bit of trouble with the no-ip part. Because I'm cursed with a DSL gateway connected to a router, all the IP's come up the same.

 If I understand you correctly, you're saying that if you check your outside IP number, the one that is "live" on the internet, on computers behind the DSL gateway, all computers show the same "live" internet IP #?

 That is correct :-)

 Behind the router though, you should be using some other IP Block. In order to not see the 404 Not Found error message when you try to go to http://<snip>.com/torrentflux, you must instruct the router to direct requests for port 80 (the "web" or http requests) to the internal IP address of the computer that is running TorrentFlux.

 This type of configuration has been discussed at great length in many threads. 

 From your response, that is what I "assume" ;-) is happening to you...

---

### Post by PurposeOfReason on 2008-03-20
I'm pretty sure that's it. But I've already forwarded port 80 for 192.168.1.5 which I get from here
```
eth0      Link encap:Ethernet  HWaddr 00:06:5B:81:A4:19  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::206:5bff:fe81:a419/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:65024 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62357 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:51018402 (48.6 MiB)  TX bytes:23435786 (22.3 MiB)
          Interrupt:185 Base address:0x4c00 
```
However, if I just go to http://<snip>.serveftp.com/ it works and takes me the the DSL gateway configuration screen (after login). I can even enter the direct ip/torrenflux and it won't work.

---

### Post by buchan on 2008-03-21
Sorry, this is a pretty old thread but I just downloaded and installed the latest version and I thought I should share my problem... 

All the basic parts worked, Apache, MySQL, php etc but for some reason I could only download one torrent at a time with torrentflux.  

Because I'm used to using a client like Deluge that will allow you to run all of your connections through one port I narrowed the port range to that one port to match the firewall rules I had already set up.  Unfortunately Torrentflux needs **one port per torrent**

If you narrow the range to only the one port you can only download one torrent at a time.

Looking back it seems pretty simple...

---

### Post by freymann on 2008-03-21
> **PurposeOfReason said:**
> I'm pretty sure that's it. But I've already forwarded port 80 for 192.168.1.5

 What happens if you try to get to the program on the local machine?

 [http://localhost/torrentflux/](http://localhost/torrentflux/)

 I guess the outside world isn't going to see it if you can't get to it from the local machine. Check to ensure apache is running, check your log files, etc.

 Once you confirm it works locally then you start looking more into the router and your port forwarding.

---

### Post by PurposeOfReason on 2008-03-21
I can confirm that is all working. Heck, I can get there from this computer if I enter it's lan address. It's when I either use no-ip or a direct IP that it fails.

---

### Post by freymann on 2008-03-21
> **PurposeOfReason said:**
> I can confirm that is all working. Heck, I can get there from this computer if I enter it's lan address. It's when I either use no-ip or a direct IP that it fails.

 That means the next place to look is:

1) Your router

-- make sure it is forwarding port 80 to your machine's internal IP

2) Your "domain" resolution

-- make sure your internet domain is pointing to your router's IP number

 If you can load the torrentflux web page locally, then those two items listed above would be the reasons why you can't load the page from the outside world.

---

### Post by PurposeOfReason on 2008-03-22
I just put the gateway into bridge mode and all is working. Now I'm just having the problem that when I search with torrentflux no results show up. It says there are pages, but nothing is there.

---

### Post by freymann on 2008-03-22
> **PurposeOfReason said:**
> I just put the gateway into bridge mode and all is working. Now I'm just having the problem that when I search with torrentflux no results show up. It says there are pages, but nothing is there.

 Glad that worked for you. :-)

 The searching thing can be solved by installing curl. If you use the Synaptic Package Manager and search for curl you should find it. I think it may even be called php5-curl? Install that and restart and you should find the searches work.

 I would also suggest you go to the forums where they maintain those search engines and download and install the latest versions of the search engines you want to use. Many corrections have been made.

---

### Post by djh82uk on 2008-03-22
I am having this exact same problem, can anyone shed any light?

DJH


> **freymann said:**
> I thought I would give Torrent-Flux I try. I am running ubuntu 7.10. I used synaptic package manager to do the installation, and I already had a working LAMP system.

The system "works" as long as I download and save the *.torrent file and then manually upload it to the web interface. After that is shows up in the queue, I activate it, it downloads and seeds fine.

I can't do any searches at PirateBay without an error:

Parse error: syntax error, unexpected T_CLASS expecting T_FUNCTION in /usr/share/torrentflux/www/searchEngines/PirateBayEngine.php on line 833

Searching at the other sites produces results, but I am unable to download ANY torrent, all I get is:

Error getting the file (download.asp.torrent), Could be a Dead URL

I went to the forums and downloaded the latest torrentspy search engine script, same thing. Downloaded the latest piratebay search engine php script, still has same error.

My search engine scripts had the same version number as those in the forums.

I decided this system wasn't for me and completely uninstalled the thing this morning. I'll continue to use uTorrent on my Vista box for torrent downloading.

I thought you may be interested in my experience. As I say, if I wanted to manually feed it the *.torrent file it works but that kinda takes away from the 'ease of use' when you can't utilize the built-in search and download functions.

---

### Post by freymann on 2008-03-22
> **djh82uk said:**
> I am having this exact same problem, can anyone shed any light?


 How 'bout me? ;-)

 Install php-curl or just curl or whatever it is called.

 Then go to the forums, where the author of the search engine you want maintains their code... download the latest. Ignore the time stamps, they update the code as they code. What you get there will likely always be more current than what you got when you installed through ubuntu.

 And that's it! I guess I should edit my post to include these details. I'm now using TorrentFlux full-time.

---

### Post by djh82uk on 2008-03-22
hmm, I have php-curl installed, and I have the latest searchengine module (1.06) for piratebay, 

Also there is that problem with trying to download torrents through torrent flux and getting the download error :(

DJH

---

### Post by freymann on 2008-03-23
> **djh82uk said:**
> hmm, I have php-curl installed, and I have the latest searchengine module (1.06) for piratebay, 

Also there is that problem with trying to download torrents through torrent flux and getting the download error :(

DJH

 I downloaded the search engine code directly from the support forum and installed it and it works. It says 1.06 and that may match yours, but download it anyway... I believe small changes have been made to the script over time but the version number hasn't changed.

---

### Post by djh82uk on 2008-03-23
hiya thats also where I got mine, and it's deffo that one which is in use :(

DJH

---

### Post by PurposeOfReason on 2008-03-23
> **djh82uk said:**
> hiya thats also where I got mine, and it's deffo that one which is in use :(

DJH
Browse that thread. There is a "fixed" one on it that I'm using. Works perfectly.

---

### Post by djh82uk on 2008-03-23
Thats really great thanks, it worked :)

Just gotta have a go at the others now

Thanks a lot :)

DJH

---

### Post by Nebetsu on 2008-03-25
I think I broke my torrentflux. Whenever I go to the index.php, it can't display it, but when I go to any other page, it's fine.

Anyone know how to fix this?

---

### Post by freymann on 2008-03-25
> **Nebetsu said:**
> I think I broke my torrentflux. Whenever I go to the index.php, it can't display it, but when I go to any other page, it's fine.

Anyone know how to fix this?

 You should probably get in the habit of making a backup copy before you start to fiddle ;-)

 I don't know if my version is the same as yours but you're welcome to either "diff" it or just use it...

 Since you've mucked it up then I assume you know it goes in 

/usr/share/torrentflux/www

 ?

(at least that's where mine is)

---

### Post by Nebetsu on 2008-03-25
> **freymann said:**
> You should probably get in the habit of making a backup copy before you start to fiddle ;-)

 I don't know if my version is the same as yours but you're welcome to either "diff" it or just use it...

 Since you've mucked it up then I assume you know it goes in 

/usr/share/torrentflux/www

 ?

(at least that's where mine is)

Didn't work. Plus I didn't change anything in index.php. It just stopped working after I tried to get it to grab a .torrent file to download something.

EDIT: Nevermind. I got it. One of the .torrent files was messing up. I finally figured out it was in downloads/.torrents. I deleted it and now everything's good again.

---

### Post by Cheat King on 2008-04-15
Hey, I get the error:

Warning: mysql_connect() [function.mysql-connect]: Access denied for user 'torrentflux'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 365

when I go to [http://localhost/torrentflux/](http://localhost/torrentflux/).

Can you help me?

---

### Post by kebes on 2008-04-15
> **Cheat King said:**
> Warning: mysql_connect() [function.mysql-connect]: Access denied for user 'torrentflux'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 365

Most of the time this error is because the password you have set for your MySQL database is different than what you set in your torrentflux config file.

Check out step 4.c. from the [how-to instructions]("http://ubuntuforums.org/showpost.php?p=1566206&postcount=1").

Basically, you need to create a new user in MySQL for torrentflux. Once that's done, you edit the file "/var/www/torrentflux/config.php" and change the values so that username and password in that file match the values you put into MySQL.

---

### Post by Cheat King on 2008-04-15
When I enter:

INSERT INTO user (Host,User,Password) VALUES('localhost','torfluxuser',PASSWORD('secret'));

I get:

ERROR 1062 (23000): Duplicate entry 'localhost-torfluxuser' for key 1

---

### Post by kebes on 2008-04-15
> **Cheat King said:**
> ERROR 1062 (23000): Duplicate entry 'localhost-torfluxuser' for key 1

That means that you already have the proper user in the MySQL table. So, since you know you have a user called "torfluxuser" (and I presume you know the password you set), you can go to the next step and edit the config file:
```
sudo nano /var/www/torrentflux/config.php
```

In that file, you should set the values for the username and password:
```

$cfg["db_user"] = "root";        // username for your MySQL database
$cfg["db_pass"] = "secret";            // password for database

```
Of course, replace "secret" with whatever you actually set as the password. Save the file (Ctrl+O in nano), exit the editor (Ctrl+X in nano), and then try to access [http://localhost/torrentflux/](http://localhost/torrentflux/) again.

---

### Post by Cheat King on 2008-04-15
I have done that but I still get the same error:

Warning: mysql_connect() [function.mysql-connect]: Access denied for user 'torrentflux'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 365

Thanks for your help btw.

---

### Post by kebes on 2008-04-15
> **Cheat King said:**
> I have done that but I still get the same error:

Warning: mysql_connect() [function.mysql-connect]: Access denied for user 'torrentflux'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 365

Thanks for your help btw.

Do a quick [search back through this thread]("http://www.google.com/search?hl=en&q=Access+denied+for+user+torrentflux+site%3Aubuntuforums.org&btnG=Search"). Other people have reported similar error messages... and one of those solutions might work for you.

It would also help to have more information about your setup. Did you install using synaptic (or apt-get), or did you do a manual install? Were you following the directions in this how-to? If you can also provide some what your config.php file looks like (but change the password), and maybe a listing of files and permissions, using
```
ls -laFR /var/www/torrentflux/
```
(Again you may need to cut parts of the output to protect your privacy.)

Briefly, the things I'm looking for are:
1. Is your configuration actually using the /var/www/torrentflux/config.php file? The error message says user "torrentflux" but you mentioned user "torfluxuser" as being in the database. If your config.php file specifies "torfluxuser" but the error still says "torrentflux" then this is strange. You should try changing the user specified in config.php (to, e.g., "wrong") and see if that changes anything.
2. Depending on what install method you used, the actual config file may be elsewhere. Try using "locate torrentflux" and see if there is another "config.php" file somewhere.
3. File permissions in your torrentflux directory may be wrong. The webserver (user "www-data") needs to be able to access the files. You can use chmod to change permissions.
4. Starting over with a clean install (and carefully following the steps in the how-to) often fixes everything.

---

### Post by Cheat King on 2008-04-15
I just changed the file to:

$cfg["db_name"] = "wrong"; // Name of the Database
$cfg["db_user"] = "wrong";        // username for your MySQL database
$cfg["db_pass"] = "wrong";            // password for database

And I still get:

Warning: mysql_connect() [function.mysql-connect]: Access denied for user 'torrentflux'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 365


Does this mean there is another config file? I'll try to locate it now.

EDIT: I have found another config file:

/usr/share/torrentflux/www/config.php

The info says:

include_once("/etc/torrentflux/config-db.php");
$cfg["db_type"] = $dbtype;       // mysql, postgres7 view adodb/drivers/
$cfg["db_host"] = $dbserver;     // DB host computer name or IP
$cfg["db_name"] = $dbname;       // Name of the Database
$cfg["db_user"] = $dbuser;       // username for your MySQL database
$cfg["db_pass"] = $dbpass;       // password for database

I'll edit it now.

YAY! That  error has now gone and I only have this one:

Database error: Access denied for user 'torfluxuser'@'localhost' to database 'torrentflux'

Always check your database variables in the config.php file.

---

### Post by kebes on 2008-04-15
> **Cheat King said:**
> 
Database error: Access denied for user 'torfluxuser'@'localhost' to database 'torrentflux'

Always check your database variables in the config.php file.

Progress!

Assuming you didn't make a typo editing your config file, then what's probably happening is that you have a MySQL user called "torfluxuser" and you have a database called "torrentflux", but you don't have a *permission* set for "torfluxuser" to access "torrentflux".

To fix this, you can use any MySQL tool (e.g. MySQL Admin or phpmyadmin) and alter the "privileges". On the commandline, you would fix it like so:

```

mysql -uroot -p
mysql> GRANT SELECT,INSERT,UPDATE,DELETE,CREATE,DROP ON torrentflux.* TO 'torfluxuser'@'localhost';
mysql> FLUSH PRIVILEGES;
mysql> exit;

```

That should make the required update to the database.

---

### Post by PurposeOfReason on 2008-04-19
I'm having a problem with apache2 I believe. I can do the test page and it loads, but when I log into torrentflux I get a white page. If I'm using firefox it asks me to download the index.php but the login works fine. I've already purged and removed torrentflux, apache2 mysql and php5 as well as reinstalling them.

Any ideas?

---

### Post by djh82uk on 2008-04-20
Sounds like a problem with PHP talking with apache to me, there is a module to make sure is installed, but cannot remember the name, I think it was in the ubuntu howto for php /LAmp

DJH

---

### Post by Thirtysixway on 2008-05-01
Does anyone know how to upgrade torrentflux?  I installed using this guide (not sudo apt-get install torrentflux) and so I have version 2.1 installed, but the latest version is 2.3.

I can't find documentation on how to do this. :(

---

### Post by kebes on 2008-05-01
> **Thirtysixway said:**
> Does anyone know how to upgrade torrentflux?
Download the torrentflux tar.gz file from [the homepage]("http://www.torrentflux.com/"), and extract the tarfile in the usual way ("tar -xvzf torrentflux_2.3.tar.gz").

In the newly created directory, you will see a file called INSTALL. If you go down to the seciton marked "Upgrading from Previous Versions of TorrentFlux", you'll see the detailed instructions you need to perform the installation:
> 
-----------------------------------------------------------------
Upgrading from Previous Versions of TorrentFlux
-----------------------------------------------------------------
IMPORTANT: Remember to always backup your database before any
upgrade -- just in case.  If you run into problems, a clean
install never hurt anyone.

1. Rename your config.php file to config.old.php or something
like that so you can look at it when entering settings in the new
config.php file.

2. Copy all the new files over your old ones including the
themes and subdirectories.

3. Edit the new config.php to contain the settings needed.

4. IMPORTANT: To upgrade a previous TorrentFlux installation
to this new version you need to select the correct upgrade file
from the upgrades directory.  Place the upgrade file in your
web root with your config.php file and launch your web browser
to that file:

    [http://www.yourdomain.com/upgrade22_23.php](http://www.yourdomain.com/upgrade22_23.php)

All the database changes will be added and updated automatically
without touching your old data.  You should delete the upgrade
PHP file after it has run and performed the upgrade.

5. It is important that you use the new TF_BitTornado along with
the new btphptornado.py file.  You should also clean up the old
TF_BitTornado from your previous version of TorrentFlux.



If you have any questions about the steps, feel free to ask! Hope that helps.

---

### Post by Thirtysixway on 2008-05-01
Thanks!  That answers my questions except one,

I have 2.1 installed.  Do I need to go 2.1 => 2.2 => 2.3 or can I go 2.1 => 2.3?

---

### Post by kebes on 2008-05-01
> **Thirtysixway said:**
> Thanks!  That answers my questions except one,

I have 2.1 installed.  Do I need to go 2.1 => 2.2 => 2.3 or can I go 2.1 => 2.3?

You upgrade it in steps. So, in your case, you would do:

1. Backup your config.php file.
2. Copy over all the files from the install package html/ directory to your torrentflux install (over-writing your previous files).
3. Edit the new config.php file with your old config settings.
4. From the install package upgrade/ directory, copy the file upgrade21_22.php to your torrentflux folder (/var/www/torrentflux/ or whatever).
5. Visit:
[http://localhost/torrentflux/upgrade21_22.php](http://localhost/torrentflux/upgrade21_22.php)
6. Click "YES".
7. From the install package upgrade/ directory, copy the file upgrade22_23.php to your torrentflux folder.
8. Visit:
[http://localhost/torrentflux/upgrade22_23.php](http://localhost/torrentflux/upgrade22_23.php)
9. Click "YES".
10. Click "Done".
11. Delete the two upgrade files from your torrentflux folder.

---

### Post by Thirtysixway on 2008-05-01
Worked!  Thanks! :)

---

### Post by mcdeath on 2008-05-02
Kebes could you tell me how I stop Torrentflux from starting when I  startup my box? I want to try another client for awhile but don't want to un-install Torrentflux.

Any advice helps.

---

### Post by iSplicer on 2008-05-02
Excellent. Thanks!

---

### Post by kebes on 2008-05-02
> **mcdeath said:**
> Kebes could you tell me how I stop Torrentflux from starting when I  startup my box?

No need to uninstall Torrentflux.

Torrentflux doesn't really start-up when you boot up your machine. It only 'starts' when you visit the torrentflux interface and start a download.

So, as long as you stop all active torrents, then Torrentflux won't be running anymore. It won't interfere with any other bit-torrent client you install or run.

---

### Post by mcdeath on 2008-05-03
Thank you very much kebes your are always most helpful, this thread would be nothing without your input.

Be well my friend.

---

### Post by DrGiz on 2008-05-22
OK first can I say how much this guide has helped me, there is no way I could have setup TF without it. Saying that I am having a problem with one aspect of the program. the only way I can access it and control my torrents is to VNC into my server and do it in the Ubuntu web browser. Can I set it up so that I can control my torrents from any browser on any PC.

---

### Post by kebes on 2008-05-22
> **DrGiz said:**
> the only way I can access it and control my torrents is to VNC into my server and do it in the Ubuntu web browser. Can I set it up so that I can control my torrents from any browser on any PC.

Yes you should be able to.

You probably need to open a port on your router, and possibly switch your webserver to a non-standard port (e.g. switch to 8080 instead of the standard 80). Take a look at step 2 from the how-to, and follow those guidelines.

Let me know which steps work and which don't. For instance, I'm assuming it works when you go to:
[http://localhost/torrentflux/](http://localhost/torrentflux/)

But what happens when you try to access:
[http://xxx.xxx.xxx.xxx/torrentflux/](http://xxx.xxx.xxx.xxx/torrentflux/)
(where the xxx.xxx.xxx.xxx is your external IP address). Try it on the actual computer, and then from some other computer. What are the results?

---

### Post by DrGiz on 2008-05-23
thanks for getting back to me kebes. 

so far I have port 80 forwarded to the internal server IP address, which is 192.168.1.153.

I also have my download ports for ft, 63000-65000, forwarded to 192.168.1.153.

With those settings I can access tf  through both localhost/torrentflux and xxx.xxx.xxx.xxx. but only on the server via VNC or direct.

---

### Post by kebes on 2008-05-23
> **DrGiz said:**
> I have port 80 forwarded to the internal server IP address. With those settings I can access tf  through both localhost/torrentflux and xxx.xxx.xxx.xxx. but only on the server via VNC or direct.

Many internet providers block port 80. So it might just be that. On your actual machine, if you go to [http://localhost/](http://localhost/) you should probably see an apache test page (or directory listing). What happens if you go to [http://xxx.xxx.xxx.xxx](http://xxx.xxx.xxx.xxx) from another computer. If you don't see the test page, then that probably means your internet provider is blocking port 80.

If so, try the steps in [2b of the how-to]("http://ubuntuforums.org/showthread.php?t=268985"). That explains how to switch your server to using a non-standard port, which often fixes the problem.



P.S.: The firewall on your computer might also be blocking. If you installed something like Firestarter, then it may have turned off port 80, in which case you should unblock it.

---

### Post by DrGiz on 2008-05-23
ive set it to 8080, if i go to localhost on the server i get the "It Works" message the same if i do it with my external IP. If I try the same from another machine on the network via its external IP address.

I have just found out though that it is avaiable on the network via [http://192.168.1.153/torrentflux/login.php](http://192.168.1.153/torrentflux/login.php)

---

### Post by gausie on 2008-06-02
Hi!

I'm trying to get my torrentflux to save to a different, mounted, harddrive.

I can access it fine, and the permissions are set identically to the currently working download directory, but for some reason it won't let me.

I want to save to "/home/me/Downloads/Video/TV/UNSORTED/"

I tried making a symbolic link in the torrentflux directory, and that didn't work either

I get the message "Path is not valid" :(

Any suggestions

Gausie

---

### Post by kebes on 2008-06-02
> **gausie said:**
> I can access it fine, and the permissions are set identically to the currently working download directory, but for some reason it won't let me.

I want to save to "/home/me/Downloads/Video/TV/UNSORTED/"

I tried making a symbolic link in the torrentflux directory, and that didn't work either

I get the message "Path is not valid"

Some things to check are:

1. Make sure the path is writeable. I know you said that you set the permissions... but you have to make sure that the entire path is traversable by the web-server. Even if a sub-directory is writeable, the server can't access it if the parent directory is protected.

This means that the download directory (UNSORTED) should have permissions set to "drwxrwxrwx" (777), and the parent directories should be "drwxr-xr-x" (755). Fixing it would invovle something like:

```
cd /home/me/Downloads/Video/TV/
chmod 777 UNSORTED
cd ..
chmod 755 TV
cd ..
chmod 755 Video
cd ..
chmod 755 Downloads
cd ..
chmod 755 me

```

2. If that doesn't work, you could also try explicitly setting the ownership of the directory. Torrentflux will run as user "www-data". So:
```
cd /home/me/Downloads/Video/TV/
chmod 777 UNSORTED
sudo chown www-data:www-data UNSORTED

```

3. Make sure you put a trailing slash, "/", at the end of the path in the torrentflux settings.

4. I don't know if this applies to you, but the download directory cannot be stored on a FAT32 or NTFS partition. It needs to be a Linux filesystem.


Hopefully one of those suggestions will sort it out!

---

### Post by jonthysell on 2008-06-09
> **kebes said:**
> Addendum:

I think it's not too difficult to change the password in the torrentflux MySQL database. Torrentflux uses the "md5" command in PHP to generate an md5 hash of the password you supply. So you can do the same thing.

Let's say you want your new password to be "secret" (without the quotes). This is what you do. First create a php file like this:
```

cd /var/www/
nano md5.php

```
In the file, put this simple code:
```

<?php
print md5("secret")
?>

```
Then when you check the page [http://localhost/md5.php](http://localhost/md5.php) you'll see the hash:
```

5ebe2294ecd0e0f08eab7690d2a6ee69

```
Copy that hash string and save it somewhere. (For security reasons, you should promptly delete the md5.php file.)

Now update the database, and put that new hash in place of the old one. This is very easy to do with the web-based "phpmyadmin" utility. If you don't have phpmyadmin, you can do it the commandline way:
```

mysql -uroot -p

```
(Enter your **MySQL root** password.) Then enter these MySQL commands:
```

mysql> USE torrentflux;
mysql> UPDATE tf_users SET password="5ebe2294ecd0e0f08eab7690d2a6ee69" WHERE uid=1;
mysql> quit;

```

This changes the password of the first torrentflux user (uid 1) to what you've chosen.

Obviously, instead of "secret" you put the password you want, and instead of the hash "5ebe..." you put the one that you got from the md5.php page you made.

Thanks a million, chose a new password with a single quote ' in it, guess they don't sanitize their inputs, cause I couldn't log back in.

---

### Post by PurposeOfReason on 2008-06-28
Everything has been working fine for some time now, but there is this one torrent that I uploaded to my torrent box and I can't remove it. It wouldn't start so I choose delete and nothing happens, it's just sitting on the index.php page doing nothing.

Another, possibly related problem, is when I try to delete this one file from my directory list I get this error.
```
**Warning**:  chmod() [[function.chmod]("http://192.168.1.5/torrentflux/function.chmod")]: No such file or directory in **/usr/share/torrentflux/www/functions.php** on line **82**

**Warning**: Cannot modify header information - headers already sent by (output started at /usr/share/torrentflux/www/functions.php:82) in **/usr/share/torrentflux/www/dir.php** on line **78
```**

---

### Post by kebes on 2008-06-28
> **PurposeOfReason said:**
> there is this one torrent that I uploaded to my torrent box and I can't remove it. when I try to delete this one file from my directory list I get this error.
```
**Warning**:  chmod() [[function.chmod]("http://192.168.1.5/torrentflux/function.chmod")]: No such file or directory in **/usr/share/torrentflux/www/functions.php** on line **82**

**Warning**: Cannot modify header information - headers already sent by (output started at /usr/share/torrentflux/www/functions.php:82) in **/usr/share/torrentflux/www/dir.php** on line **78
```**

There is probably something wrong with the torrent file (possibly just the filename contained characters that TorrentFlux couldn't process). But you should be able to just manually delete the .torrent file.

Let's say we want to get rid of "Bad_File.torrent". First, go to your torrentflux download directory, which is probably:
```

cd /var/www/torrentflux/downloads/

```
Then enter into the hidden ".torrents" sub-directory, which is where all the status information is stored:
```

cd .torrents

```
Now delete the .torrent file, and the associated status file:
```

sudo rm Bad_File.torrent
sudo rm bad_file.stat

```

After refreshing TorrentFlux, the file should be gone from the listing.

Hope that works!



P.S.: Sometimes you can fix bad torrent files just by renaming them--TorrentFlux sometimes has problems with some "bad" characters (like quotes).

---

### Post by PurposeOfReason on 2008-06-28
/var/www only contains a index.html so I went to /usr/share/torrentflux/www/downloads and still nothing was there.

---

### Post by kebes on 2008-06-28
> **PurposeOfReason said:**
> /var/www only contains a index.html so I went to /usr/share/torrentflux/www/downloads and still nothing was there.

To find out what the current download directory is, log into torrentflux, and then go to "Admin" (there's a link at the top), and then "Settings". The first setting is "Path", which is the download directory.

Go to that directory, and then follow the rest of the instructions.


(Remember that the .torrent sub-directory is hidden. So from the commandline you'll have to use something like "ls -laF" to see it. If you're using a GUI file browser, you'll need to have "show hidden files/directories" turned on.)

---

### Post by PurposeOfReason on 2008-06-28
Thank you, it worked. I still had to go in and manually remove the one file from my directory list but that takes two seconds.

---

### Post by jcr1 on 2008-06-30
hope someone can help me, bit of a n00b.

I get as far as getting the test php working, but te when I try to add the password i get the following error:

```
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

```

I am trying to set this up logged remotely via ssh if it means anything. I just have the one user on the server.

---

### Post by kebes on 2008-06-30
> **jcr1 said:**
> ```
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

```

This probably means that you already have a password set for the MySQL root user. If so, just skip this step. Of course, you'll need to know what that password is for steps 4b and 4c.

(If you're installing torrentflux on a shared hosting server of some kind, it's possible that you won't have access to the MySQL root account. That's fine, as long as you are able to create MySQL databases and users.)

Let me know if you have any other questions.

---

### Post by jcr1 on 2008-07-01
I cannot remember if or when I created a mysql password. 

My setup is a simple home file server, that only I access. I have only one user setup on it, which is me, the admin, set up when ubuntu was installed.

I had installed LAMP before, via synaptic, but since looking at this tutorial have aptitude installed each component, to make sure I had the right things definately installed.

Is there a way to reset the password?

Thanks for your reply.

---

### Post by kebes on 2008-07-01
> **jcr1 said:**
> I cannot remember if or when I created a mysql password. 

Is there a way to reset the password?

Yes, you can change the MySQL root password. Refer to the instructions [here]("http://mirror.yandex.ru/mirrors/ftp.mysql.com/doc/refman/5.0/en/resetting-permissions.html#resetting-permissions-unix") or [here]("http://en.wikibooks.org/wiki/MythTV/Troubleshooting#I_lost_my_MySQL_password"); Ubuntu-specific instructions can be found [here]("http://ubuntu.flowconsult.at/en/mysql-set-change-reset-root-password/") and [here]("http://www.jusupov.com/2008/01/18/how-to-reset-mysql-root-password-in-ubuntu-linux/").

Basically, this is what you do (all these commands should be typed into a [terminal]("http://www.psychocats.net/ubuntu/terminal")):

1. Stop the MySQL server process:
```
sudo /etc/init.d/mysql stop
```
(It will prompt you for your Linux user/admin password.)

2. Restart MySQL, without user authentication:
```
sudo mysqld --skip-grant-tables &
```
3. Login to MySQL as root (no password required):
```
mysql -u root mysql
```
4. Change the root user's password (to "supersecret" in this example). Enter each of these three commands:
```
 UPDATE user SET Password=PASSWORD('supersecret') WHERE User='root';
 FLUSH PRIVILEGES;
 exit;
```
5. Restart MySQL server:
```
sudo /etc/init.d/mysql restart
```


After that, you should be able to use "mysql" and "mysqladmin" with the new password.

Hope that helps.

---

### Post by jcr1 on 2008-07-01
Excellent! Thank you so much! Got this working now...

---

### Post by jcr1 on 2008-07-01
sorry one little question, when you chmod 777 the downloads folder to enable write access in the final few steps, I assume I could enter any directory there where I would like my downloads to go? or does it have to be within /var/www/?

For example, could I stick it in my home directory?

---

### Post by kebes on 2008-07-01
> **jcr1 said:**
> sorry one little question, when you chmod 777 the downloads folder to enable write access in the final few steps, I assume I could enter any directory there where I would like my downloads to go? or does it have to be within /var/www/?

For example, could I stick it in my home directory?

Yes, in principle you can select any directory you want. The default is "/var/www/torrentflux/downloads/", but you can change that once torrentflux is installed by loggin-in and going to "admin" > "settings" and change "Path" to whatever you've chosen.

Notes about using a non-standard download folder:
* Your download folder must be on a Linux partition (e.g. ext3) and not a mounted Windows partition (e.g. NTFS).
* The web server (user "www-data") must be able to read/traverse the path to the download folder. So you for example if you are using "/home/bob/downloads/" as the path, you must make sure that "/home/bob/" can at least be read by the webserver (permissions "drwxr-xr-x") and that the download folder can be written to (permissions "drwxrwxrwx").

---

### Post by jcr1 on 2008-07-02
Thanks for that. A question about user www-data. I moved a file I downloaded to its final resting place (from /var/www/to../dow.../ to /home/me/whatever/) and its permissions are such that it is readable, but I can't delete it because it is owned by www-data. 

How do I make this so it is just a standard file, with permissions for me to delete it if necessary.

Would I have to chown all downloads everytime to me ?

---

### Post by kebes on 2008-07-02
> **jcr1 said:**
> How do I make this so it is just a standard file, with permissions for me to delete it if necessary.

The first thing to note is that you can delete the files within Torrentflux. Just click on "directory" (at the top), and you'll get a file listing, with a delete button (red X) for each file.

If you want to manually delete the files, you can use "sudo rm" (be careful with that command!), or you can use "sudo chown" to change the ownership or "sudo chmod 777" to give full permissions.

You could also set up a script that uses cron to periodically fix the file permissions, so that the files are "normal" by the time you need to move/delete them.



Not a perfect fix, I know.

---

### Post by freymann on 2008-07-02
> **kebes said:**
> The first thing to note is that you can delete the files within Torrentflux. Just click on "directory" (at the top), and you'll get a file listing, with a delete button (red X) for each file.


 Wow! I had no idea you could delete the downloaded files from within TorrentFlux! 

 Much easier than SSH'ing into the box and using the manual 'sudo rm' command.

 Great tip!

---

### Post by jcr1 on 2008-07-03
yep, all solution are fine. Thanks very much. This works really well!

---

### Post by herbster on 2008-08-01
I'm trying to get this going currently on my home server, getting blank php pages. I have php working (localhost/test.php is fine) and mysql (mythbox runs great) but php in the torrentflux dir isn't playing nice, all pages are just blank. I'm using Arch linux, just to save anyone time from posting Ubuntu-specific commands, but any ideas would be good.

EDIT: Blasted "Indexes" needed to be added to the Directory part of httpd.conf! Works :)

---

### Post by kebes on 2008-08-01
> **herbster said:**
> I have php working (localhost/test.php is fine) and mysql (mythbox runs great) but php in the torrentflux dir isn't playing nice, all pages are just blank.
Is the page truly blank or empty? I presume the page looks entirely white, with no text. What happens if you look at the page source? Is there anything there, or is it a totally empty document? The source may provide some clues.

One possibility is that you are getting some kind of PHP error, but that your PHP is configured to suppress error reporting. You can determine if this is the case by inserting an error into your "/var/www/test.php" file:
```

<html>
<head>
  <title>Test Page</title>
</head>
<body>
Test page<br />
<?php
        echo 'If you can see this text, then PHP is working.';
        not_a_real_function();
?>
</body>
</html>

```
When you visit the page, you should see the error:
```
Fatal error: Call to undefined function not_a_real_function() in /var/www/test.php on line 9
```
If you don't see that error, then it's probably because PHP error reporting is turned off. You can turn error reporting on by editing your php.ini file (probably located at "/etc/php5/apache2/php.ini"), and looking for the line with "error_reporting". It's probably current set to "error_reporting = 0"... Setting it like so will produce more error output:
```
error_reporting  =  E_ALL & ~E_NOTICE
```
(More info [here]("http://us3.php.net/manual/en/function.error-reporting.php") and [here]("http://ist.marshall.edu/ist263/l27.html").)

My guess is that once you see the PHP error, it will be something simple to fix (like a MySQL user/password typo or something).

Hope that helps.

---

### Post by kebes on 2008-08-01
> **herbster said:**
> EDIT: Blasted "Indexes" needed to be added to the Directory part of httpd.conf! Works :)
Glad you got it working! Have fun! :)

---

### Post by herbster on 2008-08-02
Thanks for the help kebes. I have a question about the port range, though, it's currently at 49160-49300 but the port I have always used for my torrents that's forwarded in my router is 1901, would I change the 49160-49300 to 1901-1901??

EDIT: Also, I don't want to download torrents into a folder with my username. For example if my downloads path is /media/torrents, I just tried a couple small torrents to test and they all downloaded to /media/torrents/username/, but I just want them to go straight to /media/torrents/, how can I change this?? (If I can) :)

---

### Post by kebes on 2008-08-02
> **herbster said:**
> the port I have always used for my torrents that's forwarded in my router is 1901, would I change the 49160-49300 to 1901-1901??
Yes, that should work. You can use whatever port range you want (set it in admin > settings > port range). As far as I know, setting the max and min to the same value forces it to use a single port.

> they all downloaded to /media/torrents/username/, but I just want them to go straight to /media/torrents/
As far as I know, TorrentFlux doesn't provide a simple way to do this. It always downloads to your user sub-folder. However you can 'trick' it pretty easily. In torrentflux, set the download folder (admin > settings > path) as "/var/www/torrentflux/downloads/" (or whatever). This means that the downloads will be put into "/var/www/torrentflux/downloads/username/". Then just make that directory a symlink to the actual download location that you want. For instance:
```

cd /var/www/torrentflux/downloads/
rm username
ln -s /media/torrents/ username

```

With that symlink set, TorrentFlux should blindly put all of your downloads in "/media/torrents/". (The status files, by the way, will still be stored at "/var/www/torrentflux/downloads/.torrents/" ... but that shouldn't cause any problems.)

---

### Post by herbster on 2008-08-02
Okay on the port, speeds are they've always been.

As for the symlink, it doesn't appear to work. Any new torrent I try to run fails. I set the symlink to ~/public_html/torrentflux/username and links to /media/torrents, but no go. Perhaps it can't be fooled? Unless you or others have attempted this, hopefully there's a way.

Of course I just reazlied I could make a user named "torrents" and set the download to /media, hehe.

EDIT: Got it to go without a symlink, just changed default user to torrents and she's downloading fine! Also to note (apologies if it's been mentioned somewhere in this thread), I was encountering the "DONE" and "download failed" after every torrent, being able to grab just one and then no workie. I fixed this via a thread on the torrentflux forum reminding users that the BitTornado engine is at work and apparently how many torrents one can download is proportionate to the port range, so I opened up some more ports and she's workin' great :)

---

### Post by herbster on 2008-08-02
Any problems with private trackers? I can't seem to get any torrents working, have gotten the errors "rejected tracker - invalid port" and a tracker timeout. I have tried some different ports, no go.

---

### Post by kebes on 2008-08-02
> **herbster said:**
> Any problems with private trackers? I can't seem to get any torrents working, have gotten the errors "rejected tracker - invalid port" and a tracker timeout. I have tried some different ports, no go.

If it doesn't work when you copy-and-paste the URL for a private tracker .torrent into the "URL for the Torrent File" box, you can try to download the .torrent file to your computer, and then upload it to TorrentFlux using the "Select a Torrent for upload" option (just browse for the file and click Upload).



Another solution is to set a cookie inside TorrentFlux, so that it has the login credentials for the private tracker. Go to "My Profile" > "Cookie Management". (Click the "How to get cookie information...." link for a quick description of how to copy-and-paste the cookie data from a web-browser that has been authenticated to use the private tracker.)

See also [this link]("http://filesharefreak.com/2008/05/08/torrentflux-adding-torrents-from-your-private-tracker-url/") for a step-by-step on how to do that.

---

### Post by herbster on 2008-08-03
Ah yes, I got the cookies working, the problem was actually that the torrents weren't starting at all on private trackers, no connectability. I fixed it by setting Stealth Crypto to FALSE in the Admin > Settings, but a friend on IRC mentioned to me torrentflux-b4rt and I just finished setting it up, I gotta say it is schu-weet!!! I don't know if you've given it a shot but it was a breeze to setup and IMO much improved over torrentflux. Can get it here: [http://tf-b4rt.berlios.de/](http://tf-b4rt.berlios.de/)

---

### Post by kebes on 2008-08-27
[QUOTE=Cata1yst]
Im missing the following python scripts
> 
btshowmetainfo.py
btphptornado.py
btmakemetafile.py
tfQManager.py
So far i untared the 2.4 version, added the tables to MySQL, and then issued "sudo cp –r * /var/www/tf"

any idea how to get those python scripts?
[/quote]


Those files should get installed to "/var/www/tf/TF_BitTornado/". A normal install should put them at the correct location. If not, you can find them in the [install file]("http://downloads.sourceforge.net/torrentflux/torrentflux_2.4.tar.gz?modtime=1213797423&big_mirror=0") (once untarred, the files will be in "html/TF_BitTornado/" subdirectory).

> Also does it matter which version of Bit tornado im using? im assuming i can just grab the latest.

Torrentflux uses the version of BitTornado installed at "/var/www/tf/TF_BitTornado/", which is independent of any other bit-torrent client you have installed on your system. I don't think you should manually update the version of BitTornado scripts in that folder (new versions of TorrentFlux will include the new version of the scripts).

---

### Post by Crafty Kisses on 2008-08-28
Nice tutorial, very smooth and well explained.

---

### Post by ivikas on 2008-08-28
I don't down how this pst came here

---

### Post by PurposeOfReason on 2008-11-10
How would I make and seed a torrent? I made the .torrent, uploaded it to my tracker, but after that I don't know how to start it. I can start it like I'm downloading it, but then it doesn't appear "complete" and I don't think it is seeding.

---

### Post by kebes on 2008-11-10
> **PurposeOfReason said:**
> How would I make and seed a torrent? I made the .torrent, uploaded it to my tracker, but after that I don't know how to start it. I can start it like I'm downloading it, but then it doesn't appear "complete" and I don't think it is seeding.

After uploading your .torrent file to a tracker, you usually have to download the .torrent file from tracker. I think most trackers will modify the file slightly, so you may need to redownload the .torrent from the tracker (instead of using the one you generated yourself). (Some info [here]("http://seedboxhosting.com/seedbox/34/using-torrentflux-to-upload-create-and-seed-your-torrents-part-ii").)

But honestly I don't know enough about initiating new torrents to be much of a help on this one... Hopefully someone else has some good hints?

---

### Post by PurposeOfReason on 2008-11-10
I think I got it. They didn't say anything about redownloading the .torrent. Mine was just trying to download it again instead of pointing to the file. Stupid error.

---

### Post by TheKLB on 2008-12-14
Just had to register to tell you thanks! Got it to work on my Bluehost.com web server because of yout guide. Didnt really follow it to the T, but it did help

---

### Post by kebes on 2008-12-14
> **TheKLB said:**
> Just had to register to tell you thanks! Got it to work on my Bluehost.com web server because of yout guide. Didnt really follow it to the T, but it did help

Awesome! I'm glad this tutorial is still helpful and relevant!

---

### Post by kemadruma on 2009-01-17
I have installed torrentflux correctly and it is showing green light next to fields. But when i start torrent, it says "Connecting to Peers" and nothing happens there after.

I think the webserver's firewall is not allowing the torrentflux on default port, so i tried to change ports but nothing happened.

What could b the reason and How to solve it?

Help would be appreciated!

---

### Post by kebes on 2009-01-17
> **kemadruma said:**
> when i start torrent, it says "Connecting to Peers" and nothing happens there after.

Try using some other BitTorrent clients on the same port, and see if they work.

First thing to check is that your firewall (on your computer and in your router) are set to not block the port:
-By default Ubuntu shouldn't be blocking the port, but if you've installed a firewall (e.g. Firestarter) or some other security software, it may be actively blocking.
-On your router there is probably a hardware firewall. Log into your local router (usually done by going to a webpage like "http://192.168.1.1" or "http://192.168.0.1" or "http://192.168.15.1" or something like that... it depends on the make and model). Then find the settings for "Port Blocking" (may also be called "Applications & Gaming" or "Port Forwarding" or something), and set the port you're using for BitTorrent to be forwarded to the internal IP address of your computer (the LAN IP; it will probably be something like 192.168.1.101).

It's also possible that your internet provider is the one blocking it. Again, doing a quick test with another client will help.

---

### Post by jamal6008 on 2009-02-07
Hi I need some help

I used ubuntu for first time on a server and same with torrentflux.

Once I installed it I get these error messages in server settings:

transmissioncli : Executable is not TorrentFlux-bundled transmissioncli


uudeview: Path is not valid
php : Path is not valid
cksfv: Path is not valid
vlc: Path is not valid

The last 4 errors I have installed these things but they can not be found where they should i.e. /usr/bin/

Please guide me if I need to reinstall them or do something to fix this.  And first error I don't understand what that is for. I am only able to use Bittornado client and not transmission because of that error.

I would be grateful if someone can guide me with steps how to fix this problem.

Thanks

---

### Post by kebes on 2009-02-07
> **jamal6008 said:**
> transmissioncli : Executable is not TorrentFlux-bundled transmissioncli

uudeview: Path is not valid
php : Path is not valid
cksfv: Path is not valid
vlc: Path is not valid

First off, it sounds like you've installed "[torrentflux-b4rt]("http://tf-b4rt.berlios.de/")" and not normal "[torrentflux]("http://www.torrentflux.com/")". Right? (Note that the instructions in this thread are for torrentflux and may or may not apply to b4rt...)

You should probably search the [b4rt forums]("http://tf-b4rt.berlios.de/forum/"), and see if anyone has encountered your errors. Submitting your problem there might be better, too.


[This thread]("http://tf-b4rt.berlios.de/forum/index.php/topic,1365.msg6385.html#msg6385") seems to indicate that those errors are for optional components. So if you don't need those functions then you might be fine. Is torrentflux-b4rt working? It would be best to first make sure that basic functionality is working (you can start a torrent properly), and worry about extra features later...

---

### Post by jamal6008 on 2009-02-07
they are working except the transmission client. 

What is the difference between both of them? Which one is better??

---

### Post by kebes on 2009-02-07
> **jamal6008 said:**
> they are working except the transmission client. 

What is the difference between both of them? Which one is better??

I've only ever used the default torrent client (BitTornado). According to [this]("http://tf-b4rt.berlios.de/features.html"), the transmission client uses less memory, but has fewer features.

I've never had any issues with BitTornado, so unless you have a specific reason for preferring/needing transmission (like you're using a resource-limited machine or you're planning on [seeding tons of torrents]("http://seedboxhosting.com/seedbox/41/which-bittorrent-client-should-i-use-with-torrentflux")), then you can probably just use the default.

---

### Post by jamal6008 on 2009-02-08
In all the seedboxes I have ever been they have been using transmission as the client. And that is what is supposed to be default as well. I prefer using it myself as it takes less memory. You don't really need more features to be honest it works perfectly fine.

So no ideas how to fix it then?

---

### Post by kebes on 2009-02-08
> **jamal6008 said:**
> I prefer using it myself as it takes less memory. 
So no ideas how to fix it then?
To use transmission-cli with torrentflux-b4rt you need to make a special patched version of transmission.

This appears to be the procedure (haven't tried this yet but it looks right...): The [torrentflux-b4rt tar that you downloaded]("https://developer.berlios.de/project/showfiles.php?group_id=7000&release_id=14392") has a patch for the transmission source code in it. Go into the "clients" directory, then the "transmission" sub-directory. In there you will find various versions of the patch, along with instructions, which I will reproduce here:
```

1. Get the Transmission Source Code Release from
   http://www.transmissionbt.com/

2. Untar the package into a directory.

   tar -jxvf transmission-<version>.tar.bz2

3. Untar the tfb-package into a directory.

   tar -jxvf Transmission-<version>_tfCLI-<version>.tar.bz2

4. Copy the content of the tfb-package extracted in 3. to the
   Transmission-Directory extracted in 2. (overwriting files).

   FreeBSD only: Apply the patch "freebsd.patch" (file was just
                 copied to the Transmission-Directory)

5. Build + Install transmissioncli, instructions about how to
   do this can be found in the Transmission-Documentation.

```
So basically you download a version of transmission compatible with the patch, like say [v.1.06]("http://download.m0k.org/transmission/files/transmission-1.06.tar.bz2"). You untar that source code, and then also untar the corresponding patch ("Transmission-1.06_tfCLI-svn3356.tar.bz2"). From the create patch directory, you copy the file "transmissioncli.c" over to the transmission source tree, over-writting the default version.

Then you go into the directory for transmission, and follow the instructions in the INSTALL file, which [basically involve doing]("http://tf-b4rt.berlios.de/forum/index.php/topic,41.0.html"):
$ ./configure --disable-gtk
$ make
$ sudo make install

This will install the new patched version of transmission-cli to /usr/local/bin/ and will over-write any other version of transmission-cli you installed previously.


[These instructions]("http://howto.landure.fr/gnu-linux/debian-4-0-etch-en/install-torrentflux-b4rt-on-debian-4-0-etch") for Debian (scroll down to section "Using Transmission as BitTorrent client") describe the process also.


Hope that helps.

---

### Post by jamal6008 on 2009-02-08
> **kebes said:**
> To use transmission-cli with torrentflux-b4rt you need to make a special patched version of transmission.

This appears to be the procedure (haven't tried this yet but it looks right...): The [torrentflux-b4rt tar that you downloaded]("https://developer.berlios.de/project/showfiles.php?group_id=7000&release_id=14392") has a patch for the transmission source code in it. Go into the "clients" directory, then the "transmission" sub-directory. In there you will find various versions of the patch, along with instructions, which I will reproduce here:
```

1. Get the Transmission Source Code Release from
   http://www.transmissionbt.com/

2. Untar the package into a directory.

   tar -jxvf transmission-<version>.tar.bz2

3. Untar the tfb-package into a directory.

   tar -jxvf Transmission-<version>_tfCLI-<version>.tar.bz2

4. Copy the content of the tfb-package extracted in 3. to the
   Transmission-Directory extracted in 2. (overwriting files).

   FreeBSD only: Apply the patch "freebsd.patch" (file was just
                 copied to the Transmission-Directory)

5. Build + Install transmissioncli, instructions about how to
   do this can be found in the Transmission-Documentation.

```
So basically you download a version of transmission compatible with the patch, like say [v.1.06]("http://download.m0k.org/transmission/files/transmission-1.06.tar.bz2"). You untar that source code, and then also untar the corresponding patch ("Transmission-1.06_tfCLI-svn3356.tar.bz2"). From the create patch directory, you copy the file "transmissioncli.c" over to the transmission source tree, over-writting the default version.

Then you go into the directory for transmission, and follow the instructions in the INSTALL file, which [basically involve doing]("http://tf-b4rt.berlios.de/forum/index.php/topic,41.0.html"):
$ ./configure --disable-gtk
$ make
$ sudo make install

This will install the new patched version of transmission-cli to /usr/local/bin/ and will over-write any other version of transmission-cli you installed previously.


[These instructions]("http://howto.landure.fr/gnu-linux/debian-4-0-etch-en/install-torrentflux-b4rt-on-debian-4-0-etch") for Debian (scroll down to section "Using Transmission as BitTorrent client") describe the process also.


Hope that helps.

Thank you soo much. I wasn't expecting a reply.

I found a similar solution which I think is similar maybe.

I am already doing that and stuck half way. I thought I should tell you here before proceeding with this one and messing everything up. 


This is what I found

```
Download lastest version of transmission (http://download.m0k.org/transmission/files/transmission-1.22.tar.bz2)
Untar it with tar xvjf transmission-1.22.tar.bz2 replace transmission-1.22/cli/transmissioncli.c with (http://svn.berlios.de/svnroot/repos/tf-b4rt/branches/clients/transmission/transmission-1.20/cli/transmissioncli.c)

You need to install libcurl:
yum install curl
yum install curl-devel

Now, go to transmission-1.22 and type:
./configure -q && make -s
su (if necessary for the next line)
make install 
```

In these steps I have done uptill install curl.

I am using ubuntu and when I try apt-get install curl-devel it says no such thing exists

So I tried to skip this step I went into next ones I did the configure one and it said -bash: ./: is a directory 

I don't know if that is how it should be.

I tried to make install than and it said no rule to make target `install`. Stop 

I am very confused about it. I think it might be syntax problem. These instructions were for CentOS. Please guide me on this I would be really grateful.

---

### Post by kebes on 2009-02-08
> **jamal6008 said:**
> I am using ubuntu and when I try apt-get install curl-devel it says no such thing exists
I believe [in Ubuntu the package]("http://packages.ubuntu.com/search?keywords=curl+dev&searchon=names&suite=intrepid&section=all") is called "libcurl4-gnutls-dev" (that's for version 4 of curl, there is also a v.3 version of the package). So try installing that one.

Also, for the subsequent steps to work, you'll need the package "[build-essential]("http://packages.ubuntu.com/intrepid/build-essential")" installed.


> So I tried to skip this step I went into next ones I did the configure one and it said -bash: ./: is a directory 

That error happens if you type "./" in a terminal. Note that the first command you type should be "./configure" (without the quotes). 


> I tried to make install than and it said no rule to make target `install`. Stop 
The subsequent steps ("make" and "sudo make install") won't work unless configure runs properly.

> Please guide me on this I would be really grateful.
I'm happy to help. If you encounter any error messages paste the terminal output here (your command and the error message it produced).

---

### Post by jamal6008 on 2009-02-08
> **kebes said:**
> I believe [in Ubuntu the package]("http://packages.ubuntu.com/search?keywords=curl+dev&searchon=names&suite=intrepid&section=all") is called "libcurl4-gnutls-dev" (that's for version 4 of curl, there is also a v.3 version of the package). So try installing that one.

Also, for the subsequent steps to work, you'll need the package "[build-essential]("http://packages.ubuntu.com/intrepid/build-essential")" installed.




That error happens if you type "./" in a terminal. Note that the first command you type should be "./configure" (without the quotes). 



The subsequent steps ("make" and "sudo make install") won't work unless configure runs properly.


I'm happy to help. If you encounter any error messages paste the terminal output here (your command and the error message it produced).


Thanks for your help once again. The first step worked and I installed it.

In the second step which is the configuration. I tried to do the exact thing you told me and these are the statements which appeared on putty:

appending configuration tag "CXX" to libtool
appending configuration tag "F77" to libtool

configure: error: Package requirements (openssl >= 0.9.4) were not met: No package 'openssl' found

I didnt install the essential pack you told me about. Is it related to that? Do I have to wget it untar and than install????

---

### Post by kebes on 2009-02-08
> **jamal6008 said:**
> 
configure: error: Package requirements (openssl >= 0.9.4) were not met: No package 'openssl' found
You are missing the "[openssl]("http://packages.ubuntu.com/intrepid/openssl")" package (library for accessing secure https sites). Install in the usual way:
```
$ sudo apt-get install openssl
```
You might also need:
```
$ sudo apt-get install libcurl4-openssl-dev
```
Then re-run the configuration:
```
$ ./configure
```

This is the disadvantage of installing things manually... you have to manually resolve package dependencies. But hopefully there will only be a few more missing packages before the configure command runs properly.

---

### Post by jamal6008 on 2009-02-08
I tried that I think the configure worked.

Than I tried to install and that is done too.

The last couple of statements that came up which look a bit confusing were:

make[2]: leaving directory '/root/transmission-1.22/cli'
make[1]: leaving directory '/root/transmission-1.22/cli'
make[1]: entering directory '/root/transmission-1.22'
make[2]: entering directory '/root/transmission-1.22'
make[2]: Nothing to be done for 'install-axec-am'
make[2]: Nothing to be done for 'install-data-am'
make[2]: Leaving directory '/root/transmission-1.22'
make[1]: Leaving directory '/root/transmission-1.22'

I don't know If it has been done properly. Is there any way to test it? My original problem which was that it showed in server settings for torrentflux that transmission: Executable is not TorrentFlux-bundled transmissioncli

Its not changed. 

You said that this is too long. What is the easier way then??

---

### Post by kebes on 2009-02-08
> **jamal6008 said:**
> make[2]: leaving directory '/root/transmission-1.22/cli'
make[1]: leaving directory '/root/transmission-1.22/cli'
make[1]: entering directory '/root/transmission-1.22'
make[2]: entering directory '/root/transmission-1.22'
make[2]: Nothing to be done for 'install-axec-am'
make[2]: Nothing to be done for 'install-data-am'
make[2]: Leaving directory '/root/transmission-1.22'
make[1]: Leaving directory '/root/transmission-1.22'

I don't know If it has been done properly.

Looks okay.

> Is there any way to test it?
Try running "transmissioncli --help" or "transmissioncli --version". Does it tell you a version number? It should say something like:
> modified for Torrentflux-b4rt

You can use:
```
$ which transmissioncli
```
to determine where the current version in use is installed. Follow that and see if you have multiple versions of transmissioncli installed somewhere. Maybe you can update the symlinks appropriately.

For instance, your previous install of transmissioncli may still be in use. Let's say the "which" command tells you that the current version is at "/usr/bin/transmissioncli". But the new version you just built is perhaps at "/usr/local/bin/transmissioncli" (or maybe it's at "/usr/local/bin/transmissioncli-1.22/transmissioncli" or whatever--you'll have to check around a bit). You could then do something like:
-Save your old version:
```
$ cd /usr/bin/
$ mv transmissioncli old-transmissioncli

```-Use new version instead (with a symlink):
```
$ cd /usr/bin/
$ ln -s /usr/local/bin/transmissioncli transmissioncli

```

In other words, you symlink it so that the version of transmissioncli being used throughout your system is the version you want! Hopefully that makes sense... (it's hard to know exactly what to do without having it installed on my system)

---

### Post by jamal6008 on 2009-02-08
> **kebes said:**
> Looks okay.


Try running "transmissioncli --help" or "transmissioncli --version". Does it tell you a version number? It should say something like:


You can use:
```
$ which transmissioncli
```
to determine where the current version in use is installed. Follow that and see if you have multiple versions of transmissioncli installed somewhere. Maybe you can update the symlinks appropriately.

For instance, your previous install of transmissioncli may still be in use. Let's say the "which" command tells you that the current version is at "/usr/bin/transmissioncli". But the new version you just built is perhaps at "/usr/local/bin/transmissioncli" (or maybe it's at "/usr/local/bin/transmissioncli-1.22/transmissioncli" or whatever--you'll have to check around a bit). You could then do something like:
-Save your old version:
```
$ cd /usr/bin/
$ mv transmissioncli old-transmissioncli

```-Use new version instead (with a symlink):
```
$ cd /usr/bin/
$ ln -s /usr/local/bin/transmissioncli transmissioncli

```

In other words, you symlink it so that the version of transmissioncli being used throughout your system is the version you want! Hopefully that makes sense... (it's hard to know exactly what to do without having it installed on my system)

It shows the help but when I try the version nothing comes up.

Shall I proceed with other steps??

which transmissioncli shows /usr/local/bin/transmissioncli

I found another copy of it in /usr/bin/

EDIT: I followed all other commands of urs and did what you said. Than I did which transmissioncli and its still the same. In your steps you wrote the same path of transmissioncli for both of them? are you sure its same??

---

### Post by jamal6008 on 2009-02-08
I just checked the sever settings and you can actually change the path of transmission from there

I also tried both of these paths but its still same error. Do you think there can be another path? Ill search

---

### Post by kebes on 2009-02-08
> **jamal6008 said:**
> It shows the help but when I try the version nothing comes up.
Does running "transmissioncli --help" (or maybe just "transmissioncli" by itself) mention a version number or that this is a "b4rt" modified version?



> which transmissioncli shows /usr/local/bin/transmissioncli

I found another copy of it in /usr/bin/

This suggests that you're now using the correct version of transmissioncli (the one you just built & installed). Some things to check:

-Try refreshing torrentflux so that it sees the new version. (Close your torrentflux session and open it again. You can also try running "sudo /etc/init.d apache2 restart" to force a restart of the webserver, which runs torrentflux.)

-Check in the options for torrentflux-b4rt and see if there is anyplace where you specify the path for transmission. It should be "/usr/local/bin/transmissioncli"

-Before you ran the "./configure" step, you did replace the "transmissioncli.c" file, right? (There was a step in the instructions like "replace transmission-1.22/cli/transmissioncli.c with (http://svn.berlios.de/svnroot/repos/tf-b4rt/branches/clients/transmission/transmission-1.20/cli/transmissioncli.c)" which is crucial because it applies the patch.)



> Shall I proceed with other steps?? I followed all other commands of urs and did what you said. Than I did which transmissioncli and its still the same. In your steps you wrote the same path of transmissioncli for both of them? are you sure its same??
There was no need since it was already pointing to the right spot. (But it didn't do any harm.)

---

### Post by kebes on 2009-02-08
Another thing I just thought of: make sure that you don't have any instances of the old version of transmission running in memory. You can check with:
```
$ pgrep -l transmission
```
If there are, use "kill" to stop them, or:
```
$ killall transmissioncli
```

---

### Post by jamal6008 on 2009-02-08
I tried replacing it in torrentflux settings with both of the paths and both of them give error. I tried enetering a wrong path and it said that path is wrong so it means it is refreshing... Is it possible that there maybe another path? I searched but didnt find any?

Also yes I installed that patch which you told me about before I Installed.

---

### Post by jamal6008 on 2009-02-08
> **kebes said:**
> Another thing I just thought of: make sure that you don't have any instances of the old version of transmission running in memory. You can check with:
```
$ pgrep -l transmission
```
If there are, use "kill" to stop them, or:
```
$ killall transmissioncli
```

I tried these. It said no processes killed.

---

### Post by jamal6008 on 2009-02-08
I typed transmissioncli --version in root and it said

transmission 1.06 

Do I have to be in specific folder before i type it???

EDIT: I typed it everywhere and it said the same.

I wish there was a fast and easy way to do this. I have been trying to fix this for days now. Thanks for your really kind help for guiding me so much.

I dont know what to do now again.

---

### Post by kebes on 2009-02-08
> **jamal6008 said:**
> I typed transmissioncli --version in root and it said

transmission 1.06 

I need some more information. What happens when you type these commands (copy everything that they output):

```
$ which transmissioncli
$ transmissioncli --help
$ transmissioncli --version
$ /usr/bin/transmissioncli --help
$ /usr/bin/transmissioncli --version
$ /usr/local/bin/transmissioncli --help
$ /usr/local/bin/transmissioncli --version

```

Edit: If you followed my previous instruction about moving the old version of transmissioncli, then also run these:
```
$ /usr/bin/old-transmissioncli --help
$ /usr/bin/old-transmissioncli --version
```

---

### Post by jamal6008 on 2009-02-08
> **kebes said:**
> I need some more information. What happens when you type these commands (copy everything that they output):

```
$ which transmissioncli
$ transmissioncli --help
$ transmissioncli --version
$ /usr/bin/transmissioncli --help
$ /usr/bin/transmissioncli --version
$ /usr/local/bin/transmissioncli --help
$ /usr/local/bin/transmissioncli --version

```

/usr/local/bin/transmissioncli

help gives:
transmission 1.06 
usuage transmissioncli [-car[-m]] [-dfinpsuv] [-h] file.torrent [output-dir]

and all other options

I wish there was a way to copy this I have to type all this

version gives the same version shown above

And all other 4 for two different paths also give the same as these...

---

### Post by kebes on 2009-02-08
> **jamal6008 said:**
> I wish there was a way to copy this I have to type all this
In Ubuntu you can select text in a terminal and then middle-click in another document to copy-paste it. If you're using something like PuTTY, you can similarly select the text and then it copies it to the clipboard (I think it auto-copies to clipboard; if not then you can click on PuTTY's window icon and select "copy" from there I think).


> /usr/local/bin/transmissioncli

help gives:
transmission 1.06 

And all other 4 for two different paths also give the same as these...
Did you try running the commands for "/usr/bin/old-transmissioncli"?

In any case, the version is obviously wrong. First of all the patched version should say "modified for Torrentflux-b4rt" I believe. Secondly, when you patched and installed manually, what version of the transmission code were you installing? You mentioned at one point that you were following instructions that mentioned using version 1.22. Is that what you did? Or did you try to install using version 1.06 that is distributed with torrentflux-b4rt directly?

---

### Post by jamal6008 on 2009-02-08
I use putty. I will try that.

And yes it came that same version for all others.

I followed these instructions it shows which files I downloaded and which I replaced:

Download lastest version of transmission ([http://download.m0k.org/transmission/files/transmission-1.22.tar.bz2](http://download.m0k.org/transmission/files/transmission-1.22.tar.bz2))
Untar it with tar xvjf transmission-1.22.tar.bz2 replace transmission-1.22/cli/transmissioncli.c with ([http://svn.berlios.de/svnroot/repos/tf-b4rt/branches/clients/transmission/transmission-1.20/cli/transmissioncli.c](http://svn.berlios.de/svnroot/repos/tf-b4rt/branches/clients/transmission/transmission-1.20/cli/transmissioncli.c))

You need to install libcurl:
yum install curl
yum install curl-devel

Now, go to transmission-1.22 and type:
./configure -q && make -s
su (if necessary for the next line)
make install

---

### Post by jamal6008 on 2009-02-08
Is it possible to just delete all of the transmission installed and install a new one which will work. I know it will take long and again long guide and talk but I dont think I have any other option.

---

### Post by kebes on 2009-02-08
> **jamal6008 said:**
> Is it possible to just delete all of the transmission installed and install a new one which will work. I know it will take long and again long guide and talk but I dont think I have any other option.

Yes that's worth a try. How you remove the other versions depends somewhat on what you've already tried. 

You should undo that change I asked you to try awhile back (if you did indeed try it...):```

$ cd /usr/bin/
$ rm transmissioncli
$ mv old-transmissioncli transmissioncli
```

To uninstall the repository version (you installed it originally with apt-get, right?):
```
$ sudo apt-get remove transmissioncli
```

And then I guess delete the version in /usr/local/bin
```
$ sudo rm /usr/local/bin/transmissioncli
```


Then start back a few steps. I recommend that you use transmission 1.06 source code, and use the patch and instructions that are packaged with torrentflux-b4rt, rather than using those CentOS instructions.

---

### Post by jamal6008 on 2009-02-08
I did those steps and replaced the path in torrentflux server settings

and guess what it turned green :O:O

But i cant find a way to test it i changed the default client to transmission still it runs it with bittornado

---

### Post by kebes on 2009-02-08
> **jamal6008 said:**
> I did those steps and replaced the path in torrentflux server settings

and guess what it turned green
So you got the proper version of transmission running! That's good!

> But i cant find a way to test it i changed the default client to transmission still it runs it with bittornado
How do you know it's running with BitTornado?

You might have to stop all downloads to make sure that TorrentFlux fully restarts and can use the other torrent client...

---

### Post by jamal6008 on 2009-02-08
I think its working

Thanks alot for your great help.

I may have to set up this on another server. So what do you suggest?? Shall I install LAMP and than download torrentflux-b4rt tar it ?? Do you mind if I contact you once I try to set up this on other server. It wont be very soon maybe in 3 weeks time.

---

### Post by jamal6008 on 2009-02-08
I am running with transmission it shows in the torrentflux which client you using.

But the downloading and uploading speed is 0 and the peers and seeders are 0 as well why is that? I just stopped this torrent it was seeding at 1000kbps

---

### Post by kebes on 2009-02-08
> **jamal6008 said:**
> Thanks alot for your great help.
You're very welcome.

> I may have to set up this on another server. So what do you suggest?? Shall I install LAMP and than download torrentflux-b4rt tar it ?? Do you mind if I contact you once I try to set up this on other server. It wont be very soon maybe in 3 weeks time.
Yes. Install LAMP and then download torrentflux-b4rt, untar it. Then install transmission with the patch (like you just did). Then install torrentflux-b4rt. Hopefully it will go smoothly. If not, you can post to this thread again.

> the downloading and uploading speed is 0 and the peers and seeders are 0 as well why is that? I just stopped this torrent it was seeding at 1000kbps
Try switching back to BitTornado. Does it work? Then switch back to transmission. You may have to completely remove the torrent and start up a new, different one for it to work. (The clients create files with data on their progress, so switching clients may not work if a torrent was started with a different client...)

---

### Post by jamal6008 on 2009-02-08
I tried another torrent. It worked but its too slow. I dont know why that is. It verifies the files which you have downloaded through bittornado so it works because of that i think. Its very slow though.

---

### Post by kebes on 2009-02-08
> **jamal6008 said:**
> I tried another torrent. It worked but its too slow. I dont know why that is. It verifies the files which you have downloaded through bittornado so it works because of that i think. Its very slow though.

Strange. I really don't know.

The only thing I can think of is that maybe transmission is using different ports. (Did you unblock some ports for torrents?) Check around and see if there are any options to specify which ports transmission uses (although it should really be using the settings in TorrentFlux)...

---

### Post by jamal6008 on 2009-02-08
That's what I thought as well. But they are using the same ports. Its just weird.

---

### Post by mistaWAC on 2009-02-18
```

Fatal error: Call to undefined function mysql_connect() in /media/Public/FTP/www/tf/adodb/drivers/adodb-mysql.inc.php on line 354

```

Well that's the error I'm getting.  I'm using lighttpd instead of Apache because it's easier to setup.  I'm about 99% positive I set everything up correctly because I followed the INSTALL file in the directory.  Any help?

**EDIT**
Fixed it - nevermind.  For anyone else getting this error be sure to install php5-mysql.  I kinda forgot to and that fixed it.

---

### Post by DBrocks on 2009-03-19
Well, I followed all your directions, yet, when I try to add a torrent, I get this. What's going on? Any suggestions are appreciated!

```
Warning: fopen(/usr/local/torrent/.torrents/All_Time_Top_1000.torrent) [function.fopen]: failed to open stream: No such file or directory in /usr/share/torrentflux/www/index.php on line 425

Warning: fwrite(): supplied argument is not a valid stream resource in /usr/share/torrentflux/www/index.php on line 426

Warning: fclose(): supplied argument is not a valid stream resource in /usr/share/torrentflux/www/index.php on line 427

Warning: Cannot modify header information - headers already sent by (output started at /usr/share/torrentflux/www/index.php:425) in /usr/share/torrentflux/www/index.php on line 438
```

---

### Post by kebes on 2009-03-20
> **DBrocks said:**
> Warning: Cannot modify header information - headers already sent by (output started at /usr/share/torrentflux/www/index.php:425) in /usr/share/torrentflux/www/index.php on line 438[/CODE]
The "headers already sent" error message is almost always caused by having whitespace inside a PHP file outside of the delimiters. Check any files you've edited (like config-db.php) and make sure there is no whitespace (spaces, tabs, returns) before the "<?php" at the top, or after the final "?>".

For example this file would cause an error because of the spaces before the "<?php" at the top:
```
  <?php
   // A bunch of code...
?>

```
Just remove the whitespace and save the file.

---

### Post by bignickel on 2009-04-20
I'm trying to install torrentflux, but I think I have a problem with PHP.  Apache and MySQL are working, but wHen I try to run test.php firefox asks which program I'd like to use to open the php file.  Any thoughts?

UPDATE: solved.  Had to use dpkg and force a reinstall

---

### Post by digbysellers on 2009-06-21
I had this error message after changing the directory in admin -> settings -> path. Fixed by $chmod -R 777 /"PATH"/

---

### Post by tzepu on 2009-07-07
hello
i am trying to make my ubuntu server 9.04 with torrentflux 2.4 to work the way i need
both work but i found no informatin regarding to saving to different directories and importing torrents already seeding with ktorrent 
can any of you direct me to some place where i can figure this out?
should i swith to the -b4rt fork? is there another good one?
thanks in advance

---

### Post by kebes on 2009-07-09
> **tzepu said:**
> saving to different directories
In torrentflux, click "Admin" (at the top) and then "Settings". The first option, "Path", lets you specify the directory where files are saved/downloaded. You can set it to whatever you want, but you need to make sure that the webserver has access to that directory.

> importing torrents already seeding with ktorrent
I don't think you can transfer a running torrent. But you can stop the completed torrent in ktorrent, and then move the completed file into the torrentflux download folder (whatever you set for "path"). Then if you start the exact same torrent file using torrentflux, it will recognize the completed file and start seeding it.

Hope that helps.

---

### Post by zetanuxi on 2009-07-30
Worked perfectly!
Thank-You!

---

### Post by sebrock on 2009-08-18
I have an issue with torrentflux/apache2 not accepting a mouted XFS filesystem as download path. This has worked before I made a fresh system install... any advice?

It works downloading to system disk but that I don't like...

EDIT: nevermind, I got it to work. Apparently the whole path has to be +x

---

### Post by expatCM on 2009-08-20
I have torrentflux running on my server.  It works.  I followed the install guide at this link
[http://drsjlazar.blogspot.com/2007/08/serving-your-home-network-on-silver.html](http://drsjlazar.blogspot.com/2007/08/serving-your-home-network-on-silver.html)
torrentflux starts at item #14.

I have one issue and no idea how to fix.

I cannot stop torrrentflux from appearing and also cannot get anything else to load (like phpmyadmin).

So if I 

[http://servername/](http://servername/)
then the torrentflux login page appears

if I go to any of --

[http://servername/localhost](http://servername/localhost)
[http://servername/torrentflux_2.4/](http://servername/torrentflux_2.4/)
[http://servername/phpmyadmin/](http://servername/phpmyadmin/)
[http://servername/any_other_existing_directory/](http://servername/any_other_existing_directory/)


I get a 404 notice.

Curious ….  but how to fix?

---

### Post by bionnaki on 2009-08-20
*cough* ***_rtorrent + rutorrent_*** *cough*

---

### Post by kebes on 2009-08-20
> **expatCM said:**
> I cannot stop torrrentflux from appearing and also cannot get anything else to load (like phpmyadmin).
From the guide you were following, it seems to me that you've set TorrentFlux using a virtual host in Apache. Thus the web server is capturing all web-requests and redirecting them into the torrent-flux sub-folder.

So, you need to edit your Apache configuration. A simple solution is to redefine the web-document root to be "/var/www/" instead of "/var/www/torrentflux_2.4/html/". To do this, go back into webmin ([https://servername:10000/](https://servername:10000/)) and select Servers > Apache Web server, as you did before. Then change the "Document Root" to "/var/www/".

This will mean that you will then be able to go to:
[http://servername/torrentflux_2.4/html/](http://servername/torrentflux_2.4/html/)
to get to torrentflux, but things like:
[http://servername/phpmyadmin/](http://servername/phpmyadmin/)
will also work. If you don't like torrentflux being at "torrentflux_2.4/html/" you can create a symlink, e.g.:
```

cd /var/www/
ln -s torrentflux_2.4/html/ flux

```
And then torrentflux should appear at:
[http://servername/flux/](http://servername/flux/)



Like I said, this is probably simplest, but there are different solutions you could use. For instance you could re-define your virtual hosts so that each one is attached to a different domain name (if you don't want to buy "real" domain names you can get some free sub-domains from places like [no-ip]("http://www.no-ip.com/services/managed_dns/free_dynamic_dns.html") or [DynDNS]("http://www.dyndns.com/")). You can make these changes through webmin or by editing the apache config file, located at "/etc/apache2/sites-available/default".

Hope that helps.

---

### Post by expatCM on 2009-08-20
Hi kebes,

thank you for making your post.  Your solution was easy, to the point and worked :)   I really appreciated that since I could not work out the solution at all.  I now have a whole weekend to explore the things that would not work before.

Thank you .....  a lot ...

---

### Post by leet_2k on 2010-08-05
Hi there,
 I have followed all your steps (I think). Now when I go to mywebsite.co.cc/torrentflux i get the following message...

TorrentFlux Database/SQL Error                                                                                                                                                                                                                                                       Database error: **Access denied for user 'torrentflux'@'localhost' (using password: YES)**

Always check your database variables in the config.php file.


what do I do?

I seem to have ubuntu 10.4.
I tried going to 
**sudo nano /var/www/torrentflux/config.php**

and got a blank page.
I still typed  the following. Still get an error. Please help
$cfg["db_user"] = "torfluxuser";        // username for my MySQL database
$cfg["db_pass"] = "secret";            // password for database

---

### Post by kebes on 2010-08-05
> **leet_2k said:**
> 
TorrentFlux Database/SQL Error Database error: **Access denied for user 'torrentflux'@'localhost' (using password: YES)**

I tried going to 
**sudo nano /var/www/torrentflux/config.php**

and got a blank page.


Did you install torrentflux to "/var/www/torrentflux/" ? Browse to "/var/www/" and see if the "torrentflux" directory exists, and then check inside to make sure you see all the necessary files. In particular, check that "config.php" is there.

If the file is indeed there, try opening it with a different text editor and see what's inside. You can make the modifications with any text editor.

If the file is missing, you'll need to copy it from the install folder you un-tarred in a previous step.

If the file is there, but blank, you should also over-write it with the default "config.php" from the torrentflux installation tarfile.

---

### Post by pornee on 2010-08-14
[SIZE=3]Is torrentflux still working? I got it up and running no problem but only torrent-portal gives results. none of the other ones work at all, and when I download something it just stays at 0. is there any way to add more search engines like kickasstorrents?[/SIZE]

---

### Post by bigg2 on 2010-09-01
I always use torrentflux-b4rt because it has so much better functuality, and more tools for monitoring

---

### Post by pornee on 2010-09-01
Thank you Bigg2, I'll take a look into it and let you know how it turns out

---

### Post by de0xyrib0se on 2010-09-07
It works fine. There are some functions that are deprecated in PHP 5.3 but they are easily replaced with the "preg_" equivalents + surrounding the match strings with "/".

---

### Post by thebrandon on 2010-09-11
I have been having this problem when I reboot my server all of my seeds say INCOMPLETE and there size goes to zero.  When I try to restart them it makes an attempt then fails.  I have to delete it then add the torrent again and start it again and it is fine.  How can I make it restart on reboot?

---

### Post by imjakes on 2010-10-13
Hi,

After i had a power-breakdown in my house the server is running just fine besides torrentflux.

When i try to login i get the following error :
> Debug SQL is on. 

SQL: INSERT INTO tf_log ( USER_ID, FILE, ACTION, IP, IP_RESOLVED, USER_AGENT, TIME ) VALUES ( 'jakes', '/torrentflux/index.php', 'HIT', '192.168.111.7', '192.168.111.7', 'Mozilla/5.0 (Windows; U; Windows NT 6.0; en-US) AppleWebKit/534.3 (KHTML, like Gecko) Chrome/6.0.472.63 Safari/534.3', '1286944656' )


Database error: Duplicate entry '84305' for key 'PRIMARY'

Always check your database variables in the config.php file.
 

Any ide to what to do to fix this?

Regards,
Jacob

---

### Post by BlackWidower on 2010-11-29
I appear to have fully installed torrentflux properly.  But I've run into a few problems.  For one, not all torrents are working.  Two are because I know there are no seeds, so I'm not worried about that one.  But the other one is the recently released History Insurance by WikiLeaks, and it's not doing anything.

Then there's seeding.  I put two sets of files, fully downloaded, on my torrentflux box with the intention of seeding them.  But for some reason they won't seed.  Under "Estimated Time" it says "Download Failed!" and under "Status" it says "DONE" and I'm have no idea why it won't work!  What am I doing wrong.

My approach has gone thusly:  I would place the files in the torrentflux download directory and then upload the .torrent files through the main torrentflux interface.  Typically this works in other clients.  Am I missing something like a crucial step?  Is there a workaround?  Can I alter the database directly and tell it the download has already completed so it should just seed?  WHAT!?

I know torrentflux is fully installed and working properly because another torrent I aquired downloaded fine and is currently seeding fine as well.

---

### Post by xcurtisx on 2011-01-27
I am trying to find a location to set two commonly used parameters.
1) Incomplete torrent download directory (aka where the files sit as they are being downloaded)
2) Complete Torrent download directory (where they are moved to upon completion)

I normally set both of these to a separate larger file system s to not crowd my main FS. But I do not see those params?
Please advise thanks!

---

### Post by kisen on 2011-02-16
Hi! im trying to download a torrent from a torrent site there u have to register to download and now when I'm trying to copy the link adress to torrentflux it needs the password. Anyone know how u get so it never ask for the password when link adress is put in torrentflux  =) 

thnx!

---

### Post by neptune on 2011-04-25
Is TorrentFlux dead or being developed elsewhere / under a different name? The main torrentflux website and package hasn´t been updated in a long time....

---

### Post by dblkion on 2011-04-27
Hi, 

I had a torrentflux working on my server for a long time, it was set up by a friend who had good skills with linux debian.. 

Now my server crashed and the torrentflux webpage gives me a 403 error, I 've read multiple guides and cant understand how I can start it again, as everything is set and working this shouldn't be too tricky but i'm noob :/

I understand this is ubuntu but its pretty similar and i'm pretty desperate, I hope someone can help me !

Thanks in advance

---

### Post by peeyjay on 2011-05-14
Hoping some one may be able to help.

I have installed Torrentflux and it was working fine now out of the blue the Torrent list has disappeared. I ma able to upload new torrents to the service but can not see the list to start the torrent downloading. Any ideas? 

I have rebooted my server several; times and created new users but the new user accounts also do not display the torrent list...

---

### Post by mycyberquest on 2011-05-15
Excellent tutorial there.

---

### Post by ralfarof on 2011-05-28
> **peeyjay said:**
> Hoping some one may be able to help.

I have installed Torrentflux and it was working fine now out of the blue the Torrent list has disappeared. I ma able to upload new torrents to the service but can not see the list to start the torrent downloading. Any ideas? 

I have rebooted my server several; times and created new users but the new user accounts also do not display the torrent list...

I'm having the same problem since I upgraded from 10.04 to 10.10, same problem with 11.04 :confused:

---

### Post by silentwimble on 2012-07-23
Hi,
I want to use TorrentFlux 2.4 on my free hosting plan for test it.
Every things are ok;
Perl, Phyton, PHP, MySQL....


I installed TorrentFlux. Database settings, TF files CHMOD's... etc. Installing is ok.
But I'm getting these errors on site and I can't execute torrent files for download;

```
Warning: shell_exec() has been disabled for security reasons in /home/fthsglm/public_html/functions.php on line 1951
```

```
Warning: shell_exec() has been disabled for security reasons in /home/fthsglm/public_html/functions.php on line 1951
```

Can anyone help me? 
Thanks.. :)

---

### Post by ralfarof on 2012-07-23
I believe TorrentFlux project is dead and out of maintenance, I'm using uTorrent, it works good so far :popcorn:

---

### Post by Lyfang on 2012-07-24
**@silentwimble:** see also [TorrentFlux-NG]("http://www.torrentflux-ng.org/")

---

### Post by furiousanger on 2013-01-20
To anyone who had a problem with the MySQL part of this when getting to the database creation/find - this is what I had to do to get round it: 
[B]
If you get his error: 
Query Error: CREATE TABLE tf_test ( tf_key VARCHAR(255) NOT NULL default '', tf_value TEXT NOT NULL, PRIMARY KEY (tf_key) ) TYPE=MyISAM[/B]

The bit at the end TYPE=MyISAM is no longer valid in the version of MySQL currently installed on Ubuntu Server 12.04 - you have to edit the following file in /var/www/torrentflux/html/inc/install/queries.install.php to replace TYPE=MyISAM to **ENGINE=MyISAM**. 

After that, provided you have got your other information correct, it should work fine.

---

### Post by Yarbo on 2013-04-21
My god... this, right here solved all my problems! Finding this answer was like finding a needle in a haystack.  I've been pulling my hair out for the last few hours.

THANKS!

> **furiousanger said:**
> To anyone who had a problem with the MySQL part of this when getting to the database creation/find - this is what I had to do to get round it: 
[B]
If you get his error: 
Query Error: CREATE TABLE tf_test ( tf_key VARCHAR(255) NOT NULL default '', tf_value TEXT NOT NULL, PRIMARY KEY (tf_key) ) TYPE=MyISAM[/B]

The bit at the end TYPE=MyISAM is no longer valid in the version of MySQL currently installed on Ubuntu Server 12.04 - you have to edit the following file in /var/www/torrentflux/html/inc/install/queries.install.php to replace TYPE=MyISAM to **ENGINE=MyISAM**. 

After that, provided you have got your other information correct, it should work fine.

---

### Post by zuberi on 2013-06-11
**_Quickest way to install torrentflux:_**

*sudo apt-get install torrentflux*

Just follow the prompts in your terminal, they are obvious questions as are the answers to them. :D

---

### Post by cybercity@localhost on 2013-11-09
thanks for this How-To, I've tested this installation on Ubuntu 12.10 and got it working without any errors.

---

### Post by cybercity@localhost on 2013-11-09
> **neptune said:**
> Is TorrentFlux dead or being developed elsewhere / under a different name? The main torrentflux website and package hasn´t been updated in a long time....
a 403 error occurs if you don't have sufficient privilleges to access restricted area. make sure that you don't have any .htaccess configured to deny access to the files and directories.

---

### Post by adam69 on 2014-07-21
Hi guys

Sorry to digup an old thread here but im having some dramas with torrent flux

The install went all smooth, however when i add a torrent and run it, it simply fails instantly.
running torrentflux 2.4 with ubuntu 14.04

any help would be appreciated!!

---

### Post by QIII on 2014-07-21
Hello, adam69.

Since there is so much water under the bridge since this thread was started, it would be best to start a completely new thread.  Please state your problem in detail and feel free to refer back to this thread.

Cheers.

Closed.

---

