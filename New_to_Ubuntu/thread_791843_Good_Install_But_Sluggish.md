---
title: "Good Install But Sluggish"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by rocketman_dc on 2008-05-12
Hi, I had a good first day yesterday with XUBUNTU. I have an old Dell 500 mhz Pentium 3.  I had a 14 Gig hard drive that I used for the install, and I think it did 20% for XUBUNTU and 80% for bin(?)  I have 384 megs (or around there, of RAM).  Mouse, sound, internet all work.  This had been a Windows 98 machine, and I think that is still in there on the other drive.  

I even got Flash to work on websites.

So I'm happy that it works, but I thought it was going to be a bit more snappy, in terms of boot up, applications opening, and internet performance/flash video playing.  I tested my internet speed (cable) at dslreports.com and it was very good download 8000+, so the cable speed is working fine.  Is it sluggish because of the chip?  the relatively tight HD space?  the amount of RAM? 

We are going to use this computer primarily for three things:  web browsing, email (working fine), and instant messaging.  Can I speed things up for those functions? 

Two other quick questions I'll ask if you got this far:  anyone know of a good bridge application to install for xubuntu and can I use Yahoo IM on it?  

Thanks!  rocketman_dc

---

### Post by hyper_ch on 2008-05-12
> **rocketman_dc said:**
> So I'm happy that it works, but I thought it was going to be a bit more snappy, in terms of boot up, applications opening, and internet performance/flash video playing.
Well, that computer was build for an operating system that is now 10 years old... Ubuntu Hardy is an OS that is just a month old....

You might consider to use Fluxbuntu instead of Xubuntu... Fluxbuntu is even lighter...

> **rocketman_dc said:**
>  Is it sluggish because of the chip?  the relatively tight HD space?  the amount of RAM?
384 MB ram should be fine... more would be better... I guess it's a combination of both ram and cpu speed... one you run Xubuntu, open a terminal and run:
```

sudo apt-get install htop

```
and then run it by
```

htop

```
That will monitor what process is using how much resources. It should help to determine whether it's the cpu or ram....

> **rocketman_dc said:**
> We are going to use this computer primarily for three things:  web browsing, email (working fine), and instant messaging.  Can I speed things up for those functions? 
You can use lighter programs but you probably want to use Firefox and Thunderbird, right?

> **rocketman_dc said:**
> anyone know of a good bridge application What is a bridge application?


> **rocketman_dc said:**
> can I use Yahoo IM on it?
There are clients that support more than just Yahoo IM... you might want to use one of them. Have a look through synaptic.

---

### Post by gn2 on 2008-05-12
Which version of Xubuntu did you install, 6.06, 7.04, 7.10 or 8.04?

---

### Post by lswest on 2008-05-12
if by "bridge application" you meant Adobe Bridge, F-Spot is similar and (i think) it's pre-installed.  If you mean a game for playing bridge, sorry, don't know.

---

### Post by rocketman_dc on 2008-05-12
> **gn2 said:**
> Which version of Xubuntu did you install, 6.06, 7.04, 7.10 or 8.04?
I installed 8.04.  

By bridge, I meant the card game bridge.  Thanks!

---

### Post by spiderbatdad on 2008-05-12
Hello, and welcome to the forums.
Your boot up time might be increased with the application of some special boot parameters. If you run the command ```
dmesg
```in your terminal and try to follow the process, you may see some suggestions like: "apic disabled by bios, try using 'lapic.'" Or you might see a failure in proper irq routing. These problem can be fixed up and greatly increase boot time as well as hardware performance. If you find some suggestions you want to try, you apply the parameters to the file /boot/grub/menu.lst You can repost for help on how to do this.

If you are using Firefox 3 beta5, it is likely very slow. There are a number of browsers available that are much faster. I prefer SeaMonkey, an offshoot of Mozilla it is a sibling to FF and has all the latest security patches that FF has. Also flash works out-of-the-box.

Pidgin works for YIM. If you want video for YIM, look into gyache.

---

### Post by ugm6hr on 2008-05-12
> **hyper_ch said:**
> Well, that computer was build for an operating system that is now 10 years old... Ubuntu Hardy is an OS that is just a month old....

RAM makes the most difference, and 300+MB should work with Xubuntu fine.

I've had it on AMD K-6 with 128MB RAM (albeit 7.10 Xubuntu), and while not as fast as W98, it was equivalent to XP.

As stated, there are ways to speed things up further...

Browser: Opera
Window Manager: IceWM, Fluxbox

Xubuntu uses a lot of Gnome dependencies, which can slow things down.  Consider going to the options and turning off Gnome on startup and removing Network Manager.

---

### Post by rockerphil on 2008-05-12
i personally use Fluxbuntu on a machine that's about that old with even less RAM, 128 MB. and it's pretty awesome, you just gotta remember that even though you've got a more lightweight OS you still arent gonna be able to run it like a brand new machine, because no matter what you've still got limited system resources, nothing's gonna change that except for a hardware upgrade. the Fluxbuntu project is sorta stale right now, but they have got a Gutsy release which is easily upgraded to Hardy if you want, but if you're new to Linux and Ubuntu i'd suggest staying with Gutsy for a bit until all the bugs are worked out. hope this helped

---

### Post by rocketman_dc on 2008-05-12
Here are a few possibly interesting lines:

[    0.000000] ACPI: RSDP signature @ 0xC00F6B80 checksum 0
[    0.000000] ACPI: RSDP 000F6B80, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 040FDB3C, 0028 (r1 PTLTD    RSDT          0 PTL   1000000)
[    0.000000] ACPI: FACP 040FF78C, 0074 (r1 DELL   KUBLAI   19991105 PTL     F4240)
[    0.000000] ACPI: DSDT 040FDB64, 1C28 (r1  Intel  S2440BX        0 MSFT  1000004)
[    0.000000] ACPI: FACS 040FFBC0, 0040
[    0.000000] ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI
[    0.000000] ACPI: Disabling ACPI support


[   59.360160] EISA: Probing bus 0 at eisa.0
[   59.360184] Cannot allocate resource for EISA slot 1
[   59.360226] Cannot allocate resource for EISA slot 7
[   59.360235] Cannot allocate resource for EISA slot 8
[   59.360243] EISA: Detected 0 cards.

 61.395555] thermal: Unknown symbol acpi_processor_set_thermal_limit

 92.305723] PCI: Found IRQ 9 for device 0000:00:10.0
[   92.311598] PCI: Sharing IRQ 9 with 0000:00:07.2
[   92.311622] PCI: Sharing IRQ 9 with 0000:00:0f.1
[   92.317779] pcilynx0: allocated PCL memory 4096 Bytes @ 0xd5327000
[   92.317875] pcilynx0: allocated interrupt 9
[   92.317890] pcilynx0: remapped memory spaces reg 0xd696c000, rom 0xd6a80000, ram 0xd6a40000, aux 0xd6a60000
[   92.317905] pcilynx0: found old 1394 PHY
[   92.320531] pcilynx0: got bus info block from serial eeprom
[   92.320544] pcilynx: read something from serial eeprom, but it does not seem to be a valid bus info block
[   92.320573] pcilynx0: resetting bus (long bus reset, no force_root) on request

 132.937614] eth1: no IPv6 routers present
[  133.285510] eth0: no IPv6 routers present
[ 3418.771847] vortex: IRQ fifo error
[ 4101.753346] vortex: IRQ fifo error

Any of this bad?  there was a whole lot more!  thanks! :confused:

---

### Post by spiderbatdad on 2008-05-13
This suggests you should edit the file /boot/grub/menu.lst: [B]0.000000] ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI
[ 0.000000] ACPI: Disabling ACPI support[/B]

To do so, open the file with a graphical text editor like so,```
gksu gedit /boot/grub/menu.lst
```

Scroll down to the section that begins: ####END DEFAULT OPTIONS####
Just below that is a block of text. Look at the end of the line that begins with the word 'kernel.' Shown below.
```
## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
**kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=604f2b74-7f64-424f-a8bf-1160a71d9ea3 ro lapic **pci=routeirq
initrd		/boot/initrd.img-2.6.24-16-generic
quiet
savedefault
```

Where I have 'lapic pci=route irq,' You likely have '--quiet splash.'  Delete --quiet splash and add acpi=force
Save the file by clicking the floppy disk image near the top of the window and reboot. It should boot considerably faster. You can then make a "profile" of the boot process, to save a few more seconds, if you like. This is done from the grub menu presented at boot...where you choose which operating system you want to boot. If you select Ubuntu, then press 'e' you will see the same block of text you have in /boot/grub/menu.lst. Use the arrow key and move to the 'kernel' line. Press e again, then move to the end of the kernel line. You will see where you have already changed the parameters to include 'acpi=force.' after that add a space and the word 'profile,' So it looks like: acpi=force profile
Hit enter and then press b to boot. This boot will take a few extra seconds while it profiles the process. Subsequent boots will be faster.

---

### Post by james_vanb on 2008-05-13
You may have replace "gedit" with "mousepad" as I believe mousepad is the default for xubuntu.

---

### Post by rocketman_dc on 2008-05-13
Okay, I did the whole force/profile thing successfully.  I had to install that edit program, but I did that too.  I've also deleted Firefox 3 and installed Firefox 2. It's all working a little better now.  Thanks for all of your help!  I think it's running at about XP speed.  I'll definitely use this.   Thanks again.

---

### Post by FakeOutdoorsman on 2008-05-14
I would recommend a custom Ubuntu install using the "alternate" Ubuntu installation disc or the [Ubuntu Minial CD Image]("https://help.ubuntu.com/community/Installation/MinimalCD").  Using those installation methods you can choose to perform a command-line only installation and then build up from there.  You will end up with a snappier OS with only what you want installed.  It might sound daunting if you're a beginner, but you will definately learn about your machine and about Ubuntu.  It's not as hard as it may seem and I do this for all of my Ubuntu installations.  Here's a quick example for installing Openbox instead of XFCE:

1. Install the command-line system using the alternate or mini.iso.  Once you load the disc, highlight the first option (Install Ubuntu), hit F4, and then choose the command-line option.

2. Install your packages:
```
sudo aptitude update
sudo aptitude install xserver-xorg openbox openbox-themes synaptic obconf obmenu medit pidgin claws-mail pcmanfm
```

3. Start Openbox:
```
startx
```

This will give you a very basic, lightweight, and responsive base from which you can build up from and completely customize.  If you're interested in Openbox then this is an excellent resource: [Urukrama's Openbox Guide for Ubuntu]("http://urukrama.wordpress.com/openbox-guide/").  That guide will help you setup a panel, themes, etc.

---

