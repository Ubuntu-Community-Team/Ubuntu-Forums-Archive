---
title: "gnome shell - broken"
date: 2011-09-09
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by craigdabbs on 2011-09-09
Hi,

i have recently installed a fresh copy of beta 1 and done all the updates.  I have installed gnome shell also, but when i try and log in using gnome instead of unity all i am presented with is the nautilus menu bar at the top.

Is anyone having a similar issue?

---

### Post by lobo_tuerto on 2011-09-09
Yup, just happened to me, had to install Unity again, read this thread, it might help you out: [http://ubuntuforums.org/showthread.php?t=1841428](http://ubuntuforums.org/showthread.php?t=1841428)

Also read this:[http://ubuntuforums.org/showthread.php?t=1751299](http://ubuntuforums.org/showthread.php?t=1751299)

---

### Post by Benjamin_Lebsanft on 2011-09-09
Same here, was on ricotz ppa, got the problem, removed the ppa and went back to ubuntu packages only and until now it was fine. Will read the linked threads. Thanks!

---

### Post by Benjamin_Lebsanft on 2011-09-09
Reinstalling unity didn't do the trick for me.

---

### Post by jppr on 2011-09-09
[https://launchpad.net/ubuntu/oneiric/+source/gnome-shell/3.1.90.1-0ubuntu3](https://launchpad.net/ubuntu/oneiric/+source/gnome-shell/3.1.90.1-0ubuntu3)
New version is coming :popcorn:

---

### Post by craigdabbs on 2011-09-09
wow thanks for the replies guys, not used to such a active forum :p

---

### Post by Benjamin_Lebsanft on 2011-09-09
The package changelog doesn't mention any bugfix though

---

### Post by sgage on 2011-09-09
> **craigdabbs said:**
> wow thanks for the replies guys, not used to such a active forum :p

This is a good one, alright!

---

### Post by mdhollis on 2011-09-09
I installed a fresh copy of beta a couple of days ago.  Everything was fine until today. I didn't install the ricotz ppa but after today's updates I re-installed unity and installed the rictoz ppa and everything was fixed.

---

### Post by jbicha on 2011-09-09
Please install gir1.2-accountsservice-1.0 which I believe fixes this.

---

### Post by ratcheer on 2011-09-09
> **jbicha said:**
> Please install gir1.2-accountsservice-1.0 which I believe fixes this.

Yes, that fixed it for me. Thanks!

Tim

---

### Post by flipper T on 2011-09-09
+1

thx

for future reference, how did you find this out ?

---

### Post by Benjamin_Lebsanft on 2011-09-09
That did not fix it for me as it has already been installed? Any other ideas?

---

### Post by Harry33 on 2011-09-09
> **Benjamin_Lebsanft said:**
> That did not fix it for me as it has already been installed? Any other ideas?

How is your gnome-shell broken now?

---

### Post by Benjamin_Lebsanft on 2011-09-09
I still get the nautilus menu bar on top, no shell top panel, no alt+f2, no notification bar at the bottom

---

### Post by Harry33 on 2011-09-09
> **Benjamin_Lebsanft said:**
> I still get the nautilus menu bar on top, no shell top panel, no alt+f2, no notification bar at the bottom

And you do use the latest gnome-shell, clutter and mutter from Oneiric repos,
and you did install the missing gnome-shell dependency: gir1.2-accountsservice-1.0?

---

### Post by jppr on 2011-09-09
[https://launchpad.net/ubuntu/oneiric/+source/gnome-shell/3.1.90.1-0ubuntu4](https://launchpad.net/ubuntu/oneiric/+source/gnome-shell/3.1.90.1-0ubuntu4)

---

### Post by nm_geo on 2011-09-09
> **jbicha said:**
> Please install gir1.2-accountsservice-1.0 which I believe fixes this.

+1 I have had gnome shell running since first beta and lost it today until now.. Thanks

---

### Post by DogMatix on 2011-09-09
> **jppr said:**
> [https://launchpad.net/ubuntu/oneiric/+source/gnome-shell/3.1.90.1-0ubuntu3](https://launchpad.net/ubuntu/oneiric/+source/gnome-shell/3.1.90.1-0ubuntu3)
New version is coming :popcorn:
 

Phew! Launchpad is a wonderful thing.

---

### Post by DogMatix on 2011-09-09
> **nm_geo said:**
> +1 I have had gnome shell running since first beta and lost it today until now.. Thanks

I had a similar experience (acer zg8) but before I could figure it out. I screwed things up enough to make a re-install the easy option.

I'll try again tomorrow.

---

### Post by ronacc on 2011-09-09
gnome-shell had been down for me for a couple of days , update about an hour ago got it working again .

---

### Post by Benjamin_Lebsanft on 2011-09-10
Had to remove rico's testing ppa and now everything is fine. Someone should propagate the fix there too I think.

---

### Post by M4570D0N on 2011-09-10
Is anyone else having issues with gnome shell on Virtualbox? Unity seems to run okay. However, when I try to log in to the gnome shell session it appears to load, but as soon as I attempt to do anything or click anything, the entire screen in the VB window turns white. Any ideas?

This happens every time, both before and after installing the ricotz ppa.

GDM:
[[IMG]http://i596.photobucket.com/albums/tt45/SH00TTH3H0STAG3/th_Selection_045.png[/IMG]](http://i596.photobucket.com/albums/tt45/SH00TTH3H0STAG3/Selection_045.png)

Desktop:
[[IMG]http://i596.photobucket.com/albums/tt45/SH00TTH3H0STAG3/th_Selection_047.png[/IMG]](http://i596.photobucket.com/albums/tt45/SH00TTH3H0STAG3/Selection_047.png)

Click anything anywhere:
[[IMG]http://i596.photobucket.com/albums/tt45/SH00TTH3H0STAG3/th_Selection_048.png[/IMG]](http://i596.photobucket.com/albums/tt45/SH00TTH3H0STAG3/Selection_048.png)

---

### Post by MARP1961 on 2011-09-10
I was having similar problems with Gnome Shell in Virtualbox. I logged back into Unity (which worked OK), opened Synaptic Package Manager, searched for Gnome Shell and **marked it for a reinstall**. after rebooting, Gnome Shell was working and displaying correctly.

I assume these problems are typical of early Betas and are 'update related?'

---

### Post by flipper T on 2011-09-10
> Please install gir1.2-accountsservice-1.0 which I believe fixes this.

this worked for me yesterday, just rebooted into unity 3d & presented with clean desktop with nautilus menu bar at top...

gnome shell working ok.

tried re installing gir1.2-accountsservice-1.0, no help



update: unity --reset

probably a compiz conflict

problem solved

---

### Post by Harry33 on 2011-09-10
> **Benjamin_Lebsanft said:**
> Had to remove rico's testing ppa and now everything is fine. Someone should propagate the fix there too I think.

Actually I have no problems with Ricotz testing PPA.
I have updated all newer packages there is. Works really well.

---

