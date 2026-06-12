---
title: "Changing partition label"
date: 2013-04-10
forum: New to Ubuntu
---

### Post by docJ on 2013-04-10
Hi,
now that I am almsot done filling up my internal data drives, I realize I do not like the labels I've given them previously; when accessed from other computers in my network, it could get confusing to have network drive name similar to local's

I do not want to break anything, so how do I proceed (in which order) to rename my Ubuntu internal data drive, considering they are "auto-mounted", have been "chown-ed" and they are samba shared?

Thanks

---

### Post by fantab on 2013-04-10
You can change the labels with "DISKS" Utility. You have to unmount the partitons first, if they are mounted. However, I don't think you can change the label of the Disk itself. (I am not sure about this, so you can ask to confirm).
If you want to change the Label of Ubuntu '/', that is in use, then use LiveDVD/USB.

---

### Post by docJ on 2013-04-10
> **fantab said:**
> If you want to change the Label of Ubuntu '/', that is in use

If you mean **Home** directory (the data partition on the OS drive), I can live with it. I am just concerned about the other hdd's used solely for data.

Will changing the drive label affect auto mounting feature?

---

### Post by fantab on 2013-04-10
I repeat: I don't think we can change the "Drive Label". By 'Drive' I mean HDD. What we can change are the 'Partition' Labels. 

By Ubuntu '/' , I mean the 'OS partition which has your system files'. We can change the the label of '/home' after unmounting it from within the running ubuntu, IF '/home' is a separate partition.

No... changing the 'partition' labels will NOT affect the mounting feature... (unless you have manually created/edited /etc/fstab to use Labels instead of UUIDs).

---

### Post by schragge on 2013-04-10
I've just tried to change the label on a mounted ext4 partition and it worked:
```
sudo e2label /dev/sda5 new_label
``` The partition was mounted by device name, not by label.

---

### Post by docJ on 2013-04-10
My bad: when I wrote drive label, I meant partition label, as my data drives are singled partitioned.
So when I open Disk utility, I need to unmount the partition, & then I am guessing I can rename it from there (?)

---

### Post by docJ on 2013-04-10
The partition labels have been changed on the Ubuntu side, they now show up with their new names, so on the Ubuntu's side, all is well.
When I go on my Win7 pc, click on Computer, the Network, then the Ubuntu pc, I see all data drives, but with former labels. I rebooted Windows but it still shows me the old name...

Is this cause by Windows itself or by Samba not "broadcasting" the updated labels?

---

### Post by docJ on 2013-04-10
Actually, all is not that well on Ubuntu side.
My 3 data drives show up auto-mounted (with their new labels) in that left side "desktop taskbar" (sorry forgot the actual name). Also, when I click the Files folder shortcut (also on the desktop tasbar), I see my 3 data drives mounted and showing up again with updated labels. However, if I use disk utility, they still show up with former names.

I have to admit I ran into an issue trying to unmount within "disk", I was getting exit code 1; only root can unmount
I googled that & found someone that managed to unmount, relabel and remount with Gparted instead (this is what I did)

---

### Post by docJ on 2013-04-10
To go around last issue, I found you need to run disk as```
gksudo palimpsest
```
I am able to unmount, but when I click edit filesystem label, the "new" name is already there; it seems no matter what I label it to, once I remount it, it still shows up in Disk with former label

I guess I need help...

---

### Post by docJ on 2013-04-10
I better clarify my last post. 
In Disk utility window, on the left side, just above mount/unmount button, I do see the updated label.
But on the right side the mount point (above Format volume button) shows the former

I guess I do not understand the difference between partition label and mount point, except they "should" show the same name, or at least for my purpose...

---

### Post by bab1 on 2013-04-10
Let's see what you have right now.  Post the output of this terminal command```
sudo blkid -c /dev/null -o list
```

Put the output between ```
 blocks (using the # icon at the top).  That way it's formatted and easy to read.  Here is what mine looks like:[CODE]device             fs_type   label      mount point            UUID
---------------------------------------------------------------------------------------------------
/dev/sda1          ext4                 /                      c4807753-7a09-4d0a-8052-bf96c1f81d40
/dev/sda2          swap                 <swap>                 69e4c9c7-a439-416d-85a9-c79162983068
/dev/sda3          ext4                 /home                  46a258bf-6ace-4d52-b4d7-db47e7b3de7b

```

---

### Post by docJ on 2013-04-10
This is what I get:
```
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ext4             /              dd45ac45-5856-4fed-9747-77d73c1be122
/dev/sda5  swap             <swap>         1cf17074-3d96-49c2-89b3-11ec33498e90
/dev/sda6  ext4             /home          77d98a43-673a-458e-83fd-a34bb24147a9
/dev/sdb1  ext4    t2       /media/b       9d1b8994-ab09-4d39-8db5-732ac340a791
/dev/sdc1  ext4    U2       /media/c       e4cb3ab6-1be1-4cbd-b01e-62e425c916bf
/dev/sdd1  ext4    V2       /media/d       9398f40a-c0b9-4fe9-9993-afb0cbe8bcbd


```

Where t2, u2, and v2 are the names I wish to see cross-platform

---

### Post by docJ on 2013-04-10
Do I need "labels" at all? 
When I acces from other computer, I seem to see the last part of the mount point (b, c and d) ; I guess its the only thing that need to tbe updated

---

### Post by bab1 on 2013-04-10
What do you mean by "wish to see cross-platform " ?

---

### Post by bab1 on 2013-04-10
> **docJ said:**
> Do I need "labels" at all? 
When I acces from other computer, I seem to see the last part of the mount point (b, c and d) ; I guess its the only thing that need to tbe updated

My point exactly.

[COLOR="#0000FF"]Edit:  The label is only for you to use on the local machine (such as to mount the partition in fstab or some such).[/COLOR]

[COLOR="#0000FF"]I would be more inclined to make sure Samba shares were named appropriately. [/COLOR]

---

### Post by docJ on 2013-04-10
> **bab1 said:**
> What do you mean by "wish to see cross-platform " ?


As per post#7, > The partition labels have been changed on the Ubuntu side, they now show   up with their new names, so on the Ubuntu's side, all is well.
When I go on my Win7 pc, click on Computer, the Network, then the Ubuntu   pc, I see all data drives, but with former labels. I rebooted Windows   but it still shows me the old name...

---

### Post by bab1 on 2013-04-10
> **docJ said:**
> As per post#7,

The partition labels have been changed on the Ubuntu side, they now show up with their new names, so on the Ubuntu's side, all is well.
When I go on my Win7 pc, click on Computer, the Network, then the Ubuntu pc, I see all data drives, but with former labels. I rebooted Windows but it still shows me the old name... 

The partition labels are NOT what you are seeing from the Windows side.  They are the share names.

---

### Post by docJ on 2013-04-10
Indeed this is what I found out, so this thread's title might have been misleading.
I guess I want to edit the share name, so that from windows, I see T2, U2 and V2 as opposed to still seeing b, c and d
How do I do that?

---

### Post by bab1 on 2013-04-10
> **docJ said:**
> Indeed this is what I found out, so this thread's title might have been misleading.
I guess I want to edit the share name, so that from windows, I see T2, U2 and V2 as opposed to still seeing b, c and d
How do I do that?

How did you create the shares on Ubuntu?

---

### Post by docJ on 2013-04-10
Would it be as simple as using```
gksudo nautilus
```, then right-clicking the drive, properties & rename it?

> **bab1 said:**
> How did you create the shares on Ubuntu?
Sorry for being such a hopeless noob, but I don't know what you mean...:confused:

Actually, I beleive I used the last code quote to share the drives

---

### Post by bab1 on 2013-04-10
Yep.  if that is how you originally created the share.

[COLOR="#0000FF"]Edit: What do you mean by "right-clicking the drive"?  You really right-click on a folder and share that.  If the folder is at the root of the partition then you share the entire partition.  In Linux speak the drive is the device.  The physical hard drive.  You DO NOT share hard drives, you share folders on partitions.[/COLOR]

---

### Post by bab1 on 2013-04-10
>     I used the last code quote to share the drives 



What's that mean?

Did you share them using the GUI or by editing smb.conf?

---

### Post by docJ on 2013-04-10
> **docJ said:**
> Would it be as simple as using```
gksudo nautilus
```, then right-clicking the drive, properties & rename it?

I beleive this would work, but I am afaraid to break something else in the process, like auto mounting fstab thing (man, that got me stumped for days...)

---

### Post by docJ on 2013-04-10
> **bab1 said:**
> Did you share them using the GUI or by editing smb.conf?

GUI, nautilus as root, right clicking those drives, then properties, then share tab

---

### Post by bab1 on 2013-04-10
So tell me what you have done.  That won't break anything.  ;-)

I just need to see how you did it,  We aren't changing anything at this point.

What shares are you mounting via fstab?  Do you have multiple Ubuntu hosts?

---

### Post by bab1 on 2013-04-10
> **docJ said:**
> GUI, nautilus as root, right clicking those drives, then properties, then share tab

If you go back and look you will see that you named the share using the share tab.  Tell me about your adventures with fstab.

[COLOR="#FF0000"][B]DON"T CHANGE ANYTHING AT THIS POINT.
[/B][/COLOR]

---

### Post by docJ on 2013-04-10
> **bab1 said:**
> [COLOR=#0000FF]Edit: What do you mean by "right-clicking the drive"?  You really right-click on a folder and share that.  If the folder is at the root of the partition then you share the entire partition.  In Linux speak the drive is the device.  The physical hard drive.  You DO NOT share hard drives, you share folders on partitions.[/COLOR]

Again, by bad, you are right I did right click the B folder, in my mind, its a drive cause its the absolute top root, and my 3 data drives have no internal partitioning

---

### Post by docJ on 2013-04-10
> **bab1 said:**
> Tell me about your adventures with fstab.

[COLOR=#FF0000][B]DON"T CHANGE ANYTHING AT THIS POINT.
[/B][/COLOR]

You bet I won't change a thing !:)

I basically followed instructions to edit fstab so my 3 data drives would auto mount; I can't explain how I did it (as it took me like 3 days to "get it"
If it helps, I guess I can quote the code from this fstab thing (?)

---

### Post by bab1 on 2013-04-10
> **docJ said:**
> Again, by bad, you are right I did right click the B folder, in my mind, its a drive cause its the absolute top root, and my 3 data drives have no internal partitioning

Try and not think in Windows terms.  It will help you in the long run to learn Linux terms.

Your 3 data drives most certainly have been partitioned.  Even if it is only one partition for the entire physical HDD.  The partition is the formatting of the disk so the filesystem (i.e. ext4) can be applied.

---

### Post by bab1 on 2013-04-10
> **docJ said:**
> You bet I won't change a thing !:)

I basically followed instructions to edit fstab so my 3 data drives would auto mount; I can't explain how I did it (as it took me like 3 days to "get it"
If it helps, I guess I can quote the code from this fstab thing (?)

So let's look at that.  Post the output of ```

cat /etc/fstab

```

It should look something like this```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=c4807753-7a09-4d0a-8052-bf96c1f81d40 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=46a258bf-6ace-4d52-b4d7-db47e7b3de7b /home           ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=69e4c9c7-a439-416d-85a9-c79162983068 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


```

---

### Post by docJ on 2013-04-10
```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=dd45ac45-5856-4fed-9747-77d73c1be122 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=77d98a43-673a-458e-83fd-a34bb24147a9 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=1cf17074-3d96-49c2-89b3-11ec33498e90 none            swap    sw              0       0
UUID=9d1b8994-ab09-4d39-8db5-732ac340a791     /media/b     ext4     defaults    0     2
UUID=e4cb3ab6-1be1-4cbd-b01e-62e425c916bf     /media/c     ext4     defaults    0     2
UUID=9398f40a-c0b9-4fe9-9993-afb0cbe8bcbd     /media/d     ext4     defaults    0     2


```

---

### Post by bab1 on 2013-04-10
> **docJ said:**
> ```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=dd45ac45-5856-4fed-9747-77d73c1be122 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=77d98a43-673a-458e-83fd-a34bb24147a9 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=1cf17074-3d96-49c2-89b3-11ec33498e90 none            swap    sw              0       0
UUID=9d1b8994-ab09-4d39-8db5-732ac340a791     /media/b     ext4     defaults    0     2
UUID=e4cb3ab6-1be1-4cbd-b01e-62e425c916bf     /media/c    ext4     defaults    0     2
[COLOR="#008000"]UUID=9398f40a-c0b9-4fe9-9993-afb0cbe8bcbd[/COLOR]     [COLOR="#A52A2A"]/media/d [/COLOR]     ext4     defaults    0     2


```

Simple enough.  For example you have [COLOR="#008000"]a partition[/COLOR] mounted at [COLOR="#A52A2A"]a folder[/COLOR].  This mounts the partition on that drive to you local file system.  This has nothing to do with sharing it at a later date.  It only makes it available in the local file system to be shared.

You can change the name in the properties tab of the shared folder without disturbing the work you have done to the local file system using fstab.
You might find it useful to NOT use the same share as you have used in fstab.  There is no advantage to doing or not doing that.  You will find that it is easier to diagnose problems if there is no ambiguity between mountpoints of partitions and share names.

I would go ahead and right-click on one of the shares you have created and change the name if you like.  But there is no reason to.  The share is functioning correctly now.  The only reason I would change it is to make the share name more descriptive.  For example: On one of my servers I have a folder at /srv/data.  The share name is Public.  The user finds it by //SERVER_NAME/Public.  The users have no need to know where the data actually resides.

---

### Post by docJ on 2013-04-10
I would still prefer to rename the share to T, U and V (this looks like network share when I acces from windows; I didn't like too much seeing network drives marked C & D, messy-messy)
It seems to be working,
Bab1, I cannot thank you enough for sticking with me here.
I will just reboot and make sure nothing explodes (just kidding)
Thanks again !

---

### Post by docJ on 2013-04-10
I am still in one piece after a reboot, I'll call it a night, thanks a million bud!):P

---

### Post by bab1 on 2013-04-10
You might find that it takes awhile for the new share names to show up (15 minutes).  Don't panic if it takes that amount of time.  I'll be back in a couple of hours if you need me.  If it works mark the thread a [SOLVED].  You can do that using [**_[COLOR="#FF0000"]this[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2122459&p=12542445#post12542445") method.

---

### Post by fantab on 2013-04-11
Q: Have you installed Ubuntu within windows with WUBI?

You should change the Windows partition labels with Windows only. You can change them with Linux but I wouldn't recommend it.
Only Linux partitions must be changed from Linux.

[QUOTE=https://www.centos.org/docs/4/html/rhel-ig-x8664-multi-en-4/ap-partitions.html]One area that many people new to Linux find confusing is the           matter of how partitions are used and accessed by the Linux operating           system.  In DOS/Windows, it is relatively simple: Each partition gets           a "drive letter." You then use the correct drive letter to refer to           files and directories on its corresponding partition.         
This is entirely different from how Linux deals with partitions           and, for that matter, with disk storage in general.  The main           difference is that each partition is used to form part of the storage           necessary to support a single set of files and directories.  This is           done by associating a partition with a directory through a process           known as *mounting*.  Mounting a partition makes           its storage available starting at the specified directory (known as a           *mount point*).         
For example, if partition /dev/hda5 is           mounted on /usr/, that would mean that all files           and directories under /usr/ physically reside on           /dev/hda5.  So the file           /usr/share/doc/FAQ/txt/Linux-FAQ would be stored           on /dev/hda5, while the file           /etc/X11/gdm/Sessions/Gnome would not.         
Continuing our example, it is also possible that one or more           directories below /usr/ would be mount points for           other partitions.  For instance, a partition (say,           /dev/hda7) could be mounted on           /usr/local/, meaning that           /usr/local/man/whatis would then reside on           /dev/hda7 rather than           /dev/hda5.         
[/QUOTE]

---

### Post by bab1 on 2013-04-11
> **fantab said:**
> Q: Have you installed Ubuntu within windows with WUBI?

You should change the Windows partition labels with Windows only. You can change them with Linux but I wouldn't recommend it.
Only Linux partitions must be changed from Linux.

It turns out the OP didn't need to change the partition labels at all.  The Samba share names needed to be changed.  Note that the thread has been marked [SOLVED].  :-)

---

