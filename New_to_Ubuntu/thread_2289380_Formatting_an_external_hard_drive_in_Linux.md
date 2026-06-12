---
title: "Formatting an external hard drive in Linux"
date: 2015-08-03
forum: New to Ubuntu
---

### Post by Ralph_Toporoff on 2015-08-03
I am a new user using Ubuntu Linux 14.04 desktop run through Parallels Desktop  on my MacBook Pro.  I am trying to use Ubuntu tot format some hard drives in Linux.  I am creating DCP files that must be housed on a Linux formatted drive.  Linux drives are used by film theaters to project digital picture and sound files in a commercial movie house.  I was told that Ubuntu could be used to do the formatting.  

When I click the “Dash” button, an icon for “Disks” comes up.  When I click on “Disks” the only device that appears is my internal hard drive.  The external hard drives connected by USB 3 are not listed even though I can see them on my Mac desktop.

So, one, is there a way I can format external drives with Linux?  And , two, since I’m not a code writer or programmer can this be accomplished simply, without a lot of alphabet and numbers language.  Ideally it would work simply like Mac formatting which is simply using erase in the Disk Utilities program.   Any help would be greatly appreciated.

---

### Post by sudodus on 2015-08-03
Welcome to the Ubuntu Forums :-)

I suggest that you use the program gparted. It is available directly, if you boot from an Ubuntu install DVD or USB drive and 'Try Ubuntu'.

Otherwise, in a dual boot installed system, you can install it via the Software Center. Then select gparted it with Dash an if the drive is recognized at all, you should be able to format it.

But if you run Ubuntu in a virtual machine (I don't know Parallels Desktop), that is not an option, because you will not see the drives of the host system of the virtual machine.

---

### Post by Ralph_Toporoff on 2015-08-04
Thank you sudodus,  I'm now using gparted and my external hard drives are being recognized.  Now, what to do?  Under formatting I am offered EXT2, EXT3, EXT 4, Linux-swap, FAT 16 and FAT 32.  Which of these is a Linux format and if there is more than one how do you know which one to use?  Thanks again for your assistance and any help again would be greatly appreciated.

---

### Post by sudodus on 2015-08-04
The current linux format that is used by Ubuntu and many other linux distros is ***ext4***.

---

### Post by SeijiSensei on 2015-08-04
It sounds like you're making these disks for someone else.  If so, I'd get some exact specifications, not just a "Linux disc."  Linux supports a wide variety of filesystems, and while ext4 is the most commonly used one on Linux systems themselves, that may not be appropriate for your more specialized task.  XFS, for instance, is a filesystem used widely in the video industry and entirely different from ext4.

---

### Post by Mike_Walsh on 2015-08-04
> **Ralph_Toporoff said:**
> Thank you sudodus,  I'm now using gparted and my external hard drives are being recognized.  Now, what to do?  Under formatting I am offered EXT2, EXT3, EXT 4, Linux-swap, FAT 16 and FAT 32.  Which of these is a Linux format and if there is more than one how do you know which one to use?  Thanks again for your assistance and any help again would be greatly appreciated.

Hallo, Ralph.

The formats 'Ext2','Ext3' & 'Ext4' are** all** Linux formats. 'Linux-swap' is, of course, fairly self-explanatory; it's equivalent to the 'page-file' in Windows.....I confess, I don't know what the equivalent is for Apple products, never having used one.

'Fat16' & 'Fat32' are, of course, the **F**ile **A**llocation **T**able formats most commonly used by Microsoft. These are offered, usually, because if the user wishes to create a common data partition that can be accessed by both Windows and Linux, then these are the easiest ones to use. Not only can Linux read it, but Windows can, too! 'Fat32' is, in this instance, the more widely used of the two; 'Fat16' is a somewhat older format, dating back to the early days of Microsoft, amongst others.

'Ext3' and 'Ext4' are both what are known as 'journalling' file-systems. This means that they have a structure which enables the data to be recovered in the case of a hard-drive failure. 'Ext4' is most commonly used for 'fully-installed' Linux systems (where the .iso file is fully 'un-packed' onto the partition when the O/S is initially set up).....and is essentially a later, more comprehensive development of the 'Ext3' system. This is different from O/Ses like, for instance, Knoppix or 'Puppy' Linux, which have been largely developed from the very beginning to run from external flash media.....and this is why those tend to use 'Ext2'.

'Ext2' does not have this 'journalling' feature, and is more often recommended for use with those Linux distros which are capable of running entirely from a USB stick; it entails fewer read/write cycles, and, as we all know, flash memory has a finite number of read/write cycles before performance becomes degraded to the point where it becomes unusable.

You may find **this** article helpful; there again, 'too much information...' :)

[https://en.wikipedia.org/wiki/File_system#LINUX](https://en.wikipedia.org/wiki/File_system#LINUX)

Hope that helps.


Regards,

Mike.

---

### Post by Geoffrey_Arndt on 2015-08-04
+1 re SeijiSensei . . . . as the file system may be one of the more obscure ones.

---

### Post by oldfred on 2015-08-04
I had no idea what DCP is. But when I looked it up, it had several formats, but mentioned ext2 & ext3 which are older versions. Ext4 is now more common but may not work? It also mentioned some use Windows, but then you could not use Linux formats.

[https://en.wikipedia.org/wiki/Digital_Cinema_Package](https://en.wikipedia.org/wiki/Digital_Cinema_Package)

---

### Post by Ralph_Toporoff on 2015-08-04
I want to thank everyone for their replies.  The information is extremely helpful in getting me up to speed using Linux and Ubuntu.  A small fact that might be of interest:  The DCP is a file system that was developed by the major film studios to deliver a "digital print" of  a motion picture to theaters equipped with digital projection.  The Linux format was chosen because the studios didn't want to allow Apple or Microsoft  to potentially have control over  the digital print.   I can't blame them for that but it has thrown us as film makers into the world of Linux.  Again, can't thank you enough for your help and suggestions.

---

### Post by Ralph_Toporoff on 2015-08-04
So, I'm 2 feet from the goal line and can't seem to get the ball across.   I was successful using gparted in formatting my hard drive with one in EXT2 and one in EXT4.  Ubuntu Linux 14.04 desktop reads my main internal hard drive and under **devices** my external hard drives.  I copied my sound and picture folder successfully  to my main drive and then tried to to copy the folder to my external drives.  I got the following flag:  "Error while copying the folder - sound and picture - cannot be copied because you do not have permission to create it in the destination". If anyone knows why and how I can remedy this problem please let me know.  Again, all help is greatly appreciated.

---

### Post by oldfred on 2015-08-04
With Linux you have to give yourself ownership & permissions to use partition.
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

       #if not known to list partitions, change sda5 to your data partition or create multiples with different mount points
# is comment, do not type
sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data

If you have more than one partition, you have to do above for each one. You can use any mount point description you like to keep them separate. Unmount first if you clicked on them in Nautilus or whatever file manager you are using.

---

### Post by Geoffrey_Arndt on 2015-08-05
If you prefer an option to change the ownership (and thereby the permissions) of a usb stick that's newly formatted for Linux (and so is owned by root) by using a GUI tool, it can be done as follows (just going from memory here, as I can't find the original info file).  Anyway, you need to "juice up" the default Ubuntu file manager (Nautilus) so it runs with root/admin authority:

In a Linux terminal (ctrl+alt+t), input:

>   gksu nautilus (note:  if you get an error at this point, it may be because you don't have gksu installed - so, just open the Ubuntu Software Center and type "gksu" and install it).
>   nautilus will be launched in admin mode (you will be prompted for password),
>   scan the left panel area of nautilus (where files and devices are listed), and right-click the device (usb-flashstickor however it's ID'd),
>   in the pop up menu, click on "properties" option
>   navigate to the "permissions" tab
>   change the ownerships via the drop down selector

You should then be able to add, change, delete, and the new directories (folders and files) will be owned by you.

Close Nautilus and then open it normally (as user) and test the changes.

The above is basically from memory, but should be pretty close to accurate - some folks prefer a gui tool as it's less prone to typo errors due to command line syntax.

---

### Post by Ralph_Toporoff on 2015-08-05
Thank you all for the suggestions and help you've given us about the Linux format.  According to gparted we now have a Ext2 Linux format hard drive. In the Ubuntu desktop we attempted to drag files and folders from our internal hard drive to the external hard drive visible under "devices" and either continue to get permission flags or  an Error message headed "Unable to access 500 GB volume" (our Linux external hard drive)  with an explanation that was an entire paragraph long. We're in the film business not the computer business and marvel at your abilities to write and understand codes.  Until formatting a hard drive in Linux becomes a simple one button click operation like Apple or Microsoft and files can simply be dragged from one hard drive to another we feel we will have to outsource our DCP's to companies that deal with Linux.  If you ever do come up with a system that simple we will be the first ones to buy stock in your company.  Again, thanks you for your  kind and patient help in this matter.

---

### Post by SeijiSensei on 2015-08-05
Outsourcing this task seems a bit of overkill, since it's only a permissions problem that once solved, won't recur again.

Formatting in Windows or OS X is an easier task because those operating systems don't support the vast array of filesystems that Linux and other *nix systems do. Windows in particular only supports Microsoft formats like DOS or NTFS.  OS X, being Unix-based, might be more flexible, but I think any one-click method is going to use the native HFS+ filesystem.

Greater flexibility means more complexity.  Surely there must be someone in your organization willing to invest a little time to learn how to do a few basic tasks in Linux.  Wouldn't that be cheaper in the long run than outsourcing?

---

