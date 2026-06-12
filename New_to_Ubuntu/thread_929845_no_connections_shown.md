---
title: "no connections shown"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by kingtut35 on 2008-09-25
When i look under network manager it does not show my network.  I'm plugged into a router is there anything i need to do to get this to work.  I don't think ubuntu can see my nic.  When i type ifconfig it gives me a loopback ip and thats it doesn't list my network card.  Help please

---

### Post by shifty_powers on 2008-09-25
this is a really simple question, but have you actually tried opening a browser and using the net?

plus have you tried the ping commmand?

```
ping www.google.com
```

---

### Post by kingtut35 on 2008-09-25
yes i opened the browser does not work.  I haven't pinged but i assumed that nothing else was working that ping wouldn't as well.

---

### Post by shifty_powers on 2008-09-25
heh i did say it was a really simple question :D

can you post the output of:

```
lspci
```

---

### Post by kingtut35 on 2008-09-25
this is what it says after i type lspci

00:00.0 Host bridge: Intel Corporation Eaglelake DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Eaglelake PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation ICH10 USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation ICH10 USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation ICH10 USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation ICH10 USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation ICH10 HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation ICH10 PCI Express Port 1
00:1c.4 PCI bridge: Intel Corporation ICH10 PCI Express Port 5
00:1c.5 PCI bridge: Intel Corporation ICH10 PCI Express Port 6
00:1d.0 USB Controller: Intel Corporation ICH10 USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation ICH10 USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation ICH10 USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation ICH10 USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation ICH10 LPC Interface Controller
00:1f.2 SATA controller: Intel Corporation ICH10 6 port SATA AHCI Controller
00:1f.3 SMBus: Intel Corporation ICH10 SMBus Controller
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GTS (rev a)
02:00.0 Ethernet controller: Attansic Technology Corp. Unknown device 1026 (rev b0)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface (rev b2)
05:02.0 Multimedia audio controller: Creative Labs SB X-Fi

---

### Post by shifty_powers on 2008-09-25
well the fact that it say unknown device for the ethernet controller indeed indicates that the driver is not working/functional.

i'll have a look, see what i can find :D

---

### Post by shifty_powers on 2008-09-25
[http://ubuntuforums.org/showthread.php?t=770173&highlight=Attansic+Technology](http://ubuntuforums.org/showthread.php?t=770173&highlight=Attansic+Technology)

have a look at that :D

---

### Post by kingtut35 on 2008-09-25
i will try that now.  hope i can get it to work.  any tips?  i'm so new to linux

---

### Post by kingtut35 on 2008-09-25
i ran the 2 sudo codes it gives me and the first one was fine

the second i get an error part way through that says:
cannot write to /var/cache/man/cat7/atl1e.7.gz in catman mode
atl1e.

---

### Post by cariboo on 2008-09-25
Follow the directions in post #7 that is the most relevant post in the thread. Make sure you have build-essentials in stalled before you start. You obviously don't have a working network connection, so install build-essential from the livecd you'll find it in /pool/main/b.

Jim

---

### Post by kingtut35 on 2008-09-25
i was follwing the steps in 7

when i go to the live cd to install i get an error

Error: dependency is not satifiable : libc6-dev|libc-dev

---

### Post by kingtut35 on 2008-09-25
also i can't seem to get to the lib directory.  the terminal just keeps me in my username directory.

---

### Post by shifty_powers on 2008-09-25
you need to install build-essentials, as suggested.

if you put your live-cd in you can use it to install pakcages.

make sure that it is enabled in your sources (admin>preferences>sources iirc)

then type

```
sudo apt-get install build-essential
```

---

### Post by kingtut35 on 2008-09-25
ok they are installed

---

### Post by kingtut35 on 2008-09-25
same error as before at the end of the build

---

### Post by shifty_powers on 2008-09-25
it's still asking for the same dependecies?

other thing you can do is look up the dependecny and download the apackage file for it:

[http://packages.ubuntu.com/feisty/libdevel/libc6-dev](http://packages.ubuntu.com/feisty/libdevel/libc6-dev)

it can be quite tedious but you can in theory find downlaod and meet all the dependencies.

careful you don't get into dependency hell, as it is known..

---

### Post by kingtut35 on 2008-09-25
no i got the builder installed.

but when i got to the steps listed on the link to the other post
to install my drivers.  the 7th step doesn't work i don't think.  and i 8th step i'm not sure what to do

---

### Post by shifty_powers on 2008-09-25
> Hi Guys

Thank you, thank you so much !!!

I have got it working !!!

Ok first the network card is Atheros(R) AR8121/AR8113 PCI-E

Ok these are the steps i followed to get it working!

1) I installed ubuntu hardy 64bit, i has build-essential package installed
2) Then i downloaded the linux driver from: [http://support.asus.com/download/dow...model=P5KPL-CM](http://support.asus.com/download/dow...model=P5KPL-CM)
(as per my original post)
3) I then transfered the driver via usb stick to my laptop and unpacked the zip. (Actually i unpacked it on windows first as it has a .rar file that i could not unpack on linux Then i packed it up again on windows).
4) cd into <HOME_DIR>/LinuxDrivers/L1e_Lan/l1e-l2e-linux-v1.0.0.4/src
5) then i ran: sudo KBUILD_NOPEDANTIC=1 make
6) then i ran: sudo KBUILD_NOPEDANTIC=1 make install
7) that worked and put a driver in /lib/modules/2.6.24-16-generic/kernel/drivers/net/atl1e/at1le.ko
8 ) i cd into that director and i run: sudo insmod ./atl1e.ko

That is it !!! it worked as soon as i plugged in network card.

Thank you all so much !!!! I hope this helps everyone else 

is that the one you are following?

---

### Post by kingtut35 on 2008-09-25
yes that is the one

---

### Post by oldsoundguy on 2008-09-25
Read all about it:
[http://atl1.sourceforge.net/](http://atl1.sourceforge.net/)

---

### Post by shifty_powers on 2008-09-25
> **kingtut35 said:**
> yes that is the one

well step 7 is referring to where it has put the driver. however this is specific to the kernel being used.

post the output to

```
uname -r
```

---

### Post by kingtut35 on 2008-09-25
2.6.24-19-generic

---

### Post by kingtut35 on 2008-09-25
well apparently that all worked after i restarted because now it shows wired connection set up and i'm able to browse as well

Thanks everyone who helped i'm sure i will be back with more questions soon

---

### Post by shifty_powers on 2008-09-25
heh glad to have helped.

i know that linux can still be a bit arcane at times, but the beauty of linux, and especially ubuntu, is the sheer pace that it evolves :D

---

### Post by kingtut35 on 2008-09-25
i needed it for school.  starting to learn linux. I have alot to learn apparently.

---

