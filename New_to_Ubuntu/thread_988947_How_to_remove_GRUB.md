---
title: "How to remove GRUB"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by theamber on 2008-11-21
hi, I tried to install Ubuntu in a AMD 64 Turion laptop it froze up so I did turn off the machine improperly (holding power button), I know now how to reset it properly now.
the thing is that I formatted it and even low level in order to put windows on it or ubuntu but grub does not go away. How can I remove it? Sometimes it comes on in the prompt and the header checksum for windows does not match. I thought my hard disk was bad. Is there anyway to remove completely Grub. thanks. right now I have a failed Windows vista installed but it does not boot, I am using the live CD to get online now.

---

### Post by jimreynold2nd on 2008-11-21
I still did not fully understand some of your points. What do you mean when saying "low level format"? in my vocabulary, "low-level format" means rewriting the physical pattern on the HDD; people stopped doing that since the 90s AFAIK; no way GrUB will survive that.

With that said, I assume you meant you repartitioned the disk. Were you able to boot into Windows at all? And what do you mean by "sometimes it comes on in the prompt"? If the GrUB partition is gone (IF you repartitioned the disk for Windows only) then there can't be a GrUB prompt unless it's a ghost o.0. The only residue might be the MBR that GrUB placed its stage1 in. But if that's the case then you won't be able to boot into Windows at all.

Anyway, here's the generic step that will fix most of Windows' boot problems:
**If you installed XP:** put the XP boot CD back in, boot from it, when it prompts for install or repair, choose repair and you will go to recovery console. login to your admin account, then type "fixmbr", then "fixboot". That will replace the grub MBR with XP MBR.
**If you installed Vista:** put the Vista CD back in, choose repair boot and it will automatically replace the grub MBR.

**But** this is what I'm afraid: the "header checksum" error under Windows is not related to GrUB. It may be the signal of a faulty RAM stick or your HDD is dying.

---

### Post by theamber on 2008-11-21
Low level format is writing 0s on the drive there are plenty of software to do that. I installed windows XP after using all kinds of MBR fix partition and format utilities but I cannot get all the size there are something on the disk it does not give me all the space available is some type of virus because sometimes I get the message and grub terminal came out after a low level format. I have never seen anything like this in over 19 years doing this.I can't install any operating system teh drive seems healthy but I may have to throw the drive away.

---

### Post by jimmy the saint on 2008-11-21
more on low-level formatting.
[http://www.pcguide.com/ref/hdd/geom/formatLow-c.html](http://www.pcguide.com/ref/hdd/geom/formatLow-c.html)

info from MS about the MS issue
[http://forums.microsoft.com/TechNet/ShowPost.aspx?PostID=2568080&SiteID=17](http://forums.microsoft.com/TechNet/ShowPost.aspx?PostID=2568080&SiteID=17)

I suggest looking at both

---

### Post by bumanie on 2008-11-21
Go to the drive manufacturer's website and download their diagnostic tool and see what it comes up with - you 'low-level' format should  have effectively removed all references to grub.

---

### Post by jimreynold2nd on 2008-11-21
Well, I think I learned something. I always thought writing 0's is called safe-erasing, and rewriting the cylinder-head-sector pattern is low-level format....
If you only write 0's to the linux partition, then the grub partition (if there is one) and the mbr is not erased. If you wrote 0's to the entire disk (entire-disk != all-the-partitions) then grub cannot survive. If it does, then I'm afraid yours' a faulty drive.

Anyway, I would go with bumanie: go get the mfg's diagnostic tool and check the hdd.

---

### Post by theamber on 2008-11-22
> **jimreynold2nd said:**
> Well, I think I learned something. I always thought writing 0's is called safe-erasing, and rewriting the cylinder-head-sector pattern is low-level format....
If you only write 0's to the linux partition, then the grub partition (if there is one) and the mbr is not erased. If you wrote 0's to the entire disk (entire-disk != all-the-partitions) then grub cannot survive. If it does, then I'm afraid yours' a faulty drive.

Anyway, I would go with bumanie: go get the mfg's diagnostic tool and check the hdd.

I think is both what I know is that low level formatting is the closest you can get to HD factory defaults. They get low level format in the factories I think before being high level formatted.
I have managed to get the drive working for now. I changed the geometry with a program. Pressing the power in the middle of an installation is real trouble. last choice before doing that is ctrl-alt-sys rq- R E S U I B (in rapid succession). Thanks to all.

---

### Post by theamber on 2008-11-22
Grub is still in the hard disk after installing Vista. I get errors in the disk and then the grub prompt. There is no way to remove this?
What can I do if I get the grub prompt.
I can't install ubuntu it gives X server error.
Vista dos not work anymore.
Any help please teh drive is in good shape media wise.

---

### Post by caljohnsmith on 2008-11-22
If you truly wrote zeros to the entire drive in a low level format, I think the only way you could still be getting Grub is if you have Grub installed in the MBR of another drive that you have connected and are unintentionally booting; do you have any other drives connected?

How about booting your Live CD, open a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
So replace "sda" above with each of your drives. And finally, for each command above that returns "GRUB", please post:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```
And replace sda with the drives that previously returned "GRUB". That will greatly clarify what your setup is presently like.

---

### Post by theamber on 2008-11-22
sudo fdisk -lu 
I get this:
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf1e76438

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   156296384    78148161    7  HPFS/NTFS
ubuntu@ubuntu:~$
I typed the other two codes I get 
4144

---

### Post by theamber on 2008-11-22
when I get the bootloader the grub prompt can I type something to remove it from that prompt?
I tried from teh live cd booting from teh cd rom 
sudo apt-get remove grub 
and others but i get unrecognize command.
also my drive has 16383 cilinders I did not get that from the command on the other post.

---

### Post by theamber on 2008-11-22
I think when I had errors installing ubuntu and I turned off the power grub got installed in one of the partition tables because I only have one when I use utilities to reconstruct it and I suppose to have two tables right?. The utilities I used wrote 0s to the Master boot record and all. then I fixed it the MBR. The problem is in the boot loader grub is still in the drive.

---

### Post by theamber on 2008-11-22
From the live cd booting from the CDrom is there any way to repair de MBR of the drive?.

---

### Post by jimreynold2nd on 2008-11-22
Sorry to be rude, but you need to relax a little, take a breath. You are not as experienced as you thought.

Answer to your question: No, you can't install Windows' bootloader using a Linux LiveCD (duh!). You have to do it from a Windows CD, not a Linux CD. Ubuntu LiveCD can only repair MBR to make it boot Ubuntu as a Windows BootCD can be used to repair MBR to make it boot Win.
[COLOR="White"]Actually, you can write whatever you want to the MBR with the live CD, but then your computer won't be bootable at all (GrUB is gone, no bootloader in MBR) and if you overwrite the last 66 bytes, you will lost all your partitions.[/COLOR] <-- don't read those

Did you try my suggestion earlier of repairing using the Vista DVD? That will erase GrUB in MBR and replace it with Vista's boot loader.

EDIT: I re-read all your posts, and it seems like they are all confused (or perhaps you are - Relax! It'll be ok.) How can grub is still there after you wrote 0's all over? And it seems like you have only 1 HDD from your fdisk output. You should really try using the Vista installation DVD and use the boot repair utility in there.

---

### Post by theamber on 2008-11-22
> **jimreynold2nd said:**
> Sorry to be rude, but you need to relax a little, take a breath. You are not as experienced as you thought.

Answer to your question: No, you can't install Windows' bootloader using a Linux LiveCD (duh!). You have to do it from a Windows CD, not a Linux CD. Ubuntu LiveCD can only repair MBR to make it boot Ubuntu as a Windows BootCD can be used to repair MBR to make it boot Win.
[COLOR="White"]Actually, you can write whatever you want to the MBR with the live CD, but then your computer won't be bootable at all (GrUB is gone, no bootloader in MBR) and if you overwrite the last 66 bytes, you will lost all your partitions.[/COLOR] <-- don't read those

Did you try my suggestion earlier of repairing using the Vista boot CD? That will erase GrUB in MBR and replace it with Vista's boot loader.

CAN YOU SEE THIS:
I tried EVERYTHING posted and not posted grub stays.
You are wrong test disk is a program under the terminal on the live CD CAN recover partitions on ANY operating system. I invite you to load it and see.
I am NOT experienced with Linux that is why I am in the absolute beginner.
I did have my first PC back in 1989 that make me a little experienced with PC.
I am never relaxed I am ferocious!
Now do you have any tip that has not been stated already, I am about to let the drive go and buy another.The drive is good the only problem is that grub corrupted the MBR or the tables.

---

### Post by meierfra. on 2008-11-22
Do you have more than one hard drive attached to the computer? Or a flash drive?  Anything which could be interfering with the booting?  Floppy? Cdrom?

What exactly happens when you try to boot?

Type

```

geometry (fd0)

geometry (hd0)

geometry (hd1)
```

at the grub prompt and post the output.

---

### Post by theamber on 2008-11-22
None of the selected disk exists under geometry grub.
It is a laptop I only have one drive and one cd rom, nothing else.
Let me reboot the drive does not get recognized any more.

---

### Post by theamber on 2008-11-22
now I get this:
ubuntu@ubuntu:~$ fdisk -lu
Cannot open /dev/sda

---

### Post by meierfra. on 2008-11-22
> one cd rom,

Anything in the cd drive while you are trying to boot the hard drive?

---

### Post by meierfra. on 2008-11-22
> ubuntu@ubuntu:~$ fdisk -lu
Cannot open /dev/sda

You need "sudo":

```
sudo fdisk -lu
```

---

### Post by theamber on 2008-11-22
nothing in the CD disregrad last message I did not put sudo.

---

### Post by theamber on 2008-11-22
under fdisk -lu Why only shows 9729 cylinders.
Now the Vista CD does not even sees the Vista anymore.
I get just a blinking cursor on the upper left of the screen.
also all my utilities and i have them all show 76gb and the drive is 80.

---

### Post by meierfra. on 2008-11-22
Do

```
sudo dd if=/dev/sda count=63| gzip -c > ~/Desktop/sda.MBR.gz
```

and attach the  "sda.MBR.gz" file on your desktop to your next post.
I just want to see whether there are any traces of grub on the first few sectors of the hard drive.

Can you describe exactly what happens during boot up?  Does Vista start to boot? Or does the grub prompt appears right after the bios screen? Any error messages? 

> 
Why only shows 9729 cylinders

9729 is  consistent with  your fdisk output. Why do you think that the hard drive has 16383 cylinders?

 > 76gb and the drive is 80.
That's just due to the conversion. One GB is 1024 MB, and so on.

---

### Post by theamber on 2008-11-22
> **meierfra. said:**
> Do

```
sudo dd if=/dev/sda count=63| gzip -c > ~/Desktop/sda.MBR.gz
```

and attach the  "sda.MBR.gz" file on your desktop to your next post.
I just want to see whether there are any traces of grub on the first few sectors of the hard drive.

Can you describe exactly what happens during boot up?  Does Vista start to boot? Or does the grub prompt appears right after the bios screen? Any error messages? 



9729 is  consistent with  your fdisk output. Why do you think that the hard drive has 16383 cylinders?

 
That's just due to the conversion. One GB is 1024 MB, and so on.

sometimes I used to boot up right but other I used to get the grub prompt with errors right after the bios. Thanks I will post that file now....
I know the cylinders because they are printed on the drive.

---

### Post by theamber on 2008-11-22
Ok I can't open the file I have no applications for it. If someone ccan please put it on.
I am including it..

---

### Post by theamber on 2008-11-22
I do remember many years ago I had a 40 megabytes hard disk that someone put a bootloader menu at the beginning and I just used to get the menu right after the BIOS I formatted it low level and still I could never get that menu out, but all the other data got erased. The drive was find only showed that menu an initialization.
the partition or the MBR are corrupted. The thing is that some times works fine I know if I formated and install Windows it will work for a while.
also I can boot ubuntu from the CD but I cannot install it.I get server X error not loaded GDU or something like that.
any ideas how to install ubuntu on it. It does boot fins with DOS version 7.1.
With this drive I tried everything under windows utilities programs I have them all, wrote 0s to the MBR repair partition tables, format it many ways. the Media is fine and MBR fine too but some programs give me errors on the partition tables.

---

### Post by meierfra. on 2008-11-22
> Ok I can't open the file I have no applications for it. If someone ccan please put it on.
No need to open the file.  The attachment is all I wanted.


Your first sector is just the regular Windows MBR, but after that all the lines look like:

4844 4154 4844 4154 4844 4154 4844 4154

(or  HDATHDATHDATHDAT  in letters rather than hexadecimals)

 This doesn't explain how the "grub prompt" appears, but I would suggest to write zeros to the 62 sectors after the MBR and see whether it makes a difference:

```
sudo dd if=/dev/zero of=/dev/sda count=62 seek=1
```

If this does not help, I suggest to use dban to clear the hard drive and start all over again

---

### Post by ciscosurfer on 2008-11-22
@theamber,

What happened when you tried to repair the MBR using the Vista installation disc?

*jimreynold2nd* mentioned a header checksum error but I don't see anything in your posts about a checksum error--did you edit this information out of your first post?

If you're using the Live CD, you can install **gparted** from the repos and effectively wipe your drive (and MBR) using this utility.```
sudo apt-get install gparted
```

Even though this computer is releatively new, it is possible the drive is just bad/faulty.  Is this computer still under warranty?

---

### Post by theamber on 2008-11-23
> **ciscosurfer said:**
> @theamber,

What happened when you tried to repair the MBR using the Vista installation disc?

*jimreynold2nd* mentioned a header checksum error but I don't see anything in your posts about a checksum error--did you edit this information out of your first post?

If you're using the Live CD, you can install **gparted** from the repos and effectively wipe your drive (and MBR) using this utility.```
sudo apt-get install gparted
```

Even though this computer is releatively new, it is possible the drive is just bad/faulty.  Is this computer still under warranty?

I really apreciate all teh help this comunity is great.
Yes I get the checksome error is in the sencond or third post but only if there is a CDrom inserted. The windows live cd does try to fix it but get errors in the drive. I will try this commands and see what happens.

---

### Post by theamber on 2008-11-23
I am running it.... Gparted

---

### Post by theamber on 2008-11-23
I deleted the particion it formats and all but when I do check it said errors.
I will try to install ubuntu to see if it works.

---

### Post by la3875 on 2008-11-23
theamber, 

Here's a link to a great resource in the community- 

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

I recently used this to repair my MBR, and remove the previous version of Ubuntu from my laptop that I am dualbooting. Once I had repaired and wiped the second partition, I reinstalled and can't be happier with the outcome. 

I've also used the references for dual booting my desktop machine to two hard drives to keep family harmony.

All the best!

---

### Post by theamber on 2008-11-23
I tried but it does not work.
I bought a hard disk and as soon as I turned on the computer I saw this message:
Grub loading 1.5
error 17.
This hard disk never had linux.
I think grub got into my bios also in both hard disks happen the same thing ubuntu cannot install finds X server particion errors, windows install with errors. when I format them there are about 64 mb used always I can't delete that.
Can I flash the bios under the live CD?
I have the latest version in my bios.

---

### Post by jimreynold2nd on 2008-11-23
Sorry guys, 
Like meiefra said, I have no idea why GrUB is still there by looking at the MBR dump :confused:, it does look like a repaired Windows MBR to me.

And you have only one partition.

Can you try 
```
sudo dd if=/dev/sda1 of=sda1.mbr bs=512 count=1
```
and post the sda1.mbr file?

Meanwhile, you can do
```
sudo dd if=/dev/sda1 bs=512 count=1 | hexdump -C
```
and look at the bottom to see if there is the word "BOOTMGR" or "GRUB" anywhere. If there is no "GRUB", then this is the best I can do :( I don't deal with ghosts....

---

### Post by jimreynold2nd on 2008-11-23
EDIT: Do this first before doing suggestions in my last post. Try unplug the old hard drive, to see if GrUB is still there o.o. AFAIK, GrUB doesn't touch your BIOS:confused:

Make sure: No USB flash drive is plugged in, no memory card is in any reader, no CD in drive, no hdd except for the new one, no printer plugged in (those with card readers).

If GrUB still shows up, try disabling Intel Turbo Memory Cache in your BIOS setup.

The last one might be the culprit, it acts as a flash drive for Vista's ReadyBoost and GrUB *might* have written something to it.

---

### Post by theamber on 2008-11-23
> **jimreynold2nd said:**
> Sorry guys, 
Like meiefra said, I have no idea why GrUB is still there by looking at the MBR dump :confused:, it does look like a repaired Windows MBR to me.

And you have only one partition.

Can you try 
```
sudo dd if=/dev/sda1 of=sda1.mbr bs=512 count=1
```
and post the sda1.mbr file?

Meanwhile, you can do
```
sudo dd if=/dev/sda1 bs=512 count=1 | hexdump -C
```
and look at the bottom to see if there is the word "BOOTMGR" or "GRUB" anywhere. If there is no "GRUB", then this is the best I can do :( I don't deal with ghosts....
I turned off the power during an installations all kind of things can happens.
where is that file on the first code it copied but it is not on the desktop.
When I try to install Ubuntu particion x server x problems the exact same thing in both hard disks.

---

### Post by jimreynold2nd on 2008-11-23
> where is that file on the first code it copied but it is not on the desktop
It's in your current working directory (likely your home folder)
If you cant find it try:
```
sudo dd if=/dev/sda1 of=~/Desktop/sda1.mbr bs=512 count=1
```
then it will be on your desktop.

Did you read my last post?

---

### Post by theamber on 2008-11-23
Could grab be in the CDrom Bios?

---

### Post by jimreynold2nd on 2008-11-23
> Could grab be in the CDrom Bios?
No. CDrom drives don't have BIOS o.o

---

### Post by theamber on 2008-11-23
Here is the file.
I am getting upload errors I will reboot.

---

### Post by ciscosurfer on 2008-11-23
Ooh. This is getting interesting. BIOS viruses/trojans do exist and have been known to cause a bit of trouble. If this is the case, you likely inadvertently allowed it access while running Windows. To install to the BIOS, it would have needed to flash itself onto the BIOS. Some people say that the general steps to remove said annoyance is to remove the CMOS battery, short the terminal leads, replace with a fresh BIOS, wipe drive completely clean (there are so many cleaning tools to do this, many we've mentioned already). 

All of this is speculative and would also depend on whether you're _absolutely sure_ nothing (no other disks, no usb drives, no flash sticks, _nothing_) is connected when attempting to load or run the OS.

---

### Post by jimreynold2nd on 2008-11-23
Easy steps first:
**_*MAKE SURE*_** you did those: Unplug your old HDD, just the new, blank one is plugged in. No cd in drive, no memory card in reader, no usb stick, no external harddrive plugged in, no USB hub.

Reboot to see if GrUB error 17 is still there.

If it is, try going to BIOS setup and disable Intel Turbo Memory Cache.

Reboot to see GrUB error 17 is still there.

If it is, then I have **no idea**

---

### Post by theamber on 2008-11-23
> **ciscosurfer said:**
> Ooh. This is getting interesting. BIOS viruses/trojans do exist and have been known to cause a bit of trouble. If this is the case, you likely inadvertently allowed it access while running Windows. To install to the BIOS, it would have needed to flash itself onto the BIOS. Some people say that the general steps to remove said annoyance is to remove the CMOS battery, short the terminal leads, replace with a fresh BIOS, wipe drive completely clean (there are so many cleaning tools to do this, many we've mentioned already). 

All of this is speculative and would also depend on whether you're _absolutely sure_ nothing (no other disks, no usb drives, no flash sticks, _nothing_) is connected when attempting to load or run the OS.

I think you got it I have some virus in the BIOS. In the early states i did got a virus warning and I did not have any installed.
It got written in teh new drive 65 mb. I have a lot of utilities for the Bios I will try those and at last i will remove the bios Battery but if it got in the Bios that will only reset it but would it erase the flashed virus?
I will work the Bios utilities that I have.
Thanks a lot to all of you that took the time to help me.

---

### Post by theamber on 2008-11-23
Removed Bios Battery and reset it the Bios.
I used Macaffe and F-prot (dos based) they do not find a hard disk.
Norton and other utilities got errors on the partition table "extended X partition" That is created by the Linux installation I think. Every time I deleted the partitions and format the drive for Windows or Linux and put any files it created that x partition and took some bytes. The installation CD ubuntu give me errors on that x server partition and don't install. The vista sometimes installs works ok for a few hours then start to give errors on the drive. finally does not boot anymore. Both drives are the same now.
I think this computer is wasted, it is a laptop and I cannot change the Bios. 
I may try as a last resort to reinstall the flash update (I have the Windows file) but how do I do that under the live CD?.
That is the last chance to save the computer I think since it has a Bios Virus.
Gparted or other programs after deleting creating particions always I find 68 mb that I cant delete.

---

### Post by theamber on 2008-11-23
This is exactly what happened to me:
[http://techrepublic.com.com/5208-11193-0.html?forumID=81&threadID=201438](http://techrepublic.com.com/5208-11193-0.html?forumID=81&threadID=201438)

 a web site tried to inspect my pc I could not close the window I did reset and then it got locked.

---

### Post by theamber on 2008-11-24
A partition is created by the virus from the Bios and is taking up some space as the x partition on the drive. I can't install ubuntu because it runs out of space, that partition can't be made any bigger but it can be made smaller (that will not help).
Is there any patches in order to install ubuntu?, I mean if man made it man can beat it. I checked online and is a very rare virus, not software for it yet that I know of and it affects ext2 and ext3.

---

