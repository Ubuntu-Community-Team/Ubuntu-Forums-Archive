---
title: "Howto: Oracle Instant Client Install UPDATE (Ubuntu 7.10 + php5 + oci8.1.2.4)"
date: 2007-12-10
forum: Outdated Tutorials &amp; Tips
---

### Post by backwardselvis on 2007-12-10
[COLOR="Red"]**///NOTES///**[/COLOR]

**HOWTO:** Install Apache2 + PHP5 + InstantClient + oci8 on Ubuntu 7.10

**Overall Objective:** Install PHP5, APACHE2, with Instant Client 11.1 and oci8 libraries in order to connect remotely with an Oracle DB.
[B]
Personal Objective:[/B] I use PHP to interface with several Oracle databases. My scripts will run and extract data for me and then perform a multitude of tasks using the data. 
 
**OS Version: **Ubuntu 7.10 i386 Desktop

**Target Audience:** Nerds who have a basic understanding of the command line, compiling, and PHP. If your skill exceeds this then you can still follow along, but you probably could skip some steps.

**SUPPORT: **I will support this document with updates should others post their findings. I will also do my best to answer questions DIRECTLY related to this doc

**Note#1: **After setting this process up, I reinstalled Ubuntu and went through the process again, step by step, in order to maintain accuracy.

**Note#2:** After logging into Ubuntu, I issue a sudo &#8211;i command in order to maintain my root id throughout the installation process.

**Note#3: **I originally worked off Elmicha's doc until I ran into issues. So I created this doc at length to give a little deeper insight.

**Note#4: **Original .txt is attached to this post should others want to work off of it. Please site myself and Elmicha please.

**[COLOR="Red"]///BEGIN SETUP///[/COLOR]**

Login to a Terminal and issue a sudo -i

```

test@ubuntu-desktop:~$ sudo -i

```

Install Apache2

```

root@ubuntu-desktop:~# apt-get install apache2

```

Install required PHP5 modules and libraries

```

root@ubuntu-desktop:~# apt-get install php5-common php5 php5-dev libapache2-mod-php5 php5-cli

```

Install the build-essential and php-pear packages

```

root@ubuntu-desktop:~# apt-get install build-essential php-pear

```

IMPORTANT! Install libaio1 library. This is what I was having serious issues with originally.

```

root@ubuntu-desktop:~# apt-get install libaio1

```

Download the new Instantclient and SDK zip files from Oracle.

[http://www.oracle.com/technology/tech/oci/instantclient/index.html](http://www.oracle.com/technology/tech/oci/instantclient/index.html)

In my case the files are called Basic.zip and Sdk.zip Initially these files will be saved in my home directory under the Documents folder.
```

/home/ubuntu/Documents/

```

create a directory to house the zip files once they are uncompressed

```

root@ubuntu-desktop:~# mkdir /opt/oracle

```

move the .zip files in the &#8220;Documents&#8221; directory to the /opt/oracle directory

```

root@ubuntu-desktop:~# mv /home/ubuntu/Documents/*.zip /opt/oracle

```

Change to the /opt/oracle directory

```

root@ubuntu-desktop:~# cd /opt/oracle

```

Unzip the files

```

root@ubuntu-desktop:/opt/oracle# unzip \*.zip

```

rename instantclient directory 
```

root@ubuntu-desktop:/opt/oracle# mv instantclient_11_1 instantclient

```

Change directory to instantclient, list the files
```

root@ubuntu-desktop:/opt/oracle# cd instantclient

```

Create symbolic links
```

root@ubuntu-desktop:/opt/oracle# ln &#8211;s libclntsh.so.11.1 libclntsh.so
root@ubuntu-desktop:/opt/oracle# ln &#8211;s libocci.so.11.1 libocci.so

```

Create a source directory under /opt/oracle . This is where we will house the oci8 libraries.
```

root@ubuntu-desktop:/opt/oracle# mkdir /opt/oracle/src

```

Change the directory to /opt/oracle/src and download the oci8 tar using pecl
```

root@ubuntu-desktop:/opt/oracle# cd /opt/oracle/src

```
```

root@ubuntu-desktop:/opt/oracle/src# pecl download oci8

```

Untar the oci8 libraries
```

root@ubuntu-desktop:/opt/oracle/src# tar xvf oci8-1.2.4.tgz

```

Change to the newly created oci8-1.2.4 directory and issue the following commands
```

root@ubuntu-desktop:/opt/oracle/src# cd oci8-1.2.4

```
```

root@ubuntu-desktop:/opt/oracle/src/oci8-1.2.4# phpize

```

Set the ORACLE_HOME  environment variable
```

root@ubuntu-desktop:/opt/oracle/src/oci8-1.2.4# export ORACLE_HOME=/opt/oracle/instantclient

```
```

root@ubuntu-desktop:/opt/oracle/src/oci8-1.2.4# echo $ORACLE_HOME
/opt/oracle/instantclient

```

Configure oci8 to install with the necessary parameters
```

root@ubuntu-desktop:/opt/oracle/src/oci8-1.2.4# ./configure --with-oci8=share,instantclient,/opt/oracle/instantclient

```

run make to compile
```

root@ubuntu-desktop:/opt/oracle/src/oci8-1.2.4# make

```

install oci8
```

root@ubuntu-desktop:/opt/oracle/src/oci8-1.2.4# make install

```

insert the extension=oci8.so into the php.ini and cli.ini files
```

root@ubuntu-desktop:/opt/oracle/src/oci8-1.2.4# echo extension=oci8.so >> /etc/php5/apache2/php.ini
root@ubuntu-desktop:/opt/oracle/src/oci8-1.2.4# echo extension=oci8.so >> /etc/php5/cli/php.ini

```

restart apache
```

root@ubuntu-desktop:/opt/oracle/src/oci8-1.2.4# /etc/init.d/apache2 restart 

```

create a phpinfo.php file in /var/www
```

root@ubuntu-desktop:/opt/oracle/src/oci8-1.2.4# vi /var/www/phpinfo.php

```

Now go to your browser and run the phpinfo file and look for the oci8 module

```

http://localhost/phpinfo.php

```

Create a empty script to test your Oracle Connection
```

root@ubuntu-desktop:/opt/oracle/src/oci8-1.2.4# vi /home/ubuntu/oratest.php

```

Copy and Paste this PHP code into your script and change the variables accordingly
[PHP]
<?php

//oracle connection variables
$ora_user = 	'YOUR_USERNAME';	//username
$ora_pass =	'YOUR_PASS';			//user password
$ora_host =	'SERVER_IP_OF_ORACLE"';		//host name or server ip address
$ora_db   = 	'YOUR_DATABASE';	//database name

// place variable into oci_connect function, then place funtion in variable
$ora_conn = oci_connect($ora_user,$ora_pass,'//'.$ora_host.'/'.$ora_db);

// error handling
if (!ora_conn){							// if variable $ora_conn fails to connect
// do the following if it fails
$ora_conn_erno = oci_error(); 			// insert oci_error() function into variable
echo ($ora_conn_erno['message']."\n"); 	// print the $ora_conn_erno variable/oci_error() function selecting only the message (human readable)
oci_close($ora_conn); 					// close the connection just in case php doesn't close it
} else {
// if it doesn't fail it will proceed with the rest of the script
echo "Connection Succesful\n"; 	//echo message if connection does not error
oci_close($ora_conn); 			// close the connection
}

?>
[/PHP]                                                                                                                                   
                                                                                                                          
Test the connection
```

root@ubuntu-desktop:/opt/oracle/src/oci8-1.2.4# php /home/ubuntu/oratest.php
Connection Succesful
root@ubuntu-desktop:/opt/oracle/src/oci8-1.2.4#

```

---

### Post by Boodah on 2008-02-18
**Great job Elvis!! **
I just completed the install to connect to an Oracle 10g instance with almost no problems. Below is all I found.

- typo on step 23, code blocks are out of whack
- step 25 you might want to mention 'Your IP Address' is 'Your IP Address:Port No' 
- step 25 code block didn't work to well with Nano at line 21
- step 27 file name should be oratest.php

Again great job!!

----------------
Now playing: [Salt Tank - Eugina 2000 (Progressive Summer Mix)](http://www.foxytunes.com/artist/salt+tank/track/eugina+2000+(progressive+summer+mix))
via [FoxyTunes](http://www.foxytunes.com/signatunes/)

---

### Post by danharper on 2008-07-02
Great tut,

I get this message when I try the script

Parse error: syntax error, unexpected T_STRING in /var/www/drupal-6.1/kpi/bo.php on line 22

Cheers Dan

---

### Post by danharper on 2008-07-02
> **danharper said:**
> Great tut,

I get this message when I try the script

Parse error: syntax error, unexpected T_STRING in /var/www/drupal-6.1/kpi/bo.php on line 22

Cheers Dan

Sorry my fault can't copy and paste correctly, although I do get this message now

Warning: oci_connect() [function.oci-connect]: ORA-12514: TNS:listener does not currently know of service requested in connect descriptor in /var/www/drupal-6.1/kpi/bo.php on line 14

Cheers Dan

---

### Post by backwardselvis on 2008-07-18
Dan,

I see that you are using Drupal and was wondering how stable Oracle support was with the application.

When you use the supplied script what happens?


-later

---

### Post by danharper on 2008-07-19
I'm actually running drupal on mysql, the reason I need to use oracle is to write some webpages that retrieve data from one of our other databases.

The error I get when I run the script through a web borwser is as follows


Warning: oci_connect() [function.oci-connect]: ORA-12514: TNS:listener does not currently know of service requested in connect descriptor in /var/www/drupal-6.1/bo/bo.php on line 14
Connection Succesful
Warning: oci_close() expects parameter 1 to be resource, boolean given in /var/www/drupal-6.1/bo/bo.php on line 28


Cheers Dan

---

### Post by backwardselvis on 2008-07-22
It obviously isn't talking to the oracle server. I am wondering, is the tns listener started or could it be throwing errors?

---

### Post by danharper on 2008-07-23
I have sorted it, I didn't understand what the database name was. I think this actually refers to what is known as the service in Oracle.

Any who I got it to work, great tutorial thanks very much.

Dan

---

### Post by stashj on 2008-08-05
You utterly rock!

Straight through first time without a single problem and I'm up and running. You sir, are a gent.

Thank you!

---

