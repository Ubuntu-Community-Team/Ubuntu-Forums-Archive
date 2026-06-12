---
title: "Trouble installing Ubuntu 11.10 - Can't do Side By Side"
date: 2012-02-12
forum: New to Ubuntu
---

### Post by doppel.ganger on 2012-02-12
I'm trying to install Ubuntu 11.10 on a netbook (HP Mini 5101) that has Windows 7 on it. I want to install them side-by-side, but it just gives me the option to Replace Windows 7 with Ubuntu or Something Else. I'm a little afraid to venture into Something else, I don't want to accidentally delete my Windows 7 :( Help!

---

### Post by doppel.ganger on 2012-02-12
In GParted on the live disk, it shows a red ! sign next to my Windows Partition.

---

### Post by Hartwell on 2012-02-12
"Something Else"  plenty of options will come up, including one where you resize your existing windows partition, create a new / and /swap partition, and install ubuntu there.

if you are afraid to install to the hard drive, feel free to run LIVE ubuntu forever.  lots of people do this.

---

### Post by doppel.ganger on 2012-02-12
No, I've done an install before, I just don't want to get rid of Windows and I don't want to accidentally mess up the hard drive!

---

### Post by Hartwell on 2012-02-12
perhaps wubi will make you feel better

[http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)

---

### Post by doppel.ganger on 2012-02-12
I was able to create a teeny 1mb Ext4 partition for the install, but I can't resize it. See screenshots.

---

### Post by doppel.ganger on 2012-02-12
And i've heard Wubi can cause hard drive instability.

---

### Post by Hartwell on 2012-02-12
you're running windows XP and you're worried about hard drive instability?  

did you boot the installer from a USB drive or an external CD?  OR, did you cause the C: drive to be mounted?  that might be keeping gparted from being able to do its magic.

look: a million people have installed ubuntu on netbooks.  what's the worst that can happen?  (answer: you'll have to re-install windows)  BFD

good luck

---

### Post by doppel.ganger on 2012-02-12
OK, I got the netbook from a friend. The friend got it w/ Windows XP then paid for a license to install Windows 7. I don't want to delete Windows 7 because that would be a waste of a very expensive license. I do not have any means of recovering Windows 7 here.

---

### Post by westie457 on 2012-02-12
Hi

First things first.

Boot into Windows, if Windows wants to check the hard drive for errors let. If it boots into normal, open a command prompt in administrator mode and type in ```
chkdsk /f
``` you will then have to restart to force the check.
The red warning symbol is telling you there is a problem with the NTFS file system and Gparted will not do anything with it.

It is better to shrink a Windows partition using Windows partitioning programs. Suggest you use something like this one, [http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html) or one of your choice.

Shrink the partition by as much as Windows allows. Leave the newly created space unformatted so the Ubuntu installer can use it.

When doing the install use the 'Something Else' option to choose your install file systems.

If I have forgotten anything feel free to ask again.

++++++++++++++++++++++++++++++++++++++++++

Actually I did forget something very important. 

Use Windows to make a back up snapshot of the current system and burn it to DVD for worst-case scenario of system hosing. Also make a recovery CD for minor emergencies.

**Do this before going ahead with the installation.**

---

### Post by doppel.ganger on 2012-02-12
Does chkdsk /f fix the hard drive or just tell you if there's something wrong?
And, how do you make a snapshot?

---

### Post by doppel.ganger on 2012-02-12
Hey, running ```
chkdsk /f
``` worked! Now gives me the option for a side-by-side install! Thanks! SOLVED!

---

### Post by westie457 on 2012-02-12
Chkdsk /f will fix the file system, Chkdsk with no options will check and not repair, however it will report what the problems are.

To make the system image and the recovery disk click on the Windows start button, type in backup and click on the suggested program. In the window that opens are both options choose one and follow the prompts that appear. Do that for both options and you will be set to cope with most or all of Windows start up problems.

---

