---
title: "Partition of Hard Disks and Mp3 players"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by anuraggautam on 2008-06-06
1.Can any 1 tell me if i want to partition my hard drives after installation of Ubuntu Hardy , how can i do that ?

Please note that i have installed only Ubuntu in my 160 GB hard disk.

I want to partition in Window forms ,how can i do that ?

As in Windows XP there are many Softwares available to resize the parttions.howz possible in Ubuntu.

I am just trying to give feel of Windows in ubuntu.Like C: Drive,D: Drive....etc.


2. Tell me best Mp3 players for the songs in ubuntu.

I belive you got my Points 

Regards,
Anurag

---

### Post by anuraggautam on 2008-06-06
Hello Masters where r u ....please respond my query ASAP !

---

### Post by sayakb on 2008-06-06
1. Try GParted. It's best if you use it from the [Gparted LiveCD.]("http://gparted.sourceforge.net/livecd.php")
2. Exaile, Audacious, Banshee.

---

### Post by sayakb on 2008-06-06
> **anuraggautam said:**
> I am just trying to give feel of Windows in ubuntu.Like C: Drive,D: Drive....etc.

That is somewhat unnecessary. All you need is 3 partitions: /, /home and swap. The packages will always install on / (when you use package managers like synaptic, dpkg, aptitude etc) while your documents/pictures etc in your home folder will be in /home

---

### Post by rraj.be on 2008-06-06
You can work very well regarding partitioning in ubntu than in windows.

One good partitioning utility in ubuntu is gparted.

you can install gparted in your system by typing this in terminal.


```
sudo apt-get install gparted
```

try this link to get more help.

```
[gparted.sourceforge.net/]("gparted.sourceforge.net/")
```

```
[http://gparted.sourceforge.net/documentation.php]("http://gparted.sourceforge.net/documentation.php")
```



regarding Music player the default thing [Rhythum box] is well suited if yu install all codec's.

Then another go are


[They also suport video's]
1) vlc player.  sudo apt-get install vlc
2)xine 
3)smplayer      sudo apt-get install smplayer 
4)mplayer       sudo apt-get install mplayer


Further install all   gstreemer and audio codecs to get full support for all media formates.

Use synaptic package manager for these.

[Its available at   System-->Administration --> Synaptic pakage manager]

Its easy to install any thing through this.

try this one too to install w32 codecs


```
[http://medibuntu.org/]("http://medibuntu.org/")
```

---

