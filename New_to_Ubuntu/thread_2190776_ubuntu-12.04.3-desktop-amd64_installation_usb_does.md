---
title: "ubuntu-12.04.3-desktop-amd64 installation usb does not see Win 8 on HDD"
date: 2013-11-29
forum: New to Ubuntu
---

### Post by swarup on 2013-11-29
I have just purchased a new Toshiba Satellite laptop which came with Win 8. I want to set up a dual boot. I've downloaded ubuntu-12.04.3-desktop-amd64.iso and created a bootable usb using the pendrivelinux utility. Everything worked fine. I set the bios in the laptop to boot first to the usb drive, and it went right to the usb and invited me to install ubuntu, which I selected. However when the setup program reached the stage of identifying what OS's are already on the HDD, it announced that there are no OS's on the drive and only gave me the option to erase the entire drive and put Ubuntu, or to set up the partitions manually. But it should see the Win 8 OS and give me the option to automatically set up a dual boot with Win 8 and Ubuntu. Why is it not seeing Win 8 and what needs to be done to set up the dual boot?

---

### Post by fantab on 2013-11-29
Try 13.10 as some here have reported problems with 12.04.03.

Also, in all probablity, you have UEFI boot, so follow the instructions below:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If you have more doubts or trouble the start by posting the output of:
```
sudo parted -l
sudo fdisk -l
```

---

### Post by swarup on 2013-11-29
I want the LTS support version. If the 12.04.2 will work better I can use that. As for the EFI, I could follow the instructions on that page but it I wonder whether those are the issues I was facing vis a vis the Ubuntu install not seeing Win 8 partition? Or perhaps I misunderstood somehow. Anyhow I would like to install 12.04, not 13.10.

Here is the requested ouput:

```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA TOSHIBA MQ01ABF0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  1075MB  1074MB  ntfs         Basic data partition  hidden, diag
 2      1075MB  1347MB  273MB   fat32        Basic data partition  boot
 3      1347MB  1482MB  134MB   ntfs         Basic data partition  msftres
 4      1482MB  489GB   487GB   ntfs         Basic data partition
 5      489GB   500GB   11.3GB  ntfs         Basic data partition  hidden, diag


Model: Memorex TD Classic 003B (scsi)
Disk /dev/sdb: 1029MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  1029MB  1029MB  primary  fat16        lba


ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
256 heads, 63 sectors/track, 60563 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT

Disk /dev/sdb: 1029 MB, 1029439488 bytes
16 heads, 32 sectors/track, 3927 cylinders, total 2010624 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd38379b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              32     2009087     1004528    e  W95 FAT16 (LBA)
ubuntu@ubuntu:~$ 

```

---

### Post by fantab on 2013-11-29
> **swarup said:**
> 
Here is the requested ouput:

```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA TOSHIBA MQ01ABF0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  1075MB  1074MB  ntfs         Basic data partition  hidden, diag
 **2      1075MB  1347MB  273MB   fat32        Basic data partition  boot**
 3      1347MB  1482MB  134MB   ntfs         Basic data partition  msftres
 **4      1482MB  489GB   487GB   ntfs         Basic data partition**
 5      489GB   500GB   11.3GB  ntfs         Basic data partition  hidden, diag


Model: Memorex TD Classic 003B (scsi)
Disk /dev/sdb: 1029MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  1029MB  1029MB  primary  fat16        lba


ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
256 heads, 63 sectors/track, 60563 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT

Disk /dev/sdb: 1029 MB, 1029439488 bytes
16 heads, 32 sectors/track, 3927 cylinders, total 2010624 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd38379b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              32     2009087     1004528    e  W95 FAT16 (LBA)
ubuntu@ubuntu:~$ 

```

Ubuntu's installer does not see any "space" for ubuntu on the 500GB HDD. It needs space to install. 
Create space for Ubuntu by [SHRINKING Windows8 partition]("http://www.tweakhound.com/2013/01/02/how-to-resize-your-windows-8-partition/") [487Gb] . And leave the space created as 'unallocated space'.

Then install Ubuntu...

---

### Post by swarup on 2013-11-29
Ok great! If that is all there is to it, I can take care of that-- thank you. I could try and see if once there is unallocated space, it will work. 

But my question/concern is this: currently there is no allocated space and Ubuntu is not seeing the Win 8 OS. If I create unallocated space, then the Ubuntu installer will probably be ready to install there. But will Ubuntu then begin to see Win 8 and set up GRUB to work as a dual boot for the two OS's? If the Ubuntu installer doesn't see Win8 now, I don't understand how it is going to see Win8 later and set up the dual boot. My concern is it will install Ubuntu and boot only to Ubuntu-- I'll be left without a way to boot to Win8.

---

### Post by fantab on 2013-11-29
It will, there is no reason for it not to see Windows8... make sure you[** boot Ubuntu DVD/USB in EFI mode only**]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_Ubuntu_DVD_in_EFI_mode").... 
EFI booting does NOT use MBR, if you boot your Ubuntu disk in MBR mode then I don't think '**grub-pc**' can look for boot files in EFI and in MBR it will not find anything... you need to boot with '**grub-efi**'.
How you boot Ubuntu DVD/USB is how you install it...

---

### Post by swarup on 2013-11-30
I went to the link in your last post. When I boot to the Ubuntu USB, it shows the UPPER screen of the two pictured-- which according to the link means that "the BIOS is set up to boot the CD in EFI mode". So I guess that means I am on the right road and can proceed to install. 

The link does state though that: "Warning: even if your PC boots the DVD in EFI mode, it might boot the HDD in Legacy mode." So we know the USB is booting in EFI mode, but it suggests here that even then the HDD may boot in legacy mode. Do I need to check for this somehow? Or am I ready to install once I shrink the Win8 partition?

---

### Post by fantab on 2013-11-30
> **swarup said:**
> 
The link does state though that: "Warning: even if your PC boots the DVD in EFI mode, it might boot the HDD in Legacy mode." So we know the USB is booting in EFI mode, but it suggests here that even then the HDD may boot in legacy mode. Do I need to check for this somehow? Or am I ready to install once I shrink the Win8 partition?

Your HDD IS booting in UEFI mode... just ignore the warning.

How much space is available for Ubuntu after Shrinking?

---

### Post by swarup on 2013-11-30
I didn't shrink it yet, but it is a 550 GB HDD & I was thinking to give half of that i.e. 250 GB to Ubuntu, unless Win8 will limit how much I can shrink it. 

When I expressed my concern as to how the installer is going to see Win8, you replied "It will, there is no reason for it not to see Windows8"-- but I had booted in EFI mode the first time as well, and when I went to install it didn't see any OS on the HDD then. That is why I am confused as to how that is going to change.

One other query: it seems so odd to me that we have to manually shrink the existing OS (Win8) ourselves. For years, the Ubuntu installer has been doing this for the user. Now they have removed this facility?

---

### Post by fantab on 2013-11-30
I don't let Ubiquity [Ubuntu's Graphical Installer] to manage partitions for me. I like to have more control so I do it manually.
UEFI is relatively a very new technology. And I am sure Ubiquity will improve and add more features to it. Ubiquity, if I am not mistaken, still offers to shrink your partitions for Ubuntu install on BIOS/Legacy setups. 
Also OEM's are NOT implementing UEFI according to prescribed "Standard" yet... UEFI implementations differ from one OEM to another... things will hopefully improve in future.
The earlier versios of 12.04 would NOT boot or install with 'Secure Boot' enabled on Windows8 Pre-Installed machines... Now they can with 'SHIM', a microsoft signed pre-bootloader.

My two cents...


NOTE: Run Defragmentation on the partition you want to 'Shrink'. After you have 'Shrink' your Windows Partition, boot Windows8 a couple of times.. If there are any filesystem errors then that should take care of it.

---

### Post by swarup on 2013-11-30
Thanks for all the tips! I'll definitely run defrag as you suggest. (It is a brand new computer and I haven't put a single file on it yet, so there may not be much to defrag)

Last point before I start: 

When I expressed my concern as to how the installer is going to see Win8, you replied "It will, there is no reason for it not to see Windows8"-- but I had booted in EFI mode the first time as well, and when I went to install it didn't see any OS on the HDD then. That is why I am confused as to how that is going to change. But you are confident that it will start to recognize Win8 somehow even though it doesn't recognize it now, right?

---

### Post by fantab on 2013-11-30
> **swarup said:**
> Thanks for all the tips! I'll definitely run defrag as you suggest. (It is a brand new computer and I haven't put a single file on it yet, so there may not be much to defrag)

Last point before I start: 

When I expressed my concern as to how the installer is going to see Win8, you replied "It will, there is no reason for it not to see Windows8"-- but I had booted in EFI mode the first time as well, and when I went to install it didn't see any OS on the HDD then. That is why I am confused as to how that is going to change. But you are confident that it will start to recognize Win8 somehow even though it doesn't recognize it now, right?

The very first thing the Installer does, AFAIK, is to look for space to install UBUNTU, when you choose "install Ubuntu'. But when it does not see any space it, I guess, does not report NTFS partitions. It looks for Other OS only when Grub is being installed or installed and OS-prober is run. I am not 100% sure about this... someone else with more knowledge of its internal mechanics will be able to explain more clearly and precisely.

Edit: If you want, you can after you shrink Windows Partition you can use '[Macrium Reflect]("http://www.macrium.com/reflectfree.aspx")' to make an image of your HDD and save it externally. It comes in handy if your want to restore Windows8 if there are any issues.
[http://kb.macrium.com/KnowledgebaseArticle50074.aspx](http://kb.macrium.com/KnowledgebaseArticle50074.aspx)
[http://kb.macrium.com/KnowledgebaseArticle50079.aspx](http://kb.macrium.com/KnowledgebaseArticle50079.aspx)
[http://kb.macrium.com/KnowledgebaseArticle50047.aspx](http://kb.macrium.com/KnowledgebaseArticle50047.aspx)
[http://kb.macrium.com/KnowledgebaseArticle50128.aspx](http://kb.macrium.com/KnowledgebaseArticle50128.aspx)

Or use any other similar software.

---

### Post by swarup on 2013-11-30
Ok, great-- that is really helpful. So it sounds like once I create unallocated space for the new OS, then the Ubuntu installer may start to see Win8 as well. Sounds like that is the conclusion. 

And sure, just for safety I could make the external image of the HDD, then it will be very safe.

---

### Post by oldfred on 2013-11-30
Best to make full backups of efi partition and Windows partition.
Have you turned off fast boot. That is Windows always on hibernation and when Windows is hibernated the installer cannot mount nor see the Windows install. That may then overwrite Windows.
Often best to turn off secure boot, but Ubuntu will install with secure boot on.

       Backup efi partition and Windows partition before Install of Ubuntu.
Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

      
 The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[URL="http://www.runtime.org/driveimage-xml.htm"]http://www.runtime.org/driveimage-xml.htm

[/URL]
 Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[URL="http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/"]http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/

      [/URL]
 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

    [URL="http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/"]
[/URL]

[URL="http://www.runtime.org/driveimage-xml.htm"]
[/URL]

---

### Post by fantab on 2013-11-30
> **oldfred said:**
> Best to make full backups of efi partition and Windows partition.
Have you turned off fast boot. That is [SIZE=2][SIZE=2]Windows always on hibernation and[/SIZE]** [COLOR=#0000ff]when Windows is hibernated the installer cannot mount nor see the Windows install[/COLOR]**[/SIZE]. That may then overwrite Windows.
Often best to turn off secure boot, but Ubuntu will install with secure boot on.

       
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)


Thanks for the info oldfred. And I guess that should answer OP's question.

---

### Post by swarup on 2013-11-30
Hey, just got home to find your very helpful post oldfred. Yes, that sounds like a likely reason why the installer could not see Win8. I will follow all the guidelines you both have given, and go about the install. Let us see how it goes :)

---

### Post by swarup on 2013-12-29
Ok-- I followed all the steps on [this post]("http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710") as recommended by oldfred. I shrank the Win8 partition and thereby created 200GB of unallocated space for Ubuntu to be installed on. After using Macrium Reflect to make a restore image of Win8 on an external HDD, I then booted to the bootable usb 12.04.3, and proceeded to install Ubuntu. BUT even though I had created unallocated space for Ubuntu to be installed on, it STILL did not see that unallocated and threatened that there are only two options: (1) "Erase disk and install Ubuntu, which will delete any files on the HDD; or (2) Manually create partitions myself. I was expecting that after shrinking Win8, it will give me the option to install to the unallocated space and will set everything up for me. So why is it still not working properly?

---

### Post by fantab on 2013-12-29
Did you [turn off 'FastStartup']("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html") in Windows8?

---

### Post by oldfred on 2013-12-29
Is this an Ultrabook. Those use RAID to implement the Intel SRT and the desktop installer does not work with RAID. You then have to turn off Intel SRT and remove RAID meta-data.
Did you reboot into Windows after the resize? It has to run chkdsk and make some repairs based on its new size. The chkdsk flag is another flag the can prevent the installer from working correctly?

And is this a very new Haswell processor? Or 4th gen Intel. Those must have the newest Ubuntu or 13.10 or 12.04.4 when it comes out in Jan.
And they also need some UEFI/BIOS setting changes.

Some other Toshiba and what those users did.
 Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Another users in same thread used Legacy mode and then NIC worked.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor                               
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)
How to install Ubuntu 13 dual boot with Windows 8 Ubuntu Studio
[http://ubuntuforums.org/showthread.php?t=2186838](http://ubuntuforums.org/showthread.php?t=2186838)

---

### Post by swarup on 2013-12-30
> **fantab said:**
> Did you [turn off 'FastStartup']("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html") in Windows8?

Yes, I had already done that. Fast startup was already off. Even then the Ubuntu install fails to recognize the unallocated space and does not offer to install itself  in that space.

---

### Post by swarup on 2013-12-30
@oldfred: This computer is a Toshiba Satellite C55-A5300. After the resize I did reboot into Windows twice (the instructions said to do so for this very reason). The computer is a Toshiba, but doesn't seem to match the model numbers you mention. And the chip is an Intel® Celeron® Processor 1037U. This laptop is not one of the upper level models. It is an entry level laptop, and has an older chip in it. I think it is not a Haswell processor.

---

### Post by fantab on 2013-12-30
Check under your UEFI/BIOS to see what mode is SATA set to: the likely options are IDE, AHCI and RAID... let us know what you see.

---

### Post by oldfred on 2013-12-30
I saw this posted somewhere on older Toshiba's with UEFI. Now older so Toshiba may have an update that fixes it.

 Some Toshiba's will not boot.
 they managed to leave the signing key out of the database that's used to validate binaries

---

### Post by swarup on 2013-12-30
> **fantab said:**
> Check under your UEFI/BIOS to see what mode is SATA set to: the likely options are IDE, AHCI and RAID... let us know what you see.

At boot up I hit F12 to go into Set Up, which is what I understand to be entering the Bios. If not, please let me know where to go. Under setup I do not see anywhere the listings to which you refer. These are the classifications: Main, Security, Power Management, Advanced, Boot, Exit. I didn't find the SATA mode listed under any of these.

---

### Post by swarup on 2013-12-30
> **oldfred said:**
> I saw this posted somewhere on older Toshiba's with UEFI. Now older so Toshiba may have an update that fixes it.

 Some Toshiba's will not boot.
 they managed to leave the signing key out of the database that's used to validate binaries

I couldn't understand so well what you've expressed here, but this Toshiba is really not an old Toshiba. I bought it completely new 5 weeks ago. It is an entry level computer, but it is not old.

Anyhow, what is the bottom line here. I'll be able to install Ubuntu, won't I? I bought this computer to give to a friend in India, and I'll be leaving in six days for India to give it to him. There are only two options listed for install, as I mentioned earlier. The first is to totally delete everything on the drive and have only Ubuntu. The other is to do a manual install.

If you have any further ideas for how to get Ubuntu to auto install to the unallocated space, that will be great.

Otherwise, If you think it will work out, please give basic instructions and I'll select the manual option. I know one has to create an ext3 partition for the Ubuntu OS, and then another partition for linux-swap. This shouldn't be very difficult. The GRUB sits inside the Ubuntu OS, right?

---

### Post by oldfred on 2013-12-30
Some of the new Atom systems are totally locked down or Windows only. But you should be able to install. 

And if that new 13.10 may work better as UEFI has been updated a lot. Or the 12.04.4 that will be out in Jan. will also have lots of updates particularly UEFI.

You may still have updates to UEFI/BIOS from vendor. Worth checking to see.

But if the installer is not seeing partitions, either fast boot is still on or partition needs chkdsk after the resize.

---

### Post by swarup on 2013-12-30
Fast boot is definitely off. I turned it off, and in control panel it says it is off. Does chkdsk run automatically, on bootup, or do I need to run it? I have not run it, so if that needs to be done please remind me how to give that command, and I'll do it. 

As for 13.10, it is only supported for a few months. I am giving this computer to a total new-comer, so I want to give him something he can use for a longer time before a new OS is needed. And I'm leaving in six days, before 12.04.4 will come out. So I'd like to try and get 12.04.3 installed.

I downloaded the lasted bios from the toshiba website for this laptop. I'd like to find out what the current version the laptop is, and if this is newer then I'll install it.

---

### Post by oldfred on 2013-12-30
It used to be with BIOS you would see version on screen as it booted. But now UEFI is a lot quicker, so you may not be able to see it. But you should be able to go into UEFI and it should show version.

---

### Post by Jonathan Precise on 2013-12-30
> **swarup said:**
> I couldn't understand so well what you've expressed here, but this Toshiba is really not an old Toshiba. I bought it completely new 5 weeks ago. It is an entry level computer, but it is not old.

Anyhow, what is the bottom line here. I'll be able to install Ubuntu, won't I? I bought this computer to give to a friend in India, and I'll be leaving in six days for India to give it to him. There are only two options listed for install, as I mentioned earlier. The first is to totally delete everything on the drive and have only Ubuntu. The other is to do a manual install.

If you have any further ideas for how to get Ubuntu to auto install to the unallocated space, that will be great.

Otherwise, If you think it will work out, please give basic instructions and I'll select the manual option. I know one has to create an ext3 partition for the Ubuntu OS, and then another partition for linux-swap. This shouldn't be very difficult. The GRUB sits inside the Ubuntu OS, right?


EDIT: **Go to solution 2** as it might not make sense to shrink your partition even further.

**[SIZE=5]SOLUTION 1:[/SIZE]**

[s]I had a similar issue with an HP-2000 notebook PC. The way it worked for me was installing ubuntu 13.04 (NOT 13.10), then upgrading via the update-manager to 13.10.

PROS: Installer might detect your windows partition. EDIT: You already shrinked your windows partition, thus it makes no sense to use this as it will shrink it the windows partition even further.

CONS:
[LIST]
[*]**This is an outdated version of ubuntu.**
[*]**Upgrading my laptop took ~ 5-6 hours.**
[*]You will need some time.
[*]Will end up with 13.10, not 12.04
[/LIST]
[/s]

**[SIZE=5]SOLUTION (WORKAROUND) 2:[/SIZE]**

I had a similar issue with another HP-2000 notebook PC. Used the manual partitioning:

In the FREE SPACE, create a new partition. In the size part, shrink it by about 6000 MB. Ext4 journaling filesystem, format the partition, and mount-point /.
Wait...
In the FREE SPACE, create a new partition. Leave the size part alone. Linux Swap.
Wait...
INSTALL

PROS: Faster. Will end up with ubuntu 12.04.
CONS: Will have to do the manual partitioning.

---

### Post by swarup on 2013-12-30
@ Jonathan Precise: Sounds perfect, and very easy. Let me try it right now and see how it goes. But one question: Is there a danger that after installing Ubuntu, even then Win8 will not be seen by GRUB and the computer will only boot to Ubuntu? 

The fact that the installer does not see Win8 Partition, does this indicate that after installation as well Win8 Partition is not going to be visible and there not accessible i,e, unable to be booted to?

I actually went through all the steps just now: I booted up to the 12.04, went into the installer, selected to do manual partitioning, set up the two partitions exactly as you suggested, and everything looked beautiful. But I then clicked on quit rather than install, only because I am afraid Ubuntu is going to install and GRUB is not going to see Win8 so I'll end up only with Ubuntu. Do I have to be concerned about this, or once Ubuntu installs GRUB will see Win8 and everything will be fine?

---

### Post by oldfred on 2013-12-30
Yes or no.
If you install in UEFI mode not BIOS you will be able to boot both Ubuntu and Windows from grub menu, but may need fixes per below.
If you install Ubuntu in BIOS mode, you will only be able to boot from UEFI menu and may have to turn on CSM/BIOS/Legacy mode to boot Ubuntu and turn on UEFI mode to boot Windows.
Also some are hard coded to only boot Windows.
And grub has a bug in its os-prober and still only creates BIOS boot entries for Windows, but Windows is in UEFI mode. That bug is fixed with 13.10.
And Boot-Repair has fixes or workarounds for all those issues, but you have to run Boot-Repair to fix them.

       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by oldfred on 2013-12-30
You need to make sure that you have available both the Ubuntu live installer and a Windows repairCD or flash drive. Otherwise if issues you will not be able to fix. And they need to always be the current version or recent version of other repair ISO like parted magic, gparted, Knoppix and Windows repair CD.

       Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

I do not travel without several flash drives. One is a full install, and a couple that are repair flash drives with multiple bootable ISO to fix things.

---

### Post by swarup on 2013-12-30
Wow, great info-- thank you! This will be very helpful as I prepare to do the install. I would really like this to go smoothly.

With so many complicating issues, it is a wonder that anyone-- any common user -- manages to install Ubuntu! I'm not talking about geeks, but just simple users. I thought that Ubuntu must have perfected the install process after all these years. But I see it has only gotten tougher and more complex to do a basic install. All I want to do is put Ubuntu on a basic laptop for a friend. And to do it, I have had to spend hours and hours of preparation. And it looks as though I am still not ready. I shall have to make a Windows repair CD and learn how to use it, and also have to be ready to run boot-repair.

---

### Post by oldfred on 2013-12-30
With Windows 8, you have UEFI and secure boot issues. And high end systems  have Intel SRT, RAID, dual video issues. And many vendors do not support hardware in Linux so everything has to be reverse engineered and then Linux does not support new systems as well.

The last few Windows 7 systems did use UEFI from some vendors and they just installed without issue. But did have to choose UEFI or BIOS.
With old BIOS there was no choice and Ubuntu then installed, but Windows 7 often configured to use all 4 primary partitions where XP or Vista did not. So that often created issues.

Microsoft was convicted and lost a suit where they made it impossible to install other software. Not saying they are still trying to do that.

---

### Post by swarup on 2013-12-31
Ok. I have created all my rescue media, and I think I am ready to go. I've started up the installer, and selected manual partitioning. I've allocated 200 GB for ext4, and 6 GB for swap. One final question before I click on "Install Now". In Ubuntu's on-line instructions for installing in EFI mode with manual partitioning, it says:

> If you use the manual partitioning ("Something else"), the difference is that you will have to set the /boot/efi mount point to the EFI partition. And if there was not any EFI partition on your HDD, you first will have to create it (see the "Creating an EFI partition" paragraph below). 

My HDD already has an EFI partition that came with the pre-installed Win8. So as I understand, since there is already an EFI partition, I should not create one. But it does say in the above quote that I have to "set the /boot/efi mount point to the EFI partition." Do I have to do something for this? At the bottom of the manual partitioning screen, it says "Device for boot loader installation", and one can either leave it at the current setting of /dev/sda, or reset it to another partition. On this computer, the EFI partition is /dev/sda2. Am I supposed to set the "Device for boot loader installation" to the EFI partition at /dev/sda2? Is that what the Ubuntu instructions meant by "you will have to set the /boot/efi mount point to the EFI partition" ? Or should I just leave the "Device for boot loader installation" at its current setting of /dev/sda ?

---

### Post by oldfred on 2013-12-31
The mount point in fstab is automatically added by the grub-efi installer.
The boot loader combo box on the partitioning screen should just be sda or the drive. 
With BIOS it always should be sda, and I do not think saying anything else with the efi installer matters, but not sure. But if in BIOS mode then it would install grub to a PBR not the MBR and that does not work. Just leave at default of sda.

If allocating 200GB total for Ubuntu, I might suggest 10 to 25GB, many use 20GB, and add another partition for /home. That is optional and can only be done during Something else as another mount point during install. 
System does not use much space. But if installed to a large partition, the system files may be anywhere in that partition. Or drive has to move around a bit more. With data you do not access often having that anywhere on drive is not an issue.

Only disadvantage of multiple partitions is if one fills up and you have lots of space in another it can be difficult to resize later. But system partition does not grow a lot, but some housecleaning occasionally is suggested. 
Only servers or users with advanced special requirements may then also create separate partitions for other system folders. It shows a lot of options in manual install.
My / (root) uses about 11GB of 25GB. And that includes my /home but no data as I have another drive with all my data.

---

### Post by swarup on 2013-12-31
Ok-- I ran the install, and it worked smoothly. When it finished, I rebooted the computer. When the computer boots, for a brief second some error message flashes on the screen in the upper left corner (not time enough to read it), and then the computer boots straight into Ubuntu. No grub screen ever shows up. I have booted the computer up twice, and it did the same thing each time. So no sign of grub, and no sign of windows. 

What is the next step? What needs to be done to get grub to show up and the dual boot working?

---

### Post by oldfred on 2013-12-31
It is not seeing Windows, is fast boot or hibernation still on?
Try this:
sudo update-grub

If not run BootInfo report from Boot-Repair.
       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by swarup on 2013-12-31
I had a feeling this might happen, since it was never able to see the Win8 partition prior to the install. Fast boot is definitely off-- I turned it off in Win8 and checked it so many times when you guys were asking me about it. No one has ever mentioned hibernation to me on this thread, that I know of. I did not do anything with hibernation, and I cannot say anything about it. 

I did "sudo update-grub" in the Ubuntu terminal window. It did not make any difference.

I am burning the boot-repair cd now, and when I get the Boot-Info URL, I will paste it here.

---

### Post by swarup on 2013-12-31
Here is the link to the Create BootInfo report:

[http://paste.ubuntu.com/6669581/](http://paste.ubuntu.com/6669581/)

---

### Post by oldfred on 2013-12-31
You also have secure boot on.
> SecureBoot enabled.

Ubuntu will work with secure boot on. But there are several bugs that may cause issues.
Grub2's os-prober does not correctly find Windows efi files except with the very newest 13.10. Boot-Repair will add correct entries.
There is also another bug with 13.10 (maybe others) where the grub menu entry will not chainload to the Windows UEFI entry if secure boot is on. You have to use UEFI menu or one time boot key that may be f12 but does vary by vendor.

If you can boot ubuntu entry in UEFI menu do not let Boot-Repair run its buggy  UEFI rename. That is only for those systems that only boot Windows as they have hard coded UEFI to boot Windows only. The rename is a work around but then you cannot boot Windows from UEFI menu as that entry in UEFI becomes grub.

---

### Post by swarup on 2013-12-31
Ok, so are you thinking then that this "SecureBoot Enabled" is the cause of the problem? And if so, I'm sorry I could not catch from your post what it is you want me to do now. What should be my next step to solve the matter?

If you want me to run boot repair, can it be done from within Ubuntu 12.04? I installed the program there, because I could not get the computer to boot to the cd I made. I downloaded "boot-repair-disk-64bit.iso" and burned it to disc as an iso image. I also adjusted the boot order so it would boot to the cd before the HDD. Even then it won't boot to the cd; you just hear the cd revving up and then it ultimately just boots to Ubuntu. 

But anyhow I did install the boot repair application in Ubuntu 12.04 and can run it from there if that is what you want me to do.

---

### Post by Jonathan Precise on 2013-12-31
Please post the outputs of:

```
cat /etc/grub.d/40_custom
cat /etc/grub.d/proxifiedScripts/custom
cat /etc/grub.d/proxifiedScripts/os-prober
```

If the outputs are too long, then show the URLs of:

```
sudo apt-get install pastebinit
cat /etc/grub.d/40_custom | pastebinit
cat /etc/grub.d/proxifiedScripts/custom | pastebinit
cat /etc/grub.d/proxifiedScripts/os-prober | pastebinit
```

As for secure-boot, press a key like F12, F10, ESC, etc. during boot. This will show up the BIOS menu.

In the part it says BOOT, BOOT OPTIONS, or something similar, you will see something about secure-boot. Set it to OFF, DISABLED, or a similar option.

Then boot to the CD (boot-repair). Run boot-repair as oldfred mentioned: Choose advanced-options. Un-check the "Backup and rename windows boot entries (solves the [hard-coded-efi] error)". Then click "Apply". Indicate the URL and any error messages (if there are any). Reboot. Post the results.

---

### Post by swarup on 2013-12-31
Here is the output. You'll see that only the first of the three requests gives any result:

```
:~$ cat /etc/grub.d/40_custom | pastebinit
[http://paste.ubuntu.com/6669854/](http://paste.ubuntu.com/6669854/)
:~$ cat /etc/grub.d/proxifiedScripts/custom | pastebinit
cat: /etc/grub.d/proxifiedScripts/custom: No such file or directory
You are trying to send an empty document, exiting.
:~$ cat /etc/grub.d/proxifiedScripts/os-prober | pastebinit
cat: /etc/grub.d/proxifiedScripts/os-prober: No such file or directory
You are trying to send an empty document, exiting.
:~$ cat /etc/grub.d/proxifiedScripts/custom
cat: /etc/grub.d/proxifiedScripts/custom: No such file or directory
:~$ cat /etc/grub.d/proxifiedScripts/os-prober
cat: /etc/grub.d/proxifiedScripts/os-prober: No such file or directory
```

---

### Post by Jonathan Precise on 2013-12-31
Sorry, I use ubuntu 13.10. The files /etc/grub.d/proxifiedScripts/custom and /etc/grub.d/proxifiedScripts/os-prober probably don't exist in a standard 12.04 installation

Now post the outputs of:

```
sudo -i blkid /dev/sda2 | pastebinit
```

You will at first see:

```
[sudo] password for *youruser*: 
```

Enter your password. You will not see anything there (not even dots).This is normal, and it is a security feature.

Now, out of curiosity, post the output of:

```
ls /etc/grub.d/proxifiedScripts | pastebinit
echo $?
```

---

### Post by swarup on 2013-12-31
I executed Boot Repair with the "Backup and rename Windows EFI files" option unchecked. When I unchecked the option, I first got this message:

```
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? (if any choice fails, please retry with the other)

```

I opted to keep the option unchecked, and then the Boot Repair went ahead and did its work. After finishing, it gave me this message:

```
Boot successfully repaired.

Please write on a paper the following URL:
http://paste.ubuntu.com/6669901/

In case you still experience boot problem, indicate this URL to:
boot.repair@gmail.com or to your favorite support forum.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sda2/EFI/ubuntu/grubx64.efi file!

The boot files of [The OS now in use - Ubuntu 12.04.3 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. (https://help.ubuntu.com/community/BootPartition)

You may want to retry after activating the [Backup and rename Windows EFI files] option.


```

Now Grub shows up on boot, and both Win8 and Ubuntu 12.04.3 boot up fine.

Do I need to do anything about the above message that the boot files of Ubuntu are far from the start of the disk? Would it speed up the boot if I do what they suggest? (I don't want to disturb anything though-- it is working now and that is wonderful!)

---

### Post by Jonathan Precise on 2013-12-31
No. That is not necessary now, as modern BIOS implementations can detect them.

Also, go to thread tools and mark this thread as solved.

---

### Post by oldfred on 2013-12-31
The far from start of disk was an issue with some BIOS systems, and particularly USB. They give a partition not found even though UUID is correct and will not boot. Have not seen a UEFI system with that issue, but have not seen many UEFI USB boots either.

The proxified versions of grub are from Grub Customizer. If you have not run it, then you do not have those versions. 

Glad system is working :)

---

### Post by Jonathan Precise on 2013-12-31
> **oldfred said:**
> The proxified versions of grub are from Grub Customizer. If you have not run it, then you do not have those versions.

Ok. Thanks for the info!

---

### Post by swarup on 2013-12-31
Thanks to both of you for all your help! It is wonderful to have a functional computer which I can give to my friend. :)

---

