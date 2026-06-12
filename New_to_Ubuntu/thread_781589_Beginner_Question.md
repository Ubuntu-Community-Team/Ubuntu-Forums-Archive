---
title: "Beginner Question"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by chadwit on 2008-05-04
Well I finally made the leap from M$ to Ubuntu, and I must say I am pleasantly surprised way beyond all of my expectations!!! The learning curve is relatively shallow for the basic setup, however if you're inexperienced with the Linux OS from a CLI and customization perspective, be prepared for some time consuming research and experimentation. But if you're an M$ guy that enjoys tinkering with PCs and considering making the leap, don't even think about it-just do it and don't look back....

That said, since I now have everything pretty much set up the way I want it, I'm somewhat overwhelmed and the number of packages/apps that are available. I use my PC primarily for basic PC stuff, i.e. burning disks, internet access, photo/video editing, etc.-nothing "specialized. So my question is, what are some of the additional "must have" apps that aren't included in the basic installation?

Also, when I need to run an app with sudo and I edit the properties of the icon on the panel in the command field, i.e. "/usr/bin/sudo nvidia-settings", the app doesn't open. Is there a way to open an app from the panel using sudo without opening a terminal?

thanks folks!

---

### Post by macaholic on 2008-05-04
Well one way to see these so-called "must-have" apps is to look in the add/remove program application. There you can sort by popularity in each category and see what people are using most. As far as the sudo stuff, you are doing it wrong. the command would be sudo THEN the file name, not in the file name, for your example it would be gksu /usr/bin/nvidia-settings, but it should just work with gksu nvidia-settings as well.

---

### Post by Barrucadu on 2008-05-04
To launch a graphical application, use gksudo. It launches a password prompt, and works just like regular sudo.

---

### Post by chadwit on 2008-05-04
I tried sudo /usr/bin/nvidia-settings & sudo nvidia-settings, but neither worked. When I run it from terminal, it asks me for a password. Could this be part of the problem? Is there a way to specify a password in the properties of a panel icon?

---

### Post by asgard_command on 2008-05-04
When I first started I found the beauty of all those packages was that I could just keep installing them to see how they worked and if I liked them. So long as you don't have a restrictive Internet connection of some kind.
I installed so much at first but I did use the previous suggestion of using add and remove and seeing what programs rated highest in each section.

---

### Post by chadwit on 2008-05-04
Sorry Barrucadu, posted b 4 I saw your response. That worked. Thanks!!!

---

### Post by tacutu on 2008-05-04
> **chadwit said:**
> I tried sudo /usr/bin/nvidia-settings & sudo nvidia-settings, but neither worked. When I run it from terminal, it asks me for a password. Could this be part of the problem? Is there a way to specify a password in the properties of a panel icon?

you use sudo from the command line.
however, in a gui environment you should use gksudo

---

### Post by tyroeternal on 2008-05-04
> So my question is, what are some of the additional "must have" apps that aren't included in the basic installation?

As far as great applications to install goes, [here]("http://ubuntuforums.org/showthread.php?p=3255930") is a great list of "must have" apps that was posted up on these forums a while back.

---

