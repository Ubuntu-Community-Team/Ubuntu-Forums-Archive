---
title: "Dual Boot: Directly loads to Windows/Ubuntu"
date: 2018-11-07
forum: New to Ubuntu
---

### Post by aruninterval on 2018-11-07
I have a Dell laptop with preinstalled Windows 10 in UEFI mode. I ran a live Ubuntu usb but it didn't ask me if I wanted to try or Install. I thought may be it will ask me later. So I went ahead and continued with the steps. I checked the install thirdy party software and it asked me to enable secure boot and I did, then I pressed continue. Then after a minute the home screen appeared with the option of 'Install now'. Because I didn't want to install it then, I shut down the system, removed the usb and loggeg in to Windows 10. This was to create partition. Then I freed some space for Ubuntu. Now when I inserted the usb again and changed the boot option to 'usb_name', it showed the following error: Image 1.

[ATTACH=CONFIG]281582[/ATTACH]

So I changed my boot option to turn Secure Boot off and set my boot option to Legacy mode. After doing this, I selected the usb option and now it gave me option to install Ubuntu. I followed the instructions and installed Ubuntu(Dual Boot: created an ext4 partition with mount point '/', swap area partition and home partition with mount point '/home'). But after I restated the system, system loaded Windows directly without showing the Grub menu. Then I changed the BIOS to Legacy and selected internal HDD but then it loaded Ubuntu directly without showing the Grub menu. 

I tried Boot Repair by logging in to Ubuntu but still no change. This is the output of boot repair: [http://paste.ubuntu.com/p/9MNZBHykP8/](http://paste.ubuntu.com/p/9MNZBHykP8/)

Please help me.

Thanks
Arun

---

### Post by oldfred on 2018-11-07
Please attach screen shots, not post in line.
Easy to attach with Forum's advanced editor and paper clip icon.

Are you still able to boot Windows?
It does not look like you have a Windows UEFI boot entry?

When you turned Legacy/CSM/BIOS boot mode on, you then installed Ubuntu in BIOS boot mode.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  
    
UEFI & CSM are not compatible. Once you start booting in one mode, you cannot switch. 
Or grub can only offer to boot other systems in same boot mode.

It also looks like you have Windows fast start up on. That needs to be off if dual booting.
       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

If you use Boot-Repair's advanced option when booted in UEFI mode, then do a total reinstall of grub in UEFI mode.

You should not be getting mmx type errors. That is for key management. 
May be related to having UEFI Secure Boot on.
They now seem to use the mmx file to add a key for Secure boot when adding proprietary drivers.

---

### Post by aruninterval on 2018-11-07
Thanks for the reply.

The Fast start up option is turned off.

By default, the system boot Windows 10. If I have to boot Ubuntu, I've to manually change the boot settings(See attached image for reference).

---

### Post by oldfred on 2018-11-08
The report incorrect gives this error on the Windows System Reserved (since unformatted) but you seem to have same error on your main Windows partition.
> Metadata kept in Windows cache, refused to mount.
Falling back to read-only mount because the NTFS partition is in an
unsafe state. Please resume and shutdown Windows fully (no hibernation
or fast restarting.)
The disk contains an unclean file system (0, 0).

---

### Post by aruninterval on 2018-11-09
Hi,

The problem is solved as I  created a new USB disk with Ubuntu 18.04 ( the one I tried to install earlier and created problem was Ubuntu 18.10) and performed a clean  installation. I can dual boot now in UEFI mode.

PS: The bug is in the Ubuntu 18.10 and I think it's still not resolved.[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1798171](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1798171) mmx error
Thanks for all the help.

---

