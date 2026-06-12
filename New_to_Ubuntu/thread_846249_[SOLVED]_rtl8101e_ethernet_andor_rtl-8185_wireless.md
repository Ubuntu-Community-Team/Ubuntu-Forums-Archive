---
title: "[SOLVED] rtl8101e ethernet and/or rtl-8185 wireless help"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by tjwoosta on 2008-07-01
ok first i should say that i have a laptop with the rtl8101e ethernet card and it worked straight from the live cd no prob

now im trying to setup my sisters computer which also says it has rtl8101e ethernet, but it does not work

also her computer has the rtl-8185 wireless card (get to that in a min)


so i downloaded the rtl8101e
"Linux driver for kernel 2.6.X and 2.4.X (Support x86 and x64)"

from here[http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false]("http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false")


this is what happens when i follow the readme provided in the package
and i did sudo make clean modules
```

ashley@ashley-desktop:~/r8101-1.007.00$ ls
Makefile  readme  release_note.txt  src
ashley@ashley-desktop:~/r8101-1.007.00$ sudo make clean modules
[sudo] password for ashley: 
Sorry, try again.
[sudo] password for ashley: 
make -C src/ clean
make[1]: Entering directory `/home/ashley/r8101-1.007.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers rset
make[1]: Leaving directory `/home/ashley/r8101-1.007.00/src'
make -C src/ modules
make[1]: Entering directory `/home/ashley/r8101-1.007.00/src'
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:41: /src/Makefile: No such file or directory
make[3]: *** No rule to make target `/src/Makefile'.  Stop.
make[2]: *** [_module_/src] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/ashley/r8101-1.007.00/src'
make: *** [modules] Error 2
ashley@ashley-desktop:~/r8101-1.007.00$ 

```

so does anybody know what im doing wrong, or how to fix it?

or has anyone else found a driver that works?

also is there linux driver for the rtl8185 wireless card, or has anybody at least got it working in ndiswraper?  and how?

---

### Post by pytheas22 on 2008-07-01
As far as the wireless goes: there are native drivers for rtl chipsets at [http://rtl8180-sa2400.sourceforge.net/](http://rtl8180-sa2400.sourceforge.net/) .   These [directions from aircrack]("http://www.aircrack-ng.org/doku.php?id=r8187&DokuWiki=356e24d9f2459309396d784224209605") might also get it working (they're for rtl8185, but I think that's the same as rtl8187...but I don't own any realtek cards, so I could be wrong).  I helped someone the other day with an rtl8187 chipset and the first link got him working.

If the native drivers fail (you should check the list of supported cards), you should still be able to use ndiswrapper.

I don't know what's wrong with the ethernet; it looks like there's a problem with that makefile.  But you should almost never have to compile a driver for an ethernet card on Linux; almost every ethernet device in the world should "just work" at this point.  [This thread]("http://ubuntuforums.org/showthread.php?t=569944") and [this thread]("http://ubuntuforums.org/showthread.php?t=843398") may be useful to you.  If not, please post back here with the output of:
```

lspci -nn | grep -e thernet -e etwork
```

---

### Post by tjwoosta on 2008-07-01
> As far as the wireless goes: there are native drivers for rtl chipsets at [http://rtl8180-sa2400.sourceforge.net/](http://rtl8180-sa2400.sourceforge.net/)

i dont see anywhere to download the 8185 driver on this page (it just talks about it)

on my laptop i have rtl8187b wireless, i wonder if the same driver will work for this?


but anyway i figured out the problem with the the 8101e (my ethernet cable was junk)

i tried switching the cable and it works great now

---

### Post by pytheas22 on 2008-07-01
Sorry, I gave you the wrong link for the realtek driver (there is a link to a tarball towards the bottom of the page, but it's outdated anway).  An installation guide for the modern rtl drivers is at [http://rtl-wifi.sourceforge.net/wiki/Installing](http://rtl-wifi.sourceforge.net/wiki/Installing) .

---

### Post by cariboo on 2008-07-01
If it works from the liveCD then it will work after it is installed. You are needlessly trying to compile modules for your nic's. They are included in the kernel. If networking isn't working there is probably a problem with your setup.

The best thing to do is to run the LiveCD and check to see what modules are loaded to do this in a terminal type:

```
lsmod | grep rtl
```

This will give you a good starting point.

Jim

---

### Post by tjwoosta on 2008-07-01
> If it works from the liveCD then it will work after it is installed. You are needlessly trying to compile modules for your nic's. They are included in the kernel. If networking isn't working there is probably a problem with your setup.


it was never working from the live cd on this computer

i was saying that my laptop said it had the same driver and it worked from the live cd

but anyway it turned out that the reason it wasnt working on this computer was because my ethernet cable was junk


so now im focusing on the wireless card

---

### Post by bobnutfield on 2008-07-01
> **tjwoosta said:**
> i dont see anywhere to download the 8185 driver on this page (it just talks about it)

on my laptop i have rtl8187b wireless, i wonder if the same driver will work for this?


but anyway i figured out the problem with the the 8101e (my ethernet cable was junk)

i tried switching the cable and it works great now

There are no native linux drivers for the Realtek 8187b (yet), but you could look here:

[http://www.datanorth.net/~cuervo/rtl8187b/]("http://www.datanorth.net/~cuervo/rtl8187b/")


These drivers have worked for a lot of people, but I did not get very good results from them.  I did, however, get terrific results with Ndiswrapper using the Win98 drivers, with some modification.

Bob

---

### Post by tjwoosta on 2008-07-01
> There are no native linux drivers for the Realtek 8187b (yet), but you could look here:

[http://www.datanorth.net/~cuervo/rtl8187b/](http://www.datanorth.net/~cuervo/rtl8187b/)


These drivers have worked for a lot of people, but I did not get very good results from them. I did, however, get terrific results with Ndiswrapper using the Win98 drivers, with some modification.

yea thats the same driver i am using on my laptop (it works, but is very buggy)

but the my wifi card in this computer is different (its an rtl-8185 not rtl8187b)

but according to pytheas22 the rtl8185 and the rtl8187 might use the same driver (i have yet to try it out, because im not home now)

if anybody has already found a definatly working driver for this wifi card please let me know

---

### Post by bobnutfield on 2008-07-01
> but according to pytheas22 the rtl8185 and the rtl8187 might use the same driver (i have yet to try it out, because im not home now)

Sorry, I may have misunderstood.  At any rate, the rtl8187 driver will NOT work for the rtl8187b, but I do believe that the 8185 and 8187 will work with same driver.

Bob

---

### Post by bigstras on 2008-07-01
i use ndiswrapper for the 8185.  It is simple to install:

```
sudo apt-get install ndisgtk
```

You can find it under System -> Administration -> Windows Wireless Drivers.

Then you just need to get the windows drivers from the realtek website and unpack them to a folder.  

Click on Install New Driver, then go to where you unpacked the windows drivers and choose net8185.inf (thats what it was when i did it, either way it will have a .inf extension).  This will install your drivers and you should be good to go.  you may or may not need to restart afterwards.

---

### Post by tjwoosta on 2008-07-01
>  	
Re: rtl8101e ethernet and/or rtl-8185 wireless help
i use ndiswrapper for the 8185. It is simple to install:


awesome, its good to hear that someone has it working

but which windows driver do i install?

i tried the windows xp driver but it doesnt seem to do anything at all (wireless still is not even an option in network config)

---

### Post by pytheas22 on 2008-07-01
> i tried the windows xp driver but it doesnt seem to do anything at all (wireless still is not even an option in network config)

Did you remember to:
```

sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
```

first?  Otherwise you wouldn't see any wireless connection.

Also, what is the output of:
```

ndiswrapper -l
```

Hopefully it says something like "driver installed, device present" (the device present message is key; it means that ndiswrapper agrees that you have the right Windows driver for your hardware and should work).

---

### Post by tjwoosta on 2008-07-01
>  	
Re: rtl8101e ethernet and/or rtl-8185 wireless help
Quote:
i tried the windows xp driver but it doesnt seem to do anything at all (wireless still is not even an option in network config)
Did you remember to:
Code:

sudo modprobe ndiswrapper
sudo ifconfig wlan0 up

first? Otherwise you wouldn't see any wireless connection.

..no i didn't 

ok so now when i get to sudo ifconfig wlan0 up it does this
```

ashley@ashley-desktop:~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device

```

and this is the output of ndiswrapper -l
```
shley@ashley-desktop:~$ ndiswrapper -l
net8185 : driver installed
	device (10EC:8185) present

```

---

### Post by tjwoosta on 2008-07-01
i just thought of this but does it matter that im using 64bit?

---

### Post by pytheas22 on 2008-07-01
> i just thought of this but does it matter that im using 64bit?

oh, yeah, that [matters a lot]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,faq/#can_i_use_32-bit_windows_driver_in_64-bit_mode").  ndiswrapper will work fine on a 64-bit system, but the Windows drivers also need to be 64-bit, and the one you installed is probably not.  See if you can find a win64 driver for your card and install that.  As far as I know, there's no other way around it.

---

### Post by tjwoosta on 2008-07-01
> oh, yeah, that matters a lot. ndiswrapper will work fine on a 64-bit system, but the Windows drivers also need to be 64-bit, and the one you installed is probably not. See if you can find a win64 driver for your card and install that. As far as I know, there's no other way around it.

ok thanks, i found a win64 driver at the realtek site but when i tried to install it in ndiswrapper it just froze 

after force quitting ndiswrapper i tried again and it froze again, 

now it wont even load the other driver that loaded earlier without freezing

i even tried uninstalling and reinstalling and restarting but it still wont load any drivers without freezing

what happened?

what could be causing this?

---

### Post by pytheas22 on 2008-07-01
I'm not sure what's causing it.  It might help to make sure that the ndiswrapper module is unloaded before trying to install the new driver:
```

sudo rmmod ndiswrapper
```

If that doesn't help, the next thing I would try is either finding a different build of the Windows drivers or installing ndiswrapper from source.  For the latter, you would need to download the [latest stable ndiswrapper release]("http://sourceforge.net/project/downloading.php?group_id=93482&use_mirror=internap&filename=ndiswrapper-1.53.tar.gz&21491019"), and then:
```

sudo apt-get remove --purge ndiswrapper*
sudo apt-get install build-essential
cd ~/Desktop ###or wherever you saved ndiswrapper to
tar -xzvf ndiswrapper*
cd ndis*
make
sudo make install
```

then install the Windows drivers again.

If that still doesn't work, run the command "dmesg" after ndiswrapper freezes; it should contain information about what's wrong.  You can post the dmesg output here if you don't know how to read it yourself.

---

### Post by tjwoosta on 2008-07-01
> If that doesn't help, the next thing I would try is either finding a different build of the Windows drivers or installing ndiswrapper from source

ok i just compiled ndiswrapper but now there is no menu entry 

what is the command to open ndiswrapper?

---

### Post by pytheas22 on 2008-07-01
ndiswrapper is just a command-line program.  The GUI that you used before is called ndisgtk.  You could probably find the source for ndisgtk and compile it if you want, but I don't know where it is (I looked quickly and couldn't find it).  Don't install it through Synaptic, because if you do that it will force you to also install the packages for ndiswrapper, defeating the purpose of compiling from source.

It's easy enough to install the Windows driver without the GUI, however.  Just type:

```

sudo ndiswrapper -i /path/to/.inf/file
```

then run:
```

ndiswrapper -l
```

to make sure it was installed correctly.

---

### Post by tjwoosta on 2008-07-01
thanks pytheas, your a life saver

ok now it loaded the driver fine and ndiswrapper -l said it was good (i thought it was gonna work)

but then when i did sudo modprobe ndiswrapper it just does nothing and the little cursor thing just keeps blinking without going to the next line

this is the output of dmesg in another terminal while modprobe is still running (i have no idea what any of this means or what part you need so ill paste everything that showed up)

```
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bee00000)
[    0.000000] SMP: Allowing 4 CPUs, 3 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 257181
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=2763bff4-a4b4-42c3-a0f2-542e1be1a23f ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] hpet clockevent registered
[    0.000000] TSC calibrated against HPET
[   29.059794] time.c: Detected 1600.057 MHz processor.
[   29.060564] Console: colour VGA+ 80x25
[   29.060568] console [tty0] enabled
[   29.060619] Checking aperture...
[   29.060629] Calgary: detecting Calgary via BIOS EBDA area
[   29.060631] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   29.073439] Memory: 1020912k/1048320k available (2489k kernel code, 27020k reserved, 1318k data, 320k init)
[   29.073483] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
[   29.149643] Calibrating delay using timer specific routine.. 3202.69 BogoMIPS (lpj=6405388)
[   29.149683] Security Framework initialized
[   29.149692] SELinux:  Disabled at boot.
[   29.149707] AppArmor: AppArmor initialized
[   29.149712] Failure registering capabilities with primary security module.
[   29.149847] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   29.150637] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   29.151041] Mount-cache hash table entries: 256
[   29.151220] Initializing cgroup subsys ns
[   29.151227] Initializing cgroup subsys cpuacct
[   29.151244] CPU: L1 I cache: 32K, L1 D cache: 32K
[   29.151246] CPU: L2 cache: 512K
[   29.151249] CPU 0/0 -> Node 0
[   29.151251] using mwait in idle threads.
[   29.151259] CPU0: Thermal monitoring enabled (TM2)
[   29.151277] SMP alternatives: switching to UP code
[   29.152224] Early unpacking initramfs... done
[   29.586136] ACPI: Core revision 20070126
[   29.586186] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   29.640389] Using local APIC timer interrupts.
[   29.702797] APIC timer calibration result 12500443
[   29.702799] Detected 12.500 MHz APIC timer.
[   29.702852] Brought up 1 CPUs
[   29.702914] CPU0 attaching sched-domain:
[   29.702917]  domain 0: span 01
[   29.702919]   groups: 01
[   29.703115] net_namespace: 120 bytes
[   29.703538] Time:  4:40:06  Date: 07/02/08
[   29.703573] NET: Registered protocol family 16
[   29.703850] ACPI: bus type pci registered
[   29.703954] PCI: Using configuration type 1
[   29.707330] ACPI: EC: Look up EC in DSDT
[   29.713285] ACPI: Interpreter enabled
[   29.713289] ACPI: (supports S0 S1 S3 S4 S5)
[   29.713305] ACPI: Using IOAPIC for interrupt routing
[   29.723353] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   29.723910] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[   29.723914] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   29.724537] PCI: Transparent bridge - 0000:00:1e.0
[   29.724566] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   29.724738] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   29.724863] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[   29.734257] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   29.734390] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   29.734521] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   29.734650] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   29.734792] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   29.734926] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   29.735063] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   29.735193] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   29.735372] Linux Plug and Play Support v0.97 (c) Adam Belay
[   29.735418] pnp: PnP ACPI init
[   29.735428] ACPI: bus type pnp registered
[   29.740683] pnp: PnP ACPI: found 16 devices
[   29.740687] ACPI: ACPI bus type pnp unregistered
[   29.741037] PCI: Using ACPI for IRQ routing
[   29.741040] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   29.750821] NET: Registered protocol family 8
[   29.750824] NET: Registered protocol family 20
[   29.750889] PCI-GART: No AMD northbridge found.
[   29.750895] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   29.750900] hpet0: 3 64-bit timers, 14318180 Hz
[   29.751943] AppArmor: AppArmor Filesystem Enabled
[   29.754799] Time: tsc clocksource has been installed.
[   29.754815] Switched to high resolution mode on CPU 0
[   29.762846] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[   29.762861] system 00:08: ioport range 0xa00-0xa0f has been reserved
[   29.762865] system 00:08: ioport range 0xa10-0xa1f has been reserved
[   29.762869] system 00:08: ioport range 0xa20-0xa2f has been reserved
[   29.762873] system 00:08: ioport range 0xa30-0xa3f has been reserved
[   29.762882] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[   29.762886] system 00:09: ioport range 0x800-0x87f has been reserved
[   29.762890] system 00:09: ioport range 0x480-0x4bf has been reserved
[   29.762894] system 00:09: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   29.762899] system 00:09: iomem range 0xfed20000-0xfed8ffff has been reserved
[   29.762909] system 00:0c: iomem range 0xffc00000-0xfff7ffff could not be reserved
[   29.762917] system 00:0d: iomem range 0xfec00000-0xfec00fff has been reserved
[   29.762922] system 00:0d: iomem range 0xfee00000-0xfee00fff could not be reserved
[   29.762931] system 00:0e: iomem range 0xe0000000-0xe3ffffff has been reserved
[   29.762940] system 00:0f: iomem range 0x0-0x9ffff could not be reserved
[   29.762944] system 00:0f: iomem range 0xc0000-0xcffff has been reserved
[   29.762948] system 00:0f: iomem range 0xe0000-0xfffff could not be reserved
[   29.762952] system 00:0f: iomem range 0x100000-0x3fffffff could not be reserved
[   29.762957] system 00:0f: iomem range 0x0-0x0 could not be reserved
[   29.763551] PCI: Bridge: 0000:00:01.0
[   29.763554]   IO window: c000-cfff
[   29.763558]   MEM window: f0000000-fe9fffff
[   29.763560]   PREFETCH window: d8000000-dfffffff
[   29.763564] PCI: Bridge: 0000:00:1c.0
[   29.763566]   IO window: d000-dfff
[   29.763570]   MEM window: fea00000-feafffff
[   29.763574]   PREFETCH window: disabled.
[   29.763578] PCI: Bridge: 0000:00:1e.0
[   29.763581]   IO window: e000-efff
[   29.763585]   MEM window: feb00000-febfffff
[   29.763588]   PREFETCH window: disabled.
[   29.763611] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   29.763616] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   29.763633] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   29.763638] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   29.763647] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   29.763660] NET: Registered protocol family 2
[   29.798825] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   29.799283] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   29.800818] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   29.801600] TCP: Hash tables configured (established 131072 bind 65536)
[   29.801604] TCP reno registered
[   29.810918] checking if image is initramfs... it is
[   30.655098] Freeing initrd memory: 7552k freed
[   30.659796] audit: initializing netlink socket (disabled)
[   30.659810] audit(1214973607.536:1): initialized
[   30.662321] VFS: Disk quotas dquot_6.5.1
[   30.662424] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   30.662599] io scheduler noop registered
[   30.662601] io scheduler anticipatory registered
[   30.662603] io scheduler deadline registered
[   30.662749] io scheduler cfq registered (default)
[   30.663007] Boot video device is 0000:01:00.0
[   30.663167] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   30.663201] assign_interrupt_mode Found MSI capability
[   30.663229] Allocate Port Service[0000:00:01.0:pcie00]
[   30.663321] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   30.663360] assign_interrupt_mode Found MSI capability
[   30.663391] Allocate Port Service[0000:00:1c.0:pcie00]
[   30.663440] Allocate Port Service[0000:00:1c.0:pcie02]
[   30.709160] Real Time Clock Driver v1.12ac
[   30.709410] hpet_resources: 0xfed00000 is busy
[   30.709441] Linux agpgart interface v0.102
[   30.709443] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   30.711058] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   30.711142] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   30.711274] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   30.711605] serio: i8042 KBD port at 0x60,0x64 irq 1
[   30.711610] serio: i8042 AUX port at 0x60,0x64 irq 12
[   30.721450] mice: PS/2 mouse device common for all mice
[   30.721510] cpuidle: using governor ladder
[   30.721513] cpuidle: using governor menu
[   30.721721] NET: Registered protocol family 1
[   30.721852] registered taskstats version 1
[   30.721964]   Magic number: 0:708:665
[   30.722075] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   30.722079] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   30.722080] EDD information not available.
[   30.722091] Freeing unused kernel memory: 320k freed
[   30.749258] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   31.957064] fuse init (API version 7.9)
[   31.980606] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   31.980618] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   31.980627] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   32.566426] usbcore: registered new interface driver usbfs
[   32.566450] usbcore: registered new interface driver hub
[   32.582371] usbcore: registered new device driver usb
[   32.590390] r8169 Gigabit Ethernet driver 2.2LK loaded
[   32.590423] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   32.590442] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   32.590720] eth0: RTL8101e at 0xffffc200004f0000, 00:1b:b9:a5:ad:18, XID 34200000 IRQ 509
[   32.606344] USB Universal Host Controller Interface driver v3.0
[   32.606411] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
[   32.606423] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   32.606427] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   32.606711] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   32.606744] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000bc00
[   32.606879] usb usb1: configuration #1 chosen from 1 choice
[   32.606903] hub 1-0:1.0: USB hub found
[   32.606909] hub 1-0:1.0: 2 ports detected
[   32.690354] SCSI subsystem initialized
[   32.710246] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   32.710258] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   32.710262] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   32.710288] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   32.710316] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000b880
[   32.710421] usb usb2: configuration #1 chosen from 1 choice
[   32.710445] hub 2-0:1.0: USB hub found
[   32.710451] hub 2-0:1.0: 2 ports detected
[   32.746060] libata version 3.00 loaded.
[   32.814071] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   32.814083] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   32.814087] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   32.814117] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   32.814145] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b800
[   32.814253] usb usb3: configuration #1 chosen from 1 choice
[   32.814277] hub 3-0:1.0: USB hub found
[   32.814283] hub 3-0:1.0: 2 ports detected
[   32.917886] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   32.917898] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   32.917902] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   32.917931] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   32.917963] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000b480
[   32.918072] usb usb4: configuration #1 chosen from 1 choice
[   32.918099] hub 4-0:1.0: USB hub found
[   32.918105] hub 4-0:1.0: 2 ports detected
[   33.021867] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[   33.021958] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   33.021964] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   33.022013] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   33.025916] ehci_hcd 0000:00:1d.7: debug port 1
[   33.025921] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   33.025928] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xefffbc00
[   33.041601] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   33.041720] usb usb5: configuration #1 chosen from 1 choice
[   33.041744] hub 5-0:1.0: USB hub found
[   33.041750] hub 5-0:1.0: 8 ports detected
[   33.145674] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   33.145711] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   33.145722] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   33.145749] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   33.145769] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   33.145778] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   33.152296] ata_piix 0000:00:1f.1: version 2.12
[   33.152314] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   33.152350] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   33.155033] scsi0 : ata_piix
[   33.155972] scsi1 : ata_piix
[   33.157380] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   33.157385] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   33.485418] ata1.00: ATA-6: ST340015A, 3.01, max UDMA/100
[   33.485422] ata1.00: 78165360 sectors, multi 16: LBA 
[   33.485439] ata1.01: ATAPI: HL-DT-ST RW/DVD GCC-4320B, 1.01, max UDMA/33
[   33.501290] ata1.00: configured for UDMA/100
[   33.672874] ata1.01: configured for UDMA/33
[   33.839324] scsi 0:0:0:0: Direct-Access     ATA      ST340015A        3.01 PQ: 0 ANSI: 5
[   33.840250] scsi 0:0:1:0: CD-ROM            HL-DT-ST RW/DVD GCC-4320B 1.01 PQ: 0 ANSI: 5
[   33.840351] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   33.840373] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   33.840410] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   33.840858] scsi2 : ata_piix
[   33.841096] scsi3 : ata_piix
[   33.842289] ata3: SATA max UDMA/133 cmd 0xb400 ctl 0xb080 bmdma 0xa880 irq 19
[   33.842293] ata4: SATA max UDMA/133 cmd 0xb000 ctl 0xac00 bmdma 0xa888 irq 19
[   34.181875] Driver 'sd' needs updating - please use bus_type methods
[   34.181959] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   34.181971] sd 0:0:0:0: [sda] Write Protect is off
[   34.181974] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   34.181990] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.182038] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   34.182048] sd 0:0:0:0: [sda] Write Protect is off
[   34.182050] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   34.182066] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.182071]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   34.214788]  sda1 sda2 < sda5 >
[   34.241315] sd 0:0:0:0: [sda] Attached SCSI disk
[   34.247463] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   34.247483] sr 0:0:1:0: Attached scsi generic sg1 type 5
[   34.249302] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   34.249307] Uniform CD-ROM driver Revision: 3.20
[   34.249368] sr 0:0:1:0: Attached scsi CD-ROM sr0
[   34.813606] Attempting manual resume
[   34.813610] swsusp: Resume From Partition 8:5
[   34.813612] PM: Checking swsusp image.
[   34.813797] PM: Resume from disk failed.
[   34.827020] EXT3-fs: INFO: recovery required on readonly filesystem.
[   34.827025] EXT3-fs: write access will be enabled during recovery.
[   41.074067] kjournald starting.  Commit interval 5 seconds
[   41.074086] EXT3-fs: sda1: orphan cleanup on readonly fs
[   41.096871] ext3_orphan_cleanup: deleting unreferenced inode 835755
[   41.100757] EXT3-fs: sda1: 1 orphan inode deleted
[   41.100761] EXT3-fs: recovery complete.
[   41.102477] EXT3-fs: mounted filesystem with ordered data mode.
[   50.093367] ip_tables: (C) 2000-2006 Netfilter Core Team
[   50.154815] nf_conntrack version 0.5.0 (8192 buckets, 32768 max)
[   50.962295] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   51.019115] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   51.406628] input: Power Button (FF) as /devices/virtual/input/input2
[   51.416518] ACPI: Power Button (FF) [PWRF]
[   51.416646] input: Power Button (CM) as /devices/virtual/input/input3
[   51.428430] ACPI: Power Button (CM) [PWRB]
[   52.269630] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   52.526720] [fglrx] Maximum main memory to use for locked dma buffers: 922 MBytes.
[   52.526761] [fglrx] ASYNCIO init succeed!
[   52.526907] [fglrx] PAT is enabled successfully!
[   52.526931] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   53.057920] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   53.058019] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   53.091629] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   53.369370] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   53.426022] iTCO_vendor_support: vendor-support=0
[   53.477206] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   53.477294] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0860)
[   53.477326] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   53.535437] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   53.621076] intel_rng: FWH not detected
[   53.656961] usbcore: registered new interface driver ndiswrapper
[   54.545854] input: PS/2 Generic Mouse as /devices/platform/i8042/serio1/input/input5
[   56.958083] lp: driver loaded but no devices found
[   57.178097] Adding 1646620k swap on /dev/sda5.  Priority:-1 extents:1 across:1646620k
[   57.743949] EXT3 FS on sda1, internal journal
[   59.331170] No dock devices found.
[   61.012784] ppdev: user-space parallel port driver
[   61.362890] audit(1214973638.538:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4882 profile="/usr/sbin/cupsd" namespace="default"
[   62.230956] r8169: eth0: link up
[   62.230969] r8169: eth0: link up
[   62.383624] Bluetooth: Core ver 2.11
[   62.384224] NET: Registered protocol family 31
[   62.384228] Bluetooth: HCI device and connection manager initialized
[   62.384232] Bluetooth: HCI socket layer initialized
[   62.417363] Bluetooth: L2CAP ver 2.9
[   62.417368] Bluetooth: L2CAP socket layer initialized
[   62.514916] Bluetooth: RFCOMM socket layer initialized
[   62.514935] Bluetooth: RFCOMM TTY layer initialized
[   62.514936] Bluetooth: RFCOMM ver 1.8
[   65.199738] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   66.748144] NET: Registered protocol family 17
[   68.649714] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[   68.649721] [fglrx] Reserve Block - 1 offset =  0X7fff000 length = 0X1000
[   68.649723] [fglrx] Reserve Block - 2 offset =  0X7fbf000 length = 0X40000
[   68.865136] [fglrx] interrupt source 20008000 successfully enabled
[   68.865144] [fglrx] enable ID = 0x00000004
[   68.865151] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[   68.865211] [fglrx] interrupt source 10000000 successfully enabled
[   68.865213] [fglrx] enable ID = 0x00000005
[   68.865218] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[   71.172369] NET: Registered protocol family 10
[   71.172657] lo: Disabled Privacy Extensions
[   81.484756] eth0: no IPv6 routers present
[  186.375222] usbcore: deregistering interface driver ndiswrapper
[ 2535.751712] compiz.real[5837]: segfault at 1 rip 40fee0 rsp 7fff6cc04890 error 4
[ 2536.023536] [fglrx] interrupt source 10000000 successfully disabled!
[ 2536.023544] [fglrx] enable ID = 0x00000000
[ 2536.023547] [fglrx] Receive disable interrupt message with irqEnableMask: 10000000; dwIRQEnableId: 00000005
[ 2536.023904] [fglrx] interrupt source 20008000 successfully disabled!
[ 2536.023908] [fglrx] enable ID = 0x00000000
[ 2536.023910] [fglrx] Receive disable interrupt message with irqEnableMask: 20008000; dwIRQEnableId: 00000004
[ 2540.336411] [fglrx] PCIe has already been initialized. Reinitializing ...
[ 2540.344321] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[ 2540.344329] [fglrx] Reserve Block - 1 offset =  0X7fff000 length = 0X1000
[ 2540.344331] [fglrx] Reserve Block - 2 offset =  0X7fbf000 length = 0X40000
[ 2540.438827] [fglrx] interrupt source 20008000 successfully enabled
[ 2540.438835] [fglrx] enable ID = 0x00000004
[ 2540.439118] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[ 2540.439342] [fglrx] interrupt source 10000000 successfully enabled
[ 2540.439348] [fglrx] enable ID = 0x00000005
[ 2540.439580] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[ 7295.210719] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[ 7295.236686] ndiswrapper (link_pe_images:575): fixing KI_USER_SHARED_DATA address in the driver
[ 7295.238005] ndiswrapper: driver net8185x64 (Realtek,03/21/2008,5.1105.0321.2008) loaded
[ 7295.238329] ACPI: PCI Interrupt 0000:03:02.0[A] -> GSI 19 (level, low) -> IRQ 19
[ 7295.508647] ndiswrapper: using IRQ 19
[ 7300.240442] general protection fault: 0000 [1] SMP 
[ 7300.240449] CPU 0 
[ 7300.240451] Modules linked in: ndiswrapper snd_rtctimer binfmt_misc ipv6 xt_limit xt_tcpudp ipt_LOG ipt_MASQUERADE ipt_TOS ipt_REJECT nf_conntrack_irc nf_conntrack_ftp xt_state af_packet rfcomm l2cap bluetooth ppdev cpufreq_powersave cpufreq_conservative cpufreq_ondemand cpufreq_userspace cpufreq_stats freq_table sbs sbshc dock container video output battery ac parport_pc lp parport evdev serio_raw psmouse pcspkr iTCO_wdt iTCO_vendor_support snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_hwdep snd_seq_dummy fglrx(P) snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device button snd soundcore shpchp pci_hotplug intel_agp iptable_nat nf_nat nf_conntrack_ipv4 nf_conntrack iptable_mangle iptable_filter ip_tables x_tables ext3 jbd mbcache sg sr_mod cdrom sd_mod ata_piix ata_generic pata_acpi libata scsi_mod ehci_hcd uhci_hcd r8169 usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[ 7300.240523] Pid: 7342, comm: ntos_wq Tainted: P        2.6.24-19-generic #1
[ 7300.240526] RIP: 0010:[<ffffc20000e4eb8a>]  [<ffffc20000e4eb8a>]
[ 7300.240532] RSP: 0018:ffff81000b203be8  EFLAGS: 00010246
[ 7300.240535] RAX: 0000c20000e83538 RBX: ffffc20000e90000 RCX: ffffc20000e90000
[ 7300.240537] RDX: ffff81003bf36000 RSI: ffffc20000e90000 RDI: 0000000000004000
[ 7300.240540] RBP: ffffffff8062f7c0 R08: 0000000000000000 R09: ffff81003bd10000
[ 7300.240543] R10: ffffffff885b86c0 R11: ffff81000b203dc0 R12: ffff810002604980
[ 7300.240546] R13: 0000000000000000 R14: 0000000000000000 R15: 0000000000000010
[ 7300.240550] FS:  0000000000000000(0000) GS:ffffffff805b9000(0000) knlGS:0000000000000000
[ 7300.240553] CS:  0010 DS: 0018 ES: 0018 CR0: 0000000080050033
[ 7300.240556] CR2: 00007f134ce7a000 CR3: 000000003bb94000 CR4: 00000000000006e0
[ 7300.240558] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[ 7300.240561] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[ 7300.240565] Process ntos_wq (pid: 7342, threadinfo ffff81000b202000, task ffff81003dcecfc0)
[ 7300.240567] Stack:  ebc03128c48348d2 c308c48348c031c9 0f74c0850424448b 00000001042444c7
[ 7300.240583]  48000000c0908b4d 410424448d4c078b 48f28900000004b9 4128ec834818488b
[ 7300.240587]  c03128c48348d2ff 2e6666c308c48348 0000000000841f0f 314508ec8348d231
[ 7300.240590] Call Trace:
[ 7300.240612]  [<ffffffff80231c9e>] update_curr+0xee/0x100
[ 7300.240620]  [<ffffffff80247b44>] lock_timer_base+0x34/0x70
[ 7300.240625]  [<ffffffff80247d12>] __mod_timer+0xc2/0xe0
[ 7300.240628]  [<ffffffff80231c21>] update_curr+0x71/0x100
[ 7300.240661]  [<ffffffff885b6c54>] :ndiswrapper:deserialized_irq_handler+0x14/0x30
[ 7300.240690]  [<ffffffff885cb9c2>] :ndiswrapper:win2lin4+0x14/0x17
[ 7300.240712]  [<ffffffff885bc461>] :ndiswrapper:kdpc_worker+0xc1/0x140
[ 7300.240720]  [<ffffffff80466fe9>] mutex_lock+0x9/0x20
[ 7300.240740]  [<ffffffff885bc448>] :ndiswrapper:kdpc_worker+0xa8/0x140
[ 7300.240762]  [<ffffffff885bc3a0>] :ndiswrapper:kdpc_worker+0x0/0x140
[ 7300.240766]  [<ffffffff8024f2bc>] run_workqueue+0xcc/0x170
[ 7300.240770]  [<ffffffff8024fe40>] worker_thread+0x0/0x110
[ 7300.240776]  [<ffffffff8024fe40>] worker_thread+0x0/0x110
[ 7300.240780]  [<ffffffff8024fee3>] worker_thread+0xa3/0x110
[ 7300.240785]  [<ffffffff80253a00>] autoremove_wake_function+0x0/0x30
[ 7300.240791]  [<ffffffff8024fe40>] worker_thread+0x0/0x110
[ 7300.240795]  [<ffffffff8024fe40>] worker_thread+0x0/0x110
[ 7300.240799]  [<ffffffff8025363b>] kthread+0x4b/0x80
[ 7300.240804]  [<ffffffff8020d198>] child_rip+0xa/0x12
[ 7300.240815]  [<ffffffff802535f0>] kthread+0x0/0x80
[ 7300.240819]  [<ffffffff8020d18e>] child_rip+0x0/0x12
[ 7300.240823] 
[ 7300.240824] 
[ 7300.240824] Code: 66 0f 7f b4 24 a0 01 00 00 0f 84 5d 04 00 00 66 66 90 66 66 
[ 7300.240832] RIP  [<ffffc20000e4eb8a>]
[ 7300.240834]  RSP <ffff81000b203be8>
[ 7300.240838] ---[ end trace a99bcef44d2d733d ]---
ashley@ashley-desktop:~$ 

```

---

### Post by pytheas22 on 2008-07-02
Sorry to hear about the trouble.

I see in dmesg the line:
```

general protection fault
```

right after ndiswrapper was modprobed, which is bad news.  It means there's some kind of generic error when trying to insert the ndiswrapper module that you probably won't be able to track down unless you go into the ndiswrapper code, and I have no idea how to do that.

There are a few simple things to try to see if they make a difference.  First, reboot the machine without the card plugged in--ndiswrapper should be automatically loaded when it reboots--and then plug the card in and see if it works.

If it still doesn't, try:
```

sudo rmmod ndiswrapper
sudo depmod -a
sudo modprobe ndiswrapper
```

and try plugging the card in again.

Beyond that, it might still help to use a different release of the win64 driver to see if it makes a difference.  Otherwise, you can try an earlier release of ndiswrapper (so far I think you've tried 1.52, from the repositories, and 1.53, built from source)--it could be the case that there's some bug in the versions you've tried that's causing these errors.

If these things still don't work, I don't know what else to try unless you want to do a hardcore debugging session with ndiswrapper, which as I said I'm not qualified to do.  I'd recommend either trying harder to get the native rlt to work or installing a 32-bit kernel.

---

### Post by tjwoosta on 2008-07-04
ok. so alot of things happened since my last post

(ill fill you all in just incase anybody tries to fallow this thread to get there card working)


after messing with ndiswrapper trying to load the driver i gave up and i shutdown the computer

when i turned it on today it would get as far as the ubuntu loading bar and freeze

i tried recovery mode but that froze too

i even tried an old kernal but that also froze

so after asking for help in another thread i tracked the problem to ndiswrapper

i had to boot the live cd, mount my ubuntu partition and add the line "blacklist ndiswrapper" without quotes to /etc/modprobe.d/blacklist

then i ran make uninstall to remove ndiswrapper

then undid the blacklisting of ndiswrapper

then i tried a few different linux drivers i found using google

**the realtek website one would not work** (it would say error 2 when i tried to run ./makedrv)

eventually i found one from this site that did work
[http://www.willdaniels.co.uk/articles/10-howto/12-r8180-hardy]("http://www.willdaniels.co.uk/articles/10-howto/12-r8180-hardy")

all is excellent now

so thanks for all your help guys

---

