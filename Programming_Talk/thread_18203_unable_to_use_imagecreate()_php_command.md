---
title: "unable to use imagecreate() php command"
date: 2005-03-05
forum: Programming Talk
---

### Post by isaac on 2005-03-05
i have installed apache2 and php4-dev package.. the php seems to be working just that i can't use the image function to create image or even load image... what's the mistake... i visited php.net ... and it seems to be the problem of "GD" not activated? where is gd located anywhere? 

Really need help here... thanks  :confused:  :confused:

---

### Post by isaac on 2005-03-05
i'm very eager to use image drawing command in php but it seems that the apt-get php4 did not get the gd enable...

it seems like i need to enable it by adding "--with-gd" in the configure parameter... but where is the configure parameter located??!?!?!

---

### Post by HungSquirrel on 2005-03-05
[QUOTE=isaac]i'm very eager to use image drawing command in php but it seems that the apt-get php4 did not get the gd enable...

it seems like i need to enable it by adding "--with-gd" in the configure parameter... but where is the configure parameter located??!?!?![/QUOTE]
 "Configure parameters" are options you enable when compiling something from source.  Since you are using the Ubuntu package for PHP, you have no control over what configure parameters were used when it was compiled.  If, as you say, gd was not enabled in the official package, you should ask the devs to do it in the next version of the package.  I'm not sure where/how you can submit such requests.  Perhaps our esteemed moderators do.  :)

---

### Post by Maulwurf on 2005-03-22
you have to install the package php4-gd2 and afterwards edit the file /etc/php4/apache2/php.ini. search for gd.so, you'll find it in the section extensions and uncomment that line. restart the apache webserver with sudo /etc/init.d/apache2 restart and the function imagecreate() should work.

---

### Post by jfdill_2 on 2005-05-30
[QUOTE=Maulwurf]you have to install the package php4-gd2 and afterwards edit the file /etc/php4/apache2/php.ini. search for gd.so, you'll find it in the section extensions and uncomment that line. restart the apache webserver with sudo /etc/init.d/apache2 restart and the function imagecreate() should work.[/QUOTE]
Fantastic, that also fixed the egroupware set up that I was trying to do, now it passes all of the the pre-config tests.  For egroupware, you also need to un-comment the mysql.so line in php.ini.

---

