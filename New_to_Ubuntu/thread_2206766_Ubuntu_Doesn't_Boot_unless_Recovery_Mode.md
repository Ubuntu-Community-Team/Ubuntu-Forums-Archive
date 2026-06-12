---
title: "Ubuntu Doesn't Boot unless Recovery Mode"
date: 2014-02-20
forum: New to Ubuntu
---

### Post by alejandrofurfaro on 2014-02-20
Hi everyone. I'm a new Ubuntu user and I'm having a problem with my OS, I wish you could help me. I have a dual boot laptop Windows 7 and Ubuntu 13.10. At the begining I had installed Ubuntu 12.04, and then a pop-up advice me that there was a system upgrade, after the update my computer didn´t boot anymore. In fact it does but not normally. If I let the computer start normally (without chosing any option on grub), at some point the screens goes black, the speakers makes the booting sound, but it doesn't do anything anymore. After a lot of restarts with no succeed I started the system running the Recovery Mode. Finally it started, however everytime I start the Laptop I should do it on Recovery Mode, because in other way it doesn't do anything . In my opinion that's not a neat solution so I'm trying to fix it, but don't find the answer yet. I've already installed "Boot Recovery" but it didn't work. 


Please could you help me. Thanks in advance.

---

### Post by Bashing-om on 2014-02-20
alejandrofurfaro; Hi ! Welcome to the forum .

Sounds to me like a graphics driver issue.
To see your graphics card and info;
Post the outputs of terminal codes (from the recovery console is acceptable at this time):
- Between code tags -
```

lsb_release -a
uname -a
sudo lshw -C display
lspci -nnk | grep -iA3 vga

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]a tale will be told
[/INDENT][/INDENT]

---

### Post by alejandrofurfaro on 2014-02-21
Hi Bashing-om thanks for your response. Here's the code you need:
```

imrahil@imrahil-laptop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy
imrahil@imrahil-laptop:~$ uname -a
Linux imrahil-laptop 3.11.0-17-generic #31-Ubuntu SMP Mon Feb 3 21:52:43 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
imrahil@imrahil-laptop:~$ sudo lshw -C display
[sudo] password for imrahil: 
  *-display NO RECLAMADO  
       descripción: VGA compatible controller
       producto: 3rd Gen Core processor Graphics Controller
       fabricante: Intel Corporation
       id físico: 2
       información del bus: pci@0000:00:02.0
       versión: 09
       anchura: 64 bits
       reloj: 33MHz
       capacidades: msi pm vga_controller cap_list
       configuración: latency=0
       recursos: memoria:7fc00000-7fffffff memoria:90000000-9fffffff ioport:3000(size=64)
imrahil@imrahil-laptop:~$ lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
    Subsystem: Toshiba America Info Systems Device [1179:fb71]
00:14.0 USB stem: Toshiba America Info Systems Device [1179:fb72]
imrahil@imrahil-laptop:~$ 

```

Once again thanks for your help!

---

### Post by Bashing-om on 2014-02-21
alejandrofurfaro; Hey ,

As suspected, there is no graphics driver loaded, so we at least know what the problem is.
Bad news is that it is Intel, and I have no knowledge/experience with that chipset in order to advise you presently of a solution.
Let's await others with the experience to help.

Else:
In due time I will see what I can learn, and we will find a solution together.

[INDENT][INDENT]if I knew everything
[INDENT][INDENT][INDENT]I would not be me
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by kevdog on 2014-02-22
Hey can you post lspci -nn?

---

### Post by alejandrofurfaro on 2014-02-22
Hey kevdog here is the code you need

```

imrahil@imrahil-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 3rd Gen Core processor DRAM Controller [8086:0154] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
00:1a.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 [8086:1e10] (rev c4)
00:1c.1 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 [8086:1e12] (rev c4)
00:1c.3 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 [8086:1e16] (rev c4)
00:1d.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation HM76 Express Chipset LPC Controller [8086:1e59] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] [8086:1e03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller [8086:1e22] (rev 04)
01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2200 [8086:0890] (rev c4)
03:00.0 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2392] (rev 30)
03:00.2 SD Host controller [0805]: JMicron Technology Corp. Standard SD Host Controller [197b:2391] (rev 30)an

```

Thanks both of you!

---

### Post by Bashing-om on 2014-02-22
alejandrofurfaro; Morning to ya ,

I do not know that this is a viable solution, but might be worth a consideration:
As you are using Ubuntu 13.10, and intend to continue upgrading as new releases become available, check out the Intel Graphics driver installer;
[http://www.webupd8.org/2013/03/intel-releases-linux-graphics-drivers.html](http://www.webupd8.org/2013/03/intel-releases-linux-graphics-drivers.html)
for the latest drivers direct from Intel.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by oldfred on 2014-02-22
Before trying the experimental Intel driver I might try some boot options. There is only one Intel open source driver and 13.10 has a recent version. But many systems seem to need boot options to help it configure itself.

  Older Intel video card: i915.modeset=1 or i915.modeset=0 newer:  i915.i915_enable_rc6=1

   Some other Intel boot options Each line is one that may work
acpi_osi=Linux  acpi_backlight=vendor
 i915.i915_enable_rc6=1

   Force Intel Video mode as boot parameter in grub menu - Must change to your screen size, not 1280x1024
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60

You add these like nomodeset. Or at grub menu, use e to edit, scroll to linux line & replace quiet spash. If you find one that works then we can modify grub to include it all the time.
       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by alejandrofurfaro on 2014-02-23
Hi Everyone,

First of all, thanks to all of you who get involved and tried to get a solution. Second I finally solved the issue, so I wil paste here the steps if anyone in the future needs it.

1) Open the Terminal and write the code below:
```
 
gksudo gedit /etc/default/grub

```

2) That will open the Grub and you should see something like these
```

GRUB_DEFAULT="0"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="10" 
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```

3) Change the line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

4) Save the changes and in the terminal run the next code to update the grub configuration:
```

sudo update-grub

```

That's all folks. Once again thanks for your colaboration,

---

### Post by Bashing-om on 2014-02-26
alejandrofurfaro; Hey,

It is great that you can now boot, but, "nomodeset" is not the best solution as that also disables Kernel Mode Setting, That may have adverse effects. We need to find a better solution.
I have lost internet connectivity on my machine, working to find a solution of my own, so my responses at this time will be spotty at best.


when I can
[INDENT][INDENT]I do
[/INDENT][/INDENT]

---

### Post by alejandrofurfaro on 2014-03-13
Hi bashing-om. Ok, if you say that the solution is not the best I will try to find another one more appropiate. Thanks!

---

