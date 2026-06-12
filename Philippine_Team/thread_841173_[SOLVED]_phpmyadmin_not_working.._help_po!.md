---
title: "[SOLVED] phpmyadmin not working.. help po!"
date: 2008-06-26
forum: Philippine Team
---

### Post by Pedro0727 on 2008-06-26
i already installed phpmyadmin but something wrong the the [http://localhost/phpmyadmin](http://localhost/phpmyadmin) display error mssge. :confused:

help po plzz..

---

### Post by daxumaming on 2008-06-26
make sure php5 and apache's installed. now type this code to enable phpmyadmin:

```
sudo a2ensite phpmyadmin
```

---

### Post by Pedro0727 on 2008-06-26
[http://localhost](http://localhost) is working po sir

but when accessing the phpmyadmin server not found 

i already installed the php and apache

sudo a2ensite phpmyadmin
 
this site does not exist ->mssge s terminal

---

### Post by daxumaming on 2008-06-26
> **Pedro0727 said:**
> [url]
sudo a2ensite phpmyadmin
 
this site does not exist ->mssge s terminal

that means phpmyadmin isn't installed. did you install phpmyadmin from the repo? if so, try this:

```
sudo aptitude purge phpmyadmin
```
followed by
```
sudo aptitude install phpmyadmin
```

---

### Post by Samhain13 on 2008-06-26
Err... may I suggest MySQL Administrator and MySQL Query Browser? Hindi nga lang sila browser-based.

Dati kasi PHPMyAdmin din ang gamit ko, pero at some point nagkaproblema ako. Matagal na yun, since Feisty pa yata, kaya ko sinubukan yung mga apps na nirerekumenda ko. Yun pa din ang gamit ko ngayon. :)

---

### Post by jeffimperial on 2008-06-27
> **Samhain13 said:**
> Err... may I suggest **MySQL Administrator** and **MySQL Query Browser**? Hindi nga lang sila browser-based....
^ may remote access feature ba sila? ^

---

### Post by Samhain13 on 2008-06-27
Remote access feature = someone from the outside being able to use them?
I don't think so.

Remote access feature = using the apps to access a DB in another location?
Yes.

---

### Post by jeffimperial on 2008-06-27
Oh. I'll make sure to look into them. Got some links for those pieces?

---

### Post by Samhain13 on 2008-06-27
Err, they're available in the repos. :D
I don't know if there's a site I can point you to for more info. But perhaps there are links in the info from Synaptic.

---

### Post by jeffimperial on 2008-06-27
Ahh. Di ko 'yun na-realize. Anyways, i'll try asking kuya Google kung may Windows version sila. Kasi may ginawa akong DB solution para sa isang kumpanya, tapos kailangan syempre nila ng access. Di ako komportable na bigyan sila ng phpMyAdmin access kasi hindi user friendly (sabi nila) at parang delikado (sa parte ko - baka makasira sila).

---

### Post by Samhain13 on 2008-06-27
Ah... giving them these two apps might not be a good idea. The apps work just like PHPMyAdmin, but they're not browser-based and have their own "windows"-- that's the difference. Perhaps it would be better for you to just write a PHP front-end for them instead of giving them administrative tools like these apps.

Is this related to our conversation in "Kuwentuhan"? I think that class you discovered is good for your purposes. We just need to iron a few things out. Hehe.

---

### Post by jeffimperial on 2008-06-27
Yep. I just learned that a few moments ago when I tried out those two apps. Mukhang kailangan ko pa rin talaga 'yung class na yun. Or write one myself. Haay

Opo, this is exactly about that Kwentuhan question.

---

### Post by Kilarin on 2008-06-27
Hello!  I'm having the same issues as the original poster.
(this issue is also being discussed for yet another user in: [<this thread>](http://ubuntuforums.org/showthread.php?t=114129&highlight=phpmyadmin&page=3))

I installed php/mysql/apache using the instructions I found here [http://www.strdoc.net/ubuntu-apache-php-mysql-server-804-hardyheron](http://www.strdoc.net/ubuntu-apache-php-mysql-server-804-hardyheron)
```

#  Install SSH Client and Server (for my remote access)
sudo apt-get install ssh
# Install Database Server
sudo apt-get install mysql-server-5.0
# Install Apache HTTP Server
sudo apt-get install apache2
# Install PHP5 and Apache PHP5 module
sudo apt-get install php5 libapache2-mod-php5
# Restart Apache
sudo /etc/init.d/apache2 restart
# Optionally, install phpMyAdmin
sudo apt-get install phpmyadmin
```

And php works fine.  I can point firefox at [http://localhost](http://localhost) and set up cool php pages, no problem.  

BUT, now its time to learn how to combine mysql with php.  So I tried pulling up [http://localhost/phpmyadmin](http://localhost/phpmyadmin) or [http://localhost/phpMyAdmin](http://localhost/phpMyAdmin) or [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) or [http://localhost/phpMyAdmin/](http://localhost/phpMyAdmin/), and I get 404 errors on all of them.

I went into synaptic package manager and marked phpMyAdmin for reinstallation.  reinstalled it, rebooted, and tried again.  same 404 errors.  phpMyAdmin IS installed, but I can't GET to it.  When I try to enable it, as some have suggested, I get:

```
$ sudo a2ensite phpmyadmin
This site does not exist!
$ sudo a2ensite phpMyAdmin
This site does not exist!

```

Something is very wrong here.  Several people are experiencing the problem, so it's not just one of us doing something stupid. Any ideas?

---

### Post by adredz on 2008-06-27
Pedro0727,Kilarin:
i don't know if you're experiencing the same problem i've just experienced...

here's what i did..
i created a symbolic link named phpmyadmin in /var/www pointing to /usr/share/phpmyadmin cos usually there should be one..in case you don't know how to do it just type:

> sudo ln -s /usr/share/phpmyadmin /var/www/phpmyadmin 

note that i am assuming your phpmyadmin folder is located in /usr/share/. to know where it is located, just type:
>  whereis phpmyadmin 

after you have created the symlink, everything should be fine. hope this helps..

---

### Post by Kilarin on 2008-06-27
[quote="adredz"]after you have created the symlink, everything should be fine. hope this helps.. [/quote]
YOU are a genius!  It works GREAT.  Thank you VERY much!

---

### Post by adredz on 2008-06-28
> **Kilarin said:**
> YOU are a genius!  It works GREAT.  Thank you VERY much!

my pleasure.. though it sounds great to be like a GENIUS to you, it wasn't my idea at all.:lolflag:

---

### Post by daxumaming on 2008-06-28
ok, the sudo a2ensite phpmyadmin won't work.. since it ain't listed in /etc/apache2/sites-available... my bad!

however, there shouldn't be any need to create a symbolic link to your /var/www since it's already on /etc/apache2/conf.d/phpmyadmin.conf

come to think of it, can you post the output of
```
less /etc/apache2/conf.d/phpmyadmin.conf
```

---

### Post by Kilarin on 2008-06-28
[quote="daxumaming"]there shouldn't be any need to create a symbolic link to your /var/www since it's already on /etc/apache2/conf.d/phpmyadmin.conf
come to think of it, can you post the output of[/quote]

```
~$ less /etc/apache2/conf.d/phpmyadmin.conf
/etc/apache2/conf.d/phpmyadmin.conf: No such file or directory

```
Does that help explain whats going on in some way?

---

### Post by daxumaming on 2008-06-29
actually, it explains a lot. phpmyadmin's not working 'coz its configuration file's missing. you can either do 2 things.

1) create a symbolic link to phpmyadmin's config file

```
sudo ln -s /etc/phpmyadmin/apache.conf /etc/apache2/conf.d/phpmyadmin.conf
```

2) and if that didn't work, do it manually

create and edit the file
```

sudo vim /etc/apache2/conf.d/phpmyadmin.conf
or
sudo nano /etc/apache2/conf.d/phpmyadmin.conf

```

then paste the following code
```

# phpMyAdmin default Apache configuration

Alias /phpmyadmin /usr/share/phpmyadmin

<Directory /usr/share/phpmyadmin>
        Options Indexes FollowSymLinks
        DirectoryIndex index.php

        # Authorize for setup
        <Files setup.php>
            # For Apache 1.3 and 2.0
            <IfModule mod_auth.c>
                AuthType Basic
                AuthName "phpMyAdmin Setup"
                AuthUserFile /etc/phpmyadmin/htpasswd.setup
            </IfModule>
            # For Apache 2.2
            <IfModule mod_authn_file.c>
                AuthType Basic
                AuthName "phpMyAdmin Setup"
                AuthUserFile /etc/phpmyadmin/htpasswd.setup
            </IfModule>
            Require valid-user
        </Files>
        <IfModule mod_php4.c>
                AddType application/x-httpd-php .php

                php_flag magic_quotes_gpc Off
                php_flag track_vars On
                php_flag register_globals Off
                php_value include_path .
        </IfModule>
        <IfModule mod_php5.c>
                AddType application/x-httpd-php .php

                php_flag magic_quotes_gpc Off
                php_flag track_vars On
                php_flag register_globals Off
                php_value include_path .
        </IfModule>
</Directory>

```

save the file and restart/reload apache
```

sudo /etc/init.d/apache2 reload
or
sudo /etc/init.d/apache2 restart

```

oh, and don't forget the delete the phpmyadmin link at /var/www. this is very important since linking the phpmyadmin directory poses security risk especially if your server is public. users will be able to see the files inside the phpmyadmin directory.

---

### Post by adredz on 2008-06-29
> **daxumaming said:**
> 
however, there shouldn't be any need to create a symbolic link to your /var/www since it's already on /etc/apache2/conf.d/phpmyadmin.conf

wow, your fix works. thanks!:)
however, i noticed there's no difference between the default phpmyadmin.conf and the one you provided. could you explain why it worked?

---

### Post by daxumaming on 2008-06-29
> **adredz said:**
> wow, your fix works. thanks!:)
however, i noticed there's no difference between the default phpmyadmin.conf and the one you provided. could you explain why it worked?

I just copied and pasted Ubuntu's or PHPMyAdmin's /etc/phpmyadmin/apache.conf just in case you need it since I'm not sure you have that same file on that same directory

What's important is that you have the values between <Directory></Directory> to secure phpmyadmin.

---

### Post by adredz on 2008-06-29
> **daxumaming said:**
> I just copied and pasted Ubuntu's or PHPMyAdmin's /etc/phpmyadmin/apache.conf just in case you need it since I'm not sure you have that same file on that same directory

from where exactly po? from your box? is your box a server edition? so you you just copied it from there or from your desktop?
either way, they're exactly the same.. maybe it could be the link you suggested that sorted things out? however, that didn't solve the problem after i created it but only after replacing the phpmyadmin.conf file. hehehe. naleleto na ako.:)

---

### Post by Kilarin on 2008-06-29
[quote="daxumaming"]linking the phpmyadmin directory poses security risk [/quote]
Yikes!  done!  Thanks for the warning! 

[quote="daxumaming"]create a symbolic link to phpmyadmin's config file[/quote]
This didn't work for me, so I deleted it and went on to your next suggestion.

[quote="daxumaming"]and if that didn't work, do it manually[/quote]
This worked great!  Thanks!

now then, MY question is why didn't phpmyadmin install this conf file during installation?  Is there something wrong with the version in the Ubuntu repositories?

---

### Post by daxumaming on 2008-06-29
> **adredz said:**
> from where exactly po? from your box? is your box a server edition? so you you just copied it from there or from your desktop?

i have both a server and a workstation running phpmyadmin. but i copied the config file from my desktop and it's no different from the config file on my server.

> **Kilarin said:**
> 
now then, MY question is why didn't phpmyadmin install this conf file during installation?  Is there something wrong with the version in the Ubuntu repositories?

not really sure if there's something wrong, but your config file's non-existent when it should be. check if there's an apache.conf file at /etc/phpmyadmin. if none, better file a bug report since there's a few users affected by this bug. the maintainer must've overlooked this when he/she uploaded phpmyadmin to the Hardy repo.

i upgrade my Gutsy to Hardy, and i configured it (during the upgrade) not to replace all my config files. however, the Gutsy phpmyadmin config file shouldn't be different from Hardy.

---

### Post by Pedro0727 on 2008-06-30
> **adredz said:**
> Pedro0727,Kilarin:
i don't know if you're experiencing the same problem i've just experienced...

here's what i did..
i created a symbolic link named phpmyadmin in /var/www pointing to /usr/share/phpmyadmin cos usually there should be one..in case you don't know how to do it just type:

 

note that i am assuming your phpmyadmin folder is located in /usr/share/. to know where it is located, just type:


after you have created the symlink, everything should be fine. hope this helps..

MARAMING SALAMAT PO! its really working.. \\:D/=D>

---

### Post by Pedro0727 on 2008-06-30
i would like to gave thanks for those who help to fix the problem of phpmyadmin.. hehehe.. maraming salamat po sainyong lahat. happy coding:)

tnx to adredz,daxumaming and the others..

---

### Post by Kilarin on 2008-06-30
[quote="daxumaming"]check if there's an apache.conf file at /etc/phpmyadmin[/quote]
Yes, I do have a /etc/phpmyadmin/apache.conf
It's identical to the one you gave us to cut and paste into /etc/apache2/conf.d/phpmyadmin.conf.

But that still leaves us with an odd mystery.  Why is there no /etc/apache2/conf.d/phpmyadmin.conf since we obviously need one?  Should we open a bug report on this (I've never done that before)

---

### Post by AlexanderDGreat on 2009-08-20
Hi, I did this:

apt-get install apache2
apt-get install mysql-server
apt-get install php5
apt-get install php5-mysql
apt-get install phpmyadmin

Then phpmyadmin didn't work, so I did what you said: manually copy & paste /etc/phpmyadmin/apache.conf to /etc/apache2/conf.d/phpmyadmin.conf

Then phpmyadmin worked!

HOWEVER, after a few weeks, I can't run localhost/phpmyadmin ANYMORE!

So confused... Why did this happen? What will I do now? Can you pls. help? Thanks.

***

Found the solution to my own stupid problem:

I changed apache2's user from www-data to my own account in /etc/apache2/envvars because I was studying filepermissions, chown, chmod commands in building php-enabled-websites, my bad sorry... Everything's fine now. =)

---

### Post by Ferryfromholland on 2011-12-10
I had the same problem, 404 on localhost/phpmyadmin, this fixed it, Thanks!! :KS


> **adredz said:**
> Pedro0727,Kilarin:
i don't know if you're experiencing the same problem i've just experienced...

here's what i did..
i created a symbolic link named phpmyadmin in /var/www pointing to /usr/share/phpmyadmin cos usually there should be one..in case you don't know how to do it just type:

 sudo ln -s /usr/share/phpmyadmin /var/www/phpmyadmin

note that i am assuming your phpmyadmin folder is located in /usr/share/. to know where it is located, just type:


after you have created the symlink, everything should be fine. hope this helps..

---

