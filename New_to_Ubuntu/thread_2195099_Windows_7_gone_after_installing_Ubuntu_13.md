---
title: "Windows 7 gone after installing Ubuntu 13"
date: 2013-12-22
forum: New to Ubuntu
---

### Post by jabogood on 2013-12-22
Hello,

I have done a lot of research before but I am completely desperate. Years ago, I tried to approach to Ubuntu and it gave me a lot of problems and I swore I wasn't going to try it never again. I recently started studying programming and have finally tried it again. I am already regreting it, and it hasn't been more than 1 day. 

I don't have a DVD reader on this new computer. I created a bootable image with that tool for windows for the official Ubuntu 13.04 ISO. I AM SURE AS HELL that I did choose "Install Ubuntu alongside Windows 7". I started Ubuntu and tried it a little, before wanting to change the boot order in GRUB (I remember, I don't want Ubuntu to be the default OS when I turn the computer on). So I actually did not do anything, and think to myself: "Well, I will play with it when I have time, I want to go back to windows now". So I reboot:
No GRUB (as usual), just the Ubuntu installer again. "Nope :D, I don't want to install it again". Reboot. Same: Install Ubuntu alongside Ubuntu?. Me: F***, maybe it hasn't been installed well, reinstall again. Reboot: Same, ask to install Ubuntu 13. Reboot again and change the boot settings: select my Hard drive instead the USB installer. 
Still no GRUB but it at least loaded Ubuntu 13 well. I did hours of research and managed to break GRUB and put it into rescue mode and not beeing able to boot any OS. I reinstalled ubuntu for the 1023123th time in 1 day and now there's GRUB but there's no windows anywhere.
I took the hard drive out and plug it into another windows pc to desperately take some files before installing a fresh windows and forgetting all that has to relate with Ubuntu and Linux, but it didn't even recognize the hard drive, so I don't know what to do now.

Thanks.

---

### Post by Tristan_Williams on 2013-12-22
> 
No GRUB (as usual), just the Ubuntu installer again. "Nope :grin:, I don't want to install it again". Reboot. Same: Install Ubuntu alongside Ubuntu?


It says install alongside Ubuntu, which means windows is no longer on the disk. Either a bad installer or someone clicked the wrong button...

---

### Post by fantab on 2013-12-22
Boot with the Ubuntu Live USB and "Try Ubuntu Without installing"... 
Install [**Boot-Repair**]("https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu"), and 'create a **Bootinfo Summary**, note the web-LINK it generates and post that LINK here.

---

### Post by buzzingrobot on 2013-12-22
As far as I know, the installer and associated files are deleted at the end of an install, prior to the reboot.  The only reason I can think of that the installer would run again on reboot is if the install medium had not been removed.

---

### Post by jabogood on 2013-12-22
> **Tristan_Williams said:**
> It says install alongside Ubuntu, which means windows is no longer on the disk. Either a bad installer or someone clicked the wrong button...
That actually made me cry.

> **fantab said:**
> Boot with the Ubuntu Live USB and "Try Ubuntu Without installing"... 
Install [**Boot-Repair**]("https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu"), and 'create a **Bootinfo Summary**, note the web-LINK it generates and post that LINK here.
Will do, as son as I create another Live USB, because I deleted the one I used, to install Windows again.

> **buzzingrobot said:**
> As far as I know, the installer and associated files are deleted at the end of an install, prior to the reboot.  The only reason I can think of that the installer would run again on reboot is if the install medium had not been removed.
I don't know what exactly you mean. But the installer run again because I didn't change back the boot option from the USB.

---

### Post by buzzingrobot on 2013-12-22
> **jabogood said:**
> 


I don't know what exactly you mean. But the installer run again because I didn't change back the boot option from the USB.

If the install medium -- CD/DVD/USB stick -- is in the drive or on the port and the BIOS is set to try to boot from that drive first -- the installer will run every time the machine reboots.

To complete an install, you are required to remove the install medium and reboot. if I understand your first post, you did not do that.  Instead, you booted into the installer a second (and third?) time, proceeded far enough to see the partitioning options.

By default, you won't see the Grub menu.  Hold down the left shift key while the machine boots to trigger its display. The Grub configuration can be edited to insert a delay that will display the menu for a specified number of seconds.

---

### Post by jabogood on 2013-12-22
> **fantab said:**
> Boot with the Ubuntu Live USB and "Try Ubuntu Without installing"... 
Install [**Boot-Repair**]("https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu"), and 'create a **Bootinfo Summary**, note the web-LINK it generates and post that LINK here.
There it is [http://paste.ubuntu.com/6618511/](http://paste.ubuntu.com/6618511/)
I dont like how does that look. Windows is completely gone, isnt it?

> **buzzingrobot said:**
> If the install medium -- CD/DVD/USB stick -- is in the drive or on the port and the BIOS is set to try to boot from that drive first -- the installer will run every time the machine reboots.
Oh, yes, In understand you now, thanks! It was still in the port.

---

### Post by Tristan_Williams on 2013-12-22
Yes, I'm afraid windows is gone :( 

Don't feel too bad, It's happened to me at least 5 times.

---

### Post by oldfred on 2013-12-22
I do not know if it is that Windows is hibernated or fast boot is on, so installer cannot see Windows partition and then erases drive, or if user just selected the wrong choice?
If installer issue post a bug report


Another user with similar issue.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1225534](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1225534)

---

### Post by squakie on 2013-12-22
Someone can correct me if I'm wrong here, but a couple of things to remember after reinstalling Windows 7 but prior to installing Ubuntu:

- use the Windows tool to defragment the drive a couple of times prior to installing Ubuntu

- use the Windows tool to shrink the partition (if you need to) to make room for Ubuntu (I think this started with Wind 7 and all the uefi/efi "stuff")

---

### Post by fantab on 2013-12-22
> **jabogood said:**
> There it is [http://paste.ubuntu.com/6618511/](http://paste.ubuntu.com/6618511/)
I dont like how does that look. Windows is completely gone, isnt it?


NO, you don't have Windows, its gone.
The output below from your HDD does NOT show any Windows, NTFS install.
```
parted -l:

Model: ATA ST1000DM003-1CH1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      1049kB  992GB   992GB   primary   ext4            boot
2      992GB   1000GB  8519MB  extended
5      992GB   1000GB  8519MB  logical   linux-swap(v1)
```

> **oldfred said:**
> I do not know if it is that Windows is hibernated or fast boot is on, so installer cannot see Windows partition and then erases drive, or if user just selected the wrong choice?

When Windows is Hibernating, it won't shutdown. If it doesn't shutdown then its still in use. This can cause the installer to NOT see the Windows Partition or Windows, and when you choose one of the "Automatic' install method then it overwrites the disk assuming its empty. 
Or it could be that you are opting for a 'wrong' option in the installer to manage partitions to install to.

Also check in your BIOS to see if 'fastboot' is enabled, if it is then [disable fastboot]("http://www.intel.com/support/motherboards/desktop/sb/CS-032034.htm").

You may have to re-install Windows7.

---

### Post by garyzw on 2013-12-22
A good thing to do before attempting to install another OS is to do a system image to an external drive or USB stick if it is large enough . I use [Redo Backup]("http://redobackup.org/") if the installion causes problems such as deleting your Windows Partiton then all you do is run Redo Backup from the CD or USB and restore it and you back in bussiness--nothing lost but a little time.

---

