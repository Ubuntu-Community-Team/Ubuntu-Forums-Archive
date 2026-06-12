---
title: "Grub rescue problem"
date: 2016-10-20
forum: New to Ubuntu
---

### Post by andreas73 on 2016-10-20
Goodmorning, yesterday afternoon I tried to install Ubuntu 16.04 on an old partition where was installed ubuntu 14.10.
I followed a tutorial and don't think I made mistakes in formatting the partition in ext4 and with "/" in the other option.
However during the installation there was a problem with the grub and it stopped installing with a message of error.
Now when I turn on the pc I have the message of grub rescue.

I tried a lot of guide to resolve the problem, using the ubuntu live version terminal and also the windows promt in the grub rescue option.

I tried to follow this
[https://ubuntuforums.org/showthread.php?t=2223856&page=3](https://ubuntuforums.org/showthread.php?t=2223856&page=3)
That seems to be very similar to my problem, but following this procedure I have error when trying to mount the EFI partition

Sorry if my english is not perfect, I'm from Italy. As you may see, I'm not an expert user of Linux.
Please help me, at the moment I'm without pc, thank you

---

### Post by colmax on 2016-10-20
Goodmorning yesterday is so cool :)
If you format from ./ everything is gone
Seems install is the go
/ is root directory so it can wipe out all your mounted drives & itself-so to speek
not a good idea
Your english is freaking excellent
Wish i was that good with other lingoes
Cheers

---

### Post by andreas73 on 2016-10-20
I have photos shooted during the installation of my choices and the error in installation, but all in italian, I don't know if they're useful
[http://i.imgur.com/EsMBfFB.jpg](http://i.imgur.com/EsMBfFB.jpg)
[http://i.imgur.com/EGzpCOc.jpg](http://i.imgur.com/EGzpCOc.jpg)

In this second image: 
"Couldn't do GRUB installation
The installation of the packet grub-efi-amd64-signed in /target/ not done. Without the bootloader GRUB, the installed OS won't run"
And under this you can see the installation blocked while installing grub2

But the guide i followed said exactly to double click on the partition on wich I want to install ubuntu and give that option :/
So what should I do?

Pa: thank you for help and compliment :)

---

### Post by alexeyn on 2016-10-20
i think you need to format 100mb part  as 0xeE
run gnome-disks ,Edit partition ,top type

---

### Post by andreas73 on 2016-10-20
> **alexeyn said:**
> i think you need to format 100mb part  as 0xeE
run gnome-disks ,Edit partition ,top type

I don't know how to do that. And after that, what should I do? I have to proceed as in the guide that I linked?

---

### Post by alexeyn on 2016-10-20
yea.
simple advice is :
boot usb and install with "wipe out".
[https://ubuntuforums.org/showthread.php?t=2225043](https://ubuntuforums.org/showthread.php?t=2225043)

---

### Post by yancek on 2016-10-20
The first image you posted indicates you have several windows partitions.  Does that mean you have a windows OS installed and if so, which one and is it EFI?  
Selecting sda5 with a mount point of / and formatting that partition would be correct.  

I think your next best step is to get the boot repair software from the link below, download and burn it to a CD and run it selecting the option to Create BootInfo Summary and post a link to the output here.  That will provide enough information for someone to make a usefull suggestion.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by oldrocker99 on 2016-10-20
As far as GRUB not installing, I've had the same problem, which I solved by using a DVD instead of a USB drive. I don't know what the problem is, but I did verify the USB before installation, and still got (6 times in a row!) the GRUB error.

Try burning a DVD and see if that works.

---

### Post by oldfred on 2016-10-20
It looks like you have BIOS/MBR installs.
And Windows only boots in BIOS mode from MBR.
And Windows only boots in UEFI mode from gpt, but that would be a totally new install.

UEFI's standard is gpt partitioning and then grub is installed into the ESP - efi system partition. 
But with BIOS there is not normally an ESP, although such a thing is possible as installer is usually MBR, but can be booted in either UEFI or BIOS.

And the only way to choose which way you install UEFI or BIOS is how you boot install media for both Windows & Ubuntu. So always choose to boot in same boot mode for all systems & all installs. 

With new UEFI hardware you get both boot options.
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You do not have to totally reinstall, but that may be easier.
Boot-Repair can convert a UEFI install to BIOS or vice-versa, by uninstalling grub and reinstalling grub in correct version for either UEFI or BIOS boot.
       [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by andreas73 on 2016-10-20
> **yancek said:**
> The first image you posted indicates you have several windows partitions.  Does that mean you have a windows OS installed and if so, which one and is it EFI?  
Selecting sda5 with a mount point of / and formatting that partition would be correct.  

I think your next best step is to get the boot repair software from the link below, download and burn it to a CD and run it selecting the option to Create BootInfo Summary and post a link to the output here.  That will provide enough information for someone to make a usefull suggestion.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Yes, sorry, I forgot to say it because in my heas was obvius, I have Win10 in another partition, and I suppose it's EFI.
Is the same if I tho the thing with boot repair from the live on my usb?

> **oldfred said:**
> It looks like you have BIOS/MBR installs.
And Windows only boots in BIOS mode from MBR.
And Windows only boots in UEFI mode from gpt, but that would be a totally new install.

UEFI's standard is gpt partitioning and then grub is installed into the ESP - efi system partition. 
But with BIOS there is not normally an ESP, although such a thing is possible as installer is usually MBR, but can be booted in either UEFI or BIOS.

And the only way to choose which way you install UEFI or BIOS is how you boot install media for both Windows & Ubuntu. So always choose to boot in same boot mode for all systems & all installs. 

With new UEFI hardware you get both boot options.
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You do not have to totally reinstall, but that may be easier.
Boot-Repair can convert a UEFI install to BIOS or vice-versa, by uninstalling grub and reinstalling grub in correct version for either UEFI or BIOS boot.
       [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Sorry but I can't understand exactly what you want me to do. What I have to install? And I'm not sure I understood wich screen I have to post, I hope are this two

[http://i.imgur.com/HavO7Td.jpg](http://i.imgur.com/HavO7Td.jpg)
[http://i.imgur.com/uQLQkf4.jpg](http://i.imgur.com/uQLQkf4.jpg)

---

### Post by oldfred on 2016-10-20
If you get grub menu, you are booting in UEFI boot mode.
If drive is MBR(msdos) then Windows is in BIOS mode.
Screenshot did not show any of the normal Windows extra partitions it has with UEFI, so I assume BIOS/MBR.

You can confirm, just by running this. If dos or msdos then BIOS, if gpt then UEFI.
sudo parted -l

---

### Post by andreas73 on 2016-10-20
> **oldfred said:**
> If you get grub menu, you are booting in UEFI boot mode.
If drive is MBR(msdos) then Windows is in BIOS mode.
Screenshot did not show any of the normal Windows extra partitions it has with UEFI, so I assume BIOS/MBR.

You can confirm, just by running this. If dos or msdos then BIOS, if gpt then UEFI.
sudo parted -l

[IMG]http://i.imgur.com/HyekIZc.jpg[/IMG]

---

### Post by QIII on 2016-10-20
andreas73 --

Rather than posting an image, would you please copy the output of the terminal and paste it between code tags?

Also, there is no need to quote oldfred's post in your response.  

Thanks.

---

### Post by oldfred on 2016-10-20
Please attach screen shots. Easy to do with Forum's advanced editor and paperclip icon.
But terminal or text should just be copied & pasted. And again if longer use advanced editor and # icon to add code tags.

You have BIOS/MBR. So always boot live installer in BIOS mode.
If you force an UEFI install, you may convert drive to gpt partitioning, and then Windows will never work again.

---

### Post by alexeyn on 2016-10-20
and why bootloader at photo tries to deploy in efi style

---

### Post by oldfred on 2016-10-20
Not sure what photo you are asking about.
But if you boot installer in UEFI mode it will install grub to ESP - efi system partition. And of course if that does not exist, it errors out. 
You need to boot installer or repair disk in BIOS mode, so it installs grub to MBR of drive for BIOS boot.

---

### Post by alexeyn on 2016-10-20
Did you check his screens If you dont know which one, I dont wanna  explain it to you

---

### Post by QIII on 2016-10-21
alexeyn --

Your last post is exceptionally confusing.  Would you explain what you mean?

---

### Post by colmax on 2016-10-21
Screen says bios cos of extended & logical partitions-no efi unless bios is running in legacy mode (bios supports 4 primary partitions & efi supports 128)
Figure mod was just covering all angles
Just a little harsh Alexeyn
Cheers

---

### Post by andreas73 on 2016-10-21
Maybe this could help you:
When I run boot repair and I run the recommended repair, it gives me the code

```
sudo chroot "/mnt/boot-sav/sda5" dpkg --configure -a
sudo chroot "/mnt/boot-sav/sda5" apt-get install -fy
sudo chroot "/mnt/boot-sav/sda5" apt-get purge -y --force-yes grub*-common grub-common:i386 shim-signed linux-signed*
```

to copy-paste on a terminal, and this is the output of the terminal

```
ubuntu@ubuntu:~$ sudo chroot "/mnt/boot-sav/sda5" dpkg --configure -a
Setting up shim-signed (1.17~16.04.1+0.8-0ubuntu2) ...
Installing for x86_64-efi platform.
grub-install: error: cannot find EFI directory.
dpkg: error processing package shim-signed (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up grub-efi-amd64-signed (1.66.1+2.02~beta2-36ubuntu3.1) ...
Installing for x86_64-efi platform.
grub-install: error: cannot find EFI directory.
dpkg: error processing package grub-efi-amd64-signed (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 shim-signed
 grub-efi-amd64-signed
ubuntu@ubuntu:~$ sudo chroot "/mnt/boot-sav/sda5" apt-get install -fy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 246 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up grub-efi-amd64-signed (1.66.1+2.02~beta2-36ubuntu3.1) ...
Installing for x86_64-efi platform.
grub-install: error: cannot find EFI directory.
dpkg: error processing package grub-efi-amd64-signed (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up shim-signed (1.17~16.04.1+0.8-0ubuntu2) ...
Installing for x86_64-efi platform.
grub-install: error: cannot find EFI directory.
dpkg: error processing package shim-signed (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 grub-efi-amd64-signed
 shim-signed
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by alexeyn on 2016-10-21
[IMG]http://i.imgur.com/EGzpCOc.jpg[/IMG]so we have crowd effect exqmple.

---

### Post by oldfred on 2016-10-21
Please see posts #13 & 14. Link to even more info:
       If you use the advanced editor, you can use the paperclip icon to attach screenshots. Post #4 1024x768 if photo
[http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

You have BIOS installs. But keep trying to install grub in UEFI/efi boot mode which will not work as it is telling you.
Boot installer in BIOS mode, as shown in previous links and install BIOS based grub to MBR of sda, not to a partition.


 [https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System) 
And if you want Windows to directly boot which you may occasionally need, you can use your Windows repair disk.

 How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

### Post by alexeyn on 2016-10-21
104mb partition is part(remains of?) of  efi install.

---

### Post by oldfred on 2016-10-21
You show no FAT32 partitions which is required for UEFI.
Your 100MB NTFS boot partition is a standard Windows BIOS boot partition. All Windows BIOS installs after XP separate the boot files into a separate partition for standard installs. Boot partition is not required, but with standard installs boot files are only in that partition.

       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

---

### Post by andreas73 on 2016-10-21
I use this solution
> How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/Re...ta/7Bootloader]("https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader")

and in particular I use from the terminal these commands:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

and now the PC goes directly on Windows, without dual boot, but at least it turns on and I can use it. Now, if I want to install Ubuntu 16,04?
The partition are still there, as you can see from this picture
[http://imgur.com/a/EhLjw](http://imgur.com/a/EhLjw)

Thanks a lot for helping me! :D

---

### Post by oldfred on 2016-10-21
From Ubuntu live installer you can follow directions in other link.

You can use Boot-Repair which for many since GUI is easier.

But you can manually repair from Ubuntu flash drive by mounting partition and installing grub.

Change example from sda5 to correct partition.
 #Comments are anything after the #, enter commands in terminal session
#Install MBR from liveCD/DVD/USB, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

---

### Post by andreas73 on 2016-10-22
I've uses these commands
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
sudo grub-install --boot-directory=/mnt/boot /dev/sda
```

 then I rebooted without the live usb of Ubuntu and this is what I obtained

[http://i.imgur.com/CeC5WdD.jpg](http://i.imgur.com/CeC5WdD.jpg)

(I'm sure that sda5 is the partition of Linux and the installation returned no error)

NEW:

Using boot-repair it worked, now turning on the pc I have the purple screen for choosing the OS, but there is only ubuntu. However Ubuntu seems to work perfectly. What to do to for windows?

---

### Post by alexeyn on 2016-10-22
```
sudo grub-mkconfig -o ////mnt/boot/grub/grub.cfg
```
that goes before

---

### Post by oldfred on 2016-10-22
That is the same as this which should find Windows.
sudo update-grub

But Windows must be in working order which includes no hibernation nor needing chkdsk.
And Windows 8 or later uses fast start up or always on hibernation.

---

### Post by andreas73 on 2016-10-22
Now I tried to turn on the pc to try what you suggestes and after the purple screen where I chose Ubuntu I obtained this screen

[https://imgur.com/VduJf4a](https://imgur.com/VduJf4a)

But after it went in stand by, it asked me for the password in a strange flashing white window. Maybe a driver problem? Or when the installation of Ubuntu crashed for the grub error, it left some problem?

---

### Post by oldfred on 2016-10-22
Did you get grub menu? Were you choosing Ubuntu or Windows from grub?
What video card/chip?

---

### Post by andreas73 on 2016-10-23
Yes, I got the grub menu. The video card is nvidia 720m

---

### Post by oldfred on 2016-10-23
Are you using nomodeset until you install the proprietary nVidia driver from Ubuntu's repository?
Can you boot recovery mode, in grub menu advanced options sub-menu.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[URL="https://wiki.ubuntu.com/Kernel/KernelBootParameters"]https://wiki.ubuntu.com/Kernel/KernelBootParameters

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[/URL]

---

### Post by andreas73 on 2016-10-23
I tried to change quiet splash into nomodeset but nothing changed :(

---

### Post by alexeyn on 2016-10-23
turn uefi in bios ,install linux with partition system wiped out,and gpt formatted one deployed,also windows place partition,and 104mb efi partition.

---

### Post by oldfred on 2016-10-23
Did you try recovery mode?

---

### Post by andreas73 on 2016-10-24
This is my recovery mode:

[https://imgur.com/1vTbxOd](https://imgur.com/1vTbxOd)

If you want I can traslate

---

### Post by oldfred on 2016-10-24
Choose the network on option and then the terminal.

       # should show newest versions available in addition
ubuntu-drivers devices 

If you have installed any nVidia drivers, you must purge everything related first. If not and not the very newest nVidia card.
      
 If you just want default version - recommended one
sudo ubuntu-drivers autoinstall
Or you manually choose any in list.
sudo apt-get install nvidia-XXX  

 #What is installed
dpkg -l | grep -i nvidia
dkms status
lsmod | grep nvidia 

If you have installed any version, you must purge first, old will conflict with new as new install does not overwrite old version.
sudo apt-get remove --purge nvidia-*
This may not exist, so if error that would be ok
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 
sudo apt-get remove --purge nvidia-* 

If you want the very newest driver or have a 10x0 version new card.
# Shows standard repository versions
ubuntu-drivers devices
sudo apt-add-repository ppa:graphics-drivers/ppa
# should show newest versions available in addition
ubuntu-drivers devices
#Then install as above either auto or select specific one.

---

### Post by andreas73 on 2016-10-26
This is the result when I ask for my drivers
[https://imgur.com/Cou366P](https://imgur.com/Cou366P)

But then whatever I digit it gives me the message:
"dpkg has been interrupted. It's necessary to execute "sudo dpkg --configure -a" to resolve the problem"
But if I execute the command it confige a lot of things and at a certain point it stopped and I can't do anything.
This is the second time I try and now it stopped on the message
"[ OK ] started braille device support"

---

### Post by oldfred on 2016-10-26
What is the error?

Do you have other ppa enabled?
Or corruption in sources?
 cat -n /etc/apt/sources.list 

System needs to be up to date.

 sudo apt-get update
sudo apt-get upgrade
apt-get autoremove

---

### Post by andreas73 on 2016-10-26
There is no error message, it gives only that message. Now I tried to update, and after some time of updating, before finishing it gave me that message of dpkg again.
Can't I just format this partition and reinstall from the beginning? I don't know if it make sense, I'm just asking

---

### Post by oldfred on 2016-10-26
Total new install is the nuclear option. 
Do you have good backups, or is it a brand new install?

If re-installing only use the Something Else install option and choose the same / partition for your new / partition.

---

### Post by andreas73 on 2016-10-27
It gave me again the same error :(

[https://imgur.com/lfYD4Q1](https://imgur.com/lfYD4Q1)

I again restored Windows from the live version using the "lilo" commands. 
What can I do to solve? I've been unable to use my pc for a week :(

---

### Post by oldfred on 2016-10-27
What brand/model system?

If you restored Windows booting with Lilo that is BIOS. But your error message is from UEFI.
You need to install Ubuntu in same boot mode as Windows.

Add this to live installer and run report:
 May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by andreas73 on 2016-10-27
How do I install in BIOS mode?
This is my boot info link:
[http://paste2.org/LWVtG0e1](http://paste2.org/LWVtG0e1)

---

### Post by oldfred on 2016-10-27
You have Windows 8 or 10 with the fast start up option enabled which is always on hibernation.
You must turn that off.
 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold) 


> The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.

Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount -t ntfs-3g -o remove_hiberfile /dev/sda1 /mnt/boot-sav/sda1



You have BIOS/MBR installs. If hardware is newer you may be able to boot in UEFI mode, but do not want to. UEFI will offer two boot options.
How you boot install or repair media, UEFI or BIOS is then how it installs.
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Best to reboot in BIOS mode, after turning off fast start up in Windows and run Boot-Repair's auto fix.

But since BIOS, only one system can have its boot code in MBR.
Grub will only boot Working Windows, but Windows updates or even corruption will prevent grub from booting it.
Then you can restore Windows boot loader, but that only may give you a chance to use f8 to get into the internal repair console.
Best to have a separate flash drive with Windows repair/recovery tools.
       
 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

### Post by andreas73 on 2016-10-28
I turned off the fast start up option but I really didn't understood what should I do now, sorry. Could you be more clear?

---

### Post by oldfred on 2016-10-28
Did you make Windows repair flash drive or have installer on separate flash drive that has repair mode?

Boot into Ubuntu installer & add Boot-Repair, but be sure to boot in BIOS mode not UEFI.
UEFI boot menu should give two boot options, one UEFI:name and the other name (BIOS) where name is label or brand of flash drive.

Then run Boot-Repair's suggested fixes.
If still issues post new run of Summary Report.

---

### Post by andreas73 on 2016-10-30
[https://imgur.com/a/CVZVw](https://imgur.com/a/CVZVw)

I cannot boot in UEFI mode. 

Sorry but this weekend I had a lot of things to do

---

### Post by oldfred on 2016-10-31
Why do you want to boot in UEFI mode? You installs are all BIOS/MBR.
You would have to totally erase & reinstall both Windows & Ubuntu in UEFI mode, it that is what you really want.
Both Windows & Ubuntu need to be installed in same boot mode either both BIOS as you have or both UEFI.

Did you run Boot-Repair's fixes?

---

### Post by andreas73 on 2016-11-01
But how can I be sure to boot ubuntu installer in BIOS mode?

---

### Post by oldfred on 2016-11-01
That is totally controlled by you.
In your UEFI/BIOS boot menu should be two entries. One is usually clearly UEFI as "UEFI:name" and the other just "name" (BIOS) where name is brand, label or type of flash drive.

You must also have UEFI Secure boot off as BIOS is a non-secure boot option. 
You may still have to turn on boot from USB settings in UEFI/BIOS and/or CSM/BIOS/Legacy boot option(s), or UEFI off.

Attached is one example, but every UEFI is different.

---

### Post by andreas73 on 2016-11-02
[http://i.imgur.com/pLD9zTj.jpg](http://i.imgur.com/pLD9zTj.jpg) 
[http://i.imgur.com/in6C0bp.jpg](http://i.imgur.com/in6C0bp.jpg)

I thought it may be one of these option. 
This is all I got in my boot options:

[http://i.imgur.com/UvtSR0r.jpg](http://i.imgur.com/UvtSR0r.jpg)

---

### Post by oldfred on 2016-11-02
Some systems (Dell?) seem to need to have CSM enabled but can still boot in UEFI mode.
Most systems it is either CSM on/off or UEFI on/off that then determines boot mode.

What do you get with CSM off/not enabled?

---

### Post by andreas73 on 2016-11-04
How can I disable CSM?

---

### Post by oldfred on 2016-11-04
That is an UEFI setting. But UEFI varies a lot.
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

Some just have UEFI on/off.
All will not show CSM when Secure boot is on, as that is not a Secure Boot option.
Some have separate CSM on/off. And it may be called Legacy or BIOS mode.

---

### Post by andreas73 on 2016-11-05
In the firsr image I posted some message before there is a lefacy option. May be this? Open that photo and read on the right

---

### Post by oldfred on 2016-11-05
You may just have to experiment with settings.
With one of my motherboards, I could only get it to boot flash drive in UEFI mode with UEFI only setting. UEFI & CSM did not work. 

You can see which mode you booted. If grub menu then UEFI.
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You can create UEFI only boot installer also.
 If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)

---

### Post by andreas73 on 2016-11-07
[https://imgur.com/Jgq1qgx](https://imgur.com/Jgq1qgx)
These are my boot option with all "disable" and the usb key with the live Ubuntu in

---

### Post by oldfred on 2016-11-07
You show a UEFI boot entry for flash drive.

---

### Post by andreas73 on 2016-11-07
I see, so?

---

### Post by oldfred on 2016-11-07
So what is issue, now? I thought you could not boot live installer in UEFI mode?

---

### Post by andreas73 on 2016-11-07
I thought I need it to boot in BIOS mode. So do I try again to install ubuntu?

---

### Post by oldfred on 2016-11-07
Then change to enable CSM and see if you get another entry for CSM/BIOS/Legacy boot.

---

### Post by andreas73 on 2016-11-08
[https://imgur.com/uWgBodS](https://imgur.com/uWgBodS)
Nope... :(

---

### Post by oldfred on 2016-11-08
On one of your other UEFI/BIOS screens do you have Secure Boot?
Or a setting to enable USB ports or setting to enable boot from USB ports?

Have you updated to newest UEFI from your vendor for your model system?

---

### Post by andreas73 on 2016-11-08
[http://i.imgur.com/c33q7uR.jpg](http://i.imgur.com/c33q7uR.jpg)
Here is secure boot

I found this for usb options in "advanced":
[http://i.imgur.com/bwDr4ea.jpg](http://i.imgur.com/bwDr4ea.jpg)

---

### Post by oldfred on 2016-11-08
Was Legacy USB support enabled before, as that looks like it would prevent BIOS boot.

---

### Post by andreas73 on 2016-11-08
I put that to 'disable' and now the usb option disappeared

---

### Post by oldfred on 2016-11-08
It has to be enabled for USB to work at all.

---

