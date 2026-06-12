---
title: "Dual-boot Windows on Ubuntu"
date: 2013-03-03
forum: New to Ubuntu
---

### Post by c5vetter on 2013-03-03
Okay, back drop - have Ubuntu 12.10 on a computer, as decided I did NOT like Windows 8. Well, I need to use Windows for my tax program. So, want to now dual-boot Windows 7 on the HP laptop that I completely wiped and installed 12.10 on. How do I accomplish this?

---

### Post by Sin@Sin-Sacrifice on 2013-03-03
You could use WINE to run the software or use virtualbox to run Windows and the software, which would be the easiest options, but if you must dual-boot, you can put the Windows install DVD in, reboot, follow the prompts to install Windows, wait forever, reboot and find that you can't get to Ubuntu because Windows Wrote over the MBR (master boot record). Therefore, grab your Ubuntu live disk and pop it in. Reboot and "Try Ubuntu." Once the desktop loads, open a terminal and type in "sudo mount /dev/sdx /path/to/mount/point" replacing sdx with the drive where your Ubuntu install is and /path/to/mount/point with the path to where you want to mount said drive. Then you want to change the root directory of the currently running OS. For that you just have to "sudo mount --bind /dev /path/to/ubuntu/mount/dev && sudo mount --bind /dev/pts /path/to/ubuntu/mount/dev/pts && sudo mount --bind /proc /path/to/ubuntu/mount/proc && sudo mount --bind /sys /path/to/ubuntu/mount/sys" and then "chroot /path/to/ubuntu/mount". Once there, you "grub-install /dev/sdx" and then "update-grub". Type "exit" to exit the chroot and then reboot. There you should see the familiar grub boot-loader but now with Windows as an option to boot. Unfortunately I know of no easier way.

---

### Post by darkcrimson on 2013-03-03
More often than not, the tax software you're running on Windows will have a web version available. If this is the case for your tax program, it will save you the hassle of Windows overwriting your MBR.

---

### Post by presence1960 on 2013-03-03
Some of those tax software web sites do not run on linux, such as turbo tax. Check yours out to see if the web based software will run on linux. If not you want to shrink a linux partition to create enough room for windows. Install windows. It is not such a hassle to reset the MBR to GRUB. You have boot-repair or can issue two commands from terminal in a Live CD/USB session to reset MBR to GRUB. Either way takes less than a minute...not a hassle in my book. If you need help with that post back.

---

### Post by darkcrimson on 2013-03-04
> **presence1960 said:**
> Some of those tax software web sites do not run on linux, such as turbo tax. Check yours out to see if the web based software will run on linux. If not you want to shrink a linux partition to create enough room for windows. Install windows. It is not such a hassle to reset the MBR to GRUB. You have boot-repair or can issue two commands from terminal in a Live CD/USB session to reset MBR to GRUB. Either way takes less than a minute...not a hassle in my book. If you need help with that post back.

You could get TurboTax running in WINE with much less effort (or virtualbox as stated above). I think most would find shrinking a partition, installing Windows, then repairing GRUB for the sake of a single program rather time consuming. I'd consider that a last resort in my humble opinion.
[URL="http://www.taxslayer.com/"]
TaxSlayer[/URL] works from a web app perspective on Ubuntu. If it's all the same, you could consider that as an alternative. However, I understand that most tax programs are used simply because they save last year's information (which I find rather convenient, myself.)

Forgive me for not asking sooner, but which program are you wanting to use?

---

### Post by c5vetter on 2013-03-04
Have been using TAX ACT for years. Only reason I have not used web-based, as wasn't sure if you could do 1040's or not? Thought web-based was mainly for 1040EZ filers? Also, can you do "multiple" returns on-line? I am the "tax man" for the family, so easy to download and install program on desk top and then reuse, and only pay for individual state filing.

Have NOT heard about TaxSlayer, and will check it out.

BTW - as I mentioned just got really frustrated with Windows 8 on new laptop. First tried to get Windows 7 PRO and Ubuntu to play nicely together and got frustrated with that. So, did a COMPLETE wipe of HDD and installed Ubuntu 12.10 and am happy. Just was wondering if I could do an install of Windows 7 PRO after the Ubuntu install.

---

### Post by verymadpip on 2013-03-04
Yes you can.

This may all be useless as I don't know what Windows 8 does to hard drives & such like.
I'd wait for more advice before trying my suggestion. (It has, however, worked for me IN THE PAST).

Make space for Win7 from Ubuntu Live CD/USB  ***Use Windows disk management to work on Windows partitions & GParted to work on Linux partitions***.  
Install Win7
Boot Ubuntu LiveCD/USB again
Open terminal & type:

sudo fdisk -l [This tells us which are your linux & Win7 partitions]
sudo mount /dev/sdxn /mnt [x=drive n=partition eg sda1 - yours may differ.  This mounts your Ubuntu partition]
sudo grub-install --root-directory=/mnt/dev/sdx [This installs GRUB - DO NOT INCLUDE PARTITION NUMBER]
Reboot into Ubuntu
sudo update-grub [Updates GRUB]
Reboot, hopefully with a pretty menu giving you the choice of which OS to boot.

---

### Post by c5vetter on 2013-03-04
Pip,

So, to make sure I get your thought process straight:

1. How do I get to Windows disk management to work on Windows? No Windows installed

2. Understand use GParted to set-up Linux partitions

3. Do steps you indicate, as far as installing Win 7

4. Boot Ubuntu LiveCD and open terminal and type text as you indicate

---

### Post by c5vetter on 2013-03-04
Crimson,

Checked out Taxslayer, in addition to TaxAct and Online Taxes, and all three will work with Firefox web browser, which is good.  All three have what is commonly referred as Premium or Ultimate packages, whereby you can do both federal and state returns on-line for around $20.00 per return.   As "family tax man", I have been using TaxAct as downloadable desktop package, because I could do multiple returns which included as many federal returns as I wanted to do up to five; just had to pay $7.95 per return for state of Maryland returns.   So, on-line looks like would need to setup an individual username for each return.   DECISION TIME!

Am thinking on-line maybe the way to go, as really no other need for Windows!

---

### Post by oldfred on 2013-03-04
Did you install Ubuntu in UEFI mode or BIOS mode. If Ubuntu is UEFI then you have gpt partitions and have to install Windows in UEFI mode also. It also need some special partitions in UEFI mode.

If Ubuntu is in BIOS mode then all the old instructions still apply. But you have the old MBR 4 primary partition limit and Windows has to install to a primary partition, formatted NTFS, with the boot flag. 

Somewhere I read the Windows was requiring vendors to not issue new drivers for Windows 7 to work with new Windows 8 systems. So if you have any new hardware features they may not work or new drivers will not be available. Some have installed Windows 7, but those may be early systems that did not have much in the way of hardware changes.

You did make a full backup of Windows 8 before erasing it?

---

### Post by verymadpip on 2013-03-04
c5vetter - 
Take good note of oldfred's advice re UEFI etc.  It's REALLY important advice.

If there's no Windows then don't sweat it, you can do any shrinking with GParted.
***IF***, at some point, you do need to shrink a windows partition use the Windows disk management tool (start > computer > manage > disk management) to avoid corruption & ruining Windows.

Other than that, you've understood my thought process accurately.
It does look like you aren't going to need Windows though, which is nice :)
(I keep Windows around to use as a big video game machine).

---

### Post by darkcrimson on 2013-03-04
> **c5vetter said:**
> Crimson,

Checked out Taxslayer, in addition to TaxAct and Online Taxes, and all three will work with Firefox web browser, which is good.  All three have what is commonly referred as Premium or Ultimate packages, whereby you can do both federal and state returns on-line for around $20.00 per return.   As "family tax man", I have been using TaxAct as downloadable desktop package, because I could do multiple returns which included as many federal returns as I wanted to do up to five; just had to pay $7.95 per return for state of Maryland returns.   So, on-line looks like would need to setup an individual username for each return.   DECISION TIME!

Am thinking on-line maybe the way to go, as really no other need for Windows!

Ultimately, we want you to be able to file your taxes without even having to consider installing a different OS (although we don't always get our cake and eat it too). There are a lot of good pointers here. If you end up compromising with the powers that be and go for another Windows install, you're all set with the instructions!

---

### Post by c5vetter on 2013-03-04
NO backup of Windows 8, so NO Windows environment present - am thinking will do some "tweaks" within the Ubuntu desktop and just enjoy - will worry about taxes next year, as this year (2012) already filed for the entire family!

---

