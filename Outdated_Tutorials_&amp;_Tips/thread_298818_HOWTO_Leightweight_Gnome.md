---
title: "HOWTO: Leightweight Gnome"
date: 2006-11-13
forum: Outdated Tutorials &amp; Tips
---

### Post by veli on 2006-11-13
This is a supplement to the Gnome - (semi)minimalistic topic and I decided to post my experience under the HOWTO section. 
Most of the stuff has been discussed many times, and my initial idea was to collect everything in one place. 

Feel free to add and correct what I've written here.
 
This is for guys who like Gnome and prefer it over XFCE or other WM. It&#8217;ll give you almost the default Ubuntu desktop without the applications, few services, and no language packs. It contains roughly 700 packages. 
  
So, I&#8217;ve started from Dapper alternate CD with the server install option.
After that edit the sources.list file, &#8216;cause you&#8217;ll need the universe repo:
Uncomment every line starting with # 
$ sudo nano /etc/apt/sources.list
Save the file: ctrl+O, press enter and quit  nano by ctrl+X

$ sudo apt-get update

In addition to gnome-core and xorg-core you&#8217;ll need to get a few more packages that we&#8217;ll provide you almost a complete Gnome desktop environment with few apps just to administer the system.

$ sudo apt-get install x-window-system-core gnome-core gdm gnome-media gnome-system-monitor gnome-system-tools gnome-volume-manager gnome-utils gnome-app-install synaptic firefox  

Reboot and you&#8217;ll get the Gnome, but very lightweight and snappy. 

I&#8217;ve added some programs to make my life easier: 

$ sudo apt-get install evince file-roller gdebi alacarte totem sound-juicer

Beyond this set-up you could add whatever program you want (including multimedia codecs, Java, Flash). I&#8217;ve also installed all tools for kernel compiling, dev tools, make, etc, making my Ubuntu having 800 packages, and running at 70 MB RAM when idle after a fresh reboot (see the screenshot). With time, you could expect some increase in memory consumption; usually it comes from xorg and nautilus.


When you set up everything, it&#8217;s time for optimization.
This is what I&#8217;ve done:

1.	Install kernel-686. After a while I compiled my own from kernel.org.
2.	Tweak the file system-I decided to use reiserfs, and did data_writeback, and noatime tricks. 
3.	Clean up all unnecessary files using Synaptic.
4.	Enable DMA (it is I think) and other hdparm stuff for getting the best from your drives.
5.	Remove unneeded services from booting.
6.	Change swappiness from 60 to 15.
7.	Make CFQ default IO scheduler. 
8.	XML optimization.
9.	Prelink
10.	Preload

I can&#8217;t remember for more, if someone knows please add it here. The links to the 10 optimizations can be found in this forum or Google.
Reboot and you&#8217;ll enjoy a very clean and neat Ubuntu desktop.

Hope this helps out other novices like me to optimize their systems for best performance.
My comp is rather old IBM PIII desktop, 660 MHZ CPU, 256 RAM, 20 GB HDD. My boot time is 1 minute and the system eats around 70 MB when idle. Once it got down to 58 MB, I don&#8217;t know why, but I never got that again.

Opera starts for 4 sec the first time, 2-3 sec. the next ones (in Windows 2000 I got the same-I heavily tweaked Win2000 too). Nautilus starts for 1 sec. I have Cross Over Office Pro 5 for running Origin, first time it starts for 10 sec, the second one&#8211; 5 sec.

Happy ubuntuing, :-D

Some of the tweaks can be found below:

many tweaks:
[http://www.ubuntuforums.org/showthre...ht=performance](http://www.ubuntuforums.org/showthre...ht=performance)

Be careful with the tweak about LOCALE PURGE. Your system might start behaving strangely and I wouldn't recommended it on a Debian system.  

CFQ:
[http://ubuntuforums.org/showthread.php?t=119220](http://ubuntuforums.org/showthread.php?t=119220)

Faster gnome menus:
[http://www.ubuntuforums.org/showthre...t=faster+Gnome](http://www.ubuntuforums.org/showthre...t=faster+Gnome)

For ext3 file system:
[http://forums.gentoo.org/viewtopic-t...-dirindex.html](http://forums.gentoo.org/viewtopic-t...-dirindex.html)

Swappiness:
[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

---

### Post by yopnono on 2006-11-13
Links fixed I see. :)

---

### Post by xyz on 2006-12-04
[Enable Prelink]("http://ubuntuforums.org/showthread.php?t=1971")
and also:
[Here]("http://ubuntuforums.org/showthread.php?t=189192")

---

### Post by tturrisi on 2006-12-04
Good guide!
I do almost the same thing but I use the Etch net-install business card cd.  Boot using the command:
expertgui
You will get to a screen where you can select either Stable, Testing or Unstable and another screen where you can select the kernel you want.
Just yesterday I reinstalled my laptop w/ Etch again (instead of installing 450 MB of upgrades):

---

### Post by bodhi.zazen on 2006-12-06
Nice How-to



This thread has been added to the UDSF wiki.



[LightweightGnome](http://doc.gwos.org/index.php/LightweightGnome)

---

### Post by Opally on 2006-12-07
xwindow-system-core should be x-window-system-core, I believe. I was able to apt-get x-window-system-core but not xwindow-system-core.

It was x-window-system-core in Veli's post. I've fixed it in the Wiki.

And, by the way, very useful thread, thanks so much!

-Opally (newbie)

---

### Post by veli on 2006-12-07
thanks guys, it's an honor my experience being officially published. I'm glad helping Ubuntu and open source idea.

Anyway, I corrected some mistakes in the WIKI, for instance I'd written: "Clean up all necessary files in Synaptic" It should be "unnecessary". Sorry about that.

---

### Post by funkenstein on 2007-01-01
umm... didn't work for me on 64bit clean install... just had gdm, but logging in gave me a brown screen and an xterm. 

fixed by installing a cli system from the edgy alternate cd and then:
```
sudo aptitude install xorg gdm
```

Took me 3 days to figure that one out ](*,)

/edit
I updated the USDF guide with that, and the kernel-686 is depricated in Edgy...

---

### Post by techno-wiz on 2008-03-10
After following this guide and rebooting it says human theme could not load. Also seems I don't have a window manager. Windows open with no bar at the top to move them around or close them. So close to having the gui I want!

---

### Post by techno-wiz on 2008-03-10
Ok I figured out that metacity was actually installed. Started it and got my windows working right. But after reboot had the same issue. Also clicking on the little green man so I can logout/shutdown/restart/etc did nothing. Still comes up with a message at the login screen saying it can't open the human theme under /usr/share/...

Just going to install the ubuntu-desktop and be done with it. Wish this worked though. Just seems kinda buggy.

---

### Post by Nick5768 on 2008-03-11
> **techno-wiz said:**
> Ok I figured out that metacity was actually installed. Started it and got my windows working right. But after reboot had the same issue. Also clicking on the little green man so I can logout/shutdown/restart/etc did nothing. Still comes up with a message at the login screen saying it can't open the human theme under /usr/share/...

Just going to install the ubuntu-desktop and be done with it. Wish this worked though. Just seems kinda buggy.

sudo apt-get install ubuntu-artwork

Google is your friend.

---

### Post by phreaky- on 2008-05-14
Could someone update this thread? With info how I get this ligtweight installation working on Ubuntu 7.10 or 8.04.

On Ubuntu 7.10 I have no borders around my windows :S I figured out that the problem lies into the package metacity which doesn't start automaticly. But how to solve do I need to install a missing package or so.

---

### Post by Alucard-sama on 2008-05-15
One of the links is broken...

---

