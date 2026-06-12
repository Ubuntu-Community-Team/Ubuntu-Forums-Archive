---
title: "help please"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by anotherconfused1 on 2008-07-01
I tried installing ubuntu, i had it installed before but removed it because of other issues, now i get this error when i start this up.
GRUB Loading stage 1.5.
GRUB loading, please wait...
Error 17

please help!
an yes i know how to partition and that stuff, i just have trouble remembering how to do it. Please make your solution easy enough for my 16 year old mind to understand
edit: i dont have  a windows recovery CD either

---

### Post by bab1 on 2008-07-01
It sounds like when you deleted the linux install you did not remove the partition.  So you have the boot record and nothing else.  Try removing the partition.

---

### Post by rzrgenesys187 on 2008-07-01
Are you trying to reinstall ubuntu or remove the partition?

---

### Post by anotherconfused1 on 2008-07-01
I tried re installing but it still doesn't work, if not for the live CD I'd be screwed. If I could just delete the partition and get back into XP I would.

---

### Post by bab1 on 2008-07-01
So, are you saying you can't run fdisk off of the LiveCD?

---

### Post by anotherconfused1 on 2008-07-01
whats fdisk?

---

### Post by hyl4me on 2008-07-01
> **anotherconfused1 said:**
> I tried re installing but it still doesn't work, if not for the live CD I'd be screwed. If I could just delete the partition and get back into XP I would.

If you could get your hand on XP installation disc (not the recovery disc from your PC manufacture).  You could go to Recovery Console after booting by the XP disc.  Just type in "fixmbr".  Or else try 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by tjwoosta on 2008-07-01
the error you are getting is saying that your /boot/grub/menu.lst is configured wrong (or maybe grub cant find it in the first place)

you should be able to mount the filesystem from the live cd and edit it as needed

when you were reinstalling did you make sure to reinstall grub to the MBR ?

---

### Post by bab1 on 2008-07-01
fdisk is the "Partition table manipulator for Linux".  At the command line you would type "fdisk /dev/"thehardrivedeviceyouareusing"  This would be sda or hda etc.

---

### Post by fishman78 on 2008-07-01
> **anotherconfused1 said:**
> I tried installing ubuntu, i had it installed before but removed it because of other issues, now i get this error when i start this up.
GRUB Loading stage 1.5.
GRUB loading, please wait...
Error 17

please help!
an yes i know how to partition and that stuff, i just have trouble remembering how to do it. Please make your solution easy enough for my 16 year old mind to understand
edit: i dont have  a windows recovery CD either


Howdy!

I am no ubuntu expert in any way, but just had the same problem.  In the grub loader it wanted to load from hdd2,0, when I needed to load from hdd1,0.  Try changing it in your grub loader ( i think you press escape and the type e when you have the loader highlighted ).  After you get into ubuntu you can change the grub by typing:

sudo gedit /boot/grub/menu.lst

Change the values to which ever drive you need, save, reboot.

Thanks again to Kuja for helping me with that one.

Hope this helps, again I'm no expert!  This may not even be the problem, but worth a try.

Kurt

---

### Post by anotherconfused1 on 2008-07-01
> **fishman78@live.ca said:**
> Howdy!

I am no ubuntu expert in any way, but just had the same problem.  In the grub loader it wanted to load from hdd2,0, when I needed to load from hdd1,0.  Try changing it in your grub loader ( i think you press escape and the type e when you have the loader highlighted ).  After you get into ubuntu you can change the grub by typing:

sudo gedit /boot/grub/menu.lst

Change the values to which ever drive you need, save, reboot.

Thanks again to Kuja for helping me with that one.

Hope this helps, again I'm no expert!  This may not even be the problem, but worth a try.

Kurt
That helped I got the menu.lst up, but it's blank! What the heck have I done?!?

---

### Post by bab1 on 2008-07-01
You Removed The Os! THE OPERATING SYSTEM

---

### Post by anotherconfused1 on 2008-07-01
Then how the hell do I fix it?

---

### Post by fishman78 on 2008-07-01
> **anotherconfused1 said:**
> Then how the hell do I fix it?

I think you may have to re-install bud.

Sorry

Anyone else?

Kurt

---

### Post by bab1 on 2008-07-01
We told you!  Either reinstall the system or, as I said remove the booting partition for the long gone Linux system.  You said you knew how t partition the drive.  Do you?

---

### Post by anotherconfused1 on 2008-07-01
> **fishman78@live.ca said:**
> I think you may have to re-install bud.

Sorry

Anyone else?

Kurt
No offense, but I have tried it 4 times now.

---

### Post by Elfy on 2008-07-01
If you can get to another pc - download suprgrub - it has an option to fix the windows mbr, there is a way to do it from the cli but I'm getting kids ready for school, so if soemone else knows...

Get the iso, burn it as such so you can boot with it, don't panic.

[http://www.supergrubdisk.org/index.php?pid=5](http://www.supergrubdisk.org/index.php?pid=5)

---

### Post by anotherconfused1 on 2008-07-01
> **forestpixie said:**
> If you can get to another pc - download suprgrub - it has an option to fix the windows mbr, there is a way to do it from the cli but I'm getting kids ready for school, so if soemone else knows...

Get the iso, burn it as such so you can boot with it, don't panic.

[http://www.supergrubdisk.org/index.php?pid=5](http://www.supergrubdisk.org/index.php?pid=5)
Everything is going wrong for me...is it possible to boot from USB? If so, it's in BIOS right? How do I change it?

---

### Post by Elfy on 2008-07-01
usually del or esc or maybe an F key - check the message when you boot -

 [http://www.supergrubdisk.org/index.php?pid=7](http://www.supergrubdisk.org/index.php?pid=7) for usb - _read_ the instructions it gives

You need to slow down and take a breath, go outside or something :) you will be able to get back into windows, but if you don't calm down you're likely to make another mistake.

---

### Post by Tod Merley on 2008-07-01
Hi anotherconfused1,

XP and Linux on the same hard drive - my oh my - not for the beginner I think.

At this point you simply need to not panic.

If you really need to dual boot Ubuntu/XP I would move for using the XP boot loader to control who boots and when.  MS is only happy when it is in control.

It is a lot of trouble however and I do not recommend it!

Think about two separate machines if possible.

For now we all need to know:

What the sequence of events was (what was loaded or unloaded when).
What do you have on the HD now?
What do you need the machine for?
What are your resources to restore the machine (other machines, Live CDs, original os software...
What do you really want to do with your computers (which os's for what reasons)?

Relax, it is only stuff!

Tod

---

### Post by anotherconfused1 on 2008-07-01
> **Tod Merley said:**
> 
For now we all need to know:

What the sequence of events was (what was loaded or unloaded when).
What do you have on the HD now?
What do you need the machine for?
What are your resources to restore the machine (other machines, Live CDs, original os software...
What do you really want to do with your computers (which os's for what reasons)?

1. Not sure what you mean, Ubuntu was unloaded then reloaded after I thought something went wrong before during installation.
2. A bunch of stuff I would like not to wipe, I still have access to the HD through Linux Live CD and can copy my important files and wipe it. But, I don't have my XP CD anymore.
3. This is my computer, I use it for various things, a lot of programming for one.
4. I only have the Live CD, but I have 2 other laptops at my use. And a really outdated machine with Xubuntu on it.
5. XP games, Ubuntu for programming and learning more programming.

Does this help?

I had Ubuntu installed on this computer before, partitioned and everything went all right. I removed Ubuntu and went to reinstall it and got an error at 51% that said something ( I don't remember, sorry!). Then I reinstalled after doing amother partition, (which I thought I put on top of the previous one) and get the error now.

---

### Post by Elfy on 2008-07-01
Hi again - from what I understand you had a dual-boot and deleted the buntu partition and lost the mbr - all perfectly normal, 

what exactly is it you are needing to do 

reinstall the mbr or
reinstall buntu

Edit - nmot sure what the list of questions was for ;)

IF you do want to reinstall - boot with the livecd, once it's ready - opena terminal and run this - please post the output
```
sudo fdisk -l
```

---

### Post by anotherconfused1 on 2008-07-01
I tried using the supergrunt or whatever it is called but it didn't work.I have tried to reinstall ubuntu but that didn't work either. Sorry for not really being of any help.

---

### Post by Elfy on 2008-07-01
Ok - no need to apologise. Lets try to not get too far ahead - this morning you were trying to answer questions while there were questions being asked - I'm sure you were throwing your hands in the air.

I'm sure that we will be able to get you reinstalled without too much trouble - he hopes;)

I edited my post befor eI got your reply - so first of all do that.

Boot with the livecd (I assume it was a livecd and not the alternate) and run the command I gave - here it is again

```
sudo fdisk -l
```

This will tell us what partitions you have at the moment, then we can proceed hopefully.

---

### Post by anotherconfused1 on 2008-07-01
Ok What have I done now?
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9c0c9c0c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5737    46082421    7  HPFS/NTFS
/dev/sda2            5738       14593    71135820    f  W95 Ext'd (LBA)
/dev/sda5            5738        8695    23760103+   7  HPFS/NTFS
/dev/sda6           11308       12986    13486536    7  HPFS/NTFS
/dev/sda7            8696       11193    20065153+  83  Linux
/dev/sda8           11194       11307      915673+  82  Linux swap / Solaris
/dev/sda9           12987       14519    12313791   83  Linux
/dev/sda10          14520       14593      594373+  82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$

---

### Post by Elfy on 2008-07-01
I assume that you are now in the livecd - go to the system admin menu and open partition editor. Once that is open you will see all of your partitions I need to know if the swap partitions have been used by the livecd, so once you have that open can you get a screenshot of it - in accessories - take screenshot.

Post the screenshot using the manage attachments tools - use the new reply button to make the post not a quick reply.

It all looks quite normal - you have a bootable windows partition and 2 small windows partitions in addition to the linux ones.

---

### Post by anotherconfused1 on 2008-07-01
ok here is the picture

---

### Post by Elfy on 2008-07-01
Ok - open a terminal and run

```
sudo swapoff -a
```

refresh the partition editor, in the gparted menu and see if the partions are unmounted - the keys will be gone from sda,2,8 and 10

---

### Post by ET! on 2008-07-01
even i got a similar  error

GRUB Loading stage 1.5.
GRUB loading, please wait...
Error 22

i have reinstalled it and its running perfectly...i just wanted to know what caused the error.

---

### Post by anotherconfused1 on 2008-07-01
not sure what you mean. Gparted shows the same thing as before but in devices under GParted there is one thing /dev/sda

---

### Post by Elfy on 2008-07-01
> **anotherconfused1 said:**
> not sure what you mean. Gparted shows the same thing as before but in devices under GParted there is one thing /dev/sda

Did you run the command - if you did an are unsure - just post another screenshot - we don't want to talk at cross purposes.

---

### Post by Elfy on 2008-07-01
> **ET! said:**
> even i got a similar  error

GRUB Loading stage 1.5.
GRUB loading, please wait...
Error 22

i have reinstalled it and its running perfectly...i just wanted to know what caused the error.

This error is described as

 > No such partition
This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk. 

Just realised it wasn't a question after going back to look properly - sorry.

---

### Post by anotherconfused1 on 2008-07-01
ok here you go...

---

### Post by Elfy on 2008-07-01
Ok - good all the partitions are unmounted - no key/padlock symbols. That means we can work on the partitions. Before we start there is always a possibilty that something could happen during the partitioning - power outages etc. so you need to make sure you have backups of things you can't afford to lose.

I always find it best to let gparted do each step seperately rather than give it a list of things to do, so -

select sda7 in the list  - right click and delete it - then you will have a green tick on the toolbar (apply) do that and the partition will be deleted - gparted will refresh and there should be unallocated space where it used to be.

If there is not - stop and come back.

Then we can delete each of these in the same way
sda8
sda9
sda10

Once you have finished you will have grey spaces along the partition with an active partition at the beginning and one in the middle.

Come back when you've done that.

---

### Post by anotherconfused1 on 2008-07-01
i dont have a sda10 i have an sda6 you didnt list?
i deleted the ones you said except the sda6, sda5, and sda1. sda2 is there but thats a partition of sda1 right?
now it looks like this..

---

### Post by Elfy on 2008-07-01
sda10 is in the list you posted it's one of the swap partitions - sda6 is a windows partition, as is sda5.

---

### Post by anotherconfused1 on 2008-07-01
I edited my post above, I don't know if you noticed it or not. That's what it looks like now.

---

### Post by Elfy on 2008-07-01
Ok - half way there - the linux partitions have gone and we are left with ntfs partions with gaps in between - we want to get rid of the gaps now.

To answer the question first - no sda2 is a partition in it's own right, but it is an extended partition - which can contain logical partitions. A harddrive can only contain 4 primary partitions - so using extended and logicals means we can increase that number.

We will now move sda6 so it is next to sda5.

In the list select sda6 and right click - select the resize/move option, you will get another window - select sda6 and move it to the left so that it is next to sda5 and apply that action.

This could take a little while to complete - do not under any circumstances decide that it has hung and turn it off - this will cause big damage to your partitions.

---

### Post by anotherconfused1 on 2008-07-01
ok it has like 10 minutes to go now.

---

### Post by Elfy on 2008-07-01
Ok while that's cooking we can go on to the next bit - creating 2 new partitions to install into and how to go about the install procedure - 

_Partitioning_

You should now have all the unallocate dspace at the right hand end of the partition.

If you need to hibernate then swap should equal RAM regardless but if not I have 1Gb of swap and 1Gb of RAM which is more than sufficent for my purposes. If I had 2Gb I would still only have 1Gb of swap, but if I had les than 1Gb RAM I would use the 1.5xRAM to get a value for my swap.

Right click the unallocated space and create a swap partition of the size you decided on, then right click again and create an ext3 partition of the remaining space.

You will now have inside your extended sda2 - 2 ntfs partitions next to each other, 1 ext3 and 1 swap partition.

_Installation_

Close the editor and click the install icon.

Go through the process until you come to the partition part, now use the manual option.

You will now have a list of your partitions - again :D

select the new ext3 partition, close to the bottom of this window is a button marked edit - click that and then in the new window use the mountpoint dropdown menu to select a mountpoint of /

close that window, select the ext3 partition and put a tick in the format box for it, be careful not to touch any of the ntfs partitions.

Now carry on with the forward button and the install should proceed.

You get a chance before the end to make sure that you are not touching any of the other partitions - read it to make sure.

---

### Post by anotherconfused1 on 2008-07-01
like this?

---

### Post by Elfy on 2008-07-01
Whoa - no the swap is enormous :D

How much RAM doyou have - and do you need to hibernate?

You have approx 30Gb of space to use I would have 1Gb swap and 29Gb as ext3 - but depends on your needs really.

---

### Post by anotherconfused1 on 2008-07-01
i have 2gb of RAM

---

### Post by Elfy on 2008-07-01
Unless you do heavy duty image editing or need to hibernate then 1Gb swap will be more than enough and likely little used :)

So 29Gb ext3 and 1Gb as swap probably be ok.

---

### Post by anotherconfused1 on 2008-07-01
like this now?

---

### Post by Elfy on 2008-07-01
Yea looks ok as long as you are happy with the unused 3 Gb - if you are hit apply.

---

### Post by anotherconfused1 on 2008-07-01
> **forestpixie said:**
> Yea looks ok as long as you are happy with the unused 3 Gb - if you are hit apply.
Ya, I like having a little space left over.

---

### Post by Elfy on 2008-07-01
Once that's done go back to the post and do the installation bit. Off out for a short while be back later :)

---

### Post by anotherconfused1 on 2008-07-01
installing it now. *crosses fingers*

---

### Post by bab1 on 2008-07-01
I see you doing great on your reinstall of Ubuntu.  Forestpixie is great!

---

### Post by Elfy on 2008-07-01
> **anotherconfused1 said:**
> installing it now. *crosses fingers*

no need for that :)

---

### Post by anotherconfused1 on 2008-07-01
it finished rebooting now. Let you know shortly.
edit: It worked! Thank you oh so much Forestpixie! If not for you, I'd have a huge paperweight.

---

### Post by Elfy on 2008-07-01
You are welcome - could you mark thread solved.

Next thread you make I will expect a proper title :D

---

### Post by hansdown on 2008-07-01
You rock Forestpixie!

---

