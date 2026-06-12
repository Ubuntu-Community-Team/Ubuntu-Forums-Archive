---
title: "Dual boot problems leads to no OS"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by kasyl on 2008-08-27
I have an Acer Aspire 5100 laptop with an AMD Turion 64 x2 TL-56 processor, 2 GB ram, and running Vista Home Premium. I wanted to try out Ubuntu, while retaining my Vista install. I have a 160 GB hard drive, which I shrunk from within Vista, setting aside 40 GB to be used for Ubuntu. (By the way, I was following a tutorial here: [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm) )
Vista was running. I inserted the CD and chose the option that would let me restart my computer and boot Ubuntu 8.04.1 from the CD. It booted Vista up, not the CD. In Vista, I clicked on the option that installed a program that allowed it to boot from the CD. Ubuntu now loaded from  
the disk without a problem.
I began to install Ubuntu. In the partitions setup, I used the 40 GB of unused space and created a new partition out of it. Onto this I installed Ubuntu. One thing I noticed was that on the confirmation screen right before it began installing, it did NOT show "Vista/Longhorn" as the tutorial said it should. I had followed what the tutorial said to do, so I went ahead and installed anyway.
When the computer rebooted, the GRUB boot manager appeared, just as the tutorial showed. Ubuntu loaded fine, but if I chose the Vista option, it would simply reload the GRUB screen again. Also, in Ubuntu, it did not show the Vista partition as one of the available drives. I was stuck in  
Ubuntu.
I searched online for help. I found one solution which was to insert an XP CD (even though it was a Vista machine) and run the startup diagnostic. The solution I found said that it would ask for a password three times, and then begin regardless of whether the password was correct or not. It asked for the password like it said, but never began the diagnostic. I inserted the Vista DVD that came with my laptop. It ran the startup diagnostic and said that it could not repair the errors.
I went back into Ubuntu, but this time loaded it from the Live CD. I went through the installation process again, but at the partition setup, I deleted the partition that had Ubuntu on it. I then closed out without installing and restarted my computer.
I thought Vista would now load, as it is the only OS still on the computer. But all that happens is a GRUB text prompt appears. I cannot load Vista. I can load Ubuntu with the CD, but it is no longer installed. Ubuntu's partition setup in the install process shows my Vista partition is still there, and I never touched it in the whole setup process. All of my files should still be there.
How do I get back Vista without losing all of my files? Getting Ubuntu to actually work correctly dual-booting would be a plus, but I'd like to get it back to normal first.
Please help!

---

### Post by Het Irv on 2008-08-27
I think the first step you should take is restoring your MBR (Master Boot Record).  I am not familiar with the Vista DVD, so I am not sure how to do that.  I know that with XP if you to the recovery console, (at this point I always forget the commands, but I usually type help and look for the command like "fixMBR").

This should get you back to square one.  Then we can try Ubuntu again.

---

### Post by adult swim on 2008-08-27
to restore the vista MBR boot from your vista cd, select recovery and get to where you are at a dos prompt.  if you arent at a c:/> you can get there by typing in C: and hitting enter
then type in ```
bootrec /fixboot
``` hit enter and then type in ```
bootrec /fixmbr
``` hit enter and then reboot.

---

### Post by kasyl on 2008-08-27
I'll try that when I get a chance. I have an XP CD, so it might work. I have NO experience with boot settings, so I'm scared I'll screw something up.

---

### Post by Het Irv on 2008-08-27
> **kasyl said:**
> I'll try that when I get a chance. I have an XP CD, so it might work. I have NO experience with boot settings, so I'm scared I'll screw something up.

From the looks of it you already have :lolflag:

Don't worry if all you are messing with is the boot options, your data should be fine.  

Thanks for that post btw adult swim

---

### Post by kasyl on 2008-08-27
OK, major problems have arisen.
I tried to reset the MBR with the Vista CD. It said drive C was corrupted and couldn't do it. I tried it with the XP CD and it did fine.
Still wouldn't boot Vista. Only the GRUB screen appeared.
I reinstalled Ubuntu. It still says the Vista partition is there, but on the GRUB boot screen, VISTA NO LONGER APPEARS. I HAVE GONE FROM HITTING "VISTA" AND HAVING NOTHING HAPPEN TO HAVING NO "VISTA" TO SELECT!
How could the Vista partition have been corrupted? I didn't even mess with it in the install except to try to make it accessable from Ubuntu, but I _never_clicked "Format!"
Is there any way to save my files, or should I just wipe the whole drive and start from scratch? I REALLY DON'T want to do this, but I don't see any other option. Nothing is working to fix the problem. HELP!

---

### Post by erickghint on 2008-08-27
This may be a shot in the dark, however the tutorial assumes that grub is to load from (hd0,0) and that your windows partition is (hd0,1).... I'm not sure if this is of any help, but I'm thinking that it may be just as easy as making a small edit to the menu.lst . Can you go into a terminal and post the output from this: ```
sudo fdisk -l
```

---

### Post by sandysandy on 2008-08-27
give supergrub disk a try

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

see tutorial

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

[http://www.supergrubdisk.org/wiki/Howto_Fix_Grub](http://www.supergrubdisk.org/wiki/Howto_Fix_Grub)

see this link also

[http://ubuntuforums.org/showthread.php?t=740221](http://ubuntuforums.org/showthread.php?t=740221)

regards

---

### Post by caljohnsmith on 2008-08-28
> **kasyl said:**
> OK, major problems have arisen.
I tried to reset the MBR with the Vista CD. It said drive C was corrupted and couldn't do it. I tried it with the XP CD and it did fine.
Still wouldn't boot Vista. Only the GRUB screen appeared.
I reinstalled Ubuntu. It still says the Vista partition is there, but on the GRUB boot screen, VISTA NO LONGER APPEARS. I HAVE GONE FROM HITTING "VISTA" AND HAVING NOTHING HAPPEN TO HAVING NO "VISTA" TO SELECT!
How could the Vista partition have been corrupted? I didn't even mess with it in the install except to try to make it accessable from Ubuntu, but I _never_clicked "Format!"
Is there any way to save my files, or should I just wipe the whole drive and start from scratch? I REALLY DON'T want to do this, but I don't see any other option. Nothing is working to fix the problem. HELP!
First of all, take a deep breath and relax, because I don't think you have anything to worry about at this point; I've seen exactly this type of situation, and from what you describe, your Vista partition is most likely just fine. :)

Go ahead and reinstall Ubuntu, and when it gets to the part about installing Grub, select the "advanced" option, and make sure that Grub is installed to (hd0), or your HDD's master boot record (MBR). 

The next step is important to fix your Vista partition to make sure it is bootable. When you said previously that selecting Vista from the Grub menu caused you to return back to the Grub menu, that is usually a classic case of Grub being accidentally installed into the boot sector of the Vista partition. The fix is easy though. Just boot up your Vista Recovery CD/DVD, and run the following command from the recovery console/command line:
```
bootrec /fixboot
```
Now your Vista partition should be bootable (assuming no other problems). If you don't have an option to boot Vista on start up, I can help you add it if you first boot into Ubuntu and post the output of:
```
sudo fdisk -lu
cat /boot/grub/menu.lst
```
Let me know how it goes. :)

---

### Post by maybeway36 on 2008-08-28
I've always used DOS for this sort of thing. You should probably try what caljohnsmith said first, but if you have a floppy or CD that boots FreeDOS, you can type
```
fdisk /mbr
```
This will get rid of GRUB completely, but Vista should be bootable.

---

### Post by kansasnoob on 2008-08-28
Caljohnsmith,

I'm curious about this command:

"Code: sudo fdisk -lu
cat /boot/grub/menu.lst"

I've never used the fdisk -lu but rather just -l. What's the difference. Still learning here:confused:

---

### Post by caljohnsmith on 2008-08-28
> **maybeway36 said:**
> I've always used DOS for this sort of thing. You should probably try what caljohnsmith said first, but if you have a floppy or CD that boots FreeDOS, you can type
```
fdisk /mbr
```
This will get rid of GRUB completely, but Vista should be bootable.
I don't think kasyl would want to run that command, because that puts the Windows XP boot loader in the MBR; Ubuntu won't be able to boot as you point out, but as far as I know Vista won't boot either (I've never tried using a Win XP boot loader to boot Vista, but maybe it's possible). :)

---

### Post by caljohnsmith on 2008-08-28
> **kansasnoob said:**
> Caljohnsmith,

I'm curious about this command:

"Code: sudo fdisk -lu
cat /boot/grub/menu.lst"

I've never used the fdisk -lu but rather just -l. What's the difference. Still learning here:confused:
That's a good question; I like to use the "u" option because fdisk then reports partitions in terms of sectors (512 bytes) rather than "cylinders", which can be some really crazy number of bytes. For instance, on my HDD 1 cylinder = 8222838.9 bytes. In other words, it is much easier with the "u" option to see exactly where in terms of MB or GB a partition starts and stops, and how big it is. But with "cylinders" you have to do some math to figure it out, so I try to do it the easy way with the "u" option. :)

---

### Post by Gone fishing on 2008-08-28
Adult swim's post - I'd say is the correct thing to do to fix Vista, it not working is a concern.

I'd boot up on the ubuntu live disk an see if Vista mounts, If it does I'd then copy  stuff I needed onto a flash drive or a second hard drive. If Vista is there and the ntfs partition mounts the Vista is probably OK.

I'd try installing the GAG bootloader gag.sourceforge.net and seeing if it will boot Vista, then delete the Linux partition and reinstall Ubuntu loading grub onto the root partition or fixing grub by installing it on the root partition.

---

### Post by kasyl on 2008-08-28
> **caljohnsmith said:**
> First of all, take a deep breath and relax, because I don't think you have anything to worry about at this point; I've seen exactly this type of situation, and from what you describe, your Vista partition is most likely just fine. :)

Go ahead and reinstall Ubuntu, and when it gets to the part about installing Grub, select the "advanced" option, and make sure that Grub is installed to (hd0), or your HDD's master boot record (MBR). 

The next step is important to fix your Vista partition to make sure it is bootable. When you said previously that selecting Vista from the Grub menu caused you to return back to the Grub menu, that is usually a classic case of Grub being accidentally installed into the boot sector of the Vista partition. The fix is easy though. Just boot up your Vista Recovery CD/DVD, and run the following command from the recovery console/command line:
```
bootrec /fixboot
```
Now your Vista partition should be bootable (assuming no other problems). If you don't have an option to boot Vista on start up, I can help you add it if you first boot into Ubuntu and post the output of:
```
sudo fdisk -lu
cat /boot/grub/menu.lst
```
Let me know how it goes. :)

I've tried the "bootrec/fixboot" thing in the command prompt of the Vista DVD. It said that C:/ was corrupted. I was able to do it with an XP CD I happen to have, but there was no change.

---

### Post by caljohnsmith on 2008-08-28
> **kasyl said:**
> I've tried the "bootrec/fixboot" thing in the command prompt of the Vista DVD. It said that C:/ was corrupted. I was able to do it with an XP CD I happen to have, but there was no change.
That's not a good sign, so here is what I would do first:
[LIST=1]
[*]Boot the Ubuntu Live CD
Open a terminal, and do:
```
sudo fdisk -lu
```
[*]Find which /dev/sdX device is your Vista partition (sda1, sda2, sda3, etc); it will type NTFS under the "system" category. Next mount it, replacing sdX with its real device name:
```
sudo mount /dev/sdX /mnt
```
[*]Does that return any errors? If not, next do:
```
ls -l /mnt
```
Does that show your Vista root directory? 
[/LIST]
When you report back, please post the output of *all* the above commands.

---

### Post by kasyl on 2008-09-01
It has been fixed. I'm running Vista again.
Nothing within Ubuntu would recognize my Vista partition, so I used the Vista DVD to redo the partitions, wiping out Ubuntu and leaving only my untouched Vista partition and the rest as unallocated free space. I then used SuperGrub and manually booted from the Vista partition, as regular Grub STILL won't recognize it. But it works.
I'm going to try to reinstall and dual-boot Ubuntu, but this time with the help of a friend who knows Linux. Unlike myself.
Thanks for all the help.

---

### Post by Het Irv on 2008-09-02
If you still have problems with a dual-boot the second time around, I suggest using Wubi.  I is very easy to set up.

---

