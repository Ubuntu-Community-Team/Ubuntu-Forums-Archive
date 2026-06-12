---
title: "HOWTO: Enabling the Universe APT repository"
date: 2004-10-11
forum: Outdated Tutorials &amp; Tips
---

### Post by ubuntu-geek on 2004-10-11
First open a terminal window and enter:
sudo nano /etc/apt/sources.list

Look for the following lines:
> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted

Change them to look like:
> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted universe

Save the file and then run:
sudo apt-get update

This will update your repository and include all the files available in the universe.

---

### Post by LongTooth on 2004-10-12
If I include 'Universal' in my repository will there be any conflicts? True, I just installed Ubuntu and haven't done much with it but still the thought of conflicts does come up. Any problems downloading software from Universal? One other thing, is Universal packages straight from the Debian resorces? Thanks.

---

### Post by LongTooth on 2004-10-12
I should mention that the lines to alter are already there. Just uncomment them.

---

### Post by chet on 2004-11-05
I have followed the steps above and downloaded prismstumbler, I ran synaptic and installed the package but when I try and run prismstumbler I get the error /usr/bin/pst is missing

Have I correctly installed the package looking at the above?

Cheer

Chet

---

### Post by Pablasso on 2004-11-08
Hi! im new to ubuntu (i installed it just yesterday)

its there any real problem activating universal instead of the normal list?

i had just modified it, cuz i couldn't install the necesary python lib for bittorrent, but had no problems with universal

also i just installed bluefish (sudo apt-get install bluefish) and had no problems installing it but when i run it it displays this

```
root@ubuntu:/home/pablasso # bluefish

(bluefish:5868): Gtk-CRITICAL **: file gtkwidget.c: line 4205 (gtk_widget_set_sensitive): assertion `GTK_IS_WIDGET (widget)' failed

(bluefish:5868): Gtk-CRITICAL **: file gtkwidget.c: line 4205 (gtk_widget_set_sensitive): assertion `GTK_IS_WIDGET (widget)' failed

(bluefish:5868): Gtk-CRITICAL **: file gtkwidget.c: line 4205 (gtk_widget_set_sensitive): assertion `GTK_IS_WIDGET (widget)' failed

(bluefish:5868): Gtk-CRITICAL **: file gtkwidget.c: line 4205 (gtk_widget_set_sensitive): assertion `GTK_IS_WIDGET (widget)' failed
``` 

anyway it loads ok, but i had no idea of what that mesagges mean...

thanks!

---

### Post by sumanjay on 2004-11-08
I've run into a rather interesting problem after adding Universe - Synaptic now doesn't display any packages! It shows categories, but the actual packages and their descriptions are missing. Any ideas?

---

### Post by Pablasso on 2004-11-08
did you only uncomment the universe lines or did something else?

---

### Post by sumanjay on 2004-11-14
I fixed the problem by deleting all .synaptic.conf files in my home directory. Apparently, it is a bug with that version of Synaptic.

---

### Post by winRefugee on 2004-11-14
I have tried both this process and the one outlined in the wiki. Both, however, generate the same response:

404 directory doesn't exist

Is the universal directory off-line? Been moved?

thanks

---

### Post by TravisNewman on 2004-11-14
[QUOTE=winRefugee]I have tried both this process and the one outlined in the wiki. Both, however, generate the same response:

404 directory doesn't exist

Is the universal directory off-line? Been moved?

thanks[/QUOTE]
 If you're typing "universal" instead of "universe" you'll probably get that error.

A 404 error means you typed something wrong.

---

### Post by oddabe19 on 2004-11-16
[QUOTE=Pablasso]Hi! im new to ubuntu (i installed it just yesterday)

its there any real problem activating universal instead of the normal list?

i had just modified it, cuz i couldn't install the necesary python lib for bittorrent, but had no problems with universal

also i just installed bluefish (sudo apt-get install bluefish) and had no problems installing it but when i run it it displays this

```
root@ubuntu:/home/pablasso # bluefish

(bluefish:5868): Gtk-CRITICAL **: file gtkwidget.c: line 4205 (gtk_widget_set_sensitive): assertion `GTK_IS_WIDGET (widget)' failed

(bluefish:5868): Gtk-CRITICAL **: file gtkwidget.c: line 4205 (gtk_widget_set_sensitive): assertion `GTK_IS_WIDGET (widget)' failed

(bluefish:5868): Gtk-CRITICAL **: file gtkwidget.c: line 4205 (gtk_widget_set_sensitive): assertion `GTK_IS_WIDGET (widget)' failed

(bluefish:5868): Gtk-CRITICAL **: file gtkwidget.c: line 4205 (gtk_widget_set_sensitive): assertion `GTK_IS_WIDGET (widget)' failed
``` 

anyway it loads ok, but i had no idea of what that mesagges mean...

thanks![/QUOTE]


That's normal, don't worry about it.

---

### Post by paradox on 2004-12-16
Sorry. How i can create a local repository in my HD? I can try:

deb file:/dir_packages_deb stable main contrib non -free

but apt-get update return an errors: 

Packages.gz file not found. 

I must execute a procedure to create a local repository (create *.gz file etc...)?

---

### Post by theonlyalterego on 2005-01-14
Hey, Im trying to install bluefish, and I did what Pablasso said ''sudo apt-get install bluefish'' but it says this
> XXX@XXX:/usr/local # sudo apt-get install bluefish
Reading Package Lists... Done
Building Dependency Tree... Done
Package bluefish is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package bluefish has no installation candidate
Im new to Ubuntu, so can anyone tell me what I need to get Bluefish installed?
Thanks,
  Alter

---

### Post by Perfect Storm on 2005-01-14
Did you enable the 'universe'? You may recheck. Well...if it's teasing you take a check

<computer> --->  <System Configuration> -----> <Synaptic Package Management>

and search for bluefish.

---

### Post by Buffalo Soldier on 2005-01-28
[QUOTE=paradox]Sorry. How i can create a local repository in my HD?[/QUOTE]

[Automatic Debian Package Repository HOWTO](http://familiasanchez.net/~sanchezr/?page=debrepository)

[Debian Repository HOWTO](http://www.debian.org/doc/manuals/repository-howto/repository-howto.html)

---

### Post by shrekkie on 2005-03-01
Hey everyone, 
                       I am new to unix/linux and also ubuntu, I have only used mandrake before so please bear with me here. As explained in the first post I need to edit the two lines in the sources.list file, I did that, but how do I save a file in nano? I tried looking it up in the manpages using "man nano" but I couldn't see any help on saving a file. Any help will be greatly appreciated :)

---

