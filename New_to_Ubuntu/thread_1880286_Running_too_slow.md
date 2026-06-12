---
title: "Running too slow"
date: 2011-11-13
forum: New to Ubuntu
---

### Post by kushalashok on 2011-11-13
I recently downloaded ubuntu 11.10 and made a bootable cd.
First I installed it on my PC desktop, which was running XP very slow so I wanted to use Linux for better speed.

But to my surprise it is still running very slow. Even maximizing and minimizing of windows takes a lot of time.

I thought this might be a problem with my desktop, so I installed it on my laptop as well (by using virtualbox).

Now in the virtual box, ubuntu is again running very very slow, while my windows OS is working fine.

Note: during the installation I was prompted to change my color scheme from 16 bit to 32 bit. But when I checked the settings, I was already using 32 bit.

Now I have no idea, why is the ubuntu OS which I consider to be very fast is running so slow.

Please help while using layman language as I am new here.

---

### Post by Paqman on 2011-11-13
What are the specs of your desktop?


> **kushalashok said:**
> 
I thought this might be a problem with my desktop, so I installed it on my laptop as well (by using virtualbox).

Now in the virtual box, ubuntu is again running very very slow, while my windows OS is working fine.


That's doesn't prove much. Running an OS in Virtualbox is always going to be slower than one running on the actual machine, especially if you don't have the VBox Guest Additions installed.

---

### Post by BillyBoa on 2011-11-13
You don't specify what specifications have your computers.

In any case Ubuntu is a little faster than Win XP but you are not going to revive an old computer with an edging cut technology OS like Ubuntu 11.10. It needs a lot of resources, especially RAM and a decent Video card.

You could try a lighter Linux distribution like PuppyLinux which is based on Ubuntu as well.

But again don't expect miracles.

---

### Post by dslevin@gmail.com on 2011-11-13
Try installing the Unity 2D desktop environment from the software center. Also did you install it or are you running in Live CD mode. The way to tell is to take out the disc and reboot. If there is not Ubuntu then you were running in live CD.  Also if you installed did you use the WUBI installer or did you install on bare metal. Bare metal will give the fastest performance.  I hope this is helpful.

---

### Post by ask_ on 2011-11-13
> **kushalashok said:**
> 
Now I have no idea, why is the ubuntu OS which I consider to be very fast is running so slow.

Please help while using layman language as I am new here.

Ubuntu 11.10 won't run fast on any old PC ,it has a few minimum requirements. Such as 1GB RAM , 1GHz CPU. [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

I also have a quite old PC.Around 7 years old. I tried Ubuntu 11.10 and it would consume lot of CPU. I am also a beginner to Ubuntu.

I was advised to try Xubuntu / Lubuntu. I tried Lubuntu and it worked for me. 
It takes some time to boot but once booted it is running faster than Windows XP.Details of sys requirements for Lubuntu and Xubuntu are given [here]("https://help.ubuntu.com/community/Installation/SystemRequirements#Lightweight_GUI_alternative_.28Xubuntu_and_Lubuntu.29")

Installation of Lubuntu/Xubuntu is identical to that of Ubuntu. While installing from the Live CD , you will get an option to replace the Ubuntu 11.10 version by Lubuntu 11.10 (or Xubuntu 11.10,in case you download Xubuntu),Windows will be kept intact.

Lubuntu 11.10 is now officially supported by the Ubuntu community. But keep in mind, it doesn't have Ubuntu software center(in case you use it) pre-installed on it. You have to install it from Synaptic Package manager. In case, you want software center pre-installed you could try Xubuntu. It also uses pretty low resources than Ubuntu,but Lubuntu is even faster . Lubuntu can be downloaded [here]("http://cdimages.ubuntu.com/lubuntu/releases/11.10/release/")

You could also try the other lighter versions that were recommended over here.
The great thing about Ubuntu is, you have many choices.

Of course , you should post your hardware specs here as the mentors will be in  better position to help you.

To do so, Type the following command in the terminal ,

```
sudo lshw

```

and post the results here wrapped in code tags (simply cut and paste from the terminal then highlight and then click on the # symbol on this message boxes toolbar).

---

### Post by kushalashok on 2011-11-13
> **Paqman said:**
> What are the specs of your desktop?




That's doesn't prove much. Running an OS in Virtualbox is always going to be slower than one running on the actual machine, especially if you don't have the VBox Guest Additions installed.
I don't really care about the ubuntu running on virtual box of my laptop. I did all this to make my desktop better so I will probably delete ubuntu from my laptop once I figure it out.

As for the desktop it's specs are:

Memory: 994.1 MiB
Processor: Intel Pentium(R) 4 CPU 1.80 Ghz
Graphics: Unknown
OS type: 32-bit
Disk: 16.2 GB (rest of it is consumed by other partitions)

Please tell me, What else shall I specify?

---

### Post by Paqman on 2011-11-13
> **kushalashok said:**
> 
Memory: 994.1 MiB
Processor: Intel Pentium(R) 4 CPU 1.80 Ghz
Graphics: Unknown
OS type: 32-bit
Disk: 16.2 GB (rest of it is consumed by other partitions)


That should b more than sufficient to run Ubuntu at a decent speed. I suspect the issue is your graphics. Check to see if there is a driver available in Additional Drivers, if so install it. If not, open a terminal (Ctrl-Alt-T) and post the output of this command:
```
lspci
```

If your graphics card is not well supported you may have to switch to Unity 2D instead of the 3D desktop.

---

### Post by kushalashok on 2011-11-13
> **BillyBoa said:**
>  It needs a lot of resources, especially RAM and a decent Video card.
.

I just specified the specs in my last reply. Sorry about skipping them.

I have enough RAM I guess, but no video card. Maybe the resolution is creating trouble.

---

### Post by kushalashok on 2011-11-13
On running Terminal:
```
lspci
``````
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:01.0 Modem: SILICON Laboratories Intel 537 [Winmodem] (rev 04)
01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:01.0 Modem: SILICON Laboratories Intel 537 [Winmodem] (rev 04)
01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```
and..
```
sudo lshw
```It asks for admin password but the keyboard gets disabled.

---

### Post by kushalashok on 2011-11-13
> I tried Lubuntu and it worked for me. 

I will try Lubuntu too, if this doesn't work out. The code you told me asks for admin password and then I am unable to type anything in the terminal.

Thanks

---

### Post by bkratz on 2011-11-13
> **kushalashok said:**
> I will try Lubuntu too, if this doesn't work out. The code you told me asks for admin password and then I am unable to type anything in the terminal.

Thanks



You really are typing it in, it is just not echoed to the screen not even * press enter when done.

---

### Post by kushalashok on 2011-11-13
>  If your graphics card is not well supported you may have to switch to Unity 2D instead of the 3D desktop.

I do not have a graphics card. How to switch to Unity 2D? I can see that it is installed (checked at "Ubuntu software center")

---

### Post by kushalashok on 2011-11-13
> **dslevin@gmail.com said:**
> Try installing the Unity 2D desktop environment. Also if you installed did you use the WUBI installer or did you install on bare metal. Bare metal will give the fastest performance.  

How can I use the Unity 2D?
I used the WUBI installer I guess. Didn't notice bare metal.

---

### Post by Paqman on 2011-11-13
> **kushalashok said:**
> I do not have a graphics card. How to switch to Unity 2D? I can see that it is installed (checked at "Ubuntu software center")

You have an Intel integrated graphics chipset, so it's built into your motherboard.

To switch to Unity 2D log out, then click on the little cog to the top right of your username and pick "Unity 2D" then log in like normal. You should find it a lot more responsive.

---

### Post by kushalashok on 2011-11-13
> **ask_ said:**
> Ubuntu 11.10 won't run fast on any old PC ,it has a few minimum requirements. Such as 1GB RAM , 1GHz CPU. [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

I also have a quite old PC.Around 7 years old. I tried Ubuntu 11.10 and it would consume lot of CPU. I am also a beginner to Ubuntu.

I was advised to try Xubuntu / Lubuntu. I tried Lubuntu and it worked for me. 
It takes some time to boot but once booted it is running faster than Windows XP.Details of sys requirements for Lubuntu and Xubuntu are given [here]("https://help.ubuntu.com/community/Installation/SystemRequirements#Lightweight_GUI_alternative_.28Xubuntu_and_Lubuntu.29")

Installation of Lubuntu/Xubuntu is identical to that of Ubuntu. While installing from the Live CD , you will get an option to replace the Ubuntu 11.10 version by Lubuntu 11.10 (or Xubuntu 11.10,in case you download Xubuntu),Windows will be kept intact.

Lubuntu 11.10 is now officially supported by the Ubuntu community. But keep in mind, it doesn't have Ubuntu software center(in case you use it) pre-installed on it. You have to install it from Synaptic Package manager. In case, you want software center pre-installed you could try Xubuntu. It also uses pretty low resources than Ubuntu,but Lubuntu is even faster . Lubuntu can be downloaded [here]("http://cdimages.ubuntu.com/lubuntu/releases/11.10/release/")

You could also try the other lighter versions that were recommended over here.
The great thing about Ubuntu is, you have many choices.

Of course , you should post your hardware specs here as the mentors will be in  better position to help you.

To do so, Type the following command in the terminal ,

```
sudo lshw

```

and post the results here wrapped in code tags (simply cut and paste from the terminal then highlight and then click on the # symbol on this message boxes toolbar).
```

desktop            
    description: Desktop Computer
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1
  *-core
       description: Motherboard
       product: 8LD533
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: 1.x
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: 6.00 PG
          date: 11/26/2002
          size: 128KiB
          capacity: 192KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 1.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.2.7
          slot: Socket 478
          size: 1800MHz
          capacity: 3066MHz
          width: 32 bits
          clock: 100MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 8KiB
             capacity: 20KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 18
          slot: System board or motherboard
          size: 1GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
        *-bank:1
             description: DIMM 266 MHz (3.8 ns)
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 1GiB
             width: 64 bits
             clock: 266MHz (3.8ns)
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:d0000000-dfffffff
        *-display
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:e0000000-e7ffffff memory:e8100000-e817ffff
       
```

---

### Post by kushalashok on 2011-11-13
> **Paqman said:**
> You have an Intel integrated graphics chipset, so it's built into your motherboard.

To switch to Unity 2D log out, then click on the little cog to the top right of your username and pick "Unity 2D" then log in like normal. You should find it a lot more responsive.

Nice! It is working far better now. Thanks a ton.

---

### Post by kushalashok on 2011-11-13
> **bkratz said:**
> You really are typing it in, it is just not echoed to the screen not even * press enter when done.
Thanks! I thought the keys were not working. :D

---

### Post by kushalashok on 2011-11-13
> **dslevin@gmail.com said:**
> Try installing the Unity 2D desktop environment from the software center. Also did you install it or are you running in Live CD mode. The way to tell is to take out the disc and reboot. If there is not Ubuntu then you were running in live CD.  Also if you installed did you use the WUBI installer or did you install on bare metal. Bare metal will give the fastest performance.  I hope this is helpful.
"Unity 2D" stole the show. It's working far better now. 
Thanks a lot. 
I will get back to you regarding the virtual box tools, once I am done with the installation on laptop.

---

### Post by Paqman on 2011-11-13
> **kushalashok said:**
> Nice! It is working far better now. Thanks a ton.

No worries, enjoy! I use Unity 2D on my netbook, it's pretty much identical to the 3D version, but much less demanding on your hardware.

---

