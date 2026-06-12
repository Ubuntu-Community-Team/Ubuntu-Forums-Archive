---
title: "Ubuntu 14.04 - Dell Venue 11 Pro - Fail to recognize Wifi"
date: 2014-06-21
forum: New to Ubuntu
---

### Post by mike-pc-reardon on 2014-06-21
Hi

Seeking to dual boot Dell Venue 11 Pro.  Figured out how to get Ubuntu set up on UEFI, Secure boot set up.  Have live USB version up and running but can't get WIFI recognized.

Have a Dell Wireless 1537, which is manufactured by Qualcomm Atheros.  

So how to I get this recognized, is there a simple terminal edit to do?  There are no hard or soft block.

Any help is appreciated.

Mike

---

### Post by wildmanne39 on 2014-06-21
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz)depending on the size of the file and it will be placed in your home folder. The wireless information will help to diagnose your wireless issue, the Mac address, WPA key and WEP key are removed for your security, then reply back, click on the paper clip and attach the (wireless-info.txt, or wireless-info.txt.tar.gz) file as a zip file. 

If you do not have ethernet connection then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385).
Thanks

---

### Post by mike-pc-reardon on 2014-06-22
Thanks for the response


Great Avatar


I will review 2nd option since I'm attempting dual boot install per another set of instructions - which led me to this issue.  


I'll report  back.

---

### Post by mike-pc-reardon on 2014-06-22
Had to move file to Live USB from another computer, then to Windows OS on target computer.  Created a Linux folder that I can see in Windows8.1 and Live USB Ubuntu


Found Ubuntu 14.04 Nautilus however has no menu - File, Edit etc. don't exist, so could not run script.  Had to figure out how to change behavior, which didn't work in the end.


Educated myself to do so in terminal, only to get permission denied, figured out sh command.


**Here is the file:**




```
########## wireless info START ##########


##### release #####


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04 LTS
Release:	14.04
Codename:	trusty


##### kernel #####


Linux ubuntu 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####




##### lsusb #####


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 413c:81a9 Dell Computer Corp. 
Bus 001 Device 005: ID 114d:1000 Alpha Imaging Technology Corp. 
Bus 001 Device 004: ID 06cb:2819 Synaptics, Inc. 
Bus 001 Device 003: ID 0bda:5751 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 13fe:3e00 Kingston Technology Company Inc. Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA Card Info #####




##### rfkill #####


0: nfc0: NFC
	Soft blocked: no
	Hard blocked: no


##### lsmod #####




##### iw reg get #####


country 00:
	(2402 - 2472 @ 40), (6, 20)
	(2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN, NO-IBSS
	(5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS
	(5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS


##### interfaces #####


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


##### iwconfig #####




##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #####




##### nm-tool #####


NetworkManager Tool


State: disconnected




##### NetworkManager.state #####


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf #####


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### iwlist #####




##### iwlist channel #####




##### modinfo #####




##### modules #####






##### blacklist #####
```


**Meantime **research would seem to indicate that my Dell Wireless 1537 802.11 a/g/n Adapter is manufactured by Qualcom Atheros 3.7.2.45422  2013-10-17.  This seems to relate to Atheros AR6004 model, which I believe equivalent linux driver is ath9k.  If correct, then I assume I need to figure out how to set this up within Live USB in order to properly install dual boot. Please advise

---

### Post by wildmanne39 on 2014-06-22
I do not see a wireless device, which is not good. If you want to use ubuntu on a flash drive you will need to make it persistent. Is your wireless card built in? Dell computers usually have a broadcom wireless device.

---

### Post by mike-pc-reardon on 2014-06-23
Hi

My goal is to dual boot Dell Venue 11 Pro with Windows 8.1 - with Ubuntu.

Began with USB Flash drive just to see how it might operate, and so far: had to modify grub to nomodeset just to get in and see it on screen.  Once in looks good, except no wifi should I wish to install at this point.  

I have access to a USB wireless, but yes this problem is with wireless built in or described as follows: Dell Wireless 1537 802.11 a/g/n Adapter.  Is there a linux driver for this wireless adapter?

---

### Post by wildmanne39 on 2014-06-23
Boot the liveusb of ubuntu and run:
```
lspci -nnk
```
Then post the output here using code tags.
Thanks

---

### Post by Vladlenin5000 on 2014-06-23
*subscribed*

---

### Post by wildmanne39 on 2014-06-23
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by mike-pc-reardon on 2014-06-23
Hi

Sorry I'm not sure how to do what you asked: "[COLOR=#000000]Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header.  [/COLOR][COLOR=#000000]If using Quick Reply then ```
 at the beginning and 
``` at the end."

[/COLOR]However the lspci -nnk is cut and paste below, hopefully in satisfactory fashion.

Additionally my research uncovered the following:

Dell Wireless 1537 802.11 a/g/n Adapter is manufactured by Qualcom Atheros 3.7.2.45422  2013-10-17 or model AR6004 that I originally thought was handled by linux driver ath9k.  Further research has establihed 'ath6kl' is the FullMAC wireless driver for Atheros AR600x family of chips, for example AR6003, AR6004 and AR6005. Source is [http://wireless.kernel.org/en/users/Drivers/ath6kl](http://wireless.kernel.org/en/users/Drivers/ath6kl).

But I'm not skilled enough to know how to set it up in a live Ubuntu USB session according to the "Starting from Linux kernel 3.2 ath6kl is available from kernel menuconfig" source here: 
[http://forum.xda-developers.com/showthread.php?t=1032471](http://forum.xda-developers.com/showthread.php?t=1032471)

**If you can help with above and below that would be great.  Thanks in advance**

ubuntu@ubuntu:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Haswell-ULT DRAM Controller [8086:0a04] (rev 0b)
    Subsystem: Dell Device [1028:0604]
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:0a1e] (rev 0b)
    Subsystem: Dell Device [1028:0604]
00:03.0 Audio device [0403]: Intel Corporation Haswell-ULT HD Audio Controller [8086:0a0c] (rev 0b)
    Subsystem: Dell Device [1028:0604]
    Kernel driver in use: snd_hda_intel
00:14.0 USB controller [0c03]: Intel Corporation Lynx Point-LP USB xHCI HC [8086:9c31] (rev 04)
    Subsystem: Dell Device [1028:0604]
    Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation Lynx Point-LP HECI #0 [8086:9c3a] (rev 04)
    Subsystem: Dell Device [1028:0604]
    Kernel driver in use: mei_me
00:1b.0 Audio device [0403]: Intel Corporation Lynx Point-LP HD Audio Controller [8086:9c20] (rev 04)
    Subsystem: Dell Device [1028:0604]
    Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 4 [8086:9c16] (rev e4)
    Kernel driver in use: pcieport
00:1f.0 ISA bridge [0601]: Intel Corporation Lynx Point-LP LPC Controller [8086:9c43] (rev 04)
    Subsystem: Dell Device [1028:0604]
    Kernel driver in use: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] [8086:9c03] (rev 04)
    Subsystem: Dell Device [1028:0604]
    Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation Lynx Point-LP SMBus Controller [8086:9c22] (rev 04)
    Subsystem: Dell Device [1028:0604]
01:00.0 SD Host controller [0805]: O2 Micro, Inc. Device [1217:8621] (rev 01)
    Subsystem: O2 Micro, Inc. Device [1217:0002]
    Kernel driver in use: sdhci-pci
ubuntu@ubuntu:~$

---

### Post by wildmanne39 on 2014-06-23
Is that all the output from that command? there is no wireless device or ethernet device. Are you using the ethernet? If you got the most advance new computer out then your devices probably are not support in ubuntu yet.

But they should still show up when you run that command from the terminal in ubuntu.
I will do some research.

---

### Post by Vladlenin5000 on 2014-06-24
Is it possible to an hibernated Windows 8.1 to hijack the devices? It shouldn't but I wouldn't be surprised if it did...

---

### Post by wildmanne39 on 2014-06-24
> **Vladlenin5000 said:**
> Is it possible to an hibernated Windows 8.1 to hijack the devices? It shouldn't but I wouldn't be surprised if it did...That is possible, but when that happens it usually just blocks the device but in this case it does not even show one is installed. It will not do any good to try to install a driver if the device is not showing up.

Please post the complete output of:
```
dmesg
``` 
from a cold boot.
Thanks

---

### Post by mike-pc-reardon on 2014-06-24
Hi

I've since gone ahead and installed Ubuntu.  There remains issues with boot such as editing for nomodeset.

What remains is wifi still doesn't work.  The following is DMESG results:

[    0.697369] system 00:0c: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.697372] system 00:0c: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.697376] system 00:0c: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.697380] system 00:0c: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.697383] system 00:0c: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.697387] system 00:0c: [mem 0xff000000-0xffffffff] has been reserved
[    0.697391] system 00:0c: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.697395] system 00:0c: [mem 0xf7fee000-0xf7feefff] has been reserved
[    0.697398] system 00:0c: [mem 0xf7fd0000-0xf7fdffff] has been reserved
[    0.697403] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.729138] pnp: PnP ACPI: found 13 devices
[    0.729144] ACPI: bus type PNP unregistered
[    0.735921] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.735938] pci 0000:00:1c.0:   bridge window [mem 0xf7c00000-0xf7cfffff]
[    0.735952] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.735954] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.735956] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.735959] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.735961] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.735963] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.735965] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff]
[    0.735967] pci_bus 0000:00: resource 11 [mem 0x000d0000-0x000d3fff]
[    0.735969] pci_bus 0000:00: resource 12 [mem 0x000d4000-0x000d7fff]
[    0.735971] pci_bus 0000:00: resource 13 [mem 0x000d8000-0x000dbfff]
[    0.735973] pci_bus 0000:00: resource 14 [mem 0x000dc000-0x000dffff]
[    0.735976] pci_bus 0000:00: resource 15 [mem 0xdf200000-0xfeafffff]
[    0.735978] pci_bus 0000:01: resource 1 [mem 0xf7c00000-0xf7cfffff]
[    0.736015] NET: Registered protocol family 2
[    0.736204] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
[    0.736307] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    0.736387] TCP: Hash tables configured (established 32768 bind 32768)
[    0.736409] TCP: reno registered
[    0.736421] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.736442] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.736506] NET: Registered protocol family 1
[    0.736520] pci 0000:00:02.0: Boot video device
[    0.739209] PCI: CLS 64 bytes, default 64
[    0.739267] Trying to unpack rootfs image as initramfs...
[    1.168945] Freeing initrd memory: 18596K (ffff88003edd2000 - ffff88003fffb000)
[    1.168954] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.168959] software IO TLB [mem 0xc917f000-0xcd17f000] (64MB) mapped at [ffff8800c917f000-ffff8800cd17efff]
[    1.169189] microcode: CPU0 sig=0x40651, pf=0x40, revision=0x17
[    1.169200] microcode: CPU1 sig=0x40651, pf=0x40, revision=0x17
[    1.169212] microcode: CPU2 sig=0x40651, pf=0x40, revision=0x17
[    1.169223] microcode: CPU3 sig=0x40651, pf=0x40, revision=0x17
[    1.169282] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.169287] Scanning for low memory corruption every 60 seconds
[    1.169573] Initialise system trusted keyring
[    1.169625] audit: initializing netlink socket (disabled)
[    1.169636] type=2000 audit(1403611363.160:1): initialized
[    1.208125] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.209620] VFS: Disk quotas dquot_6.5.2
[    1.209671] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.210152] fuse init (API version 7.22)
[    1.210239] msgmni has been set to 7739
[    1.210297] Key type big_key registered
[    1.210758] Key type asymmetric registered
[    1.210762] Asymmetric key parser 'x509' registered
[    1.210798] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.210843] io scheduler noop registered
[    1.210847] io scheduler deadline registered (default)
[    1.210875] io scheduler cfq registered
[    1.211125] pcieport 0000:00:1c.0: irq 56 for MSI/MSI-X
[    1.211248] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    1.211252] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    1.211265] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    1.211279] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.211296] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.211344] efifb: probing for efifb
[    1.213058] efifb: framebuffer at 0xe0000000, mapped to 0xffffc90004880000, using 8100k, total 8100k
[    1.213062] efifb: mode is 1920x1080x32, linelength=7680, pages=1
[    1.213064] efifb: scrolling: redraw
[    1.213067] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    1.220361] Console: switching to colour frame buffer device 240x67
[    1.226994] fb0: EFI VGA frame buffer device
[    1.227035] intel_idle: MWAIT substates: 0x11142120
[    1.227036] intel_idle: v0.4 model 0x45
[    1.227038] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.227207] ipmi message handler version 39.2
[    1.228287] ACPI: AC Adapter [AC] (on-line)
[    1.228482] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.229204] ACPI: Lid Switch [LID0]
[    1.229272] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.229325] ACPI: Power Button [PBTN]
[    1.229413] ACPI: Fan [FAN] (off)
[    1.262416] thermal LNXTHERM:00: registered as thermal_zone0
[    1.262457] ACPI: Thermal Zone [THM] (56 C)
[    1.262533] GHES: HEST is not enabled!
[    1.262703] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.266815] Linux agpgart interface v0.103
[    1.268662] brd: module loaded
[    1.269475] loop: module loaded
[    1.269892] libphy: Fixed MDIO Bus: probed
[    1.270010] tun: Universal TUN/TAP device driver, 1.6
[    1.270041] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.270179] PPP generic driver version 2.4.2
[    1.270309] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.270380] ehci-pci: EHCI PCI platform driver
[    1.270446] ehci-platform: EHCI generic platform driver
[    1.270516] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.270585] ohci-pci: OHCI PCI platform driver
[    1.270625] ohci-platform: OHCI generic platform driver
[    1.270668] uhci_hcd: USB Universal Host Controller Interface driver
[    1.270911] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.270976] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    1.271159] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    1.271189] xhci_hcd 0000:00:14.0: irq 57 for MSI/MSI-X
[    1.271273] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.271321] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.271364] usb usb1: Product: xHCI Host Controller
[    1.271396] usb usb1: Manufacturer: Linux 3.13.0-24-generic xhci_hcd
[    1.271454] usb usb1: SerialNumber: 0000:00:14.0
[    1.271862] hub 1-0:1.0: USB hub found
[    1.271911] hub 1-0:1.0: 9 ports detected
[    1.284105] ACPI: Battery Slot [BAT0] (battery present)
[    1.319052] ACPI: Battery Slot [BAT1] (battery present)
[    1.685280] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.685322] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    1.685587] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    1.685632] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.685676] usb usb2: Product: xHCI Host Controller
[    1.687341] usb usb2: Manufacturer: Linux 3.13.0-24-generic xhci_hcd
[    1.689009] usb usb2: SerialNumber: 0000:00:14.0
[    1.690875] hub 2-0:1.0: USB hub found
[    1.692378] hub 2-0:1.0: 4 ports detected
[    1.696926] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.698577] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.700939] i8042: Warning: Keylock active
[    1.702987] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.705001] mousedev: PS/2 mouse device common for all mice
[    1.707052] rtc_cmos 00:05: RTC can wake from S4
[    1.708974] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.710706] rtc_cmos 00:05: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.712483] device-mapper: uevent: version 1.0.3
[    1.714282] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: [email]dm-devel@redhat.com[/email]
[    1.714651] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.717855] ledtrig-cpu: registered to indicate activity on CPUs
[    1.719591] EFI Variables Facility v0.08 2004-May-17
[    1.725704] TCP: cubic registered
[    1.727522] NET: Registered protocol family 10
[    1.729437] NET: Registered protocol family 17
[    1.731126] Key type dns_resolver registered
[    1.733475] Loading compiled-in X.509 certificates
[    1.736309] Loaded X.509 cert 'Magrathea: Glacier signing key: 00a5a65759de474bc5c43120880c1b94a539f431'
[    1.738061] registered taskstats version 1
[    1.743295] Key type trusted registered
[    1.747660] Key type encrypted registered
[    1.752009] AppArmor: AppArmor sha1 policy hashing enabled
[    1.753525] IMA: No TPM chip found, activating TPM-bypass!
[    1.757092] regulator-dummy: disabling
[    1.758888]   Magic number: 2:38:27
[    1.760664] rtc_cmos 00:05: setting system clock to 2014-06-24 12:02:44 UTC (1403611364)
[    1.763391] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.765086] EDD information not available.
[    1.766643] PM: Hibernation image not present or could not be loaded.
[    1.767756] Freeing unused kernel memory: 1332K (ffffffff81d1e000 - ffffffff81e6b000)
[    1.769269] Write protecting the kernel read-only data: 12288k
[    1.774012] Freeing unused kernel memory: 844K (ffff88000172d000 - ffff880001800000)
[    1.778061] Freeing unused kernel memory: 708K (ffff880001b4f000 - ffff880001c00000)
[    1.799806] systemd-udevd[115]: starting version 204
[    1.818720] sdhci: Secure Digital Host Controller Interface driver
[    1.820924] sdhci: Copyright(c) Pierre Ossman
[    1.826800] sdhci-acpi INT33C6:00: dummy supplies not allowed
[    1.826801] mmc0: no vqmmc regulator found
[    1.826804] sdhci-acpi INT33C6:00: dummy supplies not allowed
[    1.826805] mmc0: no vmmc regulator found
[    1.827921] mmc0: SDHCI controller on ACPI [INT33C6:00] using ADMA
[    1.837593] sdhci-pci 0000:01:00.0: SDHCI controller found [1217:8621] (rev 1)
[    1.844588] ahci 0000:00:1f.2: version 3.0
[    1.854852] mmc1: Unknown controller version (3). You may experience problems.
[    1.855114] ahci 0000:00:1f.2: irq 58 for MSI/MSI-X
[    1.855173] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 3 ports 6 Gbps 0x1 impl SATA mode
[    1.855177] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo only pio slum part deso sadm sds apst 
[    1.862686] sdhci-pci 0000:01:00.0: dummy supplies not allowed
[    1.864508] mmc1: no vqmmc regulator found
[    1.866337] sdhci-pci 0000:01:00.0: dummy supplies not allowed
[    1.868158] mmc1: no vmmc regulator found
[    1.871887] mmc1: SDHCI controller on PCI [0000:01:00.0] using ADMA
[    1.925094] scsi0 : ahci
[    1.927038] scsi1 : ahci
[    1.928962] scsi2 : ahci
[    1.930829] ata1: SATA max UDMA/133 abar m2048@0xf7d1a000 port 0xf7d1a100 irq 58
[    1.932685] ata2: DUMMY
[    1.934516] ata3: DUMMY
[    1.969775] mmc0: queuing unknown CIS tuple 0x01 (3 bytes)
[    1.979406] mmc0: queuing unknown CIS tuple 0x1a (5 bytes)
[    1.984605] mmc0: queuing unknown CIS tuple 0x1b (8 bytes)
[    1.987063] mmc0: queuing unknown CIS tuple 0x14 (0 bytes)
[    1.995072] mmc0: queuing unknown CIS tuple 0x80 (1 bytes)
[    1.996664] usb 1-3: new high-speed USB device number 2 using xhci_hcd
[    1.998670] mmc0: queuing unknown CIS tuple 0x81 (1 bytes)
[    2.000494] mmc0: queuing unknown CIS tuple 0x82 (1 bytes)
[    2.002259] mmc0: new high speed SDIO card at address 0001
[    2.045433] usb 1-3: New USB device found, idVendor=0bda, idProduct=5751
[    2.051472] usb 1-3: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[    2.057831] usb 1-3: Product: Integrated Webcam
[    2.065736] usb 1-3: Manufacturer: CN0WDCKY7248741R034CA00
[    2.070013] usb 1-3: SerialNumber: 200901010001
[    2.168617] tsc: Refined TSC clocksource calibration: 1496.536 MHz
[    2.248613] usb 1-4: new full-speed USB device number 3 using xhci_hcd
[    2.252554] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.254889] ata1.00: ACPI cmd ef/10:09:00:00:00:b0 (SET FEATURES) succeeded
[    2.255712] ata1.00: ATA-8: SanDisk SD6SP1M128G1012, X231312, max UDMA/133
[    2.257435] ata1.00: 250069680 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    2.260185] ata1.00: ACPI cmd ef/10:09:00:00:00:b0 (SET FEATURES) succeeded
[    2.261597] ata1.00: configured for UDMA/133
[    2.263569] scsi 0:0:0:0: Direct-Access     ATA      SanDisk SD6SP1M1 X231 PQ: 0 ANSI: 5
[    2.265314] sd 0:0:0:0: [sda] 250069680 512-byte logical blocks: (128 GB/119 GiB)
[    2.265319] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.267534] usb 1-4: New USB device found, idVendor=06cb, idProduct=2819
[    2.267537] usb 1-4: New USB device strings: Mfr=0, Product=2, SerialNumber=3
[    2.267539] usb 1-4: Product: Synaptics T Pad V 01.31
[    2.267542] usb 1-4: SerialNumber: 066EFF484956775087043935
[    2.267680] usb 1-4: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    2.267685] usb 1-4: ep 0x83 - rounding interval to 64 microframes, ep desc says 80 microframes
[    2.267688] usb 1-4: ep 0x3 - rounding interval to 64 microframes, ep desc says 80 microframes
[    2.282640] mmc1: Problem setting current limit!
[    2.283496] mmc1: new ultra high speed DDR50 SDHC card at address aaaa
[    2.297778] mmcblk0: mmc1:aaaa SU32G 29.7 GiB 
[    2.297834] hidraw: raw HID events driver (C) Jiri Kosina
[    2.297852] sd 0:0:0:0: [sda] Write Protect is off
[    2.297855] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.297876] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.299666]  sda: sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda8
[    2.300741] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.313048]  mmcblk0: p1
[    2.316666] usbcore: registered new interface driver usbhid
[    2.318567] usbhid: USB HID core driver
[    2.325372] input: Synaptics T Pad V 01.31 as /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.1/input/input3
[    2.327478] hid-generic 0003:06CB:2819.0002: input,hidraw0: USB HID v1.10 Keyboard [Synaptics T Pad V 01.31] on usb-0000:00:14.0-4/input1
[    2.330338] input: Synaptics T Pad V 01.31 as /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.2/input/input4
[    2.333962] hid-generic 0003:06CB:2819.0003: input,hiddev0,hidraw1: USB HID v1.10 Device [Synaptics T Pad V 01.31] on usb-0000:00:14.0-4/input2
[    2.361083] EXT4-fs (sda6): INFO: recovery required on readonly filesystem
[    2.363051] EXT4-fs (sda6): write access will be enabled during recovery
[    2.384490] usb 1-5: new high-speed USB device number 4 using xhci_hcd
[    2.401218] usb 1-5: New USB device found, idVendor=114d, idProduct=1000
[    2.401852] EXT4-fs (sda6): orphan cleanup on readonly fs
[    2.401980] EXT4-fs (sda6): 4 orphan inodes deleted
[    2.401981] EXT4-fs (sda6): recovery complete
[    2.406109] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    2.410722] usb 1-5: New USB device strings: Mfr=1, Product=0, SerialNumber=0
[    2.410723] usb 1-5: Manufacturer: 00000000000000000000000
[    2.507117] random: init urandom read with 68 bits of entropy available
[    2.520506] usb 1-6: new high-speed USB device number 5 using xhci_hcd
[    2.540682] usb 1-6: config 1 has an invalid interface number: 8 but max is 3
[    2.543427] usb 1-6: config 1 has no interface number 1
[    2.547738] init: plymouth-upstart-bridge main process (177) terminated with status 1
[    2.547985] usb 1-6: config 2 has an invalid interface number: 12 but max is 1
[    2.547988] usb 1-6: config 2 has an invalid interface number: 13 but max is 1
[    2.547990] usb 1-6: config 2 has an invalid interface number: 13 but max is 1
[    2.547992] usb 1-6: config 2 has no interface number 0
[    2.547994] usb 1-6: config 2 has no interface number 1
[    2.558704] usb 1-6: New USB device found, idVendor=413c, idProduct=81a9
[    2.558707] usb 1-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.558710] usb 1-6: Product: Dell Wireless 5808e Gobi\xffffffe2\xffffff84\xffffffa2\xffffff84\xffffffa2 4G LTE Mobile Broadband Card
[    2.558712] usb 1-6: Manufacturer: Sierra Wireless, Incorporated
[    2.567224] init: plymouth-upstart-bridge main process ended, respawning
[    2.578883] init: plymouth-upstart-bridge main process (187) terminated with status 1
[    2.580882] init: plymouth-upstart-bridge main process ended, respawning
[    2.590882] init: plymouth-upstart-bridge main process (196) terminated with status 1
[    2.592927] init: plymouth-upstart-bridge main process ended, respawning
[    2.598950] init: plymouth-upstart-bridge main process (199) terminated with status 1
[    2.601060] init: plymouth-upstart-bridge main process ended, respawning
[    2.751910] Adding 7812092k swap on /dev/sda7.  Priority:-1 extents:1 across:7812092k SSFS
[    2.858636] systemd-udevd[318]: starting version 204
[    2.927406] random: nonblocking pool is initialized
[    2.933940] lp: driver loaded but no devices found
[    2.946335] INT33C4:00: ttyS4 at MMIO 0xfe10b000 (irq = 21, base_baud = 6250000) is a 16550A
[    2.948596] ppdev: user-space parallel port driver
[    2.996575] INT33C5:00: ttyS5 at MMIO 0xfe10d000 (irq = 21, base_baud = 6250000) is a 16550A
[    3.008570] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[    3.071887] wmi: Mapper loaded
[    3.090067] [drm] Initialized drm 1.1.0 20060810
[    3.124710] mei_me 0000:00:16.0: irq 59 for MSI/MSI-X
[    3.136549] ACPI Warning: 0x0000000000001828-0x000000000000182f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
[    3.136561] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    3.136568] ACPI Warning: 0x0000000000001c30-0x0000000000001c3f SystemIO conflicts with Region \GPRL 1 (20131115/utaddress-251)
[    3.136574] ACPI Warning: 0x0000000000001c30-0x0000000000001c3f SystemIO conflicts with Region \GPR_ 2 (20131115/utaddress-251)
[    3.136580] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    3.136583] ACPI Warning: 0x0000000000001c00-0x0000000000001c2f SystemIO conflicts with Region \GPRL 1 (20131115/utaddress-251)
[    3.136588] ACPI Warning: 0x0000000000001c00-0x0000000000001c2f SystemIO conflicts with Region \GPR_ 2 (20131115/utaddress-251)
[    3.136594] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    3.136597] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    3.147612] mei_me 0000:00:16.0: NFC MEI VERSION: IVN 0x1 Vendor ID 0x1 Type 0x1
[    3.158471] snd_hda_intel 0000:00:03.0: enabling device (0000 -> 0002)
[    3.158783] HDA driver get symbol successfully from i915 module
[    3.158787] ------------[ cut here ]------------
[    3.158821] WARNING: CPU: 2 PID: 47 at /build/buildd/linux-3.13.0/drivers/gpu/drm/i915/intel_pm.c:5817 i915_request_power_well+0x77/0x80 [i915]()
[    3.158823] Modules linked in: snd_hda_intel(+) snd_seq_device snd_hda_codec snd_hwdep snd_pcm i915 nls_iso8859_1 lpc_ich mei_me snd_page_alloc snd_timer drm_kms_helper mei snd drm soundcore i2c_algo_bit wmi i2c_hid(+) parport_pc ppdev video 8250_dw i2c_designware_platform i2c_designware_core lp mac_hid parport intel_rst hid_generic usbhid hid mmc_block ahci libahci sdhci_pci sdhci_acpi sdhci
[    3.158862] CPU: 2 PID: 47 Comm: kworker/2:1 Not tainted 3.13.0-24-generic #46-Ubuntu
[    3.158865] Hardware name: Dell Inc. Venue 11 Pro 7130 MS/057KTY, BIOS A11 04/16/2014
[    3.158873] Workqueue: events azx_probe_work [snd_hda_intel]
[    3.158875]  0000000000000009 ffff8801190b7d50 ffffffff81715a64 0000000000000000
[    3.158882]  ffff8801190b7d88 ffffffff810676bd 0000000000000000 0000000000000000
[    3.158886]  0000000000000000 ffff8801195ba000 ffff88003fb19800 ffff8801190b7d98
[    3.158891] Call Trace:
[    3.158899]  [<ffffffff81715a64>] dump_stack+0x45/0x56
[    3.158905]  [<ffffffff810676bd>] warn_slowpath_common+0x7d/0xa0
[    3.158909]  [<ffffffff8106779a>] warn_slowpath_null+0x1a/0x20
[    3.158934]  [<ffffffffa01ecea7>] i915_request_power_well+0x77/0x80 [i915]
[    3.158943]  [<ffffffffa0252e42>] hda_display_power+0x32/0x40 [snd_hda_intel]
[    3.158949]  [<ffffffffa02517b1>] azx_probe_continue+0x41/0x960 [snd_hda_intel]
[    3.158954]  [<ffffffff81097498>] ? finish_task_switch+0x128/0x170
[    3.158962]  [<ffffffffa0252bd5>] azx_probe_work+0x15/0x20 [snd_hda_intel]
[    3.158967]  [<ffffffff810838a2>] process_one_work+0x182/0x450
[    3.158972]  [<ffffffff81084641>] worker_thread+0x121/0x410
[    3.158977]  [<ffffffff81084520>] ? rescuer_thread+0x3e0/0x3e0
[    3.158982]  [<ffffffff8108b312>] kthread+0xd2/0xf0
[    3.158986]  [<ffffffff8108b240>] ? kthread_create_on_node+0x1d0/0x1d0
[    3.158991]  [<ffffffff8172637c>] ret_from_fork+0x7c/0xb0
[    3.158995]  [<ffffffff8108b240>] ? kthread_create_on_node+0x1d0/0x1d0
[    3.158998] ---[ end trace 1ca57edbf0e55c30 ]---
[    3.159051] snd_hda_intel 0000:00:03.0: irq 60 for MSI/MSI-X
[    3.159369] snd_hda_intel 0000:00:1b.0: irq 61 for MSI/MSI-X
[    3.161227] EXT4-fs (sda8): mounted filesystem with ordered data mode. Opts: (null)
[    3.170798] Switched to clocksource tsc
[    3.214128] Linux video capture interface: v2.00
[    3.214806] SKU: Nid=0x1d sku_cfg=0x40e00001
[    3.214813] SKU: port_connectivity=0x1
[    3.214816] SKU: enable_pcbeep=0x0
[    3.214820] SKU: check_sum=0x00000000
[    3.214822] SKU: customization=0x00000000
[    3.214824] SKU: external_amp=0x0
[    3.214828] SKU: platform_type=0x0
[    3.214830] SKU: swap=0x0
[    3.214831] SKU: override=0x1
[    3.215273] autoconfig: line_outs=1 (0x1b/0x0/0x0/0x0/0x0) type:line
[    3.215277]    speaker_outs=1 (0x14/0x0/0x0/0x0/0x0)
[    3.215280]    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[    3.215283]    mono: mono_out=0x0
[    3.215285]    inputs:
[    3.215288]      Mic=0x12
[    3.215291] realtek: No valid SSID, checking pincfg 0x40e00001 for NID 0x1d
[    3.215294] realtek: Enabling init ASM_ID=0x0001 CODEC_ID=10ec0283
[    3.238687] input: Synaptics T Pad V 01.31 as /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.0/input/input5
[    3.239159] input: HDA Intel HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/sound/card0/input7
[    3.239325] input: HDA Intel HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input6
[    3.239425] hid-multitouch 0003:06CB:2819.0001: input,hiddev0,hidraw2: USB HID v1.11 Mouse [Synaptics T Pad V 01.31] on usb-0000:00:14.0-4/input0
[    3.240652] uvcvideo: Found UVC 1.00 device Integrated Webcam (0bda:5751)
[    3.240681] uvcvideo: No valid video chain found.
[    3.240725] uvcvideo: Found UVC 1.00 device <unnamed> (114d:1000)
[    3.241505] input: UVC Camera (114d:1000) as /devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5:1.0/input/input9
[    3.243125] usbcore: registered new interface driver uvcvideo
[    3.243128] USB Video Class driver (1.1.1)
[    3.248528] usbcore: registered new interface driver cdc_ncm
[    3.260163] usbcore: registered new interface driver cdc_wdm
[    3.264698] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input11
[    3.265940] input: HDA Intel PCH Dock Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card1/input10
[    3.268330] cdc_mbim 1-6:2.12: cdc-wdm2: USB WDM device
[    3.268552] cdc_mbim 1-6:2.12 wwan0: register 'cdc_mbim' at usb-0000:00:14.0-6, CDC MBIM, 86:a3:7f:8b:eb:7d
[    3.268591] usbcore: registered new interface driver cdc_mbim
[    3.302501] input: SYNA7500:00 06CB:3AF0 Pen as /devices/pci0000:00/INT33C3:00/i2c-1/i2c-SYNA7500:00/input/input12
[    3.302688] input: SYNA7500:00 06CB:3AF0 as /devices/pci0000:00/INT33C3:00/i2c-1/i2c-SYNA7500:00/input/input13
[    3.303143] hid-multitouch 0018:06CB:3AF0.0005: input,hidraw3: <UNKNOWN> HID v1.00 Device [SYNA7500:00 06CB:3AF0] on 
[    3.367106] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    3.450186] Bluetooth: Core ver 2.17
[    3.450217] NET: Registered protocol family 31
[    3.450220] Bluetooth: HCI device and connection manager initialized
[    3.450231] Bluetooth: HCI socket layer initialized
[    3.450235] Bluetooth: L2CAP socket layer initialized
[    3.450243] Bluetooth: SCO socket layer initialized
[    3.472026] Bluetooth: RFCOMM TTY layer initialized
[    3.472045] Bluetooth: RFCOMM socket layer initialized
[    3.472068] Bluetooth: RFCOMM ver 1.11
[    3.472309] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    3.472314] Bluetooth: BNEP filters: protocol multicast
[    3.472322] Bluetooth: BNEP socket layer initialized
[    3.519808] input: Dell WMI hotkeys as /devices/virtual/input/input15
[    3.536751] nfc: nfc_init: NFC Core ver 0.1
[    3.536916] NET: Registered protocol family 39
[    3.550877] Probing NFC pn544
[    3.580072] type=1400 audit(1403625766.318:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=594 comm="apparmor_parser"
[    3.580085] type=1400 audit(1403625766.318:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=594 comm="apparmor_parser"
[    3.580918] type=1400 audit(1403625766.318:4): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=594 comm="apparmor_parser"
[    3.588045] intel_rapl: domain uncore energy ctr 2163:2163 not working, skip
[    3.687769] type=1400 audit(1403625766.422:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=609 comm="apparmor_parser"
[    3.687783] type=1400 audit(1403625766.422:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=609 comm="apparmor_parser"
[    3.687791] type=1400 audit(1403625766.422:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=609 comm="apparmor_parser"
[    3.688496] type=1400 audit(1403625766.426:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=609 comm="apparmor_parser"
[    3.688503] type=1400 audit(1403625766.426:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=609 comm="apparmor_parser"
[    3.688782] type=1400 audit(1403625766.426:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=609 comm="apparmor_parser"
[    3.819363] init: failsafe main process (624) killed by TERM signal
[    4.319272] init: alsa-restore main process (886) terminated with status 99
[    4.491485] init: plymouth-upstart-bridge main process ended, respawning
[    4.645513] init: udev-fallback-graphics main process (1066) terminated with status 1
[    4.701240] init: plymouth-splash main process (1088) terminated with status 1
[    7.576852] usb 1-6: USB disconnect, device number 5
[    7.576908] cdc_mbim 1-6:2.12 wwan0: unregister 'cdc_mbim' usb-0000:00:14.0-6, CDC MBIM
[   17.027295] usb 1-6: new high-speed USB device number 6 using xhci_hcd
[   17.044216] usb 1-6: config 1 has an invalid interface number: 8 but max is 3
[   17.044222] usb 1-6: config 1 has no interface number 1
[   17.044589] usb 1-6: config 2 has an invalid interface number: 12 but max is 1
[   17.044594] usb 1-6: config 2 has an invalid interface number: 13 but max is 1
[   17.044597] usb 1-6: config 2 has an invalid interface number: 13 but max is 1
[   17.044599] usb 1-6: config 2 has no interface number 0
[   17.044601] usb 1-6: config 2 has no interface number 1
[   17.045163] usb 1-6: New USB device found, idVendor=413c, idProduct=81a9
[   17.045167] usb 1-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   17.045170] usb 1-6: Product: Dell Wireless 5808e Gobi\xffffffe2\xffffff84\xffffffa2\xffffff84\xffffffa2 4G LTE Mobile Broadband Card
[   17.045172] usb 1-6: Manufacturer: Sierra Wireless, Incorporated
[   17.047595] cdc_mbim 1-6:2.12: cdc-wdm2: USB WDM device
[   17.047759] cdc_mbim 1-6:2.12 wwan0: register 'cdc_mbim' at usb-0000:00:14.0-6, CDC MBIM, 86:a3:7f:8b:eb:7d
[   24.212463] FAT-fs (mmcblk0p1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
mike@mike-Venue-11-Pro-7130-MS:~$

---

### Post by wildmanne39 on 2014-06-24
Your card actually is showing as an usb device, it is a sierra card, dell wwan card(413c:81a9) which is a 3g/4g card and not an internal wifi card.

People have had a lot of issues getting it to work with ubuntu. I am not sure yet what the driver is called but it looks like it needs patching before it will work. I am continuing to research.

---

### Post by mike-pc-reardon on 2014-06-24
I have two wifi with this system: the one you noted or Dell Wireless 5808 Gobi 4G LTE Mobile Broadband Card

And the one that is yet to be recognized Dell Wireless 1537 Dual-Band 2x2 802.11n WiFi Driver.  This is the one that I'm trying to get working.

My research on the latter is that Dell Wireless 1537 802.11 a/g/n Adapter is a Qualcom Atheros 3.7.2.45422  2013-10-17 or AR6004 model and the equivalent linux driver is 'ath6kl'.  This is the FullMAC wireless driver for Atheros AR600x family of chips, for example AR6003, AR6004 and AR6005 according to this site [http://wireless.kernel.org/en/users/Drivers/ath6kl](http://wireless.kernel.org/en/users/Drivers/ath6kl)

Thanks for the research effort

---

### Post by wildmanne39 on 2014-06-24
Does that device work on windows? it does not matter what driver it uses since it does not even show it exits, there is no way to get it to work until it shows up.

You can go into your bios and see if there is a setting that can be changed to get it to show up, or reset the bios.

---

### Post by mike-pc-reardon on 2014-06-25
Yes, everything works in Windows.

This is why it is so disappointing that Ubuntu doesn't do as well or better. 

I'll persist for answers for a while longer

---

### Post by wildmanne39 on 2014-06-25
Their must be a setting in the bios that needs adjusting but I do not know which one.

---

### Post by mike-pc-reardon on 2014-06-30
Maybe it is bios.  But before going there, I'm not sure how?

Meantime what I don't get is that wireless works in Windows.

So what is missing in Linux?  From what I can see, there is nothing missing from a driver side:


[LIST]
[*]Dell Wireless 1537 802.11 a/g/n Adapter
[*]Is a Qualcom Atheros 3.7.2.45422  2013-10-17 or model AR6004
[*]'ath6kl' is the FullMAC wireless driver for Atheros AR600x family of chips, for example AR6003, AR6004 and AR6005 according to [http://wireless.kernel.org/en/users/Drivers/ath6kl](http://wireless.kernel.org/en/users/Drivers/ath6kl)
[*]Starting from Linux kernel 3.2 ath6kl is available from kernel menuconfig
[/LIST]

So now what, how do you get Linux or menuconfig to acknowledge that the ath6kl is the driver to use to enable wireless?

---

### Post by r_avital on 2014-06-30
Mike,
Just my 2-cents worth: Ubuntu 14.04 is the preferred version these days, not only because it's the latest, but also because it's an LTS release (Long Term Support).  It is also known to have issues with SOME wifi, most notably on computers that were running EARLIER versions of Ubuntu and using the built-in wifi without any issues at all, and once upgraded to 14.04 the SAME computer could not get its wifi recognized by 14.04.  I've personally had this happen to me (still not resolved).  One learned opinion floating around is that there is a bug with interacting with wireless-N hardware.

You seem to be adept at rolling your own ubuntu on a USB drive, so just to eliminate this possibility, see if you can test with an earlier version of ubuntu, say, 13.04.  Booting from a live cd should tell you immediately.

---

### Post by bjorn-8 on 2014-07-02
I don't know if this helps, but here is information quoted from [https://www.happyassassin.net/fedlet-a-fedora-remix-for-bay-trail-tablets/](https://www.happyassassin.net/fedlet-a-fedora-remix-for-bay-trail-tablets/)

"It’s not connected via PCI, but via SDIO. We know what the hardware is and supporting it would probably be relatively simple…if it actually showed up at all :/ SDIO devices on the V8P just don’t get enumerated by the kernel at all, so there’s nothing for a driver to do anything with. We need to solve that problem before looking at the driver level. You can confirm this by looking in /sys/bus/sdio/devices ."

---

### Post by mike-pc-reardon on 2014-07-02
Please know I appreciate your 2 cents, but I will persist a little while longer.  For example, I'm still figuring out how to implement prior bios suggestion.


I concur that my research backs up potential bug around wireless N hardware.


I've also found prior suggestion to go back a version as well.  It is just that when Windows was what I knew, I didn't go back on Me or Vista version.  I made them work until such newer version fixed issues, at least somewhat. Besides going back a version may not serve, see: Re: Cannot install Ubuntu 13.04 using a USB stick or [http://ubuntuforums.org/showthread.php?t=2159915&page=3&](http://ubuntuforums.org/showthread.php?t=2159915&page=3&)


As for happy assassin suggestion, I've previously come across this site if I recall to put on the Venue Fedora rather than Ubuntu.  Meantime I'm not sure how to look in "/sys/bus/sdio/devices" but I will research to find out how and get back to you.

---

### Post by mike-pc-reardon on 2014-07-21
To begin with, thank you everyone for helping.  Here are the results to your suggestions and latest news below.  As noted in earlier responses, wireless device cannot be seen and remains so.


[LIST]
[*]Hibernation is not the issue.  When working on this issue I avoided the use of hibernation.
[/LIST]


[LIST]
[*]To reiterate I can dual boot (with Ubuntu, Fedora, Suse, and two more), just no wifi - so what's the point for a mobile laptop hybrid device.  I also tried prior versions to no avail.
[/LIST]


[LIST]
[*]Additionally the Wifi in question is not the Sierra Mobile broadband card.  I have yet to set it up on the Windows side let alone Linux side.  This laptop has two wifi devices.  This thread is focused on the first Wifi previously noted 1537 or ath6kl driver that is not working, or more precisely not even identified or seen.
[/LIST]


[LIST]
[*]I have been all over Bios and near as I can tell (as a power user) there is nothing here seemingly impacting wireless.  There could be something from a techie perspective.
[/LIST]


[LIST]
[*]Upon further research, I came to same conclusion as bjorn-8.  It seems to be something to do with SDIO.  Except knowing and fixing are two different things.
[/LIST]


**WHAT NEW:**
Sent an email to one of the email that actually worked over at [http://wireless.kernel.org](http://wireless.kernel.org) and received the following:* _It would seem to be a kernel bug._*


Cut and paste message with bug link is below:


[INDENT]I have understood it has a variant of ar6004 hw3.0 chip and just last[/INDENT]
[INDENT]week patches supporting that went into wireless-testing tree. You also[/INDENT]
[INDENT]need to add the new SDIO id to ath6kl, more info here:[/INDENT]


[https://bugzilla.kernel.org/show_bug.cgi?id=67921](https://bugzilla.kernel.org/show_bug.cgi?id=67921)

This is the latest.  I have yet to test any possible fixes that may be mentioned in this link.

---

### Post by mike-pc-reardon on 2014-07-23
So if I understand prior note per bugzilla link, I need to [FONT=arial]add a new entry to sdio.c, right?

And how do I do so?.  I assume I can't add on a live usb version, right?

If I re-set up the dual boot, what file and how do I add this entry to sdio?[/FONT]

---

### Post by mike-pc-reardon on 2014-08-21
Wouldn't this thread demonstrate that Linux is not ready for desktops, let alone tablets (and related hybrids) particularly the latest hardware models?

If not, how can I test a live (any version) Linux on this machine with Wifi working prior to committing to it - as an advanced user?

As prior note mentioned, the WiFi driver is allegedly in the kernel except that the related hardware is not recognized. 

I am still open to setting up sdio., so that ath6kl gets picked up and I assume activates the Wifi.  I need help with sdio direction please

---

### Post by k.krsnv on 2015-07-05
Just wondering: did you eventually solved this issue (and if yes -- how?)

The thought that I'm doomed to use Windows on this wonderful device makes me really sad.

---

### Post by mike-pc-reardon on 2015-07-05
Hi 

I was not able to resolve wifi, graphic or touch.  I didn't stop trying with Ubuntu though.  I tried Suse, Fedora and various flavors of these and Ubuntu.

Going down the dual boot path was also problematic with UEFI etc. both for setting up Linux as well as Windows.  It took me a while getting Windows to work well again after my various Linux dual-boot install efforts.

The wifi issue as you may have noted seems to be a kernel bug as I understand which may be fixed by now.  Certainly the distros using kernel 3.16 were no help, at the time

Summer is here again and I was going to make a second effort.  But this time I was going to set up an SD card as a boot option and install Linux on it.  I'll report back when I do so.

Meantime nothing in the Linux news leads me to believe that the Linux community is embracing Hybrids or Touch Computers at all.  This despite the fact Android seems to have these figured out, why not Linux.

Even so, I am going to give it another go.

---

### Post by k.krsnv on 2015-07-07
Thanks for reply.

Few days ago I tried to install Arch, Manjaro and Ubuntu on it. Manjaro and Ubuntu live CDs started without issues, with graphics and touchscreen working. But none of them supported wifi. Tried Arch with kernels 3.17, 3.18 and actual to no avail.

Then I created a partition on my external HDD, installed Arch to it on other computer, then loaded Arch live usb stick on Dell, made all partitions and copied files from external HDD. Configured systemd bootloader to load both linux and windows. And it worked! Did not try to start X on it (because this involves annoying manipulations with external HDD) but pretty sure it'll work too. But what's the use of a tablet (or even laptop) without internet connection? I can't even update packages :(

Though I didn't delete these partitons yet. Maybe I'll try to compile a kernel with a patch from this kernel issue thread: [https://bugzilla.kernel.org/show_bug.cgi?id=67921](https://bugzilla.kernel.org/show_bug.cgi?id=67921) (here's the patch: [https://github.com/AdamWill/baytrail-m/blob/master/kernel/support-Dell-OEM-chipset-found-in-Venue-8-Pro-SDIO-I.patch](https://github.com/AdamWill/baytrail-m/blob/master/kernel/support-Dell-OEM-chipset-found-in-Venue-8-Pro-SDIO-I.patch)). Guys here say it worked for Dell Venue 8, maybe it'll work with 11 too.

PS I've read somewhere on Arch forums that latest models with Core M do not have problems with wifi.

---

### Post by k.krsnv on 2015-07-07
In reply to your pessimistic mood about linux on tablets.

I use linux on HP 2760p convertible for about two years. Tinkered some kind of touch-friendly and in the same time keyboard-friendly interface with i3wm, touchegg for gestures, onboard as screen keyboard (tried xfce+xmonad instead i3wm, it was ok too). Not as cute as windows 8 bubbles and whistles but ok for reading/browsing/making notes or even watching movies in subway going from home to work and back.

I mean than with relatively small efforts (obviously much smaller then ubuntu team is devoting to their 'touch' project) one can combine existing tools to get more or less convenient user interface to start with.

---

### Post by mike-pc-reardon on 2015-07-12
I attempted similar install via micro SD Card and USB as boot option, in order to avoid messing windows set up on main SSD HD. Long story short, Ubuntu didn't see micro SD while Wifi is still not working.

There are more comprehensive suggestions for properly setting up SD cards and USB as boot options within UEFI and secure boot that I haven't tried yet.


Good to know about HP experience.  And I may check Arch option as well

But so far no Ubuntu on Dell Venue 11 Pro with wifi, either dual boot (last summer) or doing it with SD Card boot option (this summer).  The issue seems to be around SDIO set up in kernel

---

### Post by ksv2 on 2015-08-05
Folks,

I got wifi to work on Arch and ubuntu LTS version. I installed these on external USB disks. But as I knew I will never use windows, I nuked it and installed ubuntu 15.04 on the SSD. Everything works, but for sound. Sound was working on the default kernel, but post update/upgrade and gnome installed, sound stopped working. The main reason I am on 15.04 is because of gnome 3.16 (which I found is easier in the tablet mode than unity). Couple of issues which I need to still work on
1. Sound
2. Hibernate/Suspend. These are not working at all.

---

### Post by howefield on 2015-08-05
> **ksv2 said:**
> Folks,

I got wifi to work on Arch and ubuntu LTS version. I installed these on external USB disks. But as I knew I will never use windows, I nuked it and installed ubuntu 15.04 on the SSD. Everything works, but for sound. Sound was working on the default kernel, but post update/upgrade and gnome installed, sound stopped working. The main reason I am on 15.04 is because of gnome 3.16 (which I found is easier in the tablet mode than unity). Couple of issues which I need to still work on
1. Sound
2. Hibernate/Suspend. These are not working at all.

So why are you posting in a thread titled "*Ubuntu 14.04 - Dell Venue 11 Pro - Fail to recognize Wifi*"

Give yourself a break and start a new thread :)

---

### Post by mike-pc-reardon on 2015-08-05
Hi

I've returned with my dual boot goal (until I'm satisfied that I can do without Windows). I was force to take secure boot off, but now I can first choose Ubuntu on boot up (on SD Card) or go to Windows (on main SSD drive).  It went straight into Try Ubuntu, without setting nomodeset.  Yeah

I have yet to install from there, or test sound etc or check if Ubuntu can see and install further on the SD card.

The reason why if Wifi remains unavailable.  I am investigating if there is anything new on Wifi since beginning this thread last year

---

### Post by mike-pc-reardon on 2015-09-21
Last update

I was unsuccessful setting Ubuntu on SD card as part of my dual boot goal alongside Windows - preferably with the ability to choose between the two upon boot up.  

Windows Boot Manager repeatedly didn't recognize SD card consistently, no matter how I could get it to see it at least once or twice - without talking about whether it could see it as a boot option.

During my trials and tribulations, I considered alternative boot manager.  Reviewed 'how to' bcdedit, easybcd through to Refind only to conclude that there has got to be an easier way.

I also attempted to achieve my goal with other Linux flavors without success.  I simply didn't want to resize main hard drive (where Windows OS resides) - given past missed experiences.

Long story short, I set up Virtual Box on Windows 8.1  with Ubuntu virtual using all of the 32 gb of SD card - where the initial results were great and  without the initial  lack of wifi.  Updated Ubuntu.  

And now reviewing Ubuntu as alternative desktop going forward.  Should I do so it likely will not be on this hybrid  laptop/tablet in the end.

This thread can now be considered close.  Thank you everyone for your attention, guidance and help.

---

### Post by Geoffrey_Arndt on 2015-09-22
Also, the whole ubuntu experience will be much more positive if obtaining certified hardware that either comes with ubuntu (or other distro) already installed, or is hardware that's linux friendly (Intel wireless, Intel graphics).   Vendors such as these:    [http://linuxpreloaded.com/](http://linuxpreloaded.com/)

Also #2 . . . another solution would have been to spend about 10 bucks on a known usb-wireless adapter that's Ubuntu friendly.    One (of many) such devices can be found at:

[http://www.pandawireless.com/Products%20|%20Panda%20Wireless.html](http://www.pandawireless.com/Products%20|%20Panda%20Wireless.html)

The Panda devices are available on Amazon, another excellent recent model is the TP-Link (Archer T4UH).

These adapters are just plug and play - no driver installs needed (kernel level support).    I don't own an Archer device (yet), but can vouch for the Panda devices.

Because industry, Science, Education don't want vendor lock-in (e.g., Microsoft only devices), there are alternatives (plus, recall that Android is linux) . . . but on _devices designed for consumers on windows, retrofitting isn't always easy._

---

