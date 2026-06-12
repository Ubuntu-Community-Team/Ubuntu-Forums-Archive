---
title: "Webcam for Vaio VPCEB15FM"
date: 2012-05-21
forum: New to Ubuntu
---

### Post by Prince199109 on 2012-05-21
Hey folks,

New user here. Trying to get my webcam to work, but to no avail. 

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller
03:00.1 System peripheral: Ricoh Co Ltd Memory Stick Host Controller
03:00.4 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller
04:00.0 Ethernet controller: Marvell Technology Group Ltd. Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB] (rev 11)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

Any help will be greatly appreciated.

---

### Post by roelforg on 2012-05-21
Run
```

ls /dev/*

```
in a terminal and post the output.

---

### Post by Prince199109 on 2012-05-22
> **roelforg said:**
> Run
```

ls /dev/*

```in a terminal and post the output.



/dev/agpgart         /dev/ram5     /dev/tty3     /dev/ttyS15
/dev/autofs         /dev/ram6     /dev/tty30     /dev/ttyS16
/dev/btrfs-control     /dev/ram7     /dev/tty31     /dev/ttyS17
/dev/cdrom         /dev/ram8     /dev/tty32     /dev/ttyS18
/dev/cdrw         /dev/ram9     /dev/tty33     /dev/ttyS19
/dev/console         /dev/ramzswap0  /dev/tty34     /dev/ttyS2
/dev/core         /dev/random     /dev/tty35     /dev/ttyS20
/dev/cpu_dma_latency     /dev/rfkill     /dev/tty36     /dev/ttyS21
/dev/dvd         /dev/root     /dev/tty37     /dev/ttyS22
/dev/dvdrw         /dev/rtc     /dev/tty38     /dev/ttyS23
/dev/ecryptfs         /dev/rtc0     /dev/tty39     /dev/ttyS24
/dev/fb0         /dev/scd0     /dev/tty4     /dev/ttyS25
/dev/full         /dev/sda     /dev/tty40     /dev/ttyS26
/dev/fuse         /dev/sda1     /dev/tty41     /dev/ttyS27
/dev/hidraw0         /dev/sda2     /dev/tty42     /dev/ttyS28
/dev/hidraw1         /dev/sda5     /dev/tty43     /dev/ttyS29
/dev/hidraw2         /dev/sda6     /dev/tty44     /dev/ttyS3
/dev/hpet         /dev/sda7     /dev/tty45     /dev/ttyS30
/dev/kmsg         /dev/sg0     /dev/tty46     /dev/ttyS31
/dev/log         /dev/sg1     /dev/tty47     /dev/ttyS4
/dev/loop0         /dev/snapshot     /dev/tty48     /dev/ttyS5
/dev/loop1         /dev/sr0     /dev/tty49     /dev/ttyS6
/dev/loop2         /dev/stderr     /dev/tty5     /dev/ttyS7
/dev/loop3         /dev/stdin     /dev/tty50     /dev/ttyS8
/dev/loop4         /dev/stdout     /dev/tty51     /dev/ttyS9
/dev/loop5         /dev/tty     /dev/tty52     /dev/uinput
/dev/loop6         /dev/tty0     /dev/tty53     /dev/urandom
/dev/loop7         /dev/tty1     /dev/tty54     /dev/usbmon0
/dev/mcelog         /dev/tty10     /dev/tty55     /dev/usbmon1
/dev/mem         /dev/tty11     /dev/tty56     /dev/usbmon2
/dev/network_latency     /dev/tty12     /dev/tty57     /dev/vboxdrv
/dev/network_throughput  /dev/tty13     /dev/tty58     /dev/vboxnetctl
/dev/null         /dev/tty14     /dev/tty59     /dev/vcs
/dev/oldmem         /dev/tty15     /dev/tty6     /dev/vcs1
/dev/port         /dev/tty16     /dev/tty60     /dev/vcs2
/dev/ppp         /dev/tty17     /dev/tty61     /dev/vcs3
/dev/psaux         /dev/tty18     /dev/tty62     /dev/vcs4
/dev/ptmx         /dev/tty19     /dev/tty63     /dev/vcs5
/dev/ram0         /dev/tty2     /dev/tty7     /dev/vcs6
/dev/ram1         /dev/tty20     /dev/tty8     /dev/vcsa
/dev/ram10         /dev/tty21     /dev/tty9     /dev/vcsa1
/dev/ram11         /dev/tty22     /dev/ttyprintk  /dev/vcsa2
/dev/ram12         /dev/tty23     /dev/ttyS0     /dev/vcsa3
/dev/ram13         /dev/tty24     /dev/ttyS1     /dev/vcsa4
/dev/ram14         /dev/tty25     /dev/ttyS10     /dev/vcsa5
/dev/ram15         /dev/tty26     /dev/ttyS11     /dev/vcsa6
/dev/ram2         /dev/tty27     /dev/ttyS12     /dev/vga_arbiter
/dev/ram3         /dev/tty28     /dev/ttyS13     /dev/zero
/dev/ram4         /dev/tty29     /dev/ttyS14

/dev/block:
1:0   11:0  1:13  1:2  1:5  1:8    7:0    7:3  7:6  8:1    8:2   8:48  8:6
1:1   1:11  1:14  1:3  1:6  1:9    7:1    7:4  7:7  8:16    8:32  8:49  8:7
1:10  1:12  1:15  1:4  1:7  251:0  7:2    7:5  8:0  8:17    8:33  8:5

/dev/bsg:
0:0:0:0  1:0:0:0

/dev/bus:
usb

/dev/cgroup:
cpu

/dev/char:
10:1    10:63    13:63    180:97     252:0    4:16  4:32  4:49  4:65    4:81  5:2
10:175    108:0    13:64    189:0     252:1    4:17  4:33  4:5   4:66    4:82  5:3
10:200    1:1    13:65    189:1     252:2    4:18  4:34  4:50  4:67    4:83  7:0
10:223    1:11    13:66    189:128  253:0    4:19  4:35  4:51  4:68    4:84  7:1
10:227    1:12    13:67    189:129  253:1    4:2   4:36  4:52  4:69    4:85  7:128
10:228    116:1    13:68    189:130  253:2    4:20  4:37  4:53  4:7    4:86  7:129
10:229    116:2    13:69    189:131  253:3    4:21  4:38  4:54  4:70    4:87  7:130
10:231    116:3    13:70    1:9     253:4    4:22  4:39  4:55  4:71    4:88  7:131
10:234    116:33    13:71    21:0     254:0    4:23  4:4   4:56  4:72    4:89  7:132
10:236    116:4    13:72    21:1     29:0    4:24  4:40  4:57  4:73    4:9   7:133
10:55    116:5    13:73    21:2     4:0    4:25  4:41  4:58  4:74    4:90  7:134
10:56    116:6    13:74    21:3     4:1    4:26  4:42  4:59  4:75    4:91  7:2
10:57    116:7    13:75    21:4     4:10    4:27  4:43  4:6   4:76    4:92  7:3
10:58    1:3    1:4    226:0     4:11    4:28  4:44  4:60  4:77    4:93  7:4
10:59    13:32    1:5    226:64     4:12    4:29  4:45  4:61  4:78    4:94  7:5
10:60    13:33    1:7    251:0     4:13    4:3   4:46  4:62  4:79    4:95  7:6
10:61    13:34    1:8    251:1     4:14    4:30  4:47  4:63  4:8    5:0
10:62    13:35    180:96    251:2     4:15    4:31  4:48  4:64  4:80    5:1

/dev/cpu:
microcode

/dev/disk:
by-id  by-path    by-uuid

/dev/dri:
card0  controlD64

/dev/fd:
0  1  2  3

/dev/input:
by-id     event1   event2  event5  event8  mouse0  mouse3
by-path  event10  event3  event6  event9  mouse1
event0     event11  event4  event7  mice      mouse2

/dev/mapper:
control

/dev/net:
tun

/dev/pktcdvd:
control

/dev/pts:
0  ptmx

/dev/shm:
mono.1918  pulse-shm-1068794892  pulse-shm-2672779338  pulse-shm-54273993
mono.1938  pulse-shm-257098543     pulse-shm-3556745132

/dev/snd:
by-path  controlC0  hwC0D0  hwC0D3  pcmC0D0c  pcmC0D0p    pcmC0D3p  seq  timer

/dev/usb:
hiddev0  hiddev1
ls: cannot open directory /dev/vboxusb: Permission denied


Thanks for the quick response :)

---

### Post by papibe on 2012-05-22
Hi Prince199109.

Almost all laptop's built-in webcams are internally connected to an USB bus.

Could you post the result of this command?
```
lsusb
```
Regards.

---

### Post by Prince199109 on 2012-05-22
> **papibe said:**
> Hi Prince199109.

Almost all laptop's built-in webcams are internally connected to an USB bus.

Could you post the result of this command?
```
lsusb
```Regards.

Sure thing.

Bus 002 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Again, I appreciate the help. Windows died on me and I'm currently deployed, so I don't have the means to bring it in for professional help, so I switched to linux. All very new to me.

---

### Post by papibe on 2012-05-22
> **Prince199109 said:**
> Bus 002 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver

There's no clear webcam devices. My guess is that it could be attached to the device above.

Do you have other usb devices connected to the computer (keyboard? mouse?).

Could you post the result of these commands?
```
dmesg | grep -i video

dmesg | grep -i Logitech
```
Regards.

---

### Post by Prince199109 on 2012-05-23
> **papibe said:**
> There's no clear webcam devices. My guess is that it could be attached to the device above.

Do you have other usb devices connected to the computer (keyboard? mouse?).

Could you post the result of these commands?
```
dmesg | grep -i video

dmesg | grep -i Logitech
```Regards.

allen@allen-VPCEB15FM:~$ dmesg | grep -i video
[    1.719644] pci 0000:00:02.0: Boot video device
[    7.451629] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5
[    7.451685] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   25.145809] sony-laptop: brightness ignored, must be controlled by ACPI video driver
[   25.398053] Linux video capture interface: v2.00
[   25.405963] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:6409)
[   25.413306] usbcore: registered new interface driver uvcvideo
[   25.413309] USB Video Class driver (v1.0.0)
allen@allen-VPCEB15FM:~$ dmesg | grep -i Logitech
[    7.225720] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input3
[    7.225867] generic-usb 0003:046D:C52B.0001: input,hidraw0: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.0-1.6/input0
[    7.227859] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.1/input/input4
[    7.228101] generic-usb 0003:046D:C52B.0002: input,hiddev0,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1.6/input1
[    7.230635] generic-usb 0003:046D:C52B.0003: hiddev0,hidraw2: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-1.6/input2
allen@allen-VPCEB15FM:~$ 


I am able to connect my camera, mouse, and Ipod to it. Currently my mouse and camera are attached.

---

### Post by Prince199109 on 2012-05-23
This is lsusb w/o anything plugged in:

Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0c45:6409 Microdia 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by papibe on 2012-05-23
> **Prince199109 said:**
> 
[   25.405963] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:6409)
[   25.413306] usbcore: registered new interface driver uvcvideo
[   25.413309] USB Video Class driver (v1.0.0)

> **Prince199109 said:**
> 
Bus 001 Device 005: ID 0c45:6409 Microdia

There it is!

While to try to make it work, boot without any other USB device connected (I imagine your laptop has a touchpad). 

Then test using the camera as much as you can: in Skype, as an input device in VLC, etc.

Remember some webcams need to set the variable LD_PRELOAD pointing to the appropriate path to v4l1compat.so before they can work (search the forums for examples).

I hope that helps, and tell us how it goes.
Regards.

---

### Post by Prince199109 on 2012-05-24
Huzzah! I see me. Now off to find a thread about making my camera work in skype...

---

### Post by mörgæs on 2012-05-24
[https://bugs.launchpad.net/ubuntu/+source/skype/+bug/908174](https://bugs.launchpad.net/ubuntu/+source/skype/+bug/908174)

---

