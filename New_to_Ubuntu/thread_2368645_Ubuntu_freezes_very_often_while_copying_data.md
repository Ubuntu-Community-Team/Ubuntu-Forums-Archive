---
title: "Ubuntu freezes very often while copying data"
date: 2017-08-13
forum: New to Ubuntu
---

### Post by alexbass on 2017-08-13
Dear all, 

I have an Ubuntu installation that I intend to use as my main desktop platform, I am very new to Linux so forgive me if I am asking stupid questions.

The problem I am experiencing right now is that Ubuntu freezes in a way that the only solution is to press the shutdown button, it happens AFAIK only when I try to move files between my USB devices, but unfortunately for troubleshooting porpoises not every single times I move files.

Bellow my system description:
```
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.2 LTS
Release:	16.04
Codename:	xenial
```
hardware Dell Optiplex 7040 
```

00:00.0 Host bridge: Intel Corporation Sky Lake Host Bridge/DRAM Registers (rev 07)
00:01.0 PCI bridge: Intel Corporation Sky Lake PCIe Controller (x16) (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Sky Lake Integrated Graphics (rev 06)
00:14.0 USB controller: Intel Corporation Sunrise Point-H USB 3.0 xHCI Controller (rev 31)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-H Thermal subsystem (rev 31)
00:16.0 Communication controller: Intel Corporation Sunrise Point-H CSME HECI #1 (rev 31)
00:16.3 Serial controller: Intel Corporation Sunrise Point-H KT Redirection (rev 31)
00:17.0 RAID bus controller: Intel Corporation SATA Controller [RAID mode] (rev 31)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-H LPC Controller (rev 31)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-H PMC (rev 31)
00:1f.3 Audio device: Intel Corporation Sunrise Point-H HD Audio (rev 31)
00:1f.4 SMBus: Intel Corporation Sunrise Point-H SMBus (rev 31)
00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection (2) I219-LM (rev 31)
```
File Systems
```

Filesystem                   Size  Used Avail Use% Mounted on
udev                         7,8G     0  7,8G   0% /dev
tmpfs                        1,6G  9,8M  1,6G   1% /run
/dev/mapper/ubuntu--vg-root  219G   49G  159G  24% /
tmpfs                        7,8G   90M  7,7G   2% /dev/shm
tmpfs                        5,0M  4,0K  5,0M   1% /run/lock
tmpfs                        7,8G     0  7,8G   0% /sys/fs/cgroup
/dev/sda2                    473M  249M  200M  56% /boot
/dev/sda1                    511M   12M  500M   3% /boot/efi
cgmfs                        100K     0  100K   0% /run/cgmanager/fs
tmpfs                        1,6G   44K  1,6G   1% /run/user/1000
/home/alexbass/.Private      219G   49G  159G  24% /home/alexbass
/dev/sdb1                    1,9T  1,8T  111G  95% /media/alexbass/Seagate Exp
/dev/sdd1                    1,8T  538G  1,2T  31% /media/alexbass/Libreria
/dev/sdc1                    4,6T  1,1T  3,6T  22% /media/alexbass/Media
alexbass@Atom:/var/log$ 
```
When looking at my Kern.log and syslog I only find this
```
Aug 13 20:33:49 Atom kernel: [34857.740478] sd 5:0:0:0: [sdd] tag#0 Add. Sense: No additional sense information
Aug 13 20:33:49 Atom kernel: [34857.740485] sd 5:0:0:0: [sdd] tag#0 CDB: ATA command pass through(12)/Blank a1 06 20 da 00 00 4f c2 00 b0 00 00
Aug 13 20:43:48 Atom kernel: [35457.114110] sd 5:0:0:0: [sdd] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
Aug 13 20:43:48 Atom kernel: [35457.114112] sd 5:0:0:0: [sdd] tag#0 Sense Key : Hardware Error [current] [descriptor] 
Aug 13 20:43:48 Atom kernel: [35457.114113] sd 5:0:0:0: [sdd] tag#0 Add. Sense: No additional sense information
Aug 13 20:43:48 Atom kernel: [35457.114114] sd 5:0:0:0: [sdd] tag#0 CDB: ATA command pass through(16) 85 06 20 00 00 00 00 00 00 00 00 00 00 00 e5 00
Aug 13 20:43:48 Atom kernel: [35457.577628] sd 5:0:0:0: [sdd] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
Aug 13 20:43:48 Atom kernel: [35457.577634] sd 5:0:0:0: [sdd] tag#0 Sense Key : Hardware Error [current] [descriptor] 
Aug 13 20:43:48 Atom kernel: [35457.577637] sd 5:0:0:0: [sdd] tag#0 Add. Sense: No additional sense information
Aug 13 20:43:48 Atom kernel: [35457.577641] sd 5:0:0:0: [sdd] tag#0 CDB: ATA command pass through(12)/Blank a1 06 20 da 00 00 4f c2 00 b0 00 00
```
Could anyone please share some light on how to proceed?

Thanks all in advance.

Alex

---

### Post by ajgreeny on 2017-08-13
What hardware do you have?

An easy way to show this is to run ```
inxi -F
``` in terminal, though you may need to install inxi first as I'm not sure if it is in a default install.

Please use code tags for terminal output.  See **Code-tags** in my signature below for a How-to.

---

### Post by user_of_gnomes on 2017-08-14
What kind of USB devices? Hard drives? What is their S.M.A.R.T status?

---

### Post by alexbass on 2017-08-15
@ajgreeny thanks for your help, please see below:

```
alexbass@Atom:~$ inxi -F
System:    Host: Atom Kernel: 4.10.0-32-generic x86_64 (64 bit)
           Desktop: Unity 7.4.0  Distro: Ubuntu 16.04 xenial
Machine:   System: Dell product: OptiPlex 7040
           Mobo: Dell model: 096JG8 v: A01
           Bios: Dell v: 1.5.7 date: 12/21/2016
CPU:       Quad core Intel Core i7-6700T (-HT-MCP-) cache: 8192 KB 
           clock speeds: max: 3600 MHz 1: 899 MHz 2: 896 MHz 3: 898 MHz
           4: 898 MHz 5: 899 MHz 6: 899 MHz 7: 899 MHz 8: 893 MHz
Graphics:  Card: Intel Sky Lake Integrated Graphics
           Display Server: X.Org 1.18.4 drivers: (unloaded: fbdev,vesa)
           Resolution: 3440x1440@49.99hz
           GLX Renderer: Mesa DRI Intel HD Graphics 530 (Skylake GT2)
           GLX Version: 3.0 Mesa 17.0.7
Audio:     Card Intel Sunrise Point-H HD Audio driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.10.0-32-generic
Network:   Card: Intel Ethernet Connection (2) I219-LM driver: e1000e
           IF: enp0s31f6 state: up speed: 1000 Mbps duplex: full
           mac: 18:66:da:3f:d0:36
Drives:    HDD Total Size: 9257.8GB (39.2% used)
           ID-1: /dev/sda model: INTEL_SSDSC2BF25 size: 256.1GB
           ID-2: USB /dev/sdb model: Expansion size: 2000.4GB
           ID-3: USB /dev/sdd model: Elements_25A3 size: 5000.9GB
           ID-4: USB /dev/sdc model: Ext_HDD_1021 size: 2000.4GB
Partition: ID-1: / size: 219G used: 49G (24%) fs: ext4 dev: /dev/dm-1
           ID-2: /boot size: 473M used: 249M (56%) fs: ext2 dev: /dev/sda2
           ID-3: swap-1 size: 17.03GB used: 0.00GB (0%) fs: swap dev: /dev/dm-3
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 60.0C mobo: 29.8C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 322 Uptime: 1:00 Memory: 3168.3/15910.0MB
           Client: Shell (bash) inxi: 2.2.35
```

---

### Post by alexbass on 2017-08-15
thanks for your help @user_of_gnomes
Two of the disks passed the s.m.a.r.t without problems, the third one, brand new Western Digital 5 TB USB3 disk, seems not to be S.M.A.R.T compatible as it does not offer me the option.

---

### Post by user_of_gnomes on 2017-08-15
> **alexbass said:**
> thanks for your help @user_of_gnomes
Two of the disks passed the s.m.a.r.t without problems, the third one, brand new Western Digital 5 TB USB3 disk, seems not to be S.M.A.R.T compatible as it does not offer me the option.

Okay, that should rule out damaged drives then. In my experience bad drives can cause operating systems to freeze, even when they're in a USB housing.

---

### Post by alexbass on 2017-08-27
> **user_of_gnomes said:**
> Okay, that should rule out damaged drives then. In my experience bad drives can cause operating systems to freeze, even when they're in a USB housing.

I will replace the disk that is not passing the smart then, thanks a lot for your help.

Alexbass

---

### Post by HermanAB on 2017-08-28
Freezing usually means that you have a hardware problem and that can lead to corruption of data on disk also.  So it tends to go down hill rapidly.  So apart from fixing your machine, also check your backups.

---

