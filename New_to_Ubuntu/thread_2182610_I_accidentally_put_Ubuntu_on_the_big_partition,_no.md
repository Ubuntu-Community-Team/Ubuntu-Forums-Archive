---
title: "I accidentally put Ubuntu on the big partition, now I just need Windows on the small"
date: 2013-10-21
forum: New to Ubuntu
---

### Post by Scott_Van_Tussenbrook on 2013-10-21
Hello all,

Let's see if I can keep this brief.  I have used Ubuntu in the past, just to try it out, and I really like it.  I was about ready to make the switch 100% from Windows, but I wanted to put it on my new laptop to try it out for awhile (again).  Long story short, I "shrunk" my hard drive by 30 GB to put Ubuntu on, and was hoping for a dual-boot situation like I had on my old computers.  I've never had a problem setting this up on the handful of older machines in the past, but...

This one was different.  It's a Dell Inspiron 5521 64 Bit with Windows 8.  I couldn't get Ubuntu to boot from a USB.  So I burned a DVD and tried to do it that way, and somehow, I've managed to overwrite the main partition on my hard drive (where I wanted to leave Windows installed), and the 30 GB "shrunk" partition is still there, just with nothing on it now.  And I get no GRUB screen when I boot up.  No options to boot into Windows.  I think I toasted it.  It starts right into Ubuntu.

All of which is well and good -- I'm fine with this, I really can't stand Windows 8 anyway.  And all my stuff is backed up onto cloud services (Evernote, Google Drive, and Dropbox) so all I've lost is the time it will take to download and set everything back up.  At this point I would kiss Windows goodbye but I do need it for a few work apps, and Visual Studio and whatnot.  I have a copy of Windows 7 I'd like to install on that small 30 GB partition, and get it so I get the option to boot either OS on startup.

I just have no idea how to go about doing that.  Trying to install the updated flash player for web browsers seemed to require a degree in computer science, so we'll worry about that later -- but I wanted to ask the experts before trying to get this dual-boot thing set up before I worry about software.

Anyone have any advice for a just-enough-knowledge-to-be-dangerous Ubuntu newbie/new fan?

Thanks!

Scott Van Tussenbrook
Los Angeles, CA

---

### Post by sandyd on 2013-10-21
> **Scott_Van_Tussenbrook said:**
> Hello all,

Let's see if I can keep this brief.  I have used Ubuntu in the past, just to try it out, and I really like it.  I was about ready to make the switch 100% from Windows, but I wanted to put it on my new laptop to try it out for awhile (again).  Long story short, I "shrunk" my hard drive by 30 GB to put Ubuntu on, and was hoping for a dual-boot situation like I had on my old computers.  I've never had a problem setting this up on the handful of older machines in the past, but...

This one was different.  It's a Dell Inspiron 5521 64 Bit with Windows 8.  I couldn't get Ubuntu to boot from a USB.  So I burned a DVD and tried to do it that way, and somehow, I've managed to overwrite the main partition on my hard drive (where I wanted to leave Windows installed), and the 30 GB "shrunk" partition is still there, just with nothing on it now.  And I get no GRUB screen when I boot up.  No options to boot into Windows.  I think I toasted it.  It starts right into Ubuntu.

All of which is well and good -- I'm fine with this, I really can't stand Windows 8 anyway.  And all my stuff is backed up onto cloud services (Evernote, Google Drive, and Dropbox) so all I've lost is the time it will take to download and set everything back up.  At this point I would kiss Windows goodbye but I do need it for a few work apps, and Visual Studio and whatnot.  I have a copy of Windows 7 I'd like to install on that small 30 GB partition, and get it so I get the option to boot either OS on startup.

I just have no idea how to go about doing that.  Trying to install the updated flash player for web browsers seemed to require a degree in computer science, so we'll worry about that later -- but I wanted to ask the experts before trying to get this dual-boot thing set up before I worry about software.

Anyone have any advice for a just-enough-knowledge-to-be-dangerous Ubuntu newbie/new fan?

Thanks!

Scott Van Tussenbrook
Los Angeles, CA
There are two directions you can go at this point

1. Delete Ubuntu and Install Windows (backup first!!)
Delete the Ubuntu partitions (if you have an Windows 7 oem disk, just hit install, and delete the partitions from there, make sure you leave space for Ubuntu)
You can then install Ubuntu - which will automatically detect Windows 7 and add it to the boot menu (which only shows if you have more than one OS on the computer)

2. Install Windows and restore the GRUB Bootloader
Install Windows (which will overwrite Ubuntu's Bootloader (GRUB))
After installing Windows, you can follow the steps at [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) to restore GRUB.

---

### Post by Mstersarg61 on 2013-10-21
Would you consider running Windows 7 in a virtual machine?  If you need to re partition your disk anyway, you could install Ubuntu as your one and only operating system and use something like Virtual Box ([https://www.virtualbox.org/](https://www.virtualbox.org/)) to install Windows in a VM environment.  I mention Virtual Box only because that is the only one I have used.

---

### Post by sandyd on 2013-10-21
> **Mstersarg61 said:**
> Would you consider running Windows 7 in a virtual machine?  If you need to re partition your disk anyway, you could install Ubuntu as your one and only operating system and use something like Virtual Box ([https://www.virtualbox.org/](https://www.virtualbox.org/)) to install Windows in a VM environment.  I mention Virtual Box only because that is the only one I have used.

Btw, if your CPU has VT/virtualization support, then KVM (with virt-manager and spice) can be used without the need of installing kernel modules, and has a higher performance

---

### Post by Bucky Ball on 2013-10-21
As you already have a 30Gb partition empty install Win7 there, then boot into Ubuntu and:

```
sudo update-grub
```

Not sure why you would go the long route and wipe everything and start again. You have an empty partition there already. I did this very thing not long ago.

---

### Post by Scott_Van_Tussenbrook on 2013-10-22
Thanks everyone for all the quick responses, I really appreciate it.  I will look over everything in the morning, after I've had some sleep.  But I am leaning toward Bucky Ball's suggestion -- that's pretty much what I was hoping for -- a way to get GRUB back and then dump Windows on that small partition, w/o having to start all all all the way over...

Thanks again.  As a newbie, I'm sure I'll be back with more questions.  (And answers, too, after I've been at this awhile.  <g>

Cheers!

-- Scott

---

### Post by oldfred on 2013-10-23
If you have a new Windows 8 system, it was installed in UEFI mode and gpt partitioning. If you have recovery partition, it may be easiest to just restore that and reinstall Ubuntu.


But you may have installed Ubuntu in BIOS/CSM boot mode even with the gpt partitioning.
Windows 7 DVD will not install in UEFI mode and Windows has to boot in UEFI mode from gpt partitioning.
You can convert a Windows 7 DVD to flash drive and make changes so it will install in UEFI mode. But it requires several partitions in UEFI mode.
Or you can convert entire drive to BIOS booting with MBR(msdos) partitioning.

 Windows Recommended UEFI-Based Disk-Partition Configurations
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
       
 Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
Convert Windows USB flash install to UEFI boot
[http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/](http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

---

