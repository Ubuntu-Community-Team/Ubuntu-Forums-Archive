---
title: "HOWTO: Restore GRUB (if your MBR is messed up)"
date: 2005-10-15
forum: Outdated Tutorials &amp; Tips
---

### Post by arnieboy on 2005-10-15
[B][URL="http://ubuntuforums.org/member.php?u=13391"]Written by vnbuddy2002
[/URL][/B]
Restoring GRUB is quite simple in Ubuntu. Instead of going through all the "gain root access" and playing with shell commands, you can use the Ubuntu installation CD to restore it without going through all kinds of hassles.

Here are the steps:

1. Boot your computer up with Ubuntu CD
2. Go through all the process until you reach "[!!!] Disk Partition"
3. Select Manual Partition
4. Mount your appropriate linux partions

/
/boot
swap
.....

5. DO NOT FORMAT THEM.
6. Finish the manual partition
7. Say "Yes" when it asks you to save the changes
8. It will give you errors saying that "the system couldn't install ....." after that
9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
10. Jump to "Install Grub ...."
11. Once it is finished, just restart your computer

Good luck!.

---

### Post by yesplease on 2005-10-16
Just an alternative: you can put Grub on floppy. 

I used the method above when something went wrong during my first install (hoary hedgehog). This made me very careful, so at point 10 I choose to put Grub on floppy. 

Edit: I tried this in Breezy and it didnt work for me (dont know why, it could be me, the hardware, or even breezy). **This method did work in Breezy**:

Boot from install CD, at the boot promt type: rescue
Follow some simple instructions (such as type the host name of your computer) and you wil get a menu where you can choose to a partition to mount.

The root partition of ubuntu is the first partition on my second hard disk, so I choose /dev/discs/disc1/part1.

At the prompt (sh-3.00#) I typed: ls
This produced a list of directories, such as boot, that convinced me that I mounted the right partition.

Mount the floppy disk: mount /dev/fd0
Install Grub on the floppy disk: sudo grub-install "(fd0)"
including the qoute signs.

Note: you can also chose the appropiate partition of your hard disk in case you want to restore your mbr.

The response was:
contents device map /bot/grub/device.map
(fd0) /dev/fd0
(hd0) /dev/sda
(hd1) /dev/sdb
asking if this was correct.
I typed exit at the prompt because this was correct: ubuntu is on the 2nd sata disk (/dev/sdb).

In the BIOS I put floppy as first boot device and could boot from foppy again.

Note: if you need to edit device.map you need a different tutorial. My floppy was already formatted.

This tutorial looks solid:
[http://www.yolinux.com/TUTORIALS/LinuxTutorialRecoveryAndBootDisk.html#RESCUE](http://www.yolinux.com/TUTORIALS/LinuxTutorialRecoveryAndBootDisk.html#RESCUE)

I still am booting from floppy because, if necessary, I can reinstall windows and it wont overwrite grub. 

This setup survived a dist-upgrade from hoary to Breezy; the entries for Breezy were added to the floppy automatically.

I have two hard disks, one for windows and one for Ubuntu, but this should work with one hard disk as well. I suppose you can also use a bootable memory stick.

Windows wants to be one the first partition on the first hard disk. I did not have to edit grub with the map option to make the windows think it is on the first disk. Windows is on the first hard disk because that is the sequence set in the BIOS. (When you boot from floppy it must be first in the BIOS boot sequence.)

Note that this setup is not necessary for security, I just find it convienient.

---

### Post by cbudden on 2005-10-16
Would you explain how to put grub on a floppy?

---

### Post by yesplease on 2005-10-16
[QUOTE=cbudden]Would you explain how to put grub on a floppy?[/QUOTE]

I edited the 2nd post in this tread to include this.

---

### Post by Curlydave on 2005-10-27
After reinstallign Windows, GRUB is gone. I tried following your instructions, but I cannot get past step 4. How do you mount the partitions? If I go to the Install Grub part of the menu, it just puts me back to the partition manager, and if I hit enter, save changes after selecting my ubuntu partition, it says that it can't find root file system and won't let me continue. How do I put GRUB back?

---

### Post by arnieboy on 2005-10-27
[QUOTE=Curlydave]After reinstallign Windows, GRUB is gone. I tried following your instructions, but I cannot get past step 4. How do you mount the partitions? If I go to the Install Grub part of the menu, it just puts me back to the partition manager, and if I hit enter, save changes after selecting my ubuntu partition, it says that it can't find root file system and won't let me continue. How do I put GRUB back?[/QUOTE]
u have to set your ubuntu partition as "/" (or the root partition ---> please dont confuse this with /root which is the directory for the root user)

---

### Post by Biffy on 2005-10-28
Yes, but how do you mount your partition like that? Tell us how you do that from the partitioning menu.

---

### Post by yesplease on 2005-10-28
When you step through the instructions, you will arrive at the partition manager.  There you will see that all partitions got general names like /media/hda1, or something like that. Now you have to mount those partitions. 

Select a partition and go to the partition description table (by pressing enter, I think). Select each line in this table and select the correct entry. For example: my root partition is used as ext3, mount point is / and bootable flag must be on.  Be sure that you leave the data on the partition (there is an entry for that). Do this for all partitions. (I have / , swap and /home, and you may also have a NTFS partition for WinXP.)

During this proces nothing is changed, so you can always abort if you are not sure.

---

### Post by Curlydave on 2005-10-29
Hmm, still can't get it mounted or figureu out how to set it up as "/". If I hit enter on a partition, I get some basic settings, like the option for a boot flag, to wipe it or not etc, but there is no mount or place to put "/". If i hit save after that I get the no root file system error and I can't put on GRUB. Let's say I'm a computer nub who needs basic step-by-step instructions. How do I get from the partition manager to the install-grub section without erasing my partition. (I know how to do it that way, but I can't get it working this way while saving the partition.)

---

### Post by yesplease on 2005-10-30
@ Curlydave: Select the partition where / should be, and go to the 'basic settings'. Select the entry 'mount point' and select '/'.  Perhaps you should scroll up or down to see it?

From my notes: root partition;  use as Ext3, format no, mount point /, mount options default, bootable flag on, size x GB.

Swap partition; use as swap, bootable flag off, size (less than 2 GB). It doesnt matter when swap gets formatted.


home partition; no notes, there is only one way to do it.

Remark: /usr is not a user partition.

---

### Post by Curlydave on 2005-10-31
> **yesplease]@ Curlydave: Select the partition where / should be, and go to the 'basic settings'. Select the entry 'mount point' and select '/'.  Perhaps you should scroll up or down to see it?

From my notes: root partition said:**
> 

Thanks, that got it working.

I propose an ammendment to this how-to:

Replace step 4-6 with the following:

[quote]Select your appropriate Linux partition using the up and down arrow keys, and press enter. Then select the "mount point" option, and press enter. From the list, select the "/" option that indicates the root file system. Select the option labled "bootable flag" by pressing enter on it. Save the changes to the partition.

Something like this would prevent nubs like me wasting time with and getting frustrated over problems with an otherwise straight-foward how-to.

---

### Post by ShirishAg75 on 2005-11-28
Sorry to put a query in the running thread but as it has to do with GRUB hence posting it here. How do I make the timings infinite. I want that unless I select something the boot screens remains as it is. Right now one can change the timings to some seconds or X no. of seconds what I want is infinity. Any way?

---

### Post by arnieboy on 2005-11-28
[QUOTE=shirishag75]Sorry to put a query in the running thread but as it has to do with GRUB hence posting it here. How do I make the timings infinite. I want that unless I select something the boot screens remains as it is. Right now one can change the timings to some seconds or X no. of seconds what I want is infinity. Any way?[/QUOTE]
do the following:
```
sudo gedit /boot/grub/menu.lst
```
look for the word **timeout** with the number of seconds shown after that.
comment that line by adding a **#** at the start of the line so that it looks something like:
> #timeout		3
save and exit and restart your computer

---

### Post by ShirishAg75 on 2005-12-08
thnx

---

### Post by wizzer on 2005-12-23
[QUOTE=arnieboy][B][URL="http://ubuntuforums.org/member.php?u=13391"]Written by vnbuddy2002
[/URL][/B]
Restore GRUB quite simple in Ubuntu, instead going through all the "gain root access" and play with shell commands, you can use the Ubuntu installation CD to restore it without going through all kinds of hassles.

Here are the steps:

1. Boot your computer up with Ubunto CD
2. Go through all the process until you reech "[!!!] Disk Partition"
3. Select Manual Partition
4. Mount your appropriate linux partions

/
/boot
swap
.....

5. DO NOT FORMAT THEM.
6. Finish the manual partition
7. Say "Yes" when it asks you to save the changes
8. It will give you errors saying that "the system couldn't install ....." after that
9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
10. Jump to "Install Grub ...."
11. Once it is finished, just restart your computer

Good luck!.[/QUOTE]


This works perfect!!!!!!   Thank you so much!!!!!\\:D/

---

### Post by ShirishAg75 on 2005-12-26
Hi all,
 I didn't have the luxury of this guide hence had to do the old way. It's interesting & one can learn a lot in the old way. 
1. The first step is making sure that the computer can boot up through a CD. So while booting up either use Escape or Alt+F2 or whatever key combination is given to access the BIOS. There look an entry which says which device to boot first, make sure that it's on CD rather than hard disk or IDE0 etc.

2. After making sure that the computer is able to boot off CD. Put in the Live CD & let it boot completely. Completely meaning till the desktop comes. If your computer is slow or has less RAM it will take quite some time. My 1.8 ghz + 128 DDRAM took around 30 minutes to fully come up. Your mileage may vary.

3. Now press ALT+CTRL+F2 to get shell prompt. The shell prompt will be something like :-
```
ubuntu@ubuntu$ :-
``` If u've got till here that means that u've a bash shell. If however u've got an unfamiliar shell then most probably its the c shell with csh or something like that. This has a limited set of commands that u can use & useless for our purposes. At any point one can use ALT+CTRL+F7 to acess the graphical boot-up.

4. Moving to the next step get the partition tables for the devices using fdisk command:
fdisk -l This will give a partition table of all the different partitions/hard disk fdisk can access. Here's a listing of what it can look like depending on u'r windows partition.

```
fdisk -l

Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         511     4104576    b  W95 FAT32
/dev/hda2             512        7651    57352050    f  W95 Ext'd (LBA)
/dev/hda3            7652        9629    15888285   83  Linux
/dev/hda4            9630        9733      835380   82  Linux swap / Solaris
/dev/hda5             512        1531     8193118+   b  W95 FAT32
/dev/hda6            1532        2551     8193118+   b  W95 FAT32
/dev/hda7            2552        3571     8193118+   b  W95 FAT32
/dev/hda8            3572        4591     8193118+   b  W95 FAT32
/dev/hda9            4592        5611     8193118+   b  W95 FAT32
/dev/hda10           5612        6631     8193118+   b  W95 FAT32
/dev/hda11           6632        7651     8193118+   b  W95 FAT32
``` 
The listing will differ in number of ways depending on whether the hard disk is a master or slave or it SATA or SCSI(sdx) or any no. of permutations & combinations.Look for ```
man fdisk
``` as well as```
info fdisk
``` for complete documentation. 

 Anyway, What we're looking for is the Linux partition. Here it's an single ext3 code 83 partition. So it's much simpler.

5. Once you identified your device file mount it. :
 ```
mkdir /santana
``` - the name can be anything.
 ```
mount /dev/hda3 /santana 
```- What gave it away atleast in my system was that's its the only ext3 partition.

6. Then use chroot command to start interactive shell with special root directory i.e. /santana will act as that special root directory.
```
cd /santana
``` 
7.Use grub-install command to reinstall grub:
```
 grub-install /dev/hda 
```- this is for single hard disk in primary master configuration. 

8.Type exit and reboot the system. You should see your GRUB and Linux again.

---

### Post by apps4apps on 2005-12-27
Any idea how to adapt this to work if you had installed using LVM. None of this seems to be working for me unfortunately... The installer does not seem to recognize the install and keeps kicking me back to the partition screen. I tried playing around a bit more but I think I ended up blowing away the install. I've had this happen a couple times now that I've accidentally blown away grub and had to start from scratch because of using LVM :( .

The only way I've found to partially recover when using LVM so far is to boot from the live CD, install EVMS-GUI, mount the LVM volume, copy the user data to another disk/partition, then completely reinstall Ubuntu and restore the data. Yuck....

I feel I must be missing something simple... Any ideas?

---

### Post by AlMaSoUdI on 2005-12-28
[QUOTE=Curlydave]Select your appropriate Linux partition using the up and down arrow keys, and press enter. Then select the "mount point" option, and press enter. From the list, select the "/" option that indicates the root file system. Select the option labled "bootable flag" by pressing enter on it. Save the changes to the partition..[/QUOTE]
 i did everything but still same...
how to save the cahnges to the partition?
i follow all the steps but still same :confused: :confused: :confused:

---

### Post by whitesox on 2005-12-28
ok, i moved my ubuntu installation onto a new hard drive, using rsync, but when I get to the grub-install (hd0), it fails.  This is correct, it is hd0, and all the partitions are mounted right, but when i chroot into my partition (using rescue at the cd boot screen) my /dev has nothing in it but null! no wonder it failed, /dev doesnt have hda1 or anything else to install to. what should I do?

---

### Post by limit223 on 2005-12-28
I don't know if somehow it helps someone here or ...probably you'll judge me offtopic...but I just want to pass something that I use every time installing different OS's(even windows) or having changes in partition table.
 I use a lot command line dd for backup, and for our case MBR backup, if it is GRUB, Lilo or NT.
 Let's say I installed an OS with Grub/Lilo/NT in MBR (assume that MBR is located in the first sector of the your hardisk that actually I exampled here by the /dev/hda)..to make a backup of it there and store it in a directory( on hardisk) or on a floppy:

dd if=/dev/hda of=/path/of/your/directory/grub.img bs=512 count=1

on a floppy:

dd if=/dev/hda of=/dev/fd0 bs=512 count=1
This /dev/hda could be /dev/hdb or /dev/hdc... was an example for an IDE controller for a P-ATA hard disk
Let's say you have a SCSI for S-ATA hard disk, then your disk is named as sda/sdb/sdc and this case your device path would be: /dev/sda

dd  if=/dev/sda of=/path/grub.img bs=512 count=1

 You have a mess in computer or some changes and just want to recover your MBR stored this way. Got your live CD or knoppix CD in assistance to reach to your data in the assumption you cannot load any of OS's that you have in computer. In this case you may mount your partition where you saved file grub.img and then:

dd if=/mounted/path/directory/grub.img of=/dev/hda bs=512 count=1

or simple just use your backup MBR floppy:

dd if=/dev/fd0 of=/dev/hda bs=512 count=1

and everything is back in the place where was before.

 I found this backup/restore very neat and easy to operate regardless the type of operating system you use.

---

### Post by apps4apps on 2005-12-29
[QUOTE=limit223]I don't know if somehow it helps someone here or ...[/quote]

Thanks :)

---

### Post by limit223 on 2005-12-29
Glad it helped....:)

---

### Post by Mazin on 2006-01-01
In the original directions, what is the point of going through the partitioner and mounting stuff?  Is it solely so we can skip to anyywhere we want?

I am trying to restore GRUB too, and I found that by going into the Ash shell from the install and then exiting, it would throw an error and let me skip to Install GRUB in the menu.  **However**, when I tried Installing GRUB from the installer, it complained that /target was not there.  I think maybe it was something I did in the shell, but I don't remember it being there when I started the shell.  What's /target supposed to be mounted as?

---

### Post by pbb on 2006-01-01
Arnieboy, I agree with Curlydave's post, point #4 needs more explaination.

Also, you're referring to "the Ubuntu CD". Since most people here have two of them lying around, you should mention that this is the Ubuntu **Install** CD.

And finally, before your step #8, I got an "Not installing to unclean target" error, which I also had to skip using "Continue". Don't know if this is common, but it might be worth mentioning.

For the rest, a good guide. This is also the way I restored my GRUB after messing with the partition tables...

---

### Post by one2one on 2006-01-04
This is really hard to comprehend and do for a newb. Old DOS instructions were "Clear" and easy to follow, not so with Linux. 

I downloaded Grub-Disk program from the repository and it is suppose to let me put the Grub Boot on a floppy. **Where do these things go when they get downloaded, installed, and don't show up in any Applications? **I tried using the "Search" but I don't have permission for much. Copied the list of Linux Commands, but like I said, more muddy than clear.

---

### Post by pbb on 2006-01-04
[QUOTE=one2one]Where do these things go when they get downloaded, installed, and don't show up in any Applications?[/QUOTE]

This is a bit off-topic, but in Synaptic, select the package you just installed (should have a green box in front of it), then click the Properties button, and go to the Installed Files tab. There you can always see which files were installed and where.

But I agree with you that applications are often difficult to find back after installation. At least in Windows, they all ended up under Program Files...

---

### Post by AlMaSoUdI on 2006-01-19
Quote:
Originally Posted by Curlydave
Select your appropriate Linux partition using the up and down arrow keys, and press enter. Then select the "mount point" option, and press enter. From the list, select the "/" option that indicates the root file system. Select the option labled "bootable flag" by pressing enter on it. Save the changes to the partition..
i did everything but still same...
how to save the cahnges to the partition?
i follow all the steps but still same 

so how................

---

### Post by robinl on 2006-02-01
I've followed the first post and installed GRUB but it just won't show up. I installed ubuntu on a clean harddrive (fresh partition) and it was fine until I installed Win XP and now I am stuck with it. I did what it says in the installation partitioner and pressed continue for 2 errors, select install grub, shows that I have WinXP (ubuntu is not on the list, however) and installed (I think). Then the screen flashes and go back to the 2 errors and back to the selection menu. When I restarted it go straight into Windows without any trace of GRUB. Any help, anyone? Thanks

**Edit:**Appearantly Windows installs MBR onto my other harddrive (hdb) so my GRUB was fine all along.

---

### Post by daredevil on 2006-03-01
Thank you very much arnieboy. this is veeery useful

---

### Post by ToastyMunch on 2006-03-06
[QUOTE=AlMaSoUdI]i did everything but still same...
how to save the cahnges to the partition?
i follow all the steps but still same :confused: :confused: :confused:[/QUOTE]
I had the same problem until I toggled the bootable flag for each partition, selected the "done with this partition" option, and then toggled the flag back to the desired settings...

---

### Post by Symok on 2006-03-15
[QUOTE=arnieboy][B][URL="http://ubuntuforums.org/member.php?u=13391"]Written by vnbuddy2002
[/URL][/B]
Restore GRUB quite simple in Ubuntu, instead going through all the "gain root access" and play with shell commands, you can use the Ubuntu installation CD to restore it without going through all kinds of hassles.

Here are the steps:

1. Boot your computer up with Ubunto CD
2. Go through all the process until you reech "[!!!] Disk Partition"
3. Select Manual Partition
[/quote]

I get this far, then run into problems. The hard drive on which Ubuntu and Windows is installed is displayed, but it does not list ANY of the partitions. When I select the drive, it asks me if I want to wipe the partition table.

I have also tried following [this](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?highlight=%28MBR%29) guide from the Wiki ("Using the Ubuntu Install CD") but when I try to run grub-install it says it can't read from a file (Can't remember what the name was ATM. Will check shortly and edit it in)

Edit:
Ok, the error message is
"The file /boot/grub/stage1 not read correctly"

Further Edit:
Also tried the "Super GRUB Disk". Didn't work either. :(

---

### Post by mconiegs on 2006-03-29
Thanks, used first post plus some discussion of step 4, and I now have a dual boot system again. :)

---

### Post by zasf on 2006-03-31
[QUOTE=limit223]I don't know if somehow it helps someone here or ...probably you'll judge me offtopic...but I just want to pass something that I use every time installing different OS's(even windows) or having changes in partition table.
 I use a lot command line dd for backup, and for our case MBR backup, if it is GRUB, Lilo or NT.
 Let's say I installed an OS with Grub/Lilo/NT in MBR (assume that MBR is located in the first sector of the your hardisk that actually I exampled here by the /dev/hda)..to make a backup of it there and store it in a directory( on hardisk) or on a floppy:

dd if=/dev/hda of=/path/of/your/directory/grub.img bs=512 count=1

on a floppy:

dd if=/dev/hda of=/dev/fd0 bs=512 count=1
This /dev/hda could be /dev/hdb or /dev/hdc... was an example for an IDE controller for a P-ATA hard disk
Let's say you have a SCSI for S-ATA hard disk, then your disk is named as sda/sdb/sdc and this case your device path would be: /dev/sda

dd  if=/dev/sda of=/path/grub.img bs=512 count=1

 You have a mess in computer or some changes and just want to recover your MBR stored this way. Got your live CD or knoppix CD in assistance to reach to your data in the assumption you cannot load any of OS's that you have in computer. In this case you may mount your partition where you saved file grub.img and then:

dd if=/mounted/path/directory/grub.img of=/dev/hda bs=512 count=1

or simple just use your backup MBR floppy:

dd if=/dev/fd0 of=/dev/hda bs=512 count=1

and everything is back in the place where was before.

 I found this backup/restore very neat and easy to operate regardless the type of operating system you use.[/QUOTE]

very nice, but I guess it works only if you don't change the partition table.. otherwise GRUB won't load ending withe error 15, guess why I know this.

---

### Post by Jinxed2 on 2006-04-07
My pennies worth ...
Love Ubuntu, for a newbie, its simple, understandable and easy to get to know your way around ... HOWEVER

part1: windows xp -- dying and suffering
part2: windows 2003 -- all the stuff the boss wants... 
part3: store

part1: -->delete for Ubuntu --- install ...  
part2: windows 2003 -- all the stuff the boss wants... 
part3: store

part1: UBUNTU!!! .. nice playing, learning, configuring, etc ... 
part2: windows 2003 -- all the stuff the boss wants... 
part3: store

boss calls: wants a field added to a "vb" program we use .. :-D ....
no problem, I have something called "GRUB" in here ....
....reboot,:-D  wait for GRUB, :-D , move to the line with something about OTHER OPERATING SYSTEM..., hit enter .... :-D  .... :-k  .... :confused: 

THE #$%$ HITS THE FAN

**final pennies worth ...**
Forums are educated, informative and helpfull places, **with nice people who write alot about what you are about to do, AND WHY YOU SHOULD'T** ...... read ...... If you need to duel boot for your Boss, **don't** install UBUNTU in 1st partition, _**Your Boss won't be happy..**_

...or am i just Jinxed ...?

---

### Post by limit223 on 2006-04-07
[QUOTE=zasf]very nice, but I guess it works only if you don't change the partition table.. otherwise GRUB won't load ending withe error 15, guess why I know this.[/QUOTE]
 If you change the partition table, meanwhile you must change /boot/grub/menu.lst with your new partition number which held the system you wanna load.

---

### Post by Papa-san on 2006-04-27
OK... After several attempts at making my system a dual boot, I am for the third time looking at this situation:

2 hard drives;
#1 - Windows XP pro, and fat32 formatted free space.
#2 - Ubuntu partitions (None of which have nice, simple names like:
  '/ ',   ' /boot ', or  'swap ') They all have different 'hda' numbers 
    - also, on this physical drive, I have a 10 gig 'fat32' partition that currently contains all of the critical files and information that must be saved and put back into my wifes XP system.
Original Post from this thread:

> 4. Mount your appropriate linux partions

/
/boot
swap
.....

5. DO NOT FORMAT THEM.
6. Finish the manual partition

Step #4 - my issue is above the quote;

Step 5 - I might be able to muddle through this part, but then again, I've screwed it up twice already..;

Step 6 - Ummmm... OK... Not exactly sure how to do this, or what I am supposed to do. 

Then, I need to set it up (assuming I actually have a functional MBR with both Win XP and Ubuntu represented) where the OS that loads without user intervention is the XP. (My bride isn't ready to commit to the guy in the tux yet!!!) :rolleyes:

---

### Post by dan_99503 on 2006-06-05
I am posting here in the hope that someone can help me. I have been fighting this for a long time and haven't been able to find the proper assistance to get it working. 

I am ready to drop Dapper since I have invested so much time (too much) trying to get around this problem. 

My System:
hda (128MB) Compact FLash IDE drive (Looks just like a 128MB HD)
hde 80GB HD
hdg 80GB HD
USB CDROM --- This ends up in HD0 in GRUB???!!!

I can get it to boot my system if I use a GRUB boot CD (RIPLinux) and use:
root (hd1,0)
kernel /vmlinuz-xxxxxx root=/dev/md0
initrd /initrd.img-xxxxx  


Although no matter what I do I cannot get it to boot correctly from the HD.

I have tried changing the config on the HD to match above. 
I have re-installed GRUB from the ubunutu CD (and tested different settings)
I have re-installed GRUB from RIPLinux CD (and tested different settings)

All of this with the USB CD-ROM off and ON..
I cannot turn OFF USB as suggested in other thread due to this server not having PS/2 ports.

I have also tried what Arnie suggested above. Run CD and don't format. But strangely enough on my system (both with Dapper install CD and ALT dapper install CD) both don't come up with ANYTHING about GRUB!  I tried what you said and it's doing a base install overwritting the existing system as I'm typing. I will probably have to re-install again in a less complex way so Ubunutu will actually CREATE the files in the /boot directory (another bug). 8(

I need help and this is my last attemp at getting it before leaving Ubuntu and coming back later after they have it working.. 

Thanks,

- Dan

---

### Post by Miles Attacca on 2006-09-26
How can I do all the reconfiguring that the installer would normally handle, from the command line? I have an AMD64 live CD and system, and I can't put in the proper drivers to keep the graphics from freezing up until after I install (meaning many fingers-crossed install attempts), so I'd rather be able to just type the lines in, after a half-dozen attempts tonight.

---

### Post by damu on 2006-12-03
I had to reinstall WinXP after a "hal.dll missing...". THe first time I used my WinXP cd to repair, it deleted the grub (expected), even though I didn't go further than the first steps and cancelled the installation . The second time (with the same procedure, in which I manually edited partitions, and selected the one dedicated to WinXP : hda1), my fat32 partition (hd4)with all my datas disappeared. I now have a nice 115 Go of free space :confused: 
Here is the structure on my HD : 
-hda1 :WinXP 
-hda2 :Studio-to-go on 
-hda3 :Ubuntu
-hda4 : empty partition (prvioulsy fat 32 with my datas)
-hda5 :swap

I reinstalled WinXP on hda1. I am now trying to restore the grub, following the method given at the beginning of this thread. I am stuck at the "Prepare mount points" during the installation process, using a dapper live cd, as it wouldn't allow me to go further if I don't format hte / partition :
> Filesystems used by the system (/, /boot, /usr, /var) must be reformatted for use by this installer. Other filesystems (/home, /media/*, /usr/local, etc.) may be used without reformatting.

I can gedit /boot/grub/menu.lst on hda3, but I don't know how to reinstall it on the MBR, and Ididn't find yet any answer in the forum or wiki. Need you help here

Thanks.

---

### Post by geodeath on 2007-02-05
well, it seems that i cannot get past the partition stage, because i will not allow me to select my / and /boot without formatting them. I am talking about the 6.10 install cd here. Its kinda different. You cant just select mount points as the other tread says. You have to select the HD you want and in the next step you have to select mount points.

It doesnt allow me to continue if i dont have format ticked and i am not sure if its going to format the disks right away or not.

---

### Post by zeroblitzt on 2007-02-05
I have a boot related problem.

I put a new hard drive in my brother's computer (seeing as he only had like 28 gigs, there was a 20 gig hard drive and an 8 gig). I put a 40 gig in, removing the 8 gig one. But his Linux installation was on the 20 gig, and the MBR was on the 8 gig apparently, because when I started it up, Linux would not boot!

I tried fixing it with the CD method, as I had previously known about that. That didn't work because his CD drive freezes about 3 minutes into the boot now for some reason (very strange). I tried making a grub boot floppy, but when I do "find /boot/grub/stage1" it can't find the files (obviouisly). Is there a way to use the floppy to reinstall grub?

Or, I just thought of something. Could I put the 8 gig drive back in, reinstall grub to the 20 gig, then take the 8 gig out and  put the bigger drive back in?

---

### Post by dillon533 on 2008-10-07
thankyou all for your help. worked a treat.

---

### Post by Liviu-Theodor on 2009-01-08
You could also dowload the grub cd from [http://supergrub.forjamari.linex.org/?section=download]("http://supergrub.forjamari.linex.org/?section=download").

---

### Post by gmaxindia on 2009-02-02
i install ubuntu and next install winxp 


how recover boot first ubuntu 


plz help me:(

---

