---
title: "Total Newbie needs installation help"
date: 2013-03-05
forum: New to Ubuntu
---

### Post by vineyridge on 2013-03-05
After about six months of thinking about it, I've finally decided to take the Linux plunge with Ubuntu.  But before I start, I'd like to put my system up for comment and help suggestions.  I've got the Ubuntu Manual and have read the installation section, but it doesn't address things in detail.

I currently have Windows XP, SP3 32 bit installed.  One reason I'm delving into Linux is that MS is going to quit supporting XP next year, and I want an alternative that is not MS.  So in a year, I'll be exclusively Linux but in the meantime I'll be dual booting.

Motherboard is Asus P5G41-M; Processor is an Intel Core 2 Duo E7500 @ 2.93GHz  Wolfdale 45nm Technology, but I'm thinking of upgrading to a Core 2 Quad or Quad Extreme (used).   I do not know if these are 64 bit capable, but since the motherboard is Windows 7 Ready, I would hope it and the processor would be.  I have not yet googled for the actual specs.  On the processor, hyperthreading (whatever that is) is not supported.

Memory is 4g of Dual Channel DDR2@400mhz.  If I were to install the 64 bit Ubuntu, I would also add memory to max out the system at 8g.

I currently have two HDs.  One is a 250G that is partitioned into a 115G with the Windows Operating System.  The other 110G is raw and has not been formatted.  The other HD is a 500G empty NTFS formatted that could easily be partitioned and each reformatted into any file system.

I know that Linux has its own file discrete file systems but also that Ubuntu works with NTFS.  

So here are my questions.  Since I have already got a partition for Ubuntu that present but not formatted, how would I go about installing Ubuntu there?  Dual boot seems to be built into Ubuntu, so would there be a problem with that if the partition involved was formatted for Linux?  On the second HD, should I just leave it NTFS, or should I partition it also into NTFS for Windows use and have another partition for the Linux file system?

Should I get the 64 bit or the 32 bit Linux?

Advice is greatly appreciated because I would like to have the most efficient Linux system possible, and I would like to do this correctly from the getgo.  After this gets answered, if it does, I'll have some more Hardware questions.

---

### Post by mamamia88 on 2013-03-05
Well 32 bit should be fine. Don't really see the need for more than 4gb right now.  I would just format the unformatted space during install to ext4 and use mount point / and save a few gb and use that as swap.   It's really not very complex.  Formatting is probably the most difficult part of installing ubuntu and they make it super easy on the uninstaller.

---

### Post by Cheesemill on 2013-03-05
I would go for 64-bit.

There is absolutely no reason not to use the 64-bit version if your hardware is capable of running it (it is).

For the most trouble free installation I would unplug all of your hard drives except the one you wish to install Ubuntu to, then run the installation and select 'use the entire drive'. Once Ubuntu is up and running you can plug the other drives back in and set up grub (the Ubuntu bootloader) to dual boot with your Windows installation.

This method ensures you don't accidentally overwrite any of your other drives.

Can you give us the details of your graphics card please. Knowing this will let people suggest the most appropriate version of Ubuntu to install.

---

### Post by papibe on 2013-03-05
Hi vineyridge. Welcome to the forums ):P

> **vineyridge said:**
> Motherboard is Asus P5G41-M; Processor is an Intel Core 2 Duo E7500 @ 2.93GHz  Wolfdale 45nm Technology,...

Memory is 4g of Dual Channel DDR2@400mhz....

That would work well with Ubuntu 32b and 64b.

> **vineyridge said:**
>  I currently have two HDs.  One is a 250G that is partitioned into a 115G with the Windows Operating System.  The other 110G is raw and has not been formatted.  The other HD is a 500G empty NTFS formatted that could easily be partitioned and each reformatted into any file system.
Although Ubuntu can work with NTFS, it needs to boot from a Linux filesystem. In the installation process you'll need to format that 110Gb partition to something like ext4 to properly install Ubuntu on it. You can leave the other disk as NTFS and share data between both OSes.

> **vineyridge said:**
>  Should I get the 64 bit or the 32 bit Linux?
Both would be valid options. It's debatable which one its better, but I would go 64b.
> **vineyridge said:**
>  Advice is greatly appreciated because I would like to have the most efficient Linux system possible, and I would like to do this correctly from the getgo.  After this gets answered, if it does, I'll have some more Hardware questions.
Since you have the budget to upgrade, I'd recommend investing on a graphic card instead:
[LIST]
[*]Later versions of Ubuntu are more graphic intensive (although you can go with something less intensive like Xubuntu).
[*]You would need it to play HD video.
[*]If you are interesting on some gaming (Steam, Humble Bundle), the experience would be greatly improved.
[/LIST]
Hope that helps. Come here often and have fun.
Regards.

---

### Post by mörgæs on 2013-03-05
> **vineyridge said:**
> ...I would like to have the most efficient Linux system possible

Then go for Xubuntu or Lubuntu. You don't need extra hardware.

Remember to test the system in a live boot as a first step.

---

### Post by coldraven on 2013-03-05
> I currently have two HDs.  One is a 250G that is partitioned into a 115G  with the Windows Operating System.  The other 110G is raw and has not  been formatted.  The other HD is a 500G empty NTFS formatted that could  easily be partitioned and each reformatted into any file system.


If you intend to do the install with both drives attached you should first boot with a Live CD and investigate your drives.
Use the "Try Ubuntu" option and find the "Disc info" utility.
This link will tell you more [https://help.ubuntu.com/8.04/installation-guide/i386/device-names.html](https://help.ubuntu.com/8.04/installation-guide/i386/device-names.html)

Make a written note of your drive names /dev/sda1 , /dev/sda2 etc. so that you do not overwrite any of your data.

A better idea as suggested above is to **remove the Windows drive** so that you can safely experiment with the other one.
You could then boot with a Live CD in "Try" mode, install Gparted and partition the 500GB drive how you like.
I would start by deleting the existing partition.
Then create a 50Gb primary partition (Formatted Ext4) for the operating system
Then a secondary partition (formatted Ext4) to fill all but 10Gb for your data and a swap partition in the remainder. (Formatted as Swap)

Gparted is fairly simple to use and nothing will actually happen until you click "Apply" on the top menu. This makes it easy to undo your changes and generally experiment with the options

When you come to do the real install you just tag the first partition as root by entering a "/".
The second as home by entering "/home" and the third will have already been formatted as swap and should just appear as such.
This is easier to do than to explain.

I have to sleep now, I will check your progress tomorrow. Have fun!

---

### Post by vineyridge on 2013-03-05
Thanks for the advice.  So far I'm still in the preparation stage, but was already planning to use a Live CD for learning.  I think Lubuntu would work quite well with my very old (2000) IBM Thinkpad 600x with a 25G HD; but I do know with that one that the old CD-ROM drive presents a problem, so  that's going to be a later migration project.

If I can run the standard Ubuntu, would there be a reason why I would want to go with a different flavor?

I do not have a separate graphics card, but am using the integrated video and audio that came with the motherboard.  Board has an Intel G41 chipset with and the graphics come from Intel GMA X4500.  I have an PCI Express x 16 slot available for a graphics card, so suggestions would be appreciated.  I'm not really much of a gamer, but I have noticed some slow redrawing in some that I have tried.

Other Hardware to consider:  
External HDs
old 180 G WD Dual Media Center using USB (NTFS)
1 T WD My Book Essential 2.0 (USB)  I save mostly to this drive.  All my work is here, not on the internal drives.
500G Toshiba Canvio USB 
I swap the Toshiba and the Media Center between the desktop and the laptop.

Printers:
Kodak ESP All in One 2150 inkjet.  This is also my only scanner, copier, and also has a fax.
Samsung CLP 315 AXX.  
Both are USB.  I swap the Samsung between the desktop and the laptop

Keyboard--generic Dell clicky type with a PS2 connector
Mouse/Mice--Very OLD Logitech Vista Trackball which is using the generic Windows MS driver because I can't seem to find Logitech software that will work and restore the extra button functionality. PS2 Connector.  I also have in reserve a Logitech Trackman Marble Wheel (USB connector) and a Logitech Marble FX (PS2 connector).  Both would be using the generic driver.  I still have the installation CDs for the latter, but I'm not sure if they would work with XP Pro, SP3. 
Old Starlogic (cheap) CRT monitor that uses generic MS Windows drivers.  I still have the documentation, but forget offhand what it's capable of.  I usually run 1240 x 1024 at 60 hz.

Since I do not have data on the internal drives, I'm not too worried about losing what I have.  Since my original Windows internal HD drive wouldn't boot because of damaged sectors, what I have now is very new and expendable.  Eventually, I hope to clone the damaged drive onto another 500 G and install it in the computer.  That one does have things that I need.  Naturally the back-up software that I was using didn't work to restore the partition images, so I'm basically at square two with what I am using now.  Both HDs are new with very little on them.

I use Open Office for my Office Suite.

My original thought was to use the unformatted 110G partition on the Windows OS drive for Ubuntu and also partition the 500G into an NTFS side and a Ubuntu side, but if I can boot from the second drive, I might just use the whole drive for Ubuntu and format the other half of the Windows Drive to NTFS.

---

### Post by papibe on 2013-03-05
> **vineyridge said:**
> If I can run the standard Ubuntu, would there be a reason why I would want to go with a different flavor?
This is a matter of personal preference. It will depend on how do you put value on easy to use, performance and personal taste.

Without a dedicated graphic card, Xubuntu will be very noticeable faster, though.
> **vineyridge said:**
> I have an PCI Express x 16 slot available for a graphics card, so suggestions would be appreciated.
I'd recommend an Nvidia card. I've read good reviews on the 550Ti card. I would upgrade my 9500 to that, If I had the budget.

Regards.

---

### Post by vineyridge on 2013-03-05
I just went to the Xubuntu site and saw nothing about Live CD.  Is that an option with Xubuntu?

---

### Post by pqwoerituytrueiwoq on 2013-03-05
> **papibe said:**
> This is a matter of personal preference. It will depend on how do you put value on easy to use, performance and personal taste.

Without a dedicated graphic card, Xubuntu will be very noticeable faster, though.

I'd recommend an Nvidia card. I've read good reviews on the 550Ti card. I would upgrade my 9500 to that, If I had the budget.

Regards.

I have a 550 ti and it works great though it has been obsoleted by the gtx 650
only complaint is it does not run heaven 4.0 worth a crap it does ok on 3.0
it is a gpu benchmarking program


xubuntu has a live cd/dvd, all *buntu variants do
[http://cdimage.ubuntu.com/xubuntu/releases/12.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/12.10/release/)
you could just go and try the 13.04 alpha release, i have had good luck with it, my main 12.10 install is a 13.04/12.10 hybrid
[http://cdimage.ubuntu.com/xubuntu/daily-live/current/](http://cdimage.ubuntu.com/xubuntu/daily-live/current/)

---

### Post by papibe on 2013-03-05
The installation CD/DVD gives you several options, and one of them is "Try (X)Ubuntu without installing ...", that is what we called "Live" ;-)

Regards.

---

### Post by vineyridge on 2013-03-05
This is kind of off point, but apparently this ATX motherboard only has a PCI Express 1.1 capability.  Would that change any graphics card recommendations.  And I haven't checked my power supply yet to see what it can handle.  Given that I don't game, I'd rather not have to replace the Power Supply.  The onboard Intel graphics suck, though.

---

### Post by papibe on 2013-03-05
As long as it is a PCI Express x16 it doesn't matter. All cards are backwards compatible. Note that x16 is important though, as it is an specific "size".

Good point about the power supply. In case you don't have enough power for a, let's say, 550, you may look for a lower end card like an Nvidia 610, or 620.

A typical 610 requires a 300W power supply which would work on most desktops.

Regards.

BTW, PSUs are not that expensive, and also are not complicated to replace. A few moths ago, my 310W original Dell PSU died. I went to Microcenter, bought a 450W for about $40, and problem solved (it was either an Antec or a Cool Master).

---

### Post by mastablasta on 2013-03-06
> **vineyridge said:**
> Printers:
Kodak ESP All in One 2150 inkjet. This is also my only scanner, copier, and also has a fax.
Samsung CLP 315 AXX. 
Both are USB. I swap the Samsung between the desktop and the laptop


samsung probably needs proprietary drivers. there is a PPA from a nice guy that modified and patched the drivers tso they work well in Ubuntu and debian. easy to install. for the rest i don't know. you need to test it first (maybe with live session). know this that in linux many drivers are inclouded in kernel (core of the OS). when computer botos hardware is read and appropriate drivers are loaded (hopefully). sometimes system missreads the hw and then you need to order it what drivers to use. no biggy, just a few chnages to config files and you will be done if that happens.

sometimes however there are no linux drivers available (thanks to manufacturers).

> 
My original thought was to use the unformatted 110G partition on the Windows OS drive for Ubuntu and also partition the 500G into an NTFS side and a Ubuntu side, but if I can boot from the second drive, I might just use the whole drive for Ubuntu and format the other half of the Windows Drive to NTFS.

i do not understand why no one gave advice on this idea. 

this is easy to do. all you need is raw space (you already have that) and Ubuntu installer will take care of the rest. oyu only need to tell it to install to largest free space. select the prefered file format or leave it at default. it will automaticly create /swap and / (root) partitions. boot loader will also be propperly put and you should see both systems avaiable on boot. if you intend to continue using XP then leave the second drive NTFS formated. ubuntu does well with 10-15GB of disk space. 30 GB is almost overkill for it. but if you intend to keep data on linux and eventually move fully to linux then it is better to format the second disk to linux format. but this is not necessary. linux can read NTFS format just fine, but windows doesn't read so well the ext format and other formats.


i plan to do somehting similar only i will keep windows for some older games and those i haven't had the time to play yet. but will probably give 20GB to linux which should be more than enough. unless i change my mind again and go with win7. 

anyway do a lot of testing try a few different version of Ubutnu before you go for it. i am enjoying Kubuntu. But Xubuntu is also great.

edit: you asked why run something else. you also asked for most efficient. well consider this - the version  mentioned run various desktop environemtns. there are also some widnows managers available. you can use 300MB ram for system+with 3D effects some GPU power or you can run something that looks like win98 with modern 2013 programmes and use only 80MB ram and no GPU power (no special desktop effects). the choice is yours and often comes prepackaged in various distributions. so while lubuntu might not look as shiny as Ubutnu it uses a lot less system resources by default.
however with your system it shouldn't be an issue. the Kubuntu i run is running on 1.3GB ram and old dual core celeron.

---

### Post by vineyridge on 2013-03-06
So here is the start of this plan.  Tonight in the wee hours, since I'm on satellite and need to preserve my usage, I'll download Kubuntu, Ubuntu, Xubuntu and Lubuntu and burn them to DVD.  Then I'll start playing with them as Live CD.  I'll give each one a week's trial and decide on my flavor.  

On the video front, I've just ordered the Nvidia 620.  Had to make sure that the card I ordered supported VGA connection.  This is one upgrade that really makes sense to me.

I grew up with the mantra:  "Use it up, wear it out, make it do, or do without."  So as long as the old stuff still works (monitor, laptop, trackballs, external), I'll keep them in service.  I still have a functional but tiny HD for the laptop that runs Win98SE.  I loved that OS.  I waited many years before switching to XP.

---

### Post by mörgæs on 2013-03-06
You could also install each version on a USB stick.

---

### Post by vineyridge on 2013-03-06
Well, this is interesting.  Kodak does not support Linux, or so their help chat person says.  There are no manufacturer's drivers available for the ESP All In One 2150.  Unless there is a Linus/Ubuntu driver for this machine, I'm going to lose the printer, the scanner, the fax and the copier.

Is there a particular place to go to find out what hardware does/will work?  I need to know what printers and scanner will work if I have to buy new hardware. And if I do, you can be sure it won't be Kodak.

I already have plenty of DVD disks, and I don't have a legion of USB sticks.

---

### Post by Cheesemill on 2013-03-06
For printers you can use this site...
[http://www.openprinting.org/printers](http://www.openprinting.org/printers)

For scanners you can use this site...
[http://www.sane-project.org/sane-supported-devices.html](http://www.sane-project.org/sane-supported-devices.html)

I've had great results with HP devices, they have a team who works on Linux support for their hardware.
You can see how well supported a certain device is by looking on the HP Linux Imaging and Printing site (hplip is also the name of the Linux driver).
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

I recently needed a new AOI device, a quick check of the HP website led me to buy an HP DeskJet 2510 for all of £25 (on special offer at PC World).
Plugged it in and turned it on and everything worked out of the box without any effort on my part at all, printing and scanning.

---

### Post by vineyridge on 2013-03-07
Just wanted to let y'all know that I am now on a Xubuntu Live Disk.  I also have three more flavors to try.  This looks like its going to be fun.

---

### Post by oldrocker99 on 2013-03-07
Don't forget that there are other desktop environments besides Unity, KDE, LXDE, and XCFE. You may like Openbox, or razor-qt, or Cinnamon, or MATE, or GNOME, or...

Remember that the true blessing of free software isn't the free price. It's the FREEDOM.

---

### Post by mastablasta on 2013-03-08
> **Cheesemill said:**
> I've had great results with HP devices, they have a team who works on Linux support for their hardware.
.


yes HP has good linux support. and they make good printers as well.

samsung printers are also supported, though their linux support is not as commited as HP's. as i said above a PPA can solve samsung compatibility easilly. the only reason i bought a samsung is because it fit on the table (it was smaller than HP with same price). i use it on XP maschine but all linux mashcines connected to it can print on it.

---

### Post by 3rdalbum on 2013-03-08
Just because Kodak doesn't support Linux, doesn't mean there are no Linux drivers for your printer/scanner. Just try adding the printer on the Printing program and see if it works.

---

