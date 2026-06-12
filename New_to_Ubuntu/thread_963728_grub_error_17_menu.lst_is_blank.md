---
title: "grub error 17: menu.lst is blank"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by rrh1 on 2008-10-30
i'm relatively new to the linux world.

machine is running ubuntu hh only.

followed the general instructions for the grub error 17, sudo fdisk -lu yields:

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd8f6105d

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   231817949   115908943+  83  Linux
/dev/hda2       231817950   234436544     1309297+   5  Extended
/dev/hda5       231818013   234436544     1309266   82  Linux swap / Solaris

then i run sudo gedit /boot/grub/menu.lst

and the file that comes up is blank.

i have no idea what to do from here.

Rh

---

### Post by phidia on 2008-10-30
I suspect that the reason the file is blank is because you are not typing the correct file name. 
It's always best to use command line completion-let the terminal auto complete the path name by typing just part of the path and pressing tab.

menu.lst has no #'s in it the character before the "s" is a lowercase "L".

---

### Post by rrh1 on 2008-10-30
the file name was typed correctly, i had been using an L and not a one.

is it correct that the function of this command is to simply open the menu.lst file that is in the file system partition in the /boot/grub folder? i decided to try to locate the file manually and my boot folder does not contain a grub folder. 

a search of the file system yields two files named

grub-menu.lst

in /usr/share/doc/memtest86+/examples and /rofs/usr/share/doc/memtest86+/examples

and two files named 

menu.lst

in /rofs/usr/share/doc/grub/examples and /usr/share/doc/grub/examples

Rh

---

### Post by rrh1 on 2008-10-30
(auto completion in terminal does not work past /boot)

so the files must be gone?

---

### Post by unutbu on 2008-10-30
If you are booting from the LiveCD, then the hda1 partition has to be mounted first:
```

sudo mount /dev/hda1 /mnt
gksu gedit /mnt/boot/grub/menu.lst
```

If that works and you would like help with the grub error 17, please post your menu.lst.

---

### Post by rrh1 on 2008-10-30
entering the first line replies with:

mount: you must specify the filesystem type

how do i do that?

---

### Post by Coreigh on 2008-10-30
I need a little clarification.

Are you in fact booting from the CD to make these repairs?

Which CD ? 8.04? or earlier?

---

### Post by rrh1 on 2008-10-30
i'm booting from an 8.04 CD, yes.

---

### Post by unutbu on 2008-10-30
Try
```

sudo mount -t ext2 /dev/hda1 /mnt
```

If that does not work, try
```

sudo mount -t ext3 /dev/hda1 /mnt
```

---

### Post by Coreigh on 2008-10-30
If you still get the filesystem type error you can use the partition editor (System >> Administration >> Partiton editor) To verify that the hard drive is associated with HDA. It could be SDA or HDB etc.

---

### Post by rrh1 on 2008-10-30
the same message comes up for both commands:

mount: wrong fs type, bad option, bad superblock on /dev/hda1, missing codepage or helper program, or other error
In some cases useful info is found in syslog - try dmesg | tail  or so

---

### Post by rrh1 on 2008-10-30
/dev/hda1 is marked as an "unknown" filesystem.

---

### Post by Duck2006 on 2008-10-30
You have to make the mount point first, be for you can mount the drive.

---

### Post by rrh1 on 2008-10-30
duck, i don't know what that means?

---

### Post by unutbu on 2008-10-30
GRUB error 17 means
```

17: Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.
```

(see [http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting](http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting))

It appears the problem is that your linux filesystem on /dev/hda1 has somehow become corrupted. Do you have any suspicion how this might have happened? Knowing this may give us a clue how to help you better.

Duck2006, /mnt is always available from the LiveCD and from a normal Ubuntu installation.

---

### Post by rrh1 on 2008-10-30
i have no idea how the filesystem could have been corrupted. i did nothing different from my regular use, mostly internet browsing and ipod sync. the computer is always on with an active internet connection. if i remember correctly - it has been a while, i got frustrated searching for a fix and just let it sit as a paperweight for a while - i went to the computer and it was turned off. i turned it on and got the grub error. no one else has access to said computer.

ideas?

---

### Post by kansasnoob on 2008-10-30
Have you just tried:

```
sudo grub
```

Then:

```
root (hd0,0)
```

Then:

```
setup (hd0)
```

Then:

```
quit
```

Then restart (remove Live CD when prompted) and see if it boots.

---

### Post by ciscosurfer on 2008-10-30
rrh1, as you begin to learn more about Linux and Ubuntu, I thought it would be helpful to point you to this "sticky thread" called [New to Ubuntu? Start here...]("http://ubuntuforums.org/showthread.php?t=801404") located at the top of the [Absolute Beginners page]("http://ubuntuforums.org/forumdisplay.php?f=326").

---

### Post by rrh1 on 2008-10-30
root(hd0,0) 

yields

Error 25: Disk read error

---

### Post by ciscosurfer on 2008-10-30
whoops #-o

---

### Post by ciscosurfer on 2008-10-30
This thread may also be useful: [http://ubuntuforums.org/showthread.php?t=715317](http://ubuntuforums.org/showthread.php?t=715317)

---

### Post by kansasnoob on 2008-10-30
> **rrh1 said:**
> root(hd0,0) 

yields

Error 25: Disk read error

This is sounding like a hard drive failure to me. But I could be wrong!

---

### Post by unutbu on 2008-10-30
You could try
```
sudo e2fsck -fv /dev/hda1
```
This will try to repair your ext2/ext3 filesystem.

When you run this command it might stop and ask if you want to repair/delete some inode. Typically, you just say yes in these situations. If this happens a lot however, it means that there is probably severe problems with the filesystem. If you see a lot of questions (more than 30?) press Ctrl-C Ctrl-C to break out of fsck. Report back here and we'll talk about data recovery techniques.

---

### Post by rrh1 on 2008-10-30
this is my sudo fdisk -l :

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd8f6105d

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14430   115908943+  83  Linux
/dev/hda2           14431       14593     1309297+   5  Extended
/dev/hda5           14431       14593     1309266   82  Linux swap / Solaris

---

### Post by kansasnoob on 2008-10-30
Read here:

[http://users.bigpond.net.au/hermanzone/p15.htm#25](http://users.bigpond.net.au/hermanzone/p15.htm#25)

---

### Post by kansasnoob on 2008-10-30
Had you made any recent hardware changes?

---

### Post by rrh1 on 2008-10-30
> **kansasnoob said:**
> Had you made any recent hardware changes?

no, none.

---

### Post by rrh1 on 2008-10-30
> **unutbu said:**
> You could try
```
sudo e2fsck -fv /dev/hda1
```
This will try to repair your ext2/ext3 filesystem.

When you run this command it might stop and ask if you want to repair/delete some inode. Typically, you just say yes in these situations. If this happens a lot however, it means that there is probably severe problems with the filesystem. If you see a lot of questions (more than 30?) press Ctrl-C Ctrl-C to break out of fsck. Report back here and we'll take about data recovery techniques.

here's what i got:

e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/hda1
Could this be a zero-length partition?

---

### Post by kansasnoob on 2008-10-30
> **rrh1 said:**
> no, none.

It's still remotely possible that it's a cable issue, but my bet's on a failing (failed) hard drive.

Is it possible that the hard drive was simply full? Had you been having some other errors just before the boot problem?

---

### Post by rrh1 on 2008-10-30
> **kansasnoob said:**
> It's still remotely possible that it's a cable issue, but my bet's on a failing (failed) hard drive.

Is it possible that the hard drive was simply full? Had you been having some other errors just before the boot problem?

the drive is nowhere near full, and i had no other errors.

---

### Post by kansasnoob on 2008-10-30
I truly fear that you've had a hard drive failure, but I could be wrong.

Hopefully someone smarter than I will jump in. I'll message someone and see if they're available to help.

---

### Post by rrh1 on 2008-10-30
glorious. is there any way to recover my data?

---

### Post by caljohnsmith on 2008-10-30
I would definitely agree with Kansasnoob; it really sounds like you have a hardware problem at this point, most likely your HDD obviously, but it could be something else. Is there any way you could swap that HDD into another computer to see if it makes any difference? 

Also, if you want to try and recover your data, you could use something like "[photorec]("http://www.cgsecurity.org/wiki/PhotoRec")" to see if it can recover any of your files. You'll need another drive to save all the files to though, and it will take quite a long time.

---

### Post by kansasnoob on 2008-10-30
> **rrh1 said:**
> glorious. is there any way to recover my data?

Don't freak out just yet! I messaged two of the smartest people I know about this. (meierfra and caljohnsmith)

Let's see if they're available and have any ideas.

There are many others smarter than me about this stuff!

---

### Post by caljohnsmith on 2008-10-30
I was also thinking, in case you can't swap that HDD into another computer, I would recommend at least checking its health with some HDD diagnostic tools; if you don't happen to have a diagnostics CD that came with your HDD, you can download and use the [Ultimate Boot CD]("http://www.ultimatebootcd.com"), because that has lots of comprehensive HDD tests. Let us know what it reports if you run the tests.

---

### Post by rrh1 on 2008-10-30
> **caljohnsmith said:**
> I would definitely agree with Kansasnoob; it really sounds like you have a hardware problem at this point, most likely your HDD obviously, but it could be something else. Is there any way you could swap that HDD into another computer to see if it makes any difference? 

Also, if you want to try and recover your data, you could use something like "[photorec]("http://www.cgsecurity.org/wiki/PhotoRec")" to see if it can recover any of your files. You'll need another drive to save all the files to though, and it will take quite a long time.

the problem hard drive is in one of two laptops i own - for general use, a gateway that originally ran windows xp - the other is a macbook pro that i use for photographic work and don't want to touch.

i also have a desktop running ubuntu 8.04, into which there's no way to swap the laptop drive, correct?

third, i have an external hard drive that i could use for photorec or possibly as a usb boot, as one thread suggested.

---

### Post by ciscosurfer on 2008-10-30
rrh1, you can also test the overall health of the hard disk```
sudo apt-get install smartmontools

man smartctl

# Will test overall health of drive
sudo smartctl -H /dev/hda
```You may also want to check out an app called **testdisk** (I've used it before successfully).  You can find out more about it [in this thread]("http://ubuntuforums.org/showpost.php?p=2952861"), and [this post in particular]("http://ubuntuforums.org/showpost.php?p=2952861&postcount=4").

---

### Post by rrh1 on 2008-10-30
SMART overall-health self-assessment test result: PASSED

still working on testdisk

---

### Post by meierfra. on 2008-10-30
You might also try to run "e2fsck" with alternate superblocks:


```
 sudo dumpe2fs /dev/hda1 |  grep superblock | awk {'print $4'}
```

This will return a bunch of numbers, like

0,
32768,
98304,
163840,
229376,
294912,
819200,
884736,
1605632,

Use these numbers with "e2fsck":

```
sudo e2fsck -b  32768 -fy /dev/hda1
```

If that fails:

```
sudo e2fsck -b  98304 -fy /dev/hda1
```

and so on.

---

### Post by ciscosurfer on 2008-10-30
rrh1, I failed to mention that the overall health assesment is based off of tests already run.  In other words, you'll need to run a few tests first using smartctl.  Go to the man page again, look for this section:  SMART RUN/ABORT OFFLINE TEST AND SELF-TEST OPTIONS: and then post back.  Check the EXAMPLES section, as there are numerous examples for you to use for various situations.

---

### Post by rrh1 on 2008-10-30
> **meierfra. said:**
> You might also try to run "e2fsck" with alternate superblocks:


```
 sudo dumpe2fs /dev/hda1 |  grep superblock | awk {'print $4'}
```



this returns:

dumpe2fs: Attempt to read block from filesystem resulted in short read while trying to open /dev/hda1

---

### Post by caljohnsmith on 2008-10-30
I wouldn't recommend using testdisk, because it can only help you repair a faulty partition table and a few other related features; also, that "PASSED" that you got from the smartctl program is from the last time a SMART test was run on your HDD, so it is not up-to-date. 

First do the following to save the current health status parameters of your HDD to a file:
```
sudo smartctl -a /dev/hda > ~/Desktop/HDD_health_before_test.txt
```
Then run:
```
sudo smartctl -t long /dev/hda
```
That command will immediately terminate while the HDD begins its self-test. You can monitor the progress with:
```
sudo smartctl -a /dev/hda | grep -A 1 -i "self-test execution status"
```
Once it says its done, then do:
```
sudo smartctl -a /dev/hda > ~/Desktop/HDD_health_after_test.txt
sudo smartctl -H /dev/hda
```
Let us know the results.

---

### Post by meierfra. on 2008-10-30
You can also use "testdisk" to locate the superblock.

Go to "System>Administration->Software Sorces" and enable all the repositories in the "ubuntu software" tab.

```
sudo apt-get install testdisk

sudo testdisk /dev/hda
```

Choose "proceed", "intel" and "advanced"

Select your ubuntu partition (hda1)   and then "Superblock"


This should list all superblocks. Use the numbers with "e2fsck" as in my previous post.

---

### Post by meierfra. on 2008-10-30
> I wouldn't recommend using testdisk, because it can only help you repair a faulty partition table

But it also lets you locate the super blocks, which can be used together with "e2fsck" to fix a filesytem.


I'm not sure right now whether it is a hard disk problem or a file system problem. So one might as well check out both possibilities.

---

### Post by ciscosurfer on 2008-10-30
@unutbu, @caljohnsmith, @meierfra.,

Good suggestions and methods all around :D

---

### Post by rrh1 on 2008-10-30
currently running the new SMART test, it's supposed to take another hour.

thanks everyone.

---

### Post by rrh1 on 2008-10-30
the SMART test was projected to take 89 minutes. it's now been about 110 and it still hasn't completed. the status command yields:

{ 121} The previous self-test completed having the read element of the test failed.

is this an error?

---

### Post by caljohnsmith on 2008-10-30
> **rrh1 said:**
> the SMART test was projected to take 89 minutes. it's now been about 110 and it still hasn't completed. the status command yields:

{ 121} The previous self-test completed having the read element of the test failed.

is this an error?
Unfortunately, yes, that is definitely an error; it's becoming more clear that your HDD is probably on its last legs. Although I suppose it's still possible that it could be a simple problem with the HDD cables or something of that sort. The only way you could find out though is by opening up your laptop, which you may have to do anyway if you are going to replace it.

---

### Post by rrh1 on 2008-10-30
the hard drive is set up so that it can be removed without opening the entire case. i took it out; all the pins are intact and there doesn't appear to be any damage to the cables, but i won't know for sure until i can take the entire thing apart, which i will do this weekend.

will post then.

Rh

---

### Post by bedes on 2009-09-02
hello, new to the forum and Linux.  I'm having the same issue, my menu.lst is blank.  Im hoping you guys can help me out to resolve the issue.  Right now Im booting off a live CD - Linux Mint 7 to access a terminal.  I had Ubuntu 9.04 installed before I removed it.  I dont have Ubuntu 9.04 on a CD, so Im using Linux mint and its working.  sdc1 is a USB drive.

here is the output from fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2cf04d55

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   739713015   369855484    7  HPFS/NTFS
/dev/sda2       739728990   949425434   104848222+   5  Extended
/dev/sda3       949428224   976766975    13669376    7  HPFS/NTFS
/dev/sda5       940814658   949425434     4305388+  82  Linux swap / Solaris

Disk /dev/sdc: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              38     7839719     3919841    b  W95 FAT32

Where do I go from here?
bedes

---

### Post by bedes on 2009-09-02
nevermind,  I just installed Mint on the blank partition and it fixed everything.  

:popcorn:

---

