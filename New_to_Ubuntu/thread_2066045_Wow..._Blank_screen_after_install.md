---
title: "Wow... Blank screen after install"
date: 2012-10-03
forum: New to Ubuntu
---

### Post by trek186 on 2012-10-03
Hello!  Linux newbie here.  I'm having a bit of a problem with my Ubuntu install.  Maybe ya'll could help a clueless Linux user out?  I originally posted this over at Linux Forums, but I figured that also posting it here couldn't hurt.

I finally managed to get Ubuntu onto a spare IBM ThinkPad (a T60 1951-U58 ) so I could play with it. I installed the ISO for v12.04.1 onto a spare USB flash drive using Unetbootin, plugged it in, and went to town. 

The install looked like it went correctly (I asked it to format the drive and then install Ubuntu), and I was asked to reboot. I rebooted the laptop, and the IBM splash screen came on (so the BIOS appears to be fine), and then it flashed to a black, blank screen. Well, blank except for a little cursor at the top of the screen. I tried rebooting a couple of times, and the same thing. I let it sit for five minutes, and nothing. Pressing keys on the keyboard or touching the trackpad does nothing.

So any idea what is wrong or what I should do? I'm thinking that I should reconfigure the boot order to boot to the USB drive first, and then I can partition/reinstall again. My only fear is that I would just get the black screen again.

If it helps, I can always opt to install over with Ubuntu Server....

My first attempts at installing onto the drive via USB from another another computer (the live install thingie) sort of worked, so I know what I should be seeing upon a successful boot, but I am not seeing it here....

---

### Post by NikTh on 2012-10-03
Hi , 

I assume you downloaded and installed the Desktop Version of Ubuntu (not the server). 

When you see this blank screen and the cursor , press [Ctrl]+[Alt]+[F2] and try to login from there with your  Username & password. 

If login successfully , then give these two commands there 
```
sudo service lightdm stop 
sudo service lightdm start
```and see if login screen fired up. 

If not , then it will be useful to provide some info . From the LiveUsb open a terminal [Ctrl]+[Alt]+[t] and give this command 
```
sudo lshw -short -numeric
```post the results back here , BUT put the results between the brackets **[noparse]```
Here
```[/noparse]** so can be readable.

Thanks

---

### Post by trek186 on 2012-10-03
Just tried [Ctrl]+[Alt]+[F2] and nothing happened.  Still black screen and blinky cursor.

---

### Post by cyb0rgb0rg on 2012-10-03
I'm no expert on the specifics, I'm sure others will supply that, but my first thought is boot sector. To me, it doesn't seem to boot the OS. By the sound of it.

---

### Post by trek186 on 2012-10-03
Ok...  Just live-booted from USB.  I opened the terminal window and ran those commands, and this is what popped out (thank you for PDFs!):

```
brad@ubuntu1:~$ sudo lshw -short -numeric
[sudo] password for brad:
H/W path Device Class Description
=========================================================
system 195158U ()
/0 bus 195158U
/0/0 memory 144KiB BIOS
/0/6 processor Intel(R) Core(TM) Duo CPU T25
/0/6/a memory 64KiB L1 cache
/0/6/c memory 2MiB L2 cache
/0/6/0.1 processor Logical CPU
/0/6/0.2 processor Logical CPU
/0/b memory 64KiB L1 cache
/0/29 memory 1GiB System Memory
/0/29/0 memory 512MiB SODIMM DDR2 Synchronous
/0/29/1 memory 512MiB SODIMM DDR2 Synchronous
/0/1 processor
/0/1/0.1 processor Logical CPU
/0/1/0.2 processor Logical CPU
/0/100 bridge Mobile 945GM/PM/GMS, 943/940GML an
/0/100/2 display Mobile 945GM/GMS, 943/940GML Expre
/0/100/2.1 display Mobile 945GM/GMS/GME, 943/940GML E
/0/100/1b multimedia N10/ICH 7 Family High Definition A
/0/100/1c bridge N10/ICH 7 Family PCI Express Port
/0/100/1c/0 eth0 network 82573L Gigabit Ethernet Controller
/0/100/1c.1 bridge N10/ICH 7 Family PCI Express Port
/0/100/1c.1/0 wlan0 network PRO/Wireless 3945ABG [Golan] Netwo
/0/100/1c.2 bridge N10/ICH 7 Family PCI Express Port
/0/100/1c.3 bridge N10/ICH 7 Family PCI Express Port
/0/100/1d bus N10/ICH 7 Family USB UHCI Controll
/0/100/1d.1 bus N10/ICH 7 Family USB UHCI Controll
/0/100/1d.2 bus N10/ICH 7 Family USB UHCI Controll
/0/100/1d.3 bus N10/ICH 7 Family USB UHCI Controll
/0/100/1d.7 bus N10/ICH 7 Family USB2 EHCI Control
/0/100/1e bridge 82801 Mobile PCI Bridge [8086:2448
/0/100/1e/0 bridge PCI1510 PC card Cardbus Controller
/0/100/1f bridge 82801GBM (ICH7-M) LPC Interface Br
/0/100/1f.1 storage 82801G (ICH7 Family) IDE Controlle
/0/100/1f.2 scsi0 storage 82801GBM/GHM (ICH7-M Family) SATA
/0/100/1f.2/0.0.0 /dev/sda disk 120GB WDC WD1200BEVS-7
/0/100/1f.2/0.0.0/1 /dev/sda1 volume 110GiB EXT4 volume
/0/100/1f.2/0.0.0/2 /dev/sda2 volume 1012MiB Extended partition
/0/100/1f.2/0.0.0/2/5 /dev/sda5 volume 1012MiB Linux swap / Solaris parti
/0/100/1f.3 bus N10/ICH 7 Family SMBus Controller
/0/2 scsi6 storage
/0/2/0.0.0 /dev/sdb disk 1001MB SCSI Disk
/0/2/0.0.0/1 /dev/sdb1 volume 951MiB Windows FAT volume
brad@ubuntu1:~$

```

---

### Post by trek186 on 2012-10-03
> **cyb0rgb0rg said:**
> I'm no expert on the specifics, I'm sure others will supply that, but my first thought is boot sector. To me, it doesn't seem to boot the OS. By the sound of it.

That's what I'm thinking too.  But if I did a straight, perfect install from the ISO file, then should the BIOS be able to boot the HD?

---

### Post by cyb0rgb0rg on 2012-10-03
> **trek186 said:**
> That's what I'm thinking too.  But if I did a straight, perfect install from the ISO file, then should the BIOS be able to boot the HD?

Try re-installing grub to the mbr from the live usb.

---

### Post by trek186 on 2012-10-03
> **cyb0rgb0rg said:**
> Try re-installing grub to the mbr from the live usb.

Okay....  At this point I have zero idea what I am doing.  Let me see if I understand this:
1) Boot into LiveUSB, load GRUB installer.
2) GRUB does its thing, installs.
3) I reboot without the USB stick plugged in, and Ubuntu loads no problem.

I found what I think is what I need to download, located [Here]("https://launchpad.net/ubuntu/+source/grub-installer/1.68ubuntu5").  I'm not sure though.  And how do I extract the file?  Or is it similar to a Windows EXE once I get it into Linux?

---

### Post by thatguruguy on 2012-10-03
Wait a minute. Before messing with GRUB, you may want to read [this page]("http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it").

---

### Post by trek186 on 2012-10-03
I followed this guide here ([http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/](http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/)), and I at least now get a command line at boot saying "Invalid file" and "grub rescue>".  It doesn't do anything, but its something.

And none of the cases in the link you posted there seem to fit, except for testing the ISO.

It almost seems like Ubuntu was not installed to the hard drive or something.

Edit: I may as well just attempt a reinstall.  How do I force the computer to do a USB boot to the Ubuntu install screen instead of the LiveUSB environment?  Or are there terminal commands in LiveUSB mode which will reformat and reinstall Ubuntu to the HD?

---

### Post by NikTh on 2012-10-03
> **trek186 said:**
> **Ok...  Just live-booted from USB.**  
```
brad@ubuntu1:~$ sudo lshw -short -numeric
[sudo] **password for brad:**
H/W path Device Class Description
```

This is NOT Live-Usb session. 
And bellow are not the full results of command I asked. Id numbers are missing.Important.
> **trek186 said:**
> ```
=========================================================
system 195158U ()
/0 bus 195158U
/0/0 memory 144KiB BIOS
/0/6 processor Intel(R) Core(TM) Duo CPU T25
/0/6/a memory 64KiB L1 cache
/0/6/c memory 2MiB L2 cache
/0/6/0.1 processor Logical CPU
/0/6/0.2 processor Logical CPU
/0/b memory 64KiB L1 cache
/0/29 memory 1GiB System Memory
/0/29/0 memory 512MiB SODIMM DDR2 Synchronous
/0/29/1 memory 512MiB SODIMM DDR2 Synchronous
/0/1 processor
/0/1/0.1 processor Logical CPU
/0/1/0.2 processor Logical CPU
/0/100 bridge Mobile 945GM/PM/GMS, 943/940GML an
/0/100/2 display Mobile 945GM/GMS, 943/940GML Expre
/0/100/2.1 display Mobile 945GM/GMS/GME, 943/940GML E
/0/100/1b multimedia N10/ICH 7 Family High Definition A
/0/100/1c bridge N10/ICH 7 Family PCI Express Port
/0/100/1c/0 eth0 network 82573L Gigabit Ethernet Controller
/0/100/1c.1 bridge N10/ICH 7 Family PCI Express Port
/0/100/1c.1/0 wlan0 network PRO/Wireless 3945ABG [Golan] Netwo
/0/100/1c.2 bridge N10/ICH 7 Family PCI Express Port
/0/100/1c.3 bridge N10/ICH 7 Family PCI Express Port
/0/100/1d bus N10/ICH 7 Family USB UHCI Controll
/0/100/1d.1 bus N10/ICH 7 Family USB UHCI Controll
/0/100/1d.2 bus N10/ICH 7 Family USB UHCI Controll
/0/100/1d.3 bus N10/ICH 7 Family USB UHCI Controll
/0/100/1d.7 bus N10/ICH 7 Family USB2 EHCI Control
/0/100/1e bridge 82801 Mobile PCI Bridge [8086:2448
/0/100/1e/0 bridge PCI1510 PC card Cardbus Controller
/0/100/1f bridge 82801GBM (ICH7-M) LPC Interface Br
/0/100/1f.1 storage 82801G (ICH7 Family) IDE Controlle
/0/100/1f.2 scsi0 storage 82801GBM/GHM (ICH7-M Family) SATA
/0/100/1f.2/0.0.0 /dev/sda disk 120GB WDC WD1200BEVS-7
/0/100/1f.2/0.0.0/1 /dev/sda1 volume 110GiB EXT4 volume
/0/100/1f.2/0.0.0/2 /dev/sda2 volume 1012MiB Extended partition
/0/100/1f.2/0.0.0/2/5 /dev/sda5 volume 1012MiB Linux swap / Solaris parti
/0/100/1f.3 bus N10/ICH 7 Family SMBus Controller
/0/2 scsi6 storage
/0/2/0.0.0 /dev/sdb disk 1001MB SCSI Disk
/0/2/0.0.0/1 /dev/sdb1 volume 951MiB Windows FAT volume
brad@ubuntu1:~$

```

Are you sure that you installed Ubuntu in HDD and not in Usb ?

---

### Post by gertcher on 2012-10-04
I am having very similar problems, see [my thread.]("http://ubuntuforums.org/showthread.php?t=2066116")

If two of use fairly close in time are have similar problem loading Ubuntu it goes without saying there are others having problems and lots of them will not be reporting their problems to a user group.

This is a BIG problem for Ubuntu and Linux in general. Linux, as an operating system is thought by some at best clunky and not a proper OS and at worse a joke to be avoided. If some new user are being put of by failed installs the clunky joke will be propagated.

I, for one, am very tolerant of these sort of glitches, and will perceiver. But, I don't have time to mess about trying to fix something even before it is loaded.

I am using Win XP Pro on 3 comps, and I have one laptop with Win 7. I am in no rush to move to Linux, XP will be supported for another 2 years. I tried Ubuntu 12.00 some time ago and felt it was not ready. Mybe this version is also not ready enough. I don't mind waiting a bit longer for the current beta to go live.

I have been a Windows user since DOS, and worked my way along through all its variants. I must have had a few bad expirences loading these OS but I cannot remember a point where I have loaded it and got nothing at the end of it.

It is essential for Ubuntu/Linux to gain the confidence of the new, and most likely entrenched user, that  they get the install to work 100%

---

### Post by Noor1101 on 2012-10-04
Hi! 
I had the [exact!] same problem, and [this thread]("http://ubuntuforums.org/showthread.php?t=1976628") (wilee-nilee's reply in particular) fixed it for me. It seems the settings about from which disc to boot weren't correct.
I hope this will help you too! And others :)

Good luck,
Regards
Noor

---

### Post by NikTh on 2012-10-04
> **gertcher said:**
> I am having very similar problems, see [my thread.]("http://ubuntuforums.org/showthread.php?t=2066116")

If two of use fairly close in time are have similar problem loading Ubuntu it goes without saying there are others having problems and lots of them will not be reporting their problems to a user group.

This is a BIG problem for Ubuntu and Linux in general. Linux, as an operating system is thought by some at best clunky and not a proper OS and at worse a joke to be avoided. If some new user are being put of by failed installs the clunky joke will be propagated.

I, for one, am very tolerant of these sort of glitches, and will perceiver. But, I don't have time to mess about trying to fix something even before it is loaded.

I am using Win XP Pro on 3 comps, and I have one laptop with Win 7. I am in no rush to move to Linux, XP will be supported for another 2 years. I tried Ubuntu 12.00 some time ago and felt it was not ready. Mybe this version is also not ready enough. I don't mind waiting a bit longer for the current beta to go live.

I have been a Windows user since DOS, and worked my way along through all its variants. I must have had a few bad expirences loading these OS but I cannot remember a point where I have loaded it and got nothing at the end of it.

It is essential for Ubuntu/Linux to gain the confidence of the new, and most likely entrenched user, that  they get the install to work 100%

In which  way this post is helpful to the user who has installation problems ?

---

### Post by offgridguy on 2012-10-04
Very interesting thread.

---

### Post by gertcher on 2012-10-04
> **NikTh said:**
> In which  way this post is helpful to the user who has installation problems ?Who said anything about it being useful.

I made a broad statement about Ubuntu/Linux needing to be more polished. If you get a new car and the key will not open the doors, you are not expected to learn how to get in via a different route. After all, the ISO disc is a turnKEY. If that does not work why should anyone bother to find out how to get around it.

I am not saying Ubuntu/Linux is good or bad, for me it is just not polished enough.

I am not subscribing to this thread any longer.

I appreciate everyone's efforts

Regards  Greg

---

### Post by NikTh on 2012-10-04
> **gertcher said:**
> Who said anything about it being useful.

I made a broad statement about Ubuntu/Linux needing to be more polished. 

Ubuntu Testimonials and Experiences forum , is here : [http://ubuntuforums.org/forumdisplay.php?f=103](http://ubuntuforums.org/forumdisplay.php?f=103)

---

### Post by cway00 on 2012-10-04
> **gertcher said:**
> Who said anything about it being useful.

I made a broad statement about Ubuntu/Linux needing to be more polished. If you get a new car and the key will not open the doors, you are not expected to learn how to get in via a different route. After all, the ISO disc is a turnKEY. If that does not work why should anyone bother to find out how to get around it.

I am not saying Ubuntu/Linux is good or bad, for me it is just not polished enough.

I am not subscribing to this thread any longer.

I appreciate everyone's efforts

Regards  Greg

You have reasons to say what you want based on your own understanding but that does not mean that the solution to your answer is no there .. 

Everyone had their first install at one certain time in life ..so guess no one gave you want does not mean that you cant give help to others and your did not give details about your driver info. 

here is a solution to solution to most of the blank screen after install :
```
http://ubuntuforums.org/showthread.php?t=2048984
```

Hope it solves your problem

---

### Post by Crafty Kisses on 2012-10-04
In the spirit of experiment, what are the results of 
```
sudo dpkg --configure -a
```
You can just try to change the permissions and then try booting back into recovery again and running the dpkg command again. That might work.
```
sudo apt-get -f install
sudo dpkg-reconfigure nautilus
```

---

### Post by trek186 on 2012-10-05
Ok, well I think I found what went wrong.  I should have kept the USB drive in while I was rebooting.

I reflashed the Ubuntu ISO onto the flash drive via my Win 7 laptop, and then reinstalled Ubuntu on the other laptop.  Bam.  Went perfectly, setup completed after reboot, and I can now boot from the hard drive.

Thanks all for the help.  Next thread: How the frak do I install applications? :)

---

### Post by cway00 on 2012-10-06
> **trek186 said:**
> Ok, well I think I found what went wrong.  I should have kept the USB drive in while I was rebooting.

I reflashed the Ubuntu ISO onto the flash drive via my Win 7 laptop, and then reinstalled Ubuntu on the other laptop.  Bam.  Went perfectly, setup completed after reboot, and I can now boot from the hard drive.

Thanks all for the help.  Next thread: How the frak do I install applications? :)

here is a basics of installing..removing and upgrading applications on ubuntu 12.04 ..```
http://www.howtogeek.com/63997/how-to-install-programs-in-ubuntu-in-the-command-line/
```

---

### Post by cyb0rgb0rg on 2012-11-04
OP, mark as solved?

---

