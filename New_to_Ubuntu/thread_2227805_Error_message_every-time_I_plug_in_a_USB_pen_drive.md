---
title: "Error message every-time I plug in a USB pen drive"
date: 2014-06-04
forum: New to Ubuntu
---

### Post by terrykiwi83 on 2014-06-04
Hey all,

Been having this problem for a while now (well since installing 14.04). Every-time I plug in a USB pen drive, I am presented with an error message, as well as two windows opening showing the contents of said pen-drive.

I don't really know where to start with troubleshooting so any advice would be appreciated.

Thanks, Terry

System: Ubuntu 14.04 x64
Pen drives: A variety of pen drives, in different sizes, and different filesystems (ntfs, fat32, ext4). 

Below is a screenshot of the error.
[ATTACH=CONFIG]253713[/ATTACH]

---

### Post by sudodus on 2014-06-04
It seems to me that you have two systems that want to mount the pendrive and open a file browser with it. And the second one cannot mount it because it is already mounted.

Those two browser windows look different. Are you running more than one file browser, for example Nautilus and Thunar? Have you installed more than one desktop environment for example standard Ubuntu with Unity and Xubuntu Desktop?

---

### Post by terrykiwi83 on 2014-06-04
Hi thanks for the message. I have installed Unity, Gnome, Mate (and am running Unity atm). Do you think I need to remove the other DEs?

---

### Post by sudodus on 2014-06-04
This could be the reason why you have this problem. But if you can live with it, and you want several desktop environments, fine :-)

It can be hard to remove completely the 'other' desktop environments. It is much easier to reinstall what you want unless you have a lot of tweaks. Anyway, backup your system or at least your personal files before you start removing things.

---

