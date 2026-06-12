---
title: "Display/hardware drivers?"
date: 2012-03-11
forum: New to Ubuntu
---

### Post by sx5622 on 2012-03-11
Hey all, I'm taking another crack at Ubuntu.  I just replaced the motherboard, ram, and processor in my desktop.  I thought this would be a pretty decent setup, but I feel my hardware isn't being utilized by the system.  For instance:

1) I can't change the screen resolution to greater than 800x600.
2) The games I've downloaded in Synaptic manager run slower than heck. 

Hardware manager says I am up to date - why is my machine acting like this?  Here is the hardware I have:

[Ram]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820103002")

[Motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813128517")

[Processor]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103957")

---

### Post by voitrix on 2012-03-11
Hello!
Which ubuntu version have you installed?
Probably the installed gpu driver doesn't support 3D. Did you check if there is any Additional Drivers (proprietary graphics driver) available for your GPU?

---

### Post by grahammechanical on 2012-03-11
You did not specify the two important pieces of hardware for this issue. The video adapter/card and the monitor.

I be very surprised that you did not buy a video card comparable to the other hardware that you have. 

Also, I must ask, what is the optimum resolution of the monitor?

Another question?

Have you run Additional Drivers to activate (install) an appropriate proprietary video driver? This could be the cause of this issue.

Regards.

---

### Post by sx5622 on 2012-03-11
I am using 10.04 LTS.  I'm not sure if there are any proprietary drivers - how can I check?  

Graham: I have no video card because the video display runs off the motherboard.  I am not using a monitor for my display, I am using a projector (Panasonic), and I am using VGA plug for it.  Again, tell me how I can find/install proprietary drivers.

Thanks!

---

### Post by kevdog on 2012-03-11
Although you don't have a video card, that just means your graphics chipset is just built into your MoBo.

lshw

will list your graphics chipset (as well as the other hardware).  Here is mine in case you cant figure out what to look for:

 *-display:0
             description: VGA compatible controller
             product: 82945G/GZ Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:e0400000-e047ffff ioport:20c0(size=8) memory:d0000000-dfffffff memory:e0500000-e053ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82945G/GZ Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:e0480000-e04fffff

---

### Post by sx5622 on 2012-03-12
Ok, here is what was listed:

 *-display UNCLAIMED
             description: VGA compatible controller
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:d0000000-dfffffff(prefetchable) ioport:f800(size=256) memory:fdfc0000-fdffffff

---

### Post by kevdog on 2012-03-12
Ok great -- you have an ATI chipset.  The word UNCLAIMED means the driver or kernel module as they refer to in linux is not installed. From what you have listed, it doesn't tell you much about the chipset.  I don't know a lot about ATI cards in linux -- other than that they are a pain in the a** to get to work.  I do a search first on the forums about ATI video chipsets to see if anything pops up.

---

### Post by 3rdalbum on 2012-03-12
You say you're running Ubuntu 10.04 and you have replaced the motherboard, presumably with a new one?

Well, that sounds like the problem. Ubuntu 10.04 only knows hardware from early 2010 and previous years. If the motherboard is new, the GPU is probably new too.

You could either install a newer version of Ubuntu such as the latest 11.10, or go to the AMD website and download the latest ATI graphics driver for Linux. Note that it's not the easiest thing to install, and you have to install it every time you get a kernel update; you might be better off just installing 11.10 and use its automatic driver installer.

---

### Post by sx5622 on 2012-03-13
> **3rdalbum said:**
> You say you're running Ubuntu 10.04 and you have replaced the motherboard, presumably with a new one?

Well, that sounds like the problem. Ubuntu 10.04 only knows hardware from early 2010 and previous years. If the motherboard is new, the GPU is probably new too.

You could either install a newer version of Ubuntu such as the latest 11.10, or go to the AMD website and download the latest ATI graphics driver for Linux. Note that it's not the easiest thing to install, and you have to install it every time you get a kernel update; you might be better off just installing 11.10 and use its automatic driver installer.

Awesome - looks like it would be best to install the latest version of Ubuntu.  However, I believe I tried to do that with a flash drive and couldn't get it to work.  Oh well, looks like it's time to try again!  Is there a way to 'update' my current version or will I have to do a clean install?

Thanks!

---

### Post by Mark Phelps on 2012-03-13
Before you do the install, how about opening the terminal, entering "lspci" and looking for the line containing "VGA".  That will tell you the make and model video chipset -- which is more useful than just "ATI".

---

### Post by bogan on 2012-03-13
Hi!, **all**

The OP's original Post #1, gave the CPU/GPU info as :> AMD A4-3300 Llano 2.5GHz Socket FM1 65W Dual-Core Desktop APU (CPU + GPU) with DirectX 11 Graphic **AMD Radeon HD 6410D **Chao!,** bogan**.

---

### Post by sx5622 on 2012-03-13
> **Mark Phelps said:**
> Before you do the install, how about opening the terminal, entering "lspci" and looking for the line containing "VGA".  That will tell you the make and model video chipset -- which is more useful than just "ATI".

00:00.0 Host bridge: Advanced Micro Devices [AMD] Device 1705
00:01.0 VGA compatible controller: ATI Technologies Inc Device 9645
00:01.1 Audio device: ATI Technologies Inc Device 1714
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Device 1709
00:10.0 USB Controller: Advanced Micro Devices [AMD] Device 7812 (rev 03)
00:10.1 USB Controller: Advanced Micro Devices [AMD] Device 7812 (rev 03)
00:11.0 SATA controller: Advanced Micro Devices [AMD] Device 7800 (rev 40)
00:12.0 USB Controller: Advanced Micro Devices [AMD] Device 7807 (rev 11)
00:12.2 USB Controller: Advanced Micro Devices [AMD] Device 7808 (rev 11)
00:13.0 USB Controller: Advanced Micro Devices [AMD] Device 7807 (rev 11)
00:13.2 USB Controller: Advanced Micro Devices [AMD] Device 7808 (rev 11)
00:14.0 SMBus: Advanced Micro Devices [AMD] Device 780b (rev 13)
00:14.1 IDE interface: Advanced Micro Devices [AMD] Device 780c
00:14.2 Audio device: Advanced Micro Devices [AMD] Device 780d (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] Device 780e (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] Device 780f (rev 40)
00:14.5 USB Controller: Advanced Micro Devices [AMD] Device 7809 (rev 11)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Device 1700 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Device 1701
00:18.2 Host bridge: Advanced Micro Devices [AMD] Device 1702
00:18.3 Host bridge: Advanced Micro Devices [AMD] Device 1703
00:18.4 Host bridge: Advanced Micro Devices [AMD] Device 1704
00:18.5 Host bridge: Advanced Micro Devices [AMD] Device 1718
00:18.6 Host bridge: Advanced Micro Devices [AMD] Device 1716
00:18.7 Host bridge: Advanced Micro Devices [AMD] Device 1719
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
02:06.0 Network controller: RaLink RT2561/RT61 802.11g PCI

---

### Post by jerrrys on 2012-03-13
lspci -nn | grep VGA

sudo lshw -C display

---

