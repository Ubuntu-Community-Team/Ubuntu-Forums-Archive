---
title: "Live USB Ubuntu 20.04"
date: 2020-07-18
forum: New to Ubuntu
---

### Post by linuxnewby3 on 2020-07-18
Hi world,

I have some troubles making a working live USB with Ubuntu.
My question is: If the live USB is done and i want to run that USB with Ubuntu on a Windows laptop/desktop, Does it have to be in Legacy mode to boot ?

I have been trying to figure this out for a couple of weeks now, as you can tell by the name i'm new in the world of Linux. 
I have tried a method with Rufus before but this time i followed a video from a youtube channel: Gary explains. 
I installed virtualbox on my desktop and installed Ubuntu on my USB using the virtualbox. After that i tried to run it on my laptop wich brings me to: Grub. (to be honest, not sure how that works or what is really is)
I've read online somewhere that i have to change my settings in the BIOS to legacy mode. So i've tried it and that works. But i don't want to switch my BIOS settings everytime i want to boot to Linux or when i want Windows. 
Also i can't even find an option to boot in Legacy mode on my desktop. And i want a portable Live USB so i can use it with 3 different computers that i have.

Hopefully anyone has some ideas how to fix this.

Regards,
Linuxnewby3

---

### Post by sudodus on 2020-07-18
**A USB drive with Ubuntu** is a 'live drive', and if you installed it with Rufus in Windows, or cloned it with 'any cloning tool' in Linux, for example the Ubuntu Startup Disk Creator, it **will be bootable bith in UEFI mode and BIOS mode** (alias CSM alias legacy mode).

It is a good idea to 'try' Ubuntu this way - boot from a USB drive and get a feeling of how it works.If you like it, the next step might be to install Ubuntu into the internal drive. You can do this alongside Windows, and, at boot time, decide which operationg system to boot, Ubuntu or Windows.

This is different from running Ubuntu in a virtual machine (via VirtualBox) because it runs the computer directly instead of via Windows and a program, that emulates a computer.

The following links may help you get started,

[help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](https://ubuntuforums.org/showthread.php?t=2230389)

[help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb)

---

### Post by linuxnewby3 on 2020-07-18
Hi sudodus, 

I have tried it, and i think it's very usefull to run it from my USB. 
At the moment i'm not really looking to convert 1 of my computers to a dedicated Linux based system.
So that's why i'm trying to figure out how to install Ubuntu to a USB-stick with the option to ad programs and save files. (it has 128gb, that will be enough for my use)
And the problem is that in the way i've tried i can only run Ubuntu when my system is in Legacy mode. and how to make the USB so any pc can read it.

If you can help me, i would really appreciated.

regards,
linuxnewby3

---

### Post by GhX6GZMB on 2020-07-18
Making a bootable USB-stick seems to carry a lot of issues. Never tried is myself, so I'm not certain where the problem is.
If your laptop has a DVD drive, the surefire way of doing a Ubuntu live boot is simply burning the .iso image to a DVD and booting from that. I've never had an issue there. It's slower, but at least you'll get a feeling for what you can do with a live boot.

The only thing you have to be sure of is that your DVD/CD drive (or your USB drive) is set as "first" in the boot sequence of your BIOS.

PS: I've been irritated for some time over why users new to (x)ubuntu have problems with USB-sticks. I'll try it myself tonight.

---

### Post by sudodus on 2020-07-18
> **linuxnewby3 said:**
> ...
So that's why i'm trying to figure out how to install Ubuntu to a USB-stick with the option to ad programs and save files. (it has 128gb, that will be enough for my use)
...

It might be a good alternative for you to use two USB drives, the stick with 128 GB, and another one, that could be 'anything', even a small 4 GB stick.

- Clone from the Ubuntu iso file to the small (4GB?) stick (a live drive).

- [Extract and] clone from a [compressed image file](https://phillw.net/isos/linux-tools/uefi-n-bios/dd_unb_ubuntu-20.04_15GB_2020-06-26.img.xz) to an installed Ubuntu 20.04 LTS system into the 128 GB stick.

- Boot into the  small (4GB?) drive, start **gparted** and grow (expand) the main partition so that it will use the whole 128 GB stick.

- Now you should have an installed system in your 128 GB stick. It is portable between PC computers with 64-bit processors and it can boot both in UEFI and BIOS mode.

**See [this link and links from it](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS).**

---

### Post by sudodus on 2020-07-18
> **ml9104 said:**
> Making a bootable USB-stick seems to carry a lot of issues. Never tried is myself, so I'm not certain where the problem is.
If your laptop has a DVD drive, the surefire way of doing a Ubuntu live boot is simply burning the .iso image to a DVD and booting from that. I've never had an issue there. It's slower, but at least you'll get a feeling for what you can do with a live boot.

The only thing you have to be sure of is that your DVD/CD drive (or your USB drive) is set as "first" in the boot sequence of your BIOS.

This is a crucial point, because many (most?) new computers lack an optical drive.
> 
PS: I've been irritated for some time over why users new to (x)ubuntu have problems with USB-sticks. I'll try it myself tonight.

- Pete Batard has spent a lot of time and effort to create [Rufus](https://rufus.ie) that works in Windows, and

- I have spent a lot of time and effort to create [mkusb](https://help.ubuntu.com/community/mkusb) that works in Ubuntu, debian and some other linux distros (also ToriOS).

in order to make it easier (and less risky to destroy valuable data) for people who want to try and install Ubuntu and other linux distros.

[hr][/hr]
Edit: But in order to create a live USB drive with Xubuntu (and the other Ubuntu family flavours), you can also use the built-in tool of the Ubuntu family, the Ubuntu Startup Disk Creator. It is simple to use and quite reliable.

---

### Post by GhX6GZMB on 2020-07-18
OK, just tried it myself.
I already have a working Lubuntu installation and have never had problems. It's installed using a DVD with a normal burned .iso image.

I just made a USB-stick with a Lubuntu .iso image using Rufus on a Win10 PC.

It makes a basic boot, I can select language and keyboard using F2/F3, but after selecting "Start Lubuntu" nothing more happens.
Rerunning Rufus and choosing NTFS (FAT32 is default) as file system for the stick, I get some errors during basic boot, but still arrive at the same menu. Pressing "Start Lubuntu": same thing, the install hangs.

Don't ask, yes I changed the boot sequence in the BIOS (otherwise it wouldn't even get to the first screen).

I can understand the major frustration of new users here, it's not acceptable.

My personal recommendation at this point: forget Rufus and USB-sticks, install from an old-fashioned DVD instead. If you don't have one, borrow an external DVD drive somewhere.

This was really sobering.

---

### Post by sudodus on 2020-07-18
@ml9104,

Which version of Lubuntu did you try (20.04 LTS)?

- Try Rufus in 'dd-mode', which means that is uses the reliable cloning method.

- You can also try the Startup Disk Creator in Lubuntu (since 16.04 LTS it is using the reliable cloning method).

I would expect that you succeed with the cloning method unless you have some special hardware, for example graphics chip, that needs a proprietary hardware driver.

Edit: Just to be sure: Did you check with md5sum that the download of the iso file was successful?

---

### Post by GhX6GZMB on 2020-07-18
> **sudodus said:**
> @ml9104,

Which version of Lubuntu did you try (20.04 LTS)?

- Try Rufus in 'dd-mode', which means that is uses the reliable cloning method.

- You can also try the Startup Disk Creator in Lubuntu (since 16.04 LTS it is using the reliable cloning method).

I would expect that you succeed with the cloning method unless you have some special hardware, for example graphics chip, that needs a proprietary hardware driver.

Edit: Just to be sure: Did you check with md5sum that the download of the iso file was successful?

As per my signature: Lubuntu 20.04LTS

Just to be clear: _I'm not the one having problems_, I'm just testing this. And it seems that live boot from USB-stick has a significant problem.

I just tried something else: I took the exact same .iso file that I used for the USB-stick and burned it onto a DVD.
Boot to the DOS-like "Start Lubuntu" menu, select same.

Behaviour as expected: half a minute pause, then dark screen, half a minute later Lubuntu logo with the five walking dots, 4 minutes later Lubuntu live desktop.
It's always worked like that by me when using a DVD. Painless.

I've no need to use Startup Disk Creator, my PC works perfectly and live boots from DVD any time it's needed.

But I feel sorry for the newcomers who are left with a super-frustrating experience after trying to install (x)ubuntu.

---

### Post by sudodus on 2020-07-18
@ml9104,

I don't think we will agree about booting live systems, and that is OK. There are many ways to install and use Linux, and let us be happy with our different ways - and let the original poster, linuxnewby3 find their own way :-)

---

### Post by GhX6GZMB on 2020-07-18
> **sudodus said:**
> @ml9104,

I don't think we will agree about booting live systems, and that is OK. There are many ways to install and use Linux, and let us be happy with our different ways - and let the original poster, linuxnewby3 find their own way :-)

Are you serious? This is not about "which way to boot a live system", this is about a way that works and one that apparently often doesn't.

I put quite some effort into testing and understanding why so many newcomers have problems live booting from USB-sticks, and I was able to reproduce the problem, but you think it's about "different ways"?

Wow.

---

### Post by GhX6GZMB on 2020-07-18
Just to round off: I did one more test.
Using the "dd" option in Rufus (instead of .iso) actually does create a working live-boot USB-stick. Too bad it's not the recommended option. New User friendly? You decide...

[ATTACH=CONFIG]286488[/ATTACH]

---

### Post by C.S.Cameron on 2020-07-18
There are many ways to install Ubuntu to USB.
A Live, (non Persistent), install is useful for installing Ubuntu.
For testing Ubuntu a Persistent install allows installing programs and setting preferences.
Making a Full install to USB, same as to Internal drive, will make a portable drive with all the features of an internal drive, allowing special drivers, updates and upgrades, increased reliability, etc.
[https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step](https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step)

---

### Post by linuxnewby3 on 2020-07-19
@ml9104 
Thank you for your response. The problem i have is not with a single computer. 
I can make it work for 1 specific laptop and i've tried to install Ubuntu 20.04 using both Rufus and Virtualbox as suggested methods by forums and youtube videos such as Gary explains and Switched to Linux. The problem starts when i want to boot the installed Ubuntu from my USB drive specifically on my desktop. (HP desktop with indeed a CD drive, but if more info is needed i can provide later) 

[ATTACH=CONFIG]286493[/ATTACH]


i have installed it in a partion (made by the installer from Ubuntu) 10GB for the system wich automatically creates the other space for storage.  ( i used 1 usb with rufus installed ISO from ubuntu and the 2 usb to install the system)
I can't figure out if the problem is with the installation somewhere with the partions/file systems or it is in the settings for my BIOS. 

Also it's not that hard if i wanted a dual-boot / replace one of my windows systems / just try ubuntu from the live USB. But that's not what i'm trying to do :P

---

### Post by linuxnewby3 on 2020-07-19
Yes, Sir the last option is what i'm trying to make. A full Install to USB. 
I tried that using Rufus for install on USB - 1 (4gb) and installed Ubuntu to USB - 2 (128gb)

Only problem is that i can't boot it from my desktop if i am not in Legacy mode. Do you know what the problem is ? (In the BIOS or in the installation process) 

regards,

---

### Post by CelticWarrior on 2020-07-19
For a full install to USB you need two USB sticks, one to run the live installer (can be done with Rufus) and the one where it will be installed. Using Rufus to burn an ISO file to a UASB stick is NOT an installation, typically a live system only. It can be done with persistence and that is closer to an actual installation (it allows saving settings, files and some installed software) but isn't.

With Rufus you may need to change the default settings to GPT/UEFI for UEFI mode (preferred) or use the DD option. Honestly, Balena Etcher, because it uses DD by default, is a simpler a fool-proof tool for beginners. Because it does an exact copy of the ISO it'll boot in BIOS and UEFI.

---

### Post by linuxnewby3 on 2020-07-19
@celticwarrior
Thanks for your reaction. I understand and know that the ISO on the 4gb USB isn't the installation. I use this small USB to try and install Ubuntu to my second 128gb USB. 
I used rufus with the settings you've suggested. Can you explain what partitions i need to make during the install from Ubuntu to that 128gb. 
I really think that something is going wrong there. 

From what i understand i need to make at least 2 partitions
- Ad the Root to one partition. (wich option in the installation do i need to make it boot on both BIOS and UEFI ? )
- And need EXT4 for storage of programs and general usage of the system. 

Because my latest try: 
i made a 8GB in Efi format
and used what's left for EXT4.
I can tell that it boots from my laptop, but again my desktop can't find that efi file. it doesn't even show up in the bootmanager if i press F9. (also tried when restarting after a regular windows boot and holding Shift)

(don't be mad i'm just trying really) I think it's something in the installation process that i've been doing wrong. Any help will be appreciated. 

Regards, newby

---

### Post by sudodus on 2020-07-19
1. Will you use the whole drive (and overwrite whatever is there now)? Or are there data, that you want to keep (in a data partition separate from the installed Ubuntu system?

2. Do you intend to use encrypted disk (a complication, but maybe necessary to protect confidential data)?

The answers will decide what method, that would be best.

---

### Post by C.S.Cameron on 2020-07-20
It sounds like you need a Full Install USB drive that boots both Legacy mode, (Desktop) and UEFI mode, (Laptop).

The easiest way to make such a drive is to Flash the image file of a pre-built Full install drive to a USB stick. 
Flashing can be done in Windows using Rufus or Etcher. It can be done in Ubuntu using Disks or mkusb.

- Download Image File: [https://phillw.net/isos/linux-tools/uefi-n-bios/dd_unb_ubuntu-20.04_15GB_2020-06-26.img.xz](https://phillw.net/isos/linux-tools/uefi-n-bios/dd_unb_ubuntu-20.04_15GB_2020-06-26.img.xz)

- Download Rufus: [https://github.com/pbatard/rufus/releases/download/v3.11/rufus-3.11.exe](https://github.com/pbatard/rufus/releases/download/v3.11/rufus-3.11.exe)

- Double click Rufus exe file. (No need to install it).

- Select USB2 Target drive in Rufus.

- Select Image File in Rufus.

- Click Rufus start button.

- Wait for flashing to complete... Done.

(Password is "changeme", change it)

Thanks to sudodus for the image file.

---

### Post by linuxnewby3 on 2020-07-20
Question 1: i will use the whole drive it's empty
Question 2: Yes, encrypted seems to the way to go. i don't want to risk losing any important files without security.

---

### Post by sudodus on 2020-07-20
Encryption rules out the easiest way, that is described by C.S.Cameron in post #19. For encrypted disk to work, *you* must install the system and set a good passphrase (longer and harder to guess than a normal password). It cannot be cloned from a compressed image file.

Do you intend to use it in several computers or in only one computer?

- If in only one computer, you can try according to [**this link**](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/942312#942312) with a detailed description. Please modify to activate LVM with LUKS encryption in the partitioning window.

- If you want to use it in several computers, it should boot both in UEFI and BIOS mode, so try according to [**this link**](https://askubuntu.com/questions/1086309/how-to-make-bios-uefi-flash-drive-with-full-disk-encryption).

---

### Post by linuxnewby3 on 2020-07-20
i do intend to use it on different computers

The link seems very usefull. Only the most frustrating thing ever.

I understand i should make a live install of ubuntu on a USB drive to install a persistent install on a second USB. 
So i need mkusb, but to use that i need the install of Ubuntu first unto so usb drive. 

Is it just me overcomplicating things. Or should just a Rufus persistant install work in the same way  ? If i install it like that to my 128gb USB and from there follow the other steps ?
***I hope you understand what i'm saying. i have like 2 USB-drives for this: Large is 128gb and small 4gb. What i think to understand i should try these steps ?: ***
***Large usb rufus install ISO file (default)***
***install Ubuntu to small USB (4gb)***
***make persistant USB of the large USB with mkusb ***

---

### Post by sudodus on 2020-07-20
You won't get an encrypted system with Rufus.

If you accept a standard installed system, you can use the method described in post #19 (and in a link from post #5).

You can also create a persistent live system with Rufus.

So if you want a qualified encryption, you have to use a more complicated method. It is not a standard procedure to install a portable system into a USB drive, and things get even more complicated when you want it encrypted.

But it is possible, if you are patient and continue until you succeed. You are not alone, we are here to help :-)

---

### Post by sudodus on 2020-07-20
> **linuxnewby3 said:**
> 
I hope you understand what i'm saying. i have like 2 USB-drives for this: Large is 128gb and small 4gb. What i think to understand i should try these steps ?: 
Large usb rufus install ISO file (default)
install Ubuntu to small USB (4gb)
make persistant USB of the large USB with mkusb 

No. I'll try to explain better.

- If you want a persistent live drive, it is a one-step procedure. Use Rufus directly from the Ubuntu iso file to the big USB drive (easy).

- If you want an installed system that boots in UEFI and BIOS mode, and you have a extracting program installed in Windows, for example 7-zip, it is a one-step procedure. Use Rufus directly from the compressed image file with Ubuntu to the big USB drive (easy).

- If you want an encrypted installed system that boots in UEFI and BIOS mode, things are more complicated. Then you should **follow exactly the steps described in [this link](https://askubuntu.com/questions/1086309/how-to-make-bios-uefi-flash-drive-with-full-disk-encryption)** and I won't repeat it here, because it might cause confusion (more complicated).

[hr][/hr]
Maybe it is a good idea to start with one of the easy methods, and when you have more experience and confidence, you create the ultimate system, an encrypted installed system that boots in UEFI and BIOS mode.

---

### Post by C.S.Cameron on 2020-07-20
> **sudodus said:**
> 
- If you want an encrypted installed system that boots in UEFI and BIOS mode, things are more complicated. Then you should **follow exactly the steps described in [this link](https://askubuntu.com/questions/1086309/how-to-make-bios-uefi-flash-drive-with-full-disk-encryption)** and I won't repeat it here, because it might cause confusion (more complicated).


The first encryption method on this page works for 18.04.

The second method, ([https://askubuntu.com/questions/1086309/how-to-make-bios-uefi-flash-drive-with-full-disk-encryption/1257347#1257347](https://askubuntu.com/questions/1086309/how-to-make-bios-uefi-flash-drive-with-full-disk-encryption/1257347#1257347)) , works for 20.04 and is a lot simpler than the 18.04 method, but you have to unplug your internal HDD or you will overwrite it.

I am still trying to figure out how to get hibernation working on it.

---

### Post by linuxnewby3 on 2020-07-22
Hi again,

I think my lack of experience has brought me to asking this many questions.
But about the install. Let's i want the easy way to install Ubuntu to my big USB drive. 

-I make the small USB drive with Rufus
-Install Ubuntu to my Large USB drive
insert question: What kind of partitions do i need to make in order to boot in BIOS and UEFI ? (in the installer from Ubuntu)
Because from standard install it make a EXT4 and that's not working. 

Let's start with the easy method indeed. encrypted isn't a thing to worry about if i don't lose the USB, right ?

---

### Post by sudodus on 2020-07-22
The easy method is described with more details at [this link](https://ubuntuforums.org/showthread.php?t=2447539&p=13974203#post13974203).

With this method you need not use the small drive for the installation, only after the installation in order to grow the root partition to use the whole drive.

Check that you have a tool for compression and extraction of compressed files. I suggest **7-zip** in Windows.

Use **Rufus** in Windows directly to extract and clone **from the compressed image file to the big USB drive**.

Then use **Rufus** to create a **live** drive with Ubuntu in the **small USB drive**.

Boot into this drive small USB drive, use **gparted** to grow (increase the size) of the root partition, the main partition of the big USB drive, so that it will use all unallocated drive space.

Let us know if you have problems, and we will help you. Good luck :-)

---

### Post by C.S.Cameron on 2020-07-22
+1 for sudodus's Ubuntu 20.04 image. 
Quicker to download and install than the ISO. 
Works with both UEFI and Legacy.

---

### Post by C.S.Cameron on 2020-07-22
> **sudodus said:**
> 
Check that you have a tool for compression and extraction of compressed files. I suggest **7-zip** in Windows.

Use **Rufus** in Windows directly to extract and clone **from the compressed image file to the big USB drive**.


I did not need **7-zip** to extract the image file, Rufus will work with a **.im.xz** file directly.

> 
Then use **Rufus** to create a **live** drive with Ubuntu in the **small USB drive**.


Better perhaps to install mkusb to the new drive and use that for making the Live drive.

---

### Post by sudodus on 2020-07-23
> **C.S.Cameron said:**
> I did not need **7-zip** to extract the image file, Rufus will work with a **.im.xz** file directly.



Better perhaps to install mkusb to the new drive and use that for making the Live drive.

I tried is a rather clean Windows 10, and Rufus did not work (with this compressed image file). Then I installed 7-zip, and after that Rufus could do it all, uncompress and clone. My interpretation is that Rufus identifies 7-zip and uses it as a preprocessor.

---

### Post by linuxnewby3 on 2020-07-23
@sudodus Thank you for your patience. 
I decided to go with a easy method one of you suggested:

[SIZE=2][FONT=book antiqua]""[/FONT][/SIZE]
[LIST]
[*][FONT=inherit][SIZE=2][FONT=book antiqua]Download BIOS/UEFI Template: [https://phillw.net/isos/linux-tools/uefi-n-bios/dd_grub-boot-template-for-uefi-n-bios.img.xz](https://phillw.net/isos/linux-tools/uefi-n-bios/dd_grub-boot-template-for-uefi-n-bios.img.xz)[/FONT][/SIZE][/FONT]
[*][FONT=inherit][SIZE=2][FONT=book antiqua]Flash image to target USB using Win32DiskImager, Rufus, mkusb, balenaEtcher, etc.[/FONT][/SIZE][/FONT]
[*][FONT=inherit][SIZE=2][FONT=book antiqua]It is recommended to unplug any internal drives especially when installing in UEFI mode.[/FONT][/SIZE][/FONT]
[*][FONT=inherit][SIZE=2][FONT=book antiqua]Boot Live Installer USB, and insert Target USB.[/FONT][/SIZE][/FONT]
[*][FONT=inherit][SIZE=2][FONT=book antiqua]Start install process, select: Language, Keyboard, Wireless, Updates and Something Else.[/FONT][/SIZE][/FONT]
[*][FONT=inherit][SIZE=2][FONT=book antiqua]Select Target USB for Bootloader installation.[/FONT][/SIZE][/FONT]
[*][FONT=inherit][SIZE=2][FONT=book antiqua](Optional Data Partition), Select the empty space on the Target drive and click the plus sign to create a FAT32 partition with mount point "/Windows". Leave at least 6GB empty space for root partition.[/FONT][/SIZE][/FONT]
[*][FONT=inherit][SIZE=2][FONT=book antiqua]Select the empty space on the Target drive and click the plus sign to create an ext4 partition with mount point "/".[/FONT][/SIZE][/FONT]
[*][FONT=inherit][SIZE=2][FONT=book antiqua]Select Install now, confirm partition to be formatted, enter location, name and password.[/FONT][/SIZE][/FONT]
[*][FONT=inherit][SIZE=2][FONT=book antiqua]When install is complete copy root /boot/grub/grub.cfg to overwrite boot,esp /boot/grub/grub.cfg[/FONT][/SIZE][/FONT]
[*][FONT=inherit][SIZE=2][FONT=book antiqua]If created in UEFI mode reinstall GRUB for BIOS boot:[/FONT][/SIZE][/FONT]
[FONT=inherit][SIZE=2][FONT=book antiqua]sudo mount /dev/sdx2 /mnt[/FONT][/SIZE][/FONT]
[FONT=inherit][SIZE=2][FONT=book antiqua]sudo grub-install --boot-directory=/mnt/boot /dev/sdx[/FONT][/SIZE][/FONT]
[/LIST]
[COLOR=#242729][FONT=Arial][SIZE=2][FONT=book antiqua]Thanks to Sudodus for the mkusb based BIOS/UEFI Template'''
[/FONT][/SIZE]
I successfully installed on the USB drive. Only problem is probably with the last 2 steps. i don't understand the files mentioned do you copy from persistant live USB ----> to the full install large usb ? 
The final step is probably just typing in the terminal. But i think it doesn't work because of the step above ? 

I'll get there. Really happy with what i've got so far. But i think i need to fix it somehow to make it work on my desktop. (Laptop works in UEFI, i've checked it)

[/FONT][/COLOR]

---

### Post by C.S.Cameron on 2020-07-23
The install process creates a valid grub.cfg file on the root partition of the target drive.
The template comes with a grub.cfg file on the EFI partition designed to boot ISO files.
It must be replaced with a grub.cfg file that will boot the full install, which the one on root does.
Reinstalling GRUB activates the boot partition so that the drive boots either BIOS or UEFI.

---

### Post by C.S.Cameron on 2020-07-24
> **sudodus said:**
> I tried is a rather clean Windows 10, and Rufus did not work (with this compressed image file). Then I installed 7-zip, and after that Rufus could do it all, uncompress and clone. My interpretation is that Rufus identifies 7-zip and uses it as a preprocessor.

I once discovered that Startup Disk Collector had an option to test drive a USB without having to logout of Ubuntu, I mentioned it to others a few times like it was normal.

Later I discovered that SDC only adds the option if QEMU is installed.

I guess I need to search for and edit a few posts now, how embarrassing.

---

### Post by sudodus on 2020-07-25
No worries C.S.Cameron, I have made similar mistakes. Most if not all of us do them. As long as we discover what went wrong, admit it and tell other people what is the correct advice, everything is fine, maybe even better than if everything was correct at once :-)

---

### Post by linuxnewby3 on 2020-07-25
Hi again! 

With: template, you refer to the grub file on the install USB right  ? 
When i want to copy that file from boot/grub/grub.cfg to the USB with ubuntu on it it says: permission denied

---

### Post by linuxnewby3 on 2020-07-25
[ATTACH=CONFIG]286539[/ATTACH]
For reference these are the disks created. It doesn't look right to me. Or is it right ?

---

### Post by sudodus on 2020-07-25
> **linuxnewby3 said:**
> Hi again! 

With the template you refer to the grub file on the install USB right  ? 
When i want to copy that file from boot/grub/grub.cfg to the USB with ubuntu on it it says: permission denied

Which template? Do you mean [FONT=Courier New]**dd_grub-boot-template-for-uefi-n-bios_dark-bg.img.xz**[/FONT] ?

Can you copy with elevated persmisisons, using
```

sudo cp /full-path-to-source/grub.cfg /full-path-to-target/grub.dfg

```

---

### Post by linuxnewby3 on 2020-07-25
I don't know. You've mentioned it in post 32.

Does that file come with the regular ISO install from the Ubuntu download ? Because my system can't find the code you've sent (post 37)

---

### Post by sudodus on 2020-07-25
I did not write post #32, but I think he means that template. Did you try to copy with sudo?

---

### Post by linuxnewby3 on 2020-07-25
my bad, didn't noticed the name ;) Can you explain how to do that ? i assume you copy it somehow in the terminal ?

---

### Post by sudodus on 2020-07-25
The template contains only the boot structure for UEFI and BIJOS mode. There is no content from the Ubuntu iso file there. If you want a compressed image file containing Ubuntu, you need a bigger file, [dd_unb_ubuntu-20.04_15GB_2020-06-26.img.xz](https://phillw.net/isos/linux-tools/uefi-n-bios/dd_unb_ubuntu-20.04_15GB_2020-06-26.img.xz).

The intention with the template is to either make a grub and iso system, booting via grub into the iso file, or to do what is described by C.S.Cameron, to install Ubuntu (make an installed ssytem), where one of the steps is to copy grub.cfg from inside the installed system to the boot parttion, that comes with the template.

---

### Post by linuxnewby3 on 2020-07-25
Im sorry you've lost me.

I have the installed system now on my USB drive. and i need to make it to boot in both modes. 
I understand that the grub.cfg is inside the installed system on my drive ? is that the one in boot/grub/grub.cfg ? and what do i need to do with that file ?

---

### Post by sudodus on 2020-07-25
> **linuxnewby3 said:**
> my bad, didn't noticed the name ;) Can you explain how to do that ? i assume you copy it somehow in the terminal ?

Yes, the command is run in a terminal window.

You must identify the full directory path of the source file and the target file. The two partitions must be mounted and the mount points plus the paths inside should be there, probably something like

```

/mountpoint-of-source/boot/grub/grub.cfg
/mountpoint-of-target/boot/grub/grub.cfg

```

You can find these mountpoints via the command 'df' (if they are mounted)

```

df

```

Otherwise you must mount them before you can run the copy command

Please check and doublecheck, that you get it the correct way. Otherwise you will overwrite the source with the target file, and there will be problems.

```

sudo cp /mountpoint-of-source/boot/grub/grub.cfg /mountpoint-of-target/boot/grub/grub.cfg

```

---

### Post by sudodus on 2020-07-25
But again, if this is too much for you, [there is an easier way](https://ubuntuforums.org/showthread.php?t=2447539&p=13974203#post13974203).

There will be no encryption, but you will get an installed system, that boots both in UEFI mode and BIOS mode. While using that system maybe during some months, you can learn how to use commands in the terminal window including how to identify file systems, to mount and unmount them, and to run commands with elevated permissions with sudo.

After that it will be rather easy for you to make exactly what you want, an *encrypted* installed system, that boots both in UEFI mode and BIOS mode.

---

### Post by linuxnewby3 on 2020-07-25
yeah, i will keep that in mind. but i will try to figure out what you've just said in post 43. I'll need some more time for that. i'll be back in 1-2 days probably. Thank you for your patience!

---

### Post by C.S.Cameron on 2020-07-25
If you look at the drive using GParted, the first partition on the left is a small, (1MB), bios_grub partition, sdx1.
The next partition, sdx2, boot,esp is the usbboot partition, It is the partition that we want to copy grub.cfg to.
The next partition is the where Ubuntu has been installed. It is where we want to copy /boot/grub/grub.cfg from.

---

### Post by linuxnewby3 on 2020-08-01
yeah, so i've tried to do that. Couldn't figure it out. Also it wouldn't let me copy it if it was booted from that file. (i think that makes sense) But gives error about permission.
And with diskmanagement i've seen that the grub somehow was installed to a small partition of my laptop instead of the USB. 

I'm giving up.
In the future the next best thing will be a dual-boot without any USB-drives. But i'm working on different laptop/desktops and that's why a full install on USB would be a nice thing to have. 
Unfortunate that it's this complicated.

Thanks for all the help!

---

### Post by C.S.Cameron on 2020-08-01
Perhaps try just once more using the **easy** method sudodus recommends:
[https://askubuntu.com/questions/1255783/cannot-install-ubuntu-on-my-flash-drive/1255893#1255893](https://askubuntu.com/questions/1255783/cannot-install-ubuntu-on-my-flash-drive/1255893#1255893)
It really is very easy.

---

