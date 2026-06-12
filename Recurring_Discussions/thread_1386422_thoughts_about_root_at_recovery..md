---
title: "thoughts about root at recovery."
date: 2010-01-20
forum: Recurring Discussions
---

### Post by Tompalaz on 2010-01-20
Hi all.
I was just thinking how easy it is to drop to root, all I have to do is to start (or restart) my computer and boot to recovery. Is there way to protect me and my data from this? 

I could use passwd root to set a password for root but then root would be able to login. There are some distros that let root be able to login, but I prefer if it wern't possible.

or I could set a password for grub, still, thats kind of annoying solution for a simple thing.

---

### Post by adam814 on 2010-01-20
Physical Access = Root Access

Short of locking your computer in a room and guarding it I don't think there's any way to eliminate the possibility of someone else with physical access and sufficient knowledge from "administering" your system for you.

Using disk encryption will protect your data at least.  But as I don't think you can encrypt your /boot with LUKS-dmcrypt a local attacker could replace your kernel image with something else (maybe network boot from somewhere else and still use your machine as they please).

---

### Post by snowpine on 2010-01-20
Recovery mode is a Feature, not a Bug.

Being able to recover your system is a great feature, trust me, you'll be glad it exists someday. :)

You are making an incorrect assumption (in my opinion): Your computer would be safe from a hacker with physical access, if you disable recovery mode.

---

### Post by bodhi.zazen on 2010-01-20
Moved to recurring discussions.

This topic comes up often and as adam814 indicated, restricting physical access is essential for security.

As an example, this post is 12 hours old:

[http://ubuntuforums.org/showpost.php?p=8694625&postcount=7](http://ubuntuforums.org/showpost.php?p=8694625&postcount=7)

---

### Post by Tompalaz on 2010-01-21
Thank you all for your answers.

I know it's a feature, and I've already used recovery many times. I just thought at least I could password protect it. It doesn't matter that much as I'm the only one with physical access at the moment. It was just a thought.

---

### Post by Techsnap on 2010-01-21
Set a root password, then you can protect it, it will ask you for a root password if you boot into FS mode after setting one.

---

### Post by fromthehill on 2010-01-21
> **Techsnap said:**
> Set a root password, then you can protect it, it will ask you for a root password if you boot into FS mode after setting one.
boot livecd
start terminal
sudo su
mkdir /tmpmount
mount sda1 /tmpmount 
<random malicious command> /tmpmount

---

### Post by adam814 on 2010-01-21
> **Techsnap said:**
> Set a root password, then you can protect it, it will ask you for a root password if you boot into FS mode after setting one.

Append init=/bin/bash to kernel boot line in GRUB config.  Doesn't even require a LiveCD.

---

### Post by Techsnap on 2010-01-21
> boot livecd
start terminal
sudo su
mkdir /tmpmount
mount sda1 /tmpmount 
<random malicious command> /tmpmount

Look, a lot of people would have password protected their BIOS where applicable also it's more likely someone could boot into the FS than boot a live CD. To secure the installed distro the best thing to do is set a root password, I can't understand the objection to setting root passwords on Ubuntu because it's flawed completely flawed!

---

### Post by aysiu on 2010-01-21
I think it's great.

Mac OS X also has a recovery mode (hold down Cmd-S during bootup) that allows you root access.

Over the holidays, I helped my in-laws reset a forgotten password on a Windows 7 computer by booting up a Ubuntu live CD.

Permissions separations are best for protecting against compromise from outside (networked/online) sources. If you don't trust the people who have physical access to your machine, block them from having physical access.

---

