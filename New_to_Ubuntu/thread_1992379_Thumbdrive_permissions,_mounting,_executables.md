---
title: "Thumbdrive permissions, mounting, executables"
date: 2012-05-31
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2012-05-31
I'm having a big problem with my thumbdrive (AKA flashdrive, pendrive et alia). 

I want to use LastPass's sesame. It's written for Ubuntu. It worked fine, yesterday, after someone helped me with

1-making a directory for the device
2-mounting the device according to: 

sudo mount -t vfat /dev/sdb1 mnt/ -o uid=1000,gid=1000,umask=022

and then, when (in Thunar GUI file manager) sesame was executed (clicked on), it ran properly.

Today, on rebooting the computer the sesame is now reporting permissions problems AGAIN.

I thought maybe I was barking up the wrong tree looking at the sesame and not the filesystem, so I searched these forums for some insight.

I read here:

[http://ubuntuforums.org/showthread.php?p=10839425&posted=1#post10839425](http://ubuntuforums.org/showthread.php?p=10839425&posted=1#post10839425)

and here:

[http://askubuntu.com/questions/88106/how-to-solve-my-partition-table](http://askubuntu.com/questions/88106/how-to-solve-my-partition-table)

and would like to try 

fdisk -f

to see if it is the easiest way to fix this mess.

I've a .iso of Precise Pangolin v. 12.04 and can run the LiveCD and run fdisk. But I have some questions:

1- how can I run fdisk -f in LiveCD as root, when I'm not a password allowed user?

2- I only want to run the fdisk -f against the thumbdrive where the linux executable is. How is that doable?

---

### Post by strask on 2012-05-31
> **Mark_in_Hollywood said:**
> I'm having a big problem with my thumbdrive (AKA flashdrive, pendrive et alia). 

I want to use LastPass's sesame. It's written for Ubuntu. It worked fine, yesterday, after someone helped me with

1-making a directory for the device
2-mounting the device according to: 

sudo mount -t vfat /dev/sdb1 mnt/ -o uid=1000,gid=1000,umask=022

and then, when (in Thunar GUI file manager) sesame was executed (clicked on), it ran properly.

Today, on rebooting the computer the sesame is now reporting permissions problems AGAIN.

Let's focus on the above, I don't think fdisk is required or helpful for your problem.

My best guess as to what is happening is that you mounted the device properly before rebooting, but that the system mounted it with different options when you rebooted. All you need to do is set it up to mount correctly at boot time, or alternately unmount it and re-type the sudo mount command you listed above.

First a question or two: Do you leave this thumbdrive plugged in all the time, or do you just plug it in at some point after the system boots?

Secondly, is the sesame application stored on the thumb drive? Or does the thumb drive just have data that sesame needs to access?

---

### Post by Mark_in_Hollywood on 2012-05-31
First a question or two: Do you leave this thumbdrive plugged in all the time, or do you just plug it in at some point after the system boots?

It is always plugged into a usb hub

Secondly, is the sesame application stored on the thumb drive? Or does the thumb drive just have data that sesame needs to access?

Yes, sesame is on the thumb drive. It must be there for LastPass to make a 2 step authentication. Calling sesame opens a LastPass applet that makes a one time password. After authenticating that, a 2nd password must be entered from within a browser. (FF, Chrome, Opera, and even msie)

I will umount the device and run the code again. Made no difference. sesame won't run.

df -h


/dev/sdc1       3.7G  925M  2.8G  25% /mnt

sudo fdisk -l

Disk /dev/sdc: 3942 MB, 3942645760 bytes
122 heads, 62 sectors/track, 1018 cylinders, total 7700480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008884e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              62     7700151     3850045    c  W95 FAT32 (LBA)

---

### Post by strask on 2012-05-31
Do this for me:```
mount
``` and then ```
ls -ld /mnt
```

The mount command will show what mount options are being used, while the ls command will show us the current permissions on /mnt.

---

### Post by Mark_in_Hollywood on 2012-05-31
relevant part of 

mount

/dev/sdc1 on /media/LEXAR_ type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)

and all the terminal said:

mark@Lexington-19:/$ ls -ld /mnt
ls: cannot access /mnt: No such file or directory

---

### Post by strask on 2012-05-31
I'm confused because above it was mounted on /mnt, and now it is under /media/LEXAR_. 

Regardless, you need to do the following I think:

```
sudo umount /media/LEXAR_
sudo mkdir /LEXAR                             (you can call this whatever you want)
sudo mount /dev/sdc1 /LEXAR -o uid=1000,gid=1000,umask=022
```

Test if the application works. Then, assuming it works, add a line like this to /etc/fstab:```

/dev/disk/by-uuid/38BEBD30698717C7 /LEXAR    vfat    uid=1000,gid=1000,umask=022    0    2
```    
Note that you need to change the UUID at the beginning to match your thumbdrive's UUID; you can figure this out by doing```
ls -l /dev/disk/by-uuid
``` and looking for the one linked to /dev/sdc1.

The reason we mount by UUID instead of just /dev/sdc1, is that the drive letters can change if you later plug in another thumb drive or something.

---

### Post by Mark_in_Hollywood on 2012-05-31
sesame is providing authentication. thanks.

Working somewhat backwards:

mark@Lexington-19:/$ ls -l /dev/disk/by-uuid
total 0

lrwxrwxrwx 1 root root 10 May 31 13:15 8874-D051 -> ../../sdc1

so, while I'm guessing, "8874-D051" is the uuid for the thumbdrive (Lexar /dev/sdc1 - currently)

sudo umount /media/LEXAR_
sudo mkdir /LEXAR
sudo mount /dev/sdc1 /LEXAR -o uid=1000,gid=1000,umask=022

(WHY does the above line read "LEXAR_"? - none the less, the mkdir ran successfully. Well, it did seems to transfer all the objects on the removable drive to the /LEXAR - but I guess I can put them back on the thumbdrive.

so, as sesame can be called by clicking it from a file manager (window) and as it operates as expected, I have created this line for the

fstab

#Entry for /dev/sdc1
/dev/disk/by-uuid/8874-D051	/LEXAR    vfat    uid=1000,gid=1000,umask=022    0    2

I hope to hear from strask before I save the fstab file.

Do I need to backup fstab first?

Do I need to reboot?

just a few more moments of your time, sir.

PS - I just noticed that the thumdrive is not showing up as a device in the panel dropdown menu. Yikes!

---

### Post by strask on 2012-05-31
> **Mark_in_Hollywood said:**
> Well, it did seems to transfer all the objects on the removable drive to the /LEXAR - but I guess I can put them back on the thumbdrive.
...
PS - I just noticed that the thumdrive is not showing up as a device in the panel dropdown menu. Yikes!

We didn't transfer the objects from the thumb drive to the /LEXAR directory; what we did was move the whole thumb drive from the /media directory (which is for removable media that you hotplug all the time) to the /LEXAR mount point.

Since you said you always leave the thumbdrive plugged in, we are causing the system to treat it just like it does an internal drive -- mount at boot, have a fixed home in the filesystem (/LEXAR) and don't show up as a removable drive.

If that's not what you want, we can change it back but then you will have to type mount commands every time you reboot in order to get it working. Unless someone knows a better way.

---

### Post by strask on 2012-05-31
> **Mark_in_Hollywood said:**
> 
#Entry for /dev/sdc1
/dev/disk/by-uuid/8874-D051    /LEXAR    vfat    uid=1000,gid=1000,umask=022    0    2

I hope to hear from strask before I save the fstab file.

Do I need to backup fstab first?
You should always make a backup of system files before modifying them, sorry for not reminding you of this in my original instructions. :)

Your line looks good, by the way.

> Do I need to reboot?

First, try "sudo umount /LEXAR" followed by "sudo mount /LEXAR"; when you don't provide mount options on the command line it looks at the /etc/fstab to figure out what you omitted, and that will confirm that the fstab is still healthy. That way you don't discover a problem at boot time, which can be painful.

---

### Post by Mark_in_Hollywood on 2012-05-31
mark@Lexington-19:/$ sudo umount /LEXAR
[sudo] password for mark: 
mark@Lexington-19:/$ sudo mount /LEXAR
mount: mount point /LEXAR does not exist

please know that the thumbdrive, named LEXAR does not appear in the panel's drop down menu. All this mount/umount should have it showing as: LEXAR.

I cannot find an object (folder, device, etc.) in neither / nor /home - nor in /etc but there is, in /media a LEXAR. I can't open that folder as non-root-user. As root, it opens, but appears empty.

PS - fstab w/o added /sdc1 & uuid is backed up within /etc

---

### Post by strask on 2012-05-31
> **Mark_in_Hollywood said:**
> mark@Lexington-19:/$ sudo umount /LEXAR
[sudo] password for mark: 
mark@Lexington-19:/$ sudo mount /LEXAR
mount: mount point /LEXAR does not exist
That is Bizarre! Why is the /LEXAR directory going away?

If you recreate it (sudo mkdir /LEXAR) does the mount command succeed? If you then repeat the umount/mount does the directory disappear again? I am so confused. :(

> please know that the thumbdrive, named LEXAR does not appear in the panel's drop down menu. All this mount/umount should have it showing as: LEXAR.

I cannot find an object (folder, device, etc.) in neither / nor /home - nor in /etc but there is, in /media a LEXAR. I can't open that folder as non-root-user. As root, it opens, but appears empty.
That all sounds normal to me, nothing to worry about as long as we can get the mounting and unmounting to behave consistently. Once it's working you can add a shortcut to your panel pointing at /LEXAR and that will make things easy.

> PS - fstab w/o added /sdc1 & uuid is backed up within /etc
Excellent.

Since the umount/mount commands didn't complain about fstab errors I don't think we will need that backup, but keep it around just in case.

---

### Post by Mark_in_Hollywood on 2012-05-31
mark@Lexington-19:/$ sudo mkdir /LEXAR
[sudo] password for mark:  [terminal returned]
mark@Lexington-19:/$


mark@Lexington-19:/$ sudo mount LEXAR

Thunar shows /LEXAR in /


mark@Lexington-19:/$ sudo umount LEXAR

Thunar shows NO /LEXAR in /

==== a few moments later ======

just playing with it:

mark@Lexington-19:/$ sudo mount LEXAR
mount: can't find LEXAR in /etc/fstab or /etc/mtab

I hope this helps.

---

### Post by strask on 2012-05-31
You need to put the slash at the front, so /LEXAR not LEXAR.

That still doesn't explain why the mount point is being removed every time we unmount.

What version of Ubuntu are you using? I am on Ubuntu 12.04; I'm starting to wonder if you are on an old version with a bug or something. I'm seriously confused about this.

---

### Post by Mark_in_Hollywood on 2012-05-31
Sorry, this is Precise Pangolin v. 12.04 LTS. But, for what it's worth, I've always had trouble mounting/unmounting USB drives, whether Seagate 3.5" drives in an external cradle, or simpler USB thumbdrives.

Please know that the thumbdrive, named LEXAR, until I started trying to fix this mess, is plugged into the usb hub port.

It has semi-critical data on it and as I have this device in a risky place, I would like to see the data that is on it, before I mess something up.

---

### Post by strask on 2012-05-31
Ok I found the bug : [https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/498423](https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/498423)

I'm not positive, but it looks like it should not be a problem after we reboot, as long as you are leaving the drive plugged in all the time. If you hotplug the drive, then use manual commands to mount it on /LEXAR again, then umount it, it will continue to delete the mount point.

> **Mark_in_Hollywood said:**
> It has semi-critical data on it and as I have this device in a risky place, I would like to see the data that is on it, before I mess something up.

Absolutely. To see the data on the drive, just recreate the mount point and mount it again:
```
sudo mkdir /LEXAR
sudo mount /LEXAR
```That assumes we still have the new line in the fstab. Once mounted, just browse to /LEXAR in your file manager or whatever to reassure yourself that your data is safe.

Edit: This is annoying, but actually before rebooting unmount it again (sudo umount /LEXAR) which will delete the mount point, then make the mount point again (sudo mkdir /LEXAR) and DON'T mount it, THEN reboot. That should be the last time you have to type manual commands.

---

### Post by Mark_in_Hollywood on 2012-05-31
Upon reboot (warm boot), LEXAR exists in / - and sesame can be executed and it properly authenticates.

But where is the thumbdrive? It's not on in the panel drop down list.

lsusb shows:

Bus 001 Device 009: ID 05dc:a769 Lexar Media, Inc. 

but since both the folder from sudo mkdir /LEXAR and the usb drive have the same name, "LEXAR", something is amiss. And I hope I'm not getting ahead of you here. But I'm somewhat lost in what we're doing.

and 
sudo fdisk -l shows:

Disk /dev/sdd: 3942 MB, 3942645760 bytes
122 heads, 62 sectors/track, 1018 cylinders, total 7700480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008884e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              62     7700151     3850045    c  W95 FAT32 (LBA)

do I have to edit /etc/fstab to reflect that the thumbdrive is now called: /dev/sdd?

---

### Post by strask on 2012-05-31
> **Mark_in_Hollywood said:**
> Upon reboot (warm boot), LEXAR exists in / - and sesame can be executed and it properly authenticates.
Excellent. I fully expect that to continue to work for you forever now.

> But where is the thumbdrive? It's not on in the panel drop down list.

The /LEXAR folder IS your thumbdrive. It just doesn't look so much like a thumb drive now. The icon or appearance may have changed (we don't use the same desktop environment, so I'm not sure what yours looks like) but it's exactly where it is supposed to be.

You can create a shortcut in Thunar or whatever to make it simple to click over to /LEXAR in the future.

If you need to safely remove the drive while the system is running, just use ```
sudo umount /LEXAR
``` and once it's unmounted, it's safe to remove.

---

### Post by strask on 2012-05-31
> **Mark_in_Hollywood said:**
> do I have to edit /etc/fstab to reflect that the thumbdrive is now called: /dev/sdd?

No, because we used the UUID to specify it in the fstab, you don't need to worry about the drive letter changing.

---

### Post by Mark_in_Hollywood on 2012-05-31
A few more moments, please. 

Upon

sudo umount /LEXAR

and using the file manager to see /

LEXAR appears. Should it, if it's unmounted? (worry-wart-me)

and

Please see the attached screenshot, left side frame, where you can see 3 other usb thumbdrives, but not LEXAR. It used to appear in that list. But even after sudo mount /LEXAR it's not to be seen. Is this critical?

... a few moments later:

mark@Lexington-19:/LEXAR$ sudo umount /LEXAR
umount: /LEXAR: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
mark@Lexington-19:/LEXAR$ 

and it will not unmount.

Maybe we should call it quits for now, but the whole point of having the linux executable on a removeable device is to prevent computer use unless it's plugged in. The 'system' is a 2-step authentication, requiring 2 passwords, but one must be generated from the thumbdrive executable. If I can't remove the thumbdrive and take it to another computer, I've defeated the purpose LastPass.

---

### Post by strask on 2012-05-31
> **Mark_in_Hollywood said:**
> sudo umount /LEXAR

and using the file manager to see /

LEXAR appears. Should it, if it's unmounted? (worry-wart-me)

Yes that's exactly what we want; that folder needs to stick around so that it mounts correctly at boot time. It will just be empty if the drive isn't mounted.

> Please see the attached screenshot, where you can see 2 other usb thumbdrives, but not LEXAR. It used to appear in that list. But even after sudo mount /LEXAR it's not to be seen. Is this critical?

Not at all critical. Possibly a minor inconvenience for you, but much less of an inconvenience than needing to type mount commands every time you boot.

The list of thumb drives that you show in that screen shot is a list of drives that ***the system mounted automatically when plugged in, but that were not listed in the fstab***. It won't list drives that you mount with manual mount commands, because those aren't automatic. And it won't list drives that you put in the fstab. That's just kind of the way it works.

Like I said before, you should be able to add a shortcut to your file browser to make /LEXAR show up on your left-hand navigation pane; I use a different file manager though so I'm not sure of the exact steps. But even if you add that shortcut, the icon won't look like a thumb drive... just a folder.

---

### Post by strask on 2012-05-31
> **Mark_in_Hollywood said:**
> mark@Lexington-19:/LEXAR$ sudo umount /LEXAR
umount: /LEXAR: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
mark@Lexington-19:/LEXAR$ 

and it will not unmount.

It won't unmount if you have the folder open in your file manager, or if the program on the thumb drive is running, or if it's otherwise in use. In this case, your terminal session is currently in the folder you are trying to unmount. Try "cd /" and then unmount again. :)

> Maybe we should call it quits for now, but the whole point of having the linux executable on a removeable device is to prevent computer use unless it's plugged in. The 'system' is a 2-step authentication, requiring 2 passwords, but one must be generated from the thumbdrive executable. If I can't remove the thumbdrive and take it to another computer, I've defeated the purpose LastPass.

You can remove it as long as it's not in use. I'm sorry you are feeling frustrated, but think how much you have learned today. It's a lot to absorb all at once. We are basically done, and once you get used to it it will be super easy.

---

### Post by Mark_in_Hollywood on 2012-05-31
Thanks for your time, and especially for your patience.

---

### Post by strask on 2012-05-31
I love linux: It only takes 5 hours to mount a thumb drive. :-D

---

### Post by Mark_in_Hollywood on 2012-07-23
THIS IS AN ADDENDUM to the above posts.

After a removable device is mounted per this manner, where the file system of the drive is NOT linux based, the drive cannot be "ejected". It must be: sudo umount /device-name-of-some-sort. Then it can be safely removed. And, I believe, by the converse, it mounts by: sudo mount/proper-name-or-location.

As my thumbdrive sits in / and has the name: LEXAR the command stirng is:

sudo mount (or umount) /LEXAR

by the bye: I first cd / 

to get to the / directory.

---

