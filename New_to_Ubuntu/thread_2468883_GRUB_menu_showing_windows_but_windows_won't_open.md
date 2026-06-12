---
title: "GRUB menu showing windows but windows won't open"
date: 2021-11-13
forum: New to Ubuntu
---

### Post by rookie69 on 2021-11-13
Hi.
My **windows 10** and **ubuntu** both works when i boot them from boot menu (UEFI menu) but from grub menu ubuntu opens perfectly but when i try to open windows it just wont work the page says "This pc needs to be repaired". I try updating GRUB menu. To mention I have 2 ssd one nvme(m.2) one sata SSD. I use ubuntu on m.2 and windows on sata drive. but in grub menu i see windows boot manager on nvme .
[HTML]Sourcing file `/etc/default/grub'Sourcing file `/etc/default/grub.d/init-select.cfg'
Sourcing file `/etc/default/grub.d/oem-flavour.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.11.0-40-generic
Found initrd image: /boot/initrd.img-5.11.0-40-generic
Found linux image: /boot/vmlinuz-5.11.0-38-generic
Found initrd image: /boot/initrd.img-5.11.0-38-generic
Found linux image: /boot/vmlinuz-5.11.0-37-generic
Found initrd image: /boot/initrd.img-5.11.0-37-generic
Found linux image: /boot/vmlinuz-5.10.0-1050-oem
Found initrd image: /boot/initrd.img-5.10.0-1050-oem
Found Windows Boot Manager on /dev/nvme0n1p2@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings
done
[/HTML]

But when i go to windows device manager i see that my boot drive is the sata ssd (sda) one. Can anyone help me. And if it isn't a problem for this community please do tell me i'll remove and post on windows community. Thank You. (I'm not that good in English. Pardon me if i made any mistake.)

---

### Post by tea for one on 2021-11-13
Each OS on a separate disk is a good plan.
Booting Ubuntu and Windows from UEFI menu is fine.

Dual booting is difficult enough in the first place and as both systems boot OK, then you only have a cosmetic problem with Grub.

Before offering any suggestions, can you confirm:-

Both systems have been installed in UEFI mode?
Both systems have GPT?
If one disk is removed, does the other disk boot (and vice-versa)?
You have backups of personal data from both systems?

---

### Post by yancek on 2021-11-13
You mention 'windows; but not which release, is it 10?  The link below is the official Ubuntu documentation on dual booting windows 10 and Ubuntu in UEFI mode so I woul suggest you begin by reading through it to see if what you have done conforms with the instructions at the link below.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I would suggest that if you begin making changes, you keep careful notes of what the changes are in case they don't work so you can change back if necessary,

> Found Windows Boot Manager on/dev/nvme0n1p2 @/EFI/Microsoft/Boot/bootmgfw.efi

The line above shows the correct EF file needed to boot windows EFI on a GPT drive.  If you mount /dev/nvme0n1p2, do you see an ubuntu folder there with EFI files?
With both drives attached, open  terminal while booted into Ubuntu and run the following command and post the output here (that's a Lower Case Letter L in the command):

```
  sudo parted -l
```

This will tell if either or both drives are GPT or not.  It will also tell if there are EFI partitions on both drives or either drive and mounting the EFI drive(s) should show a Microsoft folder as well as an ubuntu folder with the proper EFI boot files.

On a computer with a preinstalled windows EFI, the Ubiquity installer of Ubuntu will install its EFI files on the already existing windows EFI partition which confuses people.  I would post the answers to the questions here before taking any steps to modify your install on the off chance it would make things worse.  At least now you can boot either.

---

### Post by mIk3_08 on 2021-11-13
> **rookie69 said:**
> Hi.
My windows and ubuntu both works when i boot them from boot menu (UEFI menu) but from grub menu ubuntu opens perfectly but when i try to opwn windows it just wont work the page says "This pc needs to be repaired". I try updating GRUB menu. To mention I have 2 ssd one nvme(m.2) one sata SSD. I use ubuntu on m.2 and windows on sata drive. but in grub menu i see windoows boot manager on nvme .
[HTML]Sourcing file `/etc/default/grub'Sourcing file `/etc/default/grub.d/init-select.cfg'
Sourcing file `/etc/default/grub.d/oem-flavour.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.11.0-40-generic
Found initrd image: /boot/initrd.img-5.11.0-40-generic
Found linux image: /boot/vmlinuz-5.11.0-38-generic
Found initrd image: /boot/initrd.img-5.11.0-38-generic
Found linux image: /boot/vmlinuz-5.11.0-37-generic
Found initrd image: /boot/initrd.img-5.11.0-37-generic
Found linux image: /boot/vmlinuz-5.10.0-1050-oem
Found initrd image: /boot/initrd.img-5.10.0-1050-oem
Found Windows Boot Manager on /dev/nvme0n1p2@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings
done
[/HTML]

But when i go to windows device manager i see that my boot drive is the sata ssd (sda) one. Can anyone help me. And if it isn't a problem for this community please do tell me i'll remove and post on windows community. Thank You. (I'm not that good in English. Pardon me if i made any mistake.)

You can also use EFI boot loader if you want to configure your Linux Ubuntu  GRUB menu. It is nice to see boot loader on multi Operating System. This might also help to solve your issue. So  Good Luck and Regards.

---

### Post by oldfred on 2021-11-13
Grub only boots working Windows.
Can you directly boot Windows from UEFI boot menu. Same boot key you used to boot Ubuntu live installer.

Often issue is Windows turns on fast start up with updates or needs chkdsk. Those can be fixed just by directly booting from UEFI.
If bigger issues you need your Windows repair/recovery flash drive.

---

### Post by rookie69 on 2021-11-13
[HTML]Model: ATA Samsung SSD 870 (scsi)Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size    File system  Name                          Flags
 1      1049kB  452GB  452GB   ntfs         Basic data partition          msftdata
 2      452GB   484GB  32.2GB  ntfs         Basic data partition          msftdata
 3      484GB   934GB  450GB   ext4                                                ##This is my local drive for ubuntu i keep movies types files not system files
 4      934GB   934GB  16.8MB               Microsoft reserved partition  msftres


Model: Samsung SSD 970 EVO Plus 500GB (nvme)
Disk /dev/nvme0n1: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size    File system     Name  Flags
 1      1049kB  456GB  456GB   ext4
 2      456GB   456GB  200MB   fat32                 boot, esp
 3      456GB   461GB  5120MB  linux-swap(v1)        swap

[/HTML]

---

### Post by rookie69 on 2021-11-13
> **tea for one said:**
> Each OS on a separate disk is a good plan.
Booting Ubuntu and Windows from UEFI menu is fine.

Dual booting is difficult enough in the first place and as both systems boot OK, then you only have a cosmetic problem with Grub.

Before offering any suggestions, can you confirm:-

Both systems have been installed in UEFI mode?
Both systems have GPT?
If one disk is removed, does the other disk boot (and vice-versa)?
You have backups of personal data from both systems?

Yes i think both are UEFI as i see in uefi boot menu UEFI-Ubuntu or UEFI-Windows 
I dont know about gpt. Sorry :( but i think its gpt as when i run parted -l it shows "Partition Table: gpt"
It's my laptop so i can't confirm now is there any other way
Yes i have backups

---

### Post by rookie69 on 2021-11-13
One thing i forgot to mention Windows version is Windows 10 and i can run windows smoothly from uefi boot menu. It just don't load from GRUB menu

---

### Post by rookie69 on 2021-11-13
> **oldfred said:**
> Grub only boots working Windows.
Can you directly boot Windows from UEFI boot menu. Same boot key you used to boot Ubuntu live installer.

Often issue is Windows turns on fast start up with updates or needs chkdsk. Those can be fixed just by directly booting from UEFI.
If bigger issues you need your Windows repair/recovery flash drive.
Yes i can run both os from UEFI boot menu 
i disabled fast start up many days ago

---

### Post by oldfred on 2021-11-13
Windows updates which you may not really see, can turn fast start up back on.

Or Windows can do an UEFI update which may reset some UEFI settings to defaults. I keep a list, but do not have Windows and always know if I have done an UEFI update as I do it myself.

---

### Post by tea for one on 2021-11-13
In post no. 6, I am surprised that your Windows 10 drive does not have an EFI partition.
Was Windows 10 pre-installed on that disk by the vendor?
As requested by [COLOR="#0000FF"]oldfred[/COLOR], can you also double check that Windows Fast Start Up is disabled.

---

### Post by rookie69 on 2021-11-14
Yes it was pre installed but i formatted my nvme drive completely and choose something else in UBUNTU installation.
And i recently bought this new ssd and made a clean format and make 2 partition and install windows in one partition on my sata ssd 
And fast startup is disabled 
i think as windows doesn't let us make these boot or home efi partition it somehow made efi in ubuntu partition. 
I only use windows for one software proteus provided by my university so i'm going to uninstall windows 10 after this semester. I said this to ask something? As you can see windows and ubuntu both efi is somehow in same partition do i need to fresh install ubuntu again?

---

### Post by yancek on 2021-11-14
Since you are currently able to boot both your windows 10 and Ubuntu UEFI, I would not bother trying to make any changes, particularly since you plan to stop using windows soon.

Your situation is unusual.  Windows generally comes preinstalled and with an EFI partition with windows EFI boot files on that EFI partition.  The Ubuntu Ubiquity installer will put the Ubuntu EFI files on the first EFI partitiion it finds which is the already exisiting windows EFI partition.

> i think as windows doesn't let us make these boot or home efi partition it somehow made efi in ubuntu partition.  

It isn't clear to me what you've done here.  It seems you had windows 10 preinstalled, then installed Ubuntu UEFI then reinstalled windows 10 again, is that correct.  Windows can and will create an EFI partition.  If you installed Ubuntu UEFI and then windows EFI, windows may have put its EFI files on the EFI partition created by Ubuntu.  Does the windows EFI partition need to be on the same physical drive as the windows OS?  I don't know, wouldn't think so but...don't really know.

>  As you can see windows and ubuntu both efi is somehow in same partition do i need to fresh install ubuntu again? 		 

Windows and Ubuntu EFI files are almost always on the same hard drive and on the same EFI partition although this is not necessary so I don't see that as a problem

I'd again suggest you leave things as they are until the end of your semester when you plan to remove windows.  I would also suggest you read through the Ubuntu documentation link I posted earlier as well as the links posted by oldfred and any other tutorials on dual booting windows 10 and Ubuntu UEFI.  I would keep detailed notes while doing this rather than trying to make any changes as you may accidentally create more problems for yourself.

One last thing I would suggest is to go to the link below to the boot repair site.  You can download boot repair using the 2nd option on that page to install boot repair in Ubuntu.  This is very useful software to have.  If you download it, I would suggest that you select the option to Create Boot Info Summary which will output detailed information on your system and its boot files which you will be able to review yourself or post the link you get here for others to review.  I would not suggest trying to make any repairs without input from more experienced members here.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by tea for one on 2021-11-14
I agree with [COLOR="#0000FF"]yancek[/COLOR] - Do not worry about Grub until you have finished your studies.

When dual-booting with each OS on a separate drive, it is good practice to only have the target drive visible when installing the second OS.

Install with UEFI mode and GPT
Install first OS on drive A
Remove (or isolate) drive A
Install second OS on drive B
Each installation will automatically have an EFI partition
Re-attach drive A
Check that each OS boots independently
Then configure Grub because you will be able to return to independent OS booting via UEFI

---

### Post by rookie69 on 2021-11-14
> **yancek said:**
> Since you are currently able to boot both your windows 10 and Ubuntu UEFI, I would not bother trying to make any changes, particularly since you plan to stop using windows soon.

Your situation is unusual.  Windows generally comes preinstalled and with an EFI partition with windows EFI boot files on that EFI partition.  The Ubuntu Ubiquity installer will put the Ubuntu EFI files on the first EFI partitiion it finds which is the already exisiting windows EFI partition.



It isn't clear to me what you've done here.  It seems you had windows 10 preinstalled, then installed Ubuntu UEFI then reinstalled windows 10 again, is that correct.  Windows can and will create an EFI partition.  If you installed Ubuntu UEFI and then windows EFI, windows may have put its EFI files on the EFI partition created by Ubuntu.  Does the windows EFI partition need to be on the same physical drive as the windows OS?  I don't know, wouldn't think so but...don't really know.



Windows and Ubuntu EFI files are almost always on the same hard drive and on the same EFI partition although this is not necessary so I don't see that as a problem

I'd again suggest you leave things as they are until the end of your semester when you plan to remove windows.  I would also suggest you read through the Ubuntu documentation link I posted earlier as well as the links posted by oldfred and any other tutorials on dual booting windows 10 and Ubuntu UEFI.  I would keep detailed notes while doing this rather than trying to make any changes as you may accidentally create more problems for yourself.

One last thing I would suggest is to go to the link below to the boot repair site.  You can download boot repair using the 2nd option on that page to install boot repair in Ubuntu.  This is very useful software to have.  If you download it, I would suggest that you select the option to Create Boot Info Summary which will output detailed information on your system and its boot files which you will be able to review yourself or post the link you get here for others to review.  I would not suggest trying to make any repairs without input from more experienced members here.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


It had preinstalled windows but i formatted/deleted full drive when i installed ubuntu
Than after some days i had to install windows 10 for that particular software 

here is my boot summary brother: [https://paste.ubuntu.com/p/7pQG6k53FP/](https://paste.ubuntu.com/p/7pQG6k53FP/)

---

### Post by rookie69 on 2021-11-14
> **tea for one said:**
> I agree with [COLOR=#0000FF]yancek[/COLOR] - Do not worry about Grub until you have finished your studies.

When dual-booting with each OS on a separate drive, it is good practice to only have the target drive visible when installing the second OS.

Install with UEFI mode and GPT
Install first OS on drive A
Remove (or isolate) drive A
Install second OS on drive B
Each installation will automatically have an EFI partition
Re-attach drive A
Check that each OS boots independently
Then configure Grub because you will be able to return to independent OS booting via UEFI

I would have done that if i had tools to remove drive from my laptop :(
Thank you for your suggestion

---

### Post by yancek on 2021-11-14
>   here is my boot summary brother

I'd save a copy of your boot repair in your /home/user directory for future reference and do some reading on installing Ubuntu alone on a GPT drive in UEFI mode.

---

### Post by oldfred on 2021-11-14
Grub will not boot Windows with UEFI Secure boot on.

Something about the chain of Secure boot from grub bootloader to Windows boot loader cannot be approved currently.

---

### Post by rookie69 on 2021-11-15
> **oldfred said:**
> Grub will not boot Windows with UEFI Secure boot on.

Something about the chain of Secure boot from grub bootloader to Windows boot loader cannot be approved currently.
Oh! I got it.

---

### Post by yancek on 2021-11-15
If you are able to boot both windows and Ubuntu from your UEFI menu , I  would not make any changes until I learned morel  Read the Ubuntu  documentation page from the link in post 3 for starters  While doing  that, I would suggest that you keep notes, detailed notes.

Both of your drives are GPT so that means windows 10 is an EFI install.

It is a bit unusual to not have an EFI partition on the windows drive but I don't know that is part of the problem.  You should be able to mount and access the EFI partition from Ubuntu and when doing so, you should see a Microsoft directory with windows EFI files and an ubuntu directory with Ubuntu EFI files.  Have you checked that.

One other thing that has been mentioned above is hibernation.  Some windows updates will turn hibernation back on without asking the user if s/he wants that to be done and the user will not be informed that it will be done so I would suggest that after any windows update, you go into the windows Power Settings to verify that hibernation has not been turned on again.

---

### Post by rookie69 on 2021-11-15
Thanks for the help
But i installed correctly following the documentation i think windows took ubuntu efi as his efi. It also happend to my dad's pc a couple of years ago. Where i installed windows in ssd but windows made the boot driver in hdd. (if i can remember correctly i formatted everything in hdd and i didn't even made a partition when i installed windows at that time.  I think same thing happend this time also where windows took ubuntu's efi drive as his efi drive. 
Btw can you guys tell me how can i browse this "EFI" drive? Actually i'm going to stop using windows soon so i will just format that ssd and delete windows's efi data from that drive. Because i can reinstall windows but it takes a lot of time to get the software currently installed on my pc. So, i'll just delete the data if that will cause no problem.

---

### Post by oldfred on 2021-11-15
I know with BIOS installs, Windows installs its boot loader partition to the default boot drive in BIOS. So if not installing to default drive, it will create a boot partition on default drive.
Not sure then with install of Windows in UEFI mode to second drive, if it uses a default. UEFI does not specifically have default drive, but default boot entry in UEFI partition.

Your ESP will have folders for each installed system. So the Windows folder will be /EFI/Microsoft.
And you have UEFI boot entries in UEFI for Windows.

You can use live installer & mount ESP, or change in fstab the default mount parameters so you can read & write into it with sudo. Default settings now prevent access for security.
[https://askubuntu.com/questions/794725/can-i-remove-windows-boot-manager-from-dedicated-ubuntu-computer](https://askubuntu.com/questions/794725/can-i-remove-windows-boot-manager-from-dedicated-ubuntu-computer)

To see UEFI entries:
sudo efibootmgr -v
See also 
man efibootmgr

---

### Post by yancek on 2021-11-16
>  Btw can you guys tell me how can i browse this "EFI" drive?

You need to be root (use sudo) to access the /boot/efi/EFI partition as everything in that partition shows as owner:group root:root and permissions 
700 (700 meaning root/sudo has read/write/execute permissions) and users/others have NO permissions.  So open a terminal and do sudo su 
(enter the sudo password when prompted)  and run this command:

```
ls /boot/efi/EFI
Boot  HP  Microsoft  mint  Slackware  ubuntu
 
```

Yours will be different but you should see Boot, Microsoft and ubuntu baed on the information you posted.  The different efi boot files for Ubuntu 
will obviously be in that ubuntu directory and the windows entry you posted earlier will be in the Microsoft directory.

"Found Windows Boot Manager on /dev/nvme0n1p2@/EFI/Microsoft/Boot/bootmgfw.efi"

Note that it is "/boot/efi/EFI" with  lower case efi and an upper case EFI.

This is how I usually do it although I accidentally noticed on Ubuntu that if I open the file manager and go to the boot directory, I will see an efi 
directory (Lower case efi) with a red x and clicking that prompts for the sudo password twice and the efi directory will open and I will see the EFI 
directory with the above directories shown above with the ls command.  Either way should work. I'm not sure why I am prompted twice for the sudo 
password when entering /boot/efi??

Or use the Ubuntu live installer suggested by oldfred which may be the better or proper method.

---

### Post by rookie69 on 2021-11-16
Thank You So much

---

### Post by rookie69 on 2022-01-31
[B]Probably my last message about this. 
[/B]I installed windows first and install ubuntu 20 LTS later (after installing windows), i choose something else and only create root and swap, U can also create home if you like but don't create a new efi. Now it works fine without any error.  
I leave this message if anybody have the same issue this might help
Thank You. <3

---

