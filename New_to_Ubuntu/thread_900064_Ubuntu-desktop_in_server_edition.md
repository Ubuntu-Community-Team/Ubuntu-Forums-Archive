---
title: "Ubuntu-desktop in server edition?"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2008-08-25
If I install the package ubuntu-desktop in the server edition (I'm still learning about this server stuff. . .  This is on a virtual machine BTW)will it:

-Give me a GUI

-Mess up any other components

Thanks in advance!

BTW I know that most of the configuration will have to be done via a command line anyway, I would just like a gui starting out.

---

### Post by tuxxy on 2008-08-25
Yes that should install GNOME

---

### Post by pi.boy.travis on 2008-08-25
Sweet, thanks!

BTW, do you know of any good remote/web based configuration options?  Just curious. . .

---

### Post by 67comet on 2008-08-25
For remote admin of a server I suggest Webmin. I would head to Google, hit up Webmin and download the .deb package. Webmin in the repositories (installed from apt-get/Synaptics doesn't always give you the newest version).

Webmin is accessible via the www or local IP address followed by port 10000 by default. [http://localhost:10000](http://localhost:10000) if you are on the same machine it was installed on. Good app, and I usually use it when I initially set up a server (just faster then cli everything with out a script).

Hope that'll help.

---

### Post by pi.boy.travis on 2008-08-25
Thanks, I'll chack out Webmin.  My goal is to set up a file and print server.  I have also been doing some research about setting up my own proxy server.

---

### Post by Oldsoldier2003 on 2008-08-25
> **pi.boy.travis said:**
> Sweet, thanks!

BTW, do you know of any good remote/web based configuration options?  Just curious. . .

Take a look at the wiki: [uhelp]community/ServerGUI[/uhelp] for reasons why not to use the server gui, and lightweight options should you decide to use the gui.

---

### Post by pi.boy.travis on 2008-08-25
WOW. . .  Perhaps eBox or Webmin will eliminate the need for a GUI. . .

Thanks for that!

Edit:eBox is looking like exactly what I was looking for!  Thanks to all who posted!

---

### Post by 67comet on 2008-08-25
I totally forgot about eBox. That is a very handy application too. If you want to try Webmin, here is a pretty easy install:
[http://www.ubuntugeek.com/webmin-installation-and-configuration-in-ubuntu-linux.html](http://www.ubuntugeek.com/webmin-installation-and-configuration-in-ubuntu-linux.html)

The current version of Webmin is much newer than in the tutorial, but you'll see that if you want to try it and head to the webmin site.

I'm going to give eBox a try too. That looks pretty strait forward. It's got modules and everything.

Cheers,
Justin

---

### Post by JKHinton CPBD on 2008-08-25
hello pi-boy-travis,

Am I understanding your post correctly?  You had the server edition 8.04 installed and then loaded the desktop edition on top of the server?  That is exactly what I am thinking of doing.  I am trying to build a web server , but am new to Ubuntu so I believe the GUI of the desktop will help me learn to use Ubuntu. Did you run into any complications with your server edition after the desktop installation? What do you mean by a virtual machine?

Thank you

---

### Post by WRDN on 2008-08-25
I would not install the ubuntu-desktop package's on a server, as it includes many applications you will not need. Instead, you may want to install a lighweight window manager such as Fluxbox.

---

