---
title: "Multimedia Ubuntu Workstation"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by TrakerJon on 2008-06-04
Install Ubuntu and update the OS (after check marking the boxes of all the available repositories in Software Sources)

sudo apt-get install ubuntu-restricted-extras

sudo apt-get install audacious xmms2 xmms2-plugin-all avifile-divx-plugin avifile-xvid-plugin xine-plugin xvid4conf kaffeine amarok

sudo apt-get install wine

Add: 

deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) stable main 

into the Third Party Software section in Software Sources, Close and don't Reload

In a terminal session type:

sudo apt-get update 

after the key error... 

sudo apt-get install debian-multimedia-keyring

then again

sudo apt-get update

Install updates that may appear then...

sudo apt-get install acidrip

sudo apt-get install acroread realplayer

sudo apt-get install libdvdcss2

sudo apt-get install gtk-gnutella esperanza

Enjoy!

---

### Post by DrBrown on 2008-06-04
Is this how to install Ubuntu tweaked for a multimedia center?

---

### Post by roaldz on 2008-06-04
> **DrBrown said:**
> Is this how to install Ubuntu tweaked for a multimedia center?

No, it´s just some commands to install some media players, codecs and other stuff. It doesn´t magically create a multi-media workstation more than it already is:)

---

### Post by DrBrown on 2008-06-04
after a absolutely flawless recent install of Ubuntu 8.04, I await its next magically performance.

Re codecs etc. my media has come accross with no issues I was prompted to install a few codecs which was all done automatically and with again no hiccups...

Ubuntu = user friendly / "magic"

---

### Post by TrakerJon on 2008-06-04
Just a fast and easy way to get your Ubuntu workstation hooked up with audio and video.

---

### Post by DrBrown on 2008-06-04
after a absolutely flawless recent install of Ubuntu 8.04, I await its next magically performance.

Re codecs etc. my media has come accross with no issues I was prompted to install a few codecs which was all done automatically and with again no hiccups...

Ubuntu = user friendly / "magic"

So this is like a one stop sudo shop for potential media requriements?



tsk tsk Double posting

---

### Post by TrakerJon on 2008-06-04
It was recommended by others  to use the following commands for installing the latest Java JRE 1.0.6_06 with Ubuntu but I had a problem with the java browser plugin using the latest Firefox so you may want to try my solution.

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts


I download the latest <jre version>.rpm.bin file from Java.com ...then extract the .rpm file after making it executable.

Install alien...

sudo apt-get install alien

and then use...

sudo alien --scripts <jre file name>.rpm to convert it to <file name>.deb and then install the .deb file.

Then I link to the java plugin from the /usr/lib/Firefox 3.0/plugins folder...

sudo ln -s /usr/java/jre1.6.0_06/plugin/i386/ns7/libjavaplugin_oji.so ./libjavaplugin_oji.so

---

