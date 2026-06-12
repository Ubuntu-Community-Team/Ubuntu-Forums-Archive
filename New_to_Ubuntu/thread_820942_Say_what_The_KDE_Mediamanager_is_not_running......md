---
title: "Say what? The KDE Mediamanager is not running....."
date: 2008-06-06
forum: New to Ubuntu
---

### Post by stevezygote on 2008-06-06
I was just trying to access my HP Windoze XP SP3 partition from my Kubuntu 8.04 to transfer a Windoze version of a program I discovered that had both a Linux version and a Windoze version when...to my surprise...I got "The KDE MediaManager is not running" and all the icons under the "Storage" folder were gone. I fixed it by rebooting. When it came back they were there. But I've been understanding that you don't have to take a Windoze approach to things in Linux, that you can just reinitialize a portion of the system that's not working, or needs to be reinitialized. Can someone please explain? Thanks!

---

### Post by kioftes on 2008-07-10
Same problem here. It has happened to me some times with no apparent reason in gutsy and hardy. You don't have to resart the system, just the x server with ctrl+alt+backspace, but there's definitely an easier way which i am not aware of.

---

### Post by kioftes on 2008-07-10
Found it! Just open a terminal and run

kded

which is exactly what is not running. It seems that the problem is some kind of misconfiguration. If it persists you may want to try

dpkg-reconfigure kdelibs
dpkg-reconfigure kdebase

and (after backing up your xorg.conf) 

sudo dpkg-reconfigure -phigh xserver-xorg

Good luck!

---

### Post by tptbz on 2008-07-11
I have this problem, too.  But when I ran kded I got:
FATAL: DCOP communication problem!
Aborted

So, I'm not sure at the moment what I'm going to do to fix this.

updated: my fault.  I ran kded as root.  I ran it as a regular user and it's fine.

---

