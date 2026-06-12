---
title: "Php not working on Ubuntu 22.04"
date: 2022-05-22
forum: New to Ubuntu
---

### Post by gale85 on 2022-05-22
I don't know why but php will not work in the mentioned version of Ubuntu, although I checked if php and apache server are installed and activated. I have no idea where the problem might be.

---

### Post by #&amp;thj^% on 2022-05-22
More info needed, can we see this:
```
php -v
```
Also In "My Use"n I'll use some extensions :
```
sudo apt install php8.1-common php8.1-mysql php8.1-xml php8.1-xmlrpc php8.1-curl php8.1-gd php8.1-imagick php8.1-cli php8.1-dev php8.1-imap php8.1-mbstring php8.1-opcache php8.1-soap php8.1-zip php8.1-redis php8.1-intl -y
```
That code will auto download and install the above.
I also EDIT: For PHP 8.1 with Apache the php.ini location will be in following directory.
```
sudo nano /etc/php/8.1/apache2/php.ini
```
and add or change to: 
```
upload_max_filesize = 32M 
post_max_size = 48M 
memory_limit = 256M 
max_execution_time = 600 
max_input_vars = 3000 
max_input_time = 1000
```
 you need to restart your Apache for the changes to take effect.

---

### Post by gale85 on 2022-05-26
I just installed everything you told me and I restarted the apache server, but it won't start the php script. Here is the output of the php -v command > PHP 8.1.6 (cli) (built: May 17 2022 16:46:54) (NTS)Copyright (c) The PHP Group
Zend Engine v4.1.6, Copyright (c) Zend Technologies
    with Zend OPcache v8.1.6, Copyright (c), by Zend Technologies


---

### Post by #&amp;thj^% on 2022-05-26
First I did not tell you install anything, I offered what I use and may not be what you will need.
Ok buckle up  we will be here a while, information/details is *vital* to how or if I'll respond._ I would of liked to of seen the output you used? (Why it failed)_
If you can include that it would be very helpful.
here's a short list I need to see as well:
```
cat /etc/apache2/mods-enabled/php8.0.load
```
also:
```
dpkg -l | grep php8
```
this as well:
```
systemctl status apache2
\u25cf apache2.service - The Apache HTTP Server
     Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor prese>
     Active: active (running) since Thu 2022-05-26 10:03:30 EDT; 18min ago
       Docs: https://httpd.apache.org/docs/2.4/
    Process: 521 ExecStart=/usr/sbin/apachectl start (code=exited, status=0/SUC>
   Main PID: 573 (apache2)
      Tasks: 55 (limit: 4627)
     Memory: 7.7M
        CPU: 126ms
     CGroup: /system.slice/apache2.service
             \u251c\u2500573 /usr/sbin/apache2 -k start
             \u251c\u2500574 /usr/sbin/apache2 -k start
             \u2514\u2500575 /usr/sbin/apache2 -k start

```
Let get the works also:
```
sudo ufw status
```
Make sure you have allowed necessary port's:
```
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
```

---

### Post by gale85 on 2022-05-26
cat /etc/apache2/mods-enabled/php8.1.load
> cat: /etc/apache2/mods-enabled/php8.1.load: No such file or directory
dpkg -l | grep php8
> ii  libapache2-mod-php8.1                      8.1.6-1+ubuntu22.04.1+deb.sury.org+1         amd64        server-side, HTML-embedded scripting language (Apache 2 module)
ii  php-symfony-polyfill-php80                 1.24.0-1ubuntu2                              all          Symfony polyfill backporting some PHP 8.0+ features to lower PHP versions
ii  php-symfony-polyfill-php81                 1.24.0-1ubuntu2                              all          Symfony polyfill backporting some PHP 8.1+ features to lower PHP versions
rc  php8.0-bz2                                 8.0.8-1ubuntu0.3                             amd64        bzip2 module for PHP
rc  php8.0-cli                                 8.0.8-1ubuntu0.3                             amd64        command-line interpreter for the PHP scripting language
rc  php8.0-common                              8.0.8-1ubuntu0.3                             amd64        documentation, examples and common module for PHP
rc  php8.0-curl                                8.0.8-1ubuntu0.3                             amd64        CURL module for PHP
rc  php8.0-gd                                  8.0.8-1ubuntu0.3                             amd64        GD module for PHP
rc  php8.0-mbstring                            8.0.8-1ubuntu0.3                             amd64        MBSTRING module for PHP
rc  php8.0-mysql                               8.0.8-1ubuntu0.3                             amd64        MySQL module for PHP
rc  php8.0-opcache                             8.0.8-1ubuntu0.3                             amd64        Zend OpCache module for PHP
rc  php8.0-readline                            8.0.8-1ubuntu0.3                             amd64        readline module for PHP
rc  php8.0-xml                                 8.0.8-1ubuntu0.3                             amd64        DOM, SimpleXML, XML, and XSL module for PHP
rc  php8.0-zip                                 8.0.8-1ubuntu0.3                             amd64        Zip module for PHP
ii  php8.1                                     8.1.6-1+ubuntu22.04.1+deb.sury.org+1         all          server-side, HTML-embedded scripting language (metapackage)
ii  php8.1-bz2                                 8.1.6-1+ubuntu22.04.1+deb.sury.org+1         amd64        bzip2 module for PHP
ii  php8.1-cli                                 8.1.6-1+ubuntu22.04.1+deb.sury.org+1         amd64        command-line interpreter for the PHP scripting language
ii  php8.1-common                              8.1.6-1+ubuntu22.04.1+deb.sury.org+1         amd64        documentation, examples and common module for PHP
ii  php8.1-curl                                8.1.6-1+ubuntu22.04.1+deb.sury.org+1         amd64        CURL module for PHP
ii  php8.1-dev                                 8.1.6-1+ubuntu22.04.1+deb.sury.org+1         amd64        Files for PHP8.1 module development
ii  php8.1-fpm                                 8.1.6-1+ubuntu22.04.1+deb.sury.org+1         amd64        server-side, HTML-embedded scripting language (FPM-CGI binary)
ii  php8.1-gd                                  8.1.6-1+ubuntu22.04.1+deb.sury.org+1         amd64        GD module for PHP
ii  php8.1-igbinary                            3.2.7+2.0.8-1+ubuntu22.04.1+deb.sury.org+1   amd64        igbinary PHP serializer
ii  php8.1-imagick                             3.7.0-2+ubuntu22.04.1+deb.sury.org+1         amd64        Provides a wrapper to the ImageMagick library
ii  php8.1-imap                                8.1.6-1+ubuntu22.04.1+deb.sury.org+1         amd64        IMAP module for PHP
ii  php8.1-intl                                8.1.6-1+ubuntu22.04.1+deb.sury.org+1         amd64        Internationalisation module for PHP
ii  php8.1-mbstring                            8.1.6-1+ubuntu22.04.1+deb.sury.org+1         amd64        MBSTRING module for PHP
ii  php8.1-mysql                               8.1.6-1+ubuntu22.04.1+deb.sury.org+1         amd64        MySQL module for PHP
ii  php8.1-opcache                             8.1.6-1+ubuntu22.04.1+deb.sury.org+1         amd64        Zend OpCache module for PHP
ii  php8.1-readline                            8.1.6-1+ubuntu22.04.1+deb.sury.org+1         amd64        readline module for PHP
ii  php8.1-redis                               5.3.7+4.3.0-1+ubuntu22.04.1+deb.sury.org+1   amd64        PHP extension for interfacing with Redis
ii  php8.1-soap                                8.1.6-1+ubuntu22.04.1+deb.sury.org+1         amd64        SOAP module for PHP
ii  php8.1-xml                                 8.1.6-1+ubuntu22.04.1+deb.sury.org+1         amd64        DOM, SimpleXML, XML, and XSL module for PHP
ii  php8.1-xmlrpc                              3:1.0.0~rc3-4+ubuntu22.04.1+deb.sury.org+1   amd64        XML-RPC servers and clients functions for PHP
ii  php8.1-zip                                 8.1.6-1+ubuntu22.04.1+deb.sury.org+1         amd64        Zip module for PHP

---

### Post by #&amp;thj^% on 2022-05-26
One more, also reread my edits in post #4
```
a2query -m php8.1

```
I had a type o on my cat code use:
```
cat /etc/apache2/mods-enabled/php8.1.load

```
This must of been an upgrade to 22.04 and not a clean fresh install.
mine only shows:
```
dpkg -l | grep php8
ii  libapache2-mod-php8.1                      8.1.2-1ubuntu2                          amd64        server-side, HTML-embedded scripting language (Apache 2 module)
ii  php8.1                                     8.1.2-1ubuntu2                          all          server-side, HTML-embedded scripting language (metapackage)
ii  php8.1-cli                                 8.1.2-1ubuntu2                          amd64        command-line interpreter for the PHP scripting language
ii  php8.1-common                              8.1.2-1ubuntu2                          amd64        documentation, examples and common module for PHP
ii  php8.1-opcache                             8.1.2-1ubuntu2                          amd64        Zend OpCache module for PHP
ii  php8.1-readline                            8.1.2-1ubuntu2                          amd64        readline module for PHP

```

---

### Post by gale85 on 2022-05-26
systemctl status apache2
> &#9679; apache2.service - The Apache HTTP Server     Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: en>
     Active: active (running) since Thu 2022-05-26 15:06:23 CEST; 1h 43min ago
       Docs: [https://httpd.apache.org/docs/2.4/](https://httpd.apache.org/docs/2.4/)
    Process: 22454 ExecStart=/usr/sbin/apachectl start (code=exited, status=0/SUCCES>
   Main PID: 22458 (apache2)
      Tasks: 8 (limit: 7040)
     Memory: 7.2M
        CPU: 436ms
     CGroup: /system.slice/apache2.service
             &#9500;&#9472;22458 /usr/sbin/apache2 -k start
             &#9500;&#9472;22459 /usr/sbin/apache2 -k start
             &#9500;&#9472;22460 /usr/sbin/apache2 -k start
             &#9500;&#9472;22461 /usr/sbin/apache2 -k start
             &#9500;&#9472;22462 /usr/sbin/apache2 -k start
             &#9500;&#9472;22463 /usr/sbin/apache2 -k start
             &#9500;&#9472;22464 /usr/sbin/apache2 -k start
             &#9492;&#9472;22540 /usr/sbin/apache2 -k start


&#1084;&#1072;&#1112; 26 15:06:23 gale85-EP35-DS3R systemd[1]: Starting The Apache HTTP Server...
&#1084;&#1072;&#1112; 26 15:06:23 gale85-EP35-DS3R systemd[1]: Started The Apache HTTP Server.
sudo ufw status
> Status: inactive

---

### Post by #&amp;thj^% on 2022-05-26
gale85 please help me out by reading post #4 again.
Have you ran an Apache server before this?
Let's get ufw up and running first.
```
 sudo systemctl enable ufw
sudo systemctl start --now ufw
```
then open the needed ports
```
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
```
If I don't get the needed Info from you, I can't help you...in fact it could make things worse.
This is all you will need to start with:
```
apt policy apache2 php libapache2-mod-php
apache2:
  Installed: 2.4.52-1ubuntu4
  Candidate: 2.4.52-1ubuntu4
  Version table:
 *** 2.4.52-1ubuntu4 500
        500 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        100 /var/lib/dpkg/status
php:
  Installed: 2:8.1+92ubuntu1
  Candidate: 2:8.1+92ubuntu1
  Version table:
 *** 2:8.1+92ubuntu1 500
        500 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        500 http://ca.archive.ubuntu.com/ubuntu jammy/main i386 Packages
        100 /var/lib/dpkg/status
libapache2-mod-php:
  Installed: 2:8.1+92ubuntu1
  Candidate: 2:8.1+92ubuntu1
  Version table:
 *** 2:8.1+92ubuntu1 500
        500 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        500 http://ca.archive.ubuntu.com/ubuntu jammy/main i386 Packages
        100 /var/lib/dpkg/status

```
I need to see this:
```
cat /etc/apache2/mods-enabled/php8.1.load
```

---

### Post by gale85 on 2022-05-26
sudo systemctl enable ufw
> Synchronizing state of ufw.service with SysV service script with /lib/systemd/systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install enable ufw
sudo ufw allow 80/tcp
> Rules updated
Rules updated (v6)
sudo ufw allow 443/tcp
> Rules updated
Rules updated (v6)
cat /etc/apache2/mods-enabled/php8.1.load
> cat: /etc/apache2/mods-enabled/php8.1.load: No such file or directoryI'm sorry, I thought I sent you the command

apt policy apache2 php libapache2-mod-php
> apache2:  Installed: 2.4.52-1ubuntu4
  Candidate: 2.4.52-1ubuntu4
  Version table:
 *** 2.4.52-1ubuntu4 500
        500 [http://rs.archive.ubuntu.com/ubuntu](http://rs.archive.ubuntu.com/ubuntu) jammy/main amd64 Packages
        100 /var/lib/dpkg/status
php:
  Installed: 2:8.1+92+ubuntu22.04.1+deb.sury.org+1
  Candidate: 2:8.1+92+ubuntu22.04.1+deb.sury.org+1
  Version table:
 *** 2:8.1+92+ubuntu22.04.1+deb.sury.org+1 500
        500 [https://ppa.launchpadcontent.net/ondrej/php/ubuntu](https://ppa.launchpadcontent.net/ondrej/php/ubuntu) jammy/main amd64 Packages
        500 [https://ppa.launchpadcontent.net/ondrej/php/ubuntu](https://ppa.launchpadcontent.net/ondrej/php/ubuntu) jammy/main i386 Packages
        100 /var/lib/dpkg/status
     2:8.1+92ubuntu1 500
        500 [http://rs.archive.ubuntu.com/ubuntu](http://rs.archive.ubuntu.com/ubuntu) jammy/main amd64 Packages
        500 [http://rs.archive.ubuntu.com/ubuntu](http://rs.archive.ubuntu.com/ubuntu) jammy/main i386 Packages
libapache2-mod-php:
  Installed: 2:8.1+92+ubuntu22.04.1+deb.sury.org+1
  Candidate: 2:8.1+92+ubuntu22.04.1+deb.sury.org+1
  Version table:
 *** 2:8.1+92+ubuntu22.04.1+deb.sury.org+1 500
        500 [https://ppa.launchpadcontent.net/ondrej/php/ubuntu](https://ppa.launchpadcontent.net/ondrej/php/ubuntu) jammy/main amd64 Packages
        500 [https://ppa.launchpadcontent.net/ondrej/php/ubuntu](https://ppa.launchpadcontent.net/ondrej/php/ubuntu) jammy/main i386 Packages
        100 /var/lib/dpkg/status
     2:8.1+92ubuntu1 500
        500 [http://rs.archive.ubuntu.com/ubuntu](http://rs.archive.ubuntu.com/ubuntu) jammy/main amd64 Packages
        500 [http://rs.archive.ubuntu.com/ubuntu](http://rs.archive.ubuntu.com/ubuntu) jammy/main i386 Packages

---

### Post by gale85 on 2022-05-26
a2query -m php8.1
> No module matches php8.1
Yes it is an upgrade

---

### Post by #&amp;thj^% on 2022-05-26
> **gale85 said:**
> 

I'm sorry, I thought I sent you the command


That  one was my fault in post 4, but there is one problem so far.
IE:
```
cat /etc/apache2/mods-enabled/php8.1.load
# Conflicts: php5
# Depends: mpm_prefork
LoadModule php_module /usr/lib/apache2/modules/libphp8.1.so

```
is how it should show.
what is the output for this;
```
a2query -m php8.1
```
If i sound harsh, I'm not trying for that, just facts, and I'm a poor teacher I just get things done. ;)
So please know I'm not a bad guy, just a poor teacher. :)

---

### Post by gale85 on 2022-05-26
I have already written the output for that command but it is not a problem here again
a2query -m php8.1
> No module matches php8.1
I don't blame her for anything, but I thank you very much for this much effort to solve my problem with php

---

### Post by #&amp;thj^% on 2022-05-26
Yes I know you did, but problem is there.
you show nothing for that command, mine shows:
```
cat /etc/apache2/mods-enabled/php8.1.load
# Conflicts: php5
# Depends: mpm_prefork
LoadModule php_module /usr/lib/apache2/modules/libphp8.1.so
```
See the difference?
also your last "No module matches php8.1 "is related, so yes there is a problem there.
lets see what this is owned by:
```
ls -l /usr/lib/apache2/modules/libphp*

```
mine will show:
```
-rw-r--r-- 1 root root 5354272 Apr  7 13:46 /usr/lib/apache2/modules/libphp8.1.so

```
Let's run a install/reinstall of a few packages, even if you think they are already installed.
```
sudo apt-get install --reinstall apache2 php libapache2-mod-php

```
post any errors back you can see.

---

### Post by gale85 on 2022-05-26
cat /etc/apache2/mods-enabled/php8.1.load
> cat: /etc/apache2/mods-enabled/php8.1.load: No such file or directory

---

### Post by gale85 on 2022-05-26
ls -l /usr/lib/apache2/modules/libphp*
> 
-rw-r--r-- 1 root root 5354272 &#1084;&#1072;&#1112; 17 18:46 /usr/lib/apache2/modules/libphp8.1.so

sudo apt-get install --reinstall apache2 php libapache2-mod-php
> Reading package lists... DoneBuilding dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 3 reinstalled, 0 to remove and 11 not upgraded.
Need to get 112 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 [http://rs.archive.ubuntu.com/ubuntu](http://rs.archive.ubuntu.com/ubuntu) jammy/main amd64 apache2 amd64 2.4.52-1ubuntu4 [97,8 kB]
Get:2 [https://ppa.launchpadcontent.net/ondrej/php/ubuntu](https://ppa.launchpadcontent.net/ondrej/php/ubuntu) jammy/main amd64 libapache2-mod-php all 2:8.1+92+ubuntu22.04.1+deb.sury.org+1 [7376 B]
Get:3 [https://ppa.launchpadcontent.net/ondrej/php/ubuntu](https://ppa.launchpadcontent.net/ondrej/php/ubuntu) jammy/main amd64 php all 2:8.1+92+ubuntu22.04.1+deb.sury.org+1 [7158 B]
Fetched 112 kB in 1s (192 kB/s)
(Reading database ... 280813 files and directories currently installed.)
Preparing to unpack .../apache2_2.4.52-1ubuntu4_amd64.deb ...
Unpacking apache2 (2.4.52-1ubuntu4) over (2.4.52-1ubuntu4) ...
Preparing to unpack .../libapache2-mod-php_2%3a8.1+92+ubuntu22.04.1+deb.sury.org+1_all.deb ...
Unpacking libapache2-mod-php (2:8.1+92+ubuntu22.04.1+deb.sury.org+1) over (2:8.1+92+ubuntu22.04.1+deb.sury.org+1) ...
Preparing to unpack .../php_2%3a8.1+92+ubuntu22.04.1+deb.sury.org+1_all.deb ...
Unpacking php (2:8.1+92+ubuntu22.04.1+deb.sury.org+1) over (2:8.1+92+ubuntu22.04.1+deb.sury.org+1) ...
Setting up php (2:8.1+92+ubuntu22.04.1+deb.sury.org+1) ...
Setting up apache2 (2.4.52-1ubuntu4) ...
apache-htcacheclean.service is a disabled or a static unit not running, not starting it.
Setting up libapache2-mod-php (2:8.1+92+ubuntu22.04.1+deb.sury.org+1) ...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for ufw (0.36.1-4build1) ...

---

### Post by deadflowr on 2022-05-26
I'd probably start by looking at what mods are listed there first.
```
 ls /etc/apache2/mods-enabled
```
Then go from there.

(Adjust for any speeling error I might have maid.)

---

### Post by #&amp;thj^% on 2022-05-26
> **deadflowr said:**
> 
(Adjust for any speeling error I might have maid.)
:lolflag: that is good advice>>" ls /etc/apache2/mods-enabled"
Oh deadflowr you crack me up. ;)

---

### Post by gale85 on 2022-05-26
ls /etc/apache2/mods-enabled
> 
mpm_prefork.conf  reqtimeout.load
alias.conf          authz_user.load  env.load     mpm_prefork.load  setenvif.conf
alias.load          autoindex.conf   fcgid.conf   negotiation.conf  setenvif.load
auth_basic.load     autoindex.load   fcgid.load   negotiation.load  status.conf
authn_core.load     deflate.conf     filter.load  php8.0.conf       status.load
authn_file.load     deflate.load     mime.conf    php8.0.load
authz_core.load     dir.conf         mime.load    reqtimeout.conf


---

### Post by #&amp;thj^% on 2022-05-26
> **gale85 said:**
> ls /etc/apache2/mods-enabled

Goodness, i was not expecting that..?
```
access_compat.load  authz_user.load  filter.load       php8.1.load
alias.conf          autoindex.conf   mime.conf         reqtimeout.conf
alias.load          autoindex.load   mime.load         reqtimeout.load
auth_basic.load     deflate.conf     mpm_prefork.conf  setenvif.conf
authn_core.load     deflate.load     mpm_prefork.load  setenvif.load
authn_file.load     dir.conf         negotiation.conf  status.conf
authz_core.load     dir.load         negotiation.load  status.load
authz_host.load     env.load         **_php8.1.conf_**

```
was what I was hoping for.

---

### Post by #&amp;thj^% on 2022-05-26
What happens if we set it manually with:
```
update-alternatives --set php /usr/bin/php8.1
```
if all goes well reload the services:
```
sudo systemctl restart apache2
```

---

### Post by gale85 on 2022-05-26
update-alternatives --set php /usr/bin/php8.1
> 
update-alternatives: error: unable to create file '/var/lib/dpkg/alternatives/php.dpkg-tmp': Permission denied

Since I couldn't activate the command, I just added sudo, then it worked
sudo update-alternatives --set php /usr/bin/php8.1
I also restarted apache and tried but php still doesn't work

---

### Post by #&amp;thj^% on 2022-05-26
> **gale85 said:**
> 
I also restarted apache and tried but php still doesn't work
That dose not help...show me why>>what was the return??
"doesn't work" should be banned, instead information or reasons why, is all I'm after. :)

---

### Post by gale85 on 2022-05-26
There is no error instead I only get the php code instead of getting the result of that code for example if I entered the echo "test" in the file; I'll get that as a display instead of just displaying a test

---

### Post by #&amp;thj^% on 2022-05-26
> **gale85 said:**
> There is no error instead I only get the php code instead of getting the result of that code for example if I entered the echo "test" in the file; I'll get that as a display instead of just displaying a test

can you post that script here?
not the echo "test" but the script you used.
also show what your .conf file looks like:
```
<FilesMatch ".+\.ph(ar|p|tml)$">
    SetHandler application/x-httpd-php
</FilesMatch>
<FilesMatch ".+\.phps$">
    SetHandler application/x-httpd-php-source
    # Deny access to raw php sources by default
    # To re-enable it's recommended to enable access to the files
    # only in specific virtual host or directory
    Require all denied
</FilesMatch>
# Deny access to files without filename (e.g. '.php')
<FilesMatch "^\.ph(ar|p|ps|tml)$">
    Require all denied
</FilesMatch>

# Running PHP scripts in user directories is disabled by default
# 
# To re-enable PHP in user directories comment the following lines
# (from <IfModule ...> to </IfModule>.) Do NOT set it to On as it
# prevents .htaccess files from disabling it.
<IfModule mod_userdir.c>
    <Directory /home/*/public_html>
        php_admin_flag engine Off
    </Directory>
</IfModule>
```
use this to see:
```
cat /etc/apache2/mods-enabled/php8.1.conf 

```

---

### Post by gale85 on 2022-05-26
I made this script where I use only echo to test if php works, otherwise nothing will start that has to do with php, wordpress, phpmyadmin, whatever I run, I only get php code as if I started a php editor.

---

### Post by deadflowr on 2022-05-26
Oddly your php version shown in mods-enabled is 8.0 and not 8.1.

Also, is this the same system as mentioned in here: [https://ubuntuforums.org/showthread.php?t=2475173&p=14097335]("https://ubuntuforums.org/showthread.php?t=2475173&p=14097335")

---

### Post by gale85 on 2022-05-26
Yes it is

---

### Post by gale85 on 2022-05-26
I somehow managed to find the file php8.1.conf but at / etc / apache2 / mods-available
not as I was told etc / apache2 / mods-enabled / At the location where I was suggested I found the file php8.0.conf which I can't even open as root as if something is wrong with the file. Here is the contents of the php8.1.conf file located at / etc / apache2 / mods-available
> 
<FilesMatch ".+\.ph(ar|p|tml)$">
    SetHandler application/x-httpd-php
</FilesMatch>
<FilesMatch ".+\.phps$">
    SetHandler application/x-httpd-php-source
    # Deny access to raw php sources by default
    # To re-enable it's recommended to enable access to the files
    # only in specific virtual host or directory
    Require all denied
</FilesMatch>
# Deny access to files without filename (e.g. '.php')
<FilesMatch "^\.ph(ar|p|ps|tml)$">
    Require all denied
</FilesMatch>


# Running PHP scripts in user directories is disabled by default
# 
# To re-enable PHP in user directories comment the following lines
# (from <IfModule ...> to </IfModule>.) Do NOT set it to On as it
# prevents .htaccess files from disabling it.
<IfModule mod_userdir.c>
    <Directory /home/*/public_html>
        php_admin_flag engine Off
    </Directory>
</IfModule>


---

### Post by #&amp;thj^% on 2022-05-26
If you are running it inside your usr directory you'll have fix this:
**# Running PHP scripts in user directories is disabled by default**
change it to something like:
```
# Running PHP scripts in user directories is disabled by default   
#                                                                  
# To re-enable PHP in user directories comment the following lines 
# (from <IfModule ...> to </IfModule>.) Do NOT set it to On as it  
# prevents .htaccess files from disabling it.                      
<IfModule mod_userdir.c>                                           
    <Directory /home/*/public_html>                                
       ** php_admin_flag engine On    **                              
    </Directory>                                                   
</IfModule>                                    
```
I wish you would use Code Tags instead of Quote tags
and change permissions:
```
sudo -Hu SOMEUSER sh -c 'chmod 755 $HOME $HOME/public_html'

```
Then find the line containing php_admin_flag and change it to:

```
php_admin_flag engine On

```
This is due to PHP being disabled by default for user dirs for Apache 2.
EDIT So i just did some reading if that still fails try this setting:
```
#<IfModule mod_userdir.c>
#    <Directory /home/*/public_html>
#        php_admin_flag engine Off
#    </Directory>
#</IfModule>


```

---

### Post by gale85 on 2022-05-26
It is not clear to me what to do, to copy the file php8.1.conf to the location $ HOME / public_html but it is not my location where the sites I make are located on the location even on $ HOME there is no folder public_html. My site location is standard / var / www / html /

---

### Post by #&amp;thj^% on 2022-05-26
> **gale85 said:**
> It is not clear to me what to do, to copy the file php8.1.conf to the location $ HOME / public_html but it is not my location where the sites I make are located on the location even on $ HOME there is no folder public_html. My site location is standard / var / www / html /

No just edit the file "/etc/apache2/mods-enabled/php*.conf" try the first suggestion in my above post.
Hint: "php_admin_flag engine On"
EDIT: I'm going into the office for a few hours, will be back when I'm done.

---

### Post by #&amp;thj^% on 2022-05-28
Did I lose you?

---

### Post by gale85 on 2022-05-28
I'm not sorry, but I didn't get to answer. I tried to copy the contents of the php8.1.conf file located at etc / apache2 / mods-available and transferred its contents to the same file located at the location you requested etc / apache2 / mods-enabled / . I restarted the apache server and again it failed to run the php script. Maybe it's better to delete everything and reinstall what I need?

---

### Post by #&amp;thj^% on 2022-05-28
> **gale85 said:**
>  Maybe it's better to delete everything and reinstall what I need?

Sometimes that's the best, I'm not able to be behind your keyboard, so I just have to stab at what I think/feel the problems your experiencing.
Keep us posted, I'm hopeful to to see a Solved solution for you. :)

---

### Post by gale85 on 2022-05-28
I want to, of course, and thank you so much for all this effort

---

### Post by #&amp;thj^% on 2022-05-28
This may help as well: [https://www.digitalocean.com/community/tutorials/how-to-install-the-apache-web-server-on-ubuntu-22-04](https://www.digitalocean.com/community/tutorials/how-to-install-the-apache-web-server-on-ubuntu-22-04)

---

### Post by gale85 on 2022-05-29
Ok thanks a lot I will look at it in detail. Just to check just in case if I wanted to first delete all the packages I need for the apache server and the rest I would have to delete the packages apache, php, mysql, phpmyadmin with the command```
 sudo apt purge * package_name * 
```I deleted some packages, right that's enough or you need some more command to knock to completely clean the system of these packages

---

### Post by #&amp;thj^% on 2022-05-29
Start fresh by removing what you thought I wanted you to install:
```
sudo apt remove --autoremove php8.1-common php8.1-mysql php8.1-xml php8.1-xmlrpc php8.1-curl php8.1-gd php8.1-imagick php8.1-cli php8.1-dev php8.1-imap php8.1-mbstring php8.1-opcache php8.1-soap php8.1-zip php8.1-redis php8.1-intl
```
now set it up like you used to, before all this happened. The link will help you start fresh.

---

### Post by gale85 on 2022-05-29
Ok thanks a lot, I'll let you know when I do that and when I reinstall if everything works properly

---

### Post by gale85 on 2022-06-01
I deleted those packages and reinstalled them but php still doesn't work even though it says it's installed

---

### Post by mIk3_08 on 2022-06-02
> **gale85 said:**
> I don't know why but php will not work in the mentioned version of Ubuntu, although I checked if php and apache server are installed and activated. I have no idea where the problem might be. I don't know what you did this and that, all I know is that php will run only with servers. I haven't tested running php server in Linux Desktop machine but I'm pretty sure if you install everything what you need to run a php codes in your Linux server machine I think it wont be that complicated. Regards and cheers.

---

### Post by SeijiSensei on 2022-06-02
I routinely install apache2 and php on desktop machines. Usually it takes little more than "sudo apt install apache2 php".

Haven't tried on a 22.04 machine yet. On this desktop, running 20.04, after running that command I can type "localhost" in Firefox and get the default Apache page.  If I make a file called index.php in /var/www/html (requires sudo) that has just the line
```
<?php phpinfo() ?>
```
Visiting that page at "localhost/index.php" gives me the full phpinfo() report.

---

### Post by #&amp;thj^% on 2022-06-02
> **SeijiSensei said:**
> I routinely install apache2 and php on desktop machines. Usually it takes little more than "sudo apt install apache2 php".


+1


To install PHP with success you have to install some dependencies first.
```
sudo apt install software-properties-common apt-transport-https
```
This may be the difference between your troubles, and why mine works.
This step is to import a PPA repository from **Ond&#345;ej Surý who is a renowned PHP and Debian developer and maintains its packages _as well as Ubuntu’s packages_**.
```

sudo add-apt-repository ppa:ondrej/php -y
```
run your update command only...
Now see if this helps:
```
sudo apt install php8.1 libapache2-mod-php8.1
```
now reload:
```
sudo systemctl restart apache2
```
check if it is working:
```
sudo systemctl status apache2
```
```
systemctl status apache2
\u25cf apache2.service - The Apache HTTP Server
     Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor prese>
     Active: active (running) since Thu 2022-06-02 13:13:11 EDT; 8s ago
       Docs: https://httpd.apache.org/docs/2.4/
    Process: 14432 ExecStart=/usr/sbin/apachectl start (code=exited, status=0/S>
   Main PID: 14436 (apache2)
      Tasks: 6 (limit: 4622)
     Memory: 9.9M
        CPU: 52ms
     CGroup: /system.slice/apache2.service
             \u251c\u250014436 /usr/sbin/apache2 -k start
             \u251c\u250014437 /usr/sbin/apache2 -k start
             \u251c\u250014438 /usr/sbin/apache2 -k start
             \u251c\u250014439 /usr/sbin/apache2 -k start
             \u251c\u250014440 /usr/sbin/apache2 -k start
             \u2514\u250014441 /usr/sbin/apache2 -k start

```
I'm stopping here due to I set mine up different from what I've seen you do>.
Fingers Crossed

---

### Post by gale85 on 2022-06-02
People thank you very much. I managed to run php somehow and with the help of this advice written by @1fallen it now works well. Now only if I could fix phpymadmin I just don't know if I should open a new topic or can I here?

---

### Post by #&amp;thj^% on 2022-06-02
No just stay within this thread current.
Give me some time to test "phpymadmin" on a test bed.
**I'll add my findings to this post, so watch for "EDITS"**
EDIT: Start here: [https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-phpmyadmin-on-ubuntu-22-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-phpmyadmin-on-ubuntu-22-04)

---

### Post by #&amp;thj^% on 2022-06-02
Starting here now :P it was easy enough.

I started here:(You might not need to if installed)
```

sudo apt install phpmyadmin
```

Once phpMyAdmin is installed you can configure it with Apache so you can access the web interface:
```
sudo cp /etc/phpmyadmin/apache.conf /etc/apache2/conf-available/phpmyadmin.conf
```

Finally, restart the Apache webserver so that the changes take place:

```
sudo a2enconf phpmyadmin.conf
sudo systemctl restart apache2
```

Configure Firewall.
```
sudo ufw allow 'Apache Full'
sudo ufw enable
sudo ufw status
```

Now check with:
http://<your ip address here>/phpmyadmin

---

### Post by gale85 on 2022-06-02
Now phpmyadmin also works but the password and user name will not. I'll probably have to reconfigure for phpmyadmin

---

### Post by #&amp;thj^% on 2022-06-02
Hurray!

> **gale85 said:**
> I'll probably have to reconfigure for phpmyadmin
yep
EDIT: also try https://<your ip address here>/phpmyadmin  notice>> the change between  **http** with  **https**

---

### Post by mIk3_08 on 2022-06-03
> **1fallen said:**
> +1


To install PHP with success you have to install some dependencies first.
```
sudo apt install software-properties-common apt-transport-https
```
This may be the difference between your troubles, and why mine works.
This step is to import a PPA repository from **Ond&#345;ej Surý who is a renowned PHP and Debian developer and maintains its packages _as well as Ubuntu’s packages_**.
```

sudo add-apt-repository ppa:ondrej/php -y
```
run your update command only...
Now see if this helps:
```
sudo apt install php8.1 libapache2-mod-php8.1
```
now reload:
```
sudo systemctl restart apache2
```
check if it is working:
```
sudo systemctl status apache2
```
```
systemctl status apache2
\u25cf apache2.service - The Apache HTTP Server
     Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor prese>
     Active: active (running) since Thu 2022-06-02 13:13:11 EDT; 8s ago
       Docs: https://httpd.apache.org/docs/2.4/
    Process: 14432 ExecStart=/usr/sbin/apachectl start (code=exited, status=0/S>
   Main PID: 14436 (apache2)
      Tasks: 6 (limit: 4622)
     Memory: 9.9M
        CPU: 52ms
     CGroup: /system.slice/apache2.service
             \u251c\u250014436 /usr/sbin/apache2 -k start
             \u251c\u250014437 /usr/sbin/apache2 -k start
             \u251c\u250014438 /usr/sbin/apache2 -k start
             \u251c\u250014439 /usr/sbin/apache2 -k start
             \u251c\u250014440 /usr/sbin/apache2 -k start
             \u2514\u250014441 /usr/sbin/apache2 -k start

```
I'm stopping here due to I set mine up different from what I've seen you do>.
Fingers Crossed
Wow... I haven't tried it yet. But this is good.... Thanks a lot 1fallen. Do you have nginx running setup for this? :-D I think it is best for this thread post to be mark as solve as it will help to the new user same issue like this. Regards and cheers.

---

### Post by #&amp;thj^% on 2022-06-03
> **mIk3_08 said:**
> Do you have nginx running setup for this?.

No I use a far different setup
I'll add this, as it is as important to healthy mysql setup.
From the link I provided.

Additionally, _there are important security considerations_ when using software like phpMyAdmin, since it:
[list]
    [*]Communicates directly with your MySQL installation
    [*]Handles authentication using MySQL credentials
    [*]Executes and returns results for arbitrary SQL queries[/list]

For these reasons, and because it is a widely-deployed PHP application _which is frequently targeted for attack,_ you should never run phpMyAdmin on remote systems over a plain HTTP connection.

[https://www.digitalocean.com/community/tutorials/how-to-secure-apache-with-let-s-encrypt-on-ubuntu-22-04](https://www.digitalocean.com/community/tutorials/how-to-secure-apache-with-let-s-encrypt-on-ubuntu-22-04)
Everything is in a VirtualHost configuration block.

---

### Post by gale85 on 2022-06-03
People, thank you very much, I managed to create a user for phpmyadmin, it just throws out two errors when I log in. Can I post it here or open a new topic?

---

### Post by mIk3_08 on 2022-06-04
> **1fallen said:**
> No I use a far different setup
I'll add this, as it is as important to healthy mysql setup.
From the link I provided.

Additionally, _there are important security considerations_ when using software like phpMyAdmin, since it:
[LIST]
[*]Communicates directly with your MySQL installation
[*]Handles authentication using MySQL credentials
[*]Executes and returns results for arbitrary SQL queries
[/LIST]

For these reasons, and because it is a widely-deployed PHP application _which is frequently targeted for attack,_ you should never run phpMyAdmin on remote systems over a plain HTTP connection.

[https://www.digitalocean.com/community/tutorials/how-to-secure-apache-with-let-s-encrypt-on-ubuntu-22-04](https://www.digitalocean.com/community/tutorials/how-to-secure-apache-with-let-s-encrypt-on-ubuntu-22-04)
Everything is in a VirtualHost configuration block.
Yeah, Thanks. I just saw the Nginx in ondrej ppa. I might try this maybe sometime. Regards and cheers.

---

### Post by #&amp;thj^% on 2022-06-04
> **gale85 said:**
> People, thank you very much, I managed to create a user for phpmyadmin, it just throws out two errors when I log in. Can I post it here or open a new topic?

Sure, just make sure no address can be seen, that should remain out of view.
I hope you had good back-ups for your data base/s.

---

### Post by gale85 on 2022-06-04
Of course I saved everything, that's not a problem. When I log in to phpmyadmin I get these errors
```

mysqli :: real_connect (): (HY000 / 1045): Access denied for user 'user' @ 'localhost' (using password: YES)
  Connection for controller as defined in your configuration failed.

```
Of course I was trying this
```

ALTER USER 'user' @ 'localhost' IDENTIFIED BY 'mysql';
FLUSH PRIVILEGES;
GRANT ALL PRIVILEGES ON *. * TO 'user' @ 'localhost' WITH GRANT OPTION;

```
After that I restarted the apache server and mysql nothing again these errors appear

---

### Post by SeijiSensei on 2022-06-05
> 
```
ALTER USER 'user' @ 'localhost' IDENTIFIED BY 'mysql';
FLUSH PRIVILEGES;
GRANT ALL PRIVILEGES ON *. * TO 'user' @ 'localhost' WITH GRANT OPTION;

```

If there was really a space in *.* as the quoted material indicates, that's a problem.

I also think there aren't supposed to be spaces in 'user'@'localhost'.

---

### Post by #&amp;thj^% on 2022-06-05
I would also have to peek at this:
```
sudo mysql
```
then copy this exactly:
```
SELECT user,authentication_string,plugin,host FROM mysql.user;
```
I think you still have Root as the user here, not good.
Please use Code Tags for this>> it is important

---

### Post by gale85 on 2022-06-05
No spaces were used, that's because I use google translate, so he made spaces for me when I inserted the code.
Here's the command exit
[COLOR=#000000][FONT=&amp]SELECT user,authentication_string,plugin,host FROM mysql.user;
[/FONT][/COLOR]```
+------------------+------------------------------------------------------------------------+-----------------------+-----------+
| user             | authentication_string                                                  | plugin                | host      |
+------------------+------------------------------------------------------------------------+-----------------------+-----------+
| debian-sys-maint | $A$005$=c4E?Tf&f%8pf'HsIVFZSi5PKep3cd0o1.Cg6rq4HTplxY6v/SJ/Wrw5fYP8 | caching_sha2_password | localhost |
| user2             | $A$005$ "]J0u&UGw
,@Ga=8DehPdSIR8hTmZB7R0LSe1s.2VrddsTsZ5ZMcjSBtlB | caching_sha2_password | localhost |
| user1           | *35F144C978CA422A98B8A8594A3CC2413B25BED5                              | mysql_native_password | localhost |
| mysql.infoschema | $A$005$THISISACOMBINATIONOFINVALIDSALTANDPASSWORDTHATMUSTNEVERBRBEUSED | caching_sha2_password | localhost |
| mysql.session    | $A$005$THISISACOMBINATIONOFINVALIDSALTANDPASSWORDTHATMUSTNEVERBRBEUSED | caching_sha2_password | localhost |
| mysql.sys        | $A$005$THISISACOMBINATIONOFINVALIDSALTANDPASSWORDTHATMUSTNEVERBRBEUSED | caching_sha2_password | localhost |
| root             |                                                                        | auth_socket           | localhost |
+------------------+------------------------------------------------------------------------+-----------------------+-----------+

```[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]

---

### Post by gale85 on 2022-06-05
Just to mention that I use user1 and when I log in I get rid of those errors

---

### Post by #&amp;thj^% on 2022-06-05
gale85 somehow this was set right, can you try to add "your" user again.
```
CREATE USER 'yourusr'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password_here';
```
then give the correct privileges with:
```
GRANT ALL PRIVILEGES ON *.* TO 'yourusr'@'localhost' WITH GRANT OPTION;
```
You should now be able to access phpMyAdmin using this user account.
Ok this is new:
> **gale85 said:**
> Just to mention that I use user1 and when I log in I get rid of those errors
Also check in User Accounts and make sure all is good there as well. See Screenshot

---

### Post by gale85 on 2022-06-05
I tried to do that but I didn't succeed with the user I'm using, I made a new one and typed everything as it is written, but I get the same mistakes again. I also checked for the user I use to log in, it says ALL PRIVILEGES

---

### Post by #&amp;thj^% on 2022-06-05
> **gale85 said:**
> I tried to do that but I didn't succeed with the user I'm using, I made a new one and typed everything as it is written, but I get the same mistakes again. I also checked for the user I use to log in, it says ALL PRIVILEGES
Do you recall ever setting a root password?
Also verify:
```
mysql -V
mysql  Ver 8.0.29-0ubuntu0.22.04.2 for Linux on x86_64 ((Ubuntu))

```
I remember you saying you installed some more stuff, but I wouldn't know what you installed, outside of my current suggestions.

---

### Post by gale85 on 2022-06-05
I remember not setting a password for the root user but if necessary I can set one
mysql -V
```

mysql  Ver 8.0.29-0ubuntu0.22.04.2 for Linux on x86_64 ((Ubuntu))

```

---

### Post by #&amp;thj^% on 2022-06-06
> **gale85 said:**
> I remember not setting a password for the root user but if necessary I can set one

gale85, I'm not sure how to advise you now, I can create those errors, following the last link I provided, and solve them.

Lets run down a small list first, please show this:
```

sudo ufw app list
[sudo] password for me: 
Available applications:
  Apache
  Apache Full
  Apache Secure
  OpenSSH
```
It should look exactly like the above.
For now, it&#8217;s best to allow only connections on port 80, since this is a fresh Apache installation and you don&#8217;t yet have a TLS/SSL certificate configured to allow for HTTPS traffic on your server.
```
sudo ufw allow in "Apache"
Rules updated
Rules updated (v6)

```
Verify the change with:

```
sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
OpenSSH                    ALLOW       Anywhere                                
Apache                     ALLOW       Anywhere                  
OpenSSH (v6)               ALLOW       Anywhere (v6)                    
Apache (v6)                ALLOW       Anywhere (v6)
```
*If you show anything different than the above, show this:
```
cat /etc/ufw/ufw.conf | grep ENABLED
ENABLED=yes

```
If everything is now as it should be, try the secure mysql install again:
```
sudo mysql_secure_installation
```
This will ask if you want to configure the VALIDATE PASSWORD PLUGIN.

Note: Enabling this feature is something of a judgment call. **If enabled, passwords which don&#8217;t match the specified criteria will be rejected by MySQL with an error. It is safe to leave validation disabled,** but you should always use strong, unique passwords for database credentials.

Answer Y for yes, If you answer &#8220;yes&#8221;, you&#8217;ll be asked to select a level of password validation. Keep in mind that if you enter 2 for the strongest level, you will receive errors when attempting to set any password which does not contain numbers, upper and lowercase letters, and special characters:
Like:
```
There are three levels of password validation policy:

LOW    Length >= 8
MEDIUM Length >= 8, numeric, mixed case, and special characters
STRONG Length >= 8, numeric, mixed case, special characters and dictionary              file

Please enter 0 = LOW, 1 = MEDIUM and 2 = STRONG: 1
```
Regardless of whether you chose to set up the VALIDATE PASSWORD PLUGIN, your server will next ask you to select and confirm a password for the MySQL root user. This is not to be confused with the system root. The database root user is an administrative user with full privileges over the database system. Even though the default authentication method for the MySQL root user doesn&#8217;t involve using a password, even when one is set, you should define a strong password here as an additional safety measure.
Make sure these are installed:
```
apt policy php libapache2-mod-php php-mysql
php:
  Installed: 2:8.1+92+ubuntu22.04.1+deb.sury.org+1
  Candidate: 2:8.1+92+ubuntu22.04.1+deb.sury.org+1
  Version table:
 *** 2:8.1+92+ubuntu22.04.1+deb.sury.org+1 500
        500 https://ppa.launchpadcontent.net/ondrej/php/ubuntu jammy/main amd64 Packages
        500 https://ppa.launchpadcontent.net/ondrej/php/ubuntu jammy/main i386 Packages
        100 /var/lib/dpkg/status
     2:8.1+92ubuntu1 500
        500 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        500 http://ca.archive.ubuntu.com/ubuntu jammy/main i386 Packages
libapache2-mod-php:
  Installed: 2:8.1+92+ubuntu22.04.1+deb.sury.org+1
  Candidate: 2:8.1+92+ubuntu22.04.1+deb.sury.org+1
  Version table:
 *** 2:8.1+92+ubuntu22.04.1+deb.sury.org+1 500
        500 https://ppa.launchpadcontent.net/ondrej/php/ubuntu jammy/main amd64 Packages
        500 https://ppa.launchpadcontent.net/ondrej/php/ubuntu jammy/main i386 Packages
        100 /var/lib/dpkg/status
     2:8.1+92ubuntu1 500
        500 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        500 http://ca.archive.ubuntu.com/ubuntu jammy/main i386 Packages
php-mysql:
  Installed: 2:8.1+92+ubuntu22.04.1+deb.sury.org+1
  Candidate: 2:8.1+92+ubuntu22.04.1+deb.sury.org+1
  Version table:
 *** 2:8.1+92+ubuntu22.04.1+deb.sury.org+1 500
        500 https://ppa.launchpadcontent.net/ondrej/php/ubuntu jammy/main amd64 Packages
        500 https://ppa.launchpadcontent.net/ondrej/php/ubuntu jammy/main i386 Packages
        100 /var/lib/dpkg/status
     2:8.1+92ubuntu1 500
        500 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        500 http://ca.archive.ubuntu.com/ubuntu jammy/main i386 Packages

```
Now if you still see those warnings, follow this: [https://ourcodeworld.com/articles/read/1585/how-to-remove-phpmyadmin-error-mysqli-real-connect-hy000-1045-access-denied-for-user-pmalocalhost-using-password-yes](https://ourcodeworld.com/articles/read/1585/how-to-remove-phpmyadmin-error-mysqli-real-connect-hy000-1045-access-denied-for-user-pmalocalhost-using-password-yes)

---

### Post by gale85 on 2022-06-06
sudo ufw app list
```

Available applications:
  Apache
  Apache Full
  Apache Secure
  CUPS
  OpenSSH

```
apt policy php libapache2-mod-php php-mysql
```

php:
  Installed: (none)
  Candidate: 2:8.1+92+ubuntu22.04.1+deb.sury.org+1
  Version table:
     2:8.1+92+ubuntu22.04.1+deb.sury.org+1 500
        500 https://ppa.launchpadcontent.net/ondrej/php/ubuntu jammy/main amd64 Packages
        500 https://ppa.launchpadcontent.net/ondrej/php/ubuntu jammy/main i386 Packages
     2:8.1+92ubuntu1 500
        500 http://rs.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        500 http://rs.archive.ubuntu.com/ubuntu jammy/main i386 Packages
libapache2-mod-php:
  Installed: (none)
  Candidate: 2:8.1+92+ubuntu22.04.1+deb.sury.org+1
  Version table:
     2:8.1+92+ubuntu22.04.1+deb.sury.org+1 500
        500 https://ppa.launchpadcontent.net/ondrej/php/ubuntu jammy/main amd64 Packages
        500 https://ppa.launchpadcontent.net/ondrej/php/ubuntu jammy/main i386 Packages
     2:8.1+92ubuntu1 500
        500 http://rs.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        500 http://rs.archive.ubuntu.com/ubuntu jammy/main i386 Packages
php-mysql:
  Installed: 2:8.1+92+ubuntu22.04.1+deb.sury.org+1
  Candidate: 2:8.1+92+ubuntu22.04.1+deb.sury.org+1
  Version table:
 *** 2:8.1+92+ubuntu22.04.1+deb.sury.org+1 500
        500 https://ppa.launchpadcontent.net/ondrej/php/ubuntu jammy/main amd64 Packages
        500 https://ppa.launchpadcontent.net/ondrej/php/ubuntu jammy/main i386 Packages
        100 /var/lib/dpkg/status
     2:8.1+92ubuntu1 500
        500 http://rs.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        500 http://rs.archive.ubuntu.com/ubuntu jammy/main i386 Packages

```
I did not manage to set the password, I tried lowercase and uppercase letters, signs, characters, I tried various combinations but I did not succeed. The rest of what I didn't show is all the same as in your example 1fallen

[COLOR=#000000][/COLOR]

---

### Post by #&amp;thj^% on 2022-06-07
Ok I think this where your problem is, 
> I did not manage to set the password, 
Passwords are a bit finicky for MYSL: [https://dev.mysql.com/doc/refman/5.6/en/set-password.html](https://dev.mysql.com/doc/refman/5.6/en/set-password.html)
There are 3 layers for setting a good password: [https://dev.mysql.com/doc/refman/8.0/en/validate-password.html](https://dev.mysql.com/doc/refman/8.0/en/validate-password.html)
I'll always use along the lines of something like: "MyPassword123#@!"
EDIT: I think you may find better luck using the console in "phpMyAdmin"
Let me know.

---

### Post by gale85 on 2022-06-07
I tried to set the password exactly as instructed but I didn't set it. Can I somehow turn off the password for the root user, whatever makes this all work

---

### Post by #&amp;thj^% on 2022-06-08
> **gale85 said:**
> I tried to set the password exactly as instructed but I didn't set it. Can I somehow turn off the password for the root user, whatever makes this all work

This may help then, edit this file using vim or nano:

```
sudo nano /etc/init.d/mysql *
```
For debian/ubuntu add these 3 lines:
```
 echo "Usage: $SELF start|stop|restart|reload|force-reload|status"
        exit 1
        ;;
esac
[B][COLOR="#FF0000"]/* Authentication type */
$cfg['Servers'][$i]['auth_type'] = 'cookie';
$cfg['Servers'][$i]['AllowRoot'] = false;[/COLOR][/B]
# Some success paths end up returning non-zero so exit 0 explicitly. See
# bug #739846.
exit 0

```
I show where I placed mine for this example.
Save changes and restart Apache:
```
sudo systemctl restart apache2.service
```
any better now? 
For clairity these are the lines to add:
```

/* Authentication type */
$cfg['Servers'][$i]['auth_type'] = 'cookie';
$cfg['Servers'][$i]['AllowRoot'] = false;
```
EDIT: If it dose not work, you really need to show me the commands used, and the error shown. with out that we are just chasing our tails.

---

### Post by gale85 on 2022-06-08
I succeeded but not when I added the code you wrote me 1fallen but when I removed the comment // in the config.inc.php file on the line $cfg['Servers'][$i]['AllowNoPassword'] = TRUE; and then I reset mysql and apache and everything worked

---

### Post by #&amp;thj^% on 2022-06-08
YAAAY! Good News.
yep when the added lines in place allow you more privileges, but you figured it out in your  "config.inc.php file" which I wasn't sure you had one yet.
anyway success is always sweet. :)

---

### Post by gale85 on 2022-06-08
I forgot to mention I also did this command in mysql
UNINSTALL COMPONENT 'file://component_validate_password';

Everything I changed in the file
/etc/init.d/mysql
I restored to the old

---

### Post by #&amp;thj^% on 2022-06-08
> **gale85 said:**
> I forgot to mention I also did this command in mysql
UNINSTALL COMPONENT 'file://component_validate_password';
Yep that will do "UNINSTALL COMPONENT" unloads the component, and unregisters it from the mysql.component system table to cause it not to be loaded during subsequent server startups.
BTW: Here is what my user permissions look like now:
```
 User accounts overview
	User name 	Host name 	Password 	Global privileges 	Grant 	Action
	debian-sys-maint 	localhost 	Yes 	     ALL PRIVILEGES 	Yes 	        Edit privileges Edit privileges 	Export Export
	me 	                        localhost 	Yes 	ALL PRIVILEGES 	        No 	Edit privileges Edit privileges 	Export Export
	me2 	                localhost 	Yes 	ALL PRIVILEGES 	       Yes 	Edit privileges Edit privileges 	Export Export
	mysql.infoschema 	localhost 	Yes 	SELECT 	                       No 	Edit privileges Edit privileges 	Export Export
	mysql.session 	localhost 	Yes 	SHUTDOWN, SUPER    No 	Edit privileges Edit privileges 	Export Export
	mysql.sys 	        localhost 	Yes 	USAGE 	                       No 	Edit privileges Edit privileges 	Export Export
	pma 	                localhost 	Yes 	USAGE 	                       No 	Edit privileges Edit privileges 	Export Export
	root 	                localhost 	No 	USAGE 	                      No 	Edit privileges Edit privileges 	Export Export 
```

---

### Post by gale85 on 2022-06-08
Can I restore everything as it was now, it means that in the part $cfg['Servers'][$i]['AllowNoPassword'] = TRUE;

I return the comment and in mysql to type the command INSTALL COMPONENT 'file://component_validate_password';

---

### Post by #&amp;thj^% on 2022-06-08
> **gale85 said:**
> Can I restore everything as it was now, it means that in the part $cfg['Servers'][$i]['AllowNoPassword'] = TRUE;



I could, but I never seen the problems you encountered. Try it I guess.
> **gale85 said:**
> 
I return the comment and in mysql to type the command INSTALL COMPONENT 'file://component_validate_password';
Again I just don't know, try first without adding it back.

---

### Post by gale85 on 2022-06-08
All right, I'll try, so I'll let you know if everything is still working properly

---

### Post by #&amp;thj^% on 2022-06-08
Please Do.
```
mysql> SELECT User, Host FROM mysql.user;
+------------------+-----------+
| User             | Host      |
+------------------+-----------+
| debian-sys-maint | localhost |
| me               | localhost |
| me2              | localhost |
| mysql.infoschema | localhost |
| mysql.session    | localhost |
| mysql.sys        | localhost |
+------------------+-----------+
6 rows in set (0.00 sec)

```
EDIT: I'm going to be in meeting for about an hour give or take, I'll check back when done.

---

### Post by gale85 on 2022-06-08
SELECT User, Host FROM mysql.user;
```

+------------------+-----------+
| User             | Host      |
+------------------+-----------+
| User           | localhost |
| debian-sys-maint | localhost |
| user             | localhost |
| myuser           | localhost |
| mysql.infoschema | localhost |
| mysql.session    | localhost |
| mysql.sys        | localhost |
| root             | localhost |
+------------------+-----------+

```
I use myuser

---

### Post by #&amp;thj^% on 2022-06-08
So all is good then?

---

### Post by gale85 on 2022-06-09
Yes, but now, when I return it, I type the command in mysql and include the comment // in config.inc.php // [COLOR=#000000]$cfg['Servers'][$i]['AllowNoPassword'] = TRUE; [/COLOR]on the line, I immediately get those errors. I used to run into problems like this and then I found on youtube that it is first deleted in mysql, then the password component is reinstalled and then everything works ok. I don't know why it won't be fixed like that now, but in principle it's not so important if it can be fixed somehow and if not it's not a problem at all

---

### Post by #&amp;thj^% on 2022-06-09
As you can see in post #75
I deleted the root user and database from phpadmin not terminal. (Then those errors go away)
not being on your computer, I would back it up first before deleting root. just to be safe.

---

### Post by gale85 on 2022-06-10
When I delete the root user then I can't log in to mysql via the console but I can via phpmyadmin. Then I had to do it again via phpmyadmin and via console I failed. Now in the console, I can only log in with the sudo mysql root -p command with the root user, and that only happened because I deleted the root user and returned it. No other user can log in via the console except root

---

### Post by #&amp;thj^% on 2022-06-10
> **gale85 said:**
> When I delete the root user then I can't log in to mysql via the console but I can via phpmyadmin. Then I had to do it again via phpmyadmin and via console I failed. Now in the console, I can only log in with the sudo mysql root -p command with the root user, and that only happened because I deleted the root user and returned it. No other user can log in via the console except root

gale85, that's just not right I have no **root** I login just fine...I need to see what commands you are using and the result of that command. Please.
```
mysql -h localhost -u me2 -p http://10.0.2.15/phpmyadmin/index.php?route=/&route=%2F
[1] 2448

```
and 
```
mysql> SELECT User, Host FROM mysql.user;
+------------------+-----------+
| User             | Host      |
+------------------+-----------+
| debian-sys-maint | localhost |
| me               | localhost |
| me2              | localhost |
| mysql.infoschema | localhost |
| mysql.session    | localhost |
| mysql.sys        | localhost |
+------------------+-----------+
6 rows in set (0.01 sec)

mysql> 


```

---

### Post by gale85 on 2022-06-10
mysql -h localhost -u myuser -p [http://10.0.2.15/phpmyadmin/index.php?route=/&route=%2F](http://10.0.2.15/phpmyadmin/index.php?route=/&route=%2F)
```

[2] 53002

```
SELECT User, Host FROM mysql.user;
```
+------------------+-----------+
| User             | Host      |
+------------------+-----------+
| User1           | localhost |
| debian-sys-maint | localhost |
| user             | localhost |
| myuser           | localhost |
| mysql.infoschema | localhost |
| mysql.session    | localhost |
| mysql.sys        | localhost |
| root             | localhost |
+------------------+-----------+

```

---

### Post by #&amp;thj^% on 2022-06-11
> **gale85 said:**
> No other user can log in via the console except root

That's the command I need to see, and why....user login and why it fails.
There is some important details that are being omitted here, without them I just can't help...](*,)

---

### Post by gale85 on 2022-06-12
sudo mysql myuser -p
```

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

```

---

### Post by #&amp;thj^% on 2022-06-12
> **gale85 said:**
> sudo mysql myuser -p
```

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

```
Now I can work with that!
This is one of the most common errors in MySQL. It typically means you are trying to connect using a user account that doesn’t have enough privileges to connect.

By default, after installation, MySQL only allows localhost connection and blocks any remote connection attempts until the user privileges get re-configure properly. 
```
GRANT ALL PRIVILEGES ON *.* TO 'user_name'@'%' IDENTIFIED BY "Password";
```
**Yep change 'user_name' to yours and "Password" to your user password.**
then check:
```
SHOW GRANTS FOR 'user'@'host';
```
and always flush privileges:
```
FLUSH PRIVILEGES;
```

If the issue arises with the root account only after upgrading MySQL, it’s likely the authentication plugin has changed to auth_socket by default. So what you can do it to change the authentication method from auth_socket to mysql_native_password:
```

ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
```

Then flush privileges:
```

FLUSH PRIVILEGES;
```
Restart "mysql"
Good Luck, hopefully we have this marathon of a thread solved now. :D

---

### Post by gale85 on 2022-06-12
GRANT ALL PRIVILEGES ON *.* TO 'myuser'@'localhost' IDENTIFIED BY 'Password';
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'IDENTIFIED BY 'Password'' at line 1
SHOW GRANTS FOR 'myuser'@'localhost';
```

+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Grants for myuser@localhost                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| GRANT SELECT, INSERT, UPDATE, DELETE, CREATE, DROP, RELOAD, SHUTDOWN, PROCESS, FILE, REFERENCES, INDEX, ALTER, SHOW DATABASES, SUPER, CREATE TEMPORARY TABLES, LOCK TABLES, EXECUTE, REPLICATION SLAVE, REPLICATION CLIENT, CREATE VIEW, SHOW VIEW, CREATE ROUTINE, ALTER ROUTINE, CREATE USER, EVENT, TRIGGER, CREATE TABLESPACE, CREATE ROLE, DROP ROLE ON *.* TO `myuser`@`localhost` WITH GRANT OPTION                                                                                                                                                                                                                                                                                                                                                 |
| GRANT APPLICATION_PASSWORD_ADMIN,AUDIT_ABORT_EXEMPT,AUDIT_ADMIN,AUTHENTICATION_POLICY_ADMIN,BACKUP_ADMIN,BINLOG_ADMIN,BINLOG_ENCRYPTION_ADMIN,CLONE_ADMIN,CONNECTION_ADMIN,ENCRYPTION_KEY_ADMIN,FLUSH_OPTIMIZER_COSTS,FLUSH_STATUS,FLUSH_TABLES,FLUSH_USER_RESOURCES,GROUP_REPLICATION_ADMIN,GROUP_REPLICATION_STREAM,INNODB_REDO_LOG_ARCHIVE,INNODB_REDO_LOG_ENABLE,PASSWORDLESS_USER_ADMIN,PERSIST_RO_VARIABLES_ADMIN,REPLICATION_APPLIER,REPLICATION_SLAVE_ADMIN,RESOURCE_GROUP_ADMIN,RESOURCE_GROUP_USER,ROLE_ADMIN,SENSITIVE_VARIABLES_OBSERVER,SERVICE_CONNECTION_ADMIN,SESSION_VARIABLES_ADMIN,SET_USER_ID,SHOW_ROUTINE,SYSTEM_USER,SYSTEM_VARIABLES_ADMIN,TABLE_ENCRYPTION_ADMIN,XA_RECOVER_ADMIN ON *.* TO `myuser`@`localhost` WITH GRANT OPTION |
+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
2 rows in set (0,04 sec)

```

---

### Post by #&amp;thj^% on 2022-06-12
Ok I forgot you brought back root, so we will add it to the mix:
```
CREATE USER 'root'@'%' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON *.* TO 'root'@'%';
```
add your password.

---

### Post by gale85 on 2022-06-12
I did that
> **1fallen said:**
> Ok I forgot you brought back root, so we will add it to the mix:
```
CREATE USER 'root'@'%' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON *.* TO 'root'@'%';
```
add your password.
, but the command 
[COLOR=#000000]GRANT ALL PRIVILEGES ON *.* TO 'myuser'@'localhost' IDENTIFIED BY 'Password';[/COLOR]
```
[COLOR=#000000]
[/COLOR]&#8203;[COLOR=#000000]ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'IDENTIFIED BY 'Password'' at line 1[/COLOR]

```
won't

---

### Post by #&amp;thj^% on 2022-06-12
Ok this is getting to me now, let's refresh a bit here.
start with: I'm using sudo here just to be sure:
```

sudo mysql -u root
```
run these **_one line at a time_**:
```
mysql> USE mysql;
mysql> UPDATE user SET plugin='mysql_native_password' WHERE User='root';
mysql> FLUSH PRIVILEGES;
mysql> exit;
```
and always after changes run:
```

sudo service mysql restart
```

---

### Post by gale85 on 2022-06-12
sudo mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

---

### Post by #&amp;thj^% on 2022-06-12
well now, how you liking your upgrade to a newer release, I've  never encountered anything like this before.
some where things have gone amuck in your system...
```
sudo dpkg-reconfigure mysql-server-8.0
```
now try again with your user login:
for mine only just to show you results:
```
sudo dpkg-reconfigure mysql-server-8.0
mysqld will log errors to /var/log/mysql/error.log
mysqld is running as pid 8886
```
```
me@me-Standard-PC-Q35-ICH9-2009:~$ mysql -u me2 -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 8
Server version: 8.0.29-0ubuntu0.22.04.2 (Ubuntu)

Copyright (c) 2000, 2022, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
```
```

mysql> status
--------------
mysql  Ver 8.0.29-0ubuntu0.22.04.2 for Linux on x86_64 ((Ubuntu))

Connection id:		8
Current database:	
Current user:		me2@localhost
SSL:			Not in use
Current pager:		stdout
Using outfile:		''
Using delimiter:	;
Server version:		8.0.29-0ubuntu0.22.04.2 (Ubuntu)
Protocol version:	10
Connection:		Localhost via UNIX socket
Server characterset:	utf8mb4
Db     characterset:	utf8mb4
Client characterset:	utf8mb4
Conn.  characterset:	utf8mb4
UNIX socket:		/var/run/mysqld/mysqld.sock
Binary data as:		Hexadecimal
Uptime:			57 sec

Threads: 2  Questions: 5  Slow queries: 0  Opens: 117  Flush tables: 3  Open tables: 36  Queries per second avg: 0.087
--------------

```
now I'll query my data:
```

mysql> SHOW TABLES;
ERROR 1046 (3D000): No database selected
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mydatta            |
| mysql              |
| performance_schema |
| phpmyadmin         |
| radius             |
| root               |
| root-data          |
| sys                |
+--------------------+
9 rows in set (0.00 sec)


```
You don't need to show me any this, just showing you what takes place here.

---

### Post by gale85 on 2022-06-12
mysql -u myuser -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'myuser'@'localhost' (using password: YES)

---

### Post by gale85 on 2022-06-15
Now I can only log in as a root user both in the terminal and via phpmyadmin. I will try to install wordpress and I will let you know what the outcome is
This is the message it throws out to me when I try to log in via phpmayadmin
```

mysqli::real_connect(): (HY000/1045): Access denied for user 'myuser@localhost'@'localhost' (using password: YES)

```
and I have already written about logging in via the terminal

---

### Post by #&amp;thj^% on 2022-06-16
> **gale85 said:**
> Now I can only log in as a root user both in the terminal and via phpmyadmin.
This is an incredibly insecure solution. You're setting your phpMyAdmin to be completely open to whoever can connect to it. 

gale85 there are so many factors that come into play with setting up PHPAdmin.
I have tried, to help narrow down things that could have gone wrong along with solutions that work for most.
I have both created and solved what you show in this thread.
I wish i could convince you to start fresh.
You have an incorrect string somewhere, and I can't get you to show me those without revealing your key to the city.
**sudo nano '/etc/phpmyadmin/config-db.php'**
```
<?php
##
## database access settings in php format
## automatically generated from /etc/dbconfig-common/phpmyadmin.conf
## by /usr/sbin/dbconfig-generate-include
##
## by default this file is managed via ucf, so you shouldn't have to
## worry about manual changes being silently discarded.  *however*,
## you'll probably also want to edit the configuration file mentioned
## above too.
##
$dbuser='phpmyadmin';
$dbpass='your-password';
$basepath='';
$dbname='phpmyadmin';
$dbserver='localhost';
$dbport='3306';
$dbtype='mysql';
```
I hope that you are able to get this sorted though.

---

### Post by gale85 on 2022-06-17
I was able to install wordpress with the root user. As far as I'm concerned, I can use it like this, I don't care if there will be another user for mysql, the only problem for me would be that phpmayadmin or mysql doesn't crash due to some php script. If it is, I will reinstall everything. I will do as you say, the most important thing for me is that she started doing everything properly

---

### Post by #&amp;thj^% on 2022-06-18
As I've already said, Providing root account access of phpMyAdmin can be harmful to your database server. So I recommend using non-root accounts for acceding databases.
Your phpMyAdmin is accessed by browser and not by IP.

Even if you host your page on your computer, it is still better to put a password. I get my computer and servers scanned for *phpMyAdmin*, *PMA* every single day.

So yes, it's unsafe. (And not just to you but others as well)
I may ask if this whole thread be jailed, to prevent unsafe usage by other readers....

---

### Post by gale85 on 2022-06-19
Okay, let me just check again. So everything that is written here should be done again and then I should install those packages again that I need to make all this work properly?

---

### Post by #&amp;thj^% on 2022-06-19
For safety sake yes!
This time stop on any error encountered and we will try to help you before proceeding to the next step.
Also it would help me at least to know what "all" you need to use for your site or PHPAdmin.

---

### Post by gale85 on 2022-06-19
All right, agreed. In the future, I will first write what kind of error occurs and then I will solve the problem together with you. I use phpmyadmin to make the site via wordpress or standalone php code which of course includes mysql

---

### Post by #&amp;thj^% on 2022-06-19
May I point you to this: [https://www.linuxshelltips.com/completely-uninstall-mysql-server-in-ubuntu/](https://www.linuxshelltips.com/completely-uninstall-mysql-server-in-ubuntu/)
I find it a bit better to completely removing mysql as a first step.
BTW my time on forum today is very limited, so just be patient I will return ASAP

---

### Post by gale85 on 2022-06-19
sudo rm -r /var/log/mysql
```

cannot remove '/var/log/mysql': No such file or directory

```
As far as I know this means that there is no mysql folder in the log folder. Now I can easily type the command sudo apt autoremove?
It's not a problem at all, when you arrive you will answer me and how many times I don't answer right away

---

### Post by #&amp;thj^% on 2022-06-19
Good work, now lets check these two:
```

ls /etc/mysql
sudo ls /var/lib/mysql
```
I need to see those.

---

### Post by gale85 on 2022-06-19
ls /etc/mysql
```

ls: cannot access '/etc/mysql': No such file or directory

```
sudo ls /var/lib/mysql
```

ls: cannot access '/var/lib/mysql': No such file or directory

```

---

### Post by #&amp;thj^% on 2022-06-19
Ah Ha....jumping to an early point to your problem, this may be the root of your problems before we started again to rebuild.
Can you show me the output from your autoremove command now:
```
sudo apt autoremove
```

---

### Post by gale85 on 2022-06-19
sudo apt autoremove
```

Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED:
  libaio1 libcgi-fast-perl libcgi-pm-perl libevent-core-2.1-7
  libevent-pthreads-2.1-7 libfcgi-bin libfcgi-perl libfcgi0ldbl
  libhtml-template-perl libmecab2 libprotobuf-lite23 mecab-ipadic
  mecab-ipadic-utf8 mecab-utils
0 upgraded, 0 newly installed, 14 to remove and 0 not upgraded.
After this operation, 57,3 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 315010 files and directories currently installed.)
Removing libaio1:amd64 (0.3.112-13build1) ...
Removing libcgi-fast-perl (1:2.15-1) ...
Removing libhtml-template-perl (2.97-1.1) ...
Removing libcgi-pm-perl (4.54-1) ...
Removing libevent-pthreads-2.1-7:amd64 (2.1.12-stable-1build3) ...
Removing libevent-core-2.1-7:amd64 (2.1.12-stable-1build3) ...
Removing libfcgi-bin (2.4.2-2build2) ...
Removing libfcgi-perl:amd64 (0.82+ds-1build1) ...
Removing libfcgi0ldbl:amd64 (2.4.2-2build2) ...
Removing mecab-ipadic-utf8 (2.7.0-20070801+main-3) ...
update-alternatives: using /var/lib/mecab/dic/ipadic to provide /var/lib/mecab/d
ic/debian (mecab-dictionary) in auto mode
Removing mecab-ipadic (2.7.0-20070801+main-3) ...
Removing mecab-utils (0.996-14build9) ...
Removing libmecab2:amd64 (0.996-14build9) ...
Removing libprotobuf-lite23:amd64 (3.12.4-1ubuntu7) ...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for libc-bin (2.35-0ubuntu3) ...

```

---

### Post by #&amp;thj^% on 2022-06-19
I found a good guide for you to follow now: [https://www.how2shout.com/linux/how-to-install-phpmyadmin-with-apache-on-ubuntu-22-04-lts/](https://www.how2shout.com/linux/how-to-install-phpmyadmin-with-apache-on-ubuntu-22-04-lts/)
Again stop on any problems and show me what they are.
I now gone for the day...;)

---

### Post by gale85 on 2022-06-19
sudo systemctl enable -now mariadb
```

Failed to parse lines 'ow'

```

---

### Post by #&amp;thj^% on 2022-06-20
Post back what is returned by terminal:
```
sudo systemctl enable --now mariadb
```
If your second thread is solved I will continue to help here in this thread.
_But this has to be solved first_: [https://ubuntuforums.org/showthread.php?t=2476191&p=14100996#post14100996](https://ubuntuforums.org/showthread.php?t=2476191&p=14100996#post14100996)

---

### Post by gale85 on 2022-06-20
sudo systemctl enable --now mariadb
```

Synchronizing state of mariadb.service with SysV service script with /lib/systemd/systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install enable mariadb
Job for mariadb.service failed because the control process exited with error code.
See "systemctl status mariadb.service" and "journalctl -xeu mariadb.service" for details.

```

---

### Post by #&amp;thj^% on 2022-06-20
Ok before we go on this needs to be sorted out first: [https://ubuntuforums.org/showthread.php?t=2476191&p=14100996#post14100996](https://ubuntuforums.org/showthread.php?t=2476191&p=14100996#post14100996)
No sense in going on until that happens.
The system is trying to create mysql.service symlink so that the stack can talk to the database under that name. What's running under that name may well be mariadb.
And it might be partially running:
```
sudo systemctl status mariadb
```
```
sudo systemctl status mariadb
[sudo] password for me: 
&#9679; mariadb.service - MariaDB 10.8.3 database server
     Loaded: loaded (/usr/lib/systemd/system/mariadb.service; enabled; vendor preset: disabled)
     Active: active (running) since Mon 2022-06-20 09:28:04 MDT; 25min ago
       Docs: man:mariadbd(8)
             https://mariadb.com/kb/en/library/systemd/
    Process: 671 ExecStartPre=/bin/sh -c systemctl unset-environment _WSREP_START_POSITION (code=ex>
    Process: 680 ExecStartPre=/bin/sh -c [ ! -e /usr/bin/galera_recovery ] && VAR= ||   VAR=`cd /us>
    Process: 913 ExecStartPost=/bin/sh -c systemctl unset-environment _WSREP_START_POSITION (code=e>
   Main PID: 774 (mariadbd)
     Status: "Taking your SQL requests now..."
      Tasks: 8 (limit: 8753)
     Memory: 277.3M
        CPU: 511ms
     CGroup: /system.slice/mariadb.service

```

---

### Post by gale85 on 2022-06-20
sudo systemctl status mariadb
```
mariadb.service - MariaDB 10.6.7 database server     Loaded: loaded (/lib/systemd/system/mariadb.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Mon 2022-06-20 18:21:59 CEST; 40min ago
       Docs: man:mariadbd(8)
             https://mariadb.com/kb/en/library/systemd/
    Process: 35217 ExecStartPre=/usr/bin/install -m 755 -o mysql -g root -d /var/run/mysqld (code>
    Process: 35218 ExecStartPre=/bin/sh -c systemctl unset-environment _WSREP_START_POSITION (cod>
    Process: 35220 ExecStartPre=/bin/sh -c [ ! -e /usr/bin/galera_recovery ] && VAR= ||   VAR=`cd>
    Process: 35228 ExecStart=/usr/sbin/mariadbd $MYSQLD_OPTS $_WSREP_NEW_CLUSTER $_WSREP_START_PO>
   Main PID: 35228 (code=exited, status=1/FAILURE)
     Status: "MariaDB server is down"
        CPU: 133ms


&#1112;&#1091;&#1085; 20 18:21:59 gale85-EP35-DS3R systemd[1]: Starting MariaDB 10.6.7 database server...
&#1112;&#1091;&#1085; 20 18:21:59 gale85-EP35-DS3R mariadbd[35228]: 2022-06-20 18:21:59 0 [Note] /usr/sbin/mariadbd>
&#1112;&#1091;&#1085; 20 18:21:59 gale85-EP35-DS3R mariadbd[35228]: 2022-06-20 18:21:59 0 [Warning] Can't create te>
&#1112;&#1091;&#1085; 20 18:21:59 gale85-EP35-DS3R mariadbd[35228]: [99B blob data]
&#1112;&#1091;&#1085; 20 18:21:59 gale85-EP35-DS3R mariadbd[35228]: 2022-06-20 18:21:59 0 [ERROR] Aborting
&#1112;&#1091;&#1085; 20 18:21:59 gale85-EP35-DS3R systemd[1]: mariadb.service: Main process exited, code=exited, s>
&#1112;&#1091;&#1085; 20 18:21:59 gale85-EP35-DS3R systemd[1]: mariadb.service: Failed with result 'exit-code'.
&#1112;&#1091;&#1085; 20 18:21:59 gale85-EP35-DS3R systemd[1]: Failed to start MariaDB 10.6.7 database server.
```

---

### Post by #&amp;thj^% on 2022-06-21
I'm still waiting for your confirmation for your other thread has been solved first.
in meantime show this:
```
mysqld --help --verbose | grep 'log-error' | tail -1

```
Or both this as well:
```
mysqld --help --verbose | grep 'datadir' | tail -1

```

---

### Post by gale85 on 2022-06-21
mysqld --help --verbose | grep 'log-error' | tail -1
```

2022-06-22  1:24:39 0 [Warning] Could not open mysql.plugin table: "Table 'mysql.plugin' doesn't exist". Some options may be missing from the help text
log-error 

```
mysqld --help --verbose | grep 'datadir' | tail -1
```

2022-06-22  1:26:05 0 [Warning] Could not open mysql.plugin table: "Table 'mysql.plugin' doesn't exist". Some options may be missing from the help text
datadir                                                      /var/lib/mysql/

```

---

### Post by #&amp;thj^% on 2022-06-23
Can you show what kernel your using now?
```
uname -a
```
Jammy has been hit with another bug for /mariadb: [https://bugs.launchpad.net/ubuntu/+source/mariadb-10.6/+bug/1970634](https://bugs.launchpad.net/ubuntu/+source/mariadb-10.6/+bug/1970634)

---

### Post by gale85 on 2022-06-23
uname -a
```

Linux mycomp-EP35-DS3R 5.15.0-40-generic #43-Ubuntu SMP Wed Jun 15 12:54:21 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by #&amp;thj^% on 2022-06-23
We will not proceed until this is fixed: [https://ubuntuforums.org/showthread.php?t=2476191&p=14101389#post14101389](https://ubuntuforums.org/showthread.php?t=2476191&p=14101389#post14101389)
That bug I showed may be playing a factor here as well.

---

### Post by miguelabfonseca on 2023-05-18
Hi,

Can it be because you are use of the short_open_tag?
short_open_tag = Off
By default is off

Best regards,
Miguel Fonseca

---

