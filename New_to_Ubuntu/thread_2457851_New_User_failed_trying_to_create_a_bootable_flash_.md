---
title: "New User: failed trying to create a bootable flash drive on Windows XP"
date: 2021-02-10
forum: New to Ubuntu
---

### Post by caseyatthebat on 2021-02-10
Greetings! I want to join your ranks and leave Windows behind!  

My old Windows XP system is on it's last leg; I read a How To Geek article a year ago about switching to Linux and worked at the instructions in the article several times over the past year and have never been successful at creating a bootable flash drive to use with my computer so I can learn Linux and how to install and use it on the computer itself and leave the software overlords behind.

I'm nearing the cliff edge because the last browser available the Windows XP, Firefox is stopping support too, and my system is acting strange, and soon, I know, it will not work at all!  I've spent many hours again trying to make this work.

I finally found the Ubuntu.com website and your tutorials and felt like, I'm going to make it man, keep striving you'll get there................. got closer it seems but, it doesn't work. Here's what I've done so far.

Dell Dimension E521 CPU
      AMD Athlon 64 3200+ 2.0 Ghz
      2.43 GB of RAM Physical Address Extension
      Hard Drive: Total size 149 GB, Free space 24.7 GB
      Sandisk 4GB USB drive

Windows XP Media Center Edition 
      Version 2002 service pack 3

I followed the tutorial called "Create a bootable USB stick on Windows"

      I downloaded Rufus 2.18.1213.0 and Ubuntu-20.04.2-desktop-amd64.iso to my desktop and executed the Rufus utilty.

      It didn't look the same as the picture of the version of Rufus in the tutorial; I did my best to enter the correct info in the fields and then click start.

Here's the fields:

    Device: Ubuntu-20_0(I:)[4GB]
    Partition Scheme and target system type: MBR partition scheme for BIOS or UEFI
    File system: FAT32
    Cluster size:4096 bytes (default)
    New Volume label:UBUNTU-20_0
    Format Options:                     
    checked: quick format 1 Pass
                 create bootable disk using Free DOS (Disk icon to the right when clicked shows my desktop files:includes Ubuntu-20.04.2-desktop-amd64.iso
                 create extended label and icon files
          
                 
     When I clicked Start, it filled up green marks in the progress bar. When it was full I clicked Close and  then tested the USB stick by shutting down the system,
then turning it back on while holding down the F12 key. The computer beeped repeatedly while the BIOS loaded and the list of bootable devices were shown.  I chose USB-Zip.  It immediately showed the error message invalid boot error or something like that.

I re-did the whole procedure again, this time logged on as Administrator.  After trying to boot it again, choosing USB-zip. This time it gave a message about invalid partition or something like that.

When I looked at the contents of the USB drive, it showed two files calleed update. Ones a picture, the other is a short note.  Then there is a folder called Locale.  It has 25 files in it. There are 18 files named EGA.cpx through EGA18.cpx, four system files named Keyb,oard, Keybrd, Keybrd2, Keybrd3 and Keybrd4, and three application files called KEYB, MODE and DISPLAY.

Later I found a button on the Rufus utility screen that said "log". When clicked, it displayed this information:

Could not get Disk Extents: [0x00000015] The device is not ready.
Could not get Disk Extents: [0x00000015] The device is not ready.
Could not get Disk Extents: [0x00000015] The device is not ready.
Could not get Disk Extents: [0x00000015] The device is not ready.
Disk type: Removable, Disk size: 4GB, Sector size: 512 bytes
Cylinders: 486, Tracks per cylinder: 255, Sectors per track: 63
Partition type: MBR, NB Partitions: 1
Disk ID: 0x000B4957
Drive has a Windows 7 Master Boot Record
Partition 1:
  Type: FAT32 LBA (0x0c)
  Size: 3.7 GB (4003463168 bytes)
  Start Sector: 2048, Boot: Yes
Found USB 2.0 device 'SanDisk Cruzer USB Device' (0781:5530)
Using autorun.inf label for drive I: 'UBUNTU-20_0'
Found USB 2.0 device 'TEAC USB   HS-CF Card USB Device' (0644:0200)
Device eliminated because it appears to contain no media
Found USB 2.0 device 'TEAC USB   HS-MS Card USB Device' (0644:0200)
Device eliminated because it appears to contain no media
Found USB 2.0 device 'TEAC USB   HS-SD Card USB Device' (0644:0200)
Device eliminated because it appears to contain no media
Found USB 2.0 device 'TEAC USB   HS-xD/SM USB Device' (0644:0200)
Device eliminated because it appears to contain no media
1 device found
Could not get Disk Extents: [0x00000015] The device is not ready.
Could not get Disk Extents: [0x00000015] The device is not ready.
Could not get Disk Extents: [0x00000015] The device is not ready.
Could not get Disk Extents: [0x00000015] The device is not ready.
Disk type: Removable, Disk size: 4GB, Sector size: 512 bytes
Cylinders: 486, Tracks per cylinder: 255, Sectors per track: 63
Partition type: MBR, NB Partitions: 1
Disk ID: 0x000B4957
Drive has a Windows 7 Master Boot Record
Partition 1:
  Type: FAT32 LBA (0x0c)
  Size: 3.7 GB (4003463168 bytes)
  Start Sector: 2048, Boot: Yes


Well, that's everything I tried; where am I going wrong?    Thanks so much in advance!  I'm so eager to get Linux and learn how to use it!

---

### Post by DuckHook on 2021-02-10
Ohhh Boy.

If you are still on XP, you are not only courting catastrophe, but have been doing so for years. Are you sure that your "last legs" experiences are not due to malware? XP was a malware cesspool and given that it was dead and buried years ago, you have been a walking case of *pwn&#8209;me! pwn&#8209;me!* for the tech equivalent of decades.

Here's what I would do if I were you:

[LIST]
[*]Trust NOTHING that comes out of your current box. This means that I would not trust it to produce a single boot device even if I could get it working.
[*]Save all critical data files (and data files only!) to an external drive.
[*]Get a friend or relative with a working fully patched fully antibiotic&#8209;inoculated Win10 to produce that Ubuntu LiveUSB.
[*]Run that LiveUSB first as a LiveUSB to make sure it works. Then…
[*]***NUKE YOUR XP INSTALL FROM ORBIT***
[*]Install Xubuntu using the LiveUSB that has otherwise never touched your system.
[*]Run your old files through every Antivirus and malware scanning app you can think of.
[*]***DO NOT*** bring over any Windows apps, macros or utilities that you may have backed up. Nuke those too. You may not be able to do anything about MS docs that harbour hidden nasties. That's just too bad.
[*]Only after you are reasonably sure that all remaining documents are clean do you copy them back onto your new install.
[/LIST]
A few things to note:

[LIST]
[*]You are not using the proper ISO to make your LiveUSB. The files that you list do not belong to Ubuntu. They may be part of FreeDOS which you allude to in your somewhat convoluted narrative. At any rate, you may think that you are burning an Ubuntu LiveUSB, but you are not. There's nothing that anyone can help you with here except to point you to the proper instructions: [https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview)
[*]It is evident that you download scads of software from all sorts of sites willy&#8209;nilly. This is not uncommon: we all did things that way back in the XP days. But today, it is nothing short of an invitation to disaster. You really need to read the link in my sig: *Linux is Not Windows*.
[*]On your friend's machine, download only from the official Ubuntu website. DO NOT download from anywhere else.
[*]Your machine is old and under-powered. I have a Dell Optiplex that is almost identical—a little more powerful in fact. It will run Ubuntu like a pig on a poke. Better to run Xubuntu, Mate, Budgie or Lubuntu on that dinosaur.
[*]If you have not changed anything on it, then the video subsystem will be a real pain in the neck. It will likely choke and die on a modern OS. If you can, change the video card for something more powerful.
[/LIST]
I hope that you can make this transition and be properly introduced into the Linux&#8209;sphere. But you will need to unlearn a lot of bad Windows habits and start learning good Linux habits, including proper OS hygiene. You can start by refraining from such XP awfulness as autologins and running as the administrator. Again, that link in my sig is invaluable to you.

Good luck and tell us how it goes.
DH

---

### Post by Impavidus on 2021-02-11
> **DuckHook said:**
> 
[LIST]
[*]Get a friend or relative with a working fully patched fully antibiotic&#8209;inoculated Win10 to produce that Ubuntu LiveUSB. 
[/LIST]


 (grin)
Windows 8.1, Mac or Linux will do too, although on the latter two the procedure will be slightly different.

Your computer isn't too bad for a WinXP machine, but not good enough for regular Ubuntu. Your ram is good enough for Xubuntu or Mate or one of the other light flavours. On the main Ubuntu webpage, click Download, look for Ubuntu flavours and click one of the links. Graphics may be a problem. You not only need it for the OS itself, but modern web browsers also need decent graphics these days.

Your computer must be full of malware. Time to wipe it clean.

---

### Post by ActionParsnip on 2021-02-11
Get a pal to make you a bootable USB stick with something better. Then when you install Ubuntu select to use the whole disk and wipe XP off. Once Ubuntu is installed you can restore your user data from your backups after a virus scan

---

### Post by caseyatthebat on 2021-02-12
Thank you DuckHook, Impavidus, and ActionParsnip for your replies and time  It is so much appreciated!

I agree wholeheartedly that I'm in a pickle and I have a big learning curve ahead of me.

DuckHook, I read "Linux is not Windows" and agree with everything you wrote. I especially relate to your car analogy. I'm a DIYer; I rebuilt my entire rear suspension in my car by relentless research and six months of hard driveway time so my car is in my control.  I want to do the same with my computer and know there is a lot to learn.

My first step of getting a bootable Linux USB is tough because my Windows XP system is so messed up.  I don't have a friend or relative to help me with that; I just don't.  And with Covid, I'm in a high risk group, even my groceries are delivered.

Impavidus, thank you for the tip about Xubuntu or Mate being better for my older hardware.  I started searching online to see if I could buy a bootable Linux USB to get me started and I found a website called ShopLinuxOnline.com that sells many distros including different versions of Xubuntu and Mate. I've sent them an e-mail about my hardware to ask what one of their products they would recommend.  Their Better Business Bureau rating shows no complaints, price is not much so I'm thinking that might be a good move.  Any experience with them or suggestions about a reliable place to buy one?

Again, thank you all for your time and effort to help me get a toehold in Linux.  I am very grateful.

---

### Post by grahammechanical on 2021-02-12
My first attempt to create a Ubuntu install USB stick failed and I was trying from Ubuntu and using the same make of memory stick as you are. In my case the USB stick was pre-formatted to be a Windows USB stick for backup purposes. This could explain why your memory stick has a Windows 7 master boot record.

From Windows XP try formatting the memory stick. It will have to be a Microsoft file format such as FAT 32. This will wipe out the existing files. Then try using Rufus to burn the Ubuntu ISO image to the memory stick. It could be that as the memory is set up for a specific purpose the ISO image is being treated as data to be put on the stick and not as an image to burn to the stick. I am just guessing. 

My last experience of Windows was with Win98. I also built my own machine. My first install of Ubuntu was with a CD-ROM with Ubuntu on that was given away by a computer journal.

We all start somewhere and we never stop learning.

Regards

---

### Post by Impavidus on 2021-02-12
The first time I installed Ubuntu was from an Ubuntu 6.06 live cd I got from somebody I trust. Since then I've always made my own live disks. I know there are companies selling live disks of various Linux distros. It's a legitimate business and I think you can trust most of them. I don't know about any of them specifically. And if I did, they may not all ship to your country (wherever that is).

---

### Post by DuckHook on 2021-02-12
> **caseyatthebat said:**
> &#8230;I found a website called ShopLinuxOnline.com that sells many distros including different versions of Xubuntu and Mate. I've sent them an e-mail about my hardware to ask what one of their products they would recommend.  Their Better Business Bureau rating shows no complaints, price is not much so I'm thinking that might be a good move.  Any experience with them or suggestions about a reliable place to buy one?&#8230;
I've no experience with them but agree that their pricing is quite reasonable. While I would not normally recommend anything other than a spin&#8209;your&#8209;own&#8209;from&#8209;known&#8209;good&#8209;source method, in your case, I believe such a purchase to be good strategy.

I agree with others that you should not look at Ubuntu, but Mate instead. This seems to be the only flavour they carry. I can't find Xubuntu, Lubuntu or Budgie on their site. However, Mate is a perfectly good flavour and may even be more familiar to you since you are used to XP. For an idea of what the various flavours look like and why they exist, see the link in my sig: The Best 'buntu Flavour

Make sure that your system can boot from USB first before buying the USB product. Otherwise, you may have to use the DVD product.

EDIT

They do have Lubuntu and Xubuntu. You just have to dive further into their site. It's up to you which version you choose. Perhaps have a look through my link first before deciding. If you decide to go for a non 'buntu Flavour like Mint or Linux Lite, we may not be able to help you as well as their own online communities. However, I know that they have vibrant communities too, so help is usually available no matter which you choose.

---

### Post by jim Kane on 2021-02-12
I had a same problem with a USB stick trying to load windows 10 on an older PC for a friend
as you have a 'TEAC USB HS-SD Card USB Device' I  would try a new SD card 
which then worked perfect for me, and im not sure that  USB-Zip would be correct option in Bios for a usb stick
and incidentally im  typing this on Xubuntu with the same PC spec as yours AMD Athlon 64 3200+ 2.0 Ghz 2.43 GB of RAM
works fine if a little slow

---

### Post by equi000 on 2021-02-19
I also failed to create a bootable USB stick for my 9 years old Fujitsu notebook with Ubuntu 18.x 1 year ago. I could find the error message that happened during boot from the USB stick indeed in an Ubuntu blog. Guess what: Same type of notebook. Probably some BIOS issue.
Burning and booting installation from DVD worked fine.
Btw: I switched due to the fact that Win7 was no longer supported. And I&#8216;m sooo happy I left MS and Windows behind...

---

### Post by T6&amp;sfpER35% on 2021-02-19
i could never get a distro to install from a USB , I use DVD instead and it never failed .

---

### Post by mastablasta on 2021-02-22
> **3nd said:**
> i could never get a distro to install from a USB , I use DVD instead and it never failed .

this usually solves it. make sure you burn as image. 

also you can try another USB boot creator like balena etcher, yumi or linuxliveUSB cretaor (lili). sometimes they ar enot up to date and they do not create the image well and for osme reason i couldn't get certain images working. balena etcher seem to be doing it well.

balena: [https://www.balena.io/etcher/](https://www.balena.io/etcher/)
yumi: [https://www.pendrivelinux.com/yumi-multiboot-usb-creator/](https://www.pendrivelinux.com/yumi-multiboot-usb-creator/)
lili: [https://www.linuxliveusb.com/](https://www.linuxliveusb.com/)

> **DuckHook said:**
> 
[LIST]
[*]Your machine is old and under-powered. I have a Dell Optiplex that is almost identical—a little more powerful in fact. It will run Ubuntu like a pig on a poke. Better to run Xubuntu, Mate, Budgie or Lubuntu on that dinosaur.
[*]If you have not changed anything on it, then the video subsystem will be a real pain in the neck. It will likely choke and die on a modern OS. If you can, change the video card for something more powerful.
[/LIST]


this is true. video chip is actually the issue here. i have same CPU o(or from same era i think mine has higher Ghz). but i have GT 730 nvidia card inside and can run many newish games (let's say up to about 2013 and some new indie games) without issues. i also have windows XP on the other disk. i went with Kubuntu instead of Ubuntu. you need free space (un-formatted) or empty disk to install the OS to. i made the move with empty disk.

widnows XP is not such an issue as long with working antivirus and firewall. it's been 2 years since i ran it last. i kept it on the other disk while i am trying to get my favourite games from there to run on linux. i made a small shortcut called boot2win, that would reboot a PC to windows only once. this was made so that my kid could easily switch to windows games. but we moved many to linux now and he got himself a better PC, and he now plays new games in linux there. when i get a new PC i plan to move all stuff to linux and use VM for any windows only things. not many remain so far. so i haven't booted windows in 1 and a half year as i can get most stuff to run in wine/playonlinux or proton. ž

performance? well widnows XP had 4 GB ram with PAE kernel + dedicated/separte GPU VRAM, but didn't really utilise it well. much of ram was taken by windows and antivirus stuff. on linux about 450 MB is take by OS, the rest is free for apps. games generally work better. some are working slightly slower and produce some lag (Oblivion, Hitman). not quite sure how to get around it. i am sure there is a setting or library i could use but do not have too much time to tinker. if i had a new CPU they would work with no issues. overall performance is a lot better than on windows XP.

---

### Post by caseyatthebat on 2021-02-25
Dear Esteemed Forum Mates:

Here's the latest:

 Gave up on ShopLinuxOnline.com; they never replied, not sending my credit card into the unknown!

Action: Reformatted the USB stick with FAT32, used UniversalUSBInstaller with Ubuntu-Mate 18.04.5 to make a new LiveUSB.

Result: 1. Boot attempt on Dell E521; same USB-Zip; no boot
          2. Tried on old Dell Inspiron 5100 Intel Pentium 4 CPU 2.40GHz 384MB RAM;it loaded!  VERY SLOW; desktop worked; doesn't connect to internet, times out.
              Re-booted, chose Check Disk For Errors, no errors found.
              Figured the laptop didn't have enough resources.

Back to Dell E521

Actions: 1. Made bootable DVD on the DVD-RW drive (Properties said it was working properly)
                Used Ubuntu-mate 18.04.5 with CDBurnerXP to burn. It said it was successful

Results:  1. Booted on the laptop but chugged and chugged and froze up on desktop; rebooted, chose Check Disk For Errors, no errors found.
                Figured not enough resources again.
             2. E521: F12> DVD-RW>enter
                Boots but doesn't load. Long error messages and suggestions about what to do; I don't understand it.

Here goes:

```
[   0.381341] .. MP_BIOS bug: 8254 timer not connected to IO_APIC
[   0.739823] do_IRQ:0.55 No irq handler for vector
[   0.819698] Kernel panic-not syncing:IOAPIC+timer doesn't work Boot with apic=debug and send a report. Then try booting with the 'noapic' option.
[   0.819749] CPU:0_PID:0Comm:swapper/0 Not tainted 5.4.0-42generic #46~18.04.1 Ubuntu
[   0.819792] Hardware name: Dell Dimension E521/0UW457, BIOS 1.1.4_12/09/12006
[   0.819835] Call Trace:
[   0.819884] dump_stack+0c60/0c86
[   0.819926] panic+0xa8/0x276
[   0.819967] check_timer_0x5a5/0x5db
[   0.820007] ? radix_tree_lookup+0xc/0x10
[   0.820049] ? irq_to_desc+0x14/0x20
[   0.820088] setup_IO_APIC+ox150/0x199
[   0.820128] apic_intr_mode_init+0x108/0x10f
[   0.820168] x86_late_time_init+0x1d.0x24
[   0.820208] start_kernel+0x428l/0x4e6
[   0.820248] i386_start_kernel+0x5l/0x53
[   0.820288] startup_32_smp+0x164/0x168
[   0.820336] --- [End kernel panic - not syncing:IO-APIC +timer doesn't work
! Boot with apic=debug and send a report. Then try booting with the 'noapic'option.]---

```
 So the kernel is in a panic and it has something to do with timing in the BIOS but I don't know what to do with the suggestions.

Getting closer but no cigar yet!   Learning things, that's good!  Any directions for me?  Many, many thanks!

---

### Post by CelticWarrior on 2021-02-25
```
[COLOR=#000000][ 0.819698] Kernel panic-not syncing:IOAPIC+timer doesn't work Boot[/COLOR]
[COLOR=#000000]with apic=debug and send a report. **Then try booting with the 'noapic' option.**[/COLOR]
```

If using the old BIOS boot then in the same screen where you're asked for language selection you should see an additional menu at the bottom with one of the options being F6. Inside there should be the 'noapic' option among others.

Is this your [Dell Dimension E521]("https://www.cnet.com/products/dell-dimension-e521-tower-athlon-64-x2-5000-plus-2-6-ghz-2-gb-320-gb-lcd-20-1/")? Yes, it's quite underpowered in current standards but should work with light DE variants like Ubuntu-MATE, Xubuntu or Lubuntu. Use 64-bit for continuity of usage, 32-bit is as good as dead at least in what concerns the Ubuntu family.

---

### Post by DuckHook on 2021-02-25
> **caseyatthebat said:**
> &#8230;Getting closer but no cigar yet!   Learning things, that's good!
An admirable sentiment. Most new users throw up their hands with extreme frustration when they run into problems as difficult as yours. Kudos to your good cheer and tenacity.

Perhaps you can try what the error message itself suggests:
```
&#8230;try booting with the 'noapic' option.
```
During the boot process, instead of letting GRUB automatically run through to the login screen, insert the *noapic* option into the kernel as a boot parameter. General instructions for adding boot parameters are here: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Old, but you can probably still get the general idea.

There's another hint in your error output which I've highlighted:
```
[   0.381341] .. **MP_BIOS bug**: 8254 timer not connected to IO_APIC
```
&#8230;so you can try upgrading your BIOS. I don't know anything about your MOBO so you would have to research how to do that on your own.

If you are feeling especially generous with your time and patience, you can also try booting with the debug option set, then send the log to the kernel maintainers, but this is a lot to ask of a newbie. ;-)

Perhaps best to forget about contributing back just yet and stick to solving the boot issue.

---

