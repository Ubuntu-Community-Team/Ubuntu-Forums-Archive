---
title: "Unable to install Kubuntu 13.04 on new Toshiba P875-S7102 Pre-installed with Win 8"
date: 2013-08-03
forum: New to Ubuntu
---

### Post by wesley2 on 2013-08-03
Hi,

I just purchased the Toshiba Satellite P875-S7102 laptop with Windows 8 pre-installed. 

It has the following configuration:

[LIST]
[*]Intel® Core&#8482; i7-3630QM Processor 
[*]Mobile Intel® HD 4000 Graphics 
[*]8GB DDR3 1600MHz memory 
[*]750GB HDD (5400rpm, Serial ATA) 
[*]DVD-SuperMulti drive (+/-R double layer) 
[/LIST]

The BIOS is stuck in UEFI mode, but it allows me to enable/disable SecureBoot. The laptop has System BIOS v6.30, InsydeH2O Setup Utility rev 3.7

I am trying to install Kubuntu 13.04 onto this laptop for a dual boot system. I downloaded the Kubuntu LiveCD ISO installation image and put it onto a 4GB USB stick. 

I used the Kubuntu installation tool to repartition the drive as follows:
Model: ATA TOSHIBA MQ01ABD0 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size    File system     Name                  Flags
1      1049kB  473MB  472MB   ntfs            Basic data partition  hidden, diag
2      473MB   746MB  273MB   fat32           Basic data partition  boot
3      746MB   880MB  134MB   ntfs            Basic data partition  msftres
4      880MB   103GB  102GB   ntfs            Basic data partition
6      103GB   152GB  49.2GB  linux-swap(v1)
7      152GB   193GB  41.0GB  ext4
8      193GB   738GB  545GB   ext4
5      738GB   750GB  11.8GB  ntfs            Basic data partition  hidden, diag

So far, I have had no luck in completing the installation process. The installation program keeps declaring an error while trying to install GRUB:
The 'grub-efi-amd64-signed' package failed to install into /target/.  (NOTE: With SecureBoot enabled)
and
The 'grub-efi' package failed to install into /target/.  (NOTE: With SecureBoot disabled)

I also tried using Boot-Repair right after the installation failed (i.e. while still running the LiveCD image) in the hopes that it would fix the problem. Unfortunately, even this reports an error:

An error occurred during the repair.

Please write on a paper the following URL:
[http://paste.ubuntu.com/5941880/](http://paste.ubuntu.com/5941880/)

In case you still experience boot problem, indicate this URL to:
[EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]

You can now reboot your computer.
Please do not forget to make your BIOS boot on sda (750GB) disk!

I looked at the Boot-Repair log to see what was happening. So far, I've only noticed the following:
(1) WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.
(2) grub-install --efi-directory=/boot/efi --target=x86_64-efi : exit code of grub-install :1

NOTE: The log will show /dev/sdb (1GB device) and /dev/sdc (4GB device). The former is the USB drive I used to save some of the error messages I was getting, and the latter is the USB drive with the LiveCD. 

The only upside to all of this is that the laptop is still able to boot into Windows 8.

I've been searching for hours for a solution. I REALLY hope someone can help me with this.

NOTE: Until recently, I have never owned a desktop/laptop with the new UEFI stuff, so I am pretty new to all this. Also, my knowledge of Linux is still relatively beginner to intermediate.

---

### Post by leopheard on 2013-08-03
Boot-Repair log to see what was happening. So far, I've only noticed the following:
(1) WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.
(2) grub-install --efi-directory=/boot/efi --target=x86_64-efi : exit code of grub-install :1[/QUOTE]

It is suggesting disk here can't perform the action you want, and to try:

[https://www.gnu.org/software/parted/]("https://www.gnu.org/software/parted/")

---

### Post by ajgreeny on 2013-08-03
Two comments that may or may not help you, but which may lead you in a direction that ends with a solution for you.
[LIST=1]
[*]See [UEFI - Ubuntu Documentation]("https://help.ubuntu.com/community/UEFI") for a lot of information that may help you with the UEFI partitioning system, which I admit I was somewhat scared of, but which with no windows in dual boot to deal with, turned out not to be a problem, apart from #2 below.
[*]Make sure you boot the USB live system in UEFI mode or you will not be able to install, though it may still boot OK;  this was the only problem I had until I realised the DVD I was using appeared twice in the list of boot devices, first as normal DVD device, the second as a UEFI DVD device.  Choosing the UEFI version was all that was needed; from there all went very quickly and without problem.
[/LIST]

---

### Post by oldfred on 2013-08-04
The Boot-Repair runs both fdisk and parted commands. That fdisk does not work with gpt is normal.

That grub has issues writing into the efi partition is not normal. Some have locked efi partitions, but your report shows grub at least partially installed to the efi partition, but you have not installed with the secure boot version of the kernel. 

Part of the issue may be that Boot-Repair is looking for an ubuntu partition but you have the kubuntu partition??

 /EFI/kubuntu/grubx64.efi

This may be a bug in Boot-Repair?

---

### Post by YannBuntu on 2013-08-06
Hi
No, not a Boot-Repair bug here. We can see line 1054 it correctly detected the Kubuntu file.

The issue is line 1049, it's the one leopheard mentionned:
> grub-install --efi-directory=/boot/efi --target=x86_64-efi : exit code of grub-install :1

grub-install returns an error, but no additional indication, so we have to guess. I'd bet for a buggy firmware, because efibootmgr returns no Kubuntu entry.
Maybe the Windows EFI renaming would workaround.

wesley2, please run Boot-Repair --> Advanced Options --> tick "Backup and rename Windows EFI files" --> Apply, tell us the new URL, reboot, and tell us what you observe?

---

### Post by oldfred on 2013-08-06
Boot-Repair should work with kubuntu folder in efi partition so that is not an issue. Actually it turns out any name or distribution will work as Boot-Repair scans all the folders in the efi partition.

---

### Post by wesley2 on 2013-08-08
> **YannBuntu said:**
> Hi
No, not a Boot-Repair bug here. We can see line 1054 it correctly detected the Kubuntu file.

The issue is line 1049, it's the one leopheard mentionned:


grub-install returns an error, but no additional indication, so we have to guess. I'd bet for a buggy firmware, because efibootmgr returns no Kubuntu entry.
Maybe the Windows EFI renaming would workaround.

wesley2, please run Boot-Repair --> Advanced Options --> tick "Backup and rename Windows EFI files" --> Apply, tell us the new URL, reboot, and tell us what you observe?

Hi guys,

Thanks for posting all the suggestions. I really appreciate it. I would have replied sooner, but work got in the way. I tried the above suggestion and this time Boot-Repair didn't complain. 

The report is here: [http://paste.ubuntu.com/5961538/](http://paste.ubuntu.com/5961538/)

From line 1045 to the end of the file, you see that it successfully installed grub-efi-amd64-signed. However, when I reboot the laptop now goes into the GRUB mini-bash mode and that is where I am stuck. I have never worked with this before. What should I do now?

**Here are the steps I performed for this time around:**

[LIST=1]
[*]Installed kubuntu via LiveUSB with UEFI and SecureBoot enabled. Got error 'grub-efi-amd64.efi can't be installed on /target/' error as usual. 
[*]Restarted laptop. The laptop boots straight into Windows. No GRUB. 
[*]Shutdown PC. 
[*]Powered Up with LiveUSB 
[*]Installed boot-repair. 
[*]Within Boot-Repair
[LIST=1]
[*]Advance Options:
[LIST=1]
[*]Main options tab
[LIST=1]
[*]These options are already enabled: Reinstall GRUB, Use the standard EFI, Unhide bootmenu 10s 
[*]I enabled "Enabled Backup and rename Windows EFI files" 
[*]Clicked Apply 
[/LIST]
  
[*]GRUB location tab
[LIST=1]
[*] OS to boot by default: sda6 (Kubuntu 13.04) 
[*]Separate /boot/efi partition: sda2 
[/LIST]
  
[*]GRUB Options tab
[LIST=1]
[*]SecureBoot enabled 
[/LIST]
  
[*]Clicked Apply 
[/LIST]
  
[*]Boot-Repair performs its job. 
[/LIST]
  
[/LIST]

**Here is the portion of the syslog that shows the error the Kubuntu installer had in trying to install GRUB:**
```

Aug  8 05:47:40 kubuntu /plugininstall.py: Verifying downloads ...
Aug  8 05:47:40 kubuntu /plugininstall.py: Downloads verified successfully
Aug  8 05:47:40 kubuntu /plugininstall.py: log-output -t ubiquity chroot /target umount /sys
Aug  8 05:47:40 kubuntu /plugininstall.py: log-output -t ubiquity chroot /target umount /proc
Aug  8 05:47:40 kubuntu /plugininstall.py: log-output -t ubiquity umount /target/run
Aug  8 05:47:40 kubuntu /plugininstall.py: log-output -t ubiquity umount /target/dev
Aug  8 05:47:40 kubuntu /plugininstall.py: log-output -t ubiquity mount --bind /proc /target/proc
Aug  8 05:47:40 kubuntu /plugininstall.py: log-output -t ubiquity mount --bind /sys /target/sys
Aug  8 05:47:40 kubuntu /plugininstall.py: log-output -t ubiquity mount --bind /dev /target/dev
Aug  8 05:47:40 kubuntu /plugininstall.py: log-output -t ubiquity mount --bind /run /target/run
Aug  8 05:47:40 kubuntu grub-installer: info: architecture: amd64/efi
Aug  8 05:47:41 kubuntu ubiquity: File descriptor 3 (pipe:[51901]) leaked on lvdisplay invocation. Parent PID 13089: /bin/sh
Aug  8 05:47:42 kubuntu ubiquity:   Volume group "sda" not found
Aug  8 05:47:42 kubuntu ubiquity:   Skipping volume group sda
Aug  8 05:47:42 kubuntu grub-installer: info: Identified partition label for /dev/sda6: gpt
Aug  8 05:47:42 kubuntu grub-installer: dpkg: warning: ignoring request to remove grub which isn't installed
Aug  8 05:47:42 kubuntu grub-installer: dpkg: warning: ignoring request to remove grub-legacy which isn't installed
Aug  8 05:47:43 kubuntu grub-installer: (Reading database ... 
Aug  8 05:47:43 kubuntu grub-installer: 130371 files and directories currently installed.)
Aug  8 05:47:43 kubuntu grub-installer: Removing grub-pc ...
Aug  8 05:47:44 kubuntu grub-installer: Purging configuration files for grub-pc ...
Aug  8 05:47:44 kubuntu grub-installer: Removing grub-gfxpayload-lists ...
Aug  8 05:47:45 kubuntu grub-installer: Removing grub-pc-bin ...
Aug  8 05:47:46 kubuntu grub-installer: Processing triggers for man-db ...
Aug  8 05:47:46 kubuntu ubiquity: Reading package lists...
Aug  8 05:47:49 kubuntu ubiquity: 
Aug  8 05:47:49 kubuntu ubiquity: Building dependency tree...
Aug  8 05:47:49 kubuntu ubiquity: 
Aug  8 05:47:49 kubuntu ubiquity: Reading state information...
Aug  8 05:47:49 kubuntu ubiquity: 
Aug  8 05:47:49 kubuntu ubiquity: The following extra packages will be installed:
Aug  8 05:47:49 kubuntu ubiquity:   efibootmgr grub-efi-amd64 grub-efi-amd64-bin secureboot-db
Aug  8 05:47:49 kubuntu ubiquity: The following NEW packages will be installed:
Aug  8 05:47:49 kubuntu ubiquity:   efibootmgr grub-efi-amd64 grub-efi-amd64-bin grub-efi-amd64-signed
Aug  8 05:47:49 kubuntu ubiquity:   secureboot-db
Aug  8 05:47:50 kubuntu ubiquity: Preconfiguring packages ...
Aug  8 05:47:50 kubuntu ubiquity: 0 upgraded, 5 newly installed, 0 to remove and 346 not upgraded.
Aug  8 05:47:50 kubuntu ubiquity: Need to get 0 B/1,193 kB of archives.
Aug  8 05:47:50 kubuntu ubiquity: After this operation, 4,431 kB of additional disk space will be used.
Aug  8 05:47:50 kubuntu ubiquity: Selecting previously unselected package efibootmgr.
Aug  8 05:47:50 kubuntu ubiquity: (Reading database ... 
Aug  8 05:47:50 kubuntu ubiquity: 130106 files and directories currently installed.)
Aug  8 05:47:50 kubuntu ubiquity: Unpacking efibootmgr (from .../efibootmgr_0.5.4-4ubuntu1_amd64.deb) ...
Aug  8 05:47:51 kubuntu ubiquity: Selecting previously unselected package grub-efi-amd64-bin.
Aug  8 05:47:51 kubuntu ubiquity: Unpacking grub-efi-amd64-bin (from .../grub-efi-amd64-bin_2.00-13ubuntu3_amd64.deb) ...
Aug  8 05:47:52 kubuntu ubiquity: Selecting previously unselected package grub-efi-amd64.
Aug  8 05:47:52 kubuntu ubiquity: Unpacking grub-efi-amd64 (from .../grub-efi-amd64_2.00-13ubuntu3_amd64.deb) ...
Aug  8 05:47:52 kubuntu ubiquity: Selecting previously unselected package grub-efi-amd64-signed.
Aug  8 05:47:52 kubuntu ubiquity: Unpacking grub-efi-amd64-signed (from .../grub-efi-amd64-signed_1.11+2.00-12ubuntu1_amd64.deb) ...
Aug  8 05:47:53 kubuntu ubiquity: Selecting previously unselected package secureboot-db.
Aug  8 05:47:53 kubuntu ubiquity: Unpacking secureboot-db (from .../secureboot-db_1.1_amd64.deb) ...
Aug  8 05:47:53 kubuntu ubiquity: Processing triggers for man-db ...
Aug  8 05:47:55 kubuntu ubiquity: Setting up efibootmgr (0.5.4-4ubuntu1) ...
Aug  8 05:47:55 kubuntu ubiquity: Setting up grub-efi-amd64-bin (2.00-13ubuntu3) ...
Aug  8 05:47:55 kubuntu ubiquity: Setting up grub-efi-amd64 (2.00-13ubuntu3) ...
Aug  8 05:47:56 kubuntu ubiquity: 
Aug  8 05:47:56 kubuntu ubiquity: Creating config file /etc/default/grub with new version
Aug  8 05:47:59 kubuntu kernel: [  930.837626] efivars: set_variable() failed: status=8000000000000009
Aug  8 05:48:00 kubuntu ubiquity: dpkg: error processing grub-efi-amd64 (--configure):
Aug  8 05:48:00 kubuntu ubiquity:  subprocess installed post-installation script returned error exit status 1
Aug  8 05:48:00 kubuntu ubiquity: dpkg: dependency problems prevent configuration of grub-efi-amd64-signed:
Aug  8 05:48:00 kubuntu ubiquity:  grub-efi-amd64-signed depends on grub-efi-amd64 (>= 2.00-7ubuntu4); however:
Aug  8 05:48:00 kubuntu ubiquity:   Package grub-efi-amd64 is not configured yet.
Aug  8 05:48:00 kubuntu ubiquity: 
Aug  8 05:48:00 kubuntu ubiquity: dpkg: error processing grub-efi-amd64-signed (--configure):
Aug  8 05:48:00 kubuntu ubiquity:  dependency problems - leaving unconfigured
Aug  8 05:48:00 kubuntu ubiquity: Setting up secureboot-db (1.1) ...
Aug  8 05:48:00 kubuntu ubiquity: No apport report written because the error message indicates its a followup error from a previous failure.
Aug  8 05:48:00 kubuntu ubiquity: Can't access efivars filesystem at /sys/firmware/efi/efivars, aborting
Aug  8 05:48:00 kubuntu ubiquity: Errors were encountered while processing:
Aug  8 05:48:00 kubuntu ubiquity:  grub-efi-amd64
Aug  8 05:48:00 kubuntu ubiquity:  grub-efi-amd64-signed
Aug  8 05:48:00 kubuntu ubiquity: E: Sub-process /usr/bin/dpkg returned an error code (1)
Aug  8 05:48:00 kubuntu ubiquity: Reading package lists...
Aug  8 05:48:01 kubuntu ubiquity: 
Aug  8 05:48:01 kubuntu ubiquity: Building dependency tree...
Aug  8 05:48:01 kubuntu ubiquity: 
Aug  8 05:48:01 kubuntu ubiquity: Reading state information...
Aug  8 05:48:01 kubuntu ubiquity: 
Aug  8 05:48:02 kubuntu ubiquity: The following NEW packages will be installed:
Aug  8 05:48:02 kubuntu ubiquity:   shim-signed
Aug  8 05:48:02 kubuntu ubiquity: 0 upgraded, 1 newly installed, 0 to remove and 346 not upgraded.
Aug  8 05:48:02 kubuntu ubiquity: 2 not fully installed or removed.
Aug  8 05:48:02 kubuntu ubiquity: Need to get 0 B/432 kB of archives.
Aug  8 05:48:02 kubuntu ubiquity: After this operation, 1,393 kB of additional disk space will be used.
Aug  8 05:48:02 kubuntu ubiquity: Selecting previously unselected package shim-signed.
Aug  8 05:48:02 kubuntu ubiquity: (Reading database ... 
Aug  8 05:48:02 kubuntu ubiquity: 130355 files and directories currently installed.)
Aug  8 05:48:02 kubuntu ubiquity: Unpacking shim-signed (from .../shim-signed_1.2+0~20120906.bcd0a4e8-0ubuntu4_amd64.deb) ...
Aug  8 05:48:03 kubuntu ubiquity: Setting up grub-efi-amd64 (2.00-13ubuntu3) ...
Aug  8 05:48:06 kubuntu kernel: [  938.249085] efivars: set_variable() failed: status=8000000000000009
Aug  8 05:48:07 kubuntu ubiquity: dpkg: error processing grub-efi-amd64 (--configure):
Aug  8 05:48:07 kubuntu ubiquity:  subprocess installed post-installation script returned error exit status 1
Aug  8 05:48:07 kubuntu ubiquity: dpkg: dependency problems prevent configuration of grub-efi-amd64-signed:
Aug  8 05:48:07 kubuntu ubiquity:  grub-efi-amd64-signed depends on grub-efi-amd64 (>= 2.00-7ubuntu4); however:
Aug  8 05:48:07 kubuntu ubiquity:   Package grub-efi-amd64 is not configured yet.
Aug  8 05:48:07 kubuntu ubiquity: 
Aug  8 05:48:07 kubuntu ubiquity: dpkg: error processing grub-efi-amd64-signed (--configure):
Aug  8 05:48:07 kubuntu ubiquity:  dependency problems - leaving unconfigured
Aug  8 05:48:07 kubuntu ubiquity: Setting up shim-signed (1.2+0~20120906.bcd0a4e8-0ubuntu4) ...
Aug  8 05:48:07 kubuntu ubiquity: No apport report written because the error message indicates its a followup error from a previous failure.
Aug  8 05:48:10 kubuntu ubiquity: dpkg: error processing shim-signed (--configure):
Aug  8 05:48:10 kubuntu ubiquity:  subprocess installed post-installation script returned error exit status 1
Aug  8 05:48:10 kubuntu kernel: [  941.910452] efivars: set_variable() failed: status=8000000000000009
Aug  8 05:48:10 kubuntu ubiquity: Errors were encountered while processing:
Aug  8 05:48:10 kubuntu ubiquity:  grub-efi-amd64
Aug  8 05:48:10 kubuntu ubiquity:  grub-efi-amd64-signed
Aug  8 05:48:10 kubuntu ubiquity:  shim-signed
Aug  8 05:48:10 kubuntu ubiquity: E
Aug  8 05:48:10 kubuntu ubiquity: : Sub-process /usr/bin/dpkg returned an error code (1)
Aug  8 05:48:10 kubuntu grub-installer: info: Calling 'apt-install grub-efi-amd64-signed' failed
Aug  8 05:48:17 kubuntu /plugininstall.py: log-output -t ubiquity umount /target/cdrom
Aug  8 05:48:17 kubuntu finish-install: Disabling CD in sources.list
Aug  8 05:48:17 kubuntu /plugininstall.py: Exception during installation:
Aug  8 05:48:17 kubuntu /plugininstall.py: Traceback (most recent call last):
Aug  8 05:48:17 kubuntu /plugininstall.py:   File "/usr/share/ubiquity/plugininstall.py", line 1775, in <module>
Aug  8 05:48:17 kubuntu /plugininstall.py:     install.run()
Aug  8 05:48:17 kubuntu /plugininstall.py:   File "/usr/share/ubiquity/plugininstall.py", line 78, in wrapper
Aug  8 05:48:17 kubuntu /plugininstall.py:     func(self)
Aug  8 05:48:17 kubuntu /plugininstall.py:   File "/usr/share/ubiquity/plugininstall.py", line 242, in run
Aug  8 05:48:17 kubuntu /plugininstall.py:     self.configure_bootloader()
Aug  8 05:48:17 kubuntu /plugininstall.py:   File "/usr/share/ubiquity/plugininstall.py", line 1031, in configure_bootloader
Aug  8 05:48:17 kubuntu /plugininstall.py:     "GrubInstaller failed with code %d" % ret)
Aug  8 05:48:17 kubuntu /plugininstall.py: ubiquity.install_misc.InstallStepError: GrubInstaller failed with code 141
Aug  8 05:48:17 kubuntu /plugininstall.py: 
Aug  8 05:48:17 kubuntu activate-dmraid: No Serial ATA RAID disks detected
Aug  8 05:48:19 kubuntu partman:   No matching physical volumes found
Aug  8 05:48:19 kubuntu partman:   Reading all physical volumes.  This may take a while...
Aug  8 05:48:19 kubuntu partman:   No volume groups found
Aug  8 05:48:19 kubuntu partman-lvm:   No volume groups found

```

---

### Post by YannBuntu on 2013-08-08
You have:
- SecureBoot still enabled
- Windows not properly shutdown

Please:
1) run Boot-Repair --> Advanced Options --> tick Restore EFI backups --> Apply, indicate the new URL
2) reboot, it should go directly into Windows. From there, [deactivate FastBoot]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html"). 
3) deactivate SecureBoot , reboot and check that Windows still boots correctly
4) run Boot-Repair's Recommended Repair, tell us the new URL, reboot and tell us what you observe

---

### Post by wesley2 on 2013-08-09
> **YannBuntu said:**
> You have:
- SecureBoot still enabled
- Windows not properly shutdown

Please:
1) run Boot-Repair --> Advanced Options --> tick Restore EFI backups --> Apply, indicate the new URL
2) reboot, it should go directly into Windows. From there, [deactivate FastBoot]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html"). 
3) deactivate SecureBoot , reboot and check that Windows still boots correctly
4) run Boot-Repair's Recommended Repair, tell us the new URL, reboot and tell us what you observe

Here is the Boot-Repair log for step 1: [http://paste.ubuntu.com/5964925/](http://paste.ubuntu.com/5964925/)
It doesn''t appear to have done anything. I'm still getting the GRUB bash window.
I tried to redo steps 1 and 2 in the hopes I messed it up the first time around. Unfortunately, boot-repair doesn't give me the option to restore the backup again. Guess it did do the restore.
So now I can't even boot into Windows. :(
BTW, I have a zip archive of the mbr, partition table, etc that I had Boot-Repair make a while back. Is there anyway of using that archive to get the laptop to boot Windows again?

---

### Post by wesley2 on 2013-08-09
> **wesley2 said:**
> Here is the Boot-Repair log for step 1: [http://paste.ubuntu.com/5964925/](http://paste.ubuntu.com/5964925/)
It doesn''t appear to have done anything. I'm still getting the GRUB bash window.
I tried to redo steps 1 and 2 in the hopes I messed it up the first time around. Unfortunately, boot-repair doesn't give me the option to restore the backup again. Guess it did do the restore.
So now I can't even boot into Windows. :(
BTW, I have a zip archive of the mbr, partition table, etc that I had Boot-Repair make a while back. Is there anyway of using that archive to get the laptop to boot Windows again?

I just tried doing Boot-Repair again and this time enabled the "[COLOR=#000000][FONT=Ubuntu]Purge GRUB before reinstalling." under[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu] the GRUB Options tab. It came out with a dialogue box that had me issue these commands: [/FONT][/COLOR]
```
sudo chroot "/mnt/boot-sav/sda6" dpkg --configure -a
sudo chroot "/mnt/boot-sav/sda6" apt-get install -fy

sudo chroot "/mnt/boot-sav/sda6" apt-get purge -y --force-yes grub*-common shim-signed linux-signed*

sudo chroot "/mnt/boot-sav/sda6" apt-get install -y --force-yes grub-efi-amd64-signed shim-signed linux-signed-generic

```

Unforunately, this also didn't make a difference. Here is the log for this round: [http://paste.ubuntu.com/5965028/](http://paste.ubuntu.com/5965028/)

---

### Post by oldfred on 2013-08-09
You have not cleaned up the hibernation issue.

> The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount -t ntfs-3g -o remove_hiberfile /dev/sda1 /mnt/boot-sav/sda1
The disk contains an unclean file system (0, 0).

 Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/)

---

### Post by YannBuntu on 2013-08-09
> **wesley2 said:**
> boot-repair doesn't give me the option to restore the backup again. Guess it did do the restore.

Yes it did. There is no backup no more, so it does not propose to restore any.

> I have a zip archive of the mbr, partition table, etc that I had Boot-Repair make a while back. Is there anyway of using that archive to get the laptop to boot Windows again?

Unfortunately MBR backup is not useful in your case, as you have an UEFI system.

Please use a Windows8 disk [this way]("https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader#Windows_Vista_or_7_or_8"), until you get direct access to Windows at reboot.

> **oldfred said:**
> Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/)

This is automatically performed by B-R, as you can see l.565 of the [log]("http://paste.ubuntu.com/5964925/"). But in this case, removing hiberfil seems not enough, as mount then returns:
```
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda4': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
```
I will update BR so that it mounts in readonly in this particular case.

---

### Post by YannBuntu on 2013-08-10
**@wesley2:** Boot-Repair has been updated for your case (it will try to mount your Windows partitions in "read-only" mode), please could you run it and tell us the new URL that will appear?

---

### Post by wesley2 on 2013-08-11
> **YannBuntu said:**
> **@wesley2:** Boot-Repair has been updated for your case (it will try to mount your Windows partitions in "read-only" mode), please could you run it and tell us the new URL that will appear?

Hi YannBuntu,

It turns out I don't need that new version of BR (but it will probably be very helpful to others in the future). I FINALLY got the laptop to dual boot late last night  around 3am!!! :D I can't believe I went through all this headache simply because of the hiberfiles being generated by Windows 8 hibernation feature:mad: . I know you guys kept telling me I should resolve the mounting issues with the NTFS partitions, but it didn't occur to me that it was because they were preventing GRUB from being properly setup. I thought the mounting issues were nothing more than an annoyance. Anyways, now I know better.

Thanks again to everyone who spent the time trying to help me on this (especially YannBuntu and Oldfred). I can't tell you how many times I was so close to giving up on getting this laptop to dual boot. So far, Kubuntu is working great. The only minor issue that keeps coming up now is that the Muon Update Manager keeps reporting this error at the end of trying to install recent software updates:
```
grub-efi-amd64subprocess installed post-installation script returned error exit status 1


grub-efi
dependency problems - leaving unconfigured

```

Hopefully, this isn't a serious error...

For those who want to know the specific details of what I did last night, here you go...

I followed the instructions on this page to try repairing GRUB: [http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd#.UgcvaYP-AWM](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd#.UgcvaYP-AWM)
```
sudo mount /dev/sda6 /mnt
sudo mount --bind /dev /mnt/dev && sudo mount --bind /dev/pts /mnt/dev/pts && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
grub-install /dev/sda
grub-install --recheck /dev/sda
update-grub
exit && sudo umount /mnt/dev && sudo umount /mnt/dev/pts && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt

```

The above commands didn't actually get GRUB to work, but for some reason it made it possible for Windows to boot again. I then took that opportunity to configure Windows to no longer generate the hiberfile that was preventing the NTFS partitions from being mounted ([http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)). Once I verified Windows was able to boot without SecureBoot, I reran the Kubuntu LiveUSB and started up BR again. I ended up configuring BR to purge GRUB before re-installing it (just in case there was going to be weird conflicts from the previous attempts). BR had me copy and paste some commands to help purge the old GRUB install (which for some reason  got errors):
```
[FONT=arial]kubuntu@kubuntu:~$ sudo chroot "/mnt/boot-sav/sda6" dpkg --configure -a[/FONT][FONT=arial]Setting up grub-efi-amd64 (2.00-13ubuntu3) ...[/FONT]
[FONT=arial]dpkg: error processing grub-efi-amd64 (--configure):[/FONT]
[FONT=arial] subprocess installed post-installation script returned error exit status 1[/FONT]
[FONT=arial]dpkg: dependency problems prevent configuration of grub-efi:[/FONT]
[FONT=arial] grub-efi depends on grub-efi-amd64 (= 2.00-13ubuntu3); however:[/FONT]
[FONT=arial]  Package grub-efi-amd64 is not configured yet.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]dpkg: error processing grub-efi (--configure):[/FONT]
[FONT=arial] dependency problems - leaving unconfigured[/FONT]
[FONT=arial]Errors were encountered while processing:[/FONT]
[FONT=arial] grub-efi-amd64[/FONT]
[FONT=arial] grub-efi[/FONT]
[FONT=arial]kubuntu@kubuntu:~$ sudo chroot "/mnt/boot-sav/sda6" apt-get install -fy[/FONT]
[FONT=arial]Reading package lists... Done[/FONT]
[FONT=arial]Building dependency tree       [/FONT]
[FONT=arial]Reading state information... Done[/FONT]
[FONT=arial]0 upgraded, 0 newly installed, 0 to remove and 346 not upgraded.[/FONT]
[FONT=arial]2 not fully installed or removed.[/FONT]
[FONT=arial]After this operation, 0 B of additional disk space will be used.[/FONT]
[FONT=arial]Setting up grub-efi-amd64 (2.00-13ubuntu3) ...[/FONT]
[FONT=arial]dpkg: error processing grub-efi-amd64 (--configure):[/FONT]
[FONT=arial] subprocess installed post-installation script returned error exit status 1[/FONT]
[FONT=arial]dpkg: dependency problems prevent configuration of grub-efi:[/FONT]
[FONT=arial] grub-efi depends on grub-efi-amd64 (= 2.00-13ubuntu3); however:[/FONT]
[FONT=arial]  Package grub-efi-amd64 is not configured yet.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]dpkg: error processing grub-efi (--configure):[/FONT]
[FONT=arial] dependency problems - leaving unconfigured[/FONT]
[FONT=arial]No apport report written because the error message indicates its a followup error from a previous failure.[/FONT]
[FONT=arial]                                                                                                          Errors were encountered while processing:[/FONT]
[FONT=arial] grub-efi-amd64[/FONT]
[FONT=arial] grub-efi[/FONT]
[FONT=arial]E: Sub-process /usr/bin/dpkg returned an error code (1)[/FONT]
[FONT=arial]kubuntu@kubuntu:~$ man apt-get[/FONT]
[FONT=arial]kubuntu@kubuntu:~$ sudo chroot "/mnt/boot-sav/sda6" apt-get purge -y --force-yes grub*-common shim-signed linux-signed*[/FONT]
[FONT=arial]Reading package lists... Done[/FONT]
[FONT=arial]Building dependency tree       [/FONT]
[FONT=arial]Reading state information... Done[/FONT]
[FONT=arial]Note, selecting 'grub-common' for regex 'grub*-common'[/FONT]
[FONT=arial]Note, selecting 'linux-signed-image-3.8.0-23-generic' for regex 'linux-signed*'[/FONT]
[FONT=arial]Note, selecting 'linux-signed-image-3.8.0-26-generic' for regex 'linux-signed*'[/FONT]
[FONT=arial]Note, selecting 'linux-signed-image-3.8.0-21-generic' for regex 'linux-signed*'[/FONT]
[FONT=arial]Note, selecting 'linux-signed-generic' for regex 'linux-signed*'[/FONT]
[FONT=arial]Note, selecting 'linux-signed-image-3.8.0-19-generic' for regex 'linux-signed*'[/FONT]
[FONT=arial]Note, selecting 'linux-signed-image-3.8.0-27-generic' for regex 'linux-signed*'[/FONT]
[FONT=arial]Note, selecting 'linux-signed-image-3.8.0-22-generic' for regex 'linux-signed*'[/FONT]
[FONT=arial]Note, selecting 'efilinux-signed' for regex 'linux-signed*'[/FONT]
[FONT=arial]Note, selecting 'linux-signed-image-3.8.0-25-generic' for regex 'linux-signed*'[/FONT]
[FONT=arial]Note, selecting 'linux-signed-image-generic' for regex 'linux-signed*'[/FONT]
[FONT=arial]Package 'shim-signed' is not installed, so not removed[/FONT]
[FONT=arial]Package 'efilinux-signed' is not installed, so not removed[/FONT]
[FONT=arial]Package 'linux-signed-generic' is not installed, so not removed[/FONT]
[FONT=arial]Package 'linux-signed-image-3.8.0-19-generic' is not installed, so not removed[/FONT]
[FONT=arial]Package 'linux-signed-image-3.8.0-21-generic' is not installed, so not removed[/FONT]
[FONT=arial]Package 'linux-signed-image-3.8.0-22-generic' is not installed, so not removed[/FONT]
[FONT=arial]Package 'linux-signed-image-3.8.0-23-generic' is not installed, so not removed[/FONT]
[FONT=arial]Package 'linux-signed-image-3.8.0-25-generic' is not installed, so not removed[/FONT]
[FONT=arial]Package 'linux-signed-image-3.8.0-26-generic' is not installed, so not removed[/FONT]
[FONT=arial]Package 'linux-signed-image-3.8.0-27-generic' is not installed, so not removed[/FONT]
[FONT=arial]Package 'linux-signed-image-generic' is not installed, so not removed[/FONT]
[FONT=arial]The following packages will be REMOVED:[/FONT]
[FONT=arial]  grub-common* grub-efi* grub-efi-amd64* grub-efi-amd64-bin* grub2-common*[/FONT]
[FONT=arial]0 upgraded, 0 newly installed, 5 to remove and 346 not upgraded.[/FONT]
[FONT=arial]2 not fully installed or removed.[/FONT]
[FONT=arial]After this operation, 8,234 kB disk space will be freed.[/FONT]
[FONT=arial](Reading database ... 129673 files and directories currently installed.)[/FONT]
[FONT=arial]Removing grub-efi ...[/FONT]
[FONT=arial]Removing grub-efi-amd64 ...[/FONT]
[FONT=arial]Purging configuration files for grub-efi-amd64 ...[/FONT]
[FONT=arial]Removing grub2-common ...[/FONT]
[FONT=arial]Removing grub-efi-amd64-bin ...[/FONT]
[FONT=arial]Removing grub-common ...[/FONT]
[FONT=arial]Purging configuration files for grub-common ...[/FONT]
[FONT=arial]dpkg: warning: while removing grub-common, directory '/etc/grub.d' not empty so not removed[/FONT]
[FONT=arial]Processing triggers for man-db ...[/FONT]
[FONT=arial]Processing triggers for install-info ...[/FONT]
[FONT=arial]Processing triggers for ureadahead ...[/FONT]
[FONT=arial]kubuntu@kubuntu:~$ sudo chroot "/mnt/boot-sav/sda6" apt-get install -y --force-yes grub-efi linux[/FONT]
[FONT=arial]Reading package lists... Done[/FONT]
[FONT=arial]Building dependency tree       [/FONT]
[FONT=arial]Reading state information... Done[/FONT]
[FONT=arial]linux is already the newest version.[/FONT]
[FONT=arial]The following extra packages will be installed:[/FONT]
[FONT=arial]  grub-common grub-efi-amd64 grub-efi-amd64-bin grub2-common[/FONT]
[FONT=arial]Suggested packages:[/FONT]
[FONT=arial]  multiboot-doc grub-emu xorriso desktop-base[/FONT]
[FONT=arial]The following NEW packages will be installed:[/FONT]
[FONT=arial]  grub-common grub-efi grub-efi-amd64 grub-efi-amd64-bin grub2-common[/FONT]
[FONT=arial]0 upgraded, 5 newly installed, 0 to remove and 346 not upgraded.[/FONT]
[FONT=arial]Need to get 1,142 B/1,973 kB of archives.[/FONT]
[FONT=arial]After this operation, 8,234 kB of additional disk space will be used.[/FONT]
[FONT=arial]Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring/main grub-efi amd64 2.00-13ubuntu3 [1,142 B][/FONT]
[FONT=arial]Fetched 1,142 B in 0s (3,023 B/s)     [/FONT]
[FONT=arial]Preconfiguring packages ...[/FONT]
[FONT=arial]Selecting previously unselected package grub-common.[/FONT]
[FONT=arial](Reading database ... 129360 files and directories currently installed.)[/FONT]
[FONT=arial]Unpacking grub-common (from .../grub-common_2.00-13ubuntu3_amd64.deb) ...[/FONT]
[FONT=arial]Selecting previously unselected package grub2-common.[/FONT]
[FONT=arial]Unpacking grub2-common (from .../grub2-common_2.00-13ubuntu3_amd64.deb) ...[/FONT]
[FONT=arial]Selecting previously unselected package grub-efi-amd64-bin.[/FONT]
[FONT=arial]Unpacking grub-efi-amd64-bin (from .../grub-efi-amd64-bin_2.00-13ubuntu3_amd64.deb) ...[/FONT]
[FONT=arial]Selecting previously unselected package grub-efi-amd64.[/FONT]
[FONT=arial]Unpacking grub-efi-amd64 (from .../grub-efi-amd64_2.00-13ubuntu3_amd64.deb) ...[/FONT]
[FONT=arial]Selecting previously unselected package grub-efi.[/FONT]
[FONT=arial]Unpacking grub-efi (from .../grub-efi_2.00-13ubuntu3_amd64.deb) ...[/FONT]
[FONT=arial]Processing triggers for ureadahead ...[/FONT]
[FONT=arial]Processing triggers for man-db ...[/FONT]
[FONT=arial]Processing triggers for install-info ...[/FONT]
[FONT=arial]Setting up grub-common (2.00-13ubuntu3) ...[/FONT]
[FONT=arial]Processing triggers for ureadahead ...[/FONT]
[FONT=arial]Setting up grub2-common (2.00-13ubuntu3) ...[/FONT]
[FONT=arial]Setting up grub-efi-amd64-bin (2.00-13ubuntu3) ...[/FONT]
[FONT=arial]Setting up grub-efi-amd64 (2.00-13ubuntu3) ...[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Creating config file /etc/default/grub with new version[/FONT]
[FONT=arial]dpkg: error processing grub-efi-amd64 (--configure):[/FONT]
[FONT=arial] subprocess installed post-installation script returned error exit status 1[/FONT]
[FONT=arial]dpkg: dependency problems prevent configuration of grub-efi:[/FONT]
[FONT=arial] grub-efi depends on grub-efi-amd64 (= 2.00-13ubuntu3); however:[/FONT]
[FONT=arial]  Package grub-efi-amd64 is not configured yet.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]dpkg: error processing grub-efi (--configure):[/FONT]
[FONT=arial] dependency problems - leaving unconfigured[/FONT]
[FONT=arial]No apport report written because the error message indicates its a followup error from a previous failure.[/FONT]
[FONT=arial]                                                                                                          Errors were encountered while processing:[/FONT]
[FONT=arial] grub-efi-amd64[/FONT]
[FONT=arial] grub-efi[/FONT]
[FONT=arial]E: Sub-process /usr/bin/dpkg returned an error code (1)[/FONT]
[FONT=arial]kubuntu@kubuntu:~$ [/FONT]

```

As you see above, I retried the commands more than once to see which one was causing the errors. Eventually, I decided to just continue with the repair process. Once BR finished, I restarted the laptop as it instructed. After a few seconds, my jaw dropped as I was FINALLY greeted with a fully functional GRUB!!!!

Here is the BR report in case anyone wants to see it: [http://paste.ubuntu.com/5969303/](http://paste.ubuntu.com/5969303/)

**For anyone who is unfortunate to come across a very similar problem, do the following:**
[LIST=1]
[*]Make sure Windows is setup to **NOT** save hibernation data (i.e. the hiberfiles). If it is, then DISABLE IT ([http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html))!
[*]Run Kubuntu LiveCD/LiveUSB
[*]If install reports something like "t[COLOR=#000000]he 'grub-efi-amd64-signed' package failed to install into /target/. (NOTE: With SecureBoot enabled)"[/COLOR], then install and run Boot-Repair ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair))
[*]Restart the laptop and verify you can dual boot. If not and SecureBoot was enabled, then try running BR again but with SecureBoot disabled.
[/LIST]

---

### Post by oldfred on 2013-08-11
Yann may know sequence better, but the error may be from trying to install the secure boot version when booted with secure boot off. You should not need secure boot for either Windows nor Ubuntu. 
You have to boot Boot-Repair with secure boot on to install Ubuntu signed kernels for secure boot with Ubuntu.

---

### Post by YannBuntu on 2013-08-12
Hello
wesley2, glad to see you found a way :)

Fred, the remaining issue is not due to SecureBoot: his SecureBoot is disabled, and he tries to install the non-secure version (see line 1062).
Issue is during the setting of package grub-efi-amd64:
> Setting up grub-efi-amd64 (2.00-13ubuntu3) ...
Creating config file /etc/default/grub with new version
dpkg: error processing grub-efi-amd64 (--configure):
 subprocess installed post-installation script returned error exit status 1

I don't know what this can be, nor what the consequence is, so I'd suggest to create a bug report on Launchpad at [https://bugs.launchpad.net/ubuntu/+source/grub2](https://bugs.launchpad.net/ubuntu/+source/grub2)

---

