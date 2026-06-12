---
title: "OS  select option? ( Win7 - Ubuntu dual boot)"
date: 2012-01-24
forum: New to Ubuntu
---

### Post by waxcan on 2012-01-24
Hi all,
Now I'm in the very first stage of what will be a painful Windows rehab. I only just took the blue pill and I'm still trying to shake my bad habits formed by living in Redmond's world where just below the happy façade the  machines are trying to suck the life from you.

I have dual booted my laptop with Win 7 and Ubuntu.

However when I did, I had no idea what to do. I made three partitions, one ext4 for Unbuntu, one fat for Win, and the memory spill partition - whatever it's called. See? dumb.

Now I can't switch to Windows. Why do I want to? Well I don't, but the missus does.

When it happened the first time I reinstalled Win and it booted fine - into windows. I couldn't access Ubuntu.

So I install unbuntu (onto its old separate partition that is) and it just boots right into Ubuntu.

Shouldn't there be an option to select an OS? Or do I have to down some more blue pills to see what's missing here?

BTW I'll post whatever info is needed to solve the problem, I just didn't want to dump useless data.

Thanks
wc

---

### Post by QIII on 2012-01-24
Did you update GRUB after installing Ubuntu?  (It should have run during installation, but one never knows.)

Easy thing to try, then we can check some more stuff like taking a look at your partitions.

```
sudo update-grub
```

Watch to see if it picks up Windows.

Reboot.  If it goes straight to Ubuntu again, reboot again and hold the shift key down when the BIOS starts to run and keep it down.  See if that presents you with a GRUB menu.

---

### Post by Double.J on 2012-01-24
Hi there! sorry to hear you are having difficulties!

Ubuntu should have set it up as dual boot. First try to do it yourself. use boot repair to fix the common issues (recommended repair.)

Open a terminal with CTRL+ALT+T then past in
```
 sudo add-apt-repository ppa:yannubuntu/boot-repair
```
Hit ENTER when prompted, then
```
sudo apt-get update && sudo apt-get install -y boot-repair
```
Once downloaded, 
```
 boot-repair
```

if recommended values fails - have a look at the advanced options and make sure it all looks right - grub installed to dev/sda.
_____________________________________

IF boot repair fails, and yo're still booting straight into ubuntu with no way of choosing, or windows isn;t an option, post the output of
```

sudo fdisk -l
```

highlight the output and past into your reply, then highligh and click the # button :)

Hope it helps!

---

### Post by nipunshakya on 2012-01-24
so in my guess, you first installed ubuntu after windows.
 then as your windows didn't work, u reinstalled it.
Again your windows worked and now your ubuntu didn't install. Then you installed ubuntu again and now your windows won't start?

Mate, your MBR is being rewritten again n again. You have to fix that grub thing so that you can get a menu at startup that will let you select between OSs.

The first method is just load to ubuntu, goto synaptic package manager and try to see if there is an automatic update available for grub or not. It is generally listed as **linux-header-2.38.13 -generic  **or something like that.. (you might want to mark all and update just in case if your system isn't updated)Thats the easiest way so far to update your grub. Try that first and if problem exists after update, feel free to ask here.Goodluck

---

### Post by QIII on 2012-01-24
I think I'd reverse the order of operations.  Before adding a ppa, installing software and running it, let's take a look at the diagnostic tools first.

---

### Post by Mark Phelps on 2012-01-24
> **waxcan said:**
> I made three partitions, one ext4 for Unbuntu, one fat for Win, and the memory spill partition - whatever it's called. See? dumb.
Was this on an empty drive? Or, was this in addition to the partitions you already had?

If the second, what tool did you use -- Linux or MS Windows -- to create the new partitions?

Do you know how many, and of what kind, of partitions you have now?

If you don't, then boot into Ubuntu, open a terminal, and enter "sudo fdisk -lu" (lowercase L, not a one).  Not much we can do until we see your current setup.

> Shouldn't there be an option to select an OS? Or do I have to down some more blue pills to see what's missing here?

IF Windows is still bootable, the "sudo update-grub" should generate a menu that will allow you to access it again.

---

### Post by waxcan on 2012-01-25
Hi all
Thanks for the quick replies.

Right, so I didn't read a thing before I installed Ubuntu. First big mistake. 

But what's done is done and  I don't want to cause damage by reinstalling and carrying on like a bull in a china shop any longer.

When I first installed Ubuntu, I used the Ubuntu disk to delete the  single Windows partition I had previously used, since I did not know  how to split it up.

From the free space, I created two 60Gb partitions, plus a third that  contained about 200mb. I used this small partition for Swap. I see that the number should have at least been 4Gb, double to my laptop's RAM.

I then re-installed Windows on the other 60gb partition.

When Ubuntu wouldn't boot, I reinstalled that onto the first 60gb partition it was probably still on.

I take it I thrashed the MBR?

-----

I successfully updated GRUB, rebooted, held shift and it loaded with the OS option screen. However Windows was not available 
Screen:
[http://bayimg.com/hAmIdaADc](http://bayimg.com/hAmIdaADc)

Now I noticed the Windows drive appears under devices

[http://bayimg.com/hAmIbAaDc](http://bayimg.com/hAmIbAaDc)

I ran through gnu/mirow's checklist, however it still boots into Ubuntu. So here is my fdisk output

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006f404

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2046   117186559    58592257    5  Extended
/dev/sda2   *   117186560   117391359      102400   82  Linux swap / Solaris
/dev/sda3       117391360   230252543    56430592    7  HPFS/NTFS/exFAT
/dev/sda5            2048   117186559    58592256   83  Linux

Disk /dev/mapper/cryptswap1: 104 MB, 104857600 bytes
255 heads, 63 sectors/track, 12 cylinders, total 204800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x41ad344c

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table

```Thanks for your patience. I'll give back to the community when I get to grips with this.

---

### Post by nipunshakya on 2012-01-25
Whoa there mate....i guess your device mapper is not working fine.Your BIOS didn't correctly recognize your HDD and Linux used that incorrect BIOS setting...i...i guess it did...but im not sure...
However, your windows is just in perfect shape and so don't panic.....just wait for others to identify your issue too....

Regards,WinuxUser

---

### Post by mastablasta on 2012-01-25
you probably overwrote the windows boot. it is otherwise easier to install windows first then ubuntu. And put the widnows on first parititon. if you had it installed before all you had to do was defragment the driver and use windows drive manager to reduce one partition in size and leave it unformatted. the partitions you need for Ubuntu are created automaticly during install process (unless you specify manual partitioning). so it the disk formatting into the desired format.
 
also the informaiton you posted only shows partitions. to give the full picture fo your boot issue oyu will need to use the live CD, boot into it and then use this script (follow the instructions on the page and then post results.txt here in code tags): [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by waxcan on 2012-01-26
Wiped, did a clean Win7 install, then installed ubuntu/ All is well again.

Thanks guys!

---

### Post by nipunshakya on 2012-01-27
Though not total solution, glad to know you worked out with a fresh installation...Happy Linuxing...

Regards,WinuxUser

---

