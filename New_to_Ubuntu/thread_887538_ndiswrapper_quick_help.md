---
title: "ndiswrapper quick help"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by WinterMadness on 2008-08-12
im on kubuntu, but this should work for any of them
and i know i have a wireless card that works on this computer, i just removed the wubi version(ubuntu last time) and now have its own partition and i gotta set everything up again

im following this guide
[http://www.kubuntu.org/doc/7.10/network/C/connect-wifi.html](http://www.kubuntu.org/doc/7.10/network/C/connect-wifi.html)

i have ndiswrapper and i found bcmwl6.inf on my computer and i typed in sudo ndiswrapper -i bcmwl6.inf and i get this

driver bcmwl6 is already installed

THEN i try modprobe and this happens...
sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.


why is there no module and how do i go about creating one

---

### Post by caljohnsmith on 2008-08-12
I would try reinstalling ndiswrapper at this point if I were you. Try the following:
```
sudo apt-get purge ndiswrapper-utils-1.9 ndiswrapper-common
sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common
```
Then try reinstalling your Windows driver with ndiswrapper, and then doing the modprobe.

---

### Post by WinterMadness on 2008-08-12
> **caljohnsmith said:**
> I would try reinstalling ndiswrapper at this point if I were you. Try the following:
```
sudo apt-get purge ndiswrapper-utils-1.9 ndiswrapper-common
sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common
```
Then try reinstalling your Windows driver with ndiswrapper, and then doing the modprobe.


unfortunately im getting the same result
i remember the last time i did this i had to create something with "ndiswrapper" inside it. is this the same thing, and do i have to do that again?

i remember why i hated doing this so much haha

---

### Post by caljohnsmith on 2008-08-12
Did you originally install ndiswrapper through the repositories, or did you download and compile it yourself? 

If you do:
```
modinfo ndiswrapper
```
What does it return?

---

### Post by WinterMadness on 2008-08-12
> **caljohnsmith said:**
> Did you originally install ndiswrapper through the repositories, or did you download and compile it yourself? 

If you do:
```
modinfo ndiswrapper
```
What does it return?

```

ghost@laptop:~$ modinfo ndiswrapper
modinfo: could not find module ndiswrapper
ghost@laptop:~$ 


```

i think it might be important to say that I also dont have the option of "enable wireless" on network manager while using gnome. im just trying to give you as much info as possible.

but my wireless indicator on my laptop is on. weird

---

### Post by caljohnsmith on 2008-08-12
Can you tell me anything else about what might be different about your installation, or anything else that is not working? Just to clarify, is your Ubuntu a fresh install to a new partition at this point (no more Wubi)? Anything you've done recently related to using modprobe? Please post the output of:
```
which ndiswrapper
find /lib/modules/`uname -r` -iname '*ndiswrapper*'

```

---

### Post by appi2012 on 2008-08-12
do this to create a module for ndiswrapper:
```
sudo ndiswrapper -m
```

---

### Post by WinterMadness on 2008-08-12
> **caljohnsmith said:**
> Can you tell me anything else about what might be different about your installation, or anything else that is not working? Just to clarify, is your Ubuntu a fresh install to a new partition at this point (no more Wubi)? Anything you've done recently related to using modprobe? Please post the output of:
```
which ndiswrapper
find /lib/modules/`uname -r` -iname '*ndiswrapper*'

```

ghost@laptop:~$ which ndiswrapper
/usr/sbin/ndiswrapper
ghost@laptop:~$ find /lib/modules/`uname -r` -iname '*ndiswrapper*'
ghost@laptop:~$ 


the way i installed it was with the Kubuntu disc. i have both gnome and kde. but wireless dosent work in either of them. it is a partition, not wubi. its real weird, cuz when i used wubi everything worked and even on ym other computer everything works. but on this particular installation everything seems to want to crap out on me. i followed the guided partition method.

---

### Post by WinterMadness on 2008-08-12
> **appi2012 said:**
> do this to create a module for ndiswrapper:
```
sudo ndiswrapper -m
```

ghost@laptop:~$ sudo ndiswrapper -m
module configuration already contains alias directive

---

### Post by caljohnsmith on 2008-08-12
What other problems are you having besides wireless issues? Try:
```
find /lib/modules/ -iname '*ndiswrapper*'
```
That will search all your kernel module libraries (not just the kernel you are using like the previous command I gave) for ndiswrapper. If that doesn't find anything, again do:
```
sudo apt-get purge ndiswrapper-utils-1.9 ndiswrapper-common
sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common
```
But copy and paste the exact results from your terminal back here of running those commands.

---

### Post by WinterMadness on 2008-08-12
> **caljohnsmith said:**
> What other problems are you having besides wireless issues? Try:
```
find /lib/modules/ -iname '*ndiswrapper*'
```
That will search all your kernel module libraries (not just the kernel you are using like the previous command I gave) for ndiswrapper. If that doesn't find anything, again do:
```
sudo apt-get purge ndiswrapper-utils-1.9 ndiswrapper-common
sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common
```
But copy and paste the exact results from your terminal back here of running those commands.


ghost@laptop:~$ find /lib/modules/ -iname '*ndiswrapper*'
/lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper
/lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
ghost@laptop:~$ 
ghost@laptop:~$ sudo apt-get purge ndiswrapper-utils-1.9 ndiswrapper-common
[sudo] password for ghost: 

ghost@laptop:~$ sudo apt-get purge ndiswrapper-utils-1.9 ndiswrapper-common
[sudo] password for ghost: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ndiswrapper-common* ndiswrapper-utils-1.9*
0 upgraded, 0 newly installed, 2 to remove and 176 not upgraded.
After this operation, 213kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 135227 files and directories currently installed.)
Removing ndiswrapper-utils-1.9 ...
Removing ndiswrapper-common ...
dpkg - warning: while removing ndiswrapper-common, directory `/etc/ndiswrapper' not empty so not removed.


ghost@laptop:~$ sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndiswrapper-common ndiswrapper-utils-1.9
0 upgraded, 2 newly installed, 0 to remove and 176 not upgraded.
Need to get 0B/30.4kB of archives.
After this operation, 213kB of additional disk space will be used.
Selecting previously deselected package ndiswrapper-common.
(Reading database ... 135206 files and directories currently installed.)
Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.50-1ubuntu1_all.deb) ...
Selecting previously deselected package ndiswrapper-utils-1.9.
Unpacking ndiswrapper-utils-1.9 (from .../ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb) ...
Setting up ndiswrapper-common (1.50-1ubuntu1) ...
Setting up ndiswrapper-utils-1.9 (1.50-1ubuntu1) ...

ghost@laptop:~$

---

### Post by caljohnsmith on 2008-08-12
Well, that find command did find ndiswrapper in your 2.6.24-16-generic module library. But since you went and reinstalled, I can't be sure where or if the ndiswrapper module is installed now. Try the following:
```
uname -r
find /lib/modules/ -iname '*ndiswrapper*'
```
Also check to see if the problem has fixed itself with all the reinstalling, by installing your Windows driver and then modprobing:
```
sudo ndiswrapper -i <driver>.inf
ndiswrapper -l
sudo modprobe ndiswrapper
```
Please copy and paste the exact results of all the commands.

---

### Post by WinterMadness on 2008-08-12
> **caljohnsmith said:**
> Well, that find command did find ndiswrapper in your 2.6.24-16-generic module library. But since you went and reinstalled, I can't be sure where or if the ndiswrapper module is installed now. Try the following:
```
uname -r
find /lib/modules/ -iname '*ndiswrapper*'
```
Also check to see if the problem has fixed itself with all the reinstalling, by installing your Windows driver and then modprobing:
```
sudo ndiswrapper -i <driver>.inf
ndiswrapper -l
sudo modprobe ndiswrapper
```
Please copy and paste the exact results of all the commands.

ghost@laptop:~$ uname -r
2.6.24-16-386
ghost@laptop:~$ find /lib/modules/ -iname '*ndiswrapper*'
/lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper
/lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
ghost@laptop:~$ sudo ndiswrapper -i /media/OS/DELL/drivers/R174292/DRIVER_ROW/bcmwl6.inf
driver bcmwl6 is already installed
ghost@laptop:~$ ndiswrapper -l
bcmwl6 : driver installed
        device (14E4:4315) present
ghost@laptop:~$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
ghost@laptop:~$


also, when i click on the network manager i dont have the option of enabling wireless networks. i dont know if that info will help u or not

---

### Post by caljohnsmith on 2008-08-12
When you start up your computer and get the Grub menu, does one of the menu entries for Ubuntu list using the "2.6.24-16-generic" kernel? If so, use that kernel when you boot next time instead of using the 2.6.24-16-386 that you're in right now. Then try modprobing ndiswrapper. 

If you are unsure or don't have the Ubuntu w/ 2.6.24-16-generic option at startup, please post the contents of your /boot/grub/menu.lst. You can do that with:
```
cat /boot/grub/menu.lst
```
Also post the results of the following commands:
```
ls -l /boot
ls -l /lib/modules
```

---

### Post by WinterMadness on 2008-08-12
> **caljohnsmith said:**
> When you start up your computer and get the Grub menu, does one of the menu entries for Ubuntu list using the "2.6.24-16-generic" kernel? If so, use that kernel when you boot next time instead of using the 2.6.24-16-386 that you're in right now. Then try modprobing ndiswrapper. 

If you are unsure or don't have the Ubuntu w/ 2.6.24-16-generic option at startup, please post the contents of your /boot/grub/menu.lst. You can do that with:
```
cat /boot/grub/menu.lst
```
Also post the results of the following commands:
```
ls -l /boot
ls -l /lib/modules
```


the mod probe worked since i used the other one in the grub menu like you said, heres the result

ghost@laptop:~$ ls -l /boot
total 29608
-rw-r--r-- 1 root root  419412 2008-04-10 12:47 abi-2.6.24-16-386
-rw-r--r-- 1 root root  422607 2008-04-10 12:51 abi-2.6.24-16-generic
-rw-r--r-- 1 root root   79985 2008-04-10 12:47 config-2.6.24-16-386
-rw-r--r-- 1 root root   79964 2008-04-10 12:51 config-2.6.24-16-generic
drwxr-xr-x 2 root  999    4096 2008-08-12 01:47 grub
-rw-r--r-- 1 root root 7538551 2008-08-12 01:47 initrd.img-2.6.24-16-386
-rw-r--r-- 1 root root 7883328 2008-08-12 00:19 initrd.img-2.6.24-16-generic
-rw-r--r-- 1 root  999 8167811 2008-08-11 13:37 initrd.img-2.6.24-16-generic.bak
-rw-r--r-- 1 root root  103204 2007-09-28 06:06 memtest86+.bin
-rw-r--r-- 1 root root  880159 2008-04-10 12:47 System.map-2.6.24-16-386
-rw-r--r-- 1 root root  899892 2008-04-10 12:51 System.map-2.6.24-16-generic
-rw-r--r-- 1 root root 1837720 2008-04-10 12:47 vmlinuz-2.6.24-16-386
-rw-r--r-- 1 root root 1904248 2008-04-10 12:51 vmlinuz-2.6.24-16-generic
ghost@laptop:~$ ls -l /lib/modules
total 8
drwxr-xr-x 6 root root 4096 2008-08-12 09:05 2.6.24-16-386
drwxr-xr-x 7 root root 4096 2008-08-11 13:36 2.6.24-16-generic
ghost@laptop:~$ 




the only problem is now i dont know what else to do toget wireless working.

---

### Post by appi2012 on 2008-08-12
Try typing:
```
sudo rm -i /etc/modprobe.d/ndiswrapper
sudo ndiswrapper -m
sudo modprobe ndiswrapper
```

---

### Post by appi2012 on 2008-08-12
Does the option to enable wireless appear after doing the modprobe?

---

### Post by WinterMadness on 2008-08-12
> **appi2012 said:**
> Does the option to enable wireless appear after doing the modprobe?

no, I dont have wlan0 either. but like i said before, ive had this very computer use wireless on ubuntu before, same version and everything.

when i click on knetwork manager i get the option to disable them, but no wireless networks show up. on gnome, i dont get the option to enable it. its not even there for some reason.

---

### Post by caljohnsmith on 2008-08-12
OK, I'm back, glad that the modprobe worked at least now that you switched kernels. How about posting:
```
ifconfig
iwconfig
sudo iwlist scan
```
When you installed your Windows driver with ndiswrapper, did you have the .sys file in the same directory as the .inf file?

---

### Post by WinterMadness on 2008-08-12
> **caljohnsmith said:**
> OK, I'm back, glad that the modprobe worked at least now that you switched kernels. How about posting:
```
ifconfig
iwconfig
sudo iwlist scan
```
When you installed your Windows driver with ndiswrapper, did you have the .sys file in the same directory as the .inf file?



eth0      Link encap:Ethernet  HWaddr 00:1e:c9:03:db:0e
          inet addr:192.168.1.37  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:c9ff:fe03:db0e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21360 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17961 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:17734002 (16.9 MB)  TX bytes:2907901 (2.7 MB)
          Interrupt:17

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:346 errors:0 dropped:0 overruns:0 frame:0
          TX packets:346 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:17300 (16.8 KB)  TX bytes:17300 (16.8 KB)

ghost@laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ghost@laptop:~$ sudo iwlist scan
[sudo] password for ghost:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ghost@laptop:~$

---

### Post by caljohnsmith on 2008-08-12
Modprobing the ndiswrapper should have created a wlan0 interface, but it didn't seem to work. How about the output of:
```
dmesg | tail -100
dmesg | grep error
dmesg | grep wlan0

```

---

### Post by WinterMadness on 2008-08-12
> **caljohnsmith said:**
> Modprobing the ndiswrapper should have created a wlan0 interface, but it didn't seem to work. How about the output of:
```
dmesg | tail -100
dmesg | grep error
dmesg | grep wlan0

```

ghost@laptop:~$ dmesg | tail -100
[   25.342492] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   25.376295] iTCO_vendor_support: vendor-support=0
[   25.377642] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   25.378397] input: PS/2 Mouse as /devices/virtual/input/input3
[   25.495941] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input4
[   25.532588] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   25.532639] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   25.532676] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   25.638057] ACPI: Battery Slot [BAT0] (battery present)
[   25.638160] input: Lid Switch as /devices/virtual/input/input5
[   25.658852] ACPI: Lid Switch [LID]
[   25.658904] input: Power Button (CM) as /devices/virtual/input/input6
[   25.722325] ACPI: Power Button (CM) [PBTN]
[   25.722391] input: Sleep Button (CM) as /devices/virtual/input/input7
[   25.786248] ACPI: Sleep Button (CM) [SBTN]
[   25.786399] ACPI: AC Adapter [AC] (on-line)
[   25.954178] ACPI: WMI-Acer: Mapper loaded
[   26.204059] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2e/LNXVIDEO:00/input/input8
[   26.253817] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   26.263267] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input9
[   26.317757] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   26.317890] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:02/input/input10
[   26.369791] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   26.373771] nvidia: module license 'NVIDIA' taints kernel.
[   26.674226] sdhci: Secure Digital Host Controller Interface driver
[   26.674229] sdhci: Copyright(c) Pierre Ossman
[   26.674267] sdhci: SDHCI controller found at 0000:03:01.1 [1180:0822] (rev 22)
[   26.674290] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 22
[   26.677341] mmc0: SDHCI at 0xf9aff500 irq 22 DMA
[   26.723913] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   26.723924] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   26.724011] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   26.934015] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 20
[   26.934033] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   27.567432] lp: driver loaded but no devices found
[   27.677584] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   27.776989] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[   27.777000] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   27.777008] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   27.777015] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   27.777022] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   27.777041] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   27.777051] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[   27.777062] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[   27.777070] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   27.777077] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   27.777087] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   27.777094] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[   27.777105] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   27.777116] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   27.777123] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   27.777130] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[   27.777137] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   27.777152] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   27.777165] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   27.777174] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   27.777181] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   27.777188] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   27.777195] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   27.777206] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   27.777216] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   27.777219] ndiswrapper (load_sys_files:210): couldn't prepare driver 'bcmwl6'
[   27.777741] ndiswrapper (load_wrap_driver:112): couldn't load driver bcmwl6; check system log for messages from 'loadndisdriver'
[   27.780062] usbcore: registered new interface driver ndiswrapper
[   27.827720] Adding 995988k swap on /dev/sda7.  Priority:-1 extents:1 across:995988k
[   28.341846] EXT3 FS on sda6, internal journal
[   28.479544] device-mapper: uevent: version 1.0.3
[   28.479569] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: [email]dm-devel@redhat.com[/email]
[   29.306850] ip_tables: (C) 2000-2006 Netfilter Core Team
[   29.706125] No dock devices found.
[   30.722202] apm: BIOS not found.
[   30.837655] ppdev: user-space parallel port driver
[   30.941996] audit(1218565870.029:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5348 profile="/usr/sbin/cupsd" namespace="default"
[   33.232649] Bluetooth: Core ver 2.11
[   33.232954] NET: Registered protocol family 31
[   33.232956] Bluetooth: HCI device and connection manager initialized
[   33.232959] Bluetooth: HCI socket layer initialized
[   33.256348] Bluetooth: L2CAP ver 2.9
[   33.256356] Bluetooth: L2CAP socket layer initialized
[   33.397978] Bluetooth: RFCOMM socket layer initialized
[   33.398000] Bluetooth: RFCOMM TTY layer initialized
[   33.398003] Bluetooth: RFCOMM ver 1.8
[   33.787286] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   33.787297] tg3: eth0: Flow control is on for TX and on for RX.
[   35.094590] NET: Registered protocol family 17
[   37.326421] NET: Registered protocol family 10
[   37.327583] lo: Disabled Privacy Extensions
[   41.143920] eth0: no IPv6 routers present
[  343.424614] CPU0 attaching NULL sched-domain.
[  343.424633] CPU1 attaching NULL sched-domain.
[  343.428514] CPU0 attaching sched-domain:
[  343.428530]  domain 0: span 03
[  343.428540]   groups: 01 02
[  343.428547]   domain 1: span 03
[  343.428555]    groups: 03
[  343.428560] CPU1 attaching sched-domain:
[  343.428567]  domain 0: span 03
[  343.428571]   groups: 02 01
[  343.428582]   domain 1: span 03
[  343.428586]    groups: 03
ghost@laptop:~$ dmesg | grep error
[   11.980037] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
ghost@laptop:~$ dmesg | grep wlan0
ghost@laptop:~$     

i appreciate all the help youre giving!

---

### Post by caljohnsmith on 2008-08-12
Your welcome for the help; I like to help out when I have time as my way of giving back to the Ubuntu community. :)

I think I might know what is going on now that I've seen your ndiswrapper errors in dmesg; let me ask first--are you using the Windows Vista driver with ndiswrapper? Because if so, that is what is the problem I think. Try using the Windows XP driver. If you don't have it I'm sure there is some place on the web where you can download it. Be sure to first uninstall your present driver with the following before installing the Win XP version:
```
sudo ndiswrapper -r bcmwl6.inf
```

---

### Post by WinterMadness on 2008-08-12
thanks for helping. it was the driver at fault, I needed to download the XP one. wireless is up and running

---

