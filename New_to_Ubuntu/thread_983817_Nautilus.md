---
title: "Nautilus"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by SilverShadow118 on 2008-11-16
Hello!

I would like to delete some files that have been locked - though that's not the problem. It's using the code "gksudo nautilus" to get those permissions. The files are located on a flash drive. My output for "gksudo nautilus" is the following

/usr/share/themes/UbuntuStudio/gtk-2.0/gtkrc:83: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please update this theme to get rid of this warning.
Initializing nautilus-share extension
seahorse nautilus module initialized/usr/share/themes/UbuntuStudio/gtk-2.0/gtkrc:83: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please update this theme to get rid of this warning.

(nautilus:7819): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:7819): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed



Can anyone help me? It would be greatly appreciated. Thank you.

---

### Post by ciscosurfer on 2008-11-16
Is a root nautilus window opening up after you type that in?  If not, switch to a different theme and then try again.

---

### Post by alwayshere on 2008-11-16
Try 

sudo nautilus
then go to  to the file ya want to delete

if the file you want to delete has a padlock on it .right click on it go to permissions i nthe first and second drop box choose  read and write 
then it should delete

---

### Post by 3rdalbum on 2008-11-16
Those error messages are not important, unless the root file browser is not opening. When you run Gnome programs in a terminal you do tend to get superfluous warnings and other cruft like that.

---

### Post by SilverShadow118 on 2008-11-16
Switching back to the default Human theme doesn't do anything and entering "gksudo nautilus"/"sudo nautilus" doesn't open up any file browser :/

---

### Post by alwayshere on 2008-11-16
thats some crazy stuff i guess that package has been deleted somehow on you travels im not to sure what package deals with that but it wouldnt hurt to 
run in terminal 

sudo apt-get install nautilus

then

sudo apt-get update 

maybe a restart  and see if that helps

---

### Post by alwayshere on 2008-11-16
There is a package nautilus-gksu  .  But i do not have that installed .
I must be using a differnt package which comes standard with ubuntu
I always use the" sudo nautilus " command to do my doings

 nautilus-gksu  ?????????????  decription below
---------------------------------------------------------
privilege granting extension for nautilus using gksu
The gksu extension for nautilus allows you to open files with
administration privileges using the context menu when browsing your
files with nautilus.

BUT I have no idea if that is a good idea or not to install !????
maybe wait for a few more post someone else might be more clued up

---

### Post by oldos2er on 2008-11-16
> **alwayshere said:**
> There is a package nautilus-gksu  .  But i do not have that installed .
I must be using a differnt package which comes standard with ubuntu
I always use the" sudo nautilus " command to do my doings

 nautilus-gksu  ?????????????  decription below
---------------------------------------------------------
privilege granting extension for nautilus using gksu
The gksu extension for nautilus allows you to open files with
administration privileges using the context menu when browsing your
files with nautilus.

BUT I have no idea if that is a good idea or not to install !????
maybe wait for a few more post someone else might be more clued up

 nautilus-gksu and nautilus-open-terminal are usually the first packages I install on Ubuntu. They're just scripts.

 It's a good idea to use the command "gksu nautilus" to launch Nautilus as root, rather than "sudo nautilus." Here's why: [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

---

### Post by Kellemora on 2008-11-16
Hi SS

Under Applications - System Tools, Install the Root Terminal.
You have to enter your password when opening it, but it lets you handle all of these problematic files with ease.

If you don't have it installed, Right Click on Applications then select Edit Menu's.

TTUL
Gary

---

### Post by fooman on 2008-11-16
> **oldos2er said:**
> nautilus-gksu and nautilus-open-terminal are usually the first packages I install on Ubuntu.

ditto that...good stuff.  :biggrin:

---

