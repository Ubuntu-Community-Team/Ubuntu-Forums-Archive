---
title: "New security updates broke website"
date: 2012-02-17
forum: New to Ubuntu
---

### Post by GaryDev on 2012-02-17
I am running a new VM install using Ubuntu Linux 10.04.3 (Linux 2.6.32-38-generic on x86_64) along with Webmin 1.580. The server is nothing fancy, pretty much just a base LAMP install, which was configured to process PHP files first instead of HTML files.
 
Last night I ran Webmin, and it advised there were 7 or 8 updates, all labeled as Lucid security fixes, so I told Webmin to install them. It did... and now all hell is breaking loose.
 
According to the var/cache/apt/archives, the following updates were installed:
 
update-manager-core_1%3a0.134.11.2_amd64.deb
libpng12-0_1.2.42-1ubuntu2.3_amd64.deb
apache2.2-common_2.2.14-5ubuntu8.8_amd64.deb
apache2.2-bin_2.2.14-5ubuntu8.8_amd64.deb
apache2-utils_2.2.14-5ubuntu8.8_amd64.debapache2-mpm-prefork_2.2.14-5ubuntu8.8_amd64.deb
apache2-mpm-worker_2.2.14-5ubuntu8.8_amd64.deb
apache2_2.2.14-5ubuntu8.8_amd64.deb
 
Since putting these updates in, the web server side of things no longer processes PHP files... instead, it offers them as a download. It does process HTML.
 
Whats worse, the "downloaded" php file shows the other files included in other folders and one can 'http' to that file which the server wants to download to your system... including files that contain database connections. For example, we have a standard "includes" folder in 'www', and the .htaccess file there has the following:
 
<Files "constants.php">
Order Allow,Deny
Deny from All
</Files>
<Files "connection.php">
Order Allow,Deny
Deny from All
</Files>
<Files "functions.php">
Order Allow,Deny
Deny from All
</Files>
 
Yet, I can http to those exact files AND get the opportunity to 'download' them.
 
Needless to say, this is really really bad...
 
I can of course, re-image the VM and start all over again BUT.. if these same pacakges get installed...
 
How can I solve this?

---

### Post by CharlesA on 2012-02-17
I just checked my lucid box and I had those updates installed yesterday and it renders php fine.

See what this says:

```
dpkg -l | grep apache
```

---

### Post by Tony Flury on 2012-02-17
Looks like the apache upgrade broke your file type config. Look through your apache config files and see where the config should be that tells apache to execute PHP -rather than serve them.

---

### Post by GaryDev on 2012-02-17
Appreciate the fast responses.. I did just update the original post with a partial from the dpkg.log file...
 
ii  apache2                         2.2.14-5ubuntu8.8                 Apache HTT                      P Server metapackage
ii  apache2-mpm-worker              2.2.14-5ubuntu8.8                 Apache HTT                      P Server - high speed threaded mod
ri  apache2-utils                   2.2.14-5ubuntu8.8                 utility pr                      ograms for webservers
ri  apache2.2-bin                   2.2.14-5ubuntu8.8                 Apache HTT                      P Server common binary files
ii  apache2.2-common                2.2.14-5ubuntu8.8                 Apache HTT                      P Server common files
rc  libapache2-mod-php5             5.3.2-1ubuntu4.14                 server-sid                      e, HTML-embedded scripting languag

^^^^^ in putty, thats the grep output.
 
As for the config files, I am not exactly sure where to look and what to look for. :) There is a reason why I use Webmin, because I am really not a strong command prompt type user. I know enough basics to realize I am dangerous, therefore I try to keep things to Webmin.

---

### Post by GaryDev on 2012-02-17
Trying various things, made no changes to anything (other than starting and stopping servers) and now I am getting errors in trying to start Apache, saying it won't load..
 
# /etc/init.d/apache2 restart
 * Restarting web server apache2                                                apache2: Syntax error on line 204 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/mods-enabled/php5.load: Cannot load /usr/lib/apache2/modules/libphp5.so into server: /usr/lib/apache2/modules/libphp5.so: cannot open shared object file: No such file or directory

And I did a forced install of php side... I give up.
 
Will have the ISP re-image the server and start from scratch... *again*

---

### Post by CharlesA on 2012-02-17
Purge PHP and reinstall it.

```
sudo apt-get purge php5 && sudo apt-get install php5
```

---

### Post by GaryDev on 2012-02-17
Thanks Charles, I am in the process of taking a backup, and as soon as that is finished I will try your suggestion. Fingers crossed!

---

### Post by GaryDev on 2012-02-17
Well, the purge said it was not installed, yet it was running in Webmin. The install side ran and 1 package was newly installed.  Testing the site with just index.php as the entry within Directory Indexing... and... same old. It is not running the php side of things and makes the website look like a file browser.
 
I guess it's time to re-image the VM.
 
By the way, the errors from apache above... well, I went in and checked those files. The library it needed was there, the folder was there, the files were there... the "so" lib was dated Feb 10th, which is when things were first stared with this VM.
 
I appreciate the help and advice, but it seems something has drastically gone wrong. Maybe there is a hiccup in the file system on the VM machine... *shrug*... I don't see any other options at this point other than starting from scratch again.

---

### Post by lisati on 2012-02-17
I've had a similar problem of PHP files wanting to be downloaded instead of rendering. This has usually happened after a fresh install. I have usually found the information here helpful when this happens: [https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting_PHP_5](https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting_PHP_5)

---

