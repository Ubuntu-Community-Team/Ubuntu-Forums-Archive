---
title: "Changing Media Ownership"
date: 2014-05-25
forum: New to Ubuntu
---

### Post by Roy_Sperke on 2014-05-25
Hi

,I'm an absolute raw beginner in my 82nd year having great difficulty in changing ownership of my USB Disc and External Hard Drive (on an Apple iMac)

I've used commands as follows:-

 sudo chown -R roy:roy /media/roy/USB Disc/
   
sudo chown -R roy:roy /media/roy/Photos/

Terminal output from a mount search is as follows:-

/dev/sdb2 on /media/roy/000456d2-677a-3039-81c3-1caf87158549 type hfsplus (ro,nosuid,nodev,uhelper=udisks2)
/dev/sde2 on /media/roy/USB Disc type hfsplus (ro,nosuid,nodev,uhelper=udisks2)
/dev/sdc2 on /media/roy/Photos type hfsplus (ro,nosuid,nodev,uhelper=udisks2)

Will some kind soul please provide me with the correct commands?

Kind regards to all

Roy

---

### Post by SeijiSensei on 2014-05-25
> /dev/sdb2 on /media/roy/000456d2-677a-3039-81c3-1caf87158549 type hfsplus (ro,nosuid,nodev,uhelper=udisks2)

The "ro" option mounts the device **r**ead-**o**nly.  Is that the entry in /etc/fstab?  You might try removing the "ro" item and remounting the device.

---

### Post by coffeecat on 2014-05-25
That your external drives are being mounted on /media/roy/*/ suggests that you are running Ubuntu on your Apple iMac rather than OSX. Your output of mount tells us that they are all formatted hfsplus. If they are formatted with the journalled version of hfs+ then they can only be mounted read-only in Ubuntu and you will be not be able to change permissions or ownership of the files from Ubuntu. (In fact, there is a way of force-mounting hfs+ read-write in Ubuntu but it is not reliable and it is not something I would do.) 

If the drives are formatted with the non-journalled version of hfs+ then they would be mounted read-write in Ubuntu and you would be able to change ownership, etc, but since you are having difficulty with this, I suspect that they are journalled hfs+. Besides, the MacOS Disk Utility defaults to journalled hfs+ when formatting drives. 


If you are trying to access/copy files in sub-folders and are unable to do so because of ownership/permissions, I can think of four workarounds:

[list=1][*]Plug the drives into an Apple machine running MacOS and change the permissions there. You can do this either from the GUI (Finder) or from the terminal very much as you are trying to do from Ubuntu, except that the mountpoints would be different.
[*]Use an Apple Mac with OSX to remove the journal from the filesystems.
[*]Use an Apple Mac with OSX to copy the files to a drive formatted with FAT32, where the inconvenient permissions and ownership will be lost. If any of the files you wish to access are more than 4GB, this won't be feasible since FAT32 doesn't allow file sizes greater than 4GB.
[*]Use a root owned file browser in Ubuntu to browse the hfs+ filesystems and thenh copy them to another filesystem/drive where you have more control over permissions and ownership. [/list]

---

### Post by Roy_Sperke on 2014-05-25
Hi,

Many thanks for your responce, I now understand the reasons why I'm unable to change ownsership of MY media.

I appreciate your help.

Kind Regards,

Roy

---

### Post by Roy_Sperke on 2014-05-25
Hi,

Many thanks for your responce, I am imdeed running ubuntu on my Apple iMac.

I hadn't thought about the OS X journelled file system, thanks to your reply I now understand the reasons for my media problems.

Problem is solved.

Kind regards,

Roy

---

