---
title: "How-To Clone your Hard drive using Gparted"
date: 2006-11-19
forum: Outdated Tutorials &amp; Tips
---

### Post by squidward_tentacels on 2006-11-19
How-To Clone your Hard drive using Gparted

   Hello, This is my first “How-To” so go easy on me , It is also written be easily understandable to beginners, so if I'm insulting your vast technical capabilities with my simplified instructions, this “How-To” probably isn't for you : P

   I decided to write this guide after deciding to replace my old 30gb Harddrive, with a new 200gb harddrive. Its is a dual-boot between Dapper & XP, but this should work regardless of OS's. Cloning or “disk imaging” is superior to re installation as you get to keep all your settings and installed apps (plus you wont need to reactivate Windows and spend 5 hours downloading security updates from Micro soft, and sitting through a dozen reboots.) Searching around the forums here, and elsewhere, I have not come across an easier more intuitive method than the one I'm going to cover here. This guide makes a few assumptions that are necessary to use this method.

1.You have access to a computer that will support multiple hardrives, and IDE cabling.
2.You are comfortable playing with BIOS harddrive detection settings, and jumper settings on the harddrive(s).
3.You will also need to download and burn an ISO  of Gparted Live bootable cd, available for download here; [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)
***Note; You may be able to just use the Ubuntu Live CD version of Gparted, but I have not tried it.
4.You have backed-up anything you cant afford to loose before beginning. Any time you muck around with partitions, there is always a chance that due to some unforeseen bug, or user error you can hose your install and loose everything!
5.You have a Ubuntu live CD handy, as you will most likely need to reinstall grub at the procedures end.

   OK, the first step is to install the new drive as a slave drive into the appropriate bay in your box. Jumper settings vary from manufacturer to manufacturer, but make sure the drive is set to slave, and in the slave position on the IDE cabling.  Always remove the power cord and ground yourself before accessing your computer innards. Next, boot into BIOS and auto-detect the new slave drive.  Don't worry too much if the BIOS does not detect the correct sized slave drive. This is fairly common on older BIOS's , as long as it does detect there is a drive installed as slave you should be alright. My 200 gb drive was recognized as 137gb by the BIOS, but Gparted did not have any difficulty detecting the correct size.

   Now that both drives are installed power up the box, and enter BIOS settings. Normally F12 or something like that. It varies between manufactures, so youll have to watch at power on. Now you want to auto detect the new slave drive and make sure that it is “seen” by the systems BIOS. As well as ensuring that the BIOS is enabled to bot from cd first.

Unless you have special needs or something is not detected right, you can pretty much keep hitting enter thru the various choices of gpartrd, as settings such as keyboard , screen resolution, etc are normally detected right. Soon you should arrive at the screen in which you can view your current partitioning scheme on the disk you are planning to clone. 

A drop down arrow in top right hand corner should toggle between the current disk /dev/hda and your target disk /dev/hdb. Switch to /dev/hdb and ensure the size has been correctly detected and delete any existing partitions on this disk (/dev/hdb!) if it is not a new disk. 

Now switch back to /dev/hda and copy first partition. Just click on selected partition and choose copy. Switch over to /dev/hdb, and paste the first partition into the unallocated space. At this point you may resize the new partition to whatever size you desire, either through dragging the edge of the partition window, or by manually entering the size in the window beneath. Repeat this step as needed until all partitions are copied over, arranged and sized to your liking. Don't forget to leave some room at the disks end for swap.

   Click apply after the pasted preview of new partitions looks good, sit back and let copy process even error checks for file system errors and attempts to fix any if found, the ext3 file system is pretty robust, and I don't know that Ive ever encountered and file system errors.

Once the file system check is completed the actual copying/cloning process will begin, This make take some time depending on system resources available, and the sheer amount of data being copied.

   If you click on the details arrow you can  watch the new partitions being created, optimal blocksize determined, followed by the  transfer of data, once the operation is complete Gparted will begin a file integrity check of the new ext2/ ext 3 File system. 
Note; NTFS file systems will not be error checked, as I believe Gparted lacks the ability to "see" inside the partition an merely copies the image whole. Next time windows is booted on the new cloned drive, chkdisk will most likely start after boot in protest to such callous treatment. I have used this method  several times now and I have yet to see chkdisk find any bad sectors etc from this process

   All right, Nothings Blown up so far? Good : ) There may be an error about being unable to verify the contents of the NTFS partition, but we can safely ignore that. As long as all operations completed, we should be good to go. The next step is to remove the cloned drive. Make sure and set the jumper back to Master before reinstalling the new drive into the machine, or BIOS will not auto-detect it. 

Run Auto-detect and you should see the new drive, as Master. If the BIOS does not properly detect the new size of the hard drive you may have to manually enter the information, Normally found on the top of the drive (if you have an older machine, you may consider jotting this info down before installing the new drive to save yourself the trouble of pulling it back out to get this information, if you suspect theres is going to be an issue with auto-detect)

OK, the moment of truth is upon us.....We boot up and ..Nothing?? All you have now is a black screen with a blinking cursor? Fear not, You have your Ubuntu Live cd, right?
The problem here is the Computer cant find grub. To fix this we just need to reinstall grub.


For this section of the tutorial I'm going to borrow (aka cut 'n paste) from an outstanding grub how-to by catlett. The thread in its entirety can be found here; [http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Boot the Ubuntu live CD,  once you reach the desktop, open a terminal

<code>

sudo grub

</code>

This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

<code>

find /boot/grub/stage1

</code>

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

<code>

root (hd?,?)

</code>

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

<code>

setup (hd0)

</code>

Finally exit the grub shell
<code>

quit

</code>

That is it. Grub will be installed to the mbr.
When you reboot, you will have the grub menu at startup, and should be able to boot into your new cloned drive! I have successfully used this method to clone drives various times, and only had it fail once, with an I/O error. I kinda think that was from not putting the side of the case back on which alters the airflow path across the CPU, and got it too hot. 
I am still kind of a "gn00b" myself, and if anyone has any revisions or suggestions, I will be happy to revise this.
Good Luck!

---

### Post by Jose Catre-Vandis on 2006-11-19
Nice howto and good work, I kinda do this without referring to notes (!) but this serves as a useful reminder of how it should be done :)

---

### Post by oliverb on 2006-11-19
I found that the gparted found on the dapper liveCD appears incapable of copying between devices. The command line "parted" on the CD won't even try, you can only enter a source and dest part number on the same device. I think it's possible to force it using dd but I'd rather not go there.

Update: The latest version on the Gparted LiveCD is better and does copy partitions from one drive to another.

---

### Post by Richardinho on 2009-01-28
This looks great! I have been wanting to do this exact thing and have been searching around for hours for this. I'm using Gutsy and I have a dual boot with Windows XP. Essentially I want to clone the entire contents of my hard disk so that if it were to fail I would still have all my data, all my settings, my two operating systems,and all my programs (photoshop for example). Am I correct in assuming that this process will accomplish this?

---

### Post by dereknashvilleff on 2009-03-24
Just wanted to say this is awesome. I just made a clone of my hardrive and i did not even have to reload grub. just swapped the jumper and off she went. Good post.;)

---

### Post by Towermax on 2009-04-02
Excellent--worked perfectly!

---

### Post by dcstar on 2009-04-03
Please note that copying partitions using the Partition Editor retains the UUID of the partitions.

This is ideal if you are wanting to make "clones" of the partitions, but if you want to use them as extra partitions then you have to set a different UUID:

```
sudo tune2fs -U random /dev/whatever
```

---

### Post by BoDwayne on 2009-04-05
> **dcstar said:**
> Please note that copying partitions using the Partition Editor retains the UUID of the partitions.

This is ideal if you are wanting to make "clones" of the partitions, but if you want to use them as extra partitions then you have to set a different UUID:

```
sudo tune2fs -U random /dev/whatever
```

Thank you, I had exactly this problem - /sda1 and /sdb1 are trying to use identical UUIDs. Actually, the new cloned disk (sdb1) still has its old UUID somehow tied to it - I saw it on an error message when it was trying to boot - and this is causing a conflict

My QUESTION - If I use the above code and generate a random UUID for my cloned disk, do I then have to correct the grub menu.lst and/or somewhere else (like /etc/fstab or something) to point to this new UUID??

---

### Post by BoDwayne on 2009-04-06
I think I answered my own question - although there may have been an easier way.  
I used the above code to change the UUID on the cloned disk.  Then I edited **/etc/fstab** and **/boot/grub/menu.lst** to point to the new UUID.  Actually, in the menu.lst, I _added_ info for my new drive, leaving me the option of booting into the old.  =Make SURE you _know which disk_ you are editing!=

This allowed me to boot up to the new disk, but at the login screen I got several 'permissions' errors.  I clicked "okay" past all these and got to my desktop.  But here, I saw only my wallpaper, no menu bars.  So, I used Ctrl+Alt+F2 to get into a shell.  And here, I used:

sudo chown -R *username:username* /home/*username*

sudo chmod 644 /home/*username*/.dmrc

sudo chmod 644 /home/*username*/.ICEauthority

Then, with a reboot, I seemed to have everything.  Tedious, but I got there.

---

### Post by bhp0528 on 2009-07-23
Thanks much for the walk through. One question about your procedure. When you say to type in:
```
setup (hd0)
```
Does that mean that I should actually be typing
```
setup (hd?)
```
Where '?' is from the output of the command:
```
find /boot/grub/stage1
```
In my case these were the same values so I didn't worry about it but wanted to know in case the drive was in the secondary position.

---

### Post by cszikszoy on 2009-07-24
Thank you very much for this great guide.  This worked perfectly for me!

---

### Post by mjstelly on 2009-07-31
This may be all well and good for situations where the origination and destination drives reside within the same machine. But what if they don't? 

I want to clone my current config (on this box), so I can duplicate it on another machine. I, too, consider myself a Linux n00b, but technology expert. So, it's a bit frustrating for me when I know that something can be done, but not how to do it. 

Detailed instructions would be greatly appreciated. In the meantime, I'll keep scouring the forums.

Thanks.

Update: Found what I was looking for [here]("http://ubuntuforums.org/showthread.php?t=35087&highlight=disk+imaging"). Or search the forum for "disk imaging." :P

---

### Post by lineman78 on 2009-08-10
I have not yet attempted this, so sorry if it is an obvious question, but is it difficult to clone the partition and resize it at the same time using this method.  I ask because I am contemplating replacing the HDD in my netbook for a SSD, but my HDD is 160GB and most SSDs come in 120 GB.

---

### Post by wizard10000 on 2009-08-10
> **lineman78 said:**
> I have not yet attempted this, so sorry if it is an obvious question, but is it difficult to clone the partition and resize it at the same time using this method.  I ask because I am contemplating replacing the HDD in my netbook for a SSD, but my HDD is 160GB and most SSDs come in 120 GB.

Sure, but you'd shrink the source partition before you cloned it.

---

### Post by lineman78 on 2009-08-10
> **wizard10000 said:**
> Sure, but you'd shrink the source partition before you cloned it.
That's what I suspected, but was hoping the tool allowed you to only do it on the target drive during the copy.

---

### Post by oldrocker99 on 2009-08-12
Very good tutorial; thanks a lot!

:guitar:

---

### Post by lazyfirecloud on 2009-08-25
Thanks for this tutorial =). 
I just wanted to add a note for those who have an MBR instead of grub. Note that you can also copy the gurb instead of reinstall it using dd.

I personally have a dual-boot with Linux on the master hard drive and Windows on the slave hard drive. The slave also has 2 partitions: OS and data. The master has grub and the slave has MBR.

This is how I copied my system over:
1) create the partitions so that you leave 63 sectors for the MBR. 
2) use dd to copy the first 446 bytes of the MBR over to your new hard drive.
3) copy the partitions' content to the new drive
4) grow your partitions to desired size (optional, see below)

instructions for steps 1 and 2:
I found out about steps 1 and 2 from a great set of instructions for the first 2 steps at:
[http://www.nilbus.com/linux/disk-copy.php](http://www.nilbus.com/linux/disk-copy.php)

instructions for steps 3 and 4:
I used gparted for steps 3 and 4 (following the instructions from the tutorial)
For step 3, gparted will automatically check the filesystem, fix errors and use ntfsclone to copy the partition over (if it's NTFS).

Note:
* You can probably create larger partitions off the bat and copy to them, thus eliminating step 4.
* You can probably even create and copy the partitions in gparted and then use dd to copy the MBR. I think gparted will leave the 63 sectors for you to write in automatically. You can right-click on a partition in gparted and choose "information" to see the beginning and ending sectors.

---

### Post by DJonsson2008 on 2009-09-19
This worked for me going between from an IDE to a SATA drive.
Gparted did choke when attempting to resize, but robustly enough
had completed the copy task. 

The drive rebooted without having to run grub, this was for 
for a single-boot Ubuntu install.

I'll try resizing later. 

This went a lot easier than I thought it would, 
took about 30 mins for 30gigs of OS partion.

Thanks for this.
:popcorn::popcorn:

---

### Post by Jhongy on 2010-08-18
> **squidward_tentacels said:**
> 
Boot the Ubuntu live CD,  once you reach the desktop, open a terminal

<code>

sudo grub

</code>

This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

<code>

find /boot/grub/stage1

</code>

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

<code>

root (hd?,?)

</code>

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

<code>

setup (hd0)

</code>

Finally exit the grub shell
<code>

quit

</code>



This doesn't seem to be correct: you are asking grub to find /boot/grub/stage1, and then install to that disk based on information in /boot. However, in a LiveCD, won't /boot be the live CD's /boot partition?

To repair your real grub, with information in your actual boot directory, you would have to mount your / or /boot somewhere, then tell grub-install where that is with the --root-directory parameter. Alternatively, if you have a separate /boot partition, you could rm -rf the live CD's /boot, then mount your real /boot partition there instead, then just run grub-install.

I may be wrong... and anyway Grub will probably install just fine in most cases (particularly for most users with only one disk) even if you do base in on the live CD's /boot (it worked for you after all), but it seems  a bit pointless to bother typing find /xxx in that case -- just install it to any (or the first) hdd's MBR.

---

