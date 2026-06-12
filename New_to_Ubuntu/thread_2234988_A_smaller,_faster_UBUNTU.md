---
title: "A smaller, faster UBUNTU"
date: 2014-07-18
forum: New to Ubuntu
---

### Post by schmitta on 2014-07-18
I am running 12.04 on a netbook. The netbook has 1GB of ram and runs at 1GHz. My disk light is on a lot which I think is because it is paging too much. Is there a smaller faster Ubuntu that I should be using? Will it have most of what regular Ubuntu has? Thank you for your help.

---

### Post by Bucky Ball on 2014-07-18
Surprised you have Unity and a full Ubuntu install running on that machine at all!

Yes, there are many alternatives. You can try Xubuntu or Lubuntu, both lightweight (Lubuntu lightest), but there are many others (though not officially supported here). 

I generally go for a minimal install and then just add the packages/apps I want/need. xfce4 for a desktop environment and a few other bits and pieces. This would be perfect solution for you if you're up to it.

Minimal Install page:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Basic example:
[http://www.maketecheasier.com/instal...on-old-laptop/](http://www.maketecheasier.com/instal...on-old-laptop/)

Older, but info still relevant while screenshots might be a bit different now:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

Just don't pick a machine profile when you get to that part of the install, at the end reboot and you will get to a login CLI and then a command prompt. Simply: sudo apt-get install what you like.

Failing this Lubuntu is possibly your best choice and yes, it uses exactly the same repositories as Ubuntu. You can add any of the same packages.

Be aware that only Ubuntu uses the Unity desktop environment and that is the major cause of your bloat. Xubuntu uses xfce4 and Lubuntu lxde. More old school. (Xubuntu is VERY easy to configure/customise, though.)

---

### Post by newb85 on 2014-07-18
The Lubuntu documentation says it needs 128 MB RAM, and recommends 256-512.
The Xubuntu documentation says it needs 512, and recommends 1 GB.
Oddly enough, I can't seem to find up-to-date system requirements for regular Ubuntu...

Also, depending on your internet connection and your take on cloud computing, you might look at Peppermint OS.  Conceptually, it's a cross between Chrome OS and Lubuntu.  What they did was start with the Ubuntu base (under-the-hood parts), add LXDE (which is the desktop environment used by Lubuntu), add their own artwork, and add their own Site-Specific Browser management tool that integrates well into the system.  So, you have the option to run traditionally installed applications or run things like Google Docs, etc.  The latest, Peppermint 5, is based on 14.04, and was released as LTS.

---

### Post by philinux on 2014-07-18
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Scroll down a bit for info on Unity.

---

### Post by kc1di on 2014-07-18
I agree with newb85, Xubuntu or Lubuntu or you may want to give LXLE a try also it can be found [ here.]("http://lxle.net/download/")

---

### Post by ajgreeny on 2014-07-18
Go for the minimal install CD and add either **lubuntu-core** package or **lxde-core** for the easiest way to get a very light OS.  This will give you the bare minimum to which you can add your chosen web-browser, office apps, music player, etc etc.

Doing it this way you will not have to worry about adding xorg, window-manager, display-manager, etc as they will all be dependencies of the DE.

---

### Post by 3rdalbum on 2014-07-18
> **schmitta said:**
> I am running 12.04 on a netbook. The netbook has 1GB of ram and runs at 1GHz. My disk light is on a lot which I think is because it is paging too much. Is there a smaller faster Ubuntu that I should be using? Will it have most of what regular Ubuntu has? Thank you for your help.

Even with only a gigabyte of RAM, this shouldn't be happening for ordinary internet use - I'm currently on a netbook with 1GB RAM.

You might want to install "iotop" and watch to see what is causing your disk to thrash like that. Then kill the program causing the problem.

---

### Post by schmitta on 2014-07-21
Thanks to all of you for your great ideas!

---

### Post by grahammechanical on 2014-07-21
What graphic adapter does that netbook have? How much of its own memory does it have? Does it use some of the system memory? That would reduce the amount of RAM available for the system.

I do not think that the size of the OS on the disk is a factor relating to the user's perception of a fast user interface. The key software components are the Desktop Environment and the User Interface. Add into the mix the desire of users to have fancy effects and many applications loaded at the same time and we end up with a UI with a perceptibly slow response.

Edit:

On 12.04 System Monitor would record a base memory usage of about 70% of 1GB RAM. Right now on Utopic Unicorn it is 40% of 1GB RAM. Even when I open Chromium to post this edit memory usage is at 58%.

You might get better results with a more modern version of Ubuntu, Such as Xubuntu 14.04 or Lubuntu 14.04. I have found that installing gnome-session-flashback on Ubuntu Utopic Unicorn and using the Gnome Flashback (Metacity) session will give a fast UI response. Try installing gnome-session-flashback on Ubuntu 14.04.

Regards.

Edit: And then there is Ubuuntu Mate. A new project to build the Mate destop environment/user interface on Ubuntu Utopic Unicorn. The intention is for it to become another flavour of Ubuntu. This project has only been going a few weeks. System Monitor is showing a base memory usage of 20% in this 1GB RAM machine of mine.

[http://ubuntu-mate.org/about/](http://ubuntu-mate.org/about/)

[http://sourceforge.net/projects/ubuntumate/](http://sourceforge.net/projects/ubuntumate/)

---

