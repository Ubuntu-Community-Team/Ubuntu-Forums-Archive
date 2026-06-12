---
title: "HOWTO run Ubuntu on low RAM computers"
date: 2005-09-05
forum: Outdated Tutorials &amp; Tips
---

### Post by lagagnon on 2005-09-05
HOWTO run Ubuntu on low RAM computers
===========================

Ubuntu requires 256MB RAM to perform happily out of the box. It will run with 128MB of RAM, but with continuous swapping of memory to disk. If you have less than 256MB of RAM you can significantly improve Ubuntu performance by doing the following, in order of importance:

1) use a different window manager. Metacity (the default) is very memory intensive. Try icewm or fluxbox instead. To do that first ensure you have "universe" sources enabled and then "apt-get install fluxbox icewm". When you next login at the login screen click the Session button and choose either icewm or fluxbox as your default window manager.

2) remove unnecessary services. By default Ubuntu loads quite a number of services, assuming you will be using it like a server. I would hesitate to guess that 90% of Ubuntu users would rarely, if ever use such services. They all consume RAM. The easiest way to do this is to install "Boot-up Manager": "apt-get install bum". The run "bum" and unclick the following services: rsync, atd, apmd, acpi-support, dbus-1, mdadm, fetchmail, postfix - but first read what these services do and decide if you really need them. They can be rebooted if removing them break anything on your system. Others listed can also be removed in some circumstances. You will need to do a bit of research beforehand.

3) use low-RAM-requirement applications. Here are some suggestions:
browser:		dillo or opera or lynx
email:			  sylpheed or mutt or pine
word processing:   abiword
newsgroups:	     pan or slrn
file manager:	       mc
editor:			   vim
terminal:		 aterm or rxvt
pdf reader:		xpdf
programming IDE:   motor

4) remove gdm (the Gnome display manager) using bum. This consumes significant RAM. Before doing this choose the window manager you are happy with, make it your default and then next time you boot up you will login in a text mode terminal and then type "startx".

5) remove unnecessary virtual terminals. By default Ubuntu provides you with 6 virtual terminals. These are the login terminals you can get to by typing Ctrl-Alt-F2, Ctrl-Alt-F3 etc. Normally you only need one spare terminal in case of emergencies. To disable the others and free up even more RAM "gedit /etc/inittab" and comment out the lines below as shown:

#3:23:respawn:/sbin/getty 38400 tty3
#4:23:respawn:/sbin/getty 38400 tty4
#5:23:respawn:/sbin/getty 38400 tty5
#6:23:respawn:/sbin/getty 38400 tty6

6) be continuously aware of all running processes and the RAM that your applications are consuming. You can see the processes with "ps aux". Check out the RSS column which is the total memory consumed by a process. You can also check your memory situation with "free". The important value is the second row number under the free column. This is the total available free memory including memory which has cached applications. 
 
7) free up video RAM (especially for those using onboard video chips which share memory). Edit the etc/X11/xorg.conf file and comment out the following lines:
# Load "record"
# Load "dbe"
# Load "dri"
# Load "glx"
# Load "xtrap"
# Load "type1"

The most important module you're not loading is dri which is for graphics acceleration. You will need to test this; it might not work with all graphics cards and will break graphics intense apps.

8) if you have 128MB of RAM or less Ubuntu is the wrong Linux distro for you (IMHO). I can highly recommend VectorLinux ([http://www.vectorlinux.com](http://www.vectorlinux.com)). This is an incredibly fast Linux distro which can run with 64MB of RAM - and using the tweaks above can be made to run with just 32MB of RAM!

Larry

---

### Post by xequence on 2005-09-05
Thats quite cool... IceWM Is really really fast. It took all of one second to load on my computer =O

THough it isnt REALLY old :P

Ive used fluxbox on DSL before. Not for long... I realised someone could/should make an ubuntu lite... It could use the stuff you suggested and be 100-300 MB.

---

### Post by ubuntme on 2005-09-05
Fvwm is a very lite weight WM.  The default config is very ugly, but with a bit of playing and downloading a few config files It can be made to look very nice.

---

### Post by benplaut on 2005-09-05
hold on a sec, you've got a few things that really shouldn't be done in that manner.

First of all, there is a big difference between Metacity and IceWM or Flux. Metacity comes with the assumption that you're using gnome, which is the real memory hog. Switching to IceWM or Flux is more than just a move to affect speed, it alters the entire way you work.

May i offer an alternative:

XFCE.

another option is openbox & perlpanel, both of which are lightweight and quite feature-rich.

It's probably not a good idea to take acpi off the boot, alot of people actually use it  :roll: 

If you decide to get rid of GDM (which i recommend), you can't just leave the user hanging with a CLI login. XDM is much more lightweight, and gets the job done.

For file manager, mc is probably going too far. do a google for "xfe", debs are available for both FOX toolkit and XFE itself (even the ones in breezy are really old). try it out- i have 768 RAM and i still prefer XFE  :)

---

### Post by Galoot on 2005-09-05
[QUOTE=lagagnon]"apt-get install bum".[/QUOTE]
Make sure the Breezy repositories are enabled. It's [not available in Hoary](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=bum).

---

### Post by lagagnon on 2005-09-06
[QUOTE=benplaut]hold on a sec, you've got a few things that really shouldn't be done in that manner.

First of all, there is a big difference between Metacity and IceWM or Flux. Metacity comes with the assumption that you're using gnome, which is the real memory hog. Switching to IceWM or Flux is more than just a move to affect speed, it alters the entire way you work.

May i offer an alternative:

XFCE.

another option is openbox & perlpanel, both of which are lightweight and quite feature-rich.
[/quote]
You confuse the issue. I suggested icewm or fluxbox for lowering memory useage, obviously they will affect the way people work. Then you go on to suggest openbox & perpanel - they are even more minimalist than icewm/fluxbox so will affect users even more!

> 
It's probably not a good idea to take acpi off the boot, alot of people actually use it  
Perhaps, yes, those who use laptops. It doesn't affect my workstation. 
> 
If you decide to get rid of GDM (which i recommend), you can't just leave the user hanging with a CLI login.
 Yes you can. This thread is about minimizing RAM useage.

> 
For file manager, mc is probably going too far. 
 
Hardly, it is still used by thousands of Linux users around the globe.

---

### Post by chinaski on 2006-01-03
thanks a lot **lagagnon**, your tips reduced RAM usage* from 260/280Mb to 140/160Mb on my machine :p 

*just logged in, no particular apps started, and I kept Gnome ;)

edit: I'd also like to specify that I've applied the changes above suggested (except for the windows manager) on a AMD64-Bit machine with AMD64 version of Ubuntu Breezy Badger 5.10

---

### Post by Neobuntu on 2006-10-01
I just had to add, think about mc(Midnight Commander) again ```
sudo aptitude install mc
``` for when X might be DOWN, one can just type ```
mc
```

This makes it easy to navigate and edit config files (like "xorg.conf".) Still, it's your preference. 

"mc", don't leave home (X) without it. :P

---

### Post by ELMIT on 2008-05-23
I tried to use another window manager, but my screen does not show the session button. In fact the login field is slightly too much right and too much to the bottom. It seems that the screen does not fit into the monitor.

I can get the session button, if I use an external monitor and not also have enabled the internal monitor.

How can I correct that?

---

