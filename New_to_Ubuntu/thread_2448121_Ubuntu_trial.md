---
title: "Ubuntu trial"
date: 2020-08-02
forum: New to Ubuntu
---

### Post by aj34 on 2020-08-02
Please forgive my possible misuse of terminology as I'm a complete Ubuntu novice. Any terms I use that I'm unsure about, I've placed in inverted commas. I'm not particularly PC savvy either, having only ever used Microsoft operating systems in the past. Anyone kind enough to reply will *really* need to avoid jargon. Explanations will have to use layman's terms, otherwise it will mean nothing to me. Thanks for your understanding.

I would like to ditch my current operating system, the shameful debacle that is Windows 10, so I'm exploring alternative operating systems (I imagine this situation isn't uncommon). I have "installed" Ubuntu on a USB 3.0 flash memory stick and run it as a trial. So far, I'm impressed. Despite a steep learning curve, things are gradually falling into place - except a couple of areas on which I would greatly appreciate advice.

Firstly, changes to Ubuntu settings and Firefox "extensions" I made/added yesterday were gone when I logged in today. Is this because I'm using Ubuntu as a trial? I trust this wouldn't happen if I "installed" Ubuntu on my HDD as my only operating system?

Secondly, I can't seem to access my personal files that I know are on the PC's HDD. Again, is this just because it's a trial? I expect I could duplicate a few of these files onto the Ubuntu USB memory stick as a temporary measure just to get a feel for how Ubuntu handles files. Would that work out OK?

Thanks in anticipation.

---

### Post by Dennis N on 2020-08-02
> Firstly, changes to Ubuntu settings and Firefox "extensions" I made/added yesterday were gone when I logged in today. Is this because I'm using Ubuntu as a trial? I trust this wouldn't happen if I "installed" Ubuntu on my HDD as my only operating system?
Yes to both your questions.

---

### Post by crip720 on 2020-08-02
What you have installed on the USB is a 'live version installer' it will let you test out Ubuntu on your hardware but does not keep any changes until you install it to another drive.  From Win 8 on, windows uses what is called 'fast startup', this puts windows in a hibernation mode instead of shut down.  It should be turn off in windows for you to see your PC files from Ubuntu, also make sure it is turned off before installing Ubuntu.  Windows has a habit of turning it back on.  Before installing Ubuntu, google installing ubuntu with your computer make and model, should find some tips to make it easier.  Backup all important files before installing, oops happens to us at one time or another.  Backups are important, hopefully will not be needed.

---

### Post by Autodave on 2020-08-02
Normally, "fast start" is disabled by entering the BIOS.  Do you know how to do that?  If not, please give us the make and model of you PC.

---

### Post by aj34 on 2020-08-02
Thanks very much for your replies, folks. Most enlightening and I actually understood!

I have altered settings in the BIOS before so I'm comfortable with that. Just to check my understanding though: I need to disable 'fast start', which is somewhere within the BIOS settings. And this should allow me access to my personal files (on the HDD) when I "boot up" Ubuntu from the memory stick?

EDIT: Is 'fast start' specific to Windows?

---

### Post by oldfred on 2020-08-02
Do not confuse UEFI fast boot and Windows fast start up. 
Both should be off.

UEFI fast boot assumes no system changes. UEFI/BIOS then does not scan system to check what hardware systems you have and assumes it is all the same. Often then boot from UEFI is so quick to starting system, you have no time to press a key to get into UEFI or UEFI one time boot menu to boot flash drive. Cold boot from full power down usually works to have it do normal boot once.

Windows fast start up is a type of hibernation and sets the hibernation flag. The Linux NTFS driver will not normally mount any NTFS partitions with hibernation flag to prevent damage or lost files. When hibernation is restored in Windows and changes would be lost. You can often force a read only mount if required. Note that Windows updates often turn fast start up back on, so you may have to turn off again or regularly. Also grub only boots working Windows and if fast start up turned back on, grub will not boot it. With UEFI you then can boot from UEFI boot menu and turn fast start up off again.

---

### Post by SeijiSensei on 2020-08-02
You can create a bootable USB with "persistent" storage. Then if you store files or settings, they will be written to the persistent storage area on the USB.  See [https://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/](https://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/) for details.

---

### Post by pbear42 on 2020-08-02
> **SeijiSensei said:**
> You can create a bootable USB with "persistent" storage. Then if you store files or settings, they will be written to the persistent storage area on the USB.  See [https://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/](https://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/) for details.
FYI, there's an easier way to do this now.  In Windows, one should use [Rufus]("http://rufus.akeo.ie/") or [UUI]("https://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") (in Linux, mkUSB, as discussed in the article).  Persistence in Rufus only works for 19.10 and later, but obviously that includes 20.04.  Meanwhile, LiLi was last updated in 2015 and lacks configuration support for any current version of Ubuntu.

---

### Post by aj34 on 2020-08-03
Because I only want to understand how Ubuntu handles my personal files, whatever I do only needs to be a short term fix. Thanks for your replies. I didn't understand all recent respondents but I do understand:

I need to ensure UEFI fast boot and Windows fast start are disabled in order to view personal files on the HDD (and Windows may well enable 'fast start' at some point).
There is a way of creating 'persistent storage' on the Ubuntu USB memory stick.

My plan A is simply(?) to turn off the fast start and fast boot in the BIOS as I don't need to store personal files on the USB. I only need a brief look-see as to how Ubuntu handles my most common file types (documents, photos, video, spreadsheet).

Just had a thought though - I also want to see how Ubuntu will work with my QNAP NAS (i.e. 'upload' files - mainly music FLAC files - to NAS using Qsynch and interrogate the NAS). I'll get this file management side of things sorted first and may post back with a question regarding the NAS - if I need to. Thanks again for all your help - much appreciated.

---

### Post by Dennis N on 2020-08-03
> I only need a brief look-see as to how Ubuntu handles my most common file types (documents, photos, video, spreadsheet).
I think you will be pleasantly surprised.

Documents and Spreadsheets - LibreOffice is compatible with a wide range of document formats such as Microsoft Word (.doc, .docx), Excel (.xls, .xlsx), PowerPoint (.ppt, .pptx) and Publisher.

Audio. No problem. Same file formats are used by both. Files in many formats will be readable by the good Linux audio players like audacious. 
Photos. Should be no problem with the common file types.

Since you are not using Windows any longer, you will want to re-save your Documents and Spreadsheets in LibreOffice native formats.

---

### Post by sdsurfer on 2020-08-03
> **aj34 said:**
> Secondly, I can't seem to access my personal files that I know are on the PC's HDD.

One of the things I love about Linux/Ubuntu is it can read the Windows drive. Windows can't see the Ubuntu partitions, the inverse is not true. Have you ever, in Windows, gone to a directory/folder and clicked an icon with a little arrow and gotten "you do not have permissions?" This is a simple symbolic link, meaning it's a piece of data that takes you to some other directory/folder. I always found it annoying. When you access a Windows directory from Linux, it just follows the link because it's not "aware" of the Windows system permissions.

When I first started I wanted to be very sure not to nuke my Windows system (in retrospect I laugh at that now.) I bought a new larger drive, put it in as a second disk, then set up Ubuntu on it's own hard disk, leaving the Windows disk intact. You then set up Grub in a dual boot configuration to always boot to Ubuntu first, but can boot back into Windows if you ever need to. It's an approach a lot of people use instead of partitioning the existing drive for both. Do some searches for dual boot ubuntu windows, it's not that difficult.

Once configured like this, you will find your Windows drive and all files under "other locations" in the file manager.

---

### Post by C.S.Cameron on 2020-08-03
If you want to see exactly how Ubuntu will act on your computer, Drivers, Updates, Installed Programs, you can do a Full install to USB drive as you would to internal drive, see [https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step](https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step). Installing from image file per sudodus' instructions is the easiest way.

---

### Post by aj34 on 2020-08-05
> **Dennis N said:**
> 
Documents and Spreadsheets - LibreOffice is compatible with a wide range of document formats such as Microsoft Word (.doc, .docx), Excel (.xls, .xlsx), PowerPoint (.ppt, .pptx) and Publisher.

I've used OpenOffice in the distant past and can't remember why I switched back to an old version of Microsoft Word. More recently I had the latest version of Word on my PC that came free (a perk) but I found it kept pestering me to login to my Microsoft account and kept popping up with messages about new features, which I didn't appreciate. Also, I don't find recent Microsoft software intuitive to use or particularly logical. Windows 10 was the final straw (and this will be Microsoft's final OS? What a legacy! No amount of retrospective sticking plasters (updates) will turn this mess into a usable OS for me).

A few months back, I ditched Word and started using LibreOffice, recommended to me by a friend. I use only WP and spreadsheets and I like it. Ironically, LibreOffice can open an old Microsoft file extension (.wri) perfectly whereas neither the old or new versions of Word could do so without errors.

*[COLOR=#000000]"Since you are not using Windows any longer, you will want to re-save your Documents and Spreadsheets in LibreOffice native formats."[/COLOR]*[COLOR=#000000]

If I saved files in LibreOffice native formats, could I still convert file type and send those documents to other folk in Microsoft native formats?

I have a second HDD drive fitted in my PC which is not being used now so I could install Ubuntu on that. If I did so, I could set up BIOS to boot from HDD2 (don't know what is meant by 'Grub'?). Just to check my understanding, are you saying that Ubuntu could access my personal folders/files that would still be on HDD1 (along with Windows 10 OS) even though Ubuntu would be installed on HDD2? If so, That would save a lot of folder/file moving from HDD1 to HDD2 and associated ongoing synchronisation issues.

I'll check out the USB full install instructions although maybe using the (currently unused) second HDD to install Ubuntu might be preferable?

Thanks again for the useful advice and suggestions. Much appreciated.
[/COLOR]

---

### Post by CelticWarrior on 2020-08-06
> [COLOR=#000000]If I saved files in LibreOffice native formats, could I still convert file type and send those documents to other folk in Microsoft native formats?[/COLOR]


Yes! I suggest using the open formats for files intended to be used by you or anyone else with LO or other software supporting it but keep the Microsoft proprietary formats for those who don't. There's no pointy in making two conversions in this case. 

> [COLOR=#000000]I have a second HDD drive fitted in my PC which is not being used now so I could install Ubuntu on that. If I did so, I could set up BIOS to boot from HDD2 (don't know what is meant by 'Grub'?). Just to check my understanding, are you saying that Ubuntu could access my personal folders/files that would still be on HDD1 (along with Windows 10 OS) even though Ubuntu would be installed on HDD2? If so, That would save a lot of folder/file moving from HDD1 to HDD2 and associated ongoing synchronisation issues.[/COLOR]


This is a very common doubt/misunderstanding.
Where the system partition(s) reside doesn't matter as long as the system boots. Likewise, where data (personal files) reside doesn't matter as long as you have the correct permissions to open and modify them. Two or more different partitions in the same drive or in different drives doesn't matter. 

Now, for booting a dual-boot, a couple of things do matter. First of all you need to know whether the computer has BIOS (old) or UEFI (new, practically all from the last decade). The BIOS firmware "boots drives", specifically it boots a bootloader in the MBR (Master Boot Record). So, in your scenario because you have two distinct physical disks, you want to keep HDD1 with Windows unchanged and then install Ubuntu in the HDD2 and boot from it. Ubuntu's bootloader is GRUB, it boots Ubuntu and Windows if in dual-boot, something you can't do with Windows because its bootloader only boots other Windows. Many experts often suggest disconnecting the Windows drive while installing and reconnect when done, run a command to redetect OSes and then Windows should be added to the Grub's boot menu allowing the user to choose Ubuntu (default) or Windows. This certainly avoids inadvertently writing to the Windows partitions (or the consequence of making a wrong selection when installing Ubuntu) but isn't necessary. Just change the boot order in BIOS to the HDD2 - this setting will be kept - and the Ubuntu installer will write Grub in that drive only. Changing the boot order back to HDD1 results in booting Windows directly, this being the advantage of having the Windows drive unchanged. Otherwise, if you have only one drive or, with more than one, the boot order wasn't changed / Windows drive disconnected or disabled in BIOS, then the Ubuntu installer will install GRUB in the HDD1 thus replacing the Windows bootloader. This can be a problem later on if Ubuntu becomes corrupt or you decided to delete the Ubuntu system partition because then you'll need to boot from Windows installation media and reinstall the Windows bootloader (the MBR can have only one bootloader).

With UEFI everything is easier. Any preinstalled Windows 8 or newer is in a UEFI capable computer and in UEFI mode. This firmware boots bootloaders residing in the ESP (EFI System Partition), a small FAT32 partition typically at the beginning of the drive. It's always possible to boot each OS independently. Many experts often recommend duplicating the ESP to the other non-booting drives just in case. It can be a lifesaver when the drive containing the ESP fails or said partition becomes corrupt but isn't necessary. Only one ESP is required regardless of the amount of physical drives or OSes installed, all the bootloaders coexist in the ESP.

---

### Post by grahammechanical on 2020-08-07
This slide show will show you what screens you will see when installing Ubuntu

[https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

Regarding the playing of audio and video files you will find that you will need to install some codecs. They are not installed by default because some of them are not open source software and some users do not want non open source software on their computers.

So, in that slide show look at screen number 5. The third tick box is labelled "Install third party software for graphics and WiFi hardware and additional media formats. If you tick that box you will get a proprietary video driver for your graphic card and several video and audio codecs.

This will explain why things are not simple in this area of Linux.

[https://en.wikipedia.org/wiki/Ubuntu-restricted-extras](https://en.wikipedia.org/wiki/Ubuntu-restricted-extras)

The Ubuntu live session will not include these closed source, restricted codecs. We can install applications and codecs when using a live session but what is installed is lost when we close the live session.

Regards

---

### Post by kurt18947 on 2020-08-07
> **Autodave said:**
> Normally, "fast start" is disabled by entering the BIOS.  Do you know how to do that?  If not, please give us the make and model of you PC.

"Fast start" in BIOS and "fast start" in Windows are different as I understand it. "Fast start" in BIOS skips all or part of the Power On Self Test (POST), "Fast start" in windows is some sort of hybrid hibernation that Ubuntu sees as a corrupted NTFS file system.

---

