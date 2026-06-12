---
title: "Ubuntu on a pen drive"
date: 2013-02-20
forum: New to Ubuntu
---

### Post by fractalife on 2013-02-20
Hello! This is my first post on this forum. For lack of a better segue, I'm going to get right to my question. I have a pen drive (64 GB) which I plan to use for Ubuntu. I used the pen drive linux installer (as recommended here: [http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows ). However this is just the "Live CD" version of Ubuntu. I want to actually install the operating system on the pen drive, rather than just have a bootable "live cd" version of it. Unfortunately I don't know much about making USB drives bootable. Currently any changes I make are lost as soon as I restart the computer. I would like the OS to recognize changes, just as it would if it were installed on a hard drive. Any recommendations would be much appreciated! ]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows")

Also, I don't know how to terminate the URL on these forums, so it seems as though that entire paragraph following http:// was linkified. 
[ ]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows")

---

### Post by thermion on 2013-02-20
You could run the installer from another usb drive and when you get to the point where the setup is asking you to format/partition your drive, simply choose your 64 GB usb drive and make sure the bootloader gets installed on your 64 GB drive aswell. But I fear the performance will be terrible, since read/write speeds on such devices are too slow.

---

### Post by sudodus on 2013-02-20
> **thermion said:**
> You could run the installer from another usb drive and when you get to the point where the setup is asking you to format/partition your drive, simply choose your 64 GB usb drive and make sure the bootloader gets installed on you 64 GB drive aswell. But I fear the performance will be terrible, since read/write speeds on such devices are too slow.
+1
I have such an installation with Lubuntu on a 16GB USB 3 pendrive. It works quite well to run also in USB 2 ports. The worst part is updating in USB 2, because writing many small files is very inefficient.

An alternative is a persistent live system, where changes (new files etc) are stored in a casper-rw file or partition. You can find several new threads at the Ubuntu Forums discussing this topic.

These systems are portable (between computers) if you avoid proprietary drivers (typically for graphics and wifi).

---

### Post by JayKay3OOO on 2013-02-20
Performance sucks in USB2, but using a distro like Puppy Linux is a far better alternative or damn small linux if for some reason you must run your operating system from a flash drive.

Windows 7 can be run from a flash drive too, but again performance is. whatever.

---

### Post by Jay_E on 2013-02-20
Hey there.

I Think there is another aspect to your question - persistent memory.
This is a file that is put onto the USB where your changes, bookmarks, photos, 
and stuff will be put and saved.

AND there is a gotcha. At least there used to be.
If you put 100% it just won't work.
Put 90 %

OK.

Another Gotcha
the file system of the USB is a limitation.
I think the program has a requirement that it has to be "fat".

That means there is a limit of 4 gigs to the file size.
That means you want a 16 gig usb stick

You can do the same with an 8gig or 4 gig - if you can find one cheaply.

Oh yes.
Have fun.   :popcorn:


Jay

---

### Post by sudodus on 2013-02-20
> **Jay_E said:**
> ...
Another Gotcha
the file system of the USB is a limitation.
I think the program has a requirement that it has to be "fat".

That means there is a limit of 4 gigs to the file size.
That means you want a 16 gig usb stick
...
Jay
With a partition for persistence, you have no such limitation :-)

---

### Post by C.S.Cameron on 2013-02-20
Following is step by step how to a **Full** install of 12.04 on a 8GB flash drive. 
For a larger drive increase partition size(s):

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD or Live USB.
Start the computer, the CD/USB should boot.
Select language.
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Continue
At "Installation type" select "Something else".
Continue
Confirm Device is correct.
Select "New Partition Table" 
Click Continue on the drop down.

(Optional partition for use on Windows machine)
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1000 megabytes.
Location = Beginning.
"Use as:" = "FAT32 file system".
And "Mount point" = /windows.
Select "OK"

Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4500 to 6000 megabytes, Beginning, Ext4, and Mount point = "/" then OK.

(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1000 to 4000 megabytes, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional swap space, allows hibernation)

Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1000 to 2000 megabytes, or same size as RAM), Beginning and "Use as" = "swap area" then OK.

(Important)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".

Select your location.
Continue.
Select Keyboard layout.
Continue.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are worried about loosing your USB drive.
Select Continue.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
You may do an update-grub later.

---

### Post by C.S.Cameron on 2013-02-20
Following is how to make a Persistent install to flash drive:

Boot Live CD or Live USB.
Plug in flash drive.
Start gparted.

Create 2 GB FAT32 partition, (on the left side of the bar). (size is optional, extra space can be used for file storage and transfer to Windows machines).

Create a 4 GB ext2 partition to the right of this, labeled it "casper-rw". (ext3 and ext4 also work).

Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition).

Close gparted.
Un-mount and re-mount flash drive.
Start "Create a live usb startup disk", (usb-creator).
Select "Discard on shutdown".
Press "Make Startup Disk.
When usb-creator finishes, Go to the root folder of your Live USB
    Enter the syslinux directory, (or for UNetbootin the root directory).
    Make the syslinux.cfg file writeable
    Replace the contents of the file syslinux.cfg with:

```
    default persistent
    label persistent
      say Booting a persistent Ubuntu session...
      kernel /casper/vmlinuz
      append  file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz quiet splash noprompt --
```

Shutdown, remove CD, reboot.


First time booting go to users and groups and create an account with yourself up as an Administrator, with password if desired.

Note:
The above code will bypass the Try/Install and Language screens.

---

