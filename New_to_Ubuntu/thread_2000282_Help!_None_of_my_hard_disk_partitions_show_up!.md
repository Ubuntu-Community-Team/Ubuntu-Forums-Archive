---
title: "Help! None of my hard disk partitions show up!"
date: 2012-06-09
forum: New to Ubuntu
---

### Post by rangarajan14 on 2012-06-09
Hello,
  I and new to Ubuntu and I installed Ubuntu 12.04 a few days back and everything was working fine. I decided to dual boot with Windows XP, had the GRUB loader problem, corrected it by updating GRUB and all was well.
  Now all of a sudden, none of my disk partitions show up in "Computer" other than the "Filesystem" and "Floppy 0" as shown below
[IMG]http://i49.tinypic.com/34xome0.png[/IMG]
  
  When I tried fdisk in the terminal, it showed all the partitions details, but I am not able to access it from the computer or through any of the menus in different applications.

[IMG]http://i47.tinypic.com/xeel4g.png[/IMG]  

  I am pretty sure I am missing out something simple, but for the love of god can't figure out what. Any help would be much appreciated.

Thanks,
Regards,
Rangarajan.

---

### Post by Basher101 on 2012-06-09
run Gparted (install it if you do not have it), make a screenshot of it and post it here


regards

---

### Post by rangarajan14 on 2012-06-09
Installed Gparted and here are the screen shots.
Of my 160 GB hard disk:
[IMG]http://i50.tinypic.com/2dqm5ug.png[/IMG]
I have installed Ubuntu in this harddisk and I have no idea why it is shown as unallocated.

My 80 GB hard disk:
[IMG]http://i45.tinypic.com/339sgsi.png[/IMG]
And I am sure the "sdb2" you see in this pic belongs to the other hard disk, because I made all partitions in this drive as approximately 20 GB.

Also, I can open and work these drives through Windows XP.

Thanks,
Rangarajan.

---

### Post by rangarajan14 on 2012-06-09
I also played around with GRUB Customizer. Could that have caused any damage?

---

### Post by fantab on 2012-06-09
> **rangarajan14 said:**
> I also played around with GRUB Customizer. Could that have caused any damage?

If its a desktop computer you can check the cable that connects to HDD. 

Or you may have to reinstall Ubuntu. I don't think playing around with Grub Customizer will erase your partitions. Unless of course you played around with disk utility. 

If you get issues like HDD not found etc during install then you must check the cable that connects to HDD in a Desktop or Laptop.

---

### Post by arpanaut on 2012-06-09
Fire up GParted again then click on the exclamation mark next to "unallocated"
This will usually give a good explanation of what is wrong and what to do to correct.

Many times this problem occurs when ntfs/fat partitions are not cleanly un-mounted and 
linux will not read the partition.  Often running chkdisk from windows will clear the problem.

But read the error message and see what it suggests.

---

### Post by critin on 2012-06-09
> **rangarajan14 said:**
> 
My 80 GB hard disk:
[IMG]http://i45.tinypic.com/339sgsi.png[/IMG]
[B][COLOR=Red]And I am sure the "sdb2" you see in this pic belongs to the other hard disk, because I made all partitions in this drive as approximately 20 GB.
[/COLOR][/B] 
Also, I can open and work these drives through Windows XP.

Thanks,
Rangarajan.


The "sdb2" is the BLUE extended partition that holds the partitions - 5,6, and 7.  
The other HD is identified by  "sda"

---

### Post by deadflowr on 2012-06-09
From the look of your fdisk in your first post. It looks like you have a primary partition(/dev/sda3) tuck inside your extended partition. This is the most likely cause of the disk being unable to be read correctly.Typically, sda1,sda2,sda3,sda4 are allocated primary,or extended partitions, logical partitions usually sda5 and beyond.From the looks you have sda1 as primary, sda2 as extended, and sda3 as primary. As you see, sda3's sectors reside inbetween sda6, and sda7, and is most likely causing confusion, and thus the reason why gparted shows unallocated, with a bold red exclamation error icon.

---

### Post by oldfred on 2012-06-09
Good catch deadflowr, I missed it.

This is probably the easiest way to fix that type of issue.

First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt


Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by rangarajan14 on 2012-06-09
> **arpanaut said:**
> Fire up GParted again then click on the exclamation mark next to "unallocated"
This will usually give a good explanation of what is wrong and what to do to correct.

Many times this problem occurs when ntfs/fat partitions are not cleanly un-mounted and 
linux will not read the partition.  Often running chkdisk from windows will clear the problem.

But read the error message and see what it suggests.

Tried running chkdsk /f from Windows. It didn't work. 
The error message in GParted is "Can't have overlapping partitions"

---

### Post by rangarajan14 on 2012-06-09
> **oldfred said:**
> Good catch deadflowr, I missed it.

This is probably the easiest way to fix that type of issue.

First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt


Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

This FixParts can be used only for broken partition tables but not overlapping issues right? The error in GParted was "*Can't have overlapping partitions*".
So, what do I do now?

---

### Post by oldfred on 2012-06-09
Your partitions do not overlap on a sector basis. Overlap is where the end sector of one partition is after the beginning of another. Yours are just mis numbered or a primary partition is in the middle of the extended partition which I guess gparted is calling overlap. The extended partition can only have logical partitions inside it.

Only if you have a full install of Windows in sda3 may you then have further issues. Just change sda3 to a logical. If other partitions get renumbered you may have to reinstall grub2's boot loader or edit fstab, but both primarily use UUIDs which do not change, so probably not an issue.

---

### Post by deadflowr on 2012-06-09
> **oldfred said:**
> Your partitions do not overlap on a sector basis. Overlap is where the end sector of one partition is after the beginning of another. Yours are just mis numbered or a primary partition is in the middle of the extended partition which I guess gparted is calling overlap. The extended partition can only have logical partitions inside it.

Only if you have a full install of Windows in sda3 may you then have further issues. Just change sda3 to a logical. If other partitions get renumbered you may have to reinstall grub2's boot loader or edit fstab, but both primarily use UUIDs which do not change, so probably not an issue.

+1
From the original post I would assume, you installed XP after you installed Ubuntu. In oldfred's first post, the first link explains about how an XP install can change a logical partition into a primary partition.If I look at your /dev/sda partitioning scheme, you had one primary, and one extended partition(broken into several logical partitions) XP needs a primary partition, so it created one, however, the only space it could use resided in the extended partition, which it can't do, as primary partitions can't reside in extended partitions, as they are not logical.

---

### Post by rangarajan14 on 2012-06-09
> **deadflowr said:**
> +1
From the original post I would assume, you installed XP after you installed Ubuntu. In oldfred's first post, the first link explains about how an XP install can change a logical partition into a primary partition.If I look at your /dev/sda partitioning scheme, you had one primary, and one extended partition(broken into several logical partitions) XP needs a primary partition, so it created one, however, the only space it could use resided in the extended partition, which it can't do, as primary partitions can't reside in extended partitions, as they are not logical.
Yeah, that's right. I installed XP after installing Ubuntu. Also, I have no idea on how to change a partition to a logical. Any help on how to do that would be great. 
Would all this be possible without any data loss? I don't have an external drive to backup everything right now.
Would re-installing Ubuntu help with this and is it possible to re-install Ubuntu without losing any of my settings, customizations and installations?

---

### Post by deadflowr on 2012-06-09
You could always look into remastersys

[http://www.remastersys.com/index.html]("http://www.remastersys.com/index.html")

I also know that if you have an ubuntuone account, you can save, up to 5GB, files through the deja-dup back-up program installed by default in Ubuntu.(In system settings)

Of course these are just two options I can think of off the top.

When you do finally figure out what way to back-up your setting and reconfigure your partition scheme, I would suggest that you create three primary partitions and then an extended partition, then create as many logical partitions as needed(with one as a swap).How you utilize them is, of course, up to you.

---

### Post by oldfred on 2012-06-09
If you look at the instructions on fixparts it will offer all you partitions and whether you can change from primary to logical or vice-versa. The rules on partition tables limit what you can do, but you should be able to just change sda3 to logical.

---

### Post by rangarajan14 on 2012-06-10
> **oldfred said:**
> If you look at the instructions on fixparts it will offer all you partitions and whether you can change from primary to logical or vice-versa. The rules on partition tables limit what you can do, but you should be able to just change sda3 to logical.
In the fixpart tutorial  [here]("http://www.rodsbooks.com/fixparts/") when the MBR command is given as to print the partition table, it shows every partition and whether it is logical and/or primary and so on. 
But this is what I get when I do the same:
[IMG]http://i48.tinypic.com/11gpnhf.png[/IMG]
So now, how do I convert just sda3 into a Logical partition?

Thanks,

**EDIT: Never mind this post, I made a mistake and uploaded the wrong screen shot.**

---

### Post by oldfred on 2012-06-10
The drive sdc is your flash drive. It shows 7.5GB so it is a 8GB flash drive.You need to run fixparts on sda unless drives change which sometimes they do.

---

### Post by rangarajan14 on 2012-06-10
I can't believe I made that dumb mistake. Anyway, ran fixpart on sda and this is what I got. Apparently sda3 is set to Logical already:


```
FixParts 0.8.1

Loading MBR data from /dev/sda
EBR describes a logical partition!

MBR command (? for help): p

** NOTE: Partition numbers do NOT indicate final primary/logical status,
** unlike in most MBR partitioning tools!

** Extended partitions are not displayed, but will be generated as required.

Disk size is 312581808 sectors (149.1 GiB)
MBR disk identifier: 0x2CE82CE8
MBR partitions:

                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1      *             63     41945714   primary     Y        Y      0x07
   3              83891493    197197874   logical     Y        Y      0x07
   5              41947136     81829887   logical     Y        Y      0x83
   6              81831936     83890175   logical     Y               0x82
   7             197197938    312560639   primary     Y        Y      0x07

```
And for sdb:
```
FixParts 0.8.1

Loading MBR data from /dev/sdb

MBR command (? for help): p

** NOTE: Partition numbers do NOT indicate final primary/logical status,
** unlike in most MBR partitioning tools!

** Extended partitions are not displayed, but will be generated as required.

Disk size is 156301488 sectors (74.5 GiB)
MBR disk identifier: 0x10891088
MBR partitions:

                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1      *             63     40965749   primary     Y        Y      0x07
   5              40965813     77834924   logical     Y        Y      0x0B
   6              77834988    114704099   logical     Y               0x0B
   7             114704163    156280319   logical     Y        Y      0x07

```
What do I do now?
I won't be able to backup the contents anytime soon and UbuntuOne is out of the question because I have a really slow upload speed and it would take ages to finish.
Also, both XP and Ubuntu are on the same hard drives, (160 GiB, i.e sda) but on different 20 GiB partitions.
So, will re installing ubuntu work? And I just have the alternative installer, so I can re install with that right?

---

### Post by flemur13013 on 2012-06-10
> Yeah, that's right. I installed XP after installing Ubuntu.My free advice is: if you have two disks, one with Windows and the other with Linux, do your OS installs on the desired disk with the other disk physically disconnected (IOW, disconnect, as in "remove cables", the linux disk when installing windows on the other disk, and vice-versa).  And, if you can select the system to boot with BIOS, do that rather than using grub to boot Windows. After you have both OSs installed, you can hook up both disks. Also, LABEL your partitions!

---

### Post by coffeecat on 2012-06-10
> **rangarajan14 said:**
>  Apparently sda3 is set to Logical already:

Not quite. I think you missed this bit in the fixparts tutorial that oldfred linked:

> FixParts checks the validity of the partitions it finds on your disk and will automatically (and silently) make adjustments for certain problems it finds. Thus, you may discover that your partition table is fine at this point. It's also possible that you'll see some changes in primary vs. logical status, or even omitted partitions.

Fixparts would have detected the impossibility of a primary partition inside an extended and made the adjustment automatically for you. For many situations it is enough to open fixparts, and then run the 'w' command to rewrite the partition table and exit.

Also - the situation you have encountered is not uncommon when installing Windows after Ubuntu where there are Linux logical partitions already present. In certain situations, usually when one of the primary partition "slots" is free, the Windows installer will happily try to "convert" a Linux logical partition into a primary one by creating an illegality in the partition table - as has happened to you. Thank goodness for fixparts, say I!

---

### Post by rangarajan14 on 2012-06-10
> **coffeecat said:**
> Not quite. I think you missed this bit in the fixparts tutorial that oldfred linked:



Fixparts would have detected the impossibility of a primary partition inside an extended and made the adjustment automatically for you. For many situations it is enough to open fixparts, and then run the 'w' command to rewrite the partition table and exit.

Also - the situation you have encountered is not uncommon when installing Windows after Ubuntu where there are Linux logical partitions already present. In certain situations, usually when one of the primary partition "slots" is free, the Windows installer will happily try to "convert" a Linux logical partition into a primary one by creating an illegality in the partition table - as has happened to you. Thank goodness for fixparts, say I!
Yeah alright I did that, set it to logical anyway, wrote the changes to disk. The next time I restarted the system, all I get is the GRUB error and a "grub rescue>" prompt.
I am now working off my 9.10 live cd. The first thing I checked was my data and all are safe. The partitions are as I made it and there has been no damage to it.
How do I fix this now?
Should I re install GRUB? How do I do that?

---

### Post by HarryTorry on 2012-06-10
First off, boot from your LiveCD.

Determine the partition number of your main partition. GParted can help you here. I'm going to assume in this answer that it's /dev/sdb1, but make sure you use the correct partition number for your system!

Next, mount your partition:
```
sudo mount /dev/sdb1 /mnt  # make sure that sdb1 is correct!
```

Bind mount some other necessary stuff:
```
for i in /sys /proc /run /dev; do sudo mount --bind "$i" "/mnt$i"; done
```

chroot into your Ubuntu install:
[HTML]sudo chroot /mnt[/HTML]

At this point, you're in your install, not the live CD, and running as root. Update grub:
```
update-grub
```

If you get errors, continue;

Depending on your situation, you might have to reinstall grub:

```
grub-install /dev/sda
update-grub # I'm not sure if this is necessary, but it doesn't hurt.
```

If everything worked without errors, then you're all set:
```
exit
sudo reboot
```
At this point, you should be able to boot normally.




[SIZE="4"]ALTERNATIVELY[/SIZE]

You can download *Super Grub2 Disk* from [**[COLOR="DarkOrange"]here![/COLOR]**]("http://www.supergrubdisk.org/category/download/supergrub2diskdownload/") Make a boot cd/usb of it, and check up on how to use it.


The second option will probably be easier for you however!

---

### Post by rangarajan14 on 2012-06-10
Finally got it. Here's what I did just in case someone else with the same problem stumbles upon this thread:
[LIST]
[*]Installed Fixpart, set the partition 'sda3'(in my case) to logical
[*]That screwed up the bootloader and re installed GRUB from a live cd. I found instructions for that [here]("http://ubuntuforums.org/showthread.php?t=1014708")
[*]Restarted the system again, GRUB worked fine, booted Ubuntu, all the partitions were visible again and working perfectly.
[*]Also booted into XP just in case and that's working fine.
[/LIST]
Thanks a lot guys. Fistbumps to everyone around.
Marking this thread as solved. Just hoping I don't run into anymore trouble with this.

Thanks a ton,
Rangarajan.

---

### Post by HarryTorry on 2012-06-10
I'm curious, not sure if I should make a thread or ask here so I'll just ask here and hope for a reply!

Would a simple ***sudo update-grub*** have fixed it?

---

### Post by rangarajan14 on 2012-06-10
> **HarryTorry said:**
> I'm curious, not sure if I should make a thread or ask here so I'll just ask here and hope for a reply!

Would a simple ***sudo update-grub*** have fixed it?
Coming to think about it, I should have tried that. Once before, the boot loader showed just the Windows installation. Searched online for that and found that this method worked for that. 
But here, I got an unknown filesystem error as one gets if he completely removes linux but the GRUB loader still remains. So just wanted to be sure and re installed GRUB.

---

