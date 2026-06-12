---
title: "black screen on installing lubuntu with intel video card 82845G/GL"
date: 2013-06-01
forum: New to Ubuntu
---

### Post by senneca on 2013-06-01
I had some problems installing any ubuntu version because the screen always turned black.
I managed to install Lubuntu by inserting "nomodeset xforcevesa" 
(maybe one of the 2 would have done it)
The display is fine now but according to the solution i used i should now install the correct video drivers so i don't need the "nomodeset xforcevesa" solution anymore

But i don't know how to do this.
From intel's website I found this : [Intel(R) Linux* Graphics Installer version 1.0.1 for Ubuntu* 13.04 (32-bit)]("https://download.01.org/gfx/ubuntu/13.04/main/pool/13.04/i/intel-linux-graphics-installer/intel-linux-graphics-installer_1.0.1_i386.deb") 
[https://01.org/linuxgraphics/downloads](https://01.org/linuxgraphics/downloads)

But when i try to install this i get an error  : Fout: Afhankelijkheid is niet vervulbaar: libglib2.0-0 (>= 2.35.9) (=[COLOR=#444444][FONT=arial]"[/FONT][/COLOR]*Dependency*[COLOR=#444444][FONT=arial] is not satisfiable)[/FONT][/COLOR]

But maybe its the wrong packet?
Maybe i already have a driver?

Here some more info:
seneca@ubuntu:~$ sudo lshw -c video
[sudo] password for seneca: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:f0000000-f7ffffff memory:fc400000-fc47ffff



@ubuntu:~$ sudo cat /var/log/Xorg.0.log |grep -i driver
1[sudo] password for seneca: 


[    30.218]     X.Org Video Driver: 11.0
[    30.218]     X.Org XInput driver : 16.0
[    30.252] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    30.253]     Module class: X.Org Video Driver
[    30.253]     ABI class: X.Org Video Driver, version 11.0
[    30.253] (II) VESA: driver for VESA chipsets: vesa
[    30.254] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    30.257]     ABI class: X.Org Video Driver, version 11.0
[    30.264]     ABI class: X.Org Video Driver, version 11.0
[    30.668]     ABI class: X.Org Video Driver, version 11.0
[    32.686]     Module class: X.Org XInput Driver
[    32.686]     ABI class: X.Org XInput driver, version 16.0
[    32.687] (II) Using input driver 'evdev' for 'Power Button'
[    32.788] (II) Using input driver 'evdev' for 'Power Button'
[    32.792] (II) Using input driver 'evdev' for 'Dell Dell USB Keyboard'
[    32.796] (II) Using input driver 'evdev' for 'Logitech USB Optical Mouse'
[    32.800] (II) No input driver specified, ignoring this device.

---

### Post by ohnonot on 2013-06-01
1) if the computer is working well enough, don't bother changing this.
2) i'm pretty sure you can find a native linux driver for an onboard intel gpu. no need to go to intel webpage.

---

### Post by squakie on 2013-06-02
what releaase/version of ubuntu?  It's been a while since I last checked, but the 845 comes to mind as one of the GPU's there has always little quirks with.  Instead of nomodeset xforcevesa,  try chaning that to just a single i915.nomodeset=1   if that doesn't work, then try i915.modeset=0  and see if either help at all of not.

Also - just check additional drivers.

---

### Post by senneca on 2013-06-03
Thanks squakie and ohnonot

[COLOR=#000000] i915.nomodeset=1 is also working so i use that

I am using version 12.04

I will let you know if i encounter any problems[/COLOR]

---

### Post by squakie on 2013-06-03
If you don't know, this setting can be added to a file in the system so you don't have to enter it each time you boot.  Let us know if you need help doing so.

---

### Post by senneca on 2013-06-04
Thanks, I managed to make it permanent using the procedure in the thread "[How to set NOMODESET and other kernel boot options in grub2]("http://ubuntuforums.org/showthread.php?t=1613132")[COLOR=#000000]"[/COLOR]
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 

It was a bit confusing because it said "(not wubi)" and I have used wubi to install.

The first command 'gksudo gedit /etc/default/grub 'didn't do anything. There was no error message but now i know it was because gedit wasn't installed. I used leafpad instead.

---

### Post by senneca on 2013-06-06
I am experiencing some problems. The computer slows down enormously if more than 2 programs are active, for example thunderbird, chrome and calculator. I have had to shut it down a couple of times because it wasn't responding after waiting half an hour or so. 
Could it be that it is slowing down because of problem with the video driver? Or is it just a crappy computer.?
I don't know the command to show the specifications.
In the task manager X.org is using around 5-15% ot the CPU, has this to do with the graphics?

---

### Post by ohnonot on 2013-06-07
both thunderbird and chrome are non-gtk apps, so running them at the same time might slow things down on an older computer. gtk is the native toolkit of most linux distros. ([http://www.gtk.org/](http://www.gtk.org/))
i generally would not recommend chrome. use firefox, or, if you must, chromium. also, if your web browser doesn't destroy cookies every now and then, it *will* eat your cpu. and your soul belongs to google. my firefox is set up to delete all cookies when i close it, and i close it often.

you can improve your task manager research thus: right click on its titlebar and chose layer --> always on top.
in taskmanagers menu chose view and check all options.

you can find out about your hardware with 'sudo lshw' (=list hardware).
if you want you can post relevant results (i will not read the whole output, you can use sth like 'sudo lshw | grep -i <cpu or mem or whatever>').

5-15% cpu for Xorg could be quite normal for older hardware.
xorg (or X) is the base component of your graphic DE.

edit: of course there could still be a problem related to your recent adjustments.

---

### Post by senneca on 2013-06-07
Sorry, I meant Chromium, not Chrome. Since it was already installed, i figured it was faster than firefox but that's not the case?
I  will remember deleting the cookies because I like my soul.:p
Thanks for the tip for keeping the taskmanager on top. Why do the percentages in the task manager never add up to the total number at the top, even though I  clicked all tasks on (user, root, other)? My real problems begin if it stays at 100% for no apparent reason.
I noticed that If I leave my computer on for a longer period without using it the CPU usage gets higher and it gets incredibly slow.
I will post the results of lshw but it is taking very long.

---

### Post by senneca on 2013-06-08
*-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU 1.70GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: 15.1.3
          slot: XU1 PROCESSOR
          size: 1700MHz
          capacity: 3GHz
          width: 32 bits
          clock: 400MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts

   configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 6
             slot: Internal L1 Cache
             size: 8KiB
             capacity: 20KiB
             capabilities: burst internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 7
             slot: Cache L2
             size: 128KiB
             capacity: 4MiB
             capabilities: burst internal write-back data
     *-memory:0
          description: System Memory
          physical id: 22
          slot: Systeem- of moederbord
          capacity: 2GiB
        *-bank:0
             description: DIMM SDRAM Synchroon 266 MHz (3,8 ns)
             product: M3 68L3223FTN-CCC
             vendor: JEDEC ID:CE 00 00 00 00 00 00 00
             physical id: 0
             serial: 58C605F2
             slot: DIMM1
             size: 256MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:1
             description: DIMM SDRAM Synchroon 266 MHz (3,8 ns)
             product: M3 68L3223FTN-CCC
             vendor: JEDEC ID:CE 00 00 00 00 00 00 00
             physical id: 1
             serial: B1C602F2
             slot: DIMM2
             size: 256MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
     *-memory:1 UNCLAIMED
          description: Flash Memory
          physical id: 23
          slot: Systeem- of moederbord
          capacity: 512KiB
        *-bank UNCLAIMED
             description: Chip FLASH Non-volatile
             physical id: 0
             slot: SYSTEM ROM
             size: 512KiB
             width: 4 bits
     *-memory:2 UNCLAIMED
          physical id: 0
     *-memory:3 UNCLAIMED
          physical id: 2
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:f8000000-fbffffff
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list
             configuration: latency=0
             resources: memory:f0000000-f7ffffff memory:fc400000-fc47ffff

---

### Post by ohnonot on 2013-06-08
i didn't mean that my suggestions would give relevant results!
i still don't see how much ram you have there.
but i can see that you have 1 cpu with 1,7GHz - that means the computer is about 10 years old? It should be running fine with Lubuntu but nevertheless you should keep an eye on resource eating processes.

are you sure you are viewing processes of all users in task manager? did you try the same with top (terminal app) or even better htop?
also look at memory, not only cpu. but beware, it's hard to read because of linux's way of making use of free memory.

you should find out what is bringing your computer to a near halt.

it's not necessarily thunderbird or chromium, but they are most probably contributing to the resource eating.

---

### Post by squakie on 2013-06-10
I would suggest launching system monitor and checking all processes, memory usage, swap usage, cpu usage, etc., there - everything is within that one tool.  I'd particulary watch swap if things are getting slow and see if swap usage is high.  As was already mentioned, we do need to know the total memory installed as well.   That should show in system monitor. but you can also just go to system details and see that.

If this is happening even after you close every application you have opened, I would suspect a few things, but I would start with a process that hasn't actually completely stopped.  ps -e will show all processes, and I would look for multiple occurences of the same name - don't kill any of them - just post back here what they are.

---

