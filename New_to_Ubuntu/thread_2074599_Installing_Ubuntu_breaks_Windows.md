---
title: "Installing Ubuntu breaks Windows ?"
date: 2012-10-22
forum: New to Ubuntu
---

### Post by MDJPster on 2012-10-22
OK, I'm a VERY basic user here, so go easy on me, but I also tend to bite off more than I can chew... Hopefully someone can give me a hand here, cause I really like Ubuntu. :)

Let me give you guys a little info on my system... I'm running a 120GB SSD for Windows ONLY, and a 2TB HDD for all my other stuff. For about 1.5 months I had Ubuntu on a 320GB HDD that was working fine. A couple days ago I decided to ditch that relic and install Ubuntu on the SSD, alongside Windows. I then realized Windows was taking up the whole drive (only 2GB left out of 120GB). So I started fooling around in Windows, playing in things I had no idea what I was doing (like I heard disabling hibernation and moving the page file to my 2TB drive would free-up space on the SSD. I also ran CCleaner in my registry and temp folder). All was fine until I rebooted, and Windows was gone ("BOOTMGR not found, press Ctrl-Alt-Del to restart" in DOS).

After successfully re-installing Windows, I went to install Ubuntu  on the 2TB drive. Since then, I cannot access Windows. Via GRUB (I think that's the name of the switcher that allows you to choose between Win and Ubuntu, right?) it says "EFI not found". When I bypass that and boot straight from the SSD, DOS tells me to run my Windows install CD and click "Repair" but when I do that all it says is "Startup errors cannot be automatically fixed". If I unplug the 2TB, all I get is a cryptic error message followed by "GRUB-rescue". I've managed to get Windows running, but only by deleting the Ubuntu partition of the 2TB will the Win installation be successful. Otherwise it gives the above errors after the first reboot.

I have no idea what I've done, but I certainly know now not to overestimate my knowledge of tech...

---

### Post by NikTh on 2012-10-22
Hi, 

you will need 2 things.

1) The bootCD or USB of Ubuntu and boot from there 

2) Install [boot-repair](https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu) program and run the [Recommended Repair]. 

**Do not forget** to give here the **Link with the boot-info** . Useful informations for us to resolve your problem, in case that [Recommended Repair] not solving it.

Thanks

---

### Post by MDJPster on 2012-10-22
Here's the link: [http://paste.ubuntu.com/1298009/](http://paste.ubuntu.com/1298009/)

When I boot normally, it gives:

error: file '/boot/grub/x86_64-efi/normal.mod not found.
grub rescue 

I have to go into BIOS and boot from the Ubuntu drive manually. Also Windows is giving me the same errors as before.

---

### Post by *^kyfds( on 2012-10-22
is there anything still on the hard disk that you would still need to back up?

---

### Post by MDJPster on 2012-10-22
Yes, about 600GB of media+video games.

---

### Post by *^kyfds( on 2012-10-22
i was going to suggest wiping everything, but it's obviously not practical.

Go along with NikTh's thread.


Boot loaders give me a headache too.

---

### Post by gerrman97 on 2012-10-22
well first off you shouldnt have reinstalled windows. you should have done a boot repair with the operating systems install disc.
now ill tell u what u should do
take your install disc and put it in your drive
boot from disc
when screen loads
click whatever button gets you to the partition screen
FORMAT the SSD
reinstall windows
download wubi.exe from the ubuntu website
install on your SSD
everything should work fine
Have Fun,
Gerrman97

---

### Post by MDJPster on 2012-10-22
> **gerrman97 said:**
> well first off you shouldnt have reinstalled windows. you should have done a boot repair with the operating systems install disc.
I tried repair, and the installer said my version of Windows was not compatible or something like that.

---

### Post by LiamOS on 2012-10-22
If you don't mind reinstalling everything...
Here comes the *Max Power* way:

Create a new partition in the 2GB disk, and copy over your music, etc. (XFS is a good filesystem to use for that.)
Reinstall Windows and Ubuntu whereever you like, as long as you leave the new partition intact. 
Copy things back to where they should be.


Regarding the "EFI not found" issue, do you know if you were using a GUID Partition Table? I remember trying to install W7 on my sister's laptop with a GPT, and Windows 7 needs EFI(didn't have it) to boot from GPT... Talk about broken. Since then I haven't touched Windows outside of virtualbox.

---

### Post by MDJPster on 2012-10-22
2GB? Or 2TB? All my stuff is on the 2TB. 2GB is the remaining space on my SSD (Windows drive). Should I create the partition in Ubuntu or it makes no difference? XFS is the formatting, I imagine (like NTFS or FAT32)? As for the current formatting, I installed Windows first (using the Windows installer's default way of formatting, I suppose) on the SSD, then I used the Ubuntu installer and clicked on the "Install Ubuntu alongside Windows 7" option, selected my 2TB (non-Windows, storage only) disk and allocated 150GB to Ubuntu. I used the simple partition tool, the one where you just drag the slider to allocate space (with Ubuntu on the left). It never asked me anything about a partition table.

---

### Post by oldfred on 2012-10-22
It looks like you have your Windows boot/repair partition on the SSD. When you installed Windows was the SSD set as the boot drive? That partition has two of your boot files and is normally on the same drive as the main Windows install.

If Windows is in efi mode you need to install Ubuntu in UEFI mode. You have to boot the installer CD or USB in UEFI mode to have it install in UEFI mode.

Windows Recommended UEFI-Based Disk-Partition Configurations
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)

[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

Lots of detail on SSDs.
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

---

### Post by MDJPster on 2012-10-22
> **oldfred said:**
> It looks like you have your Windows boot/repair partition on the SSD. When you installed Windows was the SSD set as the boot drive? That partition has two of your boot files and is normally on the same drive as the main Windows install.

So I need to set the SSD (or whatever drive I want to install Windows on) as the main boot drive in BIOS before booting from the install CD?

---

### Post by oldfred on 2012-10-22
Yes,

Windows seems to know which drive in BIOS is boot drive and installs boot files to that drive. 

Grub just defaults to sda.

Since most have one drive either result is the same for most, but when you have multiple drives results then are different.

---

### Post by NikTh on 2012-10-23
Hi, 

in your situation I would follow the advice of boot-repair 

[quote="boot-repair"]The boot files of [Ubuntu 12.10] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))[/quote] 
So if you can create another partition in Ubuntu's installation then 
Boot from a LiveCD-USB 
Create a separate /boot partition ext4 = 500MB 
Mount it to /boot 
and then run again the boot-repair program with the option of separate /boot partition. (advanced).
I don't know if you have to move the old /boot partition to the new or the boot-repair will perform these tasks for you, I never did that before. We will see.
And something else , might be important 
[quote="boot-repair"]Please do not forget to make your BIOS boot on sdb (2000GB) disk![/quote]

Thanks

---

### Post by YannBuntu on 2012-10-23
Hello

> **MDJPster said:**
> Here's the link: [http://paste.ubuntu.com/1298009/](http://paste.ubuntu.com/1298009/)

When I boot normally, it gives:

error: file '/boot/grub/x86_64-efi/normal.mod not found.
grub rescue 

I have to go into BIOS and boot from the Ubuntu drive manually. Also Windows is giving me the same errors as before.

- Your boot files are far from the start of the disk. You may need to reduce your Windows partition in order to create a little /boot partition at the start of your disk. see [https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)
- you have a mix of GPT and non-GPT disk. 
- your firmware is UEFI, but it is not sure if it is setup to boot the HDD in UEFI mode or not.

If i were you, i would :
1) backup documents 
2) disable UEFI in the BIOS: see [https://help.ubuntu.com/community/UEFI#Setup_the_BIOS_in_EFI_or_Legacy_mode](https://help.ubuntu.com/community/UEFI#Setup_the_BIOS_in_EFI_or_Legacy_mode)
3) rename the /efi folder which is in your sda1 partition into /efi_old
4) run Boot-Repair again and tell us the new URL
5) reboot and see if you can boot both Ubuntu and Windows. If not, tell us what you observe, you may need to create a /boot partition.

---

### Post by gerrman97 on 2012-10-23
i think someone else already asked this but, do u mind erasing and starting from scratch?

---

### Post by MDJPster on 2012-10-23
I have quite a bit of stuff to back up, but I don't really mind. I'll try the other idea before I go there though, since other than my 2TB disk I only have a 320GB, so I'll need to go buy a larger storage device to back it all up.

EDIT:

> **NikTh said:**
> So if you can create another partition in Ubuntu's installation then 
Boot from a LiveCD-USB 
Create a separate /boot partition ext4 = 500MB 
Mount it to /boot 
and then run again the boot-repair program with the option of separate /boot partition. (advanced).
I don't know if you have to move the old /boot partition to the new or  the boot-repair will perform these tasks for you, I never did that  before. We will see.
And something else , might be important 


So when I reduce sdb5 by 1GB and format that space to ext4, it names the new partition "New Partition #1" and in boot-repair the only option for "Separate /boot/efi partition" is sda1. For "OS to boot by default" my only options are "sdb5 (Ubuntu 12.10)" and "Windows (via sdb5 menu)".

Thanks

---

### Post by gerrman97 on 2012-10-23
maybe format, and start from scratch. i only know so mutch about ubuntu. i know a buttload about Windows 7, though.

---

### Post by oldfred on 2012-10-23
Having the Windows boot partition on a different drive with UEFI is something I have not seen. Not sure how you move that back, but I would expect you have to create a boot partition in the Windows drive and edit BCD with new partition info from Windows. Is that really part of the EFI boot of your Windows or left over from another install on that drive?

Then you can convert/totally reformat sdb as gpt partitioning for Ubuntu. And boot Ubuntu liveCD/USB in UEFI mode so it installs correctly.

UEFI dual boot two drives
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

It looks like Windows with UEFI does not have to the the WinRE,  which in BIOS is the boot/repair partition.
Windows Recommended UEFI-Based Disk-Partition Configurations
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Change the booting style of Windows Vista or 7 x86_64 versions from BIOS-MBR mode to UEFI-GPT mode without formatting or reinstalling
[https://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI](https://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI)
Windows installs the efi bootloader to (ESP)/EFI/Microsoft/Boot/ which is identical to (WINDOWS_SYSTEM_PART)/boot/microsoft/ incase of BIOS systems.
The dir mainly consists of bootmgfw.efi, bootmgr.efi, memtest.efi and 'bcd'.

---

### Post by NikTh on 2012-10-24
> **MDJPster said:**
> 
So when I reduce sdb5 by 1GB and format that space to ext4, it names the new partition "New Partition #1" and in boot-repair the only option for "Separate /boot/efi partition" is sda1. For "OS to boot by default" my only options are "sdb5 (Ubuntu 12.10)" and "Windows (via sdb5 menu)".

I don't want to messed up things. Follow the advises of **oldfred** (more experienced) and **YannBuntu** (the developer of boot-repair). Leave my advise for last. And of course do not abandon the effort and delete everything. This is the easy way , but solving your problem is the greatest way. 

Thanks

---

