---
title: "Tip: Ubuntu 7.04 on Asus M2A-VM HDMI: boot options I used"
date: 2007-05-06
forum: Outdated Tutorials &amp; Tips
---

### Post by felker2 on 2007-05-06
Hi,

This is how I got (k)buntu 7.04 32-bit working on my Asus M2A-VM HDMI mobo with AMD 690G chipset (further specs: Athlon64 X2 3600+, 4GB RAM and a SATA drive): it's all in the boot options. Without these boot options, (k)ubuntu halted during the boot process.
Thanks to ArjanW for the tips.

Disclaimers:
1) if your (k)ubuntu runs on your M2A-VM / AMD 690G without problems and does not need options, you won't need all this
2) I found the boot options by trial-n-error. I can't explain nor support them. Comments very welcome!


Short: apparantly the boot options "pci=nomsi irqpoll noapic acpi=off" (always without the quotes) are needed on my system. Maybe less boot options are needed, but this is what worked for me.

Long: the boot options are needed in three different phases of the install:

1) booting the Live CD: immediatly after booting, in the first screen press F6 and add the "pci=nomsi irqpoll noapic acpi=off" to the end of the line. Then press ENTER. The Live CD should now boot and you can install to the hard disk and later reboot.

2) at the first boot from the harddisk, when you see GRUB, press ESC, then e to edit the first boot option, press the cursor down key to go the line which says "kernel .. vmlinuz" and press e again. Then, at the end of the line type the boot options again: "pci=nomsi irqpoll noapic acpi=off". Press ENTER and then b to boot from the harddisk. (k)ubuntu should now boot from the hard disk

3) After (k)ubntu is completely operational, make the boot options permanent in /boot/grub/menu.lst . Use 'sudo' plus an editor (kate, gedit or vi) to put the boot options into /boot/grub/menu.lst at the end of the line with first appearance of "kernel /boot/vmlinuz".

So

```

sudo kate /boot/grub/menu.lst

```

and then add the boot options (given in **bold** below). Warning: you have to scroll to the right in the window below to see the boot option!

```

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=82efad91-9c28-4d6d-9f7a-ae83a90eeaa1 ro quiet splash **pci=nomsi irqpoll noapic acpi=off**
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault


```


Save & Exit from the editor and you should be OK: the next time you boot (k)ubuntu everthing should be OK with these boot options.

This is what worked for me. Once again: I can't support this. Tips welcome. HTH.

---

### Post by fdkuyper on 2007-05-10
Thank you very much! 

My Ubuntu crashed every time I tried. I  tried to change some simple options, like changing the screen resolution, but I would have never managed to find these settings.

After following your instructions I was able to install Ubuntu! This is the first thing I am doing with it, is writing this. :D 

After this I will try to make it work as a media center with [Linux MCE]("http://www.linuxmce.com/")

Thanks again!

---

### Post by fdkuyper on 2007-05-12
It turns out that you have to use Ubuntu 6.10 for Linux MCE.

So, now I'm trying to get 6.10 installed: but here your solution doesn't work unfortunately :(

Somehow the boot options seem to help, because without them the system holds earlier with an error about a pci device (have to write it down still). 
With the boot options the Ubuntu logo appears, and the orange progress bar, but this is as far as it gets.

Do you have any suggestions how to boot Ubuntu 6.10 on a M2A-VM board :??

Edit: I got it working now! I removed the 'quiet' option from the boot line, so I could write down exactly where it went wrong. It turns out it didn't go wrong, booting was just 10 times slower than the 7.04 version. Dropping the 'quiet' option made clear the boot sequence was still continuing.  So in the end the boot instruction do work both for 7.04 and 6.10. Thanks again, and I will try to get the Linux MCE working :)

---

### Post by manolito1998 on 2007-05-12
Hello, and thanks for your post,

I'm trying to do the same like fdkuyper, install the linuxmce in a HTPC. With your command I'm able to install ubuntu, but the problem is that the USBs are not up, so I can't use my wireless neither  any device under USB.

Do you know how to solve this problem??

Thank you very much and sorry for my poor english

---

### Post by fdkuyper on 2007-05-17
Hello manolito1998: do you know if your usb-ports are connected in the right way? Because I had no problems using them. I have a USB mouse and keyboard, and they work just fine - right from the start. Do you have an other OS to see if the USB ports are working?

You could also check your BIOS settings, there are some where you can enable or disable the USB ports.

---

### Post by dwbell on 2007-06-01
Does anyone have the tv out add on card working with the Asus M2A-VM HDMI?

---

### Post by BioN on 2007-06-05
I am interested to know if the addon card works also as I have this board ready to be setup as a mythtv box but want to make sure all hardware is compatible first.

---

### Post by nfoti on 2007-06-05
HI, I have this motherboard and I'm attempting a mythtv install - Thanks for the help posted above in getting ubuntu to install - however,

I'm having major video issues with this machine:
ASUS M2A-VM AMD 690G ATI600SB ATI X1200.

I could not get video to playback reasonably well with the on-board ati video card - even installed the newest proprietary driver. So I chalked this up to ATI's drivers being sub-par. Next I threw in a nvidia geforce 7300 pci-e card i had lying around - did a fresh ubuntu feisty install, installed the nvidia drivers - and the video looks just as bad.

My question is - is anyone else having these video playback problems?

My video is choppy at best, any input from anyone with this board would be greatly appreciated.

BTW. - I wasn't aware that this board had a tv add on option, I know you can order the SPDIF out connector separately and it does work for digital audio.

---

### Post by Ekorre on 2007-06-12
I have installed both Ubuntu 7.04 and Kubuntu on my Asus M2A-VM HDMI (several times because I'm very new to linux). I managed this without any Boot options. My only problem was that no installation CD would boot correctly when I used only the DVI-port (x-server error at the end of the boot sequence).
If I connected both DVI and VGA, both screens worked without problems. I also tested to boot connecting to the TV through SVHS, this works as well.
Has anyone been able to boot this card with only the DVI-port connected?

---

### Post by bobtins on 2007-06-12
Thanks for the tip--I've got the same board and those options got me through the install. However, I ran into a very nasty problem later on--when I did some major MySQL access, my screen would get corrupted (it was in text mode, and little spots showed up all over) and the system hung completely. I don't know if it's something about the state of the drivers for this motherboard, or something wrong with my memory. I posted this at [http://ubuntuforums.org/showthread.php?t=471505](http://ubuntuforums.org/showthread.php?t=471505)

---

### Post by OliverKurz on 2007-06-26
Hello,
I also had the mentioned problems booting up an Ubuntu Installation.
So I also tried with these boot settings and it worked.

The thing is, I don't need any of these additional boot settings (just ubuntu default) when I disable
the HPET option in BIOS.
I have BIOS version 502.
Maybe this also works out for other setups.

---

### Post by mohasr on 2007-06-26
> **OliverKurz said:**
> Hello,
I also had the mentioned problems booting up an Ubuntu Installation.
So I also tried with these boot settings and it worked.

The thing is, I don't need any of these additional boot settings (just ubuntu default) when I disable
the HPET option in BIOS.
I have BIOS version 502.
Maybe this also works out for other setups.

i can confirm this as well , my mobo is asus m2a-vm [not hdmi] and by disabling the HPET option from the bios I can boot with the default kernel parameters.

other than that I need to at least append acpi=off in order to boot .

---

### Post by JumpyLINUX on 2007-07-15
> **nfoti said:**
> 
My question is - is anyone else having these video playback problems?


You are not alone with this problem. I too have a M2A-VM HDMI motherboard and I can not play a single video file.

---

### Post by JumpyLINUX on 2007-07-15
> **Ekorre said:**
> 
Has anyone been able to boot this card (M2A-VM HDMI ) with only the DVI-port connected?

I'm quite surprised since my I did not have any problems booting my computer.

I have M2A-VM HDMI and I used the Kubuntu 7.04 AMD64bit DVD through a Lite-on IDE(not SATA) DVD drive. I did not even have to change any boot settings. Also I the DVD-D connector of the motherboard.

---

### Post by phillfri on 2007-08-05
I have the Asus V3-M2AVM HDMI barebones system and so far have tried installing linux on it using PCLOS 2007 and Fedora 7. F7 LiveCD wouldn't even boot. PCLOS 2007 boots, but only with acpi=off option.

My question is, what are we doing by turning acpi=off? How does this affect motherboard capabilities? I've been trying to google this question, but I'm not getting very far. I've gotten some info that acpi is in fact needed for dual core processor issues? What else might be affected by turning it off?

I've also read that one needs at least the 2.6.21.x kernel for this motherboard to operate correctly?

Also, does anyone know  if this motherboard is the same as the Asus M2A-VM HDMI motherboard? I read elsewhere that someone needed to upgrade his M2A-VM HDMI bios to version 1001 to get rid of the acpi=off issue, but this bios is NOT listed under the V3-M2AVM HDMI barebone system as an upgrade.

Any comments would be appreciated :>)  I bought this board to build a MythTV box that will do additional duty as my home Skype phone system server and a late night backup box for my other pcs. But so far I haven't  had much luck getting this motherboard to work fully under Linux.

---

### Post by boom2k1 on 2007-08-10
I heard there is some SATA compatibility issue, is it true, if so how do you fix it?

Does anyone experience the same issue with connecting through only the DVI port, if so, how do you solve it?

Any answers to the above questions would be appreciated.
Thanks!

---

### Post by chiques on 2007-10-20
> **nfoti said:**
> HI, I have this motherboard and I'm attempting a mythtv install - Thanks for the help posted above in getting ubuntu to install - however,

I'm having major video issues with this machine:
ASUS M2A-VM AMD 690G ATI600SB ATI X1200.

I could not get video to playback reasonably well with the on-board ati video card - even installed the newest proprietary driver. So I chalked this up to ATI's drivers being sub-par. Next I threw in a nvidia geforce 7300 pci-e card i had lying around - did a fresh ubuntu feisty install, installed the nvidia drivers - and the video looks just as bad.

My question is - is anyone else having these video playback problems?

My video is choppy at best, any input from anyone with this board would be greatly appreciated.

BTW. - I wasn't aware that this board had a tv add on option, I know you can order the SPDIF out connector separately and it does work for digital audio.

I have the exact same problem in Windows XP Home. I am using Power DVD. I just finished installing Mandriva 2007 and I will see if my DVD flashes/glitches in there. I have just installed Ubuntu 7.10 and it is MUCH more difficult to troubleshoot this HDMI problem. 

ASUS M2A-VM HDMI
Integrated Radeon XPress 1250
AMD 64 Athlon
1 GB RAM
320 GB HD
40x Pioneer DVD-R

---

### Post by chiques on 2007-10-24
Here is a fix the helped me to boot Ubuntu 7.10 (in text mode). I was getting an error "[ 0.672000] PCI: Cannot allocate resource region 1 of device 0000:00:14.0"

I got it from this forum:
[http://www.ubuntu-es.org/index.php?q=node/65388]("http://www.ubuntu-es.org/index.php?q=node/65388")

---

### Post by pgarnett on 2007-12-05
This motherboard (Asus M2A-VM HDMI) is for 64-bit AMD processors like the AMD Athlon 64 X2 used by both the original poster and me.  So I think the 64-bit version of Ubuntu is the way to go.  It was for me, anyway - I just installed Ubuntu 7.04 from the 64-bit Live CD and it recognized everything on the board including graphics from the 690G chipset requiring restricted ATI drivers.  The original post described installing the 32-bit version.  Perhaps that was the problem???

---

### Post by be4truth on 2007-12-08
Asus M2a-VM with Ubuntu 7.10 32bit

There are issues with this board:
First issue: When installing an error like this occurs 'cannot allocate resource region .....'
Solution: go into the BIOS and disable the HPET option. Use the 'Alternate Install CD 7.10'. Before installing pass the boot option 'acpi=off'. Make sure you floppy drive is either connected or disabled in the BIOS as the installation routine hangs looking for it.
After complete installation install the restricted ATI driver via restricted driver module. Resolution up to 1280x1024 is ok. Sound ok. Didn't had much time to test video. Will do soon.

---

### Post by Brian96 on 2008-04-06
> **pgarnett said:**
> This motherboard (Asus M2A-VM HDMI) is for 64-bit AMD processors like the AMD Athlon 64 X2 used by both the original poster and me.  So I think the 64-bit version of Ubuntu is the way to go.  It was for me, anyway - I just installed Ubuntu 7.04 from the 64-bit Live CD and it recognized everything on the board including graphics from the 690G chipset requiring restricted ATI drivers.  The original post described installing the 32-bit version.  Perhaps that was the problem???

> **be4truth said:**
> Asus M2a-VM with Ubuntu 7.10 32bit

There are issues with this board:
First issue: When installing an error like this occurs 'cannot allocate resource region .....'
Solution: go into the BIOS and disable the HPET option. Use the 'Alternate Install CD 7.10'. Before installing pass the boot option 'acpi=off'. Make sure you floppy drive is either connected or disabled in the BIOS as the installation routine hangs looking for it.
After complete installation install the restricted ATI driver via restricted driver module. Resolution up to 1280x1024 is ok. Sound ok. Didn't had much time to test video. Will do soon.

Any update on the video with this mobo? I am also wondering if the ATI drivers required give the typical Linux/ATI headaches (like having to use XGL for Compiz).

---

### Post by Offoffoff on 2008-07-15
I am going to by this motherboard (Asus M2A-VM HDMI). Is it more stable now in 8.04? Can I use this motherboard as base of my MediaStation? Is tv-out plug working?

---

### Post by be4truth on 2008-07-15
> **Offoffoff said:**
> I am going to by this motherboard (Asus M2A-VM HDMI). Is it more stable now in 8.04? Can I use this motherboard as base of my MediaStation? Is tv-out plug working?

I don't recommend this board at all. The performance is not good, every new Ubuntu release is some other problem. I recommend either to get a cheap Intel board without the Asus media bells & whistles (who wants to be woken up by owns favourite MP3 from the PC waking up with build-in BIOS function..) or if you want an Asus get a much better quality. Cheap boards and fancy stuff doesn't go together and even less inn Linux.

---

### Post by Voxicles on 2008-07-23
Well, I too, unfortunately bought this board, as I didn't do much research before I picked it up.  Said HDMI and ASUS, that sold me. Never been disappointed by ASUS before. Last time I order crap on impulse.

ANYHOW,  been trying for 2 days now to install Kubu 8.04 64, yet to no avail.  I get to different points on different tries.  Sometimes I will get all the way to the partition manager (Which I don't need, since I already have it all  set up) and it hangs there, one time it got past that part, and started installing, then said something about my hdd, or dvd being bad.  Swapped out the SATA drive with a new one, burnt a couple new discs, same problem on a clean drive and dif disks.  Can never get all the way through the install.  I've tried both version, (alt and live) and i've tried the 32 bit version, still no worky.  The above mentioned fixes haven't worked for me either.  Any ideas?

Sys Specs:
M2a-VM HDMI mobo
AMD athlon 4600 x2
WD 160gb sata hdd
LG ide dvd
4 gigs ddr2

blah blah blah.

What I'm trying to acomplish is a triple boot with xp, kubuntu and osx.  I'm sure I'm going to run into osx problems, but I'll worry about those after linux)

Sorry about the marathon post

---

### Post by be4truth on 2008-07-23
I stopped using Kubuntu because it didn't respond to lots of hardware. Try Ubuntu instead. By now there is lots of eye candy for Gnome and fancy other stuff. A lot of K-application run under Ubuntu and if that's not enough install the kubuntu desktop later on top of Ubuntu.
I have Ubuntu Hardy perfectly running on this board by now. There are problem with the graphic card:

M2A-VM ASUS board with a radeon X1200 graphic chip

Disable BIOS option HPET to be able to boot. 

in Hardy acpi=off has to be taken out of the kernel parameters

To install graphic carder driver

sudo apt-get install fglrx-xorg-driver

---

### Post by Voxicles on 2008-07-23
I actually tried to install ubuntu also, never got past the loading screen.  ASked me to pick my language, then looked like it was loading, then all went black :-(  I would love if ubuntu would load.  I haven't tried ubuntu with the way you gave, I will do so in a few minutes

Well, I'm writing this now in ubuntu.  Yay, it works.  Though webpages load EXTREMELY slow.  Any way to fix that?

Edit: Back in windows now, the page laod times were getting horrible in ubuntu.  (Should add that I'm using wireless)  Also the sudo apt-get line you gave doesn't find anyting.  is there a file I need to dl somewhere?   One last question..  How do I get my dual screens to run separately in ubuntu using the onboard video?  And after that, it's on to tackling the OSx nightmare.  I think I might just give up on that one :-/

---

