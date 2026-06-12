---
title: "how can i install the GD-library php 5"
date: 2007-03-07
forum: Programming Talk
---

### Post by don durito on 2007-03-07
Hi,
just installed drupal 5.1 and i am trying to resolv some errors. i am unsing the standard ubuntu default lamp configuration. and drupal tells me that there either is no gd-library or it is outdated. and now i should install the gd-librarys but i don't have any clue how to do this. 

please help my guys 

thanks in advance 

don

---

### Post by hod139 on 2007-03-07
Try installing the package libgd2-dev.

---

### Post by lnostdal on 2007-03-07
try:
```
sudo -i
aptitude search libgd

```

..then use `aptitude show' to show info about packages (i don't know exactly which GD-package drupal depends on without checking)

..or you can use synaptic and do the same things via a GUI

edit: i think this is wrong .. php5-gd is probably the correct package   (though .. it depends on some libgd but this is handled automatically)

---

### Post by don durito on 2007-03-07
I tried to install libgd2-dev which worked fine. but there was no diffenrence in drupal. so i tried a nice reboot. but now i am realy ****** up. when i try to open either my drupal start side or phpmyadmin my stupid firefox tries to download some stupid php site. so i can't open my start sites anymore.

please help me guys this isn't funny anymore

---

### Post by lnostdal on 2007-03-07
ok, what happens when you do:

```

sudo /etc/init.d/apache2 restart

```

..?

is anything mentioned in /var/log/apache2/error.log ...?

maybe just doing ```
sudo aptitude remove php5
``` ..     then ```
sudo aptitude install php5 
``` will help, but i don't know at this point

maybe even:
```
sudo aptitude purge apache2 php5
sudo aptitude install apache2 php5

```

(note that this will also remove any changes you've done to your config-files in /etc ...! .. be sure to take a backup if needed)

---

### Post by don durito on 2007-03-07
thanks for the quik reply 
restarting the apache worked fine but made no difference to my proplem 

this is the error log: 
  [Mon Mar 05 04:20:43 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.6 configured -- resuming normal operations
[Mon Mar 05 04:34:25 2007] [notice] caught SIGTERM, shutting down
[Mon Mar 05 17:23:08 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.6 configured -- resuming normal operations
[Mon Mar 05 17:23:47 2007] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Mon Mar 05 17:43:47 2007] [notice] caught SIGTERM, shutting down
[Tue Mar 06 11:45:58 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.6 configured -- resuming normal operations
[Tue Mar 06 11:46:33 2007] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Wed Mar 07 00:52:00 2007] [notice] caught SIGTERM, shutting down
[Wed Mar 07 13:11:47 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.6 configured -- resuming normal operations
[Wed Mar 07 14:27:17 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Wed Mar 07 14:27:17 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Wed Mar 07 14:27:17 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Wed Mar 07 14:27:45 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Wed Mar 07 14:27:47 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Wed Mar 07 14:27:47 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Wed Mar 07 14:28:14 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Wed Mar 07 14:28:15 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Wed Mar 07 14:28:26 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Wed Mar 07 14:28:26 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Wed Mar 07 14:28:34 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Wed Mar 07 14:28:34 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Wed Mar 07 14:28:38 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Wed Mar 07 14:28:38 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Wed Mar 07 14:43:51 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Wed Mar 07 14:43:52 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Wed Mar 07 14:43:52 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Wed Mar 07 14:44:04 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Wed Mar 07 14:44:06 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Wed Mar 07 14:44:06 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Wed Mar 07 14:44:13 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Wed Mar 07 14:44:13 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Wed Mar 07 14:44:14 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Wed Mar 07 14:44:53 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Wed Mar 07 14:44:53 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Wed Mar 07 14:44:58 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Wed Mar 07 14:44:58 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Wed Mar 07 14:45:03 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Wed Mar 07 14:45:03 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Wed Mar 07 14:46:00 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Wed Mar 07 14:46:01 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Wed Mar 07 14:46:01 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Wed Mar 07 14:46:12 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Wed Mar 07 14:46:12 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Wed Mar 07 14:46:13 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Wed Mar 07 14:46:15 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Wed Mar 07 14:46:15 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Wed Mar 07 14:46:15 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Wed Mar 07 14:46:24 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Wed Mar 07 14:46:25 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Wed Mar 07 14:48:21 2007] [error] [client 127.0.0.1] File does not exist: /var/www/phpmyadmin/favicon.ico
[Wed Mar 07 17:57:04 2007] [notice] caught SIGTERM, shutting down
[Wed Mar 07 17:58:35 2007] [notice] Apache/2.0.55 (Ubuntu) configured -- resuming normal operations
[Wed Mar 07 17:59:22 2007] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Wed Mar 07 18:29:43 2007] [notice] caught SIGTERM, shutting down
[Wed Mar 07 18:35:16 2007] [notice] Apache/2.0.55 (Ubuntu) configured -- resuming normal operations
[Wed Mar 07 18:35:55 2007] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Wed Mar 07 18:35:59 2007] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Wed Mar 07 18:35:59 2007] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Wed Mar 07 18:36:18 2007] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico, referer: [http://127.0.0.1/](http://127.0.0.1/)
[Wed Mar 07 19:25:44 2007] [notice] caught SIGTERM, shutting down
[Wed Mar 07 19:25:45 2007] [notice] Apache/2.0.55 (Ubuntu) configured -- resuming normal operations


i tried the rest of you commands it worked all well. but i didn't made a difference to my problem. still when i try to enter my phpadmin or drupal through my localhost. firefox or opera tries to download some php files.

---

### Post by lnostdal on 2007-03-07
you're browsing using an address like [http://localhost/](http://localhost/)... and not file://...  right? .. heh .. pretty obvious i guess

edit: maybe clearing the browser cache would help at this point

---

### Post by don durito on 2007-03-07
yeah i am using [http://127.0.0.1/](http://127.0.0.1/) which is localhoast
and clearing my cach won't make any difference.

because it isn't working either in firefox nor opera

---

### Post by don durito on 2007-03-07
perhaps you know how to delet the whole crap. and reinstall the complete server pherahaps this will work

---

### Post by lnostdal on 2007-03-07
wait .. i missed something ..  PHP isn't actually loaded when i look at the log you pasted .. try doing this:

```

sudo -i
ln -s /etc/apache2/mods-available/php5.conf /etc/apache2/mods-enabled/
ln -s /etc/apache2/mods-available/php5.load /etc/apache2/mods-enabled/
/etc/init.d/apache2 restart

```

hm, but reinstalling should have done this automatically

---

### Post by don durito on 2007-03-07
this is my apache restart output:
root@peter-desktop:~# /etc/init.d/apache2 restart
 * Forcing reload of apache 2.0 web server...                                   apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ ok ]

but still no difference

---

### Post by don durito on 2007-03-07
but once agaain perhaps you know how to uninstall the complete lamp anr reinstall it. i mean when all the date is gone there is no problem

---

### Post by don durito on 2007-03-07
bytheway this his how it looks when i klick on phpmyadmin or drupal

---

### Post by lnostdal on 2007-03-07
that message isn't critical .. but what did error.log say after restarting this time?

doing `aptitude purge' back here is basically a reinstall .. but if you want a full reinstall you can just put the ubuntu cd back in and do a reboot and delete the root partition and reinstall there .. this shouldn't be necessary though

---

### Post by don durito on 2007-03-07
here it comes


[Wed Mar 07 18:36:18 2007] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico, referer: [http://127.0.0.1/](http://127.0.0.1/)
[Wed Mar 07 19:25:44 2007] [notice] caught SIGTERM, shutting down
[Wed Mar 07 19:25:45 2007] [notice] Apache/2.0.55 (Ubuntu) configured -- resuming normal operations
[Wed Mar 07 20:04:39 2007] [notice] caught SIGTERM, shutting down
[Wed Mar 07 20:04:41 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.6 configured -- resuming normal operations

no i don't want the reinstall the whole ubuntu just the lamp

---

### Post by lnostdal on 2007-03-07
```
Apache/2.0.55 (Ubuntu) PHP/5.1.6 configured -- resuming normal operations
```
..means that PHP should be running..

---

### Post by don durito on 2007-03-07
i know but what is the problem

---

### Post by lnostdal on 2007-03-07
i just realised php5-gd is probably the package you're after for GD .. (it depends on libgd* which is installed automatically if you install it)

..now about your latest problem i got to say i do not know at this point

---

### Post by don durito on 2007-03-07
but do you know how i can reinstall the complete lamp i mean without linux just apache mysql and php

---

### Post by lnostdal on 2007-03-07
edit: naw .. just a sec here ..

edit2:
right .. purge any installed apache-related packages: aptitude search apache ..  then do aptitude purge on anything with an "i" on the left .. turns out there are quite a few .. then purge php5 .. 

then install apache2 and php5 again .. that should do it

---

### Post by don durito on 2007-03-07
did everything you said but still the same old problem when i click on phpmyadmin or test firefox still wants to download some php ****

---

### Post by lnostdal on 2007-03-07
ok, if you're totally stuck and you're willing to give me temporary ssh-access i can take a look

i've got an msn and jabber/gtalk account: [email]larsnostdal@gmail.com[/email] .. or you can join the irc-channel in my sig. and you'll find me

edit: this is only possible if you know your way around port-forwarding .. which might be required if you're running this behind a router/firewall .. edit2: solved it by doing some reverse ssh'ing ..... :)

---

### Post by don durito on 2007-03-07
sure don't know how i can give you this access but ok

---

### Post by jetsam on 2007-03-18
I just installed Drupal 5.1 last night for the first time, and had the same issue you had with the gd related error message.  Using Synaptic to install php5-gd, which installs libgd2-xpm as a dependency, fixed the error message for me without any issues.  

My guess is that the libgd2-dev package you installed is causing your problems.  Try uninstalling that and installing php5-gd?  

If you get it working, you also might want to do this (cut and pasted from the community help [page]("https://help.ubuntu.com/community/ApacheMySQLPHP") on installing LAMP):

If you get this error:

apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName

then edit:

gksudo gedit /etc/apache2/apache2.conf

and add:

ServerName localhost 

at the end of the file.

Edit:  I just noticed your problem was solved already.  I'm leaving this here so other people know that just installing php5-gd fixes the error and doesn't cause issues.

---

