---
title: "HOWTO: Fast user switch with working sound"
date: 2005-05-15
forum: Outdated Tutorials &amp; Tips
---

### Post by g14 on 2005-05-15
*fast-user-switch-applet* (fusa) is this great little panel applet that allows you to quickly switch between users on a gnome desktop.

[IMG]http://ignore-your.tv/images/stories/fusa/fusa-menu-icon.png[/IMG] or [IMG]http://ignore-your.tv/images/stories/fusa/fusa-menu-name.png[/IMG]

1.) Download the deb file:
**wget [http://ankur.ath.cx/ubuntu/fast-user-switch-applet/fast-user-switch-applet_0.2.2-0ubuntu1_i386.deb](http://ankur.ath.cx/ubuntu/fast-user-switch-applet/fast-user-switch-applet_0.2.2-0ubuntu1_i386.deb)**

2.) Install it:
**[FONT=System]sudo dpkg -i fast-user-switch-applet_0.2.2-0ubuntu1_i386.deb[/FONT]**

3.) Edit /etc/esound/esd.conf
**[FONT=System]sudo gedit /etc/esound/esd.conf[/FONT]**

change the line reading:
[FONT=System]**default_options=**[/FONT]

to:
**[FONT=System]default_options=-unix -promiscuous[/FONT]**

4.) Right click anywhere on one of your panels and select "Add to Panel". Scroll
down and select "User Switcher" and click add.

NOTE: You might want to change it from the default (Users) to displaying a pretty
little user icon. Right click on it and select "Preferences". Click the user icon and
then ok.

I use this on a linux machine I set up for my parents and they have no problems
with it. I hope this helps someone other than myself!

[Fast User Switch Applet Homepage](http://ignore-your.tv/fusa/)

---

### Post by rwabel on 2005-05-15
[QUOTE=g14]*fast-user-switch-applet* (fusa) is this great little panel applet that allows you to quickly switch between users on a gnome desktop.

[img]http://ignore-your.tv/images/stories/fusa/fusa-menu-icon.png[/img] or [img]http://ignore-your.tv/images/stories/fusa/fusa-menu-name.png[/img]

1.) Download the deb file:
**wget [http://ankur.ath.cx/ubuntu/fast-user-switch-applet/fast-user-switch-applet_0.2.2-0ubuntu1_i386.deb]("http://ankur.ath.cx/ubuntu/fast-user-switch-applet/fast-user-switch-applet_0.2.2-0ubuntu1_i386.deb")**

2.) Install it:
**[font=System]sudo dpkg -i fast-user-switch-applet_0.2.2-0ubuntu1_i386.deb[/font]**

3.) Edit /etc/esound/esd.conf
**[font=System]sudo gedit /etc/esound/esd.conf[/font]**

change the line reading:
[font=System]**default_options=**[/font]

to:
**[font=System]default_options=-unix -promiscuous[/font]**

4.) Right click anywhere on one of your panels and select "Add to Panel". Scroll
down and select "User Switcher" and click add.

NOTE: You might want to change it from the default (Users) to displaying a pretty
little user icon. Right click on it and select "Preferences". Click the user icon and
then ok.

I use this on a linux machine I set up for my parents and they have no problems
with it. I hope this helps someone other than myself!

[Fast User Switch Applet Homepage]("http://ignore-your.tv/fusa/")[/QUOTE]
 I get a dependency problem with libc6. are you under breezy?
 ```

rwabel@RALPH:~/Desktop $ sudo dpkg -i fast-user-switch-applet_0.2.2-0ubuntu1_i386.deb
Selecting previously deselected package fast-user-switch-applet.
(Reading database ... 313772 files and directories currently installed.)
Unpacking fast-user-switch-applet (from fast-user-switch-applet_0.2.2-0ubuntu1_i386.deb) ...
dpkg: dependency problems prevent configuration of fast-user-switch-applet:
 fast-user-switch-applet depends on libc6 (>= 2.3.4-1); however:
  Version of libc6 on system is 2.3.2.ds1-21.
dpkg: error processing fast-user-switch-applet (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fast-user-switch-applet

``` 

I'm going to try it from the source. thanks for pointing out this app

---

### Post by AlvaroBF on 2005-05-15
I've got the same error
alvaro@ubuntu:~ $ sudo dpkg -i fast-user-switch-applet_0.2.2-0ubuntu1_i386.deb
Password:
Seleccionando el paquete fast-user-switch-applet previamente no seleccionado.
(Leyendo la base de datos ...
71585 ficheros y directorios instalados actualmente.)
Desempaquetando fast-user-switch-applet (de fast-user-switch-applet_0.2.2-0ubuntu1_i386.deb) ...
dpkg: problemas de dependencias impiden la configuración de fast-user-switch-applet:
 fast-user-switch-applet depende de libc6 (>= 2.3.4-1); sin embargo:
  Versión de libc6  en el sistema es 2.3.2.ds1-20ubuntu13.
dpkg: error al procesar fast-user-switch-applet (--install):
 problemas de dependencias - se deja sin configurar
Se encontraron errores al procesar:
 fast-user-switch-applet
alvaro@ubuntu:~ $

EDIT: >_< It works...  strange

---

### Post by rwabel on 2005-05-15
you are right, it's working! But you have now a broken package on your system :-)

---

### Post by bsdpro on 2005-05-15
i just did a apt-get update and tried to install it -- no go.

rj@truffles:~/downloads$ sudo dpkg -i fast-user-switch-applet_0.2.2-0ubuntu1_i386.deb
Selecting previously deselected package fast-user-switch-applet.
(Reading database ... 78622 files and directories currently installed.)
Unpacking fast-user-switch-applet (from fast-user-switch-applet_0.2.2-0ubuntu1_i386.deb) ...
dpkg: dependency problems prevent configuration of fast-user-switch-applet:
 fast-user-switch-applet depends on libc6 (>= 2.3.4-1); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu13.
dpkg: error processing fast-user-switch-applet (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fast-user-switch-applet



[QUOTE=AlvaroBF]I've got the same error
alvaro@ubuntu:~ $ sudo dpkg -i fast-user-switch-applet_0.2.2-0ubuntu1_i386.deb
Password:
Seleccionando el paquete fast-user-switch-applet previamente no seleccionado.
(Leyendo la base de datos ...
71585 ficheros y directorios instalados actualmente.)
Desempaquetando fast-user-switch-applet (de fast-user-switch-applet_0.2.2-0ubuntu1_i386.deb) ...
dpkg: problemas de dependencias impiden la configuración de fast-user-switch-applet:
 fast-user-switch-applet depende de libc6 (>= 2.3.4-1); sin embargo:
  Versión de libc6  en el sistema es 2.3.2.ds1-20ubuntu13.
dpkg: error al procesar fast-user-switch-applet (--install):
 problemas de dependencias - se deja sin configurar
Se encontraron errores al procesar:
 fast-user-switch-applet
alvaro@ubuntu:~ $

EDIT: >_< It works...  strange[/QUOTE]

---

### Post by rwabel on 2005-05-15
I compiled from source and it works fine. I would prefer a deb files, but as long as it works I'm fine with it

---

### Post by g14 on 2005-05-17
Sorry, the deb was pointed out to me right before I wrote the tutorial. I compiled this from source. Thanks for pointing out the problems though, I'll contact the maintainer before this gets uploaded to Universe.

---

### Post by Poul on 2005-05-22
although it said that there is a dependency problem it works - unfortunately synaptic reports it as broken.
How do i change icons on the side of the usernames and how do i get it to look as  on the left pic ??

---

### Post by McQuaid on 2005-05-24
Hey thanks for this tip, I'm really glad to see this.  

I tried to find more info about the options:

default_options=-unix -promiscuous

the man says about promiscuous
 -promiscuous  start unlocked and owned (disable authenticaton) NOT RECOMMENDED

I couldn't find much info other than that other than there would be security issues.  
Does anyone know anymore about this?  Also would just the promiscuous alone be required for this or does one need -unix as well?  Just curious how it all works.

Also my other problem in user switching is xscreensaver.  Right now when I do a user switch, the other users login everntually times out and xscreensaver kicks in.  Well, this is how it worked the last time I tried it in debian sid, haven't tried it in ubuntu yet.  And on top of that, the xsreensaver option to lock the screen should have an option to user switch instead of just the password for that user.  That would pretty much give us a fully functional multiuser environment with multiple users logged into X.

---

### Post by JamesCape on 2005-05-27
Regarding ESD, the "-unix" says "only use local-only sockets", and then "-promiscuous" means (when in concert with -unix) "allow other users logged into this machine to play sounds". It's a security issue because it allows other users to send sounds through esd to your soundcard -- or potentially crash esd if they found a bug.

So far as a face icon, the "gdmphotosetup" app will change it, (it's also in System->Preferences somewhere, IIRC) or you could simply rename a copy of the image to "/home/<your-username>/.face". Either way, run "killall fast-user-switch-applet" to force it to reload.

---

### Post by misGnomer on 2005-06-02
Could this be integrated to the screensaver login screen? I'm usually the sole user of my system, but I have accounts for family and guests who should be able to wander by the machine and login without me having to leave the screen unlocked.

PS. Thx JamesCape for this most useful applet for a multi-user OS!  :-)

---

### Post by vaskark on 2005-06-02
[font=Trebuchet MS]I compiled and installed this applet myself and it works great. I made the change to my sound conf file but I get no sound. I check my system monitor in the new session and find that esd isn't running, so I start it from the command line and get this:[/font]

[font=System][font=Trebuchet MS] > esd: Failed to fix owner of /tmp/.esd
Try -trust to force esd to start.
esd: Esound sound daemon unable to create unix domain socket:
/tmp/.esd/socket
The socket is not accessible by esd.
Exiting ... [/font]

[font=Trebuchet MS]Can anyone help?[/font]
[/font]

---

### Post by Sionide on 2005-06-05
Works great for me, I love it.

Apart from Synaptic now reporting the broken package. How do you fix it?

---

