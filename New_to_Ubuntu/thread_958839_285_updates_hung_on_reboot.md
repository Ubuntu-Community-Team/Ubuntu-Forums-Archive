---
title: "285 updates hung on reboot"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by Icebergaz on 2008-10-25
I am new to Ubuntu and following the install I had a notice that there were 285 updates available.  I downloaded and installed the updates.  The system asked for a reboot, but the reboot now box did not work. I shut off the computer and when it restarted it got into a loop repeating an error message.  Any suggestions?

Thanks!!

Icebergaz

---

### Post by drs305 on 2008-10-25
There really isn't enough information yet. Can you tell us what the error message was? 

Was this an initial install and you were doing the first update or have you been running it and have data you need to save on the partition?

---

### Post by st33med on 2008-10-25
Try inserting the LiveCD and we can go from there. Also, what error message is it saying?

---

### Post by dustint83 on 2008-10-25
short answer: TURN OFF AUTOMATIC UPDATES

sooner or later some update WILL break your system resulting in a full reinstall and loss of data in the process

ive learned this the hard way too many times

if your linux system works, dont update anything until you have to, its not like windows automatic updates where everything works afterwords (usually). 

for example, say you upgrade some libs that critical system process use (*.6 removed and replaced with *.72) your system will be screwed because its looking for *.6

just turn off updates

---

### Post by Icebergaz on 2008-10-26
Contrary to Dustin83"s advice, I reran the updates so that I could get the error messages - I had neglected to do that the first time.  Wouldn't you know it the updates ran clean this time and the system appears fine.  I have a couple more questions.  I am looking for printer drivers for my two printers - both HP - an OfficeJet Pro L7580 and a LaserJet 1020.  Also, the internal wireless ran fine under Windows but is not working in Ubuntu.  The computer is an HP zv5000 series.  Any suggestions as to how I might get this to come to life.  I do not have Windows running on this machine.

Thanks!!

Icebergaz

---

### Post by drs305 on 2008-10-26
For the printers, install 'hplip' and cups from synaptic or via CLI and then run System, Administration, Printers, New Printer. If you don't get it to work, you may need the more recent hplip. Here is a link on how to use the newer version (instructions were for a LJ 1000 but the install would be the same). *I would use the current version in synaptic if possible as the HPLJ 1020 should be supported.*
[http://ubuntuforums.org/showthread.php?t=957084#5]("http://ubuntuforums.org/showthread.php?t=957084#5")

I install CUPS and access it via [http://localhost:631/](http://localhost:631/) as I've used that menu system for a long time. I believe you can probably make the same settings changes via the HP Device Manager that HPLIP installs.

---

### Post by Icebergaz on 2008-10-26
Thanks to drs305 - printer drivers are installed.

---

### Post by Xiong Chiamiov on 2008-10-26
> **dustint83 said:**
> short answer: TURN OFF AUTOMATIC UPDATES

sooner or later some update WILL break your system resulting in a full reinstall and loss of data in the process

ive learned this the hard way too many times

if your linux system works, dont update anything until you have to, its not like windows automatic updates where everything works afterwords (usually). 

for example, say you upgrade some libs that critical system process use (*.6 removed and replaced with *.72) your system will be screwed because its looking for *.6

just turn off updates
I've generally had problems with Windows updates breaking things (don't update 'til they've had a chance to patch the update), while I haven't too much with Linux.  Unless you're running a server, I'd update whenever updates are available.  In the Linux community, updates are either security patches or new versions of things with new features, both of which you want.

The one thing you should be careful about are kernel upgrades.  Canonical has a habit of releasing new kernels that aren't compatible with things you use everyday (like wireless or graphics drivers), which can make life... interesting.

On to the topic at hand, what model of wireless do you have?

---

### Post by dustint83 on 2008-10-26
one thing that always seems to break for me, is pulseaudio. everytime i update it, i loose sound through pulse. even if i backup the .pulse folder and replace the files afterwards

on topic: glad you got your problems worked out with no more problems.

---

### Post by Icebergaz on 2008-10-27
Thanks to all.  I ran bcm43xx-fwcutter and after a little fiddling around the wireless came up.

Thanks Again!!!

Icebergaz

---

