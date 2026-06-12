---
title: "HOW TO : Speedtouch 330 USB on Ubuntu 8.04 Hardy Heron"
date: 2008-05-17
forum: Outdated Tutorials &amp; Tips
---

### Post by vladi11 on 2008-05-17
For connecting to the Internet using a Speedtouch 330 Usb modem, we will use [[COLOR="DarkOrange"]usb adsl manager[/COLOR]]("http://www.squeezedonkey.com/wiki/linux/index.php?title=Main_Page")

This tutorial is inspired by this [[COLOR="DarkOrange"]post[/COLOR]]("http://ubuntuforums.org/showpost.php?p=4813601&postcount=114").
Homepage for usb adsl manager [[COLOR="DarkOrange"]here[/COLOR]]("http://www.squeezedonkey.com/wiki/linux/index.php?title=Main_Page") 

In order to make the usb adsl manager to work on a fresh installed Hardy, you have to install some .deb packages.
Otherwise it won't work. 

The packages should be saved on a removable media (cd, dvd or memory flash) before you boot in Ubuntu 8.04 (remember: at this moment, you have no internet).
After you boot up in Ubuntu, install all of them in the order they are listed bellow.

Just pick the mirror closest to your location.

**Note**: choose the type you need : **32 bit or 64 bit** (depending on your operating system).

Install them in the order they are listed:

1. **32 bit / 64 bit** [[COLOR="DarkOrange"]libgda3-common[/COLOR]]("http://packages.ubuntu.com/hardy/all/libgda3-common/download") 

2. **32 bit** [[COLOR="DarkOrange"]libgda3-3[/COLOR]]("http://packages.ubuntu.com/hardy/i386/libgda3-3/download") or **64 bit** [[COLOR="DarkOrange"]libgda3-3[/COLOR]]("http://packages.ubuntu.com/hardy/amd64/libgda3-3/download")

3. **32 bit / 64 bit** [[COLOR="DarkOrange"]libgdl-1-common[/COLOR]]("http://packages.ubuntu.com/hardy/all/libgdl-1-common/download")

4. **32 bit**  [[COLOR="DarkOrange"]libgdl-1-0[/COLOR]]("http://packages.ubuntu.com/hardy/i386/libgdl-1-0/download")   or **64 bit** [[COLOR="DarkOrange"]libgdl-1-0[/COLOR]]("http://packages.ubuntu.com/hardy/amd64/libgdl-1-0/download")  

5. **32 bit** [[COLOR="DarkOrange"]libgdl-gnome-1-0[/COLOR]]("http://packages.ubuntu.com/hardy/i386/libgdl-gnome-1-0/download")  or **64 bit** [[COLOR="DarkOrange"]libgdl-gnome-1-0[/COLOR]]("http://packages.ubuntu.com/hardy/amd64/libgdl-gnome-1-0/download")

6. **32 bit** [[COLOR="DarkOrange"]python-gnome2-extras[/COLOR]]("http://packages.ubuntu.com/hardy/i386/python-gnome2-extras/download")  or **64 bit** [[COLOR="DarkOrange"]python-gnome2-extras[/COLOR]]("http://packages.ubuntu.com/hardy/amd64/python-gnome2-extras/download")

After you install all those packages, install **32 bit** [[COLOR="DarkOrange"]usb adsl manager]("http://www.squeezedonkey.com/svn/linux/trunk/releases/ubuntu/32-bit%20i386/usbadslmodemmanager_0.5.8_i386.deb")[/COLOR] or **64 bit** [[COLOR="DarkOrange"]usb adsl manager[/COLOR]]("http://www.squeezedonkey.com/svn/linux/trunk/releases/ubuntu/64-bit%20i686/usbadslmodemmanager_0.5.8-64bit_all.deb")

After installation, to acces the usb adsl manager, go to 
Applications...Internet...Usb adsl manager
Here you type the settings of your connection: username, password, VP and VC.

[[IMG]http://img88.imageshack.us/img88/130/usbadslmanagerjf1.th.jpg[/IMG]](http://img88.imageshack.us/my.php?image=usbadslmanagerjf1.jpg)

That's it. Not that hard, hah ? Have fun online. :)

---

### Post by ezze66 on 2008-05-18
I can't seem to get this to work.

Please see this post where I state the problem: [http://ubuntuforums.org/showthread.php?goto=newpost&t=585647](http://ubuntuforums.org/showthread.php?goto=newpost&t=585647)

please help. thanks

---

### Post by vladi11 on 2008-05-19
I'm afraid I can not help you.
I'm a newbie in Linux.
I presented the method I used with my modem.
Maybe someone who understand your log can help you.
Sorry. :(

---

### Post by shekhar.sathaye on 2009-06-18
How to install a cable modem used for dial up broadband connection? I am using Ubuntu 9.04.

---

