---
title: "Help Required to Restore Ubuntu Dual Boot Option"
date: 2020-04-17
forum: New to Ubuntu
---

### Post by ivatt1815 on 2020-04-17
[h=2][/h][COLOR=#000000][INDENT][COLOR=#333333][FONT=verdana]I am a Ubuntu novice having only got involved recently in an attempt to make x-plane 11 run quicker.

Whilst investigating some software the other day I annoyingly and mistakenly changed the Grub2 boot options for my PC so that my PC  boot at all, it just gave a grub error (can't remember what it said).[/FONT][/COLOR]

[COLOR=#333333][FONT=verdana]After some time I managed to get it back to the point where I can boot into W10 but my Ubuntu boot option (through Windows 10 MBR) doesn't exist or rather points to a non existent file.[/FONT][/COLOR]

[COLOR=#333333][FONT=verdana]EasyBCD shows the the boot options as below[/FONT][/COLOR]

[COLOR=#333333][FONT=verdana]There are a total of 2 entries listed in the bootloader.[/FONT][/COLOR]

[COLOR=#333333][FONT=verdana]Default: Windows 10[/FONT][/COLOR]
[COLOR=#333333][FONT=verdana]Timeout: 17 seconds[/FONT][/COLOR]
[COLOR=#333333][FONT=verdana]Boot Drive: D:\[/FONT][/COLOR]

[COLOR=#333333][FONT=verdana]Entry #1[/FONT][/COLOR]
[COLOR=#333333][FONT=verdana]Name: Windows 10[/FONT][/COLOR]
[COLOR=#333333][FONT=verdana]BCD ID: {current}[/FONT][/COLOR]
[COLOR=#333333][FONT=verdana]Drive: C:\[/FONT][/COLOR]
[COLOR=#333333][FONT=verdana]Bootloader Path: \WINDOWS\system32\winload.exe[/FONT][/COLOR]

[COLOR=#333333][FONT=verdana]Entry #2[/FONT][/COLOR]
[COLOR=#333333][FONT=verdana]Name: Grub 2 For Windows[/FONT][/COLOR]
[COLOR=#333333][FONT=verdana]BCD ID: {a0ffb549-1824-11e9-8ad8-8236e31b4d39}[/FONT][/COLOR]
[COLOR=#333333][FONT=verdana]Drive: C:\[/FONT][/COLOR]
[COLOR=#333333][FONT=verdana]Bootloader Path: \grub2\g2bootmgr\gnugrub.kernel.bios[/FONT][/COLOR]

[COLOR=#333333][FONT=verdana]Having messed things up yesterday I am loathe just to go blindly ahead in case I mess things up agaiin.[/FONT][/COLOR]

[COLOR=#333333][FONT=verdana]I would appreciate help in getting my Ubuntu boot option back.

[/FONT][/COLOR]I am due a hardware upgrade next week and intend to dual boot Ubuntu & W10 from the same SSD. [COLOR=#333333][FONT=verdana]I don't want to reinstall Ubuntu as I have it setup to use with x-plane 11 and it took some effort to get it working properly thanks to x-plane 11 Ubuntu users help.

[/FONT][/COLOR]At a least resort I need at least to be able to access Ubuntu as I believe there is a way to copy over the necessary files to the new install. I have a Ubuntu CD which I have used before to access Ubuntu without installing.

[U]I apologise in advance if I have posted this twice to different sections of the forum, it is a beginners error.
[/U]
[COLOR=#333333][FONT=verdana]Thanks[/FONT][/COLOR][/INDENT]
[/COLOR]

---

### Post by yancek on 2020-04-17
Is your windows 10 install a Legacy/MBR install?  Is Ubuntu also a Legacy/MBR install?  If you are not sure, boot the Ubuntu install usb and go to the boot repair site below and use the 2nd option to add the ppa to get boot repair.  After downloading it, run it as instructed on the site choosing NOT to do any repairs but select the Create BootInfo Summary option.  When it finishes, it will give you a link to post here and that should provide details so that someone should be able to help you.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

A default install of windows 10 will be UEFI.  According to the neosmart (EasyBCD) site, EasyBCD cannot boot non-windows systems UEFI.

[https://neosmart.net/wiki/easybcd/uefi/](https://neosmart.net/wiki/easybcd/uefi/)

---

### Post by ivatt1815 on 2020-04-17
Thanks yancek

This is the output from boot repair

[http://paste.ubuntu.com/p/pTRYghgpsS/](http://paste.ubuntu.com/p/pTRYghgpsS/)


Fingers crossed!!!

---

### Post by yancek on 2020-04-17
The Ubuntu Grub bootloader has some of the boot files on /dev/sda5 (where Ubuntu is installed) but for some reason, you have Grub boot code in the MBR of /dev/sdb.  One solution is to install Grub to the MBR of sda and boot both Ubuntu and windows with Grub. Another solution is to change the boot priority in the BIOS to boot /dev/sdb first as that has Grub in the MBR of the drive, hopefully point to the correct Grub system files. Your grub.cfg which shows the menu when you boot is shown as being on /dev/sda2 which is an ntfs partition and Grub files should never be on an ntfs partition.  Not sure how or why you did that?  There also appears to be a grub.cfg file on /dev/sda5 but that is not shown in the boot repair output

Line 465 of boot repair indicates windows was hibernated when you ran boot repair.  Is your windows system partition on the sda drive, the 1.8TB?

If you want to use EasyBCD to boot both then you need to go elsewhere as that is windows software and it is unlikely you will get much help here.

---

### Post by ivatt1815 on 2020-04-18
Thanks [COLOR=#ff0000]yancek[/COLOR]

I have read your reply and as I have said I am a real novice when it comes to Ubuntu, I only installed it because I was told it would make x-plane run faster with my somewhat aging ACER Veriton M2610 PC that I bought s/h five years ago, which it did.

When I installed Ubuntu the grub MBR was working fine, I had Ubuntu as first choice then W10. It was whilst playing around with ways I could change the boot order so that W10 was first ( I have some Windows only software that I use on a regular basis) that my problem started. I was looking at various bits of software that claimed to be able to do that and with one of them, can't remember which one now, I selected what I thought was a view option but which turned out to be replacing the grub MBR. After that I got an error a boot that the grub device couldn't be found. After several abortive attempts I managed to get back to where I am now, namely being able to boot into W10 but no access to Ubuntu.

You are correct in your assumptions that both W10 and Ubuntu were on the same drive,the 1.8TB sda, different partitions of course, together with all my other software.

Although ideally I can live with things at the moment, it would be helpful to get the grub MBR back to have the choice between W10 & Ubuntu, but I am not going to poke about blindly in case I make things worse. If you are able to give me precise instructions as to what to do I am happy to follow [COLOR=#ff0000]**verbatim**[/COLOR], safe in the knowledge that if all else fails I have somebody to fall back on (I have a laptop backup).

As stated on Thursday I am hoping to take delivery of a new PC and I plan to install a clean W10 on the ssd & also run Ubuntu on the same drive. When I switched to Ubuntu I had to get help from x-plane simmers who gave me the necessary rule changes needed for it to recognise my Saitek hardware and I am loathe to have to go through that process again so if there is a way of migrating the current Ubuntu to the new ssd that would be the perfect solution even if it means over writing a new Ubuntu install. At the very least if I could copy the rules I had to add to Ubuntu to make it compatible with x-plane 11 that would do.

Hope you can help further

Chris

---

### Post by oldfred on 2020-04-18
I do not believe in trying to copy an install to a new system.
Ubuntu is free and very easy to install.
All the user configuration files are in /home. Only if you edited some system wide configuration files may you want those from /etc. I edit grub files, and just copy those to a folder in /home so my backup of /home includes those.
Only if you installed server software or maybe your x-plane is in / and also should be backed up.
You also export a list of installed applications.

You have to assume at some time your hard drive will fail and then how do you recover. Having new system with old system still running is an ideal time to test that your backup & recovery fully works. You install & restore to new system, and if you forgot something in backup, you still have old system to go back to.

My backup includes this also. The dpkg list is a very long text list of all applications and the dependencies. 
If upgrading, you may want to edit it to remove obsolete, old kernels or others. It will not re-install anything already installed.
[https://help.ubuntu.com/community/ReinstallingSamePackages](https://help.ubuntu.com/community/ReinstallingSamePackages)
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)
Best practice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006)
[https://ubuntuforums.org/showthread.php?t=2368992&](https://ubuntuforums.org/showthread.php?t=2368992&) 
[https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)

---

### Post by ivatt1815 on 2020-04-19
Thanks [COLOR=#ff0000]oldfred[/COLOR] for the reply, as I am as stated a novice with Ubuntu I am going to have to read it carefully to see I understand. I take the point about not copying over an old ubuntu install to the new one. 
As I said I made several changes in the original Ubuntu Rules so that it would work OK with x-plane and I need to be ble to access these so I can restore them to the new install when done. I don't have any other software I need to be concerned about.
At the moment I can't access my original Ubuntu install because I have lost the dual boot option. I do have the Ubuntu install CD and can boot into the "[COLOR=#ff0000]Try Without Install[/COLOR]" option. Can I use that access to make a backup of the files I need for the rules, onto say a USB so I can restore to the new, if so how do I go about that.
It is easy enough to do a fresh install of x-plane and then copy over all my personal add-ons as the W10 and Ubuntu installs are the same.
I have seen various tutorial posted online about restoring the dual boot option but I am nervous of doing anything else in case I make the situation even worse i.e lose Windows 10 access.
I have checked my boot options and under Grub 2 For Windows it just goes to various Grub 2 options non of which give an opportunity to boot to my existing Ubuntu system. What I need is a simple way, if one exists, to add Ubuntu to my Windows MBR so I can boot to Ubuntu. I haven't as yet found any utility/software that seems to identify bootable OS on the drive and add them to a boot menu. If I can't access Ubuntu I can't restore my user info if I need to which I forgot to make a note of.
Apologies for being a bit dim but at 80 years old it takes a long time to take things in, especially after so many years using Windows only.

---

### Post by oldfred on 2020-04-19
BIOS boots from the MBR you specify.
But with multiple drives you want to keep a Windows boot loader in the MBR of the Windows drive and have grub installed in the MBR of one of your other drives. Then you can multiple boot from grub. And when Windows needs repairs, you can directly boot it from BIOS choosing Windows drive. Or if mostly Windows set Windows as default and only use BIOS selection to boot Ubuntu. 

Note that if Windows 10 it uses fast start up which is just hibernation. And grub will not boot hibernated Windows. And Windows will keep turning that on with some updates.
But grub only boots working Windows and Windows will not boot Ubuntu. There are some third party BIOS tools but I will not recommend any of them.

If you reinstall Ubuntu, with multiple drives you should always use the something else install option. I prefer to partition in advance, but you can add partitions during the Something Else install option. And at bottom of the Something Else partition screen is a combo box on which drive to install grub into. Just do not choose your Windows drive. 
Note with UEFI installs that combo box does not work.

And you normally want to install Ubuntu in same boot mode as Windows. Old systems before 2012 were BIOS, but newer systems are UEFI. Microsoft has required vendors to install Windows in UEFI boot mode since Windows 8 released in 2012.
Both Windows & Ubuntu install in boot mode that you boot install media, so newer systems need to be booted in UEFI. If your system is older then that does not matter.

But it looks like you booted Ubuntu installer in UEFI boot mode to run Boot-Repair, so your system is not that old.

If at some point you may reinstall Windows in UEFI boot mode, you may want to configure a new drive for gpt partitioning with both a bios_grub 1MB unformatted with bios_grub flag and with ESP - efi system partition, FAT32 with esp/boot flags. Then your install will use one or the other and only reinstalling grub will convert the install from BIOS to UEFI. Otherwise if MBR partitioned and later you want to convert drive, with either this system or new one, you normally erase drive & convert to gpt. There are some tools to convert, but better then to start over. 
I started converting drives to gpt in 2010, so all my drives are gpt, but I do not have any BIOS boot MBR Windows since I shutdown XP in 2011.

---

