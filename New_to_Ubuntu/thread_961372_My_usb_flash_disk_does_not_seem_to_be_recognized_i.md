---
title: "My usb flash disk does not seem to be recognized in Ubuntu, but it does on Windows"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by bcasanov on 2008-10-28
Hi,

I have a 1 GB Staples Relay USB flash drive with some files on it.  On Windows XP, the flash drive is recognized and an Explorer window pops up showing all the files on the drive.  On Ubuntu, both in Hardy and now in Intrepid, nothing seems to happen when I insert the USB flash drive.  No pop-up Nautilus window showing the contents of the drive, no mounted USB icon on the desktop, nothing.  How can I get the drive to be recognized in Ubuntu?

---

### Post by SunnyRabbiera on 2008-10-28
well keep in mind that Linux is not windows and sometimes some devices dont like linux.
With this staples device i am not surprised if you are having issues, they might use some generic maker for their stuff that doesnt care and works only for MS.
Maybe you should make a trade in, sometimes these generics are not worth it in the long run

---

### Post by Zzl1xndd on 2008-10-28
Can't say if its the same as the one I used to own, But a few years ago I had a staples relay and it worked the second I pluged it in.

---

### Post by SunnyRabbiera on 2008-10-28
> **tweakedenigma said:**
> Can't say if its the same as the one I used to own, But a few years ago I had a staples relay and it worked the second I pluged it in.

Yeh though devices like this are touch and go, thats why I dont buy generics no matter how cheap they are especially for linux use.
For more professional devices at decent prices places like newegg are a better bet...
Heck even best buy can make a good deal (I got a really good deal on my memory upgrade)

---

### Post by Zzl1xndd on 2008-10-28
Agreed, I only grabed it cause I worked at staples and got to test it first. 

For the OP I did just pick up a 4gig Kingston at Futureshop for 10 dollars.

---

### Post by philinux on 2008-10-28
> **bcasanov said:**
> Hi,

I have a 1 GB Staples Relay USB flash drive with some files on it.  On Windows XP, the flash drive is recognized and an Explorer window pops up showing all the files on the drive.  On Ubuntu, both in Hardy and now in Intrepid, nothing seems to happen when I insert the USB flash drive.  No pop-up Nautilus window showing the contents of the drive, no mounted USB icon on the desktop, nothing.  How can I get the drive to be recognized in Ubuntu?

With it unplugged post the output of lsusb.
Plug it in and repeat lsusb.

---

### Post by fuser312 on 2008-10-28
safely remove ur device frm windows and then try it in ubuntu.

---

### Post by bcasanov on 2008-10-28
The result of lsusb without the flash drive plugged in is:

```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

The result of lsusb with the flash drive plugged in is:
```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by philinux on 2008-10-28
Well that shows it's defo not being picked up.

Plug it in and then from the terminal post the output of this.
Use copy and paste.
```
 cat /var/log/messages | tail -30
```

---

### Post by bcasanov on 2008-10-28
The result of cat /var/log/messages | tail -30 is:

```
Oct 28 08:38:15 dell kernel: [15089.511483] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17                                                    
Oct 28 08:38:15 dell kernel: [15089.511971] iwl3945: Radio disabled by HW RF Kill switch                                                                        
Oct 28 08:38:15 dell kernel: [15089.512050] iwl3945 0000:0c:00.0: PCI INT A disabled                                                                            
Oct 28 08:38:17 dell kernel: [15091.089128] tg3: eth0: Link is up at 100 Mbps, full duplex.                                                                     
Oct 28 08:38:17 dell kernel: [15091.089139] tg3: eth0: Flow control is off for TX and off for RX.                                                               
Oct 28 08:38:17 dell kernel: [15091.089488] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready                                                                   
Oct 28 08:38:26 dell gnome-screensaver-dialog: pam_sm_authenticate: Called
Oct 28 08:38:26 dell gnome-screensaver-dialog: pam_sm_authenticate: username = [diazbeat]
Oct 28 08:38:26 dell gnome-screensaver-dialog: Error attempting to parse .ecryptfsrc file; rc = [-5]
Oct 28 08:38:26 dell gnome-screensaver-dialog: Unable to read salt value from user's .ecryptfsrc file; using default
Oct 28 08:38:27 dell gnome-screensaver-dialog: Passphrase key already in keyring
Oct 28 08:38:27 dell gnome-screensaver-dialog: There is already a key in the user session keyring for the given passphrase.
Oct 28 09:07:09 dell -- MARK --
Oct 28 09:27:09 dell -- MARK --
Oct 28 09:43:41 dell sudo: pam_sm_authenticate: Called
Oct 28 09:43:41 dell sudo: pam_sm_authenticate: username = [diazbeat]
Oct 28 09:43:41 dell sudo: Error attempting to parse .ecryptfsrc file; rc = [-5]
Oct 28 09:43:41 dell sudo: Unable to read salt value from user's .ecryptfsrc file; using default
Oct 28 09:43:42 dell sudo: Passphrase key already in keyring
Oct 28 09:43:42 dell sudo: There is already a key in the user session keyring for the given passphrase.
Oct 28 09:44:33 dell syslogd 1.5.0#2ubuntu6: restart.
Oct 28 10:07:09 dell -- MARK --
Oct 28 10:27:09 dell -- MARK --
Oct 28 10:41:40 dell kernel: [22494.424310] usb 4-1: new high speed USB device using ehci_hcd and address 2
Oct 28 10:41:55 dell kernel: [22509.557538] usb 4-1: configuration #1 chosen from 1 choice
Oct 28 10:45:17 dell kernel: [22711.303703] usb 4-1: USB disconnect, address 2
Oct 28 11:07:09 dell -- MARK --
Oct 28 11:27:09 dell -- MARK --
Oct 28 11:46:13 dell kernel: [26367.624168] usb 4-1: new high speed USB device using ehci_hcd and address 3
Oct 28 11:46:28 dell kernel: [26382.761386] usb 4-1: configuration #1 chosen from 1 choice

```

---

### Post by bcasanov on 2008-10-28
Is it a matter that can be fixed, or is it simply that the USB disk is not compatible at all with Linux?

---

### Post by zachalekos on 2008-10-28
Try installing pysdm
you'll find in Administration as Storage Device Manager.
Plug your usb stick and refresh.

---

### Post by bcasanov on 2008-10-28
I installed pysdm.  I plugged in the USB stick and hit Refresh, but nothing happened, I think.  It only showed my hard drive partitions.

---

### Post by Sailorcancer on 2008-10-28
I'm having the same problem with my USB external HDD.  I know it works in Linux cause back in the day when I tried Xubuntu it saw it just fine.

---

### Post by philinux on 2008-10-28
> **bcasanov said:**
> Is it a matter that can be fixed, or is it simply that the USB disk is not compatible at all with Linux?

From reading a bug on launchpad it could be the staples drive. U3 was mentioned.
The bug is this. [https://bugs.launchpad.net/ubuntu/+bug/268859](https://bugs.launchpad.net/ubuntu/+bug/268859)
This guy tried formatting the drive as fat32 in windows too.

---

### Post by bcasanov on 2008-10-28
Wow, it seems I'm having the exact same problems as this guy.  I, too, formatted the USB drive to fat32.

---

### Post by mac71 on 2008-10-28
Is it recognised if you plug it in before you boot into ubuntu?

---

### Post by ChildOfMana on 2008-10-28
I had a very similar problem and here's how I fixed it (although this may or may not work for you - so do the following at your own risk).

**_WARNING:_ this will destroy all data on the drive so if you can still access it from Windows then back it up first!!

Okay, now you've been warned, on with the instructions...

first, plug the drive in and then open a terminal and type the following:
> 
sudo fdisk -l (note the -l is a lower case L, not a number one)

You should see something like the following (this is my output - yours will differ but you should get the picture):

> Disk /dev/sdc: 4026 MB, 4026531840 bytes
124 heads, 62 sectors/track, 1022 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

Note that your Hard Disk(s) will show up higher in the list - I've cut that bit out here to save space. As long as you identify the USB drive (in my case /dev/sdc) then you'll be okay.

Once you've identified which is your USB drive (the size is a good indicator), type the following into the terminal:

> sudo fdisk /dev/sdc

**Replace /dev/sdc with the path to _your_ USB drive - be _very_ careful not to use the path to one of your Hard Drives as this would be disasterous!!**

I can't stress the importance of the above enough - if you use the wrong path then the following steps could potentially destroy all the data on your Hard Drisk. That would leave you with, well... not much tbh!!

Okay, on with the instructions from where we left off:

then press "d" (without the " marks) to delete the current partition. Press "w" (again, without the " marks... you get the picture from now on) to write the changes to disk.

After the changes have been written to disk, again type:

> sudo fdisk /pathto/yourUSBdrive

then press "n" to create a new partiton, "p" for a primary partition. Accept the suggested defaults for the start and end points (they will pertain to the cylinders on the drive - in my case 1 - 1022), then "t" to change the filesystem, then "b" for FAT32 (as this will be recognised by Windows and Linux), then "w" again to write the changes to disk.

This should (hopefully) do the trick. 

However, if Linux still won't recognise the drive then remove it and plug it in to your Windows machine. From there quick-format it (right-click > Format - check 'quick format' box) to FAT32 (it may just be called FAT under Windows) and it should now work on both your Windows and Linux installations.

Easy eh!

Hope this helps :)

---

### Post by bcasanov on 2008-10-28
Sorry guys for taking a little long to respond. 

> Is it recognised if you plug it in before you boot into ubuntu?

No.

> first, plug the drive in and then open a terminal and type the following:
sudo fdisk -l

The result of "sudo fdisk -l" after plugging in the the drive is: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda4               1        9729    78148161    f  W95 Ext'd (LBA)
/dev/sda5               1         267     2144614+  82  Linux swap / Solaris
/dev/sda6             268        9729    76003483+  83  Linux

Notice that there is no mention of /dev/sdc anywhere, even though I have the USB stick plugged in.

---

### Post by ChildOfMana on 2008-10-28
Okay then it seems your USB drive is not being recognised at all (if it was being detected it wouldn't necessarily be mounted as /dev/sdc though - that was just the case with mine as I have 2 Hard Drives - /dev/sda and /dev/sdb).

Note that /dev/sda is your Hard Drive (and the /dev/sda4, /dev/sda5 etc are the partitions on the drive) so don't attempt any of my above instructions with these whatever you do!!

Sorry I can't be of more help.

---

### Post by zerin on 2010-08-04
Hi there, sorry to be bumping old threads, but this issue hasn't been resolved yet has it? I have the same exact problem with my 8gb Sandisk cruzer drive, i uninstalled U3 and after that started giving me a whole mess of problems. But the real problem was when i unplugged the USB drive one second too soon before it was ready to be pulled out and now my Ubuntu 10.04 won't see it at all, i checked in the Storage device manager, disk Utility, Gparted and even in the terminal's fdisk! not even windows will see it, like i never plugged it in, doesn't even know i plugged it in, and now it has a solid light lit on the drive whenever i plug it in, but nothing, i hope this can be fix, i assume i corrupted the partition table when i abruptly unplugged it, but can it be fixed?

---

### Post by Desperate on 2010-08-10
same problem here with a generic usb flash drive, saved all my data on it to swap it over to Ubuntu 10.04 and now I'm kinda lost.

the rest works perfect though, even other usb sticks, just the drive isn't recognized.

All help/hints appreciated

---

### Post by QLee on 2010-08-10
Try running a fsck (filesystem check) on the unmounted partition, if and when it completes successfully, try to mount it again.

---

### Post by Desperate on 2010-08-10
That's the problem, it isn't there at all, mounted or un-mounted

---

### Post by carrotsoup on 2010-08-10
Having the exact same problem with my external harddrive. It isn't showing up at all for me to even mount it, but it worked on the live cd and it worked on windows.

---

### Post by fslezak on 2010-08-10
Try to do this:

```
 sudo gedit /etc/modules 
```and add (EXACTLY as put)...

```

ehci_hcd
usbhid
usb_storage

```

...then Reboot, and post back if this works.

---

### Post by Desperate on 2010-08-10
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
ehci_hcd
usbhid
usb_storage


no change, thanks anyway, learning as we go ;)

---

