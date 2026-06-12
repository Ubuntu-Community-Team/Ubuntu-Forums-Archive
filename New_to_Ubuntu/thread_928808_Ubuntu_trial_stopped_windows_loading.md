---
title: "Ubuntu trial stopped windows loading"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by timdownie on 2008-09-24
I successfully downloaded the desktop version and burnt my CD.  I then went for the "trial" option (i.e. run from CD) and successfully ran Ubuntu.

The problem came when I shut the PC down (following instructions).  My computer will not now boot into Windows (XP).  It always hangs during bootup showing the windows logo but no HD activity.

It *will* boot into safe mode but a system restore has made no difference, it still won't boot up into windows.

Ubuntu seems to have corrupted something basic in the boot sector (I'm guessing).

Is there any way I can repair it short of a running the full windows installation repair option?

I know how to load the recovery console but not how to use it.  I know it does offer boot sector repair but the syntax is a bit beyond me.

Help!

TIA

Tim

---

### Post by billgoldberg on 2008-09-24
The live cd never touched your HDD, so Ubuntu can't be responsible.

You can use the repair option on your Windows cd to repair the MBR.

Or use the "Super Grub Disk" live cd.

---

### Post by MikeEvans on 2008-09-24
It might just be a coincidence that your having the issue after testing ubuntu.  Unless you started the installation process or otherwise messed with the drive from the live system it should not have touched your boot record.  Also, windows safe mode starts off the same hook in boot.ini that 'normal mode' does so if the boot record was messed up you shouldn't be able to get into safe mode.  Did you make any changes to the BIOS before loading ubuntu?

If not then you should troubleshoot it like a standard windows issue.  Before making any changes unplug the system for a few minutes and power back up to see if that does the trick. 

Ubuntu does mount your hard drives and there is a small chance it did actually corrupt some needed files.  If you want to try rebuilding the boot files from the recovery console here is a guide I use on all my jobs:

[http://docs.google.com/Doc?id=dvkxj2x_92q7mrv5]("http://docs.google.com/Doc?id=dvkxj2x_92q7mrv5")

---

### Post by timdownie on 2008-09-24
> **billgoldberg said:**
> The live cd never touched your HDD, so Ubuntu can't be responsible.

You can use the repair option on your Windows cd to repair the MBR.

Or use the "Super Grub Disk" live cd.

Well it *could* be a coincidence but it's seems odd that it should happen just after trying out a new OS.

Tim

---

### Post by timdownie on 2008-09-24
> **MikeEvans said:**
> It might just be a coincidence that your having the issue after testing ubuntu.  Unless you started the installation process or otherwise messed with the drive from the live system it should not have touched your boot record.  Also, windows safe mode starts off the same hook in boot.ini that 'normal mode' does so if the boot record was messed up you shouldn't be able to get into safe mode.  



That's got me a bit foxed too.  Last time anything like this happened it wouldn't boot into safe mode.

> Did you make any changes to the BIOS before loading ubuntu?

Nope.

> If not then you should troubleshoot it like a standard windows issue.  Before making any changes unplug the system for a few minutes and power back up to see if that does the trick. 

Ubuntu does mount your hard drives and there is a small chance it did actually corrupt some needed files.  If you want to try rebuilding the boot files from the recovery console here is a guide I use on all my jobs:

[http://docs.google.com/Doc?id=dvkxj2x_92q7mrv5]("http://docs.google.com/Doc?id=dvkxj2x_92q7mrv5")

Might go down that route when I'm feeling a bit braver but I'm not getting any error messages during boot.  It just hangs with the Windows XP logo and none-moving progress bar.

Thanks for the URL.

Tim

---

### Post by t0p on 2008-09-24
> **timdownie said:**
> Well it *could* be a coincidence but it's seems odd that it should happen just after trying out a new OS.

Tim

Coincidence is always odd.  But you really do need to accept it *is* coincidence. The Live4 CD session won't have touched the HDD *unless you told it to*.

---

### Post by timdownie on 2008-09-24
> **t0p said:**
> Coincidence is always odd.  But you really do need to accept it *is* coincidence. The Live4 CD session won't have touched the HDD *unless you told it to*.

How does this square with Mike Evan's comment?
> 
Ubuntu does mount your hard drives and there is a small chance it did actually corrupt some needed files.

Both can't be true so which is right?
TIA

Tim

---

### Post by Bölvaður on 2008-09-24
There is a chance he actually didn't boot up a live cd. Isn't there some function wubi gives to windows users to test out the cd in some different way than the normal live cd we all know is?

If this is normal live-cd I am amazed it actually could do that to your system, I would guess radiation is more likely source of that kind of problem, and we aren't talking about the most unlikely thing since calculators began to guess what numbers you are going to enter and give you the sum before you begin to touch the buttons.

*added*
The live cd is able to mount your hdd when asked to do it.
The live cd I tried the last time did not mount on startup, but it has been a while... perhaps the new ubuntu is a bit different from my experience and auto mounts.

---

### Post by Paqman on 2008-09-24
The only part of a hard drive the LiveCD will mount without being told is the swap partition. If you don't already have a swap partition, it won't mount anything (until you actually browse to that drive, of course)

---

### Post by t0p on 2008-09-24
> **timdownie said:**
> How does this square with Mike Evan's comment?


Both can't be true so which is right?
TIA

Tim

I'm right.

---

### Post by egalvan on 2008-09-24
> **Paqman said:**
> The only part of a hard drive the LiveCD will mount without being told is the swap partition. If you don't already have a swap partition, it won't mount anything (until you actually browse to that drive, of course)

Let's settle this....

I'm on a LiveCD right now 

8.04.1

haven't touched anything, no file browsing,

what info can I post to show?

---

### Post by MikeEvans on 2008-09-24
I don't know exactly when the drives are mounted but I just used my live cd to rescue my system yesterday and it appeared to auto-mount my hard drives.  I noticed the icons for the partitions right away.  Also the windows (NTFS) partition was mounted read & write which would allow for file changing. 

I use the live cd all the time to do repairs on windows and linux machines and have never had this happen.  I believe the support for windows partitions is very good and it's highly unlikly it caused this issue but there is that chance.  Now I have seen windows machines do that many times for seemingly no reason.  If I was to fix your machine I would first cut the power as I suggested.  If that didn't work I would open the case and inspect it for excess dust. Next I would reseat ram and cards. Next I would rebuild boot files, then standard reinstall, then assume a hardware conflict or bad hard drive.

---

### Post by Bölvaður on 2008-09-24
> **t0p said:**
> I'm right.

I agree. And seems like Paqman was saying that he agrees in a longer more detailed way.

What I am interested in knowing is how you ran your "trial". Did you burn a cd, put it in the pc before it booted up, choise to boot from cd (or changed the boot order or some thing depending on your motherboard), and then had the menu where you can choose what to do with the cd, like check ram for faults, install straight away, run it as live cd.. etc..


If thats the way you went then windows obviously didnt need any help ruining itself on it's own. And the best thing to do is to reinstall it after taking backup of your data.. well.. you really cant fix this kind things in windows can you (I have no idea)? It's all binary and sh1tec.

---

### Post by MikeEvans on 2008-09-24
Open up a terminal and type mount for a list of things that are mounted.  You might also check the places drop down to see if your hard drives are listed.  Thats what I was referring to.  I dont know what else you could do from ubuntu to fix the issue.

---

### Post by t0p on 2008-09-24
> **egalvan said:**
> Let's settle this....

I'm on a LiveCD right now 

8.04.1

haven't touched anything, no file browsing,

what info can I post to show?

Show us if your computer's HDD is mounted.  I reckon it isn't, and won't be unless you specifically tell it to.  Some other people think differently.

---

### Post by egalvan on 2008-09-24
> **MikeEvans said:**
> Open up a terminal and type mount for a list of things that are mounted.  You might also check the places drop down to see if your hard drives are listed.  Thats what I was referring to.  I dont know what else you could do from ubuntu to fix the issue.

Power-off, reboot, insert cd
Fresh-mounted LiveCD  8.04.1

```

ubuntu@ubuntu:~$ mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
ubuntu@ubuntu:~$ 
```

No drive on "Places"



I'm just trying to settle one way or another whether LiveCD "touches" the hard drive.


A question,,, does "mounting" a drive  WRITE anything to it?

If not, then how can merely mounting cause problems?

---

### Post by billgoldberg on 2008-09-24
> **t0p said:**
> Show us if your computer's HDD is mounted.  I reckon it isn't, and won't be unless you specifically tell it to.  Some other people think differently.

Top is right.

What don't some people understand when I said "a live cd won't touch your hard drive"?

You can use the live cd to mount your harddrives sure. But that's not standard behavior.

And even if you told it to mount your ntfs partition, that won't break anything.

It's not because there are icons of your partitions/hdd's/media on your desktop, that those are mounted.

---

### Post by egalvan on 2008-09-24
> **t0p said:**
> Show us if your computer's HDD is mounted.  I reckon it isn't, and won't be unless you specifically tell it to.  Some other people think differently.

OK, but HOW do I show this info?

I'm a bit of a newbie. 

I just posted "mount"

What else do you need?


Note;;;

I'm just trying to referee the situation. I have no link to the OP.

I'm trying not to be biased....

but I for one am tired of MS problems (among others) being blamed on Linux

---

### Post by timdownie on 2008-09-24
> **egalvan said:**
> 
I'm trying not to be biased....

but I for one am tired of MS problems (among others) being blamed on Linux

I've no axe to grind either but from my point of view, I had a working OS until I tried Ubuntu.  From what folk have said, it's probably coincidental but viewed from my end of the keyboard, I think I can be forgiven for suspecting that Ubuntu may have had a hand in it.

Anyway, done a repair with the Windows CD and everything seems back to normal.  Dunno if I'll be brave enough to try the Ubntu CD again though...

---

### Post by jerome1232 on 2008-09-24
What you posted from the mount command shows no drives as mounted.

---

### Post by billgoldberg on 2008-09-24
> **timdownie said:**
> I've no axe to grind either but from my point of view, I had a working OS until I tried Ubuntu.  From what folk have said, it's probably coincidental but viewed from my end of the keyboard, I think I can be forgiven for suspecting that Ubuntu may have had a hand in it.

Anyway, done a repair with the Windows CD and everything seems back to normal.  Dunno if I'll be brave enough to try the Ubntu CD again though...

Why?

Ubuntu had nothing to do with the error you have gotten.

Just a coincidence. 

As stated before, a live cd session won't touch your hdd unless you tell it too.

If it doesn't touch your HDD, it can't do any damage.

And even if you mount the drives, that won't cause any harm.

Unless you browse to your Windows installation files and start deleting stuff, nothing will happen.

---

### Post by nowshining on 2008-09-24
how often do does the OP keep his computer running? did the OP have anti-virus/anti-malware, etc.. software running?

It could be that if they never rebooted in awhile and installed some software, ec..or a virus/malware was hiding that would screw with XP after the next reboot, etc.. (i had a hacker/cracker do this to me before all was fine until i rebooted and it wouldn't boto up) anyway back to business, yes yes, maybe just maybe now since the OP rebooted and tried XP and like I said didn't boot for awhile or a virus/malware item was hiding incase the next reboot came around, that after they tried Ubuntu and rebooted xp the malware/virus, etc.. took its' turn for the worse...and did its' damage...

edit" adding

The OP could boot into safe mode - meaning that some code that is intact and used when windows boots up is damaged or a virus/malware as I suggested above...

---

### Post by egalvan on 2008-09-24
e

---

### Post by egalvan on 2008-09-24
> **billgoldberg said:**
> The live cd never touched your HDD, so Ubuntu can't be responsible.

> **t0p said:**
> Coincidence is always odd.  But you really do need to accept it *is* coincidence. The Live4 CD session won't have touched the HDD *unless you told it to*.

I agree with billgoldberg & t0p

Linux is not at fault.


> **Paqman said:**
> The only part of a hard drive the LiveCD will mount without being told is the swap partition. If you don't already have a swap partition, it won't mount anything (until you actually browse to that drive, of course)

Seems this has been shown to be true by that 'mount' output I posted.


> **timdownie said:**
> I've no axe to grind either but from my point of view, I had a working OS until I tried Ubuntu.  ...it's probably coincidental but viewed from my end of the keyboard, I think I can be forgiven for suspecting that Ubuntu may have had a hand in it.

Anyway, done a repair with the Windows CD and everything seems back to normal.  Dunno if I'll be brave enough to try the Ubntu CD again though...

I don't think it was a coincidence... I think it was either a Microsoft error, or user error.
Or, possibly, hardware messing up.

> **jerome1232 said:**
> What you posted from the mount command shows no drives as mounted.


Yes, I agree, but I really don't know how to interpret those read-outs,
which is why i asked t0p and billgoldberg to  check on it...


for what it's worth, I have dual-booted XP & Ubuntu on six different computers here in my house.
Ranging from a high-end HP MultiMedia Core2Duo, dual-drive
high-end laptop, AMD Dual Cores, dual-drive
to a pair of mid-range Dells,
to a lowly HP E-PC running P-III @ 933 with 256meg RAM.


The ONLY time I have had XP problems is when I
decided to shrink the XP partion on my IBM T60P laptop,
and I ME MYSELF AND NO ONE ELSE typed 1000 instead of 10000 in the 'size window'
Yeah, 8gigs of XP don't like being squeezed down to 1gb
Imagine my surprise...


Thanks t0p and billgoldberg

gotta stop the LiveCD and go back to my regular Ubuntu/Kubuntu
I'm trying to solve a "PRIVILEGE" problem.

---

### Post by The Cog on 2008-09-24
I agree that is is unlikely that Ubuntu did the damage. And I fully understand why it looks suspicious to someone who is trying Ubuntu out for the first time.

As for mounting by the live CD, I believe that the disks shown in **places** get mounted only if the icon is clicked, and then a file manager opens on the partition. The mount command should confirm this (df -h is easier to read). For an NTFS partition, I believe this action makes what should be a harmless write to the partition, marking it as dirty such that it will be given a chkdsk by windows on startup if it is not later umnounted cleanly.

---

