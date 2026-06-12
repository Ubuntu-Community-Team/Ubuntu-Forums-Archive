---
title: "Error checking /windows partition"
date: 2011-09-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by dcordeiro on 2011-09-10
Hello,

After upgrading to Oneiric, I receive an error at *every* boot telling that my /windows partition have grave errors that cannot be fixed. I'm prompted to either ignore, skip mounting or manually check the error.

If I ignore, the windows partition is mounted just fine.

I hadn't this problem before. Anyone else suffering with it?

Any tips on how to fix this? I don't know even against which package I should fill a bug to report this...


Thanks,
Daniel

---

### Post by cariboo on 2011-09-10
I suggest booting int o Windows and running:

```
chkdsk c: /f /r 
```

---

### Post by VinDSL on 2011-09-10
If I remember correctly, "/f" is implied, when you invoke "/r".

Doesn't hurt anything, just saying.  ;)

Also, assuming the system files are on C-drive... the files on "c:" need to be locked, before you can fix them.

Thus, AFAIK, the OP will need to run that command in a terminal (whatever they call it) and schedule it for the next boot.

LoL!  Haven't used Winders for a while.  Hope I'm not confusing the situation.  :D

---

### Post by effenberg0x0 on 2011-09-10
I don't have a window partition to test it right now. If I did, I would attempt the following:

- You probably have a line in your /etc/fstab that mounts the Windows partition using ntfs-3g. The arguments in this line have it set to auto (automount). I would change it to noauto, so that I can mount it manually when needed.

- See if you still get the error when mounting it manually, after the complete Ubuntu boot process. I would guess there's a higher chance of a problem with automounting it at the wrong time then a more serious ntfs partition or bootsector corruption.


Regards,
Effenberg

---------------------------------
Just as a note: Oneiric is Beta1. It is expected to not work 100% and is  not what I would personally recommend for anyone that just needs to get  the job done. It's aimed at beta testers and people that can afford to  have a broken PC right now. So PLEASE: DO NOT attempt any of the  mentioned procedures if you're working on a server / production machine,  if you don't have backup of your data or if you don't have the habit of  performing fixes in Ubuntu / Linux distros. You can end up having to do  a new install from scratch. I can't be held responsible for any damage,  ok? :smile:

---

### Post by cariboo on 2011-09-11
> **VinDSL said:**
> If I remember correctly, "/f" is implied, when you invoke "/r".

Doesn't hurt anything, just saying.  ;)

Also, assuming the system files are on C-drive... the files on "c:" need to be locked, before you can fix them.

Thus, AFAIK, the OP will need to run that command in a terminal (whatever they call it) and schedule it for the next boot.

LoL!  Haven't used Winders for a while.  Hope I'm not confusing the situation.  :D

I don't use Windows often either, and it's been a while since I worked on any Windows systems, but I'm assuming the op knows how to diagnose and solve Windows problems.

There is the  option to do a disk check in the disk management menu, that runs chkdsk on the next reboot.

---

### Post by PaulInBHC on 2011-09-11
I have XP Home SP3, C and D partitions. After installing Oneiric I get a pink screen to select OS. If I pick XP, I get a black screen to select XP or ubuntu. The first time back to XP I got the blue screen stating to check disc on C. I figured that was because of the resizing of the hdd. I didn't get it again until today. I tried it run disc cleanup on D and it wouldn't work. I also updated Oneiric. I allow check disc to run. It doesn't take long for me and it can't hurt. The second time it did find some things. I think it was related to me trying to do the disc cleanup.

---

### Post by dcordeiro on 2011-09-11
Thanks for your suggestion. I've already tried that, but it doesn't fix the problem.

The strange thing is that I didn't had this error before the upgrade to Oneiric. But just after upgrading (in the first reboot into Oneiric), I started to receive it all the time.

Also, as I said, mounting this partition manually works fine (no errors or warnings).

Any suggestions? Is there a logfile somewhere where I can look for any error messages that resulted in the boot system prompting me to skip mounting /windows ?


> **cariboo907 said:**
> I suggest booting int o Windows and running:

```
chkdsk c: /f /r 
```

---

### Post by dcordeiro on 2011-09-11
Hi,


Well, the line in /etc/fstab that mounts this partition is:
/dev/sda3	/windows        ntfs    utf8,umask=007,gid=46 0       1

(gid 46 is pluddev)

I've never touched this line before, it was always managed automatically by Ubuntu.


Mounting manually by doing "$ sudo mount -v /windows" works fine. No error messages or warnings whatsoever.

> **effenberg0x0 said:**
> I don't have a window partition to test it right now. If I did, I would attempt the following:

- You probably have a line in your /etc/fstab that mounts the Windows partition using ntfs-3g. The arguments in this line have it set to auto (automount). I would change it to noauto, so that I can mount it manually when needed.

- See if you still get the error when mounting it manually, after the complete Ubuntu boot process. I would guess there's a higher chance of a problem with automounting it at the wrong time then a more serious ntfs partition or bootsector corruption.


Regards,
Effenberg

---------------------------------
Just as a note: Oneiric is Beta1. It is expected to not work 100% and is  not what I would personally recommend for anyone that just needs to get  the job done. It's aimed at beta testers and people that can afford to  have a broken PC right now. So PLEASE: DO NOT attempt any of the  mentioned procedures if you're working on a server / production machine,  if you don't have backup of your data or if you don't have the habit of  performing fixes in Ubuntu / Linux distros. You can end up having to do  a new install from scratch. I can't be held responsible for any damage,  ok? :smile:

---

### Post by effenberg0x0 on 2011-09-11
You could change it to:

/dev/sda3	/windows        ntfs    utf8,umask=007,gid=46,noauto 0       10

It would avoid automounting. Just for a test, of course.

Regards,
Effenberg

---

### Post by dcordeiro on 2011-09-11
It sure "fix" the problem for me. But since it happened after my upgrade, I would like to fill a bug report. Others may have the same problem.

Against which package should I report the bug?

> **effenberg0x0 said:**
> You could change it to:

/dev/sda3	/windows        ntfs    utf8,umask=007,gid=46,noauto 0       10

It would avoid automounting. Just for a test, of course.

Regards,
Effenberg

---

### Post by effenberg0x0 on 2011-09-11
Hey,

Ah, I knew it. I suggested removing the automount feature because I saw a similar error in a PC a week ago and I got suspicious and thinking about it. I was pretty sure the HDD was physically OK and had no MBR/logical partition or any data errors. 

I am **guessing** it has something to do with mounting the drive too soon, somehow (and I am very aware of how silly and unconventional it sounds). But I am not sure. I can't properly advice you which package to mention on the bug report. You are allowed to not specify the package and leave that to the bug reviewers, which I think its wise in this case.

I'd like to hear some opinions of other helpers and more experienced users on this issue.  

Regards,
Effenberg

--------------------------
Ubuntu Oneiric is Beta 1. It is expected to not work 100% and is not what I would personally recommend for anyone that just needs to get the job done. It's aimed at beta testers and people that can afford to have a broken PC right now. So PLEASE: DO NOT attempt any of the mentioned procedures if you're working on a server / production machine, if you don't have backup of your data or if you don't have the habit of performing fixes in Ubuntu / Linux distros. You can end up having to do a new install from scratch. I can't be held responsible for any damage, ok? :-)

---

### Post by uhop on 2011-09-13
> **dcordeiro said:**
> It sure "fix" the problem for me. But since it happened after my upgrade, I would like to fill a bug report. Others may have the same problem.

I am one of the "others" --- I have exactly the same problem. Please file a bug, and let me know where it is so I can mark it as "affecting me".

---

### Post by dcordeiro on 2011-09-13
It's good to see that I'm not alone. :)

I've filled this bug report: [https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/847465](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/847465) but got no response so far.

> **uhop said:**
> I am one of the "others" --- I have exactly the same problem. Please file a bug, and let me know where it is so I can mark it as "affecting me".

---

### Post by dino99 on 2011-09-13
> **dcordeiro said:**
> It's good to see that I'm not alone. :)

I've filled this bug report: [https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/847465](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/847465) but got no response so far.

i hope you does not have resized ntfs partition with gparted:
[https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/837213](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/837213)

( sadly this report is tagged "whislist", meaning devs will ignore it, as they have more urgent bugs to look at.

---

### Post by dcordeiro on 2011-09-13
I think that being able to resize a ntfs partition is a big deal to new Ubuntu users coming from Windows. I hope that they have taken the right decision marking it only as a wish. :P

In my case, this partition was never resized, so this is not related to my bug report.

> **dino99 said:**
> i hope you does not have resized ntfs partition with gparted:
[https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/837213](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/837213)

( sadly this report is tagged "whislist", meaning devs will ignore it, as they have more urgent bugs to look at.

---

### Post by sgage on 2011-09-13
> **dcordeiro said:**
> Hello,

After upgrading to Oneiric, I receive an error at *every* boot telling that my /windows partition have grave errors that cannot be fixed. I'm prompted to either ignore, skip mounting or manually check the error.

If I ignore, the windows partition is mounted just fine.

I hadn't this problem before. Anyone else suffering with it?

Any tips on how to fix this? I don't know even against which package I should fill a bug to report this...


Thanks,
Daniel

I have the exact same problem. I've always done what you've done, so that my Windows partition is automatically mounted at boot.

There are no issues with the partition, I can mount in manually with no problem. If I remove the line in fstab, I can mount the drive from Nautilus with no problem.

I'd like to have a real fix for this.

---

### Post by effenberg0x0 on 2011-09-13
A few questions for you guys. What happens if you try it like this:

sudo apt-get install ntfs-3g
gksudo gedit /etc/fstab

1- Put a comment mark (#) in front of your windows mount line. For backup reasons.
2- Create a new Windows mount line below, using ntfs-3g and defaults. The final result will look like this:

```

#/dev/sda3    /windows        ntfs    utf8,umask=007,gid=46,noauto 0 10
#/dev/sda3    /windows    ntfs-3g   defaults,force 0 0

```3- Save /etc/fstab and restart the PC.

In order to revert this changes, all you have to do is

1- gksudo /etc/fstab
2- Remove comment from first WIndows mount line (the one that uses ntfs)
3- Remove the second line (the one that uses ntfs-3g
4- Restart the PC

Regards,
Effenberg

--------------------------
Ubuntu Oneiric is Beta 1. It is expected to not work 100% and is not what I would personally recommend for anyone that just needs to get the job done. It's aimed at beta testers and people that can afford to have a broken PC right now. So PLEASE: DO NOT attempt any of the mentioned procedures if you're working on a server / production machine, if you don't have backup of your data or if you don't have the habit of performing fixes in Ubuntu / Linux distros. You can end up having to do a new install from scratch. I can't be held responsible for any damage, ok? :-)

---

### Post by dcordeiro on 2011-09-15
Hello,

I tested changing from ntfs to ntfs-3g yesterday (after applying all the updates) and the problem persists. :(

> **effenberg0x0 said:**
> A few questions for you guys. What happens if you try it like this:

sudo apt-get install ntfs-3g
gksudo gedit /etc/fstab

1- Put a comment mark (#) in front of your windows mount line. For backup reasons.
2- Create a new Windows mount line below, using ntfs-3g and defaults. The final result will look like this:

```

#/dev/sda3    /windows        ntfs    utf8,umask=007,gid=46,noauto 0 10
#/dev/sda3    /windows    ntfs-3g   defaults,force 0 0

```3- Save /etc/fstab and restart the PC.

In order to revert this changes, all you have to do is

1- gksudo /etc/fstab
2- Remove comment from first WIndows mount line (the one that uses ntfs)
3- Remove the second line (the one that uses ntfs-3g
4- Restart the PC

Regards,
Effenberg

--------------------------
Ubuntu Oneiric is Beta 1. It is expected to not work 100% and is not what I would personally recommend for anyone that just needs to get the job done. It's aimed at beta testers and people that can afford to have a broken PC right now. So PLEASE: DO NOT attempt any of the mentioned procedures if you're working on a server / production machine, if you don't have backup of your data or if you don't have the habit of performing fixes in Ubuntu / Linux distros. You can end up having to do a new install from scratch. I can't be held responsible for any damage, ok? :-)

---

### Post by deadvirus on 2011-09-24
I also have this problem after updating from Natty to Oneiric Beta 2... No fix yet?

---

### Post by dcordeiro on 2011-10-07
No fix and no one is assigned to bug [https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/838091](https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/838091) yet. :(

> **deadvirus said:**
> I also have this problem after updating from Natty to Oneiric Beta 2... No fix yet?

---

