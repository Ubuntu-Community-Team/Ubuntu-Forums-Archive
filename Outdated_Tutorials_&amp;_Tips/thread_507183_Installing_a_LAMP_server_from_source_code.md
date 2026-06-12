---
title: "Installing a LAMP server from source code"
date: 2007-07-22
forum: Outdated Tutorials &amp; Tips
---

### Post by p_quarles on 2007-07-22
I found that the default installation of Apache, MySQL and PHP in the server edition of Ubuntu has some frustrating limitations. The file structure, for instance, is sufficiently different from the source builds of these applications that I found it very difficult to follow some of the tutorials I found on implementing advanced features. Because of this, I decided to reinstall these applications from the latest source code.

Much of this guide is based upon instructions I received from Julie Meloni's _Teach Yourself PHP, MySQL and Apache_, though these basic procedures are widely available in many locations. I modified these instructions considerably based on my experience installing these applications in Ubuntu. Specifically, I performed this installation on an Intel Pentium 4 1.8 GHz machine with 384 MB of memory running the 32-bit version of Ubuntu 7.04.

Obviously, if you're happy with your LAMP server setup, there is no reason for you to follow this how-to. I just wanted to share my experience with those who might also find it useful.

I am offering this tutorial "as is," meaning that while I will try to answer any questions you may have, I don't feel confident enough to promise any support. This is a very basic setup, so this is not recommended for anyone who doesn't know (or doesn't want to bother learning) how to further configure these applications. This will, however, give you an installation that integrates the three for the purposes of web development. 

As long as you follow the recommended file placement given below, this is very easy to undo. Simply delete the directories containing the respective applications, which will all be subdirectories of /usr/local/

**Preparing**

I was able to retrieve all necessary dependencies for this source code using apt-get:
```
sudo apt-get build-dep apache2 php5 mysql-server
```**Installing MySQL**

You can find the latest source code for MySQL at [http://dev.mysql.com/downloads](http://dev.mysql.com/downloads)

Get the source (tar.gz) file appropriate for your system, and place it in the directory /usr/src/

Before unpacking, you need to create a user for the MySQL daemon. If you have had another version of MySQL running on your server in the past, you will already have this user.

```
sudo groupadd mysql
sudo useradd -g mysql mysql
```Now unpack the tarball:
```
cd /usr/local
sudo gunzip < /usr/src/mysql-5.0.45-linux-i686.tar.gz | sudo tar xvf -
```Make a symbolic link to the MySQL directory (unless you want to type out the entire version number to get there)
```
sudo ln -s mysql-5.0.45-linux-i686 mysql
cd mysql
```Open the file called INSTALL-BINARY (using the cat command, or a text editor). This provides you with very accurate instructions for getting through the rest of the basic installation. I found two things useful at this point: 1) copying the INSTALL-BINARY file to a separate window while I went through the instructions. 2) I found it more convenient to log in as root (sudo su or sudo bash) during this process. This saves you from having to sudo every single command. If you do this, remember to type "exit" to get back to user mode after you're done.

Finally, to start MySQL in safe mode (non-root process), type:```
sudo bin/mysqld_safe --user=mysql &
```**Installing Apache**

Get the latest source code from [http://httpd.apache.org/download.cgi](http://httpd.apache.org/download.cgi)
and place it in the /usr/src/ directory and unpack it:
```
sudo gunzip < httpd-2.2.4.tar.gz | sudo tar xvf -
```The following "configure" command will setup Apache in preparation to share objects with PHP (again, more convenient to login as root):
```
cd apache2
./configure --prefix=/usr/local/apache2 --enable-module=so
```If you get a "configure ok" message at the end of this process, you can proceed to enter the "make" and "make install" commands to finish compiling and installing the code. After this is done, check to see if installation was successful:
```
sudo /usr/local/apache2/bin/httpd -v
```To start the web server daemon, type:
```
sudo /usr/local/apache2/bin/apachectl start
```**Installing PHP**

Get the latest source code from [http://www.php.net/downloads.php#v5](http://www.php.net/downloads.php#v5)
and place it in the /usr/src/ directory. 

Unpack it:
```
sudo gunzip < /usr/src/php-5.2.3.tar.gz | sudo tar xvf -
```And configure it to work with Apache and MySQL(I used a root login):
```
cd php-5.2.3
./configure --prefix=/usr/local/php --with-mysqli=/usr/local/mysql/bin/mysql_config --with-apxs2=/usr/local/apache2/bin/apxs
```This will take some time. After this, you can use the "make" and "make install" commands to finish the work.

To test PHP's web-readiness, make a file called info.php and place it in the /usr/local/apache2/htdocs/ directory. The file should contain the PHP script:
```
<?php phpinfo(); ?>
``` Point your browser to the {hostname}/info.php . You should be greeted with information about the PHP version and its installation on your system. 

One other minor tweak you may want: use the recommended php.ini file by typing:
```
sudo cp php.ini-recommended /usr/local/lib/php.ini
```Please feel free to suggest additions, request corrections, or add any other information that might help streamline or optimize this installation.

---

### Post by infamous-online on 2007-07-23
well i'm trying to compile php 5.2.3 from the source using apache 2.0.59 on one machine and 2.2.4 on another, and yet they yeild the same error.

> **infamous-online said:**
> this is upsetting dearly, for whatever reason php5 keeps thinking my apache version is the 1.0 series of the 2.0 series. what's the problem GRRR!!! apache 2.0.59 is built from the source, and so is php, but why can't i get past this error.

Configuring SAPI modules
checking for AOLserver support... no
checking for Apache 1.x module support via DSO through APXS... no
checking for Apache 1.x module support... no
checking for mod_charset compatibility option... yes
checking for Apache 2.0 filter-module support via DSO through APXS... no
checking for Apache 2.0 handler-module support via DSO through APXS... expr: non-numeric argument
**configure: error: You have enabled Apache 2 support while your server is Apache 1.3.  Please use the appropiate switch --with-apxs (without the 2)**


here's the code in question used for php5 

./configure --prefix=/php5 --libexecdir=/usr/lib/apache2/modules  --with-apxs2=/usr/lib/apache2/bin/apxs  

it doesn't matter if i used the apxs2filter or the apxs2 NONE of the following will allow the script to go any further, but if i used the with-apxs feature it's continues on, and fails during the middle of the make process. please i know someone else has went through this, so how did you get past this? :confused:

---

### Post by p_quarles on 2007-07-23
I never got such an error, so I don't know how much help I'll be. That said, I wonder if you might have an old version of Apache running on both of these machines. Maybe far-fetched, but worth checking:
```
sudo /etc/init.d/apache restart
```
This should give you an error. If it doesn't, you might have an old copy running. 

Aside from that, the best suggestion I can give is to use PHP ./configure options that I posted above, corrected for your Apache2 file paths and minus the MySQL options (assuming you aren't using that).

---

### Post by infamous-online on 2007-07-23
Nope i don't like to use the stuff installed from the repository so it can't be that, i never received this error before. I haven't the slightest idea as to how to fix it.

the problem isn't with mysql, it's only php. everything else is installed and working correctly, however php won't cooperate! :(

---

### Post by p_quarles on 2007-07-23
Yeah, that sucks. 

My suggestion actually didn't have anything to do with SQL, just suggesting that you remove the second argument of your ./configure command. Just to see if it works.

Also, just FYI, you don't necessarily need to have used the repos to get the Debian build of Apache on your system . . . if you installed either of these boxes with Ubuntu served edition CD, it could be on there. Unlikely, I know.

One more thing to try, though. What's the output of this?
```
/usr/lib/apache2/bin/httpd -v
```

---

### Post by infamous-online on 2007-07-23
> **p_quarles said:**
> Yeah, that sucks. 

My suggestion actually didn't have anything to do with SQL, just suggesting that you remove the second argument of your ./configure command. Just to see if it works.

Also, just FYI, you don't necessarily need to have used the repos to get the Debian build of Apache on your system . . . if you installed either of these boxes with Ubuntu served edition CD, it could be on there. Unlikely, I know.

One more thing to try, though. What's the output of this?
```
/usr/lib/apache2/bin/httpd -v
```

hey man, i think i figure out the problem, i believe it was what i had in the script. **-libexecdir=/usr/lib/apache2/modules** --with-apxs2=/usr/lib/apache2/bin/apxs

i removed the line in bold print, and so far the installation has moved further than what it has before. the real test will be once everything is complete though. that's when i'll know if it was a success or not. i'll keep you posted.

---

