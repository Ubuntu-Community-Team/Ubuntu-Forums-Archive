---
title: "Switching distros"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by rich97 on 2008-10-24
Ok fisrt off your looking at a relative noob here :P so be gentle.

I have used Linux Ditros in the past but they are less than user friendly, I can use the command line a bit (I've installed 64 bit flash etc but I dont know most of the commands by heart). I have been told that Ubantu is one of the more friendly distros and It looks pretty cool what you can do with it.

At the moment I have Fedora 9 (64 bit) on a dual boot with Vista(32 bit...yes it was cheap) on my laptop. Thing is Fedora sucks in terms of usability and looks like a pigs ****, from what I've seen Ubantu looks a bit sleeker and of cource it has the linux core I'm looking for. As Vista takes up 1/2 of my 2 gig ram, which is rediculous.

What I really wan to know is weather it is hard to switch distros and how should I do this? Just delete the partition with Fedora on and reinstall? Or should I just Install over the top of it like i would with windows? Will Ubantu write over the MBR with it's own version of GRUB? Finally, what GUI does Ubantu use KDE or GNOME and can you swap easily if you dont like one?

Thanks, Rich.

---

### Post by kpkeerthi on 2008-10-24
Just install Ubuntu over the partition(s) Fedora is using now. 
As for the looks, it can be changed. Any distro can be made to look like any other.
[http://www.gnome-look.org/](http://www.gnome-look.org/)

---

### Post by phr0ze on 2008-10-24
I'd delete the partition then install.
I have heard Fedora had the better UI, but I've never looked.
Ubuntu is gnome, but you can install Kubuntu or just add kde later. Its easy.
Ubuntu should replace the MBR.

---

### Post by mariuskl on 2008-10-24
Agree with kpkeerthi. It is the simple way.

---

### Post by Keen101 on 2008-10-24
I've never installed over another distro, so i don't know if it will cause any problems or not. If it were me i'd just wipe the partitions with the Gparted Live-CD [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) and install ubuntu into the free space.

> What I really wan to know is weather it is hard to switch distros and how should I do this? Just delete the partition with Fedora on and reinstall? Or should I just Install over the top of it like i would with windows? Will Ubantu write over the MBR with it's own version of GRUB? Finally, what GUI does Ubantu use KDE or GNOME and can you swap easily if you dont like one? yeah ubuntu will write it's own GRUB. Yeah you can use the following code to install the KDE desktop for ubuntu:

```
sudo apt-get install kubuntu-desktop
```

---

### Post by rich97 on 2008-10-24
Thanks guys,

Will try it sometime over the weekend and thanks for the live partion CD thing I didn't even know anything like that existed.

See you soon, your more than likly to see me with lots of "Help!" threads being the newbie I am :)

---

