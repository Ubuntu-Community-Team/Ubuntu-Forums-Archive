---
title: "HOWTO: Tweak your ext3 filesystem for a performance boost"
date: 2005-12-24
forum: Outdated Tutorials &amp; Tips
---

### Post by GoldBuggie on 2005-12-24
I'm using an old 900MHz Toshiba Laptop and these below changes changed my system quite noticable. You should feel an increase in video, image or audio usage.

Linux has several choices of filesystems. Two quite known filesystems are ext3 and ReiserFS. This following howto **works for both** those two filesystems. 

The ext3 filesystem provides more journaling which makes it "safer" and recovery of files in case of a crash is more likely. This has its price in performance thou. ReiserFS is a faster filesystem but with less safety. The default for ubuntu systems is ext3.

Ext3 & ReiserFS has three kinds of journaling methods:
[COLOR=Blue]**1)**[/COLOR] Journal Data Writeback
[COLOR=Blue]**2)**[/COLOR] Journal Data Ordered
[COLOR=Blue]**3)**[/COLOR] Journal Data

I don't want to explain them to much here but the difference of the three is when the actual data is written to the filesystem in relation to the metadata and its entrance into the journal.

By default the the 2nd method is used.

To speed things up we will make it use method 1. The price to pay is that it may allow old data to appear in files after a crash and journal recovery. That is the last things you wrote or did prior a crash isn't recovered. (I can live with that, since I the most recent things I often have in my head and can reproduce)


[COLOR=Green][B]How to make ext3 or reiserfs use journal data writeback

[/B][/COLOR]```
sudo kate /etc/fstab
``` Add the thing marked in bold to your fstab root mount line.
```
/dev/hda1 / ext3 defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid,nouser**,data=writeback** 0 1
``` Save that file and change the following file```
sudo kate /boot/grub/menu.lst
```Change the following two lines by adding the following marked in bold
```
# defoptions=quiet splash **rootflags=data=writeback**
# altoptions=(recovery mode) single **rootflags=data=writeback**
```Now run ```
sudo update-grub
``` and the added flags will automatically be added to the kernel line and stay there in case of kernel update*(thank you reet for this method)*

[COLOR=Red](There have been reports of problems when rebooting if the following is _not_ done)[/COLOR] [COLOR=DarkRed]Note! tune2fs only works for ext3. Reiserfs can't change the journal method on the fly.[/COLOR]
Before rebooting change the filesystem manually to writeback.
```
 sudo tune2fs -o journal_data_writeback /dev/hda1
``` Check that it is running
```
 sudo tune2fs -l /dev/hda1
``` 
That's it. However I have one more thing I would recommend changing.


**[COLOR=Green]Remove update of access time for files[/COLOR]**

Having the modified time change I can understand but having the system updating the access time every time a file is accessed is not to my liking. According to the manual the only thing that might happen if you turn this off is that when compiling certain things the make might need that info. (I haven't seen a compilation that needs it yet and if I somehow come across it I will change this back or look into that then, but it is such a rare case)

To change this do the following:
```
 sudo kate /etc/fstab
``` add the following marked in bold(not that you might have the switch that enables it)
```
/dev/hda1 / ext3 defaults,errors=remount-ro,**noatime**,auto,rw,dev,exec,suid,nouser,data=writeback 0 1
``` 
Now reboot and enjoy a much faster system:D

---

### Post by viscount on 2005-12-26
Cool howto, but I use reiserfs.

I wonder if there is anyway to speed up reiserfs?

---

### Post by reet on 2005-12-26
You can apply the noatime option to your reiserfs partitions in fstab.

---

### Post by GoldBuggie on 2005-12-26
Well...I didn't want to mention to much about reiserfs since I haven't tried anything on it yet. I'll install it in about 2 weeks. But according to the documentation of reiserfs kernel 2.6.X the above howto should work and make it faster as well.

Not that I have not tried it but I would be happy to see someone try it before me:D and report back here. Then I'll change the howto so that it includes both popular filesystems.

---

### Post by MetalMusicAddict on 2005-12-26
Looks cool. Ill use this on non-system (storage) drives. :)

---

### Post by GoldBuggie on 2005-12-26
> Looks cool. Ill use this on non-system (storage) drives.
Enjoy the ride!:cool:

---

### Post by viscount on 2005-12-28
[QUOTE=reet]You can apply the noatime option to your reiserfs partitions in fstab.[/QUOTE]

Looked it up, yeah shouldn't cause any trouble and perhaps increase
performance.

---

### Post by xyz on 2005-12-28
Thanks a lot, GoldBuggie...amazing difference on my system!
Happy New Year.

---

### Post by kaamos on 2005-12-28
Whoa, I knew I had damn small linux on a usb-stick for a reason. ;)

System no more booted and gave errors "read only filesystem". Got it back running by undoing the changes but I couldn't find any typos or anything in either fstab or in menu.lst. Unless the fstab line for the filesystem needs more options than these?
> /dev/hda3       /               ext3    defaults,errors=remount-ro,noatime,data=writeback 0       1


---

### Post by bikeboy on 2005-12-28
I had the same problem.

Another way to rescue is to reboot into recovery mode, when it gets you to the CLI type:

mount -o remount,rw /dev/hdXX /

hdXX being your hard drive partition. This will allow you to edit the fstab and menu.lst to undo the chnages.

Now if I could just work out what's going wrong, time for bed me thinks...leave it until tomorrow.

---

### Post by a8ne on 2005-12-28
Same problem here.  Almost everything fails (write only file system warning) and then it hangs on "Starting logging daemon".  Oh well.

---

### Post by GoldBuggie on 2005-12-28
> System no more booted and gave errors "read only filesystem". Got it back running by undoing the changes but I couldn't find any typos or anything in either fstab or in menu.lst. Unless the fstab line for the filesystem needs more options than these?I haven't had any boot trouble so I can't give any advice which I know will work. The above howto is how I exactly have it in my menu.lst and fstab; remember not to copy the whole meny.lst since I use the i686 kernel.

Also if you want you can try and first manually overide the writeback and then  maybe add it to fstab and menu.lst.

To manually change the filesystem:
```
sudo tune2fs -o journal_data_writeback /dev/hda1
```

Check that it is running by
```
sudo tune2fs -l /dev/hda1
```



> Thanks a lot, GoldBuggie...amazing difference on my system!
Happy New Year.:KSA HAPPY NEW YEAR TO YOU AND TO ALL!:KS

---

### Post by GoldBuggie on 2005-12-28
**[kaamos]("http://ubuntuforums.org/member.php?u=44487")**
You can try and add som of the things that I have on my fstab line.

---

### Post by bikeboy on 2005-12-28
[QUOTE=GoldBuggie]
Also if you want you can try and first manually overide the writeback and then  maybe add it to fstab and menu.lst.
[/QUOTE]

This made the difference for me. I enabled writeback using tune2fs like you said. Then I edited the fstab and menu.lst files before rebooting so that writeback would be enabled when I booted again. No more errors!!! I checked and it is running :)

I think the problem is that when you change the config files without writeback already enabled the system chucks a fit on shutdown, triggering the read only mounting on reboot. I know I recieved errors just before shutdown but had no time to read them.

Why it happens to some people and not others I have no idea, I'm still only just learning.

Thanks for your help Goldbuggie

---

### Post by reet on 2005-12-28
This is a good HOWTO, however I don't agree with your methods of editing the grub menu.lst file. If the kernel were to change, grub would be reconfigured and your writeback settings would be lost. The writeback option should be applied to the commented options section of the menu.lst file. Look at the text between "##Start Default Options##" and "##End Default Options##". The actual uncommented grub menu should not be altered. Below is an example of what the menu.lst will look like on most systems: (altered lines have been highlighted in red)
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		2

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
[COLOR="Red"]# altoptions=(recovery mode) single rootflags=data=writeback[/COLOR]

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
[COLOR="Red"]# nonaltoptions=quiet splash rootflags=data=writeback[/COLOR]

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-10-k7 
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.12-10-k7 root=/dev/hda4 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-k7
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-k7 (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.12-10-k7 root=/dev/hda4 ro single 
initrd		/boot/initrd.img-2.6.12-10-k7
boot

title		Ubuntu, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows XP Professional x64 Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```
When this is done, save the file and run "sudo update-grub" to change the grub menu accordingly. The reason this is so important, is when a package is installed that changes the grub menu (such as installing a different kernel), the update-grub command is used which changes the grub menu according to the options in the commented section.

---

### Post by muchmusic on 2005-12-29
Excellent writeup. Interestingly, this works on ppc without any modification to the bootloader. I did have to run the tune2fs commands though, which makes sense. Thanks!

---

### Post by reet on 2005-12-29
Just because you said that, I had to know for myself. Sure enough, the bootloader does not need to be modified in order for this to work.

---

### Post by GoldBuggie on 2005-12-29
First: Could and admin change the main title to the following: [B]General - HOWTO: Tweak the ext3 or reiserfs filesystem for a performance boost
[/B][B]
Reet:[/B] Thank you for pointing out the grub menu thingy. I didn't know about how that worked. I added it to the howto and gave you recognition

I do know that the method seems to work without the adding to the grub but from what I've read and looked I can't fully explain why it is needed. When I myself discovered about this tweak from the manual I read some things about it and the grub thingy was mentioned. So I will keep it there for completeness or until someone can give me an explenation of why to remove it. Meaning why it is there in the first place. I didn't want to submit an howto which wasn't more or less fullproof.

Thanks again

---

### Post by meborc on 2005-12-29
ok, tried it yesterday and found miselt doing a format to my comp... had some failiors doing bootup... it would have been OK if the CLI could have turned up :rolleyes: but it didn't... tried many times... comp just hanged, didn't respond... safe mode didn't help either... nor the live cd, which of course hanged on boot aswell...

:D ... now back to original ubuntu install... i made a record installing full ubuntu in under an hour on my duron 800 MHz machine... jippii

---

### Post by Nano on 2005-12-29
I think I'll have a try in non-system partitions.
Thx

---

### Post by xyz on 2005-12-30
Hi everyone and thanks for this great help/howto.
When I run the following I get this:
```
th@ubuntu:~$ sudo tune2fs -o journal_data_writeback /dev/hda1
tune2fs 1.38 (30-Jun-2005)
tune2fs: Bad magic number in super-block while trying to open /dev/hda1
Couldn't find valid filesystem superblock.

```

and GoldBuggie wrote:
> (There have been reports of problems when rebooting if the following is not done)
Before rebooting change the filesystem manually to writeback.

I'm a newbie and I would apprciate any help you'd pass on to me.
From what I understand, it seems important to run sudo tune2fs....and I don't understand what is meant by "bad magic number" and what can be done to fix this?

---

### Post by Shin Natsume on 2006-01-15
to my horror it deleted the windows partition from the grub menu on my friends pc, luckily enough i saved a copy of the grub menu b4 hand, so all i have to do is add the info into the the new menu.lst

ciao

---

### Post by Brando569 on 2006-01-18
[QUOTE=xyz]Hi everyone and thanks for this great help/howto.
When I run the following I get this:
```
th@ubuntu:~$ sudo tune2fs -o journal_data_writeback /dev/hda1
tune2fs 1.38 (30-Jun-2005)
tune2fs: Bad magic number in super-block while trying to open /dev/hda1
Couldn't find valid filesystem superblock.

```


I'm a newbie and I would apprciate any help you'd pass on to me.
From what I understand, it seems important to run sudo tune2fs....and I don't understand what is meant by "bad magic number" and what can be done to fix this?[/QUOTE]

the bad magic number error is because hda1 isnt your root (/) partition. look in your /etc/fstab file and look for a forward slash (/) and see what drive/partition it corresponds to. that should fix it :D

---

### Post by benplaut on 2006-01-18
looks like a decent chance of problems... i'll skip.

/me waits for dapper to download... i want reiser on that install!

---

### Post by syuusuke on 2006-01-18
do i just use this command to reverse the tune2fs setting?
sudo tune2fs -o journal_data_ordered /dev/hda1

---

### Post by GoldBuggie on 2006-01-18
> do i just use this command to reverse the tune2fs setting?
sudo tune2fs -o journal_data_ordered /dev/hda1
That and removing the fstab and grub changes will do it.
> 
/me waits for dapper to download... i want reiser on that install! Everyone has his or her choice but I've noticed that on some commands ext3 is noticably faster then reiserfs. So reiserfs doesn't mean a faster filesystem. It just means different fs. It all depends on your need and what you do to your system. ext3, reiserfs & xfs are all good fs. I currently have reiserfs on this install but I will change on next install since for me I have found some things that isn't to my liking. But to each his own.

Cheers

---

### Post by quadomatic on 2006-01-18
this is proly a really stupid question (im a total noob:confused: )

when i do sudo kate /etc/fstab, it says kate isn't a command. im using ubuntu 5.1....is kate a kubuntu only command or something?

---

### Post by southernman on 2006-01-19
Your correct, Kate is KDE specific. You'd need to run:

sudo nano /etc/fstab

you could also do

sudo gedit /etc/fstab

The latter may be more user friendly if you've not used command line editors before.

---

### Post by quadomatic on 2006-01-19
nm, i figured out kate was kde text editor. i just used gedit. suprisingly, i didn't screw up my system!:D I'm not sure yet how much faster its running....

do i need to worry about something happening if i update the kernel? or should i update it with no worries?

---

### Post by GoldBuggie on 2006-01-19
>  do i need to worry about something happening if i update the kernel? or should i update it with no worries? Update with no worries

---

### Post by Ainvar on 2006-01-20
Just applied your tweak to my Ubuntu 5.10 install on a Dell Laptop with a 100gig 7200rpm drive. It is a bit quicker.

---

### Post by GoldBuggie on 2006-01-20
> Just applied your tweak to my Ubuntu 5.10 install on a Dell Laptop with a 100gig 7200rpm drive. It is a bit quicker.Nice to hear it:D

---

### Post by DDM on 2006-01-21
I get the same error message as noted in this thread:
```
th@ubuntu:~$ sudo tune2fs -o journal_data_writeback /dev/hda1
tune2fs 1.38 (30-Jun-2005)
tune2fs: Bad magic number in super-block while trying to open /dev/hda1
Couldn't find valid filesystem superblock.
```

Note that this is on a reiserfs partition, hda1 is correct.

I did, however, get this to work on my desktop's ext3 partition, i noticed a huge speed improvement when using apt-get and synaptic, small improvements elsewhere. A straight up $cp stuff/ ~/Desktop/ took exactly the same amount of time, stuff/ had 1400 files and was 240MB.

---

### Post by autocrosser on 2006-01-22
I'm a PPC user & looking at the ppc of grub (yaboot), I don't get the same areas to change for writeback--any ideas??  I included the noatime (which was used in fstab with Yellowdog Linux) & am "slightly" faster:smile:

---

### Post by GoldBuggie on 2006-01-23
> I'm a PPC user & looking at the ppc of grub (yaboot), I don't get the same areas to change for writeback--any ideas?? Well..just changing your fstab will probably work but to answer your question: change the kernel line.(but this option will then get removed when updating your kernel)
```
 kernel          /boot/vmlinuz-2.6.12-10-686 root=/dev/hda1 ro quiet splash vga=792 devfs=mount **rootflags=data=writeback**
```

---

### Post by GoldBuggie on 2006-01-23
> I'm a PPC user & looking at the ppc of grub (yaboot), I don't get the same areas to change for writeback--any ideas?? Well..just changing your fstab will probably work but to answer your question: change the kernel line.(but this option will then get removed when updating your kernel)
```
 kernel          /boot/vmlinuz-2.6.12-10-686 root=/dev/hda1 ro quiet splash vga=792 devfs=mount **rootflags=data=writeback**
```

---

### Post by dcast on 2006-01-26
works great! definate performance boost on my p3 550. Thanks a lot :)

---

### Post by GoldBuggie on 2006-01-27
> works great! definate performance boost on my p3 550. Thanks a lot Super! Always nice to hear. :-D

---

### Post by Sionide on 2006-01-27
If the /etc/fstab file is for static drives. Where's the equivalent file for hotplug USB drives for example?? I want to make this change to my storage drives, as others have recommended doing.. But they're USB and don't show up in fstab when mounted..

---

### Post by jackwhite on 2006-01-27
Hi,

I'm going to try this on my computer over the weeked. I also have a super old Thinkpad 380ED which I'm fixing up for a friend. I've got Mepis on it, will this work on other distro's too?

---

### Post by GoldBuggie on 2006-01-27
> If the /etc/fstab file is for static drives. Where's the equivalent file for hotplug USB drives for example?? I want to make this change to my storage drives, as others have recommended doing.. But they're USB and don't show up in fstab when mounted..I would change the options in hal for this. If I remember correctly it is the file /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi which you need to change for this. Don't remember all the details. You will have to look it up in the manual for hal. Sorry that I can't be of more assistant here but it takes some time going thrue the hal info.

> I'm going to try this on my computer over the weeked. I also have a super old Thinkpad 380ED which I'm fixing up for a friend. I've got Mepis on it, will this work on other distro's too?
Yes it will work on other distro's. It is a filesystem thingy. Hence it will work on all linux.

---

### Post by autocrosser on 2006-01-27
Thanks Goldbuggie--I'm having some kernel problems in Dapper right now (still at the -15-11-smp)--So I can change my vmlinux-old & keep that unchanged for a while. I'll give it a go this weedend.....
 
[quote=GoldBuggie]Well..just changing your fstab will probably work but to answer your question: change the kernel line.(but this option will then get removed when updating your kernel)
```
 kernel          /boot/vmlinuz-2.6.12-10-686 root=/dev/hda1 ro quiet splash vga=792 devfs=mount **rootflags=data=writeback**
```[/quote]

---

### Post by dcstar on 2006-01-28
[QUOTE=GoldBuggie]
.......
Ext3 & ReiserFS has three kinds of journaling methods:
[COLOR=Blue]**1)**[/COLOR] Journal Data Writeback
[COLOR=Blue]**2)**[/COLOR] Journal Data Ordered
[COLOR=Blue]**3)**[/COLOR] Journal Data

I don't want to explain them to much here but the difference of the three is when the actual data is written to the filesystem in relation to the metadata and its entrance into the journal.
.......[/QUOTE]
For anyone that cares about the three different options:

(Taken from [http://www.nyx.net/~sgjoen/disk-5.html](http://www.nyx.net/~sgjoen/disk-5.html))
--------
Metadata, data that describes the structure of the files, is written in a journal to the disk. Note that there are 3 modes of operations for ext3fs.

**data=writeback**

    This is metadata-only journalling. File data is written back to the main fs lazily.

    After a crash and recovery the file integrity is intact but file content can be old.

    Normally this is the fastest mode.

**data=ordered**

    Here file data is written before metadata.

    After a crash and recovery the file integrity is intact and files contain correct, recent data.

    Normally this is only slightly slower.

**data=journal**

    All data (as well as to metadata) is written to the journal before it is released to the main fs for writeback.

    This is a specialised mode for cases where synchronous operations are required, such as for mail spools and synchronous NFS mounts.
--------

---

### Post by Mortimer on 2006-01-28
This went smoothy for me, no problems. What I recommend for beginners is to do it all exactly.

As far as the performance increase, it's hard to say if opening files is faster, because I don't think it is. Writing a lot of tiny files rapidly seems faster, though.

---

### Post by cws on 2006-01-28
I first tested this on my Ubuntu test machine (laptop) and everything went well. Then I unfortunately had the guts to apply this on my main Ubuntu desktop.

I did everything exactly like advised. When I rebooted, something went wrong. Some services (calculating module dependencies, network, loading modules) failed to start and it got completely stucked when trying to start the Log daemon.

Then I  rebooted to recovery mode to undo the changes made to *fstab* and *menu.lst*. But in my */etc/fstab* is a line "**errors=remount-ro**". So now the whole hda1 is read-only and I can't make any changes to those files. :neutral:  I'm sure there is a simple solution to this but I don't know what it is...

In spite of all, thanks for the howto. It atleast speeded up my laptop ;)

EDIT: ```
# mount -o remount,rw /
``` did for me.

---

### Post by duffydack on 2006-01-29
I have an external usb HD, i think its using write caching, how do i turn this off.  The windows equivalent to "optimise for quick removal" is what im looking for.

---

### Post by RAOF on 2006-01-30
[QUOTE=DDM]I get the same error message as noted in this thread:
```
th@ubuntu:~$ sudo tune2fs -o journal_data_writeback /dev/hda1
tune2fs 1.38 (30-Jun-2005)
tune2fs: Bad magic number in super-block while trying to open /dev/hda1
Couldn't find valid filesystem superblock.
```

Note that this is on a reiserfs partition, hda1 is correct.

I did, however, get this to work on my desktop's ext3 partition, i noticed a huge speed improvement when using apt-get and synaptic, small improvements elsewhere. A straight up $cp stuff/ ~/Desktop/ took exactly the same amount of time, stuff/ had 1400 files and was 240MB.[/QUOTE]
The reason why this doesn't work for reiserfs partitions is that "tune2fs" is the ext2/ext3 tuning program.  "reiserfstune" is the one you want for reiserfs, and it doesn't support the "-o journal_data_writeback" option.  In fact, it doesn't seem to support changing the journal style at all.  Maybe it doesn't need to be changed on-disc.

---

### Post by GoldBuggie on 2006-01-30
> The reason why this doesn't work for reiserfs partitions is that "tune2fs" is the ext2/ext3 tuning program. "reiserfstune" is the one you want for reiserfs, and it doesn't support the "-o journal_data_writeback" option. In fact, it doesn't seem to support changing the journal style at all. Maybe it doesn't need to be changed on-disc. I've tested the howto for reiserfs without using any tune2fs similar command and it worked for me.

---

### Post by ashrack on 2006-01-30
[QUOTE=GoldBuggie]I've tested the howto for reiserfs without using any tune2fs similar command and it worked for me.[/QUOTE]
M2

---

### Post by oleoleole on 2006-01-30
Ohh, this worked nice. And I'm was following the HowTo. 

Here is my setup, since I run more than 1 partitition.

For the root-partitition options in fstab, it's enough with this line:
```
/dev/hde1 / ext3  defaults,errors=remount-ro,noatime,data=writeback 0 1
```
defaults = Uses the default options that are rw, suid, dev, exec, auto, nouser, and async. Source: [http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html")

Since I've got more than one partitition, I added this in my /etc/fstab to:
```

/dev/hde5 /home ext3 defaults,noatime,data=writeback 0 2
/dev/hdf1 /home/ole/warez/videodisk1 ext3 defaults,noatime,data=writeback 0 2

```

And I did:

```

sudo tune2fs -o journal_data_writeback /dev/hde5; tune2fs -o journal_data_writeback /dev/hdf1
sudo tune2fs -l /dev/hde5 | grep "mount options"
sudo tune2fs -l /dev/hdf1 | grep "mount options"

```

And everything seems to work just fine.

You should be seing this line after doing the "tune2fs -l"

```

root@propell:/home/ole# tune2fs -l /dev/hdf1 | grep "mount options"
Default mount options:    journal_data_writeback

```

---

### Post by duffydack on 2006-02-02
[QUOTE=Sionide]If the /etc/fstab file is for static drives. Where's the equivalent file for hotplug USB drives for example?? I want to make this change to my storage drives, as others have recommended doing.. But they're USB and don't show up in fstab when mounted..[/QUOTE]


Me too... 
???

---

### Post by GoldBuggie on 2006-02-02
>      Quote:
                                                 Originally Posted by **Sionide**
                 *If the /etc/fstab file is for static drives. Where's the equivalent file for hotplug USB drives for example?? I want to make this change to my storage drives, as others have recommended doing.. But they're USB and don't show up in fstab when mounted..*
                                 
 

Me too... 
???As mentioned before I would change the setup for hal (/usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi) or maybe just maybe I would make a static point in fstab. You can see how your usb is currently mounted in /etc/mtab, Take that info, tweak it, and put it in fstab.

---

### Post by jpkotta on 2006-02-25
Good HowTo, though I'm not sure how much I got out of it.  I did a really simple (probably useless) benchmark: ```
time ls -R /
```

Before:
real	1m25.029s
user	0m3.207s
sys	0m6.069s

After:
real	1m19.654s
user	0m3.158s
sys	0m5.885s

Oh well, it's always fun to tweak stuff.

---

### Post by deathbyswiftwind on 2006-02-27
Dude thanks so much my quake 4 runs like a champ now!

---

### Post by jomtois on 2006-05-05
Thanks!  THis worked great for me per the how-to instructions.

---

### Post by GoldBuggie on 2006-05-05
Glad it worked out for ya:D

---

### Post by too_many_people on 2006-05-15
I really appreciate this HOW-TO.

Before:

```

sudo hdparm -t /dev/hda1

/dev/hda1:
 Timing buffered disk reads: 28 MB in 3.32 seconds = 8.44 MB/sec 

```

After:

```

sudo hdparm -t /dev/hda1

/dev/hda1:
 Timing buffered disk reads: 30 MB in 3.07 seconds = 9.76 MB/sec

``` 

I'm running an old laptop (433 MHz, etc.) and every little bit of speed helps.

---

### Post by xXx 0wn3d xXx on 2006-05-15
Does this work on Dapper because it worked great on Breezy. I assume it does but I don't really want to mess up my filesystem.

---

### Post by edwing on 2006-06-06
Good tip, thanks, worked like a charm and my laptop seems to load and run noticably faster.

---

### Post by ShayneOSU on 2006-06-06
[QUOTE=MasterChief1234]Does this work on Dapper because it worked great on Breezy. I assume it does but I don't really want to mess up my filesystem.[/QUOTE]

It seems to work great on Dapper so far.  It took my disk accesses in hdparm from 19MB/sec to 25MB/sec.  And things seem more responsive, too.  Nice tip here!

---

### Post by GoA on 2006-06-06
Yes it works.

---

### Post by elemental666 on 2006-06-07
Got another 1.75 MB/s on Dapper with ext3, thanks ^^

---

### Post by yopnono on 2006-06-07
Ok. I have tried this and I did noticed the downside of it.
I shutdown the machine by unplugging it from the poweroutlet :)

And on start, it did a recover from the journal.... it was old data. lost my firefox, thunderbird profile etc, etc.

So I did put it back to ordered and did a unplug just to test. it did recover from journal and it was not old data this time.

---

### Post by GoldBuggie on 2006-06-07
>  I shutdown the machine by unplugging it from the poweroutlet
Well loosing more data is the downside. This method of powerdown is a bit harsch but the fuze might go.
Since "data=..." changes when metadata is written to disc it effects how safely your data is saved. It is all a matter of preferences. 

My girl doesn't use the data= option since she wants to be sure everything is saved in case of a crash. She writes alot of documents and does not want to rewrite things.

It is all a trade off. For me the snappier computer was exactly what I needed.

---

### Post by trapanator on 2006-06-09
[QUOTE=GoldBuggie]change the following file```
sudo kate /boot/grub/menu.lst
```Change the following two lines by adding the following marked in bold
```
# nonaltoptions=quiet splash **rootflags=data=writeback**
# altoptions=(recovery mode) single **rootflags=data=writeback**
```Now run ```
sudo update-grub
``` and the added flags will automatically be added to the kernel line and stay there in case of kernel update*(thank you reet for this method)*[/QUOTE]

these options are not in my menu.lst anymore (Ubuntu Dapper Drake 6.06). And now?

---

### Post by GoldBuggie on 2006-06-09
use **defoptions**

---

### Post by trapanator on 2006-06-09
[QUOTE=GoldBuggie]use **defoptions**[/QUOTE]

I noticed that

> 
# altoptions=(recovery mode) single rootflags=data-writeback

is commented. It's correct?

---

### Post by GoldBuggie on 2006-06-09
yes...it is correct

---

### Post by Cirrocco on 2006-06-10
excellent how to, it works wonderfully for me.

I have a question though:
I mount additional harddrives (hdb1 and hdc1) using a script after successfully logging in.  I don't always want them mounted, therefore I don't want to place them in the fstab.  The script just says: "sudo mount /dev/hdb1 /media/hdb1".  is there a way to run this with the "noatime" condition?

---

### Post by GoldBuggie on 2006-06-11
```
sudo mount -o noatime /dev/hdb1 /media/hdb1
```

---

### Post by ekp on 2006-06-11
I tried you tweak and notice no difference to the existing system Dapper 6.0.  I can change settings in files back to original but what would be the code to redo journaling method to orginal or is that necessary?

---

### Post by GoldBuggie on 2006-06-11
removing the changes in fstab and/or menu.lst will revert back to default.

---

### Post by Cirrocco on 2006-06-12
Thanks, GoldBuggie

---

### Post by lzap on 2006-06-19
Please write somewhere not to remove comments in menu.lst! It doesnt work when you remove "#"...

And its *defoptions* now...

ps - and thanks :-D

update: it didnt work, dmesg shows: Cannot change options while remount (or similar)

---

### Post by Peepsalot on 2006-07-04
I found this thread linked from another thread about speeding up boot times.  I followed all the instructions and no problems occurred, but there was no difference in boot speed.  Takes about 60seconds before and after.

I would have tried a before/after "hdparm -t", but I didn't know about this command until I had already made the changes.  I can't tell if things are  faster really.  I guess some hardware configurations have more to gain than others.  Good howto though.

---

### Post by michaelt on 2006-07-09
(on a Toshiba Tecra 8100, running at 4-500MHz, running Ubuntu 6.06 LTS - Dapper - and quite stably...)

Performed this command:

 sudo hdparm -t /dev/hda3

with result:

 Timing buffered disk reads:   18 MB in  3.09 seconds =   5.83 MB/sec

Then performed this command:

 sudo tune2fs -c 12 -i 7d -o journal_data_writeback /dev/hda3

(sets max-mount-count=12, from 30, time-based-e2fsck=7days, journaling commit policy=writeback - the latter being the subject of this How-To..)

Immediately thereafter, performed:

 sudo hdparm -t /dev/hda3

 Timing buffered disk reads:   28 MB in  3.15 seconds =   8.89 MB/sec

Then, minutes later, with the system relatively quiescent, I repeated the same command several times in quick succession:

 Timing buffered disk reads:   28 MB in  3.15 seconds =   8.89 MB/sec
 ...  8.34 MB/sec
 ...  11.08 MB/sec
 ...  11.28 MB/sec
 ...  10.61 MB/sec

Sound - or looks - suspiciously like a big boost in buffered disk reads.

I then made the changes to /etc/fstab and to /boot/grub/menu.lst, as suggested in the first post to this thread. I followed up by running, as recommended:

 sudo update-grub

Since I had changed the journal commit policy to **writeback** prior to making the changes this thread is discussing, I verified (before rebooting) that the **writeback** policy was in effect (as per recommendation in this thread) using:

 sudo tune2fs -l /dev/hda3 | grep "mount option" 

Got back:

 Default mount options:    journal_data_writeback

I added the **noatime** option for the / partition in /etc/fstab, as per suggestion in this thread.

All seeming good, time to restart. But first:

 sudo hdparm -t /dev/hda3

 Timing buffered disk reads:   30 MB in  3.29 seconds =   9.11 MB/sec
 ...  10.44 MB/sec
 ...  9.82 MB/sec
 ...  10.22 MB/sec
 ...  12.43 MB/sec
 ...  12.50 MB/sec
 ...  12.58 MB/sec

Nice.

On reboot, once things have settled down a bit, I run:

 sudo hdparm -t /dev/hda3

 Timing buffered disk reads:   36 MB in  3.14 seconds =  11.45 MB/sec

I'm content. Or almost. I run, against the /home partition:

 sudo hdparm -t /dev/hda5

 Timing buffered disk reads:   18 MB in  3.10 seconds =   5.81 MB/sec

!

Re-iterate:

 ...  7.35 MB/sec
 ...  9.73 MB/sec
 ...  9.38 MB/sec
 ...  10.40 MB/sec
 ...  10.26 MB/sec
 ...  9.30 MB/sec

I guess I'll add the changes to /etc/fstab for that partition and see if the system seems even faster on reboot...

---

### Post by HAARP on 2006-07-10
Strange. As far as I can tell, you're only benching the raw device, without the file-system interfering.

---

### Post by michaelt on 2006-07-10
> **HAARP said:**
> Strange. As far as I can tell, you're only benching the raw device, without the file-system interfering.

Understood. I'm aware that the test is a proxy measure. Can you suggest another, more direct, means of testing the effect(s) of the writeback change under discussion?

The hdparm test, as recommended, should be run multiple times, as done. What I believe is relevant is not the later results in each series, but the first i.e. the first run on two different partitions gave results just below 6MB/sec. Roughly controlling for other factors (rebooting after making changes to fstab) yielded results 50% higher on first runs (machine fresh from startup). Is there no significance to this, relative to the subject of the thread?

Also interested to know: Does the hdparm test not use the file-system at all - i.e. is the reference 'under Linux', in the snippet below, unnecessary? Could the resulting (apparent) improvement suggested by the data be entirely attributable to the inclusion of the noatime option for the two partitions in fstab?

For reference, here's a snippet relative to the -t option of hdparm:

"[-t] displays the speed of reading through the buffer
cache to the disk without any prior caching of data. This mea&#8208;
surement is an indication of how fast the drive can sustain
sequential data reads under Linux, without any filesystem over&#8208;
head. To ensure accurate measurements, the buffer cache is
flushed during the processing of -t using the BLKFLSBUF ioctl."

Last question: should the above read "reading through the buffer
cache *from* the disk"?

---

### Post by skull_leader on 2006-07-10
It seems like I goofed up kinda bad on my fstab. I did something that made Ubuntu not able to load X-Server. It would be a quick fix copying fstab.backup to fstab... only, my entire filesystem is read-only.

Anyone know how to fix this problem?

---

### Post by GoBieN on 2006-07-10
As mentioned above in this thread:
Boot in recovery mode, then:
mount -o remount,rw /dev/hd??

Where ?? is your hd ;)

---

### Post by veli on 2006-07-10
I don't have the following line in my grub menu list:

# nonaltoptions=quiet splash rootflags=data=writeback

What should I do in this case?

Thanks,

---

### Post by Peepsalot on 2006-07-10
I didn't have that line either.  I think it is called defoptions now instead of nonaltoptions.  I edited this line in mine.
```
# defoptions=quiet splash rootflags=data=writeback

```

---

### Post by veli on 2006-07-10
Thanks Peepsalot, I'll try this.

---

### Post by oss_monkey on 2006-07-10
I tried using your method, and at first it didn't work. :mad: 

For some reason, during recovery mode, I ran tune2fs as root and now it works! I did get some error messages when I sudo'd it as the main user... ](*,) 

All in all, I think there is a difference. Not yet very noticeable, but there is, indeed. Good work. :)

---

### Post by veli on 2006-07-10
This tweaking worked for me. The system reboot with no problem. There is a bit improvement. Great work.

One more question: Can "noatime" be applied to FAT32 partitions?

---

### Post by GoldBuggie on 2006-07-11
>  One more question: Can "noatime" be applied to FAT32 partitions?
Alas no, it cannot. There isn't much you can do with FAT32 except to use it for a shared HD between Windows and XP.

---

### Post by Don_DiZzLe on 2006-07-11
Hi u might wanna check this out: [http://forums.gentoo.org/viewtopic-t-305871-highlight-ext3.html](http://forums.gentoo.org/viewtopic-t-305871-highlight-ext3.html) and if necessary update ur Howto accordingly

---

### Post by GoldBuggie on 2006-07-11
> Hi u might wanna check this out: [http://forums.gentoo.org/viewtopic-t...ight-ext3.html]("http://forums.gentoo.org/viewtopic-t-305871-highlight-ext3.html") and if necessary update ur Howto accordingly

Don't know what you are pointing at with "update accordingly" but I am fine with the howto as is.

Thank you anyway

---

### Post by ciscosurfer on 2006-08-09
> **GoldBuggie said:**
> ```
/dev/hda1 / ext3 defaults,errors=remount-ro,noatime,auto,rw,dev,exec,suid,nouser,data=writeback 0 1
```

I am aware of the benefits of the *noatime* option.  But why add: *auto,rw,dev,exec,suid,nouser* ?  The *defaults* options takes care of these including the option to *async*.  I did not read the entire thread and so I apologize if I'm missing something here regarding the specifics of writeback and journaling.

---

### Post by GoldBuggie on 2006-08-09
just add the noatime option...the other options was just there when I copy pasted from my fstab since I played around with different things at that time(or was it like that in default with earlier ubuntu, I don't remember). You should see that I put the noatime option in bold meaning that do not take notice about the other things.

Anyway...happy tweaking

---

### Post by Xk2c on 2006-08-26
Have a look at:
Some ext3 Filesystem Tips
[http://forums.gentoo.org/viewtopic-t-305871.html](http://forums.gentoo.org/viewtopic-t-305871.html)

and
[http://forums.gentoo.org/viewtopic.php?p=3252486#3252486](http://forums.gentoo.org/viewtopic.php?p=3252486#3252486)

also.  ;)

---

### Post by efreddi on 2006-09-03
Great HOWTO!
I really boosted the speed of my Dell Latitude C600 following this howto.
In my opinion it's worth to do it on a laptop since the battery will avoid any sudden power down, I would think twice instead on a desktop.

Thanks a lot!


Elia

---

### Post by GoldBuggie on 2006-09-03
> Great HOWTO!
I really boosted the speed of my Dell Latitude C600 following this howto.
In my opinion it's worth to do it on a laptop since the battery will avoid any sudden power down, I would think twice instead on a desktop.

Thanks a lot!


Elia
Happy you liked it:D

---

### Post by ferd on 2006-09-14
Amazing performance increase for a couple of lines of code. I found this while trying to solve another problem. The other problem remains, but who cares? I will be able to solve it in half the time because of this.\\:D/

---

### Post by mdan on 2006-09-16
Tried this on my 700mhz amd desktop numerous times, in different order, always booted readonly, and then it had trouble unmounting file systems on reboot, forcing a check of /dev/hdc7 (my root partition).

Is it possible I don't need the " rootflags=data=writeback" option in grub?

From what I understand, my system mounts / as read-only ext2 and later parses
/etc/fstab to remount it as ext3. Mightn't the "data=writeback" option be enough to enable this during the remount? 

Also, how much could performance be boosted by compiling my own kernel?

Thanks,
Dan

---

### Post by GoldBuggie on 2006-09-17
>  Is it possible I don't need the " rootflags=data=writeback" option in grub? You can live without this option. Just enabled it in fstab for the ext3 filesystem. Check to see that it is enabled thrue 
```
sudo tune2fs -l /dev/hda1
``` Replace /dev/hda1 with your ext3 partition

>  Also, how much could performance be boosted by compiling my own kernel?There are subjective and objective approaches and answers to this. But since I am a compile kernel freak I would go with compiling it. But the performance increase depends on what options you choose and you also have to consider for what type of system you are building it for.

For me there are some ubuntu defaults that I change since they try to cover a broader audience.

Also there are better memory inprint considerations to consider when compiling your own kernel. Smaller kernel = smaller inprint.

---

### Post by vbgunz on 2006-10-09
I have several questions. First is, my root partition is hda3 not hda1. This means, in your how to, where ever I see hda1, change it to hda3. I did this, is this correct?. I am not sure how much of a speedup I got on a two year old $600 box but the following is my results divided by 5 runs.
```
[FONT="Courier New"]$ sudo hdparm -tT /dev/hda3
/dev/hda3:
 Timing cached reads:   1242 MB in  2.00 seconds = 620 MB/sec
 Timing buffered disk reads:  101 MB in  3.00 seconds =  32.25 MB/sec[/FONT]
```

I am not sure if this is good, bad, fair or simply incorrect *but* those are my results. I've, done a bit of tweaking in the last couple of days on a new Edgy Eft install because *Nautilus* is extremely slow at traversing some directories on the root partition. I still haven't noticed anything to speed it up so I am still trying. My second question is, I've run tunefs -i *but* I am not sure about what it is I am reading.
```
[FONT="Courier New"]tune2fs 1.39 (29-May-2006)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          d0018f51-0ee6-4414-a142-0111cde0fab3
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal filetype needs_recovery sparse_super
Default mount options:    journal_data_writeback
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              1465920
Block count:              2929854
Reserved block count:     146492
Free blocks:              1954308
Free inodes:              1307743
First block:              0
Block size:               4096
Fragment size:            4096
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         16288
Inode blocks per group:   509
Last mount time:          Sun Oct  8 23:34:39 2006
Last write time:          Sun Oct  8 23:34:39 2006
Mount count:              22
Maximum mount count:      30
Last checked:             Wed Dec 31 19:00:00 1969
Check interval:           0 (<none>)
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               128
Journal inode:            8
First orphan inode:       817243
Journal backup:           inode blocks[/FONT]
```

Does anything appear off in relation to this how to or does all seem correct?

My third question is, I have my home partition separated from root.Do I have to do this how to again for my home partition OR should I just leave it alone?

Fourth question is, Whats the downside again? Some people say, old data might crop up on a crash or something *but* what is this old data? whats happening exactly? I mean, if I open a file, write to it and save it, it doesn't actually get saved when I save it? What is a possible case of where data might be reverted to something old? Does this inadvertently affect the home partition? Sorry for the so many part question :(

Thank you for your help and time on this, I really appreciate it!

---

### Post by GoldBuggie on 2006-10-09
> First is, my root partition is hda3 not hda1. This means, in your how to, where ever I see hda1, change it to hda3. I did this, is this correct?.That is a correct observation.
> I have my home partition separated from root.Do I have to do this how to again for my home partition OR should I just leave it alone?You must do this configuration for that partition as well if you want the effects for the files on that partition as well. If it is benefitial or not depends on what you do but I'm guessing that the work and fun you do with your computer you mostly work with files in your home directory so applying this tweak to your home is maybe more important then doing it to root.

About using ```
[FONT=Courier New]hdparm -tT[/FONT]
``` for testing the difference....I would say that the test that hdparm -tT provides is not an accurate test for this tweak. You need a tool that stresses the filesystem more.

I've done some tests using bonnie++(which lies on my internal wiki, must get a provider for my wiki as a christmas gift:-D) which is a better and more accurate tool for this job.

> My second question is, I've run tunefs -i *but* I am not sure about what it is I am reading.Just note that 
**[FONT=Courier New]Default mount options: [/FONT]**[FONT=Courier New]says [/FONT][FONT=Courier New]**journal_data_writeback** so that you can reassure yourself that the filesystem tweak was applied.

[/FONT]> Fourth question is, Whats the downside again? Some people say, old data
might crop up on a crash or something *but* what is this old data? When using this method you are saying that the meatdata that the filesystem uses may be written before actual data. This means that data may be cached for some limited time before actually getting written to the HD. Which means that the cpu can work on other tasks and when those "other tasks" are finished or isn't so cpu intensive the cached data is written to disk. If your computer should crash before your cach has been flushed you will loose that data. You can tweak the time between metadata and cachflush if you want at the expense of speed. Thus if your computer crashed before a flush the "old" data will still be on the HD since the new data hasn't actually been written to the HD yet.

>  *Nautilus* is extremely slow at traversing some directories on the root partition
A last tweak that you might want to use is
```
tune2fs -O dir_index /dev/hda1
e2fsck -D /dev/hda1
```
This enabled the filesystem to use the b-tree algorithm for filesearching and may improve your responce time if you have many files and/or directories on your HD.

Hope this helps

cheers
GoldBuggie

---

### Post by vbgunz on 2006-10-09
Wow, I really didn't expect for you to answer every question :) I really appreciate it very much. Thank you :)

How exactly would you recommend running the last command "e2fsck -D"? I ask because I tried to run it but got this warning which is really scary:```
WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.
``` I didn't run it at all *but* how would I do it if I wanted too? I mean, how would I unmount the root partition and still have a useable box? Is it even possible? Thank you very much for your time and patience again!

PS. The only reason I went tweak crazy in the last couple of days is because of Nautilus. It really is very slow whereas everything is snappier than ever. Thanks again!

---

### Post by vbgunz on 2006-10-09
I think I just did it. I booted up with the livecd and ran it. It seemed to do something. I hope this was correct as I do not see any problems when booting back into the system.

Here is just one of the problems I see in Nautilus acting slow. Using the filetree on the left, I drop the arrows and navigate to /usr/share/ ... thats it, here is where it freezes. If I launch "gksudo nautilus", without changing its preferences at all, I have problems navigating to other directories like /proc and looking around. Other than Nautilus running slow, I am boggled about it as I constantly have 16 gui apps launching and running at lightening speed. This problem with Nautilus occurs either with all apps on screen or none at all. heh, I might just have to switch nautilus out for something else just to get the most out of Nautilus :)

Thanks for the tips and help, I really appreciated it!

---

### Post by GoldBuggie on 2006-10-09
running the command with a live cd is correct. sorry that i didn't write it in the previous post since it is hazardous. But good to see that you think or read warnings before pressing continue.

I hope you get to the bottom of your nautilus problems somehow.

---

### Post by louistan3 on 2006-10-13
cool... works great! :D

---

### Post by Mike_Longbow on 2006-11-03
Hi:

I have only one question: would this method work on a ext2 drive??? 
When I got this this drive it was somehow preformatted in ext2, and I've been using it normally without even noticed it :neutral: 

Greetings.
Mike

---

### Post by oleoleole on 2006-11-03
> **Mike_Longbow said:**
> Hi:

I have only one question: would this method work on a ext2 drive??? 
When I got this this drive it was somehow preformatted in ext2, and I've been using it normally without even noticed it :neutral: 

Greetings.
Mike

Convert your drive to ext3.

---

### Post by regeya on 2006-11-04
> **GoldBuggie said:**
> running the command with a live cd is correct. sorry that i didn't write it in the previous post since it is hazardous. But good to see that you think or read warnings before pressing continue.

I hope you get to the bottom of your nautilus problems somehow.

Heh, there's been a lot of explanation getting left out throughout the thread, so I wouldn't feel bad if I were you.  :D 

noatime - the atime attribute will not be updated when files are accessed.  a time sink more substantial than many people realize; if you want forensic data for after a break-in* then leave it on.

dir_index - huge difference on directories with huge numbers of files.  a word of warning - gui burners like serpentine seem to lean on the filesystem for putting tracks in the proper order.  i discovered this when I tried copying a cd for my wife to take to school; when she played it, the tracks were in random order.  workaround:  cdrdao.  you do indeed need to have the filesystem unmounted before doing a tune2fs -O dir_index && fsck -D.

I've changed the journaling options before, and back when I did it I was getting a minimal speed boost for a fair amount of headache.  I must try it again someday.  But to be honest, dir_index was the main thing I needed.  ext3 today is vastly superior to ext2--faster, speedy dir access, lower cpu usage; it's getting some of the benefit of reiserfs on a more stable codebase from a more stable developer.

*not that you should rely on anything to be accurate after you've been hacked, so turn it off anyway.

---

### Post by GoldBuggie on 2006-11-04
> Hi:

I have only one question: would this method work on a ext2 drive??? 
When I got this this drive it was somehow preformatted in ext2, and I've been using it normally without even noticed it :neutral: 

Greetings.
Mike
This method will not work with ext2 since ext2 is not a journaling filesystem. "noatime" will work since it has nothing to do with journaling.

---

### Post by SpEcIeS on 2006-11-05
That was a great set of tweaks. Thanks. :)

---

### Post by Don_DiZzLe on 2006-11-15
Does this howto also work for Edgy?

...and is it similar to this howto: [http://wiki.archlinux.org/index.php/Ext3_Filesystem_Tips](http://wiki.archlinux.org/index.php/Ext3_Filesystem_Tips) ?

---

### Post by GoldBuggie on 2006-11-15
it works for edgy...it has nothing to do with distro or version...it only depends on which filesystem you use.

---

### Post by esaym on 2006-11-15
Just to let the cat out of the bag here...

I have been doing alot of reading trying to figure out what kind of fs to use with ubuntu.  In short I will be doing a massive benchmark of filesystems sometime in the next month to see what all is what.

But in the mean time from what I gather a journalized filesystem is not so much for data integrity but for speed of recovery after an unclean dismount.  That reminds me of this one instructor I had a few years back.  He had what appeared to be a laptop with win2000 and fat32 installed.  Every morning when he would boot it up it would go to the check disk screen.  He would cuss at it and force it to exit before finishing.  This went on every day until about 6 months later he showed up to class with no laptop cussing saying that the hard drive had crashed and took all his data with it.

This seems to be the mentality of alot of people behind a computer.  Hence the reason a journalized file system came along.  Not so much for data integrity but for speedy recoveries after an unclean dismount.  We are all smart people here so why not do away with the journal all together if you don't mind a longer wait after an unclean mount:

```
tune2fs -O ^has_hournal /dev/hdXXX
```   

I have been using ext2 for several years with no data loss.  Some of the partitions have seen ALOT.  I have never had a problem with data loss.  The more I read the more it seems a journal does nothing for data and when corruption and data loss happens on a journalized system it happens on a much larger scale then on a system with no journal.  Ironically someone in this thread experienced data loss by simply unplugging their computer once.

I am not trying to start a flame war but I am looking for info and more opinions :p

---

### Post by BrowneR on 2006-11-24
> **esaym said:**
> from what I gather a journalized filesystem is not so much for data integrity but for speed of recovery after an unclean dismount.

I too have been using ext2 on my partitions for a year or so to enable easy data sharing with windows (which i seldom use by the way :p). It is all running fine although disk access does seem to be a bit of a bottleneck for me performance wise.

I guess things would only get worse if I converted to ext3 and added all the journalling overheads?

Those benchmarks you are doing [USER]esaym[/USER] sure would be interesting to see.

---

### Post by BrowneR on 2006-11-24
After a quick bit of googling i found [this]("http://linuxgazette.net/102/piszcz.html") benchmark of the most common linux filesystems. It seems fairly complete and the testing technique looks to stress the filesystem under various conditions.

ext2 seems to compare favourably with the more exotic xfs/jfs and so it seems logical to me that if you want some extra speed (possibly at the expense of crash recovery?) then convert from ext3 back to ext2 by removing the journal altogether. this way you still have a very well supported filesystem and some extra speed. possibly not the best idea for large disks as fsck times will increase dramatically in the case of a unclean umount.

---

### Post by esaym on 2006-11-27
I am aware of the benchmarks by Justin Piszcz.  They seem very well laid out and professional.  However I am really not so interested in which filesystem can create 10,000 empty files the fastest.  I plan on simply filling a 30gb partition about 45% full will typical desktop type files and then benchmarking how long it will take to copy all of the files out of that partition. Then I plan on repeating it again only filing the partition up to about 90% and then doing it again, this way it will test for how well fragmentation is handled.

Not the most professional method but I think it might shine some light. I just got to find time in the next few weeks to do it.

---

### Post by esaym on 2006-11-29
Well today I was digging around looking for some ideas on how to run my benchmarks and I came across lots of sites that have already done lots of testing.  It seems the more I research and think I have found the fastest filesytem, then the next thing I know is I come across a benchmark that flips my conclusions.

[http://linuxperf.sourceforge.net/iozone/iozone.php](http://linuxperf.sourceforge.net/iozone/iozone.php)

[http://kerneltrap.org/node/1054](http://kerneltrap.org/node/1054)

[http://fsbench.netnation.com/](http://fsbench.netnation.com/)
Looking at the combined tests and skipping to the total time numbers on the right of the graph shows jfs to be pretty strong most of the time.  Even though reiser has some of the highest read speeds it falls short in some other areas.

However right when you start to think jfs is the way to go you see this:

> I've been reading good thing about JFS and decided to try it on my spare 10G hard drive. Before each test I erased and created new partition with and used appropriate mkfs command to create jfs/reiser/ext3 file system.
I used reiserfs and extfs drivers included in stock 2.4.22 kernel. I downloaded latest JFS sources at that time (more than one week ago) and recompiled kernel.

test1: "time tar jxvf linux-2.4.21.tar.bz2"

JFS(worst) reiser3(best) ext3
real 2m57.296s 0m48.341s 1m22.625s
user 0m29.900s 0m30.470s 0m29.920s
sys 0m3.140s 0m3.900s 0m3.240s

test2: "time rm -r linux-2.4.21"

JFS(worst) reiser3 ext3(best)
real 1m48.794s 0m2.143s 0m0.627s
user 0m0.060s 0m0.030s 0m0.010s
sys 0m0.660s 0m0.880s 0m0.470s

test3: "time cp /mnt/somewhere/700MBfile.bin /mnt/test_partition"
(copy one large file from fast 80GB disk to 10GB test disk)

JFS(worst) reiser3 ext3(best)
real 4m29.414s 1m7.493s 0m58.911s
user 0m0.170s 0m0.130s 0m0.080s
sys 0m7.010s 0m7.800s 0m6.730s

Results speak for themselves. With work I do as a desktop user (uncompressing, compiling, and deleting large source trees and doing some multimedia stuff) JFS might be wrong choice. I'm using reiserfs and I'm quite satisfied with it.

regards

According to the comments left here: [http://linux.slashdot.org/article.pl?sid=06/01/06/1539235&tid=198](http://linux.slashdot.org/article.pl?sid=06/01/06/1539235&tid=198)

xfs and jfs are for enterprise solutions and do not take well to power loses, unclean mounts or kernal panics.  Apparently ext2&3 were made just for consumer level desktops.

I think I will stick with ext2 for now.  Once I get ubuntu up on my desktop it will be interesting how long a fsck will take on the 200gb disk in it vs the 40gb one in my laptop right now.

---

### Post by esaym on 2006-12-23
Well just an update I'm moving back to ext3 lol

I have been having some lock up problems on my desktop: [http://ubuntuforums.org/showthread.php?p=1904500#post1904500](http://ubuntuforums.org/showthread.php?p=1904500#post1904500)

Usually what happens after it locks and I force it off is all the small config files for kde that were loaded into memory get unattached from the inodes.  fsck will run and find them but since there is no journal to tell where the file goes it gets dropped into your lost+found folder.  So now you have a config file with a random number as a file name and you don't know where in the world it goes.  In the mean time you have all your themes, fonts and generally your whole desktop screwed up (visually).  I had a really bad lock up this morning.  I logged off and then logged back on and got a corrupt screen (I think it my video card) and I had to force it off.  Messed up a bunch of stuff and I have spent 2 hours trying to get my desktop visually back to the way it should be but I haven't had any luck.

In summary I am going to move all my computers to the writeback mode just like this excellent howto says:D 

Live and learn

---

### Post by esaym on 2006-12-23
Ok ext3 with data write back mode passes my data integrity test.  I just did a bunch of "horrible" things to it like pulling the plug, opening 20 applications and then forcing it off ect.  fsck never even ran.  Everything seems fine.:mrgreen:

---

### Post by raul_ on 2006-12-30
Hummm...oh well writing from the Live CD here :P i get this error when i tried to reboot:

```
/bin/sh : can't access tty ; job control turned off
``` and then it jumps to a built in shell and i can't do anything with it, not even undo the procedure...

stuck big time

---

### Post by raul_ on 2006-12-30
Back in business. Mounted my drive with the live CD and undid the changes there. I noticed that my filesystem is actually ext2 #-o (don't know how that happened, maybe because i haven't performed a clean install since Hoary?) bah...now i want ext3 :(

---

### Post by raul_ on 2006-12-30
Ok, converted to ext3 and now the tweak works. I can't see no real improvement though. I actually did this for fun :mrgreen: now i'm afraid that i'll lose my data with a power failure :-k maybe i'll switch to ordered journaling again

---

### Post by BoomerTPU on 2007-04-16
Hi I'm a linux newbie and I've read your guide.
I'm running Ubuntu 6.10 on an old P3-m 128mb ram machine. My problem is that when I type in the "sudo kate /etc/fstab" I get an error message saying something about the function kate doesn't exist. Do I have to install anything else before following this guide ?

Thanks for the help!

---

### Post by rsambuca on 2007-04-16
> **BoomerTPU said:**
> Hi I'm a linux newbie and I've read your guide.
I'm running Ubuntu 6.10 on an old P3-m 128mb ram machine. My problem is that when I type in the "sudo kate /etc/fstab" I get an error message saying something about the function kate doesn't exist. Do I have to install anything else before following this guide ?

Thanks for the help!

If you are using ubuntu (gnome interface), then you will need to the command```
gksudo gedit /etc/fstab
```

---

### Post by BoomerTPU on 2007-04-17
Thanks rsambuca!

But how come my fstab file looks nothing like the one describe in the guide?
Is it because the guide is written for another version of Ubuntu ? 

Thanks for the help.

---

### Post by OffHand on 2007-04-17
> **BoomerTPU said:**
> Thanks rsambuca!

But how come my fstab file looks nothing like the one describe in the guide?
Is it because the guide is written for another version of Ubuntu ? 

Thanks for the help.

Are you confused about the UUID= instead of /dev/sda  ?

---

### Post by esaym on 2007-04-17
I have actually ran into some data corruption from using writeback mode.  I was messing with some software and the computer locked.  After forcing it to reboot I had a lot of files missing.  Very similar to a crash with ext2.  I have not had any trouble with the ordered mode.

Like I said earlier in this thread: 

using ext2, a transfer from hard drive A to hard drive B had  a throughput of 50mBs
using ext3 writeback, a transfer from hard drive A to hard drive B had a throughput of 7-15mBs.

Same goes for ext3 in data ordered mode.   I could not see a speed difference between the 2.

EXT3 supports  external journaling so of course if you want to be 1337, you can always install another hard drive and direct all your partitions to use the other hard drive  for journal space.  This will give an ext3 partition similar performance to that of ext2.  Just search google for "ext3 external journaling"

---

### Post by goldenatom on 2007-04-20
Will this still work for 7.04?

---

### Post by GoldBuggie on 2007-04-21
> Will this still work for 7.04?The guide is independent of version number yes

---

### Post by beuh_dave on 2007-05-17
Using Feisty and it worked perfectly, I didn't have any problems on my PIII 600Mhz, it's much much faster now! It boots faster, programs load faster, it doesn't lag when I scroll down big webpages anymore... Not sure exactly why, but I'm very happy..

Thanks for the hack!

---

### Post by GoldBuggie on 2007-05-17
> Using Feisty and it worked perfectly, I didn't have any problems on my PIII 600Mhz, it's much much faster now! It boots faster, programs load faster, it doesn't lag when I scroll down big webpages anymore... Not sure exactly why, but I'm very happy..

Thanks for the hack!
Really happy it did some good for you. For lower spec machines you always need some extra boost with todays apps and this little tweak makes its usage just there. People who already have to much power on there hands doesn't notice anything of course, but strangley enough they are often the ones crying buh the first *hehe*

---

### Post by ciper on 2007-08-01
I wanted to post three things that could help everyone in this thread. 

First I think the following script is a more accurate way to test your disc speed since it uses file system access instead of direct disc access like HDPARM.
```
echo "start 50mb write"
time dd if=/dev/zero of=/var/testfile bs=50000k count=1
echo "start 50mb read"
time dd if=/var/testfile of=/dev/null bs=1000k
echo "size of file in kilobytes"
ls -k -s testfile | cut -d ' ' -f 1
rm /var/testfile
```
Replace instances of "/var/testfile" with whatever writable partition and random filename you want to test. I didnt use urandom because its not fast enough. If a disk doesnt contain a mountable/writable partition you can at least test read speeds with
"time dd if=/dev/hdb2 of=/dev/null bs=1000k count=50" (useful for the next hack...)

2. Although the change of options in the walkthrough did improve my speed slightly I got a MUCH higher imrprovement by running the following command at every boot. Edit to list all your hard drives. These settings are generic to most any OS but check your man page to be sure because on my Tivo the "-M" option controls streaming media mode instead of acoustic settings. To find the best setting for the "-m" option run "hdparm -i /dev/hda /dev/hdb" then look for MaxMultSect and use that number. The "-S" option prevents the drive from spinning down (disabling power management) which also helps extend drive life. The "-a" option controls read ahead and you may be able to set it higher (on some systems -a 1024 is best).
```
hdparm -a 255 -c 1 -d 1 -k 1 -m 16 -M 254 -S 0 -u 1 /dev/hda /dev/hdb
```


Last I don't know if anyone mentioned this but you can test the noatime option without rebooting with
```
mount -o noatime,remount /
or
mount -o atime,remount /
```

---

### Post by southernman on 2007-08-03
First off - @ GoldBuggie: Thank you for this hack. Although I am not running a laptop and my system is somewhat new (old by todays standards though) and pretty snappy, this hack DOES make a difference. 

Second - @ ciper (or anyone else that is in the know): Thanks for the hdparm tip. Just a quick question... 

After reading the man hdparm file, I've discovered the /etc/hdparm.conf file. Instead of having to pass these options after each boot, could you just edit/add your options to the configuration file? Or is there a specific reason this would be a bad idea?

Thanks for the help... in advance!

```
## This is the default configuration for hdparm for Debian.  It is a 
## rather simple script, so please follow the following guidelines :)
## Any line that begins with a comment is ignored - add as many as you 
## like.  Note that an in-line comment is not supported.  If a line 
## consists of whitespace only (tabs, spaces, carriage return), it will be
## ignored, so you can space control fields as you like.  ANYTHING ELSE
## IS PARSED!!  This means that lines with stray characters or lines that 
## use non # comment characters will be interpreted by the initscript.  
## This has probably minor, but potentially serious, side effects for your 
## hard drives, so please follow the guidelines.  Patches to improve 
## flexibilty welcome.  Please read /usr/share/doc/hdparm/README.Debian for 
## notes about known issues, especially if you have an MD array.
##
## Note that if the init script causes boot problems, you can pass 'nohdparm' 
## on the kernel command line, and the script will not be run.
##
## Uncommenting the options below will cause them to be added to the DEFAULT
## string which is prepended to options listed in the blocks below.
##
## If an option is listed twice, the second instance replaces the first.
##
## /sbin/hdparm is not run unless a block of the form:
##      DEV {
##         option
##         option
##         ...
##      }
## exists.  This blocks will cause /sbin/hdparm OPTIONS DEV to be run.
## Where OPTIONS is the concatenation of all options previously defined
## outside of a block and all options defined with in the block.

# -q be quiet
quiet 
# -a sector count for filesystem read-ahead
#read_ahead_sect = 12
# -A disable/enable the IDE drive's read-lookahead feature
#lookahead = on
# -b bus state
#bus = on
# -B apm setting
#apm = 255
# -c enable (E)IDE 32-bit I/O support - can be any of 0,1,3
#io32_support = 1
# -d disable/enable the "using_dma" flag for this drive
#dma = off
# -D enable/disable the on-drive defect management
#defect_mana = off
# -E cdrom speed
#cd_speed = 16
# -k disable/enable the "keep_settings_over_reset" flag for this drive
#keep_settings_over_reset = off
# -K disable/enable the drive's "keep_features_over_reset" flag
#keep_features_over_reset = on
# -m sector count for multiple sector I/O
#mult_sect_io = 32
# -P maximum sector count for the drive's internal prefetch mechanism
#prefetch_sect = 12
# -r read-only flag for device
#read_only = off
# -s Turn on/off power on in standby mode
#poweron_standby = off
# -S standby (spindown) timeout for the drive
#spindown_time = 24
# -u interrupt-unmask flag for the drive
#interrupt_unmask = on
# -W Disable/enable the IDE drive's write-caching feature
#write_cache = off
# -X IDE transfer mode for newer (E)IDE/ATA2 drives
#transfer_mode = 34
# -y force to immediately enter the standby mode
#standby
# -Y force to immediately enter the sleep mode
#sleep
# -Z Disable the power-saving function of certain Seagate drives
#disable_seagate
# -M Set the acoustic management properties of a drive
#acoustic_management
# -p Set the chipset PIO mode
# chipset_pio_mode
# --security-freeze Freeze the drive's security status
# security_freeze
# --security-unlock Unlock the drive's security
# security_unlock = PWD
# --security-set-pass Set security password
# security_pass = password
# --security-disable Disable drive locking
# security_disable
# --user-master Select password to use
# user-master = u
# --security-mode Set the security mode
# security_mode = h

# Root file systems.  Please see README.Debian for details
# ROOTFS = /dev/hda

## New note - you can use straight hdparm commands in this config file 
## as well - the set up is ugly, but it keeps backwards compatibility
## Additionally, it should be noted that any blocks that begin with 
## the keyword 'command_line' are not run until after the root filesystem
## is mounted.  This is done to avoid running blocks twice.  If you need 
## to run hdparm to set parameters for your root disk, please use the 
## standard format.

#Samples follow:
#First three are good for devfs systems, fourth one for systems that do 
#not use devfs.  The fifth example uses straight hdparm command line
#syntax.  Any of the blocks that use command line syntax must begin with
#the keyword 'command_line', and no attempt is made to validate syntax.  
#It is provided for those more comfortable with hdparm syntax. 

#/dev/discs/disc0/disc {
#	mult_sect_io = 16
#	write_cache = off
#	spindown_time = 240
#}

#/dev/discs/disc1/disc {
#	mult_sect_io = 32
#	spindown_time = 36
#	write_cache = off
#}

#/dev/cdroms/cdrom0 {
#	dma = on		   
#	interrupt_unmask = on
#	io32_support = 0
#}

#/dev/hda {
#	mult_sect_io = 16
#	write_cache = off
#	dma = on
#}

#command_line {
#       hdparm -q -m16 -q -W0 -q -d1 /dev/hda
#}
```

---

### Post by ciper on 2007-08-04
My original goal was to increase the speed of my Tivo. Because its an "embedded" device some standard features don't work. I didn't use the conf file because it doesnt exist on the Tivo and might not be supported.  You have no idea how hard it was to get a non standard swap partition working on HDB. The original kernel only supported version 0 swap, no lba48 support and you couldn't add additional lines to the FSTAB. Ill try that conf file in the next few days or so to see if it works.
 
I found a site that gives a better explanation of HDPARM than the man file if you wan't to take a look
[http://gentoo-wiki.com/HOWTO_Use_hdparm_to_improve_IDE_device_performance](http://gentoo-wiki.com/HOWTO_Use_hdparm_to_improve_IDE_device_performance)

For those of you adjusting the atime parameter I wanted to share this message with you
[http://oss.sgi.com/archives/xfs/2004-02/msg00009.html](http://oss.sgi.com/archives/xfs/2004-02/msg00009.html)

---

### Post by southernman on 2007-08-04
I thought you may be a gentoo-er! Going to have a read... Thanks ciper!

---

### Post by ciper on 2007-08-04
I run Windows XP, OSX 10.4.8 and ubuntu live on my Dell laptop. 

I found another tip that may be helpful regarding swap files/partitions. In the fstab or with swapon you can give each swap a priority from 0-100. The higher the number the sooner the OS will use it. If you set two swap partitions/files to the same priority the OS will write to both of them at the same time (like a software raid set).

It is helpful if you created a swap partition that is too small and want to add more space with a swap file. You can give the swap partition higher priority than the swap file so that it doesnt get used unless the system really needs it.

For example I had a 700mb swap partition on my B drive and a 127mb swap partition on my A drive. I set priorty 5 on /dev/hdb2 and priority 3 on /dev/hda8. This way swapping wouldn't compete with writes to the database on drive A until it had used up all the swap space on the B drive.

---

### Post by vexorian on 2007-08-10
I have only tried noatime and also nodiratime, the performance benefit is nice, nautilus takes much less time loading /home

---

### Post by ciper on 2007-08-12
This may sound like a stupid question but would the noatime parameter have any effect on a read only file system? It is possible to run the following command with success 
```
mount -o remount,ro,noatime /
```

Does anyone have tips on increasing the speed of a read only file system besides what I have already mentioned?

---

### Post by vexorian on 2007-08-12
> This may sound like a stupid question but would the noatime parameter have any effect on a read only file system?
nope, it is simply to prevent disk writes whenever you read a file, if the filesystem is read only it never writes to the disk.

Regarding success of using the option, I guess that's something you'd have to test, worst case scenario you'd get a complaint from the mount command

---

### Post by ciper on 2007-08-13
> **vexorian said:**
> nRegarding success of using the option, I guess that's something you'd have to test, worst case scenario you'd get a complaint from the mount command
In my prior post I was trying to say that setting noatime and ro was successful.
```
bash-2.02# mount
/dev/hda7 on / type ext2 (ro,noatime)
/dev/hda9 on /var type ext2 (rw)
/proc on /proc type proc (rw)
```

---

### Post by Bart_D on 2007-08-30
> **GoldBuggie said:**
> .........```
sudo update-grub
``` and the added flags will automatically be added to the kernel line and stay there in case of kernel update*(thank you reet for this method)*

[COLOR=Red](There have been reports of problems when rebooting if the following is _not_ done)[/COLOR] [COLOR=DarkRed]Note! tune2fs only works for ext3. Reiserfs can't change the journal method on the fly.[/COLOR]
Before rebooting change the filesystem manually to writeback.
```
 sudo tune2fs -o journal_data_writeback /dev/hda1
``` Check that it is running
```
 sudo tune2fs -l /dev/hda1
```.....

Should this be done before only the first reboot after the rest of the commands above it **and below it** were entered or should it be done before every reboot?

---

### Post by ArtF10 on 2007-08-31
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=afa3be73-e851-4336-87c5-b27e50dfe9ea /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=41a72100-52cc-4956-8466-c2c6350614c9 /media/hda1     ext3    defaults        0       2
# /dev/hda5
UUID=6127b952-4832-4445-8d8d-c1f2abff56a7 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

My root mount line in step 1 does not contain atime, auto, rw, etc.  The step requires me to add only the stuff in bold, but should I add the others (atime, auto, rw, etc.) as well?

---

### Post by Yes on 2007-08-31
If I were to decide that I didn't want/need this anymore, would I just go back and undo all the changes I made?

---

### Post by ArtF10 on 2007-08-31
It may be too late then....that's wherre I'm concerned.

---

### Post by filipe.rosset on 2007-10-15
time ls -R /

before
real    2m56.377s
user    0m2.596s
sys     0m4.912s

after
real    1m55.628s
user    0m2.228s
sys     0m4.796s

sudo hdparm -t /dev/sda1

/dev/sda1:
 Timing buffered disk reads:  116 MB in  3.03 seconds =  38.28 MB/sec

---

### Post by atlfalcons866 on 2007-10-16
is journal data writeback equilivent to the way jfs journals its data?

---

### Post by carlos1992 on 2007-11-07
hey can someone really explain this tweak the last part was the only i couldn't get it seems to be that you have to change the same line you have already written on but i don't know if i have to put the "," in there or what

---

### Post by knutschr on 2007-11-08
Thank you :)
Even though i have a 3.2 GH dual-processor and 1 GB RAM the speed of my Kubuntu Gutsy increased enormously!
I got an error it the two lasts commands (enabling writeback manually end check), so to reboot was exciting.
But no errors, and with an never before seen speed :)

---

### Post by neto07 on 2008-01-02
thank you very much for this tweak! my start up time according to bootchart is decreased from 2:49 to 1:31!! so almost twice as fast! thanks GoldBuggy

---

### Post by neto07 on 2008-01-02
> **carlos1992 said:**
> hey can someone really explain this tweak the last part was the only i couldn't get it seems to be that you have to change the same line you have already written on but i don't know if i have to put the "," in there or what

Hi carlos1992,
as for how I understood it: yes, it is the same line. and I put the "," to separate the "words" (I'm a linux newbie, don't know how to call it... ) from each other. it worked for me! buena suerte!

---

### Post by artti on 2008-02-24
What i should do when i have /dev/sda1 instead of /dev/hda1?

---

### Post by Tarlak on 2008-02-29
> **artti said:**
> What i should do when i have /dev/sda1 instead of /dev/hda1?

You can do the same fing but when it's write /dev/hda1 you must have /dev/sda1

And it's work, i do it on my laptop :)

---

### Post by jsbach on 2008-05-18
I would say the noatime/nodiratime mount options are a good idea for most systems.

But I cannot agree with changing the journalling options to data=writeback. This has caused real problems when power outages and the like occur.

Anyone using firefox, when a hard-freeze or power outage occurs, for example, will almost certainly lose all their settings, bookmarks, extensions, themes etc.

I have had this happen on several systems. I am not guessing or postulating, I am stating from painful, hard experience.

---

### Post by articpenguin on 2008-05-19
if you are really paranoid about data safety like the ext3 devs. Change your journalling mode to journal data.

---

### Post by psyke83 on 2008-05-21
> **articpenguin said:**
> if you are really paranoid about data safety like the ext3 devs. Change your journalling mode to journal data.

Aside from increased data security, it seems wise to try full "journal_data" mode as it can possibly decrease latency and give the impression of better overall "I/O multitasking" performance.

See: [http://www.ibm.com/developerworks/library/l-fs8.html](http://www.ibm.com/developerworks/library/l-fs8.html) and [http://bugzilla.kernel.org/show_bug.cgi?id=9546](http://bugzilla.kernel.org/show_bug.cgi?id=9546)

Also, it may alleviate this Firefox 3 bug: [https://bugzilla.mozilla.org/show_bug.cgi?id=421482](https://bugzilla.mozilla.org/show_bug.cgi?id=421482)

---

### Post by Aanidaani on 2008-05-24
Worked great. Thanks!

---

### Post by wquiles on 2008-05-24
Worked great with my Ubuntu 8.04 Server - thanks much!

(and yes, I needed the grub and tune2fs steps - first time without these I got the read-only problem!)

Will

---

### Post by tad1073 on 2008-05-25
I have sda1 for swap and sda2 for / on drive0, sdb1 for  /home on drive1 and sdc1 for /mnt on drive2. Do I need to add data=writeback to each entry in fstab, minus swap?

---

### Post by janfsd on 2008-06-04
So what about noatime vs relatime? I am asking since Hardy uses relatime.

---

### Post by Lazy123 on 2008-06-12
> **janfsd said:**
> So what about noatime vs relatime? I am asking since Hardy uses relatime.

From the man page:
```
              relatime
                     Update inode access times relative to  modify  or  change
                     time.  Access time is only updated if the previous access
                     time was earlier than the current modify or change  time.
                     (Similar  to  noatime,  but  doesn’t  break mutt or other
                     applications that need to know if a file  has  been  read
                     since the last time it was modified.)
```

So it seems like it has the advantages of the noatime without the disadvantages.

---

### Post by Masoris on 2008-06-21
Thank a lot, my Ubuntu become much more faster :)

BTW, I just want to apply this tweak only my /home folder partition (/dev/sda6), should I edit /boot/grub/menu.lst for this?

---

### Post by autocrosser on 2008-06-21
Edit your /etc/fstab for the partitions you want changed--

NOTE: as of fresh Hardy installs--everything is changed to "relatime"--I changed all mine to reflect the change.......

---

### Post by Bakerconspiracy on 2008-06-24
*********FIXED*********************************
What if my fstab looks like this:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9eb9eb1f-e9be-4da6-b75a-10125013d55f /               ext3    defaults,errors=remount-ro,data=writeback     0       1
# /dev/sda5
UUID=56ccca5d-6cfd-449c-8ff4-9e7257ac3c64 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sdb1       /home/andrew/Desktop/sdb1       ext3    defaults        0       0

//see the /dev/sda1 is commented out, but I am left with a crazy UID. Any suggestions?

....Sorry didn't read tunefs options.

---

### Post by grndrush on 2008-08-07
> **Bakerconspiracy said:**
> *********FIXED*********************************
What if my fstab looks like this:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9eb9eb1f-e9be-4da6-b75a-10125013d55f /               ext3    defaults,errors=remount-ro,data=writeback     0       1
# /dev/sda5
UUID=56ccca5d-6cfd-449c-8ff4-9e7257ac3c64 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sdb1       /home/andrew/Desktop/sdb1       ext3    defaults        0       0

//see the /dev/sda1 is commented out, but I am left with a crazy UID. Any suggestions?

....Sorry didn't read tunefs options.

Suggestion: LEAVE WELL ENOUGH ALONE, LOL!

If you check, you'll see the UUID ("9eb9...") is the same UUID as your /dev/sda1 (barring any possible recent disk maintenance). See /dev/sda1 commented out on the line above?

A number of distros are (misguidedly, IMNSHO), going to UUID's instead of partition ID's to ID the disk/partition in question. Due to the recent PATA/SATA driver changes in the kernel/modules, some BIOS'es are apparently not always assigning HD ID's (/dev/hda, /dev/sdb) in the same order on every boot, causing havoc at mount time.

I'll fight that battle when I get such a mobo. Right now, THIS change causes me pains (I immediately revert them); for a number of reasons, several of my partitions get rebuilt (generating a new UUID) on a regular basis. But I do understand why they did it - those that don't know or care better won't be affected, and anal types like myself who are always fiddling with crap they really oughtn't know when they'll be affected, and how to work around it. Ah, progress...

---

### Post by pwerner2 on 2008-10-20
Ok, the instructions worked, but I think I would like to try journaled for a while. So, if I wanted to switch to from ordered or writeback to journaled, I would just have to replace the "writeback" with "journaled", right?

---

### Post by giorgosc61 on 2008-12-31
Hello,

I would also like to revert back to ordered.

What I have to do to revert back without problems?

Thank you in advance....:)

---

### Post by Kissell on 2008-12-31
I have always used EXT3 in linux, because it was the default in linux...  I recently switch away from ext3 for my data partition...  And I'm never going back!  

Now I'm using XFS and loving it!  You guys might want to look into that instead...  It is noticably faster in my case.  Although there may be other factors, like I dumped all the data to the file system in one large copy, so everything is continugous now, versus on my EXT3 partition it wasn't...  and a really nice benefit, is XFS doesn't require me to run checkdisk every few dozen reboots, that was horrible on a 8TB volume, unexpectedly took forever on some reboots because of that.

I have mostly large files, so its faster and has lots of little benefits, like it freed up 300GB of space versus EXT3 on my 8TB volume.  I guess it just handled storing the files better and wasted less space...  Maybe related to the contiguous thing again...  I made no other change, just reformatted and put XFS on and copied the data back, it just used less space to store the files now, and this wasn't even a consideration when I switched to try it.

But, it doesn't work well with Grub, so I wasn't able to use it for my boot partition...  but I originally didn't know about it, and am loving it, i'll use XFS from now on for my data.  

NOTE: One disadvantage, you can't use XFS in windows... AFAIK...  I have a program that lets you read EXT3 in windows, but not one for XFS...  no big deal to me...  but might be a deal breaker for some.

---

### Post by bustherh on 2009-02-21
I just have to say that this worked great for me. Noticable improvement in performance and speed. My linux was running pretty choppy for some reason.

---

### Post by KhaaL on 2009-03-12
A word of warning, the data=writeback flag will make a ext4 system boot into read-only mode, so be cautious.

---

### Post by dcstar on 2009-04-29
> **Kissell said:**
> 
.......so everything is continugous now, versus on my EXT3 partition it wasn't...  and a really nice benefit, **is XFS doesn't require me to run checkdisk every few dozen reboots**, that was horrible on a 8TB volume, unexpectedly took forever on some reboots because of that.
.........

And neither does EXT2/3/4, that is just a default setting you could have changed in about 30 seconds.

I cannot believe how many people complain about particular things (and then stop using them) when all their issue sometimes is their own inability to do a little research that would have resolved it quickly and permanently.

---

### Post by fungiside on 2009-09-19
This made the ssd in my netbook way faster! Thanks!

---

### Post by J V on 2010-01-30
how to stop data=writeback booting into ro with grub2? :/

Will update-grub work? Or am I going to have to edit grub.cfg every kernel update?

---

### Post by bilijoe on 2010-01-31
> **GoldBuggie said:**
> I'm using an old 900MHz Toshiba Laptop and these below changes changed my system quite noticable. You should feel an increase in video, image or audio usage.

Linux has several choices of filesystems. Two quite known filesystems are ext3 and ReiserFS. This following howto **works for both** those two filesystems. 

The ext3 filesystem provides more journaling which makes it "safer" and recovery of files in case of a crash is more likely. This has its price in performance thou. ReiserFS is a faster filesystem but with less safety. The default for ubuntu systems is ext3.

Ext3 & ReiserFS has three kinds of journaling methods:
[COLOR=Blue]**1)**[/COLOR] Journal Data Writeback
[COLOR=Blue]**2)**[/COLOR] Journal Data Ordered
[COLOR=Blue]**3)**[/COLOR] Journal Data

I don't want to explain them to much here but the difference of the three is when the actual data is written to the filesystem in relation to the metadata and its entrance into the journal.

By default the the 2nd method is used.

To speed things up we will make it use method 1. .... **Does this work with the [new] ext4 filesystem?**

---

### Post by Kangarooo on 2010-11-21
:popcorn: BUMP? Does this work and how with EXT4 ? :popcorn:

---

### Post by enthy on 2011-08-31
i just found that : [http://doc.ubuntu-fr.org/mount_fstab]("http://doc.ubuntu-fr.org/mount_fstab")

PARTITION	TYPE		OPTION 
/		reiserfs noatime,notail,data=ordered,errors=remount-ro

/boot		ext2		defaults,noatime,noauto*
/usr		reiserfs	defaults,noatime,notail,nodev
/var		reiserfs	defaults,noatime,notail,nodev
/tmp		ext2		defaults,noatime,notail,nodev,noexec
/home		asYOUwish	defaults,rw,user

/storage**	xfs		rw,user
/backup***	xfs		rw,user,sync

TYPE : 
ext2 no journaling (ideal for boot) max: 16TB
ext3, ext4 ext4 is improved (performance and reliability)
xfs storage big files (avi, iso, zip ...) max: 8EB
reiserfs very fast with small and large files (good for /home; /public) max: 16TB

OPTIONS : 
rw	read + write
ro	read only
noexec	can&#8217;t execute file on this partition
nodev	can&#8217;t mount device on this partition
nosuid	no su id
sync	input and output to the filesystem

**notail	increases performances [reiserfs]**
noatime	turns off atimes for increased performance - normally not needed (except for mail service + application partition)

noauto	no auto mounted at bootup
nofail	ignore if not present &#8211; ideal for $backup over usbdrive
user	user can mout it (explicit option: noexec, nosuid, et nodev)

usrquota	active user quota - UID
grpquota	active group quota &#8211; GUID
acl		access control list

data=	metadata for files can be written after the file is written (journal, ordered or writeback)****

errors=	when it do if errors during boot (remount-ro or continue)

* only need /boot when you update your kernel
** i use storage for iso, avi, zip, dump, ... "big files"
*** external usb drive
**** writeback is less secure than ordered

source:
[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

ps: by the way defaults are rw, suid, dev, exec, auto, nouser, and async.

---

