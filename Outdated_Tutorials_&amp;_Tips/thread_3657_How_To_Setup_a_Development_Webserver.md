---
title: "How To: Setup a Development Webserver"
date: 2004-11-08
forum: Outdated Tutorials &amp; Tips
---

### Post by eNiNjA on 2004-11-08
This may not be the best or easiest route, but this is how I setup mine on a fresh Ubuntu install.
  
  Your results may vary...
  
  Development Webserver, Using Apache2, PHP 5, and MySQL 4, Running on Ubuntu Linux
 
 sudo aptitude install build-essential
 sudo apt-get install flex
 sudo apt-get install bison
 sudo apt-get install libgd-dev
 
 download the binary version of MySQL (currently MySQL 4.1.7) from [http://mysql.com]("http://mysql.com")
 download the latest version oh PHP (currently PHP 5.0.2) from [http://php.net]("http://php.net")
 download the latest version of apache 2 (currently Apache 2.0.52) from [http://apache.org]("http://apache.org")
 download the latest libxml2 library (currently libxml2-2.6.15.tar.gz), from [http://xmlsoft.org]("http://xmlsoft.org")
 download the latest zlib library (currently zlib 1.2.1), from [http://gzip.org/zlib]("http://gzip.org/zlib")
 
 :~ $ mv php-5.0.2.tar.gz \
 > libxml2-2.6.15.tar.gz \
 > mysql-standard-4.1.7-pc-linux-i686.tar.gz \
 > httpd-2.0.52.tar.gz \
 > zlib-1.2.1.tar.gz /tmp
 
 cd /tmp
 
 tar -zxvf mysql-standard-4.1.7-pc-linux-i686.tar.gz
 tar -zxvf php-5.0.2.tar.gz
 tar -zxvf httpd-2.0.52.tar.gz
 tar -zxvf libxml2-2.6.15.tar.gz
 tar -zxvf zlib-1.2.1.tar.gz
 
 cd libxml2-2.6.15
 ./configure
 make
 sudo make install
 
 cd /tmp/zlib-1.2.1
 ./configure
 make
 sudo make install
 
 Installing MySQL:
 
 cd /tmp
 
 sudo mv mysql-standard-4.1.7-pc-linux-i686 /usr/local/mysql
 
 sudo groupadd mysql
 
 sudo useradd -g mysql mysql
 
 sudo mv /usr/local/mysql/share/fill_help_tables.sql /usr/local/mysql/support-files
 
 sudo /usr/local/mysql/scripts/mysql_install_db --user=mysql
 
 sudo chown -R root /usr/local/mysql
 
 sudo chgrp -R mysql /usr/local/mysql
 
 sudo chown -R mysql /usr/local/mysql/data
 
 Start it up:
 
 sudo /usr/local/mysql/support-files/mysql.server start
 
 Test it:
 
 /usr/local/mysql/bin/mysql
 
 Secure it:
 
 sudo /usr/local/mysql/bin/mysql -u root
 SET PASSWORD FOR ''@'localhost' = PASSWORD('newpass');
 SET PASSWORD FOR ''@'host_name' = PASSWORD('newpwd');
 
 Installing Apache:
 
 cd /tmp/httpd-2.0.52
 ./configure --prefix=/usr/local/apache2 --enable-so
 make
 sudo make install
 
 Installing PHP:
 
 cd /tmp/php-5.0.2
 nano config.sh
 
 Add (this will vary depend on your needs):
 
 ./configure \
 --prefix=/usr/local/php5 \
 --with-apxs2=/usr/local/apache2/bin/apxs \
 --with-libxml-dir=/usr/local/lib \
 --with-zlib \
 --with-zlib-dir=/usr/local/lib \
 --with-mysql=/usr/local/mysql \
 --with-mysqli=/usr/local/mysql/bin/mysql_config \
 --with-gd \
 --enable-sockets
 
 Press ctrl+o
 Then ctrl+x
 
 chmod 755 config.sh
 
 ./config.sh
 make
 sudo make install
 
 sudo mv /tmp/php-5.0.2/php.ini-dist /usr/local/lib/php.ini
 
 sudo nano /usr/local/apache2/conf/httpd.conf
 
 Add:
 
 AddType application/x-httpd-php .php
 
 ctrl+o
 ctrl+x
  
 sudo /usr/local/apache2/bin/apachectl start
 
 sudo nano /usr/local/apache2/htdocs/test.php
 
 Add:
 
 ```

 <?php
 phpinfo();
 ?>
 
```
 
 Open a browser and visit:
 
 [http://localhost/test.php]("http://localhost/test.php")

---

### Post by TravisNewman on 2004-11-08
Just out of curiosity, why did you compile all that when it's all in the repositories for apt-get?

---

### Post by Artiom on 2004-11-08
Also you can use [xampp for linux](http://www.apachefriends.org/en/xampp-linux.html)   :-k

---

### Post by eNiNjA on 2004-11-08
[QUOTE=panickedthumb]Just out of curiosity, why did you compile all that when it's all in the repositories for apt-get?[/QUOTE] PHP 5 wasnt compiling correctly, and I wasnt aware that its availible in apt-get.
  
  This was a complete clean install, so I didnt have the universe and multiverse enabled.[img]http://www.ubuntuforums.org/images/smilies/icon_eek.gif[/img]
 
 Besides, sometimes its just plain fun to do thing on your own =)

---

### Post by eNiNjA on 2004-11-08
[QUOTE=Artiom]Also you can use [xampp for linux]("http://www.apachefriends.org/en/xampp-linux.html")   :-k[/QUOTE]  xampp is very insecure, and i dont like where it puts stuff.

---

### Post by jwenting on 2004-11-08
An easier route by far is to install Orion [http://www.orionserver.com](http://www.orionserver.com) (or Tomcat [http://jakarta.apache.org](http://jakarta.apache.org) if you prefer something that's completely free).
Then add a decent database, I prefer Firebird ([http://www.ibphoenix.com](http://www.ibphoenix.com) ).
All that after installing JDK and J2EE.

Won't give you PHP without a bit of work but will give JSP which is superior.

---

### Post by eNiNjA on 2004-11-08
> but will give JSP which is superior 
 Where i come from JSP is a dirty, dirty word.
 
 *looks at the ubuntu-geek
 
 hehe...

---

### Post by ubuntu-geek on 2004-11-08
[QUOTE=eNiNjA]Where i come from JSP is a dirty, dirty word.
  
  *looks at the ubuntu-geek
  
  hehe...[/QUOTE] 
 
 :-\"

---

### Post by filattiera on 2004-11-09
[QUOTE=eNiNjA]PHP 5 wasnt compiling correctly, and I wasnt aware that its availible in apt-get.
  
  This was a complete clean install, so I didnt have the universe and multiverse enabled.[img]http://www.ubuntuforums.org/images/smilies/icon_eek.gif[/img]
 
 Besides, sometimes its just plain fun to do thing on your own =)[/QUOTE]

Thanks for your Howto.
Please, if I want to install LAMP with apt-get, which are the packages to install?

I try:
apache2
libapache2-mod-php4
mysql-server

They are enough or I can install other in addition?
Thanks.

Ciao.
Luke.

 :-k

---

### Post by jwenting on 2004-11-09
[QUOTE=eNiNjA]Where i come from JSP is a dirty, dirty word.
 
 hehe...[/QUOTE]
 Weird dictionary you have  :-k 

I've some PHP experience and a LOT of JSP experience (first did JSPs for a customer in 2000 and now work on a project that has over 500 of them).
JSP are far easier to maintain (if written properly, as with any language spaghetti code is possible) which makes them infinitely more suitable to large projects.

---

### Post by eNiNjA on 2004-11-09
[QUOTE=jwenting]Weird dictionary you have  :-k 
 
 I've some PHP experience and a LOT of JSP experience (first did JSPs for a customer in 2000 and now work on a project that has over 500 of them).
 JSP are far easier to maintain (if written properly, as with any language spaghetti code is possible) which makes them infinitely more suitable to large projects.[/QUOTE] 
 Hehe, my dictionary comes from managing servers with many clients using a shared jvm, and ALL of them trying to hog it up to themselves.
 
 *crash *bang *ran_out_of_memory etc..
 
 Other than that, I have nothing against it =)

---

### Post by eNiNjA on 2004-11-09
[QUOTE=filattiera]Thanks for your Howto.
 Please, if I want to install LAMP with apt-get, which are the packages to install?
 
 I try:
 apache2
 libapache2-mod-php4
 mysql-server
 
 They are enough or I can install other in addition?
 Thanks.
 
 Ciao.
 Luke.
 
  :-k[/QUOTE] 
 Im not even sure about this.
 
 Anyone know?

---

### Post by dorris on 2004-11-10
This was a great howto, sure is nice to get your hands dirty once in a while, theres just one problem I've found with mixing debian package management, and compiling sources for yourself. 
Apt won't register what has been compiled from source, anyone know a workaround??

not serious, it just means that things with apache /php as a dependancy will not be downloaded using APT.

hehe, this one was the height of laziness, I didn't feel like finding the site to download the php files for phpmyadmin, so just went into synaptic, DOH, dependancys, apache and php4, OOPS,  i guess i gotta do this manually now, but where to begin
point....click.............wow, that was hectic!

---

### Post by eNiNjA on 2004-11-10
DOH!
  
  I forgot about phpmyadmin, I will try to work that in there.
  
  If there is anything else anyone would like to see added, suggest it, and I will do my best to get it in there.

---

### Post by TravisNewman on 2004-11-10
How about Wordpress (Movable Type has gone to the darkside), Mambo, and phpBB or another open source BB system. Doesn't do me much good, I have webspace that I use, but I'm sure some people would like to know how to set up stuff like that on their own server.

---

### Post by eNiNjA on 2004-11-10
Mambo, great idea..
    
    All the others..not many hosts will put up with them long....
    
    MT will kill a server...even if its there alone...
    
    Wordpress tooo..
    
    And I'm seeing phpBB being hacked on a daily basis...along with nuke
  
 I would like to see..simple php sites, home brew style, that serve the needs of the user, without all the *wizzz *bang *lookatme_i_install_just_like_this
  
  You can feed a human fish, you can teach a human to fish, most, they do not care about fishing, but it all smells funny to me..
  
  ./endrant

---

### Post by eNiNjA on 2004-11-10
ooo..I forgot
  
  i wrote a script that does this whole how-to auto style
  
  email [email="will.ingram@gmail.com"]will.ingram@gmail.com[/email]
  
  Also, do NOT run the script on a production environment, or any computer you value lol..
  
  And heh..most of this wasnt supposed to run together, and I have patched *rigged it
  
  <--not perfect

---

### Post by eNiNjA on 2004-11-10
and yes...it installs everything for you...;)
 
 also have been playing with a script that installs zope | cmf | cmfplone flawlessly on ubuntu, totally fun to play with..
 
 mail me for that also....

---

### Post by 2fargon on 2004-11-11
[QUOTE=eNiNjA]Mambo, great idea..
    
    All the others..not many hosts will put up with them long....
    
    MT will kill a server...even if its there alone...
    
    Wordpress tooo..
    
     
  ./endrant[/QUOTE]

I beg to differ. If you have any issues with wordpress, or know any security risks, please let the developers know. Wordpress is an OpenSource project, just like so many others. It doesn't seem fair to accuse a stable program of being a server-killer, without good reason. 

There is a wordpress debian package, for those interested, by the way so you can apt-get install wordpress.

---

### Post by TravisNewman on 2004-11-11
Yeah I've been using Wordpress for a while now, and with the exception of comment spam I've recently started getting, which is quite a pain, I have no problems with it at all. How do they "kill" the server exactly? I had MT running on my own webserver for a while with no problems.

---

### Post by TravisNewman on 2004-11-11
I have a question for you eninja, and since you've got all this stuff, you may know what I need. I have major issues with file transfers because of my NAT firewall and gaim not getting along. I want to set up a fileserver (using proftpd or whatever works best) with an interface for people to upload files. Whenever someone wants to send me a file, I'll just send them the link to the fileserver, where they'll have an interface for uploading files (a lot of my friends are computer illiterate, so I have to hold their hands with this a bit). Do you know of anything like that? If so, can you incorporate it?

---

### Post by jdodson on 2004-11-11
[QUOTE=panickedthumb]I have a question for you eninja, and since you've got all this stuff, you may know what I need. I have major issues with file transfers because of my NAT firewall and gaim not getting along. I want to set up a fileserver (using proftpd or whatever works best) with an interface for people to upload files. Whenever someone wants to send me a file, I'll just send them the link to the fileserver, where they'll have an interface for uploading files (a lot of my friends are computer illiterate, so I have to hold their hands with this a bit). Do you know of anything like that? If so, can you incorporate it?[/QUOTE]

[this might help.](http://www.phpfreaks.com/quickcode/File_Uploader/152.php)  

you could always setup the anonymous FTP account to allow for uploads, this is a potential security risk as people might upload virii, etc.  though you might want to create a dummy account that you turn on and off via FTP when you want people to transfer you files.   as far as setting up an FTP "interface" they could use gftp(in linux) or filezilla(windows) to upload the files in an easy manner.

you could also use GAIM to transfer files.  the interface is getting better, it doesnt always crash anymore:)

---

### Post by TravisNewman on 2004-11-11
Yeah, they don't get ftp clients *L* See what I mean about holding their hands?

But gaim is my problem. I can't recieve files on gaim (at least not on the AIM network, since that's where most of my friends are) because of my NAT router. If you know a way around that, lemme know!

---

### Post by nixn00b on 2004-11-14
Thanks for this, just one more thing I'm not capable of , once its installed as suggested in this thread, how do I start the SQL server and apache on bootup??

I guess I could put it into the session startup, but I figure this is something I gotta learn sometime or it will bite me again later.

thanks in advance

---

### Post by MatthewMetzger on 2004-12-05
> how do I start the SQL server and apache on bootup??

They should be set up to start at bootup, but I installed mine with apt-get. I'm not sure what advantages there are to downloading everything seperating and compiling. Apt-get is the reason I switch to debian-based ubuntu.

A question of my own: What is the proper way of creating vitual servers in the default apache install. Before I was using Xampp and I had it working there, but I'd like to learn how to use the seamingly more secure defualt way that ubuntu/debain installs apache. Is there a HOWTO anywhere on virtual servers on apache in ubuntu?

---

### Post by athem on 2004-12-06
I completed all of the steps required to install PHP 5, *except*  I'm using Apache 1.3. When I try running test.php, my browser tries to open it as a text file using gedit.  I think this might be a problem with setting up the mime type correctly for Apache 1.3 - any ideas what might be causing this and how to fix?  Thanks.

---

### Post by Alessio on 2004-12-06
[QUOTE=eNiNjA]xampp is very insecure, and i dont like where it puts stuff.[/QUOTE]
Why do you say this? 8-[

---

### Post by daniels on 2004-12-06
Hi,
If you do this, you lose all security support -- when there's a new hole in PHP, your development web server gets rooted.  Apache 2.0.52, whatever the latest version of mySQL is, and also, I think, PHP5, are all available in our repositories.

Please use those!  We don't just make them for fun/ease; we also support them security-wise, so you don't have to get cracked.

---

### Post by Alessio on 2004-12-06
[QUOTE=daniels]Hi,
If you do this, you lose all security support -- when there's a new hole in PHP, your development web server gets rooted.  Apache 2.0.52, whatever the latest version of mySQL is, and also, I think, PHP5, are all available in our repositories.

Please use those!  We don't just make them for fun/ease; we also support them security-wise, so you don't have to get cracked.[/QUOTE]

For local use? Like have a speed alternative for web development without access from internet?

---

### Post by Alessio on 2004-12-06
[QUOTE=daniels]Hi,
If you do this, you lose all security support -- when there's a new hole in PHP, your development web server gets rooted.  Apache 2.0.52, whatever the latest version of mySQL is, and also, I think, PHP5, are all available in our repositories.

Please use those!  We don't just make them for fun/ease; we also support them security-wise, so you don't have to get cracked.[/QUOTE]
But if i install all by source, like this howto, i lose all security support too! Or not?
I must recompile if there is a new hole! Or not?

---

### Post by Alessio on 2004-12-06
[QUOTE=filattiera]Thanks for your Howto.
Please, if I want to install LAMP with apt-get, which are the packages to install?

I try:
apache2
libapache2-mod-php4
mysql-server
[/QUOTE]
Is this enough?

---

### Post by Alessio on 2004-12-08
Up :roll:

---

### Post by filattiera on 2004-12-09
Alessio,

it is enough.
I have installed LAMP in this mode.

I am italian like you.
If you have some questions, you can write me also in private by email.

Ciao.
Luca.

---

### Post by an3a on 2004-12-14
[QUOTE=filattiera]Thanks for your Howto.
Please, if I want to install LAMP with apt-get, which are the packages to install?

I try:
apache2
libapache2-mod-php4
mysql-server

They are enough or I can install other in addition?
Thanks.

Ciao.
Luke.

 :-k[/QUOTE]

sorry but my local webserver still don't work with php pages ...
i had installa ubuntu wary, than upgrade to hoary ... 
well, i had install apche2, libapache2-mod-php4 and mysql-server (anch mysql-client) ... if i also install php4 and php4-mysql i receive error message that mysql_connect is an undefined function ...

i read on this post that php4 is not supported, now after install 3 modules up i have to install php from source?

thank for help!

---

### Post by machiner on 2004-12-14
To answer a posters question about Mambo -- that's the package I use to make sites for people.  

It's pretty easy to set up and use on ubuntu - or any distro...if you are having problems let me know and I'll help if I can.,

I am unable to work on my sites currently because I am having a problem with .php pages now after I rolled my own lamp.

If you install apache2 and the mysql-server and mod_php4 from the repository you will have no problem running mambo, however, I could not get the SEO aspect (.htaccess and supporting .php script) to work -- mod_rewrite would never load for me.

Otherwise, you can run and build with mambo without SEF and you'll be good.

I was thinking that if I cannot get the development server to work on my box that I would reinstall ubuntu and apache2 et. al. and change to SEF when I upload my sites to a live host.  That should work fine...your links will work because mod_rewrite will rewrite them on the fly and not point them to bogus spots.

lemme know



------------
machiner

---

### Post by afrifreak on 2004-12-21
@daniel dot stone:

php5 is by no means available in the repositories. I wish it were.

What's your objection to installing apache, mysql and php5 manually?

greetz,

Andres

---

### Post by afrifreak on 2004-12-23
Hi folks,

Right now I'm trying to set up a development server using the howto eNiNjA wrote. It al goes well until the installation of mysql. I get the following output (no I didn't forget the useradd commands, once you entered them they don't need to be entered again):

----------------------
andres@andres:/tmp $  sudo mv mysql-standard-4.1.7-pc-linux-i686 /usr/local/mysql
andres@andres:/tmp $  sudo mv /usr/local/mysql/share/fill_help_tables.sql /usr/local/mysql/support-files
andres@andres:/tmp $  sudo /usr/local/mysql/scripts/mysql_install_db --user=mysql
/usr/local/mysql/scripts/mysql_install_db: line 1: my_print_defaults: command not found
Could not find help file 'fill_help_tables.sql' in ./support-files or inside ..
----------------------

The install script can't find the fill_help_tables.sql file, but I'm sure it is there. What is wrong here?

Andres  :-D

---

### Post by afrifreak on 2004-12-23
Nobody? 
My second option is XAMPP but I prefer the real thing.

---

### Post by offby1 on 2004-12-24
Additionally, it'd sure be nice if there was an apt-friendly way to install Tomcat.  Has anyone in this thread set that one up?

---

### Post by cencami on 2004-12-25
I download apache2 + php4 and mysql and installed them manually And I didn't compile them together. If you are asking WHY? becuase I didn't know any better. So anyway, now my apache2 server is working html pages but it won't browse php files.  when I go to my home page it lists the directory instead of showing me the index.php And when I click on index.php it trys to download it instead of executing it.

So please help me with this. I know I have to do too many adjustments but I don't know where to start from. Ohh I checked and made addtype php lines enable in apache2.conf file already so thats not the problem! 

thanks in advance.

> **eNiNjA]This may not be the best or easiest route, but this is how I setup mine on a fresh Ubuntu install.
  
  Your results may vary...
  
  Development Webserver, Using Apache2, PHP 5, and MySQL 4, Running on Ubuntu Linux
 
 sudo aptitude install build-essential
 sudo apt-get install flex
 sudo apt-get install bison
 sudo apt-get install libgd-dev
 
 download the binary version of MySQL (currently MySQL 4.1.7) from [http://mysql.com]("http://mysql.com")
 download the latest version oh PHP (currently PHP 5.0.2) from [http://php.net]("http://php.net")
 download the latest version of apache 2 (currently Apache 2.0.52) from [http://apache.org]("http://apache.org")
 download the latest libxml2 library (currently libxml2-2.6.15.tar.gz), from [http://xmlsoft.org]("http://xmlsoft.org")
 download the latest zlib library (currently zlib 1.2.1), from [http://gzip.org/zlib]("http://gzip.org/zlib")
 
 :~ $ mv php-5.0.2.tar.gz \
 > libxml2-2.6.15.tar.gz \
 > mysql-standard-4.1.7-pc-linux-i686.tar.gz \
 > httpd-2.0.52.tar.gz \
 > zlib-1.2.1.tar.gz /tmp
 
 cd /tmp
 
 tar -zxvf mysql-standard-4.1.7-pc-linux-i686.tar.gz
 tar -zxvf php-5.0.2.tar.gz
 tar -zxvf httpd-2.0.52.tar.gz
 tar -zxvf libxml2-2.6.15.tar.gz
 tar -zxvf zlib-1.2.1.tar.gz
 
 cd libxml2-2.6.15
 ./configure
 make
 sudo make install
 
 cd /tmp/zlib-1.2.1
 ./configure
 make
 sudo make install
 
 Installing MySQL:
 
 cd /tmp
 
 sudo mv mysql-standard-4.1.7-pc-linux-i686 /usr/local/mysql
 
 sudo groupadd mysql
 
 sudo useradd -g mysql mysql
 
 sudo mv /usr/local/mysql/share/fill_help_tables.sql /usr/local/mysql/support-files
 
 sudo /usr/local/mysql/scripts/mysql_install_db --user=mysql
 
 sudo chown -R root /usr/local/mysql
 
 sudo chgrp -R mysql /usr/local/mysql
 
 sudo chown -R mysql /usr/local/mysql/data
 
 Start it up:
 
 sudo /usr/local/mysql/support-files/mysql.server start
 
 Test it:
 
 /usr/local/mysql/bin/mysql
 
 Secure it:
 
 sudo /usr/local/mysql/bin/mysql -u root
 SET PASSWORD FOR ''@'localhost' = PASSWORD('newpass') said:**
> http://localhost/test.php[/url]

---

### Post by markdav on 2005-01-05
cencami

I've just set up apache2 + php4 + mysql using apt-get (took about 10mins). I found some useful info for this at [http://ubuntuguide.org/index.html](http://ubuntuguide.org/index.html). I hope this helps.

OK - it's not php5 but it works fine. I prefer OO in Java & Python so this isn't a problem for me. I thought that php5 was unstable under apache2 anyway?

offby1 - I can't find a Ubuntu package for Tomcat. I'd prefer to install this using apt as well. Manually installing the binary package from jakarta.apache.org should be pretty straightforward (it's just extracting stuff & setting some vars) but I'll need to find out how to create the startup scripts - anyone got any pointers/urls for a Linux newbie?

cheers

---

### Post by hemebond on 2005-01-17
I can't compile PHP. It quits with this error```
ext/libxml/libxml.lo: file not recognized: File truncated
collect2: ld returned 1 exit status
make: *** [libphp5.la] Error 1
```New version fixed this problem. Everything is now running fine.

---

### Post by akurashy on 2005-01-22
can Ubuntu be used as a distro to host sites? 
i mean i know ubuntu is starting but ina certain future it has to host some sites at least o_o

---

### Post by eNiNjA on 2005-01-22
[QUOTE=afrifreak]Hi folks,
  
 Right now I'm trying to set up a development server using the howto eNiNjA wrote. It al goes well until the installation of mysql. I get the following output (no I didn't forget the useradd commands, once you entered them they don't need to be entered again):
  
  ----------------------
  andres@andres:/tmp $  sudo mv mysql-standard-4.1.7-pc-linux-i686 /usr/local/mysql
  andres@andres:/tmp $  sudo mv /usr/local/mysql/share/fill_help_tables.sql /usr/local/mysql/support-files
  andres@andres:/tmp $  sudo /usr/local/mysql/scripts/mysql_install_db --user=mysql
  /usr/local/mysql/scripts/mysql_install_db: line 1: my_print_defaults: command not found
  Could not find help file 'fill_help_tables.sql' in ./support-files or inside ..
  ----------------------
  
   The install script can't find the fill_help_tables.sql file, but I'm sure it is there. What is wrong here?
   
   Andres  :-D[/QUOTE]
  
  Wow, never really thought there would be much response to this thread. Sorry, I have been, um ...busy...
  
  For the Quote above:
  
  Are you sure you issued the following, and didnt migrate from the original post?
  
    sudo mv /usr/local/mysql/share/fill_help_tables.sql /usr/local/mysql/support-files
 
 If your positive, it was, issue:
 
   sudo /usr/local/mysql/scripts/mysql_install_db --user=mysql , again after the error.
 
 Then go through the rest of the MySQL install, and see if it fires up.
  
  This is one of the *rigs, in the original post, to supress this error.
 
 If this still fails, open the mysql_install_db  script, and have a peek at where it is looking for it.
 
 Just may be time for me to back over the install of this.
 
 Anyone want to donate a computer? =P

---

### Post by eNiNjA on 2005-01-22
[QUOTE=akurashy]can Ubuntu be used as a distro to host sites? 
 i mean i know ubuntu is starting but ina certain future it has to host some sites at least o_o[/QUOTE]
 
 I would love to find a dedicated server host that would lemme try.

---

### Post by eNiNjA on 2005-01-22
> Additionally, it'd sure be nice if there was an apt-friendly way to install Tomcat. Has anyone in this thread set that one up? 
  
 Actually, Tomcat isnt too awful hard to get into this. I ran into shitloads of trouble with Resin, but Tomcat functioned using existing How-Tos found on the net.
   
   I used the one at the DirectAdmin Forums as a base, for example, changing stuff where nessessary.

---

### Post by eNiNjA on 2005-01-22
> **daniels]Hi,
 If you do this, you lose all security support -- when there's a new hole in PHP, your development web server gets rooted. Apache 2.0.52, whatever the latest version of mySQL is, and also, I think, PHP5, are all available in our repositories.
  
 Please use those! We don't just make them for fun/ease said:**
> 
  
  =P
 
  [QUOTE]fun/ease 
 but its also quite fulfilling, to dig in, see whats going on, ..learn..

---

### Post by eNiNjA on 2005-01-22
and, omg, i'm posting from yoper....
  
  *runs like hell [-X
 
 also, hehe, i wish i could change the name of this post, to:
 
 Installing Apache2, PHP5, MySQL, for fun and giggles =P
 
 ..because thats what it is supposed to be about..
 
 oooo, and thanks to everyone for actually reading it
 
 *waves at the ubuntu-geek

---

### Post by eNiNjA on 2005-01-22
[QUOTE=Alessio]Why do you say this? 8-[[/QUOTE]
 
 [http://www.apachefriends.org/en/xampp-linux.html#381](http://www.apachefriends.org/en/xampp-linux.html#381)

---

### Post by eNiNjA on 2005-01-22
[QUOTE=panickedthumb]I have a question for you eninja, and since you've got all this stuff, you may know what I need. I have major issues with file transfers because of my NAT firewall and gaim not getting along. I want to set up a fileserver (using proftpd or whatever works best) with an interface for people to upload files. Whenever someone wants to send me a file, I'll just send them the link to the fileserver, where they'll have an interface for uploading files (a lot of my friends are computer illiterate, so I have to hold their hands with this a bit). Do you know of anything like that? If so, can you incorporate it?[/QUOTE]
 
 You still have this problem?
 
 Im not sure I totally understand, but does your router have a setting for DMZ? Only way I could ever transfer files via IM is to enable it, and input the ip of the machine I'm on.
 
 Had the same problem with torrent stuff, until I did this. Problem is, this machine is now wide open =(.
 
 Using a Linksys Etherfast btw....
 
 Sorry if I'm totally off base on this =/

---

### Post by lillowap on 2005-01-25
[QUOTE=eNiNjA]Wow, never really thought there would be much response to this thread. Sorry, I have been, um ...busy...
  
  For the Quote above:
  
  Are you sure you issued the following, and didnt migrate from the original post?
  
    sudo mv /usr/local/mysql/share/fill_help_tables.sql /usr/local/mysql/support-files
 
 If your positive, it was, issue:
 
   sudo /usr/local/mysql/scripts/mysql_install_db --user=mysql , again after the error.
 
 Then go through the rest of the MySQL install, and see if it fires up.
  
  This is one of the *rigs, in the original post, to supress this error.
 
 If this still fails, open the mysql_install_db  script, and have a peek at where it is looking for it.
 
 Just may be time for me to back over the install of this.
 
 Anyone want to donate a computer? =P[/QUOTE]

Hi to All!

I'm new on Linux so may be I made some mistake.

I have the following errors:

/usr/local/mysql/scripts/mysql_install_db: line 1: my_print_defaults: command not found
Could not find help file 'fill_help_tables.sql' in ./support-files or inside ..

Thank you to anyone can help.

---

### Post by mpowell on 2005-02-11
The original HowTo of this thread is great. However, could someone re-write it from the perspective of apt-get.  I have installed apache-mysql-php according to the ubuntu guide but can't get my xoops test site to install correctly.  It blanks during the install process and can't seem to connect to the mysql database.

Specifically what files need to be changed (i.e. owners, groups, config) and where would they be located based on an apt-get install.

Thanks,

mpowell

---

### Post by Quest-Master on 2005-03-12
[QUOTE=mpowell]The original HowTo of this thread is great. However, could someone re-write it from the perspective of apt-get.  I have installed apache-mysql-php according to the ubuntu guide but can't get my xoops test site to install correctly.  It blanks during the install process and can't seem to connect to the mysql database.

Specifically what files need to be changed (i.e. owners, groups, config) and where would they be located based on an apt-get install.

Thanks,

mpowell[/QUOTE]
 I second this.

:)

---

### Post by CrustyDOD on 2005-03-25
[QUOTE=lillowap]Hi to All!

I'm new on Linux so may be I made some mistake.

I have the following errors:

/usr/local/mysql/scripts/mysql_install_db: line 1: my_print_defaults: command not found
Could not find help file 'fill_help_tables.sql' in ./support-files or inside ..

Thank you to anyone can help.[/QUOTE]

Sorry for a small topic digging :)

Anyway, i had the same problem today while installing mysql using this tutorial. To solve this, move yourself from /tmp folder into /usr/local/mysql and try again! cause /tmp/support-files do not exists :)

Great tutorial!!! Used it myself and it works!

---

### Post by underworld on 2005-03-26
[QUOTE=eNiNjA][http://www.apachefriends.org/en/xampp-linux.html#381](http://www.apachefriends.org/en/xampp-linux.html#381)[/QUOTE]

I second that.

On my development machine I do now use Ubuntu (great Desktop operating system by the way) and for development Xampp as I do already use the new features of PHP5 (OO). This I combine with a firewall so no one can connect neither to mysql or apache on my development machine.

On our server I do however use Gentoo as I can configure it exactly to my needs (USE flags) and it does already have mod_php5.

Greetings,
Daniel

---

### Post by themoddingden on 2005-08-11
Does anyone here have a hand holder guide to setting up virtual host under kubuntu???


I need to host two sites on a 600mhz hp e-pc with 192 meg ram externel storage will be added later.
It has a 40 gig drive in it now.

The sites are:
Computer store
Tech/modding website
mid to low web usage small store and modding site.
email is handeled bye yahoo for the modding site.
Will host some files on the sites linux iso's and drivers .
The modding site will also have a case gallery 

Any help will be greatly helpful.
Thank you.

---

### Post by orev on 2005-09-15
```
:~ $ mv php-5.0.2.tar.gz \
> libxml2-2.6.15.tar.gz \
> mysql-standard-4.1.7-pc-linux-i686.tar.gz \
> httpd-2.0.52.tar.gz \
> zlib-1.2.1.tar.gz /tmp
```

Does this refer to some terminal action, or just moving these files into the root directory?

---

### Post by eNiNjA on 2005-09-21
[QUOTE=orev]```
:~ $ mv php-5.0.2.tar.gz \
> libxml2-2.6.15.tar.gz \
> mysql-standard-4.1.7-pc-linux-i686.tar.gz \
> httpd-2.0.52.tar.gz \
> zlib-1.2.1.tar.gz /tmp
```

Does this refer to some terminal action, or just moving these files into the root directory?[/QUOTE]

It's moving them to /tmp, via the command line. The \ at the end of each line, allows the command to be broken into lines, instead of issuing mv everytime.

---

### Post by robotic_overlord on 2005-09-21
Here is some addition to mysql server setup. 

When i run the command 

root@marvin:/tmp# sudo /usr/local/mysql/scripts/mysql_install_db --user=mysql
/usr/local/mysql/scripts/mysql_install_db: line 85: my_print_defaults: command not found
Could not find help file 'fill_help_tables.sql' in ./support-files or inside ..

**I don't know if this is only in mycase but i had to cd to mysql directory because fil_help_tables.sql could not be found. Hope this helps someome.**

root@marvin:/tmp# cd /usr/local/mysql/

root@marvin:/usr/local/mysql# sudo /usr/local/mysql/scripts/mysql_install_db --user=mysql
Installing all prepared tables
Fill help tables
...........................

---

### Post by eNiNjA on 2007-04-03
If just one.....

....... one at all started a sever | database | icecast server \ shoutcast ....


anyone......

Guess what? My Server is up iika russian cab driver, in love a blondish~blackish Austrialia chickie~doo

---

### Post by iohasexy6881 on 2007-05-15
<snip>

---

### Post by eNiNjA on 2010-03-14
word...

so...how yo dooin?

---

