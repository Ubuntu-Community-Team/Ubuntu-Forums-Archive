---
title: "Login Screen is not Coming"
date: 2012-03-27
forum: New to Ubuntu
---

### Post by sagar_aarya on 2012-03-27
Whenever i am booting my laptop,login screen is not appearing

something look like this image..
[http://www.sucka.net/wp-content/uploads/2010/03/boot.png?cda6c1](http://www.sucka.net/wp-content/uploads/2010/03/boot.png?cda6c1)

no login option  

i tried 
sudo apt-get install ubuntu-desktop

but didnt worked.


whereas i am able to login from text mode(using ctrl+alt+f1)

this problem came since yesterday....

:confused: :confused: :confused:

---

### Post by sagar_aarya on 2012-03-28
??????

:mad: :mad: :mad:

---

### Post by solocommand on 2012-03-28
I believe if you hit Esc during that screen, you should be able to see the boot log. Are there any errors that come up that might be causing it to hang?

---

### Post by sagar_aarya on 2012-03-28
> **solocommand said:**
> I believe if you hit Esc during that screen, you should be able to see the boot log. Are there any errors that come up that might be causing it to hang?


hitting Esc screen didnt solved d problem.

Actually,I installed some of softwares,packages,update etc etc.

After that this problem persist.

sometimes only black screen with cursor blinking is coming.

---

### Post by Perfect Storm on 2012-03-28
Try:
```
startx
```

1. Also can you post the specs of your computer (specially video card).
2. Do you use any PPA or/and other untrusted sourcelist?
3. How did you installed your videocard (if using Nvidia or ATI)?

---

### Post by sagar_aarya on 2012-04-01
> **Artificial Intelligence said:**
> Try:
```
startx
```

1. Also can you post the specs of your computer (specially video card).
2. Do you use any PPA or/and other untrusted sourcelist?
3. How did you installed your videocard (if using Nvidia or ATI)?

i tried startx ,nothing happened
[B]sagar@MRFRODO:~$ startx
Fatal server error:
server is already active for display 0
If this server is no longer running,remove /tmp/.X0-lock
and start again

Please consult the The X.Org Foundation support
at [http://wiki.x.org](http://wiki.x.org)
for help

ddxSigGiveUp:CLosing log
Invalid MIT-MAGIC-COOKIE-1 keygivingup.
xinit: Resource temporarily unavailable (errno 11):unable to connect to X server
xinit: No such process (errno 3):Server error.
sagar@MRFRODO:~$
 [/B]

---

### Post by sagar_aarya on 2012-04-01
> **Artificial Intelligence said:**
> Try:
```
startx
```

1. Also can you post the specs of your computer (specially video card).
2. Do you use any PPA or/and other untrusted sourcelist?
3. How did you installed your videocard (if using Nvidia or ATI)?


Video card: 
00:02.0 VGA compatible controller:Intel Corporation Mobile GM965/GL960 Integrated Graphich Controller (rev 0c)

I think Yes,A day before to this problem,i tried to upgrade

---

### Post by HiImTye on 2012-04-01
try
```
sudo /etc/init.d/lightdm restart
```

---

### Post by sagar_aarya on 2012-04-01
> **HiImTye said:**
> try
```
sudo /etc/init.d/lightdm restart
```

sagar@MRFRODO:~$sudo /etc/init.d/lightdm restart
sudo:/etc/init.d/lightdm:command not found

---

### Post by HiImTye on 2012-04-01
```
apt-cache policy lightdm
```edit: if you are using a version of Ubuntu before 11.10 then use gdm instead of lightdm in the command in the previous post

---

### Post by sagar_aarya on 2012-04-01
> **HiImTye said:**
> ```
apt-cache policy lightdm
```edit: if you are using a version of Ubuntu before 11.10 then use gdm instead of lightdm in the command in the previous post


W:Unable to locate package lightdm


:confused: :confused: :confused:

---

### Post by HiImTye on 2012-04-01
what version of ubuntu are you using?

---

### Post by sagar_aarya on 2012-04-01
> **HiImTye said:**
> ```
apt-cache policy lightdm
```edit: if you are using a version of Ubuntu before 11.10 then use gdm instead of lightdm in the command in the previous post


yeah i m using 10.04LTS

i tried it with gdm

but black screen is coming

:confused::confused::confused::confused:

---

### Post by HiImTye on 2012-04-01
```
cat /etc/X11/xorg.conf
```

---

### Post by sagar_aarya on 2012-04-01
> **HiImTye said:**
> ```
cat /etc/X11/xorg.conf
```


**cat: /etc/X11/xorg.conf:No such file or directory**


But output of 

**cat /etc/X11/xorg.conf.failsafe**

Section "Device"
      Identifier  "Configured Video Device"
      Driver "fbdev"
EndSection

Section "Monitor"
 Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection

---

### Post by HiImTye on 2012-04-01
try
```
sudo cp /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf
```

---

### Post by sagar_aarya on 2012-04-01
> **HiImTye said:**
> try
```
sudo cp /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf
```

I did this command

again repeated the process,

sudo /etc/init.d/gdm restart


But still black screen is coming
:confused::confused:

---

### Post by HiImTye on 2012-04-01
```
apt-cache policy xserver-xorg-video-intel
```

---

### Post by sagar_aarya on 2012-04-01
> **HiImTye said:**
> ```
apt-cache policy xserver-xorg-video-intel
```

[B]xserver-xorg-video-intel:
Installed: 2:2.9.1-3ubuntu5
Candidate: 2:2.9.1-3ubuntu5
Version table:
***2:2.9.1-3ubuntu5 0
      500 [http://in.archive.ubuntu.com/ubuntu/lucid/main](http://in.archive.ubuntu.com/ubuntu/lucid/main) Packages
      180 /var/lib/dpkg/status

[/B]

---

### Post by HiImTye on 2012-04-01
```
sudo rm /etc/X11/xorg.conf
```
then reboot, go to a terminal and
```
cat /var/log/boot.log
cat /var/log/kern.log
```
let's see if youre getting any errors

---

### Post by sagar_aarya on 2012-04-01
> **HiImTye said:**
> ```
sudo rm /etc/X11/xorg.conf
```
then reboot, go to a terminal and
```
cat /var/log/boot.log
cat /var/log/kern.log
```
let's see if youre getting any errors

cat /var/log/boot.log
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
dosfsck 3.0.7, 24Dec 2009,FAT32, LFN
/dev/sda1: clean,172464/1114112 files
fsck from util-linux-ng 2.17.2
/dev/sda3: 0 files,1/1249372 clusters
/dev/sda4: clean,188116/7348224 files
init:unreadahead-other main process (840) terminated with status 4
*starting AppArmor profiles
Skipping profile in etc/apparmor.d/disable: usr.bin.firefox
*Setting sensor limits   
*Speech-dispatcher configured for user sessions
*Starting the Winbind daemon winbind


and



cat /var/log/kern.log
its gave soo much text...file is too big

---

### Post by HiImTye on 2012-04-01
try
```
cat /var/log/kern.log | grep intel
```or
```
cat /var/log/syslog
```

---

### Post by raja.genupula on 2012-04-01
then do as ```
cat /var/log/kern.log > out.txt
```

there will be a out.txt file in your home directory while you did this your terminal directory as Home . 

attach it to here .

---

### Post by sagar_aarya on 2012-04-01
> **HiImTye said:**
> try
```
cat /var/log/kern.log | grep intel
```or
```
cat /var/log/syslog
```

 
output of 
cat /var/log/kern.log | grep intel


Apr  1 11:31:02 MRFRODO kernel: [    7.157735] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
Apr  1 11:31:02 MRFRODO kernel: [    7.173043] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
Apr  1 11:31:02 MRFRODO kernel: [    7.178648] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
Apr  1 11:31:02 MRFRODO kernel: [    8.194749] fb0: inteldrmfb frame buffer device
Apr  1 11:33:21 MRFRODO kernel: [    9.617768] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
Apr  1 11:33:21 MRFRODO kernel: [    9.618437] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
Apr  1 11:33:21 MRFRODO kernel: [    9.664913] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
Apr  1 11:33:21 MRFRODO kernel: [   10.550630] fb0: inteldrmfb frame buffer device
Apr  1 11:42:18 MRFRODO kernel: [    9.607967] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
Apr  1 11:42:18 MRFRODO kernel: [    9.608652] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
Apr  1 11:42:18 MRFRODO kernel: [    9.628121] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
Apr  1 11:42:18 MRFRODO kernel: [   10.482482] fb0: inteldrmfb frame buffer device
Apr  1 11:55:27 MRFRODO kernel: [    9.550856] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
Apr  1 11:55:27 MRFRODO kernel: [    9.552098] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
Apr  1 11:55:27 MRFRODO kernel: [    9.660223] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
Apr  1 11:55:27 MRFRODO kernel: [   10.687017] fb0: inteldrmfb frame buffer device
Apr  1 12:16:05 MRFRODO kernel: [    9.661925] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
Apr  1 12:16:05 MRFRODO kernel: [    9.662596] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
Apr  1 12:16:05 MRFRODO kernel: [    9.683218] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
Apr  1 12:16:05 MRFRODO kernel: [   10.574838] fb0: inteldrmfb frame buffer device
Apr  1 13:40:15 MRFRODO kernel: [    9.750179] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
Apr  1 13:40:15 MRFRODO kernel: [    9.750862] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
Apr  1 13:40:15 MRFRODO kernel: [    9.785317] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
Apr  1 13:40:15 MRFRODO kernel: [   10.646489] fb0: inteldrmfb frame buffer device
Apr  1 14:16:55 MRFRODO kernel: [    9.669410] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
Apr  1 14:16:55 MRFRODO kernel: [    9.670065] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
Apr  1 14:16:55 MRFRODO kernel: [    9.678223] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
Apr  1 14:16:55 MRFRODO kernel: [   10.585039] fb0: inteldrmfb frame buffer device
Apr  1 14:32:29 MRFRODO kernel: [    9.629112] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
Apr  1 14:32:29 MRFRODO kernel: [    9.629788] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
Apr  1 14:32:29 MRFRODO kernel: [    9.742853] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
Apr  1 14:32:29 MRFRODO kernel: [   10.662643] fb0: inteldrmfb frame buffer device
Apr  1 15:10:05 MRFRODO kernel: [    9.653128] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
Apr  1 15:10:05 MRFRODO kernel: [    9.653791] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
Apr  1 15:10:05 MRFRODO kernel: [    9.696959] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
Apr  1 15:10:05 MRFRODO kernel: [   10.532814] fb0: inteldrmfb frame buffer device

---

### Post by HiImTye on 2012-04-01
can you paste that log, sans the grep command? I was hoping your errors would be obvious, but they arent

---

### Post by sagar_aarya on 2012-04-01
> **HiImTye said:**
> can you paste that log, sans the grep command? I was hoping your errors would be obvious, but they arent

Apr  1 11:23:32 MRFRODO kernel: [ 1360.777585] tg3: eth0: Link is up at 100 Mbps, full duplex.
Apr  1 11:23:32 MRFRODO kernel: [ 1360.777591] tg3: eth0: Flow control is on for TX and on for RX.
Apr  1 11:23:32 MRFRODO kernel: [ 1360.777977] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Apr  1 11:23:33 MRFRODO kernel: [ 1361.301401] tg3: eth0: Link is down.
Apr  1 11:23:35 MRFRODO kernel: [ 1363.281443] tg3: eth0: Link is up at 100 Mbps, full duplex.
Apr  1 11:23:35 MRFRODO kernel: [ 1363.281449] tg3: eth0: Flow control is on for TX and on for RX.
Apr  1 11:23:43 MRFRODO kernel: [ 1371.664158] eth0: no IPv6 routers present
Apr  1 11:23:56 MRFRODO kernel: [ 1384.877619] NET: Registered protocol family 24
Apr  1 11:25:11 MRFRODO kernel: [ 1460.053945] ip_tables: (C) 2000-2006 Netfilter Core Team
Apr  1 11:29:03 MRFRODO kernel: [ 1691.474168] tg3: eth0: Link is down.
Apr  1 11:31:01 MRFRODO kernel: imklog 4.2.0, log source = /proc/kmsg started.
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] Initializing cgroup subsys cpuset
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] Initializing cgroup subsys cpu
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] Linux version 2.6.32-21-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 (Ubuntu 2.6.32-21.32-generic 2.6.32.11+drm33.2)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] KERNEL supported cpus:
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]   Intel GenuineIntel
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]   AMD AuthenticAMD
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]   NSC Geode by NSC
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]   Cyrix CyrixInstead
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]   Centaur CentaurHauls
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]   Transmeta GenuineTMx86
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]   Transmeta TransmetaCPU
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]   UMC UMC UMC UMC
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] BIOS-provided physical RAM map:
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003f6d0000 (usable)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]  BIOS-e820: 000000003f6d0000 - 000000003f6e3000 (ACPI NVS)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]  BIOS-e820: 000000003f6e3000 - 0000000040000000 (reserved)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] DMI present.
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] last_pfn = 0x3f6d0 max_arch_pfn = 0x100000
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] MTRR default type: uncachable
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] MTRR fixed ranges enabled:
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]   00000-9FFFF write-back
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]   A0000-BFFFF uncachable
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]   C0000-FFFFF write-protect
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] MTRR variable ranges enabled:
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]   0 base 000000000 mask FC0000000 write-back
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]   1 base 03F700000 mask FFFF00000 uncachable
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]   2 base 03F800000 mask FFF800000 uncachable
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]   3 disabled
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]   4 disabled
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]   5 disabled
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]   6 disabled
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]   7 disabled
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] Scanning 1 areas for low memory corruption
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] modified physical RAM map:
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]  modified: 00000000000d2000 - 00000000000d4000 (reserved)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]  modified: 0000000000100000 - 000000003f6d0000 (usable)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]  modified: 000000003f6d0000 - 000000003f6e3000 (ACPI NVS)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]  modified: 000000003f6e3000 - 0000000040000000 (reserved)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] initial memory mapped : 0 - 00c00000
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]  0000400000 - 0037400000 page 2M
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] RAMDISK: 2f1c4000 - 2f95bad3
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] ACPI: RSDP 000f7240 00024 (v02 LENOVO)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] ACPI: XSDT 3f6d864f 00094 (v01 LENOVO TP-68    06040000  LTP 00000000)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] ACPI: FACP 3f6dfbd2 000F4 (v03 TOSCPL CRESTLNE 06040000 ALAN 00000001)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] ACPI: DSDT 3f6d9b4b 06013 (v02 TOSCPL CRESTLNE 06040000 INTL 20060608)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] ACPI: FACS 3f6e2fc0 00040
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] ACPI: APIC 3f6dfcc6 00068 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] ACPI: HPET 3f6dfd2e 00038 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] ACPI: MCFG 3f6dfd66 0003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] ACPI: TCPA 3f6dfda2 00032 (v01 Intel  CRESTLNE 06040000 LOHR 0000005A)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] ACPI: TMOR 3f6dfdd4 00026 (v01 PTLTD           06040000 PTL  00000003)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] ACPI: SLIX 3f6dfdfa 00176 (v01 LENOVO TP-68    06040000 TBD  00000001)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] ACPI: APIC 3f6dff70 00068 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] ACPI: BOOT 3f6dffd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] ACPI: SSDT 3f6d989e 002AD (v01 SataRe SataAhci 00001000 INTL 20050624)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] ACPI: SSDT 3f6d97fb 000A3 (v01 BrtRef  DD01BRT 00001000 INTL 20050624)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] ACPI: SSDT 3f6d8c6f 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] ACPI: SSDT 3f6d8bc9 000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20050624)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] ACPI: SSDT 3f6d86e3 004E6 (v01  PmRef    CpuPm 00003000 INTL 20050624)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify [email]linux-acpi@vger.kernel.org[/email]
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] 126MB HIGHMEM available.
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] 887MB LOWMEM available.
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]   low ram: 0 - 377fe000
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]   node 0 low ram: 00000000 - 377fe000
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]   node 0 bootmap 00008000 - 0000ef00
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]   #3 [0000100000 - 00008d9e98]    TEXT DATA BSS ==> [0000100000 - 00008d9e98]
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]   #4 [002f1c4000 - 002f95bad3]          RAMDISK ==> [002f1c4000 - 002f95bad3]
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]   #5 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]   #6 [00008da000 - 00008dd198]              BRK ==> [00008da000 - 00008dd198]
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] found SMP MP-table at [c00f72c0] f72c0
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] Zone PFN ranges:
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]   HighMem  0x000377fe -> 0x0003f6d0
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] Movable zone start PFN for each node
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] early_node_map[3] active PFN ranges
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]     0: 0x00000000 -> 0x00000002
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]     0: 0x00000006 -> 0x0000009f
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]     0: 0x00000100 -> 0x0003f6d0
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] On node 0 totalpages: 259691
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] free_area_init_node: node 0, pgdat c0798720, node_mem_map c1001000
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]   DMA zone: 0 pages reserved
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]   DMA zone: 3963 pages, LIFO batch:0
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]   Normal zone: 221486 pages, LIFO batch:31
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]   HighMem zone: 254 pages used for memmap
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]   HighMem zone: 32212 pages, LIFO batch:7
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] Using APIC driver default
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] ACPI: IRQ0 used by override.
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] ACPI: IRQ2 used by override.
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] ACPI: IRQ9 used by override.
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] nr_irqs_gsi: 24
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:a0000000)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36024 r0 d21320 u2097152
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] pcpu-alloc: s36024 r0 d21320 u2097152 alloc=1*4194304
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] pcpu-alloc: [0] 0 1 
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257661
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=3feab3eb-2b6a-4043-a49c-763525893dbf ro quiet splash
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] Enabling fast FPU save and restore... done.
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] Initializing CPU#0
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] allocated 5195840 bytes of page_cgroup
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0003f6d0)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] Memory: 1008272k/1039168k available (4673k kernel code, 29992k reserved, 2122k data, 656k init, 129864k highmem)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] virtual kernel memory layout:
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]       .init : 0xc07a3000 - 0xc0847000   ( 656 kB)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]       .data : 0xc0590613 - 0xc07a2e48   (2122 kB)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000]       .text : 0xc0100000 - 0xc0590613   (4673 kB)
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] Hierarchical RCU implementation.
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] NR_IRQS:2304 nr_irqs:424
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] Extended CMOS year: 2000
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] Console: colour VGA+ 80x25
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] console [tty0] enabled
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] hpet clockevent registered
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] Fast TSC calibration using PIT
Apr  1 11:31:02 MRFRODO kernel: [    0.000000] Detected 1662.683 MHz processor.
Apr  1 11:31:02 MRFRODO kernel: [    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 3325.36 BogoMIPS (lpj=6650732)
Apr  1 11:31:02 MRFRODO kernel: [    0.004023] Security Framework initialized
Apr  1 11:31:02 MRFRODO kernel: [    0.004041] AppArmor: AppArmor initialized
Apr  1 11:31:02 MRFRODO kernel: [    0.004048] Mount-cache hash table entries: 512
Apr  1 11:31:02 MRFRODO kernel: [    0.004175] Initializing cgroup subsys ns
Apr  1 11:31:02 MRFRODO kernel: [    0.004179] Initializing cgroup subsys cpuacct
Apr  1 11:31:02 MRFRODO kernel: [    0.004184] Initializing cgroup subsys memory
Apr  1 11:31:02 MRFRODO kernel: [    0.004192] Initializing cgroup subsys devices
Apr  1 11:31:02 MRFRODO kernel: [    0.004195] Initializing cgroup subsys freezer
Apr  1 11:31:02 MRFRODO kernel: [    0.004198] Initializing cgroup subsys net_cls
Apr  1 11:31:02 MRFRODO kernel: [    0.004220] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr  1 11:31:02 MRFRODO kernel: [    0.004223] CPU: L2 cache: 2048K
Apr  1 11:31:02 MRFRODO kernel: [    0.004226] CPU: Physical Processor ID: 0
Apr  1 11:31:02 MRFRODO kernel: [    0.004228] CPU: Processor Core ID: 0
Apr  1 11:31:02 MRFRODO kernel: [    0.004234] mce: CPU supports 6 MCE banks
Apr  1 11:31:02 MRFRODO kernel: [    0.004242] CPU0: Thermal monitoring handled by SMI
Apr  1 11:31:02 MRFRODO kernel: [    0.004246] using mwait in idle threads.
Apr  1 11:31:02 MRFRODO kernel: [    0.004251] Performance Events: Core2 events, Intel PMU driver.
Apr  1 11:31:02 MRFRODO kernel: [    0.004261] ... version:                2
Apr  1 11:31:02 MRFRODO kernel: [    0.004263] ... bit width:              40
Apr  1 11:31:02 MRFRODO kernel: [    0.004265] ... generic registers:      2
Apr  1 11:31:02 MRFRODO kernel: [    0.004268] ... value mask:             000000ffffffffff
Apr  1 11:31:02 MRFRODO kernel: [    0.004270] ... max period:             000000007fffffff
Apr  1 11:31:02 MRFRODO kernel: [    0.004273] ... fixed-purpose events:   3
Apr  1 11:31:02 MRFRODO kernel: [    0.004275] ... event mask:             0000000700000003
Apr  1 11:31:02 MRFRODO kernel: [    0.004279] Checking 'hlt' instruction... OK.
Apr  1 11:31:02 MRFRODO kernel: [    0.023186] ACPI: Core revision 20090903
Apr  1 11:31:02 MRFRODO kernel: [    0.036028] ftrace: converting mcount calls to 0f 1f 44 00 00
Apr  1 11:31:02 MRFRODO kernel: [    0.036038] ftrace: allocating 21771 entries in 43 pages
Apr  1 11:31:02 MRFRODO kernel: [    0.040066] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr  1 11:31:02 MRFRODO kernel: [    0.040448] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr  1 11:31:02 MRFRODO kernel: [    0.083167] CPU0: Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz stepping 0d
Apr  1 11:31:02 MRFRODO kernel: [    0.084001] Booting processor 1 APIC 0x1 ip 0x6000
Apr  1 11:31:02 MRFRODO kernel: [    0.008000] Initializing CPU#1
Apr  1 11:31:02 MRFRODO kernel: [    0.008000] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr  1 11:31:02 MRFRODO kernel: [    0.008000] CPU: L2 cache: 2048K
Apr  1 11:31:02 MRFRODO kernel: [    0.008000] CPU: Physical Processor ID: 0
Apr  1 11:31:02 MRFRODO kernel: [    0.008000] CPU: Processor Core ID: 1
Apr  1 11:31:02 MRFRODO kernel: [    0.008000] CPU1: Thermal monitoring handled by SMI
Apr  1 11:31:02 MRFRODO kernel: [    0.168074] CPU1: Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz stepping 0d
Apr  1 11:31:02 MRFRODO kernel: [    0.168088] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Apr  1 11:31:02 MRFRODO kernel: [    0.172022] Brought up 2 CPUs
Apr  1 11:31:02 MRFRODO kernel: [    0.172025] Total of 2 processors activated (6650.38 BogoMIPS).
Apr  1 11:31:02 MRFRODO kernel: [    0.172557] CPU0 attaching sched-domain:
Apr  1 11:31:02 MRFRODO kernel: [    0.172561]  domain 0: span 0-1 level MC
Apr  1 11:31:02 MRFRODO kernel: [    0.172564]   groups: 0 1
Apr  1 11:31:02 MRFRODO kernel: [    0.172571] CPU1 attaching sched-domain:
Apr  1 11:31:02 MRFRODO kernel: [    0.172574]  domain 0: span 0-1 level MC
Apr  1 11:31:02 MRFRODO kernel: [    0.172577]   groups: 1 0
Apr  1 11:31:02 MRFRODO kernel: [    0.172690] devtmpfs: initialized
Apr  1 11:31:02 MRFRODO kernel: [    0.172690] regulator: core version 0.5
Apr  1 11:31:02 MRFRODO kernel: [    0.172690] Time:  6:00:48  Date: 04/01/12
Apr  1 11:31:02 MRFRODO kernel: [    0.172690] NET: Registered protocol family 16
Apr  1 11:31:02 MRFRODO kernel: [    0.172690] Trying to unpack rootfs image as initramfs...
Apr  1 11:31:02 MRFRODO kernel: [    0.172690] EISA bus registered
Apr  1 11:31:02 MRFRODO kernel: [    0.172690] ACPI: bus type pci registered
Apr  1 11:31:02 MRFRODO kernel: [    0.172690] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Apr  1 11:31:02 MRFRODO kernel: [    0.172690] PCI: MCFG area at e0000000 reserved in E820
Apr  1 11:31:02 MRFRODO kernel: [    0.172690] PCI: Using MMCONFIG for extended config space
Apr  1 11:31:02 MRFRODO kernel: [    0.172690] PCI: Using configuration type 1 for base access
Apr  1 11:31:02 MRFRODO kernel: [    0.176120] bio: create slab <bio-0> at 0
Apr  1 11:31:02 MRFRODO kernel: [    0.177408] ACPI: EC: Look up EC in DSDT
Apr  1 11:31:02 MRFRODO kernel: [    0.184115] ACPI: BIOS _OSI(Linux) query ignored
Apr  1 11:31:02 MRFRODO kernel: [    0.414623] Freeing initrd memory: 7774k freed
Apr  1 11:31:02 MRFRODO kernel: [    0.704124] ACPI: Interpreter enabled
Apr  1 11:31:02 MRFRODO kernel: [    0.704162] ACPI: (supports S0 S3 S4 S5)
Apr  1 11:31:02 MRFRODO kernel: [    0.708034] ACPI: Using IOAPIC for interrupt routing
Apr  1 11:31:02 MRFRODO kernel: [    0.752770] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
Apr  1 11:31:02 MRFRODO kernel: [    0.753162] ACPI: No dock devices found.
Apr  1 11:31:02 MRFRODO kernel: [    0.753866] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr  1 11:31:02 MRFRODO kernel: [    0.753984] pci 0000:00:02.0: reg 10 64bit mmio: [0xfc000000-0xfc0fffff]
Apr  1 11:31:02 MRFRODO kernel: [    0.753994] pci 0000:00:02.0: reg 18 64bit mmio pref: [0xd0000000-0xdfffffff]
Apr  1 11:31:02 MRFRODO kernel: [    0.754001] pci 0000:00:02.0: reg 20 io port: [0x1800-0x1807]
Apr  1 11:31:02 MRFRODO kernel: [    0.754054] pci 0000:00:02.1: reg 10 64bit mmio: [0xfc100000-0xfc1fffff]
Apr  1 11:31:02 MRFRODO kernel: [    0.754192] pci 0000:00:1a.0: reg 20 io port: [0x1820-0x183f]
Apr  1 11:31:02 MRFRODO kernel: [    0.754270] pci 0000:00:1a.1: reg 20 io port: [0x1840-0x185f]
Apr  1 11:31:02 MRFRODO kernel: [    0.754355] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfc504800-0xfc504bff]
Apr  1 11:31:02 MRFRODO kernel: [    0.754431] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
Apr  1 11:31:02 MRFRODO kernel: [    0.754438] pci 0000:00:1a.7: PME# disabled
Apr  1 11:31:02 MRFRODO kernel: [    0.754504] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfc300000-0xfc303fff]
Apr  1 11:31:02 MRFRODO kernel: [    0.754577] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Apr  1 11:31:02 MRFRODO kernel: [    0.754583] pci 0000:00:1b.0: PME# disabled
Apr  1 11:31:02 MRFRODO kernel: [    0.754694] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Apr  1 11:31:02 MRFRODO kernel: [    0.754700] pci 0000:00:1c.0: PME# disabled
Apr  1 11:31:02 MRFRODO kernel: [    0.754817] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Apr  1 11:31:02 MRFRODO kernel: [    0.754822] pci 0000:00:1c.1: PME# disabled
Apr  1 11:31:02 MRFRODO kernel: [    0.754938] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Apr  1 11:31:02 MRFRODO kernel: [    0.754944] pci 0000:00:1c.2: PME# disabled
Apr  1 11:31:02 MRFRODO kernel: [    0.755058] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Apr  1 11:31:02 MRFRODO kernel: [    0.755064] pci 0000:00:1c.3: PME# disabled
Apr  1 11:31:02 MRFRODO kernel: [    0.755143] pci 0000:00:1d.0: reg 20 io port: [0x1860-0x187f]
Apr  1 11:31:02 MRFRODO kernel: [    0.755221] pci 0000:00:1d.1: reg 20 io port: [0x1880-0x189f]
Apr  1 11:31:02 MRFRODO kernel: [    0.755300] pci 0000:00:1d.2: reg 20 io port: [0x18a0-0x18bf]
Apr  1 11:31:02 MRFRODO kernel: [    0.755384] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfc504c00-0xfc504fff]
Apr  1 11:31:02 MRFRODO kernel: [    0.755460] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Apr  1 11:31:02 MRFRODO kernel: [    0.755467] pci 0000:00:1d.7: PME# disabled
Apr  1 11:31:02 MRFRODO kernel: [    0.755672] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Apr  1 11:31:02 MRFRODO kernel: [    0.755677] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
Apr  1 11:31:02 MRFRODO kernel: [    0.755683] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0680 (mask 007f)
Apr  1 11:31:02 MRFRODO kernel: [    0.755688] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 1640 (mask 000f)
Apr  1 11:31:02 MRFRODO kernel: [    0.755754] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
Apr  1 11:31:02 MRFRODO kernel: [    0.755764] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
Apr  1 11:31:02 MRFRODO kernel: [    0.755773] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
Apr  1 11:31:02 MRFRODO kernel: [    0.755783] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
Apr  1 11:31:02 MRFRODO kernel: [    0.755793] pci 0000:00:1f.1: reg 20 io port: [0x1810-0x181f]
Apr  1 11:31:02 MRFRODO kernel: [    0.755881] pci 0000:00:1f.2: reg 10 io port: [0x1c00-0x1c07]
Apr  1 11:31:02 MRFRODO kernel: [    0.755890] pci 0000:00:1f.2: reg 14 io port: [0x18d4-0x18d7]
Apr  1 11:31:02 MRFRODO kernel: [    0.755900] pci 0000:00:1f.2: reg 18 io port: [0x18d8-0x18df]
Apr  1 11:31:02 MRFRODO kernel: [    0.755909] pci 0000:00:1f.2: reg 1c io port: [0x18d0-0x18d3]
Apr  1 11:31:02 MRFRODO kernel: [    0.755919] pci 0000:00:1f.2: reg 20 io port: [0x18e0-0x18ff]
Apr  1 11:31:02 MRFRODO kernel: [    0.755929] pci 0000:00:1f.2: reg 24 32bit mmio: [0xfc504000-0xfc5047ff]
Apr  1 11:31:02 MRFRODO kernel: [    0.755979] pci 0000:00:1f.2: PME# supported from D3hot
Apr  1 11:31:02 MRFRODO kernel: [    0.755985] pci 0000:00:1f.2: PME# disabled
Apr  1 11:31:02 MRFRODO kernel: [    0.756034] pci 0000:00:1f.3: reg 10 32bit mmio: [0x000000-0x0000ff]
Apr  1 11:31:02 MRFRODO kernel: [    0.756064] pci 0000:00:1f.3: reg 20 io port: [0x1c20-0x1c3f]
Apr  1 11:31:02 MRFRODO kernel: [    0.756170] pci 0000:00:1c.0: bridge io port: [0x2000-0x2fff]
Apr  1 11:31:02 MRFRODO kernel: [    0.756177] pci 0000:00:1c.0: bridge 32bit mmio: [0xf6000000-0xf7ffffff]
Apr  1 11:31:02 MRFRODO kernel: [    0.756187] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xf0000000-0xf1ffffff]
Apr  1 11:31:02 MRFRODO kernel: [    0.756341] pci 0000:04:00.0: reg 10 32bit mmio: [0xf8000000-0xf8000fff]
Apr  1 11:31:02 MRFRODO kernel: [    0.756597] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
Apr  1 11:31:02 MRFRODO kernel: [    0.756611] pci 0000:04:00.0: PME# disabled
Apr  1 11:31:02 MRFRODO kernel: [    0.756739] pci 0000:00:1c.1: bridge io port: [0x3000-0x3fff]
Apr  1 11:31:02 MRFRODO kernel: [    0.756746] pci 0000:00:1c.1: bridge 32bit mmio: [0xf8000000-0xf9ffffff]
Apr  1 11:31:02 MRFRODO kernel: [    0.756756] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xf2000000-0xf3ffffff]
Apr  1 11:31:02 MRFRODO kernel: [    0.756829] pci 0000:00:1c.2: bridge io port: [0x4000-0x4fff]
Apr  1 11:31:02 MRFRODO kernel: [    0.756836] pci 0000:00:1c.2: bridge 32bit mmio: [0xfa000000-0xfbffffff]
Apr  1 11:31:02 MRFRODO kernel: [    0.756845] pci 0000:00:1c.2: bridge 64bit mmio pref: [0xf4000000-0xf5ffffff]
Apr  1 11:31:02 MRFRODO kernel: [    0.757045] pci 0000:06:00.0: reg 10 64bit mmio: [0xc8000000-0xc800ffff]
Apr  1 11:31:02 MRFRODO kernel: [    0.757294] pci 0000:06:00.0: PME# supported from D3hot D3cold
Apr  1 11:31:02 MRFRODO kernel: [    0.757306] pci 0000:06:00.0: PME# disabled
Apr  1 11:31:02 MRFRODO kernel: [    0.757422] pci 0000:00:1c.3: bridge io port: [0x5000-0x5fff]
Apr  1 11:31:02 MRFRODO kernel: [    0.757429] pci 0000:00:1c.3: bridge 32bit mmio: [0xc8000000-0xc9ffffff]
Apr  1 11:31:02 MRFRODO kernel: [    0.757438] pci 0000:00:1c.3: bridge 64bit mmio pref: [0xcc000000-0xcdffffff]
Apr  1 11:31:02 MRFRODO kernel: [    0.757503] pci 0000:08:06.0: reg 10 32bit mmio: [0xfc200000-0xfc2007ff]
Apr  1 11:31:02 MRFRODO kernel: [    0.757573] pci 0000:08:06.0: supports D1 D2
Apr  1 11:31:02 MRFRODO kernel: [    0.757576] pci 0000:08:06.0: PME# supported from D0 D1 D2 D3hot D3cold
Apr  1 11:31:02 MRFRODO kernel: [    0.757582] pci 0000:08:06.0: PME# disabled
Apr  1 11:31:02 MRFRODO kernel: [    0.757632] pci 0000:08:06.1: reg 10 32bit mmio: [0xfc200800-0xfc2008ff]
Apr  1 11:31:02 MRFRODO kernel: [    0.757703] pci 0000:08:06.1: supports D1 D2
Apr  1 11:31:02 MRFRODO kernel: [    0.757706] pci 0000:08:06.1: PME# supported from D0 D1 D2 D3hot D3cold
Apr  1 11:31:02 MRFRODO kernel: [    0.757712] pci 0000:08:06.1: PME# disabled
Apr  1 11:31:02 MRFRODO kernel: [    0.757764] pci 0000:08:06.2: reg 10 32bit mmio: [0xfc200c00-0xfc200cff]
Apr  1 11:31:02 MRFRODO kernel: [    0.757835] pci 0000:08:06.2: supports D1 D2
Apr  1 11:31:02 MRFRODO kernel: [    0.757838] pci 0000:08:06.2: PME# supported from D0 D1 D2 D3hot D3cold
Apr  1 11:31:02 MRFRODO kernel: [    0.757844] pci 0000:08:06.2: PME# disabled
Apr  1 11:31:02 MRFRODO kernel: [    0.757894] pci 0000:08:06.3: reg 10 32bit mmio: [0xfc201000-0xfc2010ff]
Apr  1 11:31:02 MRFRODO kernel: [    0.757965] pci 0000:08:06.3: supports D1 D2
Apr  1 11:31:02 MRFRODO kernel: [    0.757968] pci 0000:08:06.3: PME# supported from D0 D1 D2 D3hot D3cold
Apr  1 11:31:02 MRFRODO kernel: [    0.757974] pci 0000:08:06.3: PME# disabled
Apr  1 11:31:02 MRFRODO kernel: [    0.758047] pci 0000:00:1e.0: transparent bridge
Apr  1 11:31:02 MRFRODO kernel: [    0.758057] pci 0000:00:1e.0: bridge 32bit mmio: [0xfc200000-0xfc2fffff]
Apr  1 11:31:02 MRFRODO kernel: [    0.758101] pci_bus 0000:00: on NUMA node 0
Apr  1 11:31:02 MRFRODO kernel: [    0.758107] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Apr  1 11:31:02 MRFRODO kernel: [    0.758342] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Apr  1 11:31:02 MRFRODO kernel: [    0.758433] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
Apr  1 11:31:02 MRFRODO kernel: [    0.758523] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
Apr  1 11:31:02 MRFRODO kernel: [    0.758613] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
Apr  1 11:31:02 MRFRODO kernel: [    0.758745] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
Apr  1 11:31:02 MRFRODO kernel: [    0.772779] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
Apr  1 11:31:02 MRFRODO kernel: [    0.772904] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Apr  1 11:31:02 MRFRODO kernel: [    0.773027] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *7 10 12 14 15)
Apr  1 11:31:02 MRFRODO kernel: [    0.773148] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Apr  1 11:31:02 MRFRODO kernel: [    0.773269] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
Apr  1 11:31:02 MRFRODO kernel: [    0.773392] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Apr  1 11:31:02 MRFRODO kernel: [    0.773513] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
Apr  1 11:31:02 MRFRODO kernel: [    0.773635] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
Apr  1 11:31:02 MRFRODO kernel: [    0.773775] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Apr  1 11:31:02 MRFRODO kernel: [    0.773797] vgaarb: loaded
Apr  1 11:31:02 MRFRODO kernel: [    0.773947] SCSI subsystem initialized
Apr  1 11:31:02 MRFRODO kernel: [    0.774000] libata version 3.00 loaded.
Apr  1 11:31:02 MRFRODO kernel: [    0.774000] usbcore: registered new interface driver usbfs
Apr  1 11:31:02 MRFRODO kernel: [    0.774000] usbcore: registered new interface driver hub
Apr  1 11:31:02 MRFRODO kernel: [    0.774000] usbcore: registered new device driver usb
Apr  1 11:31:02 MRFRODO kernel: [    0.774000] ACPI: WMI: Mapper loaded
Apr  1 11:31:02 MRFRODO kernel: [    0.774000] PCI: Using ACPI for IRQ routing
Apr  1 11:31:02 MRFRODO kernel: [    0.774000] NetLabel: Initializing
Apr  1 11:31:02 MRFRODO kernel: [    0.774000] NetLabel:  domain hash size = 128
Apr  1 11:31:02 MRFRODO kernel: [    0.774000] NetLabel:  protocols = UNLABELED CIPSOv4
Apr  1 11:31:02 MRFRODO kernel: [    0.774000] NetLabel:  unlabeled traffic allowed by default
Apr  1 11:31:02 MRFRODO kernel: [    0.774000] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Apr  1 11:31:02 MRFRODO kernel: [    0.774000] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Apr  1 11:31:02 MRFRODO kernel: [    0.780014] Switching to clocksource tsc
Apr  1 11:31:02 MRFRODO kernel: [    0.782591] AppArmor: AppArmor Filesystem Enabled
Apr  1 11:31:02 MRFRODO kernel: [    0.782601] pnp: PnP ACPI init
Apr  1 11:31:02 MRFRODO kernel: [    0.782613] ACPI: bus type pnp registered
Apr  1 11:31:02 MRFRODO kernel: [    0.804014] pnp: PnP ACPI: found 10 devices
Apr  1 11:31:02 MRFRODO kernel: [    0.804017] ACPI: ACPI bus type pnp unregistered
Apr  1 11:31:02 MRFRODO kernel: [    0.804021] PnPBIOS: Disabled by ACPI PNP
Apr  1 11:31:02 MRFRODO kernel: [    0.804032] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
Apr  1 11:31:02 MRFRODO kernel: [    0.804036] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
Apr  1 11:31:02 MRFRODO kernel: [    0.804040] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
Apr  1 11:31:02 MRFRODO kernel: [    0.804044] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
Apr  1 11:31:02 MRFRODO kernel: [    0.804047] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
Apr  1 11:31:02 MRFRODO kernel: [    0.804051] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
Apr  1 11:31:02 MRFRODO kernel: [    0.804055] system 00:01: iomem range 0xfed40000-0xfed44fff has been reserved
Apr  1 11:31:02 MRFRODO kernel: [    0.804059] system 00:01: iomem range 0xfed45000-0xfed8ffff has been reserved
Apr  1 11:31:02 MRFRODO kernel: [    0.804067] system 00:04: iomem range 0xfed00000-0xfed003ff has been reserved
Apr  1 11:31:02 MRFRODO kernel: [    0.804076] system 00:06: ioport range 0x680-0x69f has been reserved
Apr  1 11:31:02 MRFRODO kernel: [    0.804079] system 00:06: ioport range 0x800-0x80f has been reserved
Apr  1 11:31:02 MRFRODO kernel: [    0.804083] system 00:06: ioport range 0x1000-0x107f has been reserved
Apr  1 11:31:02 MRFRODO kernel: [    0.804087] system 00:06: ioport range 0x1180-0x11bf has been reserved
Apr  1 11:31:02 MRFRODO kernel: [    0.804090] system 00:06: ioport range 0xfe00-0xfe00 has been reserved
Apr  1 11:31:02 MRFRODO kernel: [    0.804094] system 00:06: ioport range 0xff00-0xff7f has been reserved
Apr  1 11:31:02 MRFRODO kernel: [    0.838882] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
Apr  1 11:31:02 MRFRODO kernel: [    0.838887] pci 0000:00:1c.0:   IO window: 0x2000-0x2fff
Apr  1 11:31:02 MRFRODO kernel: [    0.838895] pci 0000:00:1c.0:   MEM window: 0xf6000000-0xf7ffffff
Apr  1 11:31:02 MRFRODO kernel: [    0.838902] pci 0000:00:1c.0:   PREFETCH window: 0x000000f0000000-0x000000f1ffffff
Apr  1 11:31:02 MRFRODO kernel: [    0.838912] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:04
Apr  1 11:31:02 MRFRODO kernel: [    0.838917] pci 0000:00:1c.1:   IO window: 0x3000-0x3fff
Apr  1 11:31:02 MRFRODO kernel: [    0.838924] pci 0000:00:1c.1:   MEM window: 0xf8000000-0xf9ffffff
Apr  1 11:31:02 MRFRODO kernel: [    0.838931] pci 0000:00:1c.1:   PREFETCH window: 0x000000f2000000-0x000000f3ffffff
Apr  1 11:31:02 MRFRODO kernel: [    0.838941] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:05
Apr  1 11:31:02 MRFRODO kernel: [    0.838945] pci 0000:00:1c.2:   IO window: 0x4000-0x4fff
Apr  1 11:31:02 MRFRODO kernel: [    0.838953] pci 0000:00:1c.2:   MEM window: 0xfa000000-0xfbffffff
Apr  1 11:31:02 MRFRODO kernel: [    0.838959] pci 0000:00:1c.2:   PREFETCH window: 0x000000f4000000-0x000000f5ffffff
Apr  1 11:31:02 MRFRODO kernel: [    0.838969] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:06
Apr  1 11:31:02 MRFRODO kernel: [    0.838974] pci 0000:00:1c.3:   IO window: 0x5000-0x5fff
Apr  1 11:31:02 MRFRODO kernel: [    0.838981] pci 0000:00:1c.3:   MEM window: 0xc8000000-0xc9ffffff
Apr  1 11:31:02 MRFRODO kernel: [    0.838988] pci 0000:00:1c.3:   PREFETCH window: 0x000000cc000000-0x000000cdffffff
Apr  1 11:31:02 MRFRODO kernel: [    0.838998] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:08
Apr  1 11:31:02 MRFRODO kernel: [    0.839001] pci 0000:00:1e.0:   IO window: disabled
Apr  1 11:31:02 MRFRODO kernel: [    0.839008] pci 0000:00:1e.0:   MEM window: 0xfc200000-0xfc2fffff
Apr  1 11:31:02 MRFRODO kernel: [    0.839014] pci 0000:00:1e.0:   PREFETCH window: disabled
Apr  1 11:31:02 MRFRODO kernel: [    0.839036]   alloc irq_desc for 17 on node -1
Apr  1 11:31:02 MRFRODO kernel: [    0.839038]   alloc kstat_irqs on node -1
Apr  1 11:31:02 MRFRODO kernel: [    0.839044] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Apr  1 11:31:02 MRFRODO kernel: [    0.839052] pci 0000:00:1c.0: setting latency timer to 64
Apr  1 11:31:02 MRFRODO kernel: [    0.839064]   alloc irq_desc for 16 on node -1
Apr  1 11:31:02 MRFRODO kernel: [    0.839066]   alloc kstat_irqs on node -1
Apr  1 11:31:02 MRFRODO kernel: [    0.839070] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Apr  1 11:31:02 MRFRODO kernel: [    0.839077] pci 0000:00:1c.1: setting latency timer to 64
Apr  1 11:31:02 MRFRODO kernel: [    0.839089]   alloc irq_desc for 18 on node -1
Apr  1 11:31:02 MRFRODO kernel: [    0.839091]   alloc kstat_irqs on node -1
Apr  1 11:31:02 MRFRODO kernel: [    0.839096] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Apr  1 11:31:02 MRFRODO kernel: [    0.839102] pci 0000:00:1c.2: setting latency timer to 64
Apr  1 11:31:02 MRFRODO kernel: [    0.839114]   alloc irq_desc for 19 on node -1
Apr  1 11:31:02 MRFRODO kernel: [    0.839116]   alloc kstat_irqs on node -1
Apr  1 11:31:02 MRFRODO kernel: [    0.839121] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Apr  1 11:31:02 MRFRODO kernel: [    0.839127] pci 0000:00:1c.3: setting latency timer to 64
Apr  1 11:31:02 MRFRODO kernel: [    0.839137] pci 0000:00:1e.0: setting latency timer to 64
Apr  1 11:31:02 MRFRODO kernel: [    0.839143] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Apr  1 11:31:02 MRFRODO kernel: [    0.839146] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
Apr  1 11:31:02 MRFRODO kernel: [    0.839150] pci_bus 0000:02: resource 0 io:  [0x2000-0x2fff]
Apr  1 11:31:02 MRFRODO kernel: [    0.839153] pci_bus 0000:02: resource 1 mem: [0xf6000000-0xf7ffffff]
Apr  1 11:31:02 MRFRODO kernel: [    0.839157] pci_bus 0000:02: resource 2 pref mem [0xf0000000-0xf1ffffff]
Apr  1 11:31:02 MRFRODO kernel: [    0.839160] pci_bus 0000:04: resource 0 io:  [0x3000-0x3fff]
Apr  1 11:31:02 MRFRODO kernel: [    0.839163] pci_bus 0000:04: resource 1 mem: [0xf8000000-0xf9ffffff]
Apr  1 11:31:02 MRFRODO kernel: [    0.839166] pci_bus 0000:04: resource 2 pref mem [0xf2000000-0xf3ffffff]
Apr  1 11:31:02 MRFRODO kernel: [    0.839170] pci_bus 0000:05: resource 0 io:  [0x4000-0x4fff]
Apr  1 11:31:02 MRFRODO kernel: [    0.839173] pci_bus 0000:05: resource 1 mem: [0xfa000000-0xfbffffff]
Apr  1 11:31:02 MRFRODO kernel: [    0.839176] pci_bus 0000:05: resource 2 pref mem [0xf4000000-0xf5ffffff]
Apr  1 11:31:02 MRFRODO kernel: [    0.839179] pci_bus 0000:06: resource 0 io:  [0x5000-0x5fff]
Apr  1 11:31:02 MRFRODO kernel: [    0.839182] pci_bus 0000:06: resource 1 mem: [0xc8000000-0xc9ffffff]
Apr  1 11:31:02 MRFRODO kernel: [    0.839186] pci_bus 0000:06: resource 2 pref mem [0xcc000000-0xcdffffff]
Apr  1 11:31:02 MRFRODO kernel: [    0.839189] pci_bus 0000:08: resource 1 mem: [0xfc200000-0xfc2fffff]
Apr  1 11:31:02 MRFRODO kernel: [    0.839192] pci_bus 0000:08: resource 3 io:  [0x00-0xffff]
Apr  1 11:31:02 MRFRODO kernel: [    0.839195] pci_bus 0000:08: resource 4 mem: [0x000000-0xffffffff]
Apr  1 11:31:02 MRFRODO kernel: [    0.839233] NET: Registered protocol family 2
Apr  1 11:31:02 MRFRODO kernel: [    0.839345] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr  1 11:31:02 MRFRODO kernel: [    0.839743] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Apr  1 11:31:02 MRFRODO kernel: [    0.840309] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Apr  1 11:31:02 MRFRODO kernel: [    0.840544] TCP: Hash tables configured (established 131072 bind 65536)
Apr  1 11:31:02 MRFRODO kernel: [    0.840547] TCP reno registered
Apr  1 11:31:02 MRFRODO kernel: [    0.840634] NET: Registered protocol family 1
Apr  1 11:31:02 MRFRODO kernel: [    0.840659] pci 0000:00:02.0: Boot video device
Apr  1 11:31:02 MRFRODO kernel: [    0.840846] Simple Boot Flag at 0x36 set to 0x1
Apr  1 11:31:02 MRFRODO kernel: [    0.841056] cpufreq-nforce2: No nForce2 chipset.
Apr  1 11:31:02 MRFRODO kernel: [    0.841087] Scanning for low memory corruption every 60 seconds
Apr  1 11:31:02 MRFRODO kernel: [    0.841220] audit: initializing netlink socket (disabled)
Apr  1 11:31:02 MRFRODO kernel: [    0.841231] type=2000 audit(1333260048.839:1): initialized
Apr  1 11:31:02 MRFRODO kernel: [    0.853258] highmem bounce pool size: 64 pages
Apr  1 11:31:02 MRFRODO kernel: [    0.853264] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Apr  1 11:31:02 MRFRODO kernel: [    0.855159] VFS: Disk quotas dquot_6.5.2
Apr  1 11:31:02 MRFRODO kernel: [    0.855235] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr  1 11:31:02 MRFRODO kernel: [    0.855935] fuse init (API version 7.13)
Apr  1 11:31:02 MRFRODO kernel: [    0.856042] msgmni has been set to 1731
Apr  1 11:31:02 MRFRODO kernel: [    0.856297] alg: No test for stdrng (krng)
Apr  1 11:31:02 MRFRODO kernel: [    0.856359] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Apr  1 11:31:02 MRFRODO kernel: [    0.856362] io scheduler noop registered
Apr  1 11:31:02 MRFRODO kernel: [    0.856365] io scheduler anticipatory registered
Apr  1 11:31:02 MRFRODO kernel: [    0.856367] io scheduler deadline registered
Apr  1 11:31:02 MRFRODO kernel: [    0.856414] io scheduler cfq registered (default)
Apr  1 11:31:02 MRFRODO kernel: [    0.856624]   alloc irq_desc for 24 on node -1
Apr  1 11:31:02 MRFRODO kernel: [    0.856627]   alloc kstat_irqs on node -1
Apr  1 11:31:02 MRFRODO kernel: [    0.856640] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
Apr  1 11:31:02 MRFRODO kernel: [    0.856654] pcieport 0000:00:1c.0: setting latency timer to 64
Apr  1 11:31:02 MRFRODO kernel: [    0.856836]   alloc irq_desc for 25 on node -1
Apr  1 11:31:02 MRFRODO kernel: [    0.856838]   alloc kstat_irqs on node -1
Apr  1 11:31:02 MRFRODO kernel: [    0.856849] pcieport 0000:00:1c.1: irq 25 for MSI/MSI-X
Apr  1 11:31:02 MRFRODO kernel: [    0.856861] pcieport 0000:00:1c.1: setting latency timer to 64
Apr  1 11:31:02 MRFRODO kernel: [    0.857041]   alloc irq_desc for 26 on node -1
Apr  1 11:31:02 MRFRODO kernel: [    0.857043]   alloc kstat_irqs on node -1
Apr  1 11:31:02 MRFRODO kernel: [    0.857053] pcieport 0000:00:1c.2: irq 26 for MSI/MSI-X
Apr  1 11:31:02 MRFRODO kernel: [    0.857066] pcieport 0000:00:1c.2: setting latency timer to 64
Apr  1 11:31:02 MRFRODO kernel: [    0.857245]   alloc irq_desc for 27 on node -1
Apr  1 11:31:02 MRFRODO kernel: [    0.857248]   alloc kstat_irqs on node -1
Apr  1 11:31:02 MRFRODO kernel: [    0.857258] pcieport 0000:00:1c.3: irq 27 for MSI/MSI-X
Apr  1 11:31:02 MRFRODO kernel: [    0.857271] pcieport 0000:00:1c.3: setting latency timer to 64
Apr  1 11:31:02 MRFRODO kernel: [    0.857399] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr  1 11:31:02 MRFRODO kernel: [    0.857556] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Apr  1 11:31:02 MRFRODO kernel: [    0.857713] ACPI: AC Adapter [ACAD] (on-line)
Apr  1 11:31:02 MRFRODO kernel: [    0.857804] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
Apr  1 11:31:02 MRFRODO kernel: [    0.857851] ACPI: Lid Switch [LID0]
Apr  1 11:31:02 MRFRODO kernel: [    0.857904] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
Apr  1 11:31:02 MRFRODO kernel: [    0.857907] ACPI: Power Button [PWRB]
Apr  1 11:31:02 MRFRODO kernel: [    0.857981] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Apr  1 11:31:02 MRFRODO kernel: [    0.857984] ACPI: Power Button [PWRF]
Apr  1 11:31:02 MRFRODO kernel: [    0.858763] ACPI: SSDT 3f6d953d 001F6 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
Apr  1 11:31:02 MRFRODO kernel: [    0.859401] ACPI: SSDT 3f6d8ece 005EA (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
Apr  1 11:31:02 MRFRODO kernel: [    0.862371] Monitor-Mwait will be used to enter C-1 state
Apr  1 11:31:02 MRFRODO kernel: [    0.862412] Monitor-Mwait will be used to enter C-2 state
Apr  1 11:31:02 MRFRODO kernel: [    0.862444] Monitor-Mwait will be used to enter C-3 state
Apr  1 11:31:02 MRFRODO kernel: [    0.862454] Marking TSC unstable due to TSC halts in idle
Apr  1 11:31:02 MRFRODO kernel: [    0.862516] Switching to clocksource hpet
Apr  1 11:31:02 MRFRODO kernel: [    0.862609] processor LNXCPU:00: registered as cooling_device0
Apr  1 11:31:02 MRFRODO kernel: [    0.863053] ACPI: SSDT 3f6d9733 000C8 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
Apr  1 11:31:02 MRFRODO kernel: [    0.863490] ACPI: SSDT 3f6d94b8 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
Apr  1 11:31:02 MRFRODO kernel: [    0.864979] processor LNXCPU:01: registered as cooling_device1
Apr  1 11:31:02 MRFRODO kernel: [    0.885889] ACPI: Battery Slot [BAT1] (battery present)
Apr  1 11:31:02 MRFRODO kernel: [    0.885903] isapnp: Scanning for PnP cards...
Apr  1 11:31:02 MRFRODO kernel: [    0.887080] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Apr  1 11:31:02 MRFRODO kernel: [    0.888720] brd: module loaded
Apr  1 11:31:02 MRFRODO kernel: [    0.889292] loop: module loaded
Apr  1 11:31:02 MRFRODO kernel: [    0.889384] input: Macintosh mouse button emulation as /devices/virtual/input/input3
Apr  1 11:31:02 MRFRODO kernel: [    0.889493] ata_piix 0000:00:1f.1: version 2.13
Apr  1 11:31:02 MRFRODO kernel: [    0.889507] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Apr  1 11:31:02 MRFRODO kernel: [    0.889548] ata_piix 0000:00:1f.1: setting latency timer to 64
Apr  1 11:31:02 MRFRODO kernel: [    0.889630] scsi0 : ata_piix
Apr  1 11:31:02 MRFRODO kernel: [    0.889713] scsi1 : ata_piix
Apr  1 11:31:02 MRFRODO kernel: [    0.890423] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
Apr  1 11:31:02 MRFRODO kernel: [    0.890427] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
Apr  1 11:31:02 MRFRODO kernel: [    0.890848] Fixed MDIO Bus: probed
Apr  1 11:31:02 MRFRODO kernel: [    0.890887] PPP generic driver version 2.4.2
Apr  1 11:31:02 MRFRODO kernel: [    0.890933] tun: Universal TUN/TAP device driver, 1.6
Apr  1 11:31:02 MRFRODO kernel: [    0.890935] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Apr  1 11:31:02 MRFRODO kernel: [    0.891031] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Apr  1 11:31:02 MRFRODO kernel: [    0.891052] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Apr  1 11:31:02 MRFRODO kernel: [    0.891067] ehci_hcd 0000:00:1a.7: setting latency timer to 64
Apr  1 11:31:02 MRFRODO kernel: [    0.891072] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Apr  1 11:31:02 MRFRODO kernel: [    0.891112] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Apr  1 11:31:02 MRFRODO kernel: [    0.891152] ehci_hcd 0000:00:1a.7: debug port 1
Apr  1 11:31:02 MRFRODO kernel: [    0.895038] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
Apr  1 11:31:02 MRFRODO kernel: [    0.895054] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfc504800
Apr  1 11:31:02 MRFRODO kernel: [    0.912017] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Apr  1 11:31:02 MRFRODO kernel: [    0.912126] usb usb1: configuration #1 chosen from 1 choice
Apr  1 11:31:02 MRFRODO kernel: [    0.912161] hub 1-0:1.0: USB hub found
Apr  1 11:31:02 MRFRODO kernel: [    0.912170] hub 1-0:1.0: 4 ports detected
Apr  1 11:31:02 MRFRODO kernel: [    0.912237]   alloc irq_desc for 23 on node -1
Apr  1 11:31:02 MRFRODO kernel: [    0.912240]   alloc kstat_irqs on node -1
Apr  1 11:31:02 MRFRODO kernel: [    0.912247] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Apr  1 11:31:02 MRFRODO kernel: [    0.912259] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Apr  1 11:31:02 MRFRODO kernel: [    0.912264] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Apr  1 11:31:02 MRFRODO kernel: [    0.912302] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Apr  1 11:31:02 MRFRODO kernel: [    0.912332] ehci_hcd 0000:00:1d.7: debug port 1
Apr  1 11:31:02 MRFRODO kernel: [    0.916221] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
Apr  1 11:31:02 MRFRODO kernel: [    0.916236] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfc504c00
Apr  1 11:31:02 MRFRODO kernel: [    0.932016] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Apr  1 11:31:02 MRFRODO kernel: [    0.932099] usb usb2: configuration #1 chosen from 1 choice
Apr  1 11:31:02 MRFRODO kernel: [    0.932133] hub 2-0:1.0: USB hub found
Apr  1 11:31:02 MRFRODO kernel: [    0.932141] hub 2-0:1.0: 6 ports detected
Apr  1 11:31:02 MRFRODO kernel: [    0.932211] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Apr  1 11:31:02 MRFRODO kernel: [    0.932230] uhci_hcd: USB Universal Host Controller Interface driver
Apr  1 11:31:02 MRFRODO kernel: [    0.932253] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr  1 11:31:02 MRFRODO kernel: [    0.932261] uhci_hcd 0000:00:1a.0: setting latency timer to 64
Apr  1 11:31:02 MRFRODO kernel: [    0.932265] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Apr  1 11:31:02 MRFRODO kernel: [    0.932300] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Apr  1 11:31:02 MRFRODO kernel: [    0.932340] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001820
Apr  1 11:31:02 MRFRODO kernel: [    0.932445] usb usb3: configuration #1 chosen from 1 choice
Apr  1 11:31:02 MRFRODO kernel: [    0.932476] hub 3-0:1.0: USB hub found
Apr  1 11:31:02 MRFRODO kernel: [    0.932484] hub 3-0:1.0: 2 ports detected
Apr  1 11:31:02 MRFRODO kernel: [    0.932538]   alloc irq_desc for 21 on node -1
Apr  1 11:31:02 MRFRODO kernel: [    0.932540]   alloc kstat_irqs on node -1
Apr  1 11:31:02 MRFRODO kernel: [    0.932545] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Apr  1 11:31:02 MRFRODO kernel: [    0.932553] uhci_hcd 0000:00:1a.1: setting latency timer to 64
Apr  1 11:31:02 MRFRODO kernel: [    0.932557] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Apr  1 11:31:02 MRFRODO kernel: [    0.932593] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Apr  1 11:31:02 MRFRODO kernel: [    0.932632] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001840
Apr  1 11:31:02 MRFRODO kernel: [    0.932743] usb usb4: configuration #1 chosen from 1 choice
Apr  1 11:31:02 MRFRODO kernel: [    0.932774] hub 4-0:1.0: USB hub found
Apr  1 11:31:02 MRFRODO kernel: [    0.932782] hub 4-0:1.0: 2 ports detected
Apr  1 11:31:02 MRFRODO kernel: [    0.932836] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Apr  1 11:31:02 MRFRODO kernel: [    0.932843] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Apr  1 11:31:02 MRFRODO kernel: [    0.932848] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Apr  1 11:31:02 MRFRODO kernel: [    0.932885] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
Apr  1 11:31:02 MRFRODO kernel: [    0.932915] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
Apr  1 11:31:02 MRFRODO kernel: [    0.933020] usb usb5: configuration #1 chosen from 1 choice
Apr  1 11:31:02 MRFRODO kernel: [    0.933057] hub 5-0:1.0: USB hub found
Apr  1 11:31:02 MRFRODO kernel: [    0.933064] hub 5-0:1.0: 2 ports detected
Apr  1 11:31:02 MRFRODO kernel: [    0.933118] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Apr  1 11:31:02 MRFRODO kernel: [    0.933126] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Apr  1 11:31:02 MRFRODO kernel: [    0.933130] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Apr  1 11:31:02 MRFRODO kernel: [    0.933167] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
Apr  1 11:31:02 MRFRODO kernel: [    0.933209] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
Apr  1 11:31:02 MRFRODO kernel: [    0.933310] usb usb6: configuration #1 chosen from 1 choice
Apr  1 11:31:02 MRFRODO kernel: [    0.933341] hub 6-0:1.0: USB hub found
Apr  1 11:31:02 MRFRODO kernel: [    0.933351] hub 6-0:1.0: 2 ports detected
Apr  1 11:31:02 MRFRODO kernel: [    0.933410] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Apr  1 11:31:02 MRFRODO kernel: [    0.933417] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Apr  1 11:31:02 MRFRODO kernel: [    0.933422] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Apr  1 11:31:02 MRFRODO kernel: [    0.933457] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
Apr  1 11:31:02 MRFRODO kernel: [    0.933488] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
Apr  1 11:31:02 MRFRODO kernel: [    0.933591] usb usb7: configuration #1 chosen from 1 choice
Apr  1 11:31:02 MRFRODO kernel: [    0.933622] hub 7-0:1.0: USB hub found
Apr  1 11:31:02 MRFRODO kernel: [    0.933629] hub 7-0:1.0: 2 ports detected
Apr  1 11:31:02 MRFRODO kernel: [    0.933743] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Apr  1 11:31:02 MRFRODO kernel: [    0.943021] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr  1 11:31:02 MRFRODO kernel: [    0.943108] mice: PS/2 mouse device common for all mice
Apr  1 11:31:02 MRFRODO kernel: [    0.943255] rtc_cmos 00:07: RTC can wake from S4
Apr  1 11:31:02 MRFRODO kernel: [    0.943295] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
Apr  1 11:31:02 MRFRODO kernel: [    0.943330] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
Apr  1 11:31:02 MRFRODO kernel: [    0.943452] device-mapper: uevent: version 1.0.3
Apr  1 11:31:02 MRFRODO kernel: [    0.943559] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
Apr  1 11:31:02 MRFRODO kernel: [    0.943630] device-mapper: multipath: version 1.1.0 loaded
Apr  1 11:31:02 MRFRODO kernel: [    0.943636] device-mapper: multipath round-robin: version 1.0.0 loaded
Apr  1 11:31:02 MRFRODO kernel: [    0.943764] EISA: Probing bus 0 at eisa.0
Apr  1 11:31:02 MRFRODO kernel: [    0.943771] Cannot allocate resource for EISA slot 1
Apr  1 11:31:02 MRFRODO kernel: [    0.943774] Cannot allocate resource for EISA slot 2
Apr  1 11:31:02 MRFRODO kernel: [    0.943777] Cannot allocate resource for EISA slot 3
Apr  1 11:31:02 MRFRODO kernel: [    0.943779] Cannot allocate resource for EISA slot 4
Apr  1 11:31:02 MRFRODO kernel: [    0.943782] Cannot allocate resource for EISA slot 5
Apr  1 11:31:02 MRFRODO kernel: [    0.943798] EISA: Detected 0 cards.
Apr  1 11:31:02 MRFRODO kernel: [    0.943962] cpuidle: using governor ladder
Apr  1 11:31:02 MRFRODO kernel: [    0.944112] cpuidle: using governor menu
Apr  1 11:31:02 MRFRODO kernel: [    0.944662] TCP cubic registered
Apr  1 11:31:02 MRFRODO kernel: [    0.944842] NET: Registered protocol family 10
Apr  1 11:31:02 MRFRODO kernel: [    0.945414] lo: Disabled Privacy Extensions
Apr  1 11:31:02 MRFRODO kernel: [    0.945836] NET: Registered protocol family 17
Apr  1 11:31:02 MRFRODO kernel: [    0.946778] Using IPI No-Shortcut mode
Apr  1 11:31:02 MRFRODO kernel: [    0.946892] PM: Resume from disk failed.
Apr  1 11:31:02 MRFRODO kernel: [    0.946905] registered taskstats version 1
Apr  1 11:31:02 MRFRODO kernel: [    0.947650]   Magic number: 8:655:12
Apr  1 11:31:02 MRFRODO kernel: [    0.947744] rtc_cmos 00:07: setting system clock to 2012-04-01 06:00:49 UTC (1333260049)
Apr  1 11:31:02 MRFRODO kernel: [    0.947748] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Apr  1 11:31:02 MRFRODO kernel: [    0.947750] EDD information not available.
Apr  1 11:31:02 MRFRODO kernel: [    1.085521] ata1.00: ATAPI: MATSHITADVD-RAM UJ-850, RB41, max UDMA/33
Apr  1 11:31:02 MRFRODO kernel: [    1.101446] ata1.00: configured for UDMA/33
Apr  1 11:31:02 MRFRODO kernel: [    1.753813] isapnp: No Plug & Play device found
Apr  1 11:31:02 MRFRODO kernel: [    2.422058] i8042.c: Can't reactivate KBD port.
Apr  1 11:31:02 MRFRODO kernel: [    2.422494] scsi 0:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-850   RB41 PQ: 0 ANSI: 5
Apr  1 11:31:02 MRFRODO kernel: [    2.430390] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Apr  1 11:31:02 MRFRODO kernel: [    2.430396] Uniform CD-ROM driver Revision: 3.20
Apr  1 11:31:02 MRFRODO kernel: [    2.430561] sr 0:0:0:0: Attached scsi CD-ROM sr0
Apr  1 11:31:02 MRFRODO kernel: [    2.430636] sr 0:0:0:0: Attached scsi generic sg0 type 5
Apr  1 11:31:02 MRFRODO kernel: [    2.430721] Freeing unused kernel memory: 656k freed
Apr  1 11:31:02 MRFRODO kernel: [    2.431109] Write protecting the kernel text: 4676k
Apr  1 11:31:02 MRFRODO kernel: [    2.431175] Write protecting the kernel read-only data: 1840k
Apr  1 11:31:02 MRFRODO kernel: [    2.451584] udev: starting version 151
Apr  1 11:31:02 MRFRODO kernel: [    2.476075] usb 1-4: new high speed USB device using ehci_hcd and address 3
Apr  1 11:31:02 MRFRODO kernel: [    2.552780] ahci 0000:00:1f.2: version 3.0
Apr  1 11:31:02 MRFRODO kernel: [    2.552805] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Apr  1 11:31:02 MRFRODO kernel: [    2.552862]   alloc irq_desc for 28 on node -1
Apr  1 11:31:02 MRFRODO kernel: [    2.552865]   alloc kstat_irqs on node -1
Apr  1 11:31:02 MRFRODO kernel: [    2.552879] ahci 0000:00:1f.2: irq 28 for MSI/MSI-X
Apr  1 11:31:02 MRFRODO kernel: [    2.552960] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
Apr  1 11:31:02 MRFRODO kernel: [    2.552965] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ccc 
Apr  1 11:31:02 MRFRODO kernel: [    2.552972] ahci 0000:00:1f.2: setting latency timer to 64
Apr  1 11:31:02 MRFRODO kernel: [    2.571005] scsi2 : ahci
Apr  1 11:31:02 MRFRODO kernel: [    2.585575] tg3.c:v3.102 (September 1, 2009)
Apr  1 11:31:02 MRFRODO kernel: [    2.585613] tg3 0000:06:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Apr  1 11:31:02 MRFRODO kernel: [    2.585630] tg3 0000:06:00.0: setting latency timer to 64
Apr  1 11:31:02 MRFRODO kernel: [    2.590297] scsi3 : ahci
Apr  1 11:31:02 MRFRODO kernel: [    2.605580] scsi4 : ahci
Apr  1 11:31:02 MRFRODO kernel: [    2.605798] ata3: SATA max UDMA/133 abar m2048@0xfc504000 port 0xfc504100 irq 28
Apr  1 11:31:02 MRFRODO kernel: [    2.605803] ata4: SATA max UDMA/133 abar m2048@0xfc504000 port 0xfc504180 irq 28
Apr  1 11:31:02 MRFRODO kernel: [    2.605808] ata5: SATA max UDMA/133 abar m2048@0xfc504000 port 0xfc504200 irq 28
Apr  1 11:31:02 MRFRODO kernel: [    2.617418] usb 1-4: configuration #1 chosen from 1 choice
Apr  1 11:31:02 MRFRODO kernel: [    2.856122] usb 4-1: new full speed USB device using uhci_hcd and address 2
Apr  1 11:31:02 MRFRODO kernel: [    2.870135] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Apr  1 11:31:02 MRFRODO kernel: [    2.894038] eth0: Tigon3 [partno(BCM95906) rev c002] (PCI Express) MAC address 00:1e:ec:07:fd:f0
Apr  1 11:31:02 MRFRODO kernel: [    2.894042] eth0: attached PHY is 5906 (10/100Base-TX Ethernet) (WireSpeed[0])
Apr  1 11:31:02 MRFRODO kernel: [    2.894046] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
Apr  1 11:31:02 MRFRODO kernel: [    2.894049] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
Apr  1 11:31:02 MRFRODO kernel: [    2.924131] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Apr  1 11:31:02 MRFRODO kernel: [    2.924165] ata5: SATA link down (SStatus 0 SControl 300)
Apr  1 11:31:02 MRFRODO kernel: [    2.924194] ata4: SATA link down (SStatus 0 SControl 300)
Apr  1 11:31:02 MRFRODO kernel: [    2.924899] ACPI Warning for \_SB_.PCI0.SATA.PRT0._GTF: Return type mismatch - found Integer, expected Buffer (20090903/nspredef-1006)
Apr  1 11:31:02 MRFRODO kernel: [    2.924909] ata3.00: _GTF unexpected object type 0x1
Apr  1 11:31:02 MRFRODO kernel: [    2.925067] ata3.00: ATA-8: FUJITSU MHW2160BH PL, 0084001E, max UDMA/100
Apr  1 11:31:02 MRFRODO kernel: [    2.925073] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (not used)
Apr  1 11:31:02 MRFRODO kernel: [    2.925974] ata3.00: _GTF unexpected object type 0x1
Apr  1 11:31:02 MRFRODO kernel: [    2.926178] ata3.00: configured for UDMA/100
Apr  1 11:31:02 MRFRODO kernel: [    2.940349] scsi 2:0:0:0: Direct-Access     ATA      FUJITSU MHW2160B 0084 PQ: 0 ANSI: 5
Apr  1 11:31:02 MRFRODO kernel: [    2.940520] sd 2:0:0:0: Attached scsi generic sg1 type 0
Apr  1 11:31:02 MRFRODO kernel: [    2.940632] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Apr  1 11:31:02 MRFRODO kernel: [    2.940690] sd 2:0:0:0: [sda] Write Protect is off
Apr  1 11:31:02 MRFRODO kernel: [    2.940693] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr  1 11:31:02 MRFRODO kernel: [    2.940724] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  1 11:31:02 MRFRODO kernel: [    2.940886]  sda: sda1 sda2 < sda5 > sda3 sda4
Apr  1 11:31:02 MRFRODO kernel: [    2.977585] sd 2:0:0:0: [sda] Attached SCSI disk
Apr  1 11:31:02 MRFRODO kernel: [    2.981278]   alloc irq_desc for 22 on node -1
Apr  1 11:31:02 MRFRODO kernel: [    2.981282]   alloc kstat_irqs on node -1
Apr  1 11:31:02 MRFRODO kernel: [    2.981290] ohci1394 0000:08:06.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Apr  1 11:31:02 MRFRODO kernel: [    3.017840] usb 4-1: configuration #1 chosen from 1 choice
Apr  1 11:31:02 MRFRODO kernel: [    3.038075] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[fc200000-fc2007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Apr  1 11:31:02 MRFRODO kernel: [    3.496326] EXT4-fs (sda1): mounted filesystem with ordered data mode
Apr  1 11:31:02 MRFRODO kernel: [    4.312267] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f82ac404511]
Apr  1 11:31:02 MRFRODO kernel: [    5.091598] Adding 999416k swap on /dev/sda5.  Priority:-1 extents:1 across:999416k 
Apr  1 11:31:02 MRFRODO kernel: [    5.230076] udev: starting version 151
Apr  1 11:31:02 MRFRODO kernel: [    6.301697] Linux video capture interface: v2.00
Apr  1 11:31:02 MRFRODO kernel: [    6.353832] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (04f2:b013)
Apr  1 11:31:02 MRFRODO kernel: [    6.356686] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4:1.0/input/input5
Apr  1 11:31:02 MRFRODO kernel: [    6.356795] usbcore: registered new interface driver uvcvideo
Apr  1 11:31:02 MRFRODO kernel: [    6.356842] USB Video Class driver (v0.1.0)
Apr  1 11:31:02 MRFRODO kernel: [    6.409495] lp: driver loaded but no devices found
Apr  1 11:31:02 MRFRODO kernel: [    6.673960] cfg80211: Calling CRDA to update world regulatory domain
Apr  1 11:31:02 MRFRODO kernel: [    7.002630] cfg80211: World regulatory domain updated:
Apr  1 11:31:02 MRFRODO kernel: [    7.002634] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Apr  1 11:31:02 MRFRODO kernel: [    7.002638] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  1 11:31:02 MRFRODO kernel: [    7.002641] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr  1 11:31:02 MRFRODO kernel: [    7.002644] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr  1 11:31:02 MRFRODO kernel: [    7.002647] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  1 11:31:02 MRFRODO kernel: [    7.002650] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  1 11:31:02 MRFRODO kernel: [    7.062542] sdhci: Secure Digital Host Controller Interface driver
Apr  1 11:31:02 MRFRODO kernel: [    7.062546] sdhci: Copyright(c) Pierre Ossman
Apr  1 11:31:02 MRFRODO kernel: [    7.068786] Linux agpgart interface v0.103
Apr  1 11:31:02 MRFRODO kernel: [    7.127302] sdhci-pci 0000:08:06.1: SDHCI controller found [1180:0822] (rev 19)
Apr  1 11:31:02 MRFRODO kernel: [    7.127326] sdhci-pci 0000:08:06.1: PCI INT B -> GSI 23 (level, low) -> IRQ 23
Apr  1 11:31:02 MRFRODO kernel: [    7.129578] Registered led device: mmc0::
Apr  1 11:31:02 MRFRODO kernel: [    7.130648] mmc0: SDHCI controller on PCI [0000:08:06.1] using PIO
Apr  1 11:31:02 MRFRODO kernel: [    7.157142] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
Apr  1 11:31:02 MRFRODO kernel: [    7.157146] iwl3945: Copyright(c) 2003-2009 Intel Corporation
Apr  1 11:31:02 MRFRODO kernel: [    7.157222] iwl3945 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Apr  1 11:31:02 MRFRODO kernel: [    7.157238] iwl3945 0000:04:00.0: setting latency timer to 64
Apr  1 11:31:02 MRFRODO kernel: [    7.157735] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
Apr  1 11:31:02 MRFRODO kernel: [    7.173043] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
Apr  1 11:31:02 MRFRODO kernel: [    7.178648] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
Apr  1 11:31:02 MRFRODO kernel: [    7.230956] [drm] Initialized drm 1.1.0 20060810
Apr  1 11:31:02 MRFRODO kernel: [    7.235450] iwl3945 0000:04:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
Apr  1 11:31:02 MRFRODO kernel: [    7.235454] iwl3945 0000:04:00.0: Detected Intel Wireless WiFi Link 3945ABG
Apr  1 11:31:02 MRFRODO kernel: [    7.235578]   alloc irq_desc for 29 on node -1
Apr  1 11:31:02 MRFRODO kernel: [    7.235581]   alloc kstat_irqs on node -1
Apr  1 11:31:02 MRFRODO kernel: [    7.235616] iwl3945 0000:04:00.0: irq 29 for MSI/MSI-X
Apr  1 11:31:02 MRFRODO kernel: [    7.476867] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr  1 11:31:02 MRFRODO kernel: [    7.476874] i915 0000:00:02.0: setting latency timer to 64
Apr  1 11:31:02 MRFRODO kernel: [    7.483050]   alloc irq_desc for 30 on node -1
Apr  1 11:31:02 MRFRODO kernel: [    7.483054]   alloc kstat_irqs on node -1
Apr  1 11:31:02 MRFRODO kernel: [    7.483065] i915 0000:00:02.0: irq 30 for MSI/MSI-X
Apr  1 11:31:02 MRFRODO kernel: [    7.483074] [drm] set up 7M of stolen space
Apr  1 11:31:02 MRFRODO kernel: [    7.575107] type=1505 audit(1333260056.124:2):  operation="profile_load" pid=494 name="/sbin/dhclient3"
Apr  1 11:31:02 MRFRODO kernel: [    7.575978] type=1505 audit(1333260056.124:3):  operation="profile_load" pid=494 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Apr  1 11:31:02 MRFRODO kernel: [    7.576464] type=1505 audit(1333260056.128:4):  operation="profile_load" pid=494 name="/usr/lib/connman/scripts/dhclient-script"
Apr  1 11:31:02 MRFRODO kernel: [    7.577042] type=1505 audit(1333260056.128:5):  operation="profile_replace" pid=501 name="/sbin/dhclient3"
Apr  1 11:31:02 MRFRODO kernel: [    7.577917] type=1505 audit(1333260056.128:6):  operation="profile_replace" pid=501 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Apr  1 11:31:02 MRFRODO kernel: [    7.578401] type=1505 audit(1333260056.128:7):  operation="profile_replace" pid=501 name="/usr/lib/connman/scripts/dhclient-script"
Apr  1 11:31:02 MRFRODO kernel: [    7.607093] [drm] initialized overlay support
Apr  1 11:31:02 MRFRODO kernel: [    7.644110] phy0: Selected rate control algorithm 'iwl-3945-rs'
Apr  1 11:31:02 MRFRODO kernel: [    8.194749] fb0: inteldrmfb frame buffer device
Apr  1 11:31:02 MRFRODO kernel: [    8.194752] registered panic notifier
Apr  1 11:31:02 MRFRODO kernel: [    8.206248] acpi device:07: registered as cooling_device2
Apr  1 11:31:02 MRFRODO kernel: [    8.206975] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input6
Apr  1 11:31:02 MRFRODO kernel: [    8.207120] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Apr  1 11:31:02 MRFRODO kernel: [    8.207407] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Apr  1 11:31:02 MRFRODO kernel: [    8.370664] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Apr  1 11:31:02 MRFRODO kernel: [    8.370720] HDA Intel 0000:00:1b.0: setting latency timer to 64
Apr  1 11:31:02 MRFRODO kernel: [    8.411265] vga16fb: initializing
Apr  1 11:31:02 MRFRODO kernel: [    8.411270] vga16fb: mapped to 0xc00a0000
Apr  1 11:31:02 MRFRODO kernel: [    8.411275] vga16fb: not registering due to another framebuffer present
Apr  1 11:31:02 MRFRODO kernel: [    8.568415] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input7
Apr  1 11:31:02 MRFRODO kernel: [    8.605283] Console: switching to colour frame buffer device 160x50
Apr  1 11:31:02 MRFRODO kernel: [   11.164431] EXT4-fs (sda4): mounted filesystem with ordered data mode
Apr  1 11:31:02 MRFRODO kernel: [   12.558030]   alloc irq_desc for 31 on node -1
Apr  1 11:31:02 MRFRODO kernel: [   12.558034]   alloc kstat_irqs on node -1
Apr  1 11:31:02 MRFRODO kernel: [   12.558067] tg3 0000:06:00.0: irq 31 for MSI/MSI-X
Apr  1 11:31:02 MRFRODO kernel: [   12.587962] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr  1 11:31:03 MRFRODO kernel: [   14.457004] type=1505 audit(1333260063.008:8):  operation="profile_replace" pid=922 name="/sbin/dhclient3"
Apr  1 11:31:03 MRFRODO kernel: [   14.457891] type=1505 audit(1333260063.008:9):  operation="profile_replace" pid=922 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Apr  1 11:31:03 MRFRODO kernel: [   14.458382] type=1505 audit(1333260063.008:10):  operation="profile_replace" pid=922 name="/usr/lib/connman/scripts/dhclient-script"
Apr  1 11:31:03 MRFRODO kernel: [   14.608352] type=1505 audit(1333260063.160:11):  operation="profile_load" pid=921 name="/usr/share/gdm/guest-session/Xsession"
Apr  1 11:31:03 MRFRODO kernel: [   14.659177] type=1505 audit(1333260063.208:12):  operation="profile_load" pid=925 name="/usr/lib/cups/backend/cups-pdf"
Apr  1 11:31:03 MRFRODO kernel: [   14.660289] type=1505 audit(1333260063.212:13):  operation="profile_load" pid=925 name="/usr/sbin/cupsd"
Apr  1 11:31:03 MRFRODO kernel: [   14.689284] type=1505 audit(1333260063.240:14):  operation="profile_load" pid=926 name="/usr/sbin/tcpdump"
Apr  1 11:31:03 MRFRODO kernel: [   14.714076] type=1505 audit(1333260063.265:15):  operation="profile_load" pid=923 name="/usr/bin/evince"
Apr  1 11:31:03 MRFRODO kernel: [   14.725417] type=1505 audit(1333260063.277:16):  operation="profile_load" pid=923 name="/usr/bin/evince-previewer"
Apr  1 11:31:03 MRFRODO kernel: [   14.732475] type=1505 audit(1333260063.281:17):  operation="profile_load" pid=923 name="/usr/bin/evince-thumbnailer"
Apr  1 11:31:06 MRFRODO kernel: [   18.092777] ppdev: user-space parallel port driver
Apr  1 11:32:50 MRFRODO kernel: Kernel logging (proc) stopped.
Apr  1 11:33:21 MRFRODO kernel: imklog 4.2.0, log source = /proc/kmsg started.
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] Initializing cgroup subsys cpuset
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] Initializing cgroup subsys cpu
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] Linux version 2.6.32-21-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 (Ubuntu 2.6.32-21.32-generic 2.6.32.11+drm33.2)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] KERNEL supported cpus:
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]   Intel GenuineIntel
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]   AMD AuthenticAMD
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]   NSC Geode by NSC
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]   Cyrix CyrixInstead
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]   Centaur CentaurHauls
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]   Transmeta GenuineTMx86
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]   Transmeta TransmetaCPU
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]   UMC UMC UMC UMC
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] BIOS-provided physical RAM map:
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003f6d0000 (usable)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]  BIOS-e820: 000000003f6d0000 - 000000003f6e3000 (ACPI NVS)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]  BIOS-e820: 000000003f6e3000 - 0000000040000000 (reserved)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] DMI present.
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] last_pfn = 0x3f6d0 max_arch_pfn = 0x100000
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] MTRR default type: uncachable
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] MTRR fixed ranges enabled:
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]   00000-9FFFF write-back
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]   A0000-BFFFF uncachable
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]   C0000-FFFFF write-protect
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] MTRR variable ranges enabled:
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]   0 base 000000000 mask FC0000000 write-back
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]   1 base 03F700000 mask FFFF00000 uncachable
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]   2 base 03F800000 mask FFF800000 uncachable
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]   3 disabled
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]   4 disabled
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]   5 disabled
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]   6 disabled
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]   7 disabled
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] Scanning 1 areas for low memory corruption
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] modified physical RAM map:
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]  modified: 00000000000d2000 - 00000000000d4000 (reserved)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]  modified: 0000000000100000 - 000000003f6d0000 (usable)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]  modified: 000000003f6d0000 - 000000003f6e3000 (ACPI NVS)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]  modified: 000000003f6e3000 - 0000000040000000 (reserved)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] initial memory mapped : 0 - 00c00000
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]  0000400000 - 0037400000 page 2M
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] RAMDISK: 2f1c4000 - 2f95bad3
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] ACPI: RSDP 000f7240 00024 (v02 LENOVO)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] ACPI: XSDT 3f6d864f 00094 (v01 LENOVO TP-68    06040000  LTP 00000000)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] ACPI: FACP 3f6dfbd2 000F4 (v03 TOSCPL CRESTLNE 06040000 ALAN 00000001)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] ACPI: DSDT 3f6d9b4b 06013 (v02 TOSCPL CRESTLNE 06040000 INTL 20060608)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] ACPI: FACS 3f6e2fc0 00040
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] ACPI: APIC 3f6dfcc6 00068 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] ACPI: HPET 3f6dfd2e 00038 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] ACPI: MCFG 3f6dfd66 0003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] ACPI: TCPA 3f6dfda2 00032 (v01 Intel  CRESTLNE 06040000 LOHR 0000005A)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] ACPI: TMOR 3f6dfdd4 00026 (v01 PTLTD           06040000 PTL  00000003)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] ACPI: SLIX 3f6dfdfa 00176 (v01 LENOVO TP-68    06040000 TBD  00000001)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] ACPI: APIC 3f6dff70 00068 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] ACPI: BOOT 3f6dffd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] ACPI: SSDT 3f6d989e 002AD (v01 SataRe SataAhci 00001000 INTL 20050624)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] ACPI: SSDT 3f6d97fb 000A3 (v01 BrtRef  DD01BRT 00001000 INTL 20050624)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] ACPI: SSDT 3f6d8c6f 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] ACPI: SSDT 3f6d8bc9 000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20050624)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] ACPI: SSDT 3f6d86e3 004E6 (v01  PmRef    CpuPm 00003000 INTL 20050624)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify [email]linux-acpi@vger.kernel.org[/email]
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] 126MB HIGHMEM available.
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] 887MB LOWMEM available.
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]   low ram: 0 - 377fe000
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]   node 0 low ram: 00000000 - 377fe000
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]   node 0 bootmap 00008000 - 0000ef00
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]   #3 [0000100000 - 00008d9e98]    TEXT DATA BSS ==> [0000100000 - 00008d9e98]
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]   #4 [002f1c4000 - 002f95bad3]          RAMDISK ==> [002f1c4000 - 002f95bad3]
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]   #5 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]   #6 [00008da000 - 00008dd198]              BRK ==> [00008da000 - 00008dd198]
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] found SMP MP-table at [c00f72c0] f72c0
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] Zone PFN ranges:
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]   HighMem  0x000377fe -> 0x0003f6d0
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] Movable zone start PFN for each node
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] early_node_map[3] active PFN ranges
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]     0: 0x00000000 -> 0x00000002
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]     0: 0x00000006 -> 0x0000009f
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]     0: 0x00000100 -> 0x0003f6d0
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] On node 0 totalpages: 259691
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] free_area_init_node: node 0, pgdat c0798720, node_mem_map c1001000
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]   DMA zone: 0 pages reserved
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]   DMA zone: 3963 pages, LIFO batch:0
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]   Normal zone: 221486 pages, LIFO batch:31
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]   HighMem zone: 254 pages used for memmap
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]   HighMem zone: 32212 pages, LIFO batch:7
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] Using APIC driver default
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] ACPI: IRQ0 used by override.
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] ACPI: IRQ2 used by override.
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] ACPI: IRQ9 used by override.
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] nr_irqs_gsi: 24
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:a0000000)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36024 r0 d21320 u2097152
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] pcpu-alloc: s36024 r0 d21320 u2097152 alloc=1*4194304
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] pcpu-alloc: [0] 0 1 
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257661
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=3feab3eb-2b6a-4043-a49c-763525893dbf ro quiet splash
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] Enabling fast FPU save and restore... done.
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] Initializing CPU#0
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] allocated 5195840 bytes of page_cgroup
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0003f6d0)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] Memory: 1008272k/1039168k available (4673k kernel code, 29992k reserved, 2122k data, 656k init, 129864k highmem)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] virtual kernel memory layout:
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]       .init : 0xc07a3000 - 0xc0847000   ( 656 kB)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]       .data : 0xc0590613 - 0xc07a2e48   (2122 kB)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000]       .text : 0xc0100000 - 0xc0590613   (4673 kB)
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] Hierarchical RCU implementation.
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] NR_IRQS:2304 nr_irqs:424
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] Extended CMOS year: 2000
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] Console: colour VGA+ 80x25
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] console [tty0] enabled
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] hpet clockevent registered
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] Fast TSC calibration using PIT
Apr  1 11:33:21 MRFRODO kernel: [    0.000000] Detected 1662.578 MHz processor.
Apr  1 11:33:21 MRFRODO kernel: [    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 3325.15 BogoMIPS (lpj=6650312)
Apr  1 11:33:21 MRFRODO kernel: [    0.004023] Security Framework initialized
Apr  1 11:33:21 MRFRODO kernel: [    0.004041] AppArmor: AppArmor initialized
Apr  1 11:33:21 MRFRODO kernel: [    0.004049] Mount-cache hash table entries: 512
Apr  1 11:33:21 MRFRODO kernel: [    0.004173] Initializing cgroup subsys ns
Apr  1 11:33:21 MRFRODO kernel: [    0.004178] Initializing cgroup subsys cpuacct
Apr  1 11:33:21 MRFRODO kernel: [    0.004183] Initializing cgroup subsys memory
Apr  1 11:33:21 MRFRODO kernel: [    0.004191] Initializing cgroup subsys devices
Apr  1 11:33:21 MRFRODO kernel: [    0.004194] Initializing cgroup subsys freezer
Apr  1 11:33:21 MRFRODO kernel: [    0.004197] Initializing cgroup subsys net_cls
Apr  1 11:33:21 MRFRODO kernel: [    0.004219] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr  1 11:33:21 MRFRODO kernel: [    0.004222] CPU: L2 cache: 2048K
Apr  1 11:33:21 MRFRODO kernel: [    0.004226] CPU: Physical Processor ID: 0
Apr  1 11:33:21 MRFRODO kernel: [    0.004228] CPU: Processor Core ID: 0
Apr  1 11:33:21 MRFRODO kernel: [    0.004234] mce: CPU supports 6 MCE banks
Apr  1 11:33:21 MRFRODO kernel: [    0.004242] CPU0: Thermal monitoring handled by SMI
Apr  1 11:33:21 MRFRODO kernel: [    0.004245] using mwait in idle threads.
Apr  1 11:33:21 MRFRODO kernel: [    0.004251] Performance Events: Core2 events, Intel PMU driver.
Apr  1 11:33:21 MRFRODO kernel: [    0.004261] ... version:                2
Apr  1 11:33:21 MRFRODO kernel: [    0.004263] ... bit width:              40
Apr  1 11:33:21 MRFRODO kernel: [    0.004265] ... generic registers:      2
Apr  1 11:33:21 MRFRODO kernel: [    0.004267] ... value mask:             000000ffffffffff
Apr  1 11:33:21 MRFRODO kernel: [    0.004270] ... max period:             000000007fffffff
Apr  1 11:33:21 MRFRODO kernel: [    0.004272] ... fixed-purpose events:   3
Apr  1 11:33:21 MRFRODO kernel: [    0.004274] ... event mask:             0000000700000003
Apr  1 11:33:21 MRFRODO kernel: [    0.004278] Checking 'hlt' instruction... OK.
Apr  1 11:33:21 MRFRODO kernel: [    0.023199] ACPI: Core revision 20090903
Apr  1 11:33:21 MRFRODO kernel: [    0.036028] ftrace: converting mcount calls to 0f 1f 44 00 00
Apr  1 11:33:21 MRFRODO kernel: [    0.036037] ftrace: allocating 21771 entries in 43 pages
Apr  1 11:33:21 MRFRODO kernel: [    0.040067] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr  1 11:33:21 MRFRODO kernel: [    0.040448] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr  1 11:33:21 MRFRODO kernel: [    0.083510] CPU0: Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz stepping 0d
Apr  1 11:33:21 MRFRODO kernel: [    0.084001] Booting processor 1 APIC 0x1 ip 0x6000
Apr  1 11:33:21 MRFRODO kernel: [    0.008000] Initializing CPU#1
Apr  1 11:33:21 MRFRODO kernel: [    0.008000] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr  1 11:33:21 MRFRODO kernel: [    0.008000] CPU: L2 cache: 2048K
Apr  1 11:33:21 MRFRODO kernel: [    0.008000] CPU: Physical Processor ID: 0
Apr  1 11:33:21 MRFRODO kernel: [    0.008000] CPU: Processor Core ID: 1
Apr  1 11:33:21 MRFRODO kernel: [    0.008000] CPU1: Thermal monitoring handled by SMI
Apr  1 11:33:21 MRFRODO kernel: [    0.168075] CPU1: Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz stepping 0d
Apr  1 11:33:21 MRFRODO kernel: [    0.168089] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Apr  1 11:33:21 MRFRODO kernel: [    0.172020] Brought up 2 CPUs
Apr  1 11:33:21 MRFRODO kernel: [    0.172024] Total of 2 processors activated (6650.17 BogoMIPS).
Apr  1 11:33:21 MRFRODO kernel: [    0.172554] CPU0 attaching sched-domain:
Apr  1 11:33:21 MRFRODO kernel: [    0.172558]  domain 0: span 0-1 level MC
Apr  1 11:33:21 MRFRODO kernel: [    0.172561]   groups: 0 1
Apr  1 11:33:21 MRFRODO kernel: [    0.172569] CPU1 attaching sched-domain:
Apr  1 11:33:21 MRFRODO kernel: [    0.172572]  domain 0: span 0-1 level MC
Apr  1 11:33:21 MRFRODO kernel: [    0.172575]   groups: 1 0
Apr  1 11:33:21 MRFRODO kernel: [    0.172689] devtmpfs: initialized
Apr  1 11:33:21 MRFRODO kernel: [    0.172689] regulator: core version 0.5
Apr  1 11:33:21 MRFRODO kernel: [    0.172689] Time:  6:03:10  Date: 04/01/12
Apr  1 11:33:21 MRFRODO kernel: [    0.172689] NET: Registered protocol family 16
Apr  1 11:33:21 MRFRODO kernel: [    0.172689] Trying to unpack rootfs image as initramfs...
Apr  1 11:33:21 MRFRODO kernel: [    0.172689] EISA bus registered
Apr  1 11:33:21 MRFRODO kernel: [    0.172689] ACPI: bus type pci registered
Apr  1 11:33:21 MRFRODO kernel: [    0.172689] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Apr  1 11:33:21 MRFRODO kernel: [    0.172689] PCI: MCFG area at e0000000 reserved in E820
Apr  1 11:33:21 MRFRODO kernel: [    0.172689] PCI: Using MMCONFIG for extended config space
Apr  1 11:33:21 MRFRODO kernel: [    0.172689] PCI: Using configuration type 1 for base access
Apr  1 11:33:21 MRFRODO kernel: [    0.176119] bio: create slab <bio-0> at 0
Apr  1 11:33:21 MRFRODO kernel: [    0.177412] ACPI: EC: Look up EC in DSDT
Apr  1 11:33:21 MRFRODO kernel: [    0.184105] ACPI: BIOS _OSI(Linux) query ignored
Apr  1 11:33:21 MRFRODO kernel: [    0.210060] ACPI: Interpreter enabled
Apr  1 11:33:21 MRFRODO kernel: [    0.210060] ACPI: (supports S0 S3 S4 S5)
Apr  1 11:33:21 MRFRODO kernel: [    0.210060] ACPI: Using IOAPIC for interrupt routing
Apr  1 11:33:21 MRFRODO kernel: [    0.252879] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
Apr  1 11:33:21 MRFRODO kernel: [    0.253275] ACPI: No dock devices found.
Apr  1 11:33:21 MRFRODO kernel: [    0.253997] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr  1 11:33:21 MRFRODO kernel: [    0.254120] pci 0000:00:02.0: reg 10 64bit mmio: [0xfc000000-0xfc0fffff]
Apr  1 11:33:21 MRFRODO kernel: [    0.254130] pci 0000:00:02.0: reg 18 64bit mmio pref: [0xd0000000-0xdfffffff]
Apr  1 11:33:21 MRFRODO kernel: [    0.254137] pci 0000:00:02.0: reg 20 io port: [0x1800-0x1807]
Apr  1 11:33:21 MRFRODO kernel: [    0.254190] pci 0000:00:02.1: reg 10 64bit mmio: [0xfc100000-0xfc1fffff]
Apr  1 11:33:21 MRFRODO kernel: [    0.254329] pci 0000:00:1a.0: reg 20 io port: [0x1820-0x183f]
Apr  1 11:33:21 MRFRODO kernel: [    0.254408] pci 0000:00:1a.1: reg 20 io port: [0x1840-0x185f]
Apr  1 11:33:21 MRFRODO kernel: [    0.254496] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfc504800-0xfc504bff]
Apr  1 11:33:21 MRFRODO kernel: [    0.254572] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
Apr  1 11:33:21 MRFRODO kernel: [    0.254579] pci 0000:00:1a.7: PME# disabled
Apr  1 11:33:21 MRFRODO kernel: [    0.254644] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfc300000-0xfc303fff]
Apr  1 11:33:21 MRFRODO kernel: [    0.254717] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Apr  1 11:33:21 MRFRODO kernel: [    0.254723] pci 0000:00:1b.0: PME# disabled
Apr  1 11:33:21 MRFRODO kernel: [    0.254837] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Apr  1 11:33:21 MRFRODO kernel: [    0.254843] pci 0000:00:1c.0: PME# disabled
Apr  1 11:33:21 MRFRODO kernel: [    0.254959] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Apr  1 11:33:21 MRFRODO kernel: [    0.254965] pci 0000:00:1c.1: PME# disabled
Apr  1 11:33:21 MRFRODO kernel: [    0.255082] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Apr  1 11:33:21 MRFRODO kernel: [    0.255088] pci 0000:00:1c.2: PME# disabled
Apr  1 11:33:21 MRFRODO kernel: [    0.255205] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Apr  1 11:33:21 MRFRODO kernel: [    0.255211] pci 0000:00:1c.3: PME# disabled
Apr  1 11:33:21 MRFRODO kernel: [    0.255293] pci 0000:00:1d.0: reg 20 io port: [0x1860-0x187f]
Apr  1 11:33:21 MRFRODO kernel: [    0.255372] pci 0000:00:1d.1: reg 20 io port: [0x1880-0x189f]
Apr  1 11:33:21 MRFRODO kernel: [    0.255451] pci 0000:00:1d.2: reg 20 io port: [0x18a0-0x18bf]
Apr  1 11:33:21 MRFRODO kernel: [    0.255535] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfc504c00-0xfc504fff]
Apr  1 11:33:21 MRFRODO kernel: [    0.255611] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Apr  1 11:33:21 MRFRODO kernel: [    0.255618] pci 0000:00:1d.7: PME# disabled
Apr  1 11:33:21 MRFRODO kernel: [    0.255826] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Apr  1 11:33:21 MRFRODO kernel: [    0.255832] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
Apr  1 11:33:21 MRFRODO kernel: [    0.255837] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0680 (mask 007f)
Apr  1 11:33:21 MRFRODO kernel: [    0.255843] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 1640 (mask 000f)
Apr  1 11:33:21 MRFRODO kernel: [    0.255909] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
Apr  1 11:33:21 MRFRODO kernel: [    0.255919] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
Apr  1 11:33:21 MRFRODO kernel: [    0.255929] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
Apr  1 11:33:21 MRFRODO kernel: [    0.255938] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
Apr  1 11:33:21 MRFRODO kernel: [    0.255948] pci 0000:00:1f.1: reg 20 io port: [0x1810-0x181f]
Apr  1 11:33:21 MRFRODO kernel: [    0.256052] pci 0000:00:1f.2: reg 10 io port: [0x1c00-0x1c07]
Apr  1 11:33:21 MRFRODO kernel: [    0.256062] pci 0000:00:1f.2: reg 14 io port: [0x18d4-0x18d7]
Apr  1 11:33:21 MRFRODO kernel: [    0.256071] pci 0000:00:1f.2: reg 18 io port: [0x18d8-0x18df]
Apr  1 11:33:21 MRFRODO kernel: [    0.256081] pci 0000:00:1f.2: reg 1c io port: [0x18d0-0x18d3]
Apr  1 11:33:21 MRFRODO kernel: [    0.256091] pci 0000:00:1f.2: reg 20 io port: [0x18e0-0x18ff]
Apr  1 11:33:21 MRFRODO kernel: [    0.256101] pci 0000:00:1f.2: reg 24 32bit mmio: [0xfc504000-0xfc5047ff]
Apr  1 11:33:21 MRFRODO kernel: [    0.256153] pci 0000:00:1f.2: PME# supported from D3hot
Apr  1 11:33:21 MRFRODO kernel: [    0.256159] pci 0000:00:1f.2: PME# disabled
Apr  1 11:33:21 MRFRODO kernel: [    0.256199] pci 0000:00:1f.3: reg 10 32bit mmio: [0x000000-0x0000ff]
Apr  1 11:33:21 MRFRODO kernel: [    0.256229] pci 0000:00:1f.3: reg 20 io port: [0x1c20-0x1c3f]
Apr  1 11:33:21 MRFRODO kernel: [    0.256336] pci 0000:00:1c.0: bridge io port: [0x2000-0x2fff]
Apr  1 11:33:21 MRFRODO kernel: [    0.256342] pci 0000:00:1c.0: bridge 32bit mmio: [0xf6000000-0xf7ffffff]
Apr  1 11:33:21 MRFRODO kernel: [    0.256353] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xf0000000-0xf1ffffff]
Apr  1 11:33:21 MRFRODO kernel: [    0.256511] pci 0000:04:00.0: reg 10 32bit mmio: [0xf8000000-0xf8000fff]
Apr  1 11:33:21 MRFRODO kernel: [    0.256769] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
Apr  1 11:33:21 MRFRODO kernel: [    0.256783] pci 0000:04:00.0: PME# disabled
Apr  1 11:33:21 MRFRODO kernel: [    0.256912] pci 0000:00:1c.1: bridge io port: [0x3000-0x3fff]
Apr  1 11:33:21 MRFRODO kernel: [    0.256919] pci 0000:00:1c.1: bridge 32bit mmio: [0xf8000000-0xf9ffffff]
Apr  1 11:33:21 MRFRODO kernel: [    0.256929] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xf2000000-0xf3ffffff]
Apr  1 11:33:21 MRFRODO kernel: [    0.257001] pci 0000:00:1c.2: bridge io port: [0x4000-0x4fff]
Apr  1 11:33:21 MRFRODO kernel: [    0.257008] pci 0000:00:1c.2: bridge 32bit mmio: [0xfa000000-0xfbffffff]
Apr  1 11:33:21 MRFRODO kernel: [    0.257018] pci 0000:00:1c.2: bridge 64bit mmio pref: [0xf4000000-0xf5ffffff]
Apr  1 11:33:21 MRFRODO kernel: [    0.257219] pci 0000:06:00.0: reg 10 64bit mmio: [0xc8000000-0xc800ffff]
Apr  1 11:33:21 MRFRODO kernel: [    0.257471] pci 0000:06:00.0: PME# supported from D3hot D3cold
Apr  1 11:33:21 MRFRODO kernel: [    0.257484] pci 0000:06:00.0: PME# disabled
Apr  1 11:33:21 MRFRODO kernel: [    0.257602] pci 0000:00:1c.3: bridge io port: [0x5000-0x5fff]
Apr  1 11:33:21 MRFRODO kernel: [    0.257608] pci 0000:00:1c.3: bridge 32bit mmio: [0xc8000000-0xc9ffffff]
Apr  1 11:33:21 MRFRODO kernel: [    0.257618] pci 0000:00:1c.3: bridge 64bit mmio pref: [0xcc000000-0xcdffffff]
Apr  1 11:33:21 MRFRODO kernel: [    0.257685] pci 0000:08:06.0: reg 10 32bit mmio: [0xfc200000-0xfc2007ff]
Apr  1 11:33:21 MRFRODO kernel: [    0.257755] pci 0000:08:06.0: supports D1 D2
Apr  1 11:33:21 MRFRODO kernel: [    0.257758] pci 0000:08:06.0: PME# supported from D0 D1 D2 D3hot D3cold
Apr  1 11:33:21 MRFRODO kernel: [    0.257764] pci 0000:08:06.0: PME# disabled
Apr  1 11:33:21 MRFRODO kernel: [    0.257818] pci 0000:08:06.1: reg 10 32bit mmio: [0xfc200800-0xfc2008ff]
Apr  1 11:33:21 MRFRODO kernel: [    0.257889] pci 0000:08:06.1: supports D1 D2
Apr  1 11:33:21 MRFRODO kernel: [    0.257892] pci 0000:08:06.1: PME# supported from D0 D1 D2 D3hot D3cold
Apr  1 11:33:21 MRFRODO kernel: [    0.257898] pci 0000:08:06.1: PME# disabled
Apr  1 11:33:21 MRFRODO kernel: [    0.257952] pci 0000:08:06.2: reg 10 32bit mmio: [0xfc200c00-0xfc200cff]
Apr  1 11:33:21 MRFRODO kernel: [    0.258024] pci 0000:08:06.2: supports D1 D2
Apr  1 11:33:21 MRFRODO kernel: [    0.258026] pci 0000:08:06.2: PME# supported from D0 D1 D2 D3hot D3cold
Apr  1 11:33:21 MRFRODO kernel: [    0.258033] pci 0000:08:06.2: PME# disabled
Apr  1 11:33:21 MRFRODO kernel: [    0.258085] pci 0000:08:06.3: reg 10 32bit mmio: [0xfc201000-0xfc2010ff]
Apr  1 11:33:21 MRFRODO kernel: [    0.258158] pci 0000:08:06.3: supports D1 D2
Apr  1 11:33:21 MRFRODO kernel: [    0.258160] pci 0000:08:06.3: PME# supported from D0 D1 D2 D3hot D3cold
Apr  1 11:33:21 MRFRODO kernel: [    0.258166] pci 0000:08:06.3: PME# disabled
Apr  1 11:33:21 MRFRODO kernel: [    0.258239] pci 0000:00:1e.0: transparent bridge
Apr  1 11:33:21 MRFRODO kernel: [    0.258249] pci 0000:00:1e.0: bridge 32bit mmio: [0xfc200000-0xfc2fffff]
Apr  1 11:33:21 MRFRODO kernel: [    0.258295] pci_bus 0000:00: on NUMA node 0
Apr  1 11:33:21 MRFRODO kernel: [    0.258301] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Apr  1 11:33:21 MRFRODO kernel: [    0.258542] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Apr  1 11:33:21 MRFRODO kernel: [    0.258634] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
Apr  1 11:33:21 MRFRODO kernel: [    0.258725] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
Apr  1 11:33:21 MRFRODO kernel: [    0.258815] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
Apr  1 11:33:21 MRFRODO kernel: [    0.258950] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
Apr  1 11:33:21 MRFRODO kernel: [    0.273066] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
Apr  1 11:33:21 MRFRODO kernel: [    0.273194] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Apr  1 11:33:21 MRFRODO kernel: [    0.273318] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *7 10 12 14 15)
Apr  1 11:33:21 MRFRODO kernel: [    0.273440] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Apr  1 11:33:21 MRFRODO kernel: [    0.273564] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
Apr  1 11:33:21 MRFRODO kernel: [    0.273688] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Apr  1 11:33:21 MRFRODO kernel: [    0.273810] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
Apr  1 11:33:21 MRFRODO kernel: [    0.273936] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
Apr  1 11:33:21 MRFRODO kernel: [    0.274073] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Apr  1 11:33:21 MRFRODO kernel: [    0.274096] vgaarb: loaded
Apr  1 11:33:21 MRFRODO kernel: [    0.274250] SCSI subsystem initialized
Apr  1 11:33:21 MRFRODO kernel: [    0.274367] libata version 3.00 loaded.
Apr  1 11:33:21 MRFRODO kernel: [    0.274456] usbcore: registered new interface driver usbfs
Apr  1 11:33:21 MRFRODO kernel: [    0.274473] usbcore: registered new interface driver hub
Apr  1 11:33:21 MRFRODO kernel: [    0.274504] usbcore: registered new device driver usb
Apr  1 11:33:21 MRFRODO kernel: [    0.274698] ACPI: WMI: Mapper loaded
Apr  1 11:33:21 MRFRODO kernel: [    0.274700] PCI: Using ACPI for IRQ routing
Apr  1 11:33:21 MRFRODO kernel: [    0.274965] NetLabel: Initializing
Apr  1 11:33:21 MRFRODO kernel: [    0.274967] NetLabel:  domain hash size = 128
Apr  1 11:33:21 MRFRODO kernel: [    0.274969] NetLabel:  protocols = UNLABELED CIPSOv4
Apr  1 11:33:21 MRFRODO kernel: [    0.274985] NetLabel:  unlabeled traffic allowed by default
Apr  1 11:33:21 MRFRODO kernel: [    0.275025] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Apr  1 11:33:21 MRFRODO kernel: [    0.275031] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Apr  1 11:33:21 MRFRODO kernel: [    0.280250] Switching to clocksource tsc
Apr  1 11:33:21 MRFRODO kernel: [    0.282610] AppArmor: AppArmor Filesystem Enabled
Apr  1 11:33:21 MRFRODO kernel: [    0.282626] pnp: PnP ACPI init
Apr  1 11:33:21 MRFRODO kernel: [    0.282645] ACPI: bus type pnp registered
Apr  1 11:33:21 MRFRODO kernel: [    0.303852] pnp: PnP ACPI: found 10 devices

---

### Post by sagar_aarya on 2012-04-01
**contd....**
Apr  1 11:33:21 MRFRODO kernel: [    0.303856] ACPI: ACPI bus type pnp unregistered
Apr  1 11:33:21 MRFRODO kernel: [    0.303861] PnPBIOS: Disabled by ACPI PNP
Apr  1 11:33:21 MRFRODO kernel: [    0.303879] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
Apr  1 11:33:21 MRFRODO kernel: [    0.303883] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
Apr  1 11:33:21 MRFRODO kernel: [    0.303887] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
Apr  1 11:33:21 MRFRODO kernel: [    0.303891] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
Apr  1 11:33:21 MRFRODO kernel: [    0.303894] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
Apr  1 11:33:21 MRFRODO kernel: [    0.303898] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
Apr  1 11:33:21 MRFRODO kernel: [    0.303902] system 00:01: iomem range 0xfed40000-0xfed44fff has been reserved
Apr  1 11:33:21 MRFRODO kernel: [    0.303906] system 00:01: iomem range 0xfed45000-0xfed8ffff has been reserved
Apr  1 11:33:21 MRFRODO kernel: [    0.303915] system 00:04: iomem range 0xfed00000-0xfed003ff has been reserved
Apr  1 11:33:21 MRFRODO kernel: [    0.303924] system 00:06: ioport range 0x680-0x69f has been reserved
Apr  1 11:33:21 MRFRODO kernel: [    0.303928] system 00:06: ioport range 0x800-0x80f has been reserved
Apr  1 11:33:21 MRFRODO kernel: [    0.303931] system 00:06: ioport range 0x1000-0x107f has been reserved
Apr  1 11:33:21 MRFRODO kernel: [    0.303935] system 00:06: ioport range 0x1180-0x11bf has been reserved
Apr  1 11:33:21 MRFRODO kernel: [    0.303940] system 00:06: ioport range 0xfe00-0xfe00 has been reserved
Apr  1 11:33:21 MRFRODO kernel: [    0.303944] system 00:06: ioport range 0xff00-0xff7f has been reserved
Apr  1 11:33:21 MRFRODO kernel: [    0.338780] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
Apr  1 11:33:21 MRFRODO kernel: [    0.338786] pci 0000:00:1c.0:   IO window: 0x2000-0x2fff
Apr  1 11:33:21 MRFRODO kernel: [    0.338795] pci 0000:00:1c.0:   MEM window: 0xf6000000-0xf7ffffff
Apr  1 11:33:21 MRFRODO kernel: [    0.338801] pci 0000:00:1c.0:   PREFETCH window: 0x000000f0000000-0x000000f1ffffff
Apr  1 11:33:21 MRFRODO kernel: [    0.338812] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:04
Apr  1 11:33:21 MRFRODO kernel: [    0.338816] pci 0000:00:1c.1:   IO window: 0x3000-0x3fff
Apr  1 11:33:21 MRFRODO kernel: [    0.338825] pci 0000:00:1c.1:   MEM window: 0xf8000000-0xf9ffffff
Apr  1 11:33:21 MRFRODO kernel: [    0.338831] pci 0000:00:1c.1:   PREFETCH window: 0x000000f2000000-0x000000f3ffffff
Apr  1 11:33:21 MRFRODO kernel: [    0.338842] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:05
Apr  1 11:33:21 MRFRODO kernel: [    0.338846] pci 0000:00:1c.2:   IO window: 0x4000-0x4fff
Apr  1 11:33:21 MRFRODO kernel: [    0.338854] pci 0000:00:1c.2:   MEM window: 0xfa000000-0xfbffffff
Apr  1 11:33:21 MRFRODO kernel: [    0.338861] pci 0000:00:1c.2:   PREFETCH window: 0x000000f4000000-0x000000f5ffffff
Apr  1 11:33:21 MRFRODO kernel: [    0.338871] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:06
Apr  1 11:33:21 MRFRODO kernel: [    0.338875] pci 0000:00:1c.3:   IO window: 0x5000-0x5fff
Apr  1 11:33:21 MRFRODO kernel: [    0.338883] pci 0000:00:1c.3:   MEM window: 0xc8000000-0xc9ffffff
Apr  1 11:33:21 MRFRODO kernel: [    0.338890] pci 0000:00:1c.3:   PREFETCH window: 0x000000cc000000-0x000000cdffffff
Apr  1 11:33:21 MRFRODO kernel: [    0.338900] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:08
Apr  1 11:33:21 MRFRODO kernel: [    0.338903] pci 0000:00:1e.0:   IO window: disabled
Apr  1 11:33:21 MRFRODO kernel: [    0.338911] pci 0000:00:1e.0:   MEM window: 0xfc200000-0xfc2fffff
Apr  1 11:33:21 MRFRODO kernel: [    0.338917] pci 0000:00:1e.0:   PREFETCH window: disabled
Apr  1 11:33:21 MRFRODO kernel: [    0.338945]   alloc irq_desc for 17 on node -1
Apr  1 11:33:21 MRFRODO kernel: [    0.338948]   alloc kstat_irqs on node -1
Apr  1 11:33:21 MRFRODO kernel: [    0.338957] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Apr  1 11:33:21 MRFRODO kernel: [    0.338965] pci 0000:00:1c.0: setting latency timer to 64
Apr  1 11:33:21 MRFRODO kernel: [    0.338977]   alloc irq_desc for 16 on node -1
Apr  1 11:33:21 MRFRODO kernel: [    0.338979]   alloc kstat_irqs on node -1
Apr  1 11:33:21 MRFRODO kernel: [    0.338984] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Apr  1 11:33:21 MRFRODO kernel: [    0.338990] pci 0000:00:1c.1: setting latency timer to 64
Apr  1 11:33:21 MRFRODO kernel: [    0.339003]   alloc irq_desc for 18 on node -1
Apr  1 11:33:21 MRFRODO kernel: [    0.339005]   alloc kstat_irqs on node -1
Apr  1 11:33:21 MRFRODO kernel: [    0.339010] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Apr  1 11:33:21 MRFRODO kernel: [    0.339017] pci 0000:00:1c.2: setting latency timer to 64
Apr  1 11:33:21 MRFRODO kernel: [    0.339029]   alloc irq_desc for 19 on node -1
Apr  1 11:33:21 MRFRODO kernel: [    0.339031]   alloc kstat_irqs on node -1
Apr  1 11:33:21 MRFRODO kernel: [    0.339035] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Apr  1 11:33:21 MRFRODO kernel: [    0.339042] pci 0000:00:1c.3: setting latency timer to 64
Apr  1 11:33:21 MRFRODO kernel: [    0.339053] pci 0000:00:1e.0: setting latency timer to 64
Apr  1 11:33:21 MRFRODO kernel: [    0.339058] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Apr  1 11:33:21 MRFRODO kernel: [    0.339062] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
Apr  1 11:33:21 MRFRODO kernel: [    0.339065] pci_bus 0000:02: resource 0 io:  [0x2000-0x2fff]
Apr  1 11:33:21 MRFRODO kernel: [    0.339069] pci_bus 0000:02: resource 1 mem: [0xf6000000-0xf7ffffff]
Apr  1 11:33:21 MRFRODO kernel: [    0.339072] pci_bus 0000:02: resource 2 pref mem [0xf0000000-0xf1ffffff]
Apr  1 11:33:21 MRFRODO kernel: [    0.339076] pci_bus 0000:04: resource 0 io:  [0x3000-0x3fff]
Apr  1 11:33:21 MRFRODO kernel: [    0.339079] pci_bus 0000:04: resource 1 mem: [0xf8000000-0xf9ffffff]
Apr  1 11:33:21 MRFRODO kernel: [    0.339082] pci_bus 0000:04: resource 2 pref mem [0xf2000000-0xf3ffffff]
Apr  1 11:33:21 MRFRODO kernel: [    0.339085] pci_bus 0000:05: resource 0 io:  [0x4000-0x4fff]
Apr  1 11:33:21 MRFRODO kernel: [    0.339089] pci_bus 0000:05: resource 1 mem: [0xfa000000-0xfbffffff]
Apr  1 11:33:21 MRFRODO kernel: [    0.339092] pci_bus 0000:05: resource 2 pref mem [0xf4000000-0xf5ffffff]
Apr  1 11:33:21 MRFRODO kernel: [    0.339095] pci_bus 0000:06: resource 0 io:  [0x5000-0x5fff]
Apr  1 11:33:21 MRFRODO kernel: [    0.339098] pci_bus 0000:06: resource 1 mem: [0xc8000000-0xc9ffffff]
Apr  1 11:33:21 MRFRODO kernel: [    0.339101] pci_bus 0000:06: resource 2 pref mem [0xcc000000-0xcdffffff]
Apr  1 11:33:21 MRFRODO kernel: [    0.339105] pci_bus 0000:08: resource 1 mem: [0xfc200000-0xfc2fffff]
Apr  1 11:33:21 MRFRODO kernel: [    0.339108] pci_bus 0000:08: resource 3 io:  [0x00-0xffff]
Apr  1 11:33:21 MRFRODO kernel: [    0.339111] pci_bus 0000:08: resource 4 mem: [0x000000-0xffffffff]
Apr  1 11:33:21 MRFRODO kernel: [    0.339162] NET: Registered protocol family 2
Apr  1 11:33:21 MRFRODO kernel: [    0.339298] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr  1 11:33:21 MRFRODO kernel: [    0.339737] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Apr  1 11:33:21 MRFRODO kernel: [    0.340295] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Apr  1 11:33:21 MRFRODO kernel: [    0.340609] TCP: Hash tables configured (established 131072 bind 65536)
Apr  1 11:33:21 MRFRODO kernel: [    0.340613] TCP reno registered
Apr  1 11:33:21 MRFRODO kernel: [    0.340719] NET: Registered protocol family 1
Apr  1 11:33:21 MRFRODO kernel: [    0.340749] pci 0000:00:02.0: Boot video device
Apr  1 11:33:21 MRFRODO kernel: [    0.340942] Simple Boot Flag at 0x36 set to 0x1
Apr  1 11:33:21 MRFRODO kernel: [    0.341157] cpufreq-nforce2: No nForce2 chipset.
Apr  1 11:33:21 MRFRODO kernel: [    0.341190] Scanning for low memory corruption every 60 seconds
Apr  1 11:33:21 MRFRODO kernel: [    0.341336] audit: initializing netlink socket (disabled)
Apr  1 11:33:21 MRFRODO kernel: [    0.341350] type=2000 audit(1333260189.339:1): initialized
Apr  1 11:33:21 MRFRODO kernel: [    0.353403] highmem bounce pool size: 64 pages
Apr  1 11:33:21 MRFRODO kernel: [    0.353410] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Apr  1 11:33:21 MRFRODO kernel: [    0.355318] VFS: Disk quotas dquot_6.5.2
Apr  1 11:33:21 MRFRODO kernel: [    0.355393] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr  1 11:33:21 MRFRODO kernel: [    0.356111] fuse init (API version 7.13)
Apr  1 11:33:21 MRFRODO kernel: [    0.356220] msgmni has been set to 1716
Apr  1 11:33:21 MRFRODO kernel: [    0.356477] alg: No test for stdrng (krng)
Apr  1 11:33:21 MRFRODO kernel: [    0.356541] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Apr  1 11:33:21 MRFRODO kernel: [    0.356545] io scheduler noop registered
Apr  1 11:33:21 MRFRODO kernel: [    0.356548] io scheduler anticipatory registered
Apr  1 11:33:21 MRFRODO kernel: [    0.356550] io scheduler deadline registered
Apr  1 11:33:21 MRFRODO kernel: [    0.356597] io scheduler cfq registered (default)
Apr  1 11:33:21 MRFRODO kernel: [    0.356818]   alloc irq_desc for 24 on node -1
Apr  1 11:33:21 MRFRODO kernel: [    0.356821]   alloc kstat_irqs on node -1
Apr  1 11:33:21 MRFRODO kernel: [    0.356835] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
Apr  1 11:33:21 MRFRODO kernel: [    0.356849] pcieport 0000:00:1c.0: setting latency timer to 64
Apr  1 11:33:21 MRFRODO kernel: [    0.357032]   alloc irq_desc for 25 on node -1
Apr  1 11:33:21 MRFRODO kernel: [    0.357035]   alloc kstat_irqs on node -1
Apr  1 11:33:21 MRFRODO kernel: [    0.357045] pcieport 0000:00:1c.1: irq 25 for MSI/MSI-X
Apr  1 11:33:21 MRFRODO kernel: [    0.357058] pcieport 0000:00:1c.1: setting latency timer to 64
Apr  1 11:33:21 MRFRODO kernel: [    0.357240]   alloc irq_desc for 26 on node -1
Apr  1 11:33:21 MRFRODO kernel: [    0.357243]   alloc kstat_irqs on node -1
Apr  1 11:33:21 MRFRODO kernel: [    0.357254] pcieport 0000:00:1c.2: irq 26 for MSI/MSI-X
Apr  1 11:33:21 MRFRODO kernel: [    0.357267] pcieport 0000:00:1c.2: setting latency timer to 64
Apr  1 11:33:21 MRFRODO kernel: [    0.357447]   alloc irq_desc for 27 on node -1
Apr  1 11:33:21 MRFRODO kernel: [    0.357449]   alloc kstat_irqs on node -1
Apr  1 11:33:21 MRFRODO kernel: [    0.357460] pcieport 0000:00:1c.3: irq 27 for MSI/MSI-X
Apr  1 11:33:21 MRFRODO kernel: [    0.357473] pcieport 0000:00:1c.3: setting latency timer to 64
Apr  1 11:33:21 MRFRODO kernel: [    0.357601] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr  1 11:33:21 MRFRODO kernel: [    0.357760] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Apr  1 11:33:21 MRFRODO kernel: [    0.357918] ACPI: AC Adapter [ACAD] (on-line)
Apr  1 11:33:21 MRFRODO kernel: [    0.357993] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
Apr  1 11:33:21 MRFRODO kernel: [    0.358039] ACPI: Lid Switch [LID0]
Apr  1 11:33:21 MRFRODO kernel: [    0.358092] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
Apr  1 11:33:21 MRFRODO kernel: [    0.358096] ACPI: Power Button [PWRB]
Apr  1 11:33:21 MRFRODO kernel: [    0.358173] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Apr  1 11:33:21 MRFRODO kernel: [    0.358177] ACPI: Power Button [PWRF]
Apr  1 11:33:21 MRFRODO kernel: [    0.358977] ACPI: SSDT 3f6d953d 001F6 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
Apr  1 11:33:21 MRFRODO kernel: [    0.359631] ACPI: SSDT 3f6d8ece 005EA (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
Apr  1 11:33:21 MRFRODO kernel: [    0.362705] Monitor-Mwait will be used to enter C-1 state
Apr  1 11:33:21 MRFRODO kernel: [    0.362741] Monitor-Mwait will be used to enter C-2 state
Apr  1 11:33:21 MRFRODO kernel: [    0.362771] Monitor-Mwait will be used to enter C-3 state
Apr  1 11:33:21 MRFRODO kernel: [    0.362778] Marking TSC unstable due to TSC halts in idle
Apr  1 11:33:21 MRFRODO kernel: [    0.362864] processor LNXCPU:00: registered as cooling_device0
Apr  1 11:33:21 MRFRODO kernel: [    0.363310] ACPI: SSDT 3f6d9733 000C8 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
Apr  1 11:33:21 MRFRODO kernel: [    0.363748] ACPI: SSDT 3f6d94b8 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
Apr  1 11:33:21 MRFRODO kernel: [    0.364896] Switching to clocksource hpet
Apr  1 11:33:21 MRFRODO kernel: [    0.366013] processor LNXCPU:01: registered as cooling_device1
Apr  1 11:33:21 MRFRODO kernel: [    0.391222] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Apr  1 11:33:21 MRFRODO kernel: [    0.392899] brd: module loaded
Apr  1 11:33:21 MRFRODO kernel: [    0.393522] loop: module loaded
Apr  1 11:33:21 MRFRODO kernel: [    0.393625] input: Macintosh mouse button emulation as /devices/virtual/input/input3
Apr  1 11:33:21 MRFRODO kernel: [    0.393745] ata_piix 0000:00:1f.1: version 2.13
Apr  1 11:33:21 MRFRODO kernel: [    0.393761] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Apr  1 11:33:21 MRFRODO kernel: [    0.393812] ata_piix 0000:00:1f.1: setting latency timer to 64
Apr  1 11:33:21 MRFRODO kernel: [    0.394017] scsi0 : ata_piix
Apr  1 11:33:21 MRFRODO kernel: [    0.394113] scsi1 : ata_piix
Apr  1 11:33:21 MRFRODO kernel: [    0.394832] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
Apr  1 11:33:21 MRFRODO kernel: [    0.394837] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
Apr  1 11:33:21 MRFRODO kernel: [    0.395265] Fixed MDIO Bus: probed
Apr  1 11:33:21 MRFRODO kernel: [    0.395305] PPP generic driver version 2.4.2
Apr  1 11:33:21 MRFRODO kernel: [    0.395355] tun: Universal TUN/TAP device driver, 1.6
Apr  1 11:33:21 MRFRODO kernel: [    0.395358] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Apr  1 11:33:21 MRFRODO kernel: [    0.395458] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Apr  1 11:33:21 MRFRODO kernel: [    0.395481] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Apr  1 11:33:21 MRFRODO kernel: [    0.395500] ehci_hcd 0000:00:1a.7: setting latency timer to 64
Apr  1 11:33:21 MRFRODO kernel: [    0.395505] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Apr  1 11:33:21 MRFRODO kernel: [    0.395546] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Apr  1 11:33:21 MRFRODO kernel: [    0.395582] ehci_hcd 0000:00:1a.7: debug port 1
Apr  1 11:33:21 MRFRODO kernel: [    0.399483] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
Apr  1 11:33:21 MRFRODO kernel: [    0.400052] ACPI: Battery Slot [BAT1] (battery present)
Apr  1 11:33:21 MRFRODO kernel: [    0.400065] isapnp: Scanning for PnP cards...
Apr  1 11:33:21 MRFRODO kernel: [    0.405648] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfc504800
Apr  1 11:33:21 MRFRODO kernel: [    0.417201] Freeing initrd memory: 7774k freed
Apr  1 11:33:21 MRFRODO kernel: [    0.436027] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Apr  1 11:33:21 MRFRODO kernel: [    0.436229] usb usb1: configuration #1 chosen from 1 choice
Apr  1 11:33:21 MRFRODO kernel: [    0.436266] hub 1-0:1.0: USB hub found
Apr  1 11:33:21 MRFRODO kernel: [    0.436279] hub 1-0:1.0: 4 ports detected
Apr  1 11:33:21 MRFRODO kernel: [    0.436368]   alloc irq_desc for 23 on node -1
Apr  1 11:33:21 MRFRODO kernel: [    0.436370]   alloc kstat_irqs on node -1
Apr  1 11:33:21 MRFRODO kernel: [    0.436380] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Apr  1 11:33:21 MRFRODO kernel: [    0.436410] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Apr  1 11:33:21 MRFRODO kernel: [    0.436414] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Apr  1 11:33:21 MRFRODO kernel: [    0.436458] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Apr  1 11:33:21 MRFRODO kernel: [    0.436496] ehci_hcd 0000:00:1d.7: debug port 1
Apr  1 11:33:21 MRFRODO kernel: [    0.440381] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
Apr  1 11:33:21 MRFRODO kernel: [    0.440403] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfc504c00
Apr  1 11:33:21 MRFRODO kernel: [    0.456016] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Apr  1 11:33:21 MRFRODO kernel: [    0.456109] usb usb2: configuration #1 chosen from 1 choice
Apr  1 11:33:21 MRFRODO kernel: [    0.456141] hub 2-0:1.0: USB hub found
Apr  1 11:33:21 MRFRODO kernel: [    0.456151] hub 2-0:1.0: 6 ports detected
Apr  1 11:33:21 MRFRODO kernel: [    0.456231] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Apr  1 11:33:21 MRFRODO kernel: [    0.456256] uhci_hcd: USB Universal Host Controller Interface driver
Apr  1 11:33:21 MRFRODO kernel: [    0.456311] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr  1 11:33:21 MRFRODO kernel: [    0.456321] uhci_hcd 0000:00:1a.0: setting latency timer to 64
Apr  1 11:33:21 MRFRODO kernel: [    0.456326] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Apr  1 11:33:21 MRFRODO kernel: [    0.456367] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Apr  1 11:33:21 MRFRODO kernel: [    0.456409] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001820
Apr  1 11:33:21 MRFRODO kernel: [    0.456516] usb usb3: configuration #1 chosen from 1 choice
Apr  1 11:33:21 MRFRODO kernel: [    0.456547] hub 3-0:1.0: USB hub found
Apr  1 11:33:21 MRFRODO kernel: [    0.456557] hub 3-0:1.0: 2 ports detected
Apr  1 11:33:21 MRFRODO kernel: [    0.456613]   alloc irq_desc for 21 on node -1
Apr  1 11:33:21 MRFRODO kernel: [    0.456615]   alloc kstat_irqs on node -1
Apr  1 11:33:21 MRFRODO kernel: [    0.456621] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Apr  1 11:33:21 MRFRODO kernel: [    0.456629] uhci_hcd 0000:00:1a.1: setting latency timer to 64
Apr  1 11:33:21 MRFRODO kernel: [    0.456633] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Apr  1 11:33:21 MRFRODO kernel: [    0.456679] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Apr  1 11:33:21 MRFRODO kernel: [    0.456719] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001840
Apr  1 11:33:21 MRFRODO kernel: [    0.456830] usb usb4: configuration #1 chosen from 1 choice
Apr  1 11:33:21 MRFRODO kernel: [    0.456861] hub 4-0:1.0: USB hub found
Apr  1 11:33:21 MRFRODO kernel: [    0.456872] hub 4-0:1.0: 2 ports detected
Apr  1 11:33:21 MRFRODO kernel: [    0.456930] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Apr  1 11:33:21 MRFRODO kernel: [    0.456938] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Apr  1 11:33:21 MRFRODO kernel: [    0.456942] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Apr  1 11:33:21 MRFRODO kernel: [    0.456985] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
Apr  1 11:33:21 MRFRODO kernel: [    0.457015] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
Apr  1 11:33:21 MRFRODO kernel: [    0.457125] usb usb5: configuration #1 chosen from 1 choice
Apr  1 11:33:21 MRFRODO kernel: [    0.457155] hub 5-0:1.0: USB hub found
Apr  1 11:33:21 MRFRODO kernel: [    0.457164] hub 5-0:1.0: 2 ports detected
Apr  1 11:33:21 MRFRODO kernel: [    0.457222] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Apr  1 11:33:21 MRFRODO kernel: [    0.457230] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Apr  1 11:33:21 MRFRODO kernel: [    0.457234] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Apr  1 11:33:21 MRFRODO kernel: [    0.457274] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
Apr  1 11:33:21 MRFRODO kernel: [    0.457314] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
Apr  1 11:33:21 MRFRODO kernel: [    0.457430] usb usb6: configuration #1 chosen from 1 choice
Apr  1 11:33:21 MRFRODO kernel: [    0.457461] hub 6-0:1.0: USB hub found
Apr  1 11:33:21 MRFRODO kernel: [    0.457472] hub 6-0:1.0: 2 ports detected
Apr  1 11:33:21 MRFRODO kernel: [    0.457532] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Apr  1 11:33:21 MRFRODO kernel: [    0.457540] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Apr  1 11:33:21 MRFRODO kernel: [    0.457544] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Apr  1 11:33:21 MRFRODO kernel: [    0.457580] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
Apr  1 11:33:21 MRFRODO kernel: [    0.457612] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
Apr  1 11:33:21 MRFRODO kernel: [    0.457719] usb usb7: configuration #1 chosen from 1 choice
Apr  1 11:33:21 MRFRODO kernel: [    0.457753] hub 7-0:1.0: USB hub found
Apr  1 11:33:21 MRFRODO kernel: [    0.457762] hub 7-0:1.0: 2 ports detected
Apr  1 11:33:21 MRFRODO kernel: [    0.457881] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Apr  1 11:33:21 MRFRODO kernel: [    0.482378] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr  1 11:33:21 MRFRODO kernel: [    0.482386] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr  1 11:33:21 MRFRODO kernel: [    0.482532] mice: PS/2 mouse device common for all mice
Apr  1 11:33:21 MRFRODO kernel: [    0.484217] rtc_cmos 00:07: RTC can wake from S4
Apr  1 11:33:21 MRFRODO kernel: [    0.484275] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
Apr  1 11:33:21 MRFRODO kernel: [    0.484310] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
Apr  1 11:33:21 MRFRODO kernel: [    0.484426] device-mapper: uevent: version 1.0.3
Apr  1 11:33:21 MRFRODO kernel: [    0.484561] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
Apr  1 11:33:21 MRFRODO kernel: [    0.484641] device-mapper: multipath: version 1.1.0 loaded
Apr  1 11:33:21 MRFRODO kernel: [    0.484644] device-mapper: multipath round-robin: version 1.0.0 loaded
Apr  1 11:33:21 MRFRODO kernel: [    0.484772] EISA: Probing bus 0 at eisa.0
Apr  1 11:33:21 MRFRODO kernel: [    0.484779] Cannot allocate resource for EISA slot 1
Apr  1 11:33:21 MRFRODO kernel: [    0.484782] Cannot allocate resource for EISA slot 2
Apr  1 11:33:21 MRFRODO kernel: [    0.484785] Cannot allocate resource for EISA slot 3
Apr  1 11:33:21 MRFRODO kernel: [    0.484787] Cannot allocate resource for EISA slot 4
Apr  1 11:33:21 MRFRODO kernel: [    0.484790] Cannot allocate resource for EISA slot 5
Apr  1 11:33:21 MRFRODO kernel: [    0.484806] EISA: Detected 0 cards.
Apr  1 11:33:21 MRFRODO kernel: [    0.484981] cpuidle: using governor ladder
Apr  1 11:33:21 MRFRODO kernel: [    0.485124] cpuidle: using governor menu
Apr  1 11:33:21 MRFRODO kernel: [    0.485680] TCP cubic registered
Apr  1 11:33:21 MRFRODO kernel: [    0.485866] NET: Registered protocol family 10
Apr  1 11:33:21 MRFRODO kernel: [    0.486448] lo: Disabled Privacy Extensions
Apr  1 11:33:21 MRFRODO kernel: [    0.486871] NET: Registered protocol family 17
Apr  1 11:33:21 MRFRODO kernel: [    0.487950] Using IPI No-Shortcut mode
Apr  1 11:33:21 MRFRODO kernel: [    0.488095] PM: Resume from disk failed.
Apr  1 11:33:21 MRFRODO kernel: [    0.488110] registered taskstats version 1
Apr  1 11:33:21 MRFRODO kernel: [    0.488851]   Magic number: 8:208:63
Apr  1 11:33:21 MRFRODO kernel: [    0.488943] rtc_cmos 00:07: setting system clock to 2012-04-01 06:03:10 UTC (1333260190)
Apr  1 11:33:21 MRFRODO kernel: [    0.488947] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Apr  1 11:33:21 MRFRODO kernel: [    0.488949] EDD information not available.
Apr  1 11:33:21 MRFRODO kernel: [    0.502752] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Apr  1 11:33:21 MRFRODO kernel: [    0.564521] ata1.00: ATAPI: MATSHITADVD-RAM UJ-850, RB41, max UDMA/33
Apr  1 11:33:21 MRFRODO kernel: [    0.583854] ata1.00: configured for UDMA/33
Apr  1 11:33:21 MRFRODO kernel: [    0.758669] isapnp: No Plug & Play device found
Apr  1 11:33:21 MRFRODO kernel: [    0.760758] scsi 0:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-850   RB41 PQ: 0 ANSI: 5
Apr  1 11:33:21 MRFRODO kernel: [    0.765550] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Apr  1 11:33:21 MRFRODO kernel: [    0.765555] Uniform CD-ROM driver Revision: 3.20
Apr  1 11:33:21 MRFRODO kernel: [    0.765725] sr 0:0:0:0: Attached scsi CD-ROM sr0
Apr  1 11:33:21 MRFRODO kernel: [    0.765793] sr 0:0:0:0: Attached scsi generic sg0 type 5
Apr  1 11:33:21 MRFRODO kernel: [    0.765875] Freeing unused kernel memory: 656k freed
Apr  1 11:33:21 MRFRODO kernel: [    0.766265] Write protecting the kernel text: 4676k
Apr  1 11:33:21 MRFRODO kernel: [    0.766329] Write protecting the kernel read-only data: 1840k
Apr  1 11:33:21 MRFRODO kernel: [    0.786422] udev: starting version 151
Apr  1 11:33:21 MRFRODO kernel: [    0.856051] usb 1-4: new high speed USB device using ehci_hcd and address 3
Apr  1 11:33:21 MRFRODO kernel: [    0.873959] tg3.c:v3.102 (September 1, 2009)
Apr  1 11:33:21 MRFRODO kernel: [    0.873997] tg3 0000:06:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Apr  1 11:33:21 MRFRODO kernel: [    0.874015] tg3 0000:06:00.0: setting latency timer to 64
Apr  1 11:33:21 MRFRODO kernel: [    0.874361] ahci 0000:00:1f.2: version 3.0
Apr  1 11:33:21 MRFRODO kernel: [    0.874377] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Apr  1 11:33:21 MRFRODO kernel: [    0.874423]   alloc irq_desc for 28 on node -1
Apr  1 11:33:21 MRFRODO kernel: [    0.874426]   alloc kstat_irqs on node -1
Apr  1 11:33:21 MRFRODO kernel: [    0.874442] ahci 0000:00:1f.2: irq 28 for MSI/MSI-X
Apr  1 11:33:21 MRFRODO kernel: [    0.874528] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
Apr  1 11:33:21 MRFRODO kernel: [    0.874533] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ccc 
Apr  1 11:33:21 MRFRODO kernel: [    0.874539] ahci 0000:00:1f.2: setting latency timer to 64
Apr  1 11:33:21 MRFRODO kernel: [    0.919258] scsi2 : ahci
Apr  1 11:33:21 MRFRODO kernel: [    0.937371] scsi3 : ahci
Apr  1 11:33:21 MRFRODO kernel: [    0.944933] scsi4 : ahci
Apr  1 11:33:21 MRFRODO kernel: [    0.945212] ata3: SATA max UDMA/133 abar m2048@0xfc504000 port 0xfc504100 irq 28
Apr  1 11:33:21 MRFRODO kernel: [    0.945217] ata4: SATA max UDMA/133 abar m2048@0xfc504000 port 0xfc504180 irq 28
Apr  1 11:33:21 MRFRODO kernel: [    0.945221] ata5: SATA max UDMA/133 abar m2048@0xfc504000 port 0xfc504200 irq 28
Apr  1 11:33:21 MRFRODO kernel: [    0.997368] usb 1-4: configuration #1 chosen from 1 choice
Apr  1 11:33:21 MRFRODO kernel: [    1.222139] eth0: Tigon3 [partno(BCM95906) rev c002] (PCI Express) MAC address 00:1e:ec:07:fd:f0
Apr  1 11:33:21 MRFRODO kernel: [    1.222143] eth0: attached PHY is 5906 (10/100Base-TX Ethernet) (WireSpeed[0])
Apr  1 11:33:21 MRFRODO kernel: [    1.222147] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]

---

### Post by sagar_aarya on 2012-04-01
contd...

Apr  1 11:33:21 MRFRODO kernel: [    1.222150] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
Apr  1 11:33:21 MRFRODO kernel: [    1.236078] usb 4-1: new full speed USB device using uhci_hcd and address 2
Apr  1 11:33:21 MRFRODO kernel: [    1.264088] ata5: SATA link down (SStatus 0 SControl 300)
Apr  1 11:33:21 MRFRODO kernel: [    1.264122] ata4: SATA link down (SStatus 0 SControl 300)
Apr  1 11:33:21 MRFRODO kernel: [    1.264154] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Apr  1 11:33:21 MRFRODO kernel: [    1.264879] ACPI Warning for \_SB_.PCI0.SATA.PRT0._GTF: Return type mismatch - found Integer, expected Buffer (20090903/nspredef-1006)
Apr  1 11:33:21 MRFRODO kernel: [    1.264889] ata3.00: _GTF unexpected object type 0x1
Apr  1 11:33:21 MRFRODO kernel: [    1.265059] ata3.00: ATA-8: FUJITSU MHW2160BH PL, 0084001E, max UDMA/100
Apr  1 11:33:21 MRFRODO kernel: [    1.265066] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (not used)
Apr  1 11:33:21 MRFRODO kernel: [    1.265967] ata3.00: _GTF unexpected object type 0x1
Apr  1 11:33:21 MRFRODO kernel: [    1.266177] ata3.00: configured for UDMA/100
Apr  1 11:33:21 MRFRODO kernel: [    1.280288] scsi 2:0:0:0: Direct-Access     ATA      FUJITSU MHW2160B 0084 PQ: 0 ANSI: 5
Apr  1 11:33:21 MRFRODO kernel: [    1.280462] sd 2:0:0:0: Attached scsi generic sg1 type 0
Apr  1 11:33:21 MRFRODO kernel: [    1.280472] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Apr  1 11:33:21 MRFRODO kernel: [    1.280542] sd 2:0:0:0: [sda] Write Protect is off
Apr  1 11:33:21 MRFRODO kernel: [    1.280546] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr  1 11:33:21 MRFRODO kernel: [    1.280638] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  1 11:33:21 MRFRODO kernel: [    1.280805]  sda: sda1 sda2 < sda5 > sda3 sda4
Apr  1 11:33:21 MRFRODO kernel: [    1.316522] sd 2:0:0:0: [sda] Attached SCSI disk
Apr  1 11:33:21 MRFRODO kernel: [    1.319930]   alloc irq_desc for 22 on node -1
Apr  1 11:33:21 MRFRODO kernel: [    1.319933]   alloc kstat_irqs on node -1
Apr  1 11:33:21 MRFRODO kernel: [    1.319941] ohci1394 0000:08:06.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Apr  1 11:33:21 MRFRODO kernel: [    1.378069] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[fc200000-fc2007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Apr  1 11:33:21 MRFRODO kernel: [    1.397922] usb 4-1: configuration #1 chosen from 1 choice
Apr  1 11:33:21 MRFRODO kernel: [    1.746317] EXT4-fs (sda1): mounted filesystem with ordered data mode
Apr  1 11:33:21 MRFRODO kernel: [    2.656494] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f82ac404511]
Apr  1 11:33:21 MRFRODO kernel: [    9.307702] udev: starting version 151
Apr  1 11:33:21 MRFRODO kernel: [    9.337276] Adding 999416k swap on /dev/sda5.  Priority:-1 extents:1 across:999416k 
Apr  1 11:33:21 MRFRODO kernel: [    9.526549] Linux agpgart interface v0.103
Apr  1 11:33:21 MRFRODO kernel: [    9.538380] lp: driver loaded but no devices found
Apr  1 11:33:21 MRFRODO kernel: [    9.599080] Linux video capture interface: v2.00
Apr  1 11:33:21 MRFRODO kernel: [    9.603035] cfg80211: Calling CRDA to update world regulatory domain
Apr  1 11:33:21 MRFRODO kernel: [    9.603615] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (04f2:b013)
Apr  1 11:33:21 MRFRODO kernel: [    9.617768] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
Apr  1 11:33:21 MRFRODO kernel: [    9.618437] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
Apr  1 11:33:21 MRFRODO kernel: [    9.627714] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4:1.0/input/input5
Apr  1 11:33:21 MRFRODO kernel: [    9.627784] usbcore: registered new interface driver uvcvideo
Apr  1 11:33:21 MRFRODO kernel: [    9.627788] USB Video Class driver (v0.1.0)
Apr  1 11:33:21 MRFRODO kernel: [    9.664913] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
Apr  1 11:33:21 MRFRODO kernel: [    9.673628] cfg80211: World regulatory domain updated:
Apr  1 11:33:21 MRFRODO kernel: [    9.673632] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Apr  1 11:33:21 MRFRODO kernel: [    9.673636] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  1 11:33:21 MRFRODO kernel: [    9.673639] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr  1 11:33:21 MRFRODO kernel: [    9.673643] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr  1 11:33:21 MRFRODO kernel: [    9.673646] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  1 11:33:21 MRFRODO kernel: [    9.673649] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  1 11:33:21 MRFRODO kernel: [    9.675611] sdhci: Secure Digital Host Controller Interface driver
Apr  1 11:33:21 MRFRODO kernel: [    9.675614] sdhci: Copyright(c) Pierre Ossman
Apr  1 11:33:21 MRFRODO kernel: [    9.676513] [drm] Initialized drm 1.1.0 20060810
Apr  1 11:33:21 MRFRODO kernel: [    9.677259] sdhci-pci 0000:08:06.1: SDHCI controller found [1180:0822] (rev 19)
Apr  1 11:33:21 MRFRODO kernel: [    9.677281] sdhci-pci 0000:08:06.1: PCI INT B -> GSI 23 (level, low) -> IRQ 23
Apr  1 11:33:21 MRFRODO kernel: [    9.679360] Registered led device: mmc0::
Apr  1 11:33:21 MRFRODO kernel: [    9.680452] mmc0: SDHCI controller on PCI [0000:08:06.1] using PIO
Apr  1 11:33:21 MRFRODO kernel: [    9.780152] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr  1 11:33:21 MRFRODO kernel: [    9.780159] i915 0000:00:02.0: setting latency timer to 64
Apr  1 11:33:21 MRFRODO kernel: [    9.791093]   alloc irq_desc for 29 on node -1
Apr  1 11:33:21 MRFRODO kernel: [    9.791097]   alloc kstat_irqs on node -1
Apr  1 11:33:21 MRFRODO kernel: [    9.791108] i915 0000:00:02.0: irq 29 for MSI/MSI-X
Apr  1 11:33:21 MRFRODO kernel: [    9.791116] [drm] set up 7M of stolen space
Apr  1 11:33:21 MRFRODO kernel: [    9.797639] type=1505 audit(1333260199.808:2):  operation="profile_load" pid=636 name="/sbin/dhclient3"
Apr  1 11:33:21 MRFRODO kernel: [    9.798511] type=1505 audit(1333260199.808:3):  operation="profile_load" pid=636 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Apr  1 11:33:21 MRFRODO kernel: [    9.798992] type=1505 audit(1333260199.808:4):  operation="profile_load" pid=636 name="/usr/lib/connman/scripts/dhclient-script"
Apr  1 11:33:21 MRFRODO kernel: [    9.800814] type=1505 audit(1333260199.808:5):  operation="profile_replace" pid=644 name="/sbin/dhclient3"
Apr  1 11:33:21 MRFRODO kernel: [    9.801719] type=1505 audit(1333260199.812:6):  operation="profile_replace" pid=644 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Apr  1 11:33:21 MRFRODO kernel: [    9.802208] type=1505 audit(1333260199.812:7):  operation="profile_replace" pid=644 name="/usr/lib/connman/scripts/dhclient-script"
Apr  1 11:33:21 MRFRODO kernel: [    9.812060] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
Apr  1 11:33:21 MRFRODO kernel: [    9.812064] iwl3945: Copyright(c) 2003-2009 Intel Corporation
Apr  1 11:33:21 MRFRODO kernel: [    9.812144] iwl3945 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Apr  1 11:33:21 MRFRODO kernel: [    9.812160] iwl3945 0000:04:00.0: setting latency timer to 64
Apr  1 11:33:21 MRFRODO kernel: [    9.935674] iwl3945 0000:04:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
Apr  1 11:33:21 MRFRODO kernel: [    9.935679] iwl3945 0000:04:00.0: Detected Intel Wireless WiFi Link 3945ABG
Apr  1 11:33:21 MRFRODO kernel: [    9.935802]   alloc irq_desc for 30 on node -1
Apr  1 11:33:21 MRFRODO kernel: [    9.935805]   alloc kstat_irqs on node -1
Apr  1 11:33:21 MRFRODO kernel: [    9.935841] iwl3945 0000:04:00.0: irq 30 for MSI/MSI-X
Apr  1 11:33:21 MRFRODO kernel: [    9.959161] [drm] initialized overlay support
Apr  1 11:33:21 MRFRODO kernel: [   10.023200] phy0: Selected rate control algorithm 'iwl-3945-rs'
Apr  1 11:33:21 MRFRODO kernel: [   10.550630] fb0: inteldrmfb frame buffer device
Apr  1 11:33:21 MRFRODO kernel: [   10.550633] registered panic notifier
Apr  1 11:33:21 MRFRODO kernel: [   10.576239] acpi device:07: registered as cooling_device2
Apr  1 11:33:21 MRFRODO kernel: [   10.576530] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input6
Apr  1 11:33:21 MRFRODO kernel: [   10.576578] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Apr  1 11:33:21 MRFRODO kernel: [   10.576611] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Apr  1 11:33:21 MRFRODO kernel: [   10.578707] vga16fb: initializing
Apr  1 11:33:21 MRFRODO kernel: [   10.578711] vga16fb: mapped to 0xc00a0000
Apr  1 11:33:21 MRFRODO kernel: [   10.578715] vga16fb: not registering due to another framebuffer present
Apr  1 11:33:21 MRFRODO kernel: [   10.581169] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Apr  1 11:33:21 MRFRODO kernel: [   10.581204] HDA Intel 0000:00:1b.0: setting latency timer to 64
Apr  1 11:33:21 MRFRODO kernel: [   10.697308] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input7
Apr  1 11:33:21 MRFRODO kernel: [   10.717087] Console: switching to colour frame buffer device 160x50
Apr  1 11:33:21 MRFRODO kernel: [   10.873301] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x25c0b1, caps: 0xa04713/0x200000
Apr  1 11:33:21 MRFRODO kernel: [   10.953295] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
Apr  1 11:33:21 MRFRODO kernel: [   11.098128] EXT4-fs (sda4): mounted filesystem with ordered data mode
Apr  1 11:33:21 MRFRODO kernel: [   11.625543]   alloc irq_desc for 31 on node -1
Apr  1 11:33:21 MRFRODO kernel: [   11.625547]   alloc kstat_irqs on node -1
Apr  1 11:33:21 MRFRODO kernel: [   11.625581] tg3 0000:06:00.0: irq 31 for MSI/MSI-X
Apr  1 11:33:21 MRFRODO kernel: [   11.656468] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr  1 11:33:21 MRFRODO kernel: [   11.706871] type=1505 audit(1333260201.715:8):  operation="profile_load" pid=915 name="/usr/share/gdm/guest-session/Xsession"
Apr  1 11:33:21 MRFRODO kernel: [   11.710868] type=1505 audit(1333260201.719:9):  operation="profile_replace" pid=916 name="/sbin/dhclient3"
Apr  1 11:33:21 MRFRODO kernel: [   11.711760] type=1505 audit(1333260201.719:10):  operation="profile_replace" pid=916 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Apr  1 11:33:21 MRFRODO kernel: [   11.717285] type=1505 audit(1333260201.727:11):  operation="profile_replace" pid=916 name="/usr/lib/connman/scripts/dhclient-script"
Apr  1 11:33:22 MRFRODO kernel: [   11.993290] ppdev: user-space parallel port driver
Apr  1 11:33:22 MRFRODO kernel: [   12.003631] iwl3945 0000:04:00.0: firmware: requesting iwlwifi-3945-2.ucode
Apr  1 11:33:22 MRFRODO kernel: [   12.089321] iwl3945 0000:04:00.0: loaded firmware version 15.32.2.9
Apr  1 11:33:22 MRFRODO kernel: [   12.089497] iwl3945 0000:04:00.0: Radio disabled by HW RF Kill switch
Apr  1 11:33:43 MRFRODO kernel: Kernel logging (proc) stopped.
Apr  1 11:42:18 MRFRODO kernel: imklog 4.2.0, log source = /proc/kmsg started.
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] Initializing cgroup subsys cpuset
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] Initializing cgroup subsys cpu
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] Linux version 2.6.32-21-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 (Ubuntu 2.6.32-21.32-generic 2.6.32.11+drm33.2)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] KERNEL supported cpus:
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]   Intel GenuineIntel
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]   AMD AuthenticAMD
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]   NSC Geode by NSC
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]   Cyrix CyrixInstead
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]   Centaur CentaurHauls
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]   Transmeta GenuineTMx86
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]   Transmeta TransmetaCPU
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]   UMC UMC UMC UMC
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] BIOS-provided physical RAM map:
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003f6d0000 (usable)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]  BIOS-e820: 000000003f6d0000 - 000000003f6e3000 (ACPI NVS)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]  BIOS-e820: 000000003f6e3000 - 0000000040000000 (reserved)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] DMI present.
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] last_pfn = 0x3f6d0 max_arch_pfn = 0x100000
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] MTRR default type: uncachable
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] MTRR fixed ranges enabled:
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]   00000-9FFFF write-back
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]   A0000-BFFFF uncachable
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]   C0000-FFFFF write-protect
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] MTRR variable ranges enabled:
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]   0 base 000000000 mask FC0000000 write-back
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]   1 base 03F700000 mask FFFF00000 uncachable
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]   2 base 03F800000 mask FFF800000 uncachable
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]   3 disabled
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]   4 disabled
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]   5 disabled
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]   6 disabled
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]   7 disabled
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] Scanning 1 areas for low memory corruption
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] modified physical RAM map:
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]  modified: 00000000000d2000 - 00000000000d4000 (reserved)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]  modified: 0000000000100000 - 000000003f6d0000 (usable)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]  modified: 000000003f6d0000 - 000000003f6e3000 (ACPI NVS)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]  modified: 000000003f6e3000 - 0000000040000000 (reserved)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] initial memory mapped : 0 - 00c00000
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]  0000400000 - 0037400000 page 2M
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] RAMDISK: 2f1c4000 - 2f95bad3
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] ACPI: RSDP 000f7240 00024 (v02 LENOVO)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] ACPI: XSDT 3f6d864f 00094 (v01 LENOVO TP-68    06040000  LTP 00000000)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] ACPI: FACP 3f6dfbd2 000F4 (v03 TOSCPL CRESTLNE 06040000 ALAN 00000001)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] ACPI: DSDT 3f6d9b4b 06013 (v02 TOSCPL CRESTLNE 06040000 INTL 20060608)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] ACPI: FACS 3f6e2fc0 00040
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] ACPI: APIC 3f6dfcc6 00068 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] ACPI: HPET 3f6dfd2e 00038 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] ACPI: MCFG 3f6dfd66 0003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] ACPI: TCPA 3f6dfda2 00032 (v01 Intel  CRESTLNE 06040000 LOHR 0000005A)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] ACPI: TMOR 3f6dfdd4 00026 (v01 PTLTD           06040000 PTL  00000003)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] ACPI: SLIX 3f6dfdfa 00176 (v01 LENOVO TP-68    06040000 TBD  00000001)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] ACPI: APIC 3f6dff70 00068 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] ACPI: BOOT 3f6dffd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] ACPI: SSDT 3f6d989e 002AD (v01 SataRe SataAhci 00001000 INTL 20050624)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] ACPI: SSDT 3f6d97fb 000A3 (v01 BrtRef  DD01BRT 00001000 INTL 20050624)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] ACPI: SSDT 3f6d8c6f 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] ACPI: SSDT 3f6d8bc9 000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20050624)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] ACPI: SSDT 3f6d86e3 004E6 (v01  PmRef    CpuPm 00003000 INTL 20050624)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify [email]linux-acpi@vger.kernel.org[/email]
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] 126MB HIGHMEM available.
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] 887MB LOWMEM available.
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]   low ram: 0 - 377fe000
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]   node 0 low ram: 00000000 - 377fe000
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]   node 0 bootmap 00008000 - 0000ef00
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]   #3 [0000100000 - 00008d9e98]    TEXT DATA BSS ==> [0000100000 - 00008d9e98]
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]   #4 [002f1c4000 - 002f95bad3]          RAMDISK ==> [002f1c4000 - 002f95bad3]
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]   #5 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]   #6 [00008da000 - 00008dd198]              BRK ==> [00008da000 - 00008dd198]
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] found SMP MP-table at [c00f72c0] f72c0
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] Zone PFN ranges:
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]   HighMem  0x000377fe -> 0x0003f6d0
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] Movable zone start PFN for each node
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] early_node_map[3] active PFN ranges
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]     0: 0x00000000 -> 0x00000002
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]     0: 0x00000006 -> 0x0000009f
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]     0: 0x00000100 -> 0x0003f6d0
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] On node 0 totalpages: 259691
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] free_area_init_node: node 0, pgdat c0798720, node_mem_map c1001000
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]   DMA zone: 0 pages reserved
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]   DMA zone: 3963 pages, LIFO batch:0
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]   Normal zone: 221486 pages, LIFO batch:31
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]   HighMem zone: 254 pages used for memmap
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]   HighMem zone: 32212 pages, LIFO batch:7
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] Using APIC driver default
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)

---

### Post by sagar_aarya on 2012-04-01
**contd....**

Apr  1 11:42:18 MRFRODO kernel: [    0.000000] ACPI: IRQ0 used by override.
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] ACPI: IRQ2 used by override.
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] ACPI: IRQ9 used by override.
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] nr_irqs_gsi: 24
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000dc000
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:a0000000)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36024 r0 d21320 u2097152
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] pcpu-alloc: s36024 r0 d21320 u2097152 alloc=1*4194304
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] pcpu-alloc: [0] 0 1 
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257661
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=3feab3eb-2b6a-4043-a49c-763525893dbf ro quiet splash
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] Enabling fast FPU save and restore... done.
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] Initializing CPU#0
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] allocated 5195840 bytes of page_cgroup
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0003f6d0)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] Memory: 1008272k/1039168k available (4673k kernel code, 29992k reserved, 2122k data, 656k init, 129864k highmem)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] virtual kernel memory layout:
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]       .init : 0xc07a3000 - 0xc0847000   ( 656 kB)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]       .data : 0xc0590613 - 0xc07a2e48   (2122 kB)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000]       .text : 0xc0100000 - 0xc0590613   (4673 kB)
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] Hierarchical RCU implementation.
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] NR_IRQS:2304 nr_irqs:424
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] Extended CMOS year: 2000
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] Console: colour VGA+ 80x25
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] console [tty0] enabled
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] hpet clockevent registered
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] Fast TSC calibration using PIT
Apr  1 11:42:18 MRFRODO kernel: [    0.000000] Detected 1662.547 MHz processor.
Apr  1 11:42:18 MRFRODO kernel: [    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 3325.09 BogoMIPS (lpj=6650188)
Apr  1 11:42:18 MRFRODO kernel: [    0.004023] Security Framework initialized
Apr  1 11:42:18 MRFRODO kernel: [    0.004041] AppArmor: AppArmor initialized
Apr  1 11:42:18 MRFRODO kernel: [    0.004048] Mount-cache hash table entries: 512
Apr  1 11:42:18 MRFRODO kernel: [    0.004173] Initializing cgroup subsys ns
Apr  1 11:42:18 MRFRODO kernel: [    0.004178] Initializing cgroup subsys cpuacct
Apr  1 11:42:18 MRFRODO kernel: [    0.004183] Initializing cgroup subsys memory
Apr  1 11:42:18 MRFRODO kernel: [    0.004191] Initializing cgroup subsys devices
Apr  1 11:42:18 MRFRODO kernel: [    0.004194] Initializing cgroup subsys freezer
Apr  1 11:42:18 MRFRODO kernel: [    0.004197] Initializing cgroup subsys net_cls
Apr  1 11:42:18 MRFRODO kernel: [    0.004218] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr  1 11:42:18 MRFRODO kernel: [    0.004222] CPU: L2 cache: 2048K
Apr  1 11:42:18 MRFRODO kernel: [    0.004225] CPU: Physical Processor ID: 0
Apr  1 11:42:18 MRFRODO kernel: [    0.004227] CPU: Processor Core ID: 0
Apr  1 11:42:18 MRFRODO kernel: [    0.004233] mce: CPU supports 6 MCE banks
Apr  1 11:42:18 MRFRODO kernel: [    0.004241] CPU0: Thermal monitoring handled by SMI
Apr  1 11:42:18 MRFRODO kernel: [    0.004245] using mwait in idle threads.
Apr  1 11:42:18 MRFRODO kernel: [    0.004250] Performance Events: Core2 events, Intel PMU driver.
Apr  1 11:42:18 MRFRODO kernel: [    0.004260] ... version:                2
Apr  1 11:42:18 MRFRODO kernel: [    0.004263] ... bit width:              40
Apr  1 11:42:18 MRFRODO kernel: [    0.004265] ... generic registers:      2
Apr  1 11:42:18 MRFRODO kernel: [    0.004267] ... value mask:             000000ffffffffff
Apr  1 11:42:18 MRFRODO kernel: [    0.004269] ... max period:             000000007fffffff
Apr  1 11:42:18 MRFRODO kernel: [    0.004272] ... fixed-purpose events:   3
Apr  1 11:42:18 MRFRODO kernel: [    0.004274] ... event mask:             0000000700000003
Apr  1 11:42:18 MRFRODO kernel: [    0.004278] Checking 'hlt' instruction... OK.
Apr  1 11:42:18 MRFRODO kernel: [    0.023188] ACPI: Core revision 20090903
Apr  1 11:42:18 MRFRODO kernel: [    0.036027] ftrace: converting mcount calls to 0f 1f 44 00 00
Apr  1 11:42:18 MRFRODO kernel: [    0.036037] ftrace: allocating 21771 entries in 43 pages
Apr  1 11:42:18 MRFRODO kernel: [    0.044069] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr  1 11:42:18 MRFRODO kernel: [    0.044451] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr  1 11:42:18 MRFRODO kernel: [    0.087762] CPU0: Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz stepping 0d
Apr  1 11:42:18 MRFRODO kernel: [    0.088001] Booting processor 1 APIC 0x1 ip 0x6000
Apr  1 11:42:18 MRFRODO kernel: [    0.008000] Initializing CPU#1
Apr  1 11:42:18 MRFRODO kernel: [    0.008000] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr  1 11:42:18 MRFRODO kernel: [    0.008000] CPU: L2 cache: 2048K
Apr  1 11:42:18 MRFRODO kernel: [    0.008000] CPU: Physical Processor ID: 0
Apr  1 11:42:18 MRFRODO kernel: [    0.008000] CPU: Processor Core ID: 1
Apr  1 11:42:18 MRFRODO kernel: [    0.008000] CPU1: Thermal monitoring handled by SMI
Apr  1 11:42:18 MRFRODO kernel: [    0.172073] CPU1: Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz stepping 0d
Apr  1 11:42:18 MRFRODO kernel: [    0.172088] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Apr  1 11:42:18 MRFRODO kernel: [    0.176020] Brought up 2 CPUs
Apr  1 11:42:18 MRFRODO kernel: [    0.176023] Total of 2 processors activated (6650.10 BogoMIPS).
Apr  1 11:42:18 MRFRODO kernel: [    0.176553] CPU0 attaching sched-domain:
Apr  1 11:42:18 MRFRODO kernel: [    0.176557]  domain 0: span 0-1 level MC
Apr  1 11:42:18 MRFRODO kernel: [    0.176560]   groups: 0 1
Apr  1 11:42:18 MRFRODO kernel: [    0.176568] CPU1 attaching sched-domain:
Apr  1 11:42:18 MRFRODO kernel: [    0.176570]  domain 0: span 0-1 level MC
Apr  1 11:42:18 MRFRODO kernel: [    0.176573]   groups: 1 0
Apr  1 11:42:18 MRFRODO kernel: [    0.176686] devtmpfs: initialized
Apr  1 11:42:18 MRFRODO kernel: [    0.176686] regulator: core version 0.5
Apr  1 11:42:18 MRFRODO kernel: [    0.176686] Time:  6:04:08  Date: 04/01/12
Apr  1 11:42:18 MRFRODO kernel: [    0.176686] NET: Registered protocol family 16
Apr  1 11:42:18 MRFRODO kernel: [    0.176686] Trying to unpack rootfs image as initramfs...
Apr  1 11:42:18 MRFRODO kernel: [    0.176686] EISA bus registered
Apr  1 11:42:18 MRFRODO kernel: [    0.176686] ACPI: bus type pci registered
Apr  1 11:42:18 MRFRODO kernel: [    0.176686] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Apr  1 11:42:18 MRFRODO kernel: [    0.176686] PCI: MCFG area at e0000000 reserved in E820
Apr  1 11:42:18 MRFRODO kernel: [    0.176686] PCI: Using MMCONFIG for extended config space
Apr  1 11:42:18 MRFRODO kernel: [    0.176686] PCI: Using configuration type 1 for base access
Apr  1 11:42:18 MRFRODO kernel: [    0.180118] bio: create slab <bio-0> at 0
Apr  1 11:42:18 MRFRODO kernel: [    0.181411] ACPI: EC: Look up EC in DSDT
Apr  1 11:42:18 MRFRODO kernel: [    0.188110] ACPI: BIOS _OSI(Linux) query ignored
Apr  1 11:42:18 MRFRODO kernel: [    0.204041] ACPI: EC: GPE storm detected, transactions will use polling mode
Apr  1 11:42:18 MRFRODO kernel: [    0.240122] ACPI: Interpreter enabled
Apr  1 11:42:18 MRFRODO kernel: [    0.240131] ACPI: (supports S0 S3 S4 S5)
Apr  1 11:42:18 MRFRODO kernel: [    0.240161] ACPI: Using IOAPIC for interrupt routing
Apr  1 11:42:18 MRFRODO kernel: [    0.304866] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
Apr  1 11:42:18 MRFRODO kernel: [    0.305264] ACPI: No dock devices found.
Apr  1 11:42:18 MRFRODO kernel: [    0.305988] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr  1 11:42:18 MRFRODO kernel: [    0.306106] pci 0000:00:02.0: reg 10 64bit mmio: [0xfc000000-0xfc0fffff]
Apr  1 11:42:18 MRFRODO kernel: [    0.306116] pci 0000:00:02.0: reg 18 64bit mmio pref: [0xd0000000-0xdfffffff]
Apr  1 11:42:18 MRFRODO kernel: [    0.306123] pci 0000:00:02.0: reg 20 io port: [0x1800-0x1807]
Apr  1 11:42:18 MRFRODO kernel: [    0.306177] pci 0000:00:02.1: reg 10 64bit mmio: [0xfc100000-0xfc1fffff]
Apr  1 11:42:18 MRFRODO kernel: [    0.306315] pci 0000:00:1a.0: reg 20 io port: [0x1820-0x183f]
Apr  1 11:42:18 MRFRODO kernel: [    0.306394] pci 0000:00:1a.1: reg 20 io port: [0x1840-0x185f]
Apr  1 11:42:18 MRFRODO kernel: [    0.306480] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfc504800-0xfc504bff]
Apr  1 11:42:18 MRFRODO kernel: [    0.306558] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
Apr  1 11:42:18 MRFRODO kernel: [    0.306565] pci 0000:00:1a.7: PME# disabled
Apr  1 11:42:18 MRFRODO kernel: [    0.306631] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfc300000-0xfc303fff]
Apr  1 11:42:18 MRFRODO kernel: [    0.306705] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Apr  1 11:42:18 MRFRODO kernel: [    0.306711] pci 0000:00:1b.0: PME# disabled
Apr  1 11:42:18 MRFRODO kernel: [    0.306828] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Apr  1 11:42:18 MRFRODO kernel: [    0.306834] pci 0000:00:1c.0: PME# disabled
Apr  1 11:42:18 MRFRODO kernel: [    0.306950] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Apr  1 11:42:18 MRFRODO kernel: [    0.306956] pci 0000:00:1c.1: PME# disabled
Apr  1 11:42:18 MRFRODO kernel: [    0.307073] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Apr  1 11:42:18 MRFRODO kernel: [    0.307079] pci 0000:00:1c.2: PME# disabled
Apr  1 11:42:18 MRFRODO kernel: [    0.307197] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Apr  1 11:42:18 MRFRODO kernel: [    0.307203] pci 0000:00:1c.3: PME# disabled
Apr  1 11:42:18 MRFRODO kernel: [    0.307285] pci 0000:00:1d.0: reg 20 io port: [0x1860-0x187f]
Apr  1 11:42:18 MRFRODO kernel: [    0.307362] pci 0000:00:1d.1: reg 20 io port: [0x1880-0x189f]
Apr  1 11:42:18 MRFRODO kernel: [    0.307442] pci 0000:00:1d.2: reg 20 io port: [0x18a0-0x18bf]
Apr  1 11:42:18 MRFRODO kernel: [    0.307527] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfc504c00-0xfc504fff]
Apr  1 11:42:18 MRFRODO kernel: [    0.307603] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Apr  1 11:42:18 MRFRODO kernel: [    0.307609] pci 0000:00:1d.7: PME# disabled
Apr  1 11:42:18 MRFRODO kernel: [    0.307817] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Apr  1 11:42:18 MRFRODO kernel: [    0.307822] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
Apr  1 11:42:18 MRFRODO kernel: [    0.307828] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0680 (mask 007f)
Apr  1 11:42:18 MRFRODO kernel: [    0.307833] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 1640 (mask 000f)
Apr  1 11:42:18 MRFRODO kernel: [    0.307900] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
Apr  1 11:42:18 MRFRODO kernel: [    0.307910] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
Apr  1 11:42:18 MRFRODO kernel: [    0.307920] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
Apr  1 11:42:18 MRFRODO kernel: [    0.307929] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
Apr  1 11:42:18 MRFRODO kernel: [    0.307939] pci 0000:00:1f.1: reg 20 io port: [0x1810-0x181f]
Apr  1 11:42:18 MRFRODO kernel: [    0.308038] pci 0000:00:1f.2: reg 10 io port: [0x1c00-0x1c07]
Apr  1 11:42:18 MRFRODO kernel: [    0.308048] pci 0000:00:1f.2: reg 14 io port: [0x18d4-0x18d7]
Apr  1 11:42:18 MRFRODO kernel: [    0.308058] pci 0000:00:1f.2: reg 18 io port: [0x18d8-0x18df]
Apr  1 11:42:18 MRFRODO kernel: [    0.308068] pci 0000:00:1f.2: reg 1c io port: [0x18d0-0x18d3]
Apr  1 11:42:18 MRFRODO kernel: [    0.308078] pci 0000:00:1f.2: reg 20 io port: [0x18e0-0x18ff]
Apr  1 11:42:18 MRFRODO kernel: [    0.308088] pci 0000:00:1f.2: reg 24 32bit mmio: [0xfc504000-0xfc5047ff]
Apr  1 11:42:18 MRFRODO kernel: [    0.308140] pci 0000:00:1f.2: PME# supported from D3hot
Apr  1 11:42:18 MRFRODO kernel: [    0.308146] pci 0000:00:1f.2: PME# disabled
Apr  1 11:42:18 MRFRODO kernel: [    0.308187] pci 0000:00:1f.3: reg 10 32bit mmio: [0x000000-0x0000ff]
Apr  1 11:42:18 MRFRODO kernel: [    0.308217] pci 0000:00:1f.3: reg 20 io port: [0x1c20-0x1c3f]
Apr  1 11:42:18 MRFRODO kernel: [    0.308324] pci 0000:00:1c.0: bridge io port: [0x2000-0x2fff]
Apr  1 11:42:18 MRFRODO kernel: [    0.308331] pci 0000:00:1c.0: bridge 32bit mmio: [0xf6000000-0xf7ffffff]
Apr  1 11:42:18 MRFRODO kernel: [    0.308341] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xf0000000-0xf1ffffff]
Apr  1 11:42:18 MRFRODO kernel: [    0.308498] pci 0000:04:00.0: reg 10 32bit mmio: [0xf8000000-0xf8000fff]
Apr  1 11:42:18 MRFRODO kernel: [    0.308757] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
Apr  1 11:42:18 MRFRODO kernel: [    0.308771] pci 0000:04:00.0: PME# disabled
Apr  1 11:42:18 MRFRODO kernel: [    0.308901] pci 0000:00:1c.1: bridge io port: [0x3000-0x3fff]
Apr  1 11:42:18 MRFRODO kernel: [    0.308907] pci 0000:00:1c.1: bridge 32bit mmio: [0xf8000000-0xf9ffffff]
Apr  1 11:42:18 MRFRODO kernel: [    0.308917] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xf2000000-0xf3ffffff]
Apr  1 11:42:18 MRFRODO kernel: [    0.308991] pci 0000:00:1c.2: bridge io port: [0x4000-0x4fff]
Apr  1 11:42:18 MRFRODO kernel: [    0.308998] pci 0000:00:1c.2: bridge 32bit mmio: [0xfa000000-0xfbffffff]
Apr  1 11:42:18 MRFRODO kernel: [    0.309008] pci 0000:00:1c.2: bridge 64bit mmio pref: [0xf4000000-0xf5ffffff]
Apr  1 11:42:18 MRFRODO kernel: [    0.309208] pci 0000:06:00.0: reg 10 64bit mmio: [0xc8000000-0xc800ffff]
Apr  1 11:42:18 MRFRODO kernel: [    0.309459] pci 0000:06:00.0: PME# supported from D3hot D3cold
Apr  1 11:42:18 MRFRODO kernel: [    0.309472] pci 0000:06:00.0: PME# disabled
Apr  1 11:42:18 MRFRODO kernel: [    0.309590] pci 0000:00:1c.3: bridge io port: [0x5000-0x5fff]
Apr  1 11:42:18 MRFRODO kernel: [    0.309596] pci 0000:00:1c.3: bridge 32bit mmio: [0xc8000000-0xc9ffffff]
Apr  1 11:42:18 MRFRODO kernel: [    0.309606] pci 0000:00:1c.3: bridge 64bit mmio pref: [0xcc000000-0xcdffffff]
Apr  1 11:42:18 MRFRODO kernel: [    0.309672] pci 0000:08:06.0: reg 10 32bit mmio: [0xfc200000-0xfc2007ff]
Apr  1 11:42:18 MRFRODO kernel: [    0.309744] pci 0000:08:06.0: supports D1 D2
Apr  1 11:42:18 MRFRODO kernel: [    0.309747] pci 0000:08:06.0: PME# supported from D0 D1 D2 D3hot D3cold
Apr  1 11:42:18 MRFRODO kernel: [    0.309753] pci 0000:08:06.0: PME# disabled
Apr  1 11:42:18 MRFRODO kernel: [    0.309804] pci 0000:08:06.1: reg 10 32bit mmio: [0xfc200800-0xfc2008ff]
Apr  1 11:42:18 MRFRODO kernel: [    0.309879] pci 0000:08:06.1: supports D1 D2
Apr  1 11:42:18 MRFRODO kernel: [    0.309882] pci 0000:08:06.1: PME# supported from D0 D1 D2 D3hot D3cold
Apr  1 11:42:18 MRFRODO kernel: [    0.309889] pci 0000:08:06.1: PME# disabled
Apr  1 11:42:18 MRFRODO kernel: [    0.309941] pci 0000:08:06.2: reg 10 32bit mmio: [0xfc200c00-0xfc200cff]
Apr  1 11:42:18 MRFRODO kernel: [    0.310013] pci 0000:08:06.2: supports D1 D2
Apr  1 11:42:18 MRFRODO kernel: [    0.310015] pci 0000:08:06.2: PME# supported from D0 D1 D2 D3hot D3cold
Apr  1 11:42:18 MRFRODO kernel: [    0.310021] pci 0000:08:06.2: PME# disabled
Apr  1 11:42:18 MRFRODO kernel: [    0.310073] pci 0000:08:06.3: reg 10 32bit mmio: [0xfc201000-0xfc2010ff]
Apr  1 11:42:18 MRFRODO kernel: [    0.310143] pci 0000:08:06.3: supports D1 D2
Apr  1 11:42:18 MRFRODO kernel: [    0.310145] pci 0000:08:06.3: PME# supported from D0 D1 D2 D3hot D3cold
Apr  1 11:42:18 MRFRODO kernel: [    0.310152] pci 0000:08:06.3: PME# disabled
Apr  1 11:42:18 MRFRODO kernel: [    0.310226] pci 0000:00:1e.0: transparent bridge
Apr  1 11:42:18 MRFRODO kernel: [    0.310235] pci 0000:00:1e.0: bridge 32bit mmio: [0xfc200000-0xfc2fffff]
Apr  1 11:42:18 MRFRODO kernel: [    0.310281] pci_bus 0000:00: on NUMA node 0
Apr  1 11:42:18 MRFRODO kernel: [    0.310287] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Apr  1 11:42:18 MRFRODO kernel: [    0.310525] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Apr  1 11:42:18 MRFRODO kernel: [    0.310617] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
Apr  1 11:42:18 MRFRODO kernel: [    0.310708] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
Apr  1 11:42:18 MRFRODO kernel: [    0.310798] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
Apr  1 11:42:18 MRFRODO kernel: [    0.310932] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
Apr  1 11:42:18 MRFRODO kernel: [    0.325044] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
Apr  1 11:42:18 MRFRODO kernel: [    0.325171] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Apr  1 11:42:18 MRFRODO kernel: [    0.325295] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *7 10 12 14 15)
Apr  1 11:42:18 MRFRODO kernel: [    0.325421] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Apr  1 11:42:18 MRFRODO kernel: [    0.325543] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
Apr  1 11:42:18 MRFRODO kernel: [    0.325665] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Apr  1 11:42:18 MRFRODO kernel: [    0.325790] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
Apr  1 11:42:18 MRFRODO kernel: [    0.325911] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
Apr  1 11:42:18 MRFRODO kernel: [    0.326054] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Apr  1 11:42:18 MRFRODO kernel: [    0.326078] vgaarb: loaded
Apr  1 11:42:18 MRFRODO kernel: [    0.326224] SCSI subsystem initialized
Apr  1 11:42:18 MRFRODO kernel: [    0.326351] libata version 3.00 loaded.
Apr  1 11:42:18 MRFRODO kernel: [    0.326444] usbcore: registered new interface driver usbfs
Apr  1 11:42:18 MRFRODO kernel: [    0.326461] usbcore: registered new interface driver hub
Apr  1 11:42:18 MRFRODO kernel: [    0.326493] usbcore: registered new device driver usb
Apr  1 11:42:18 MRFRODO kernel: [    0.326690] ACPI: WMI: Mapper loaded
Apr  1 11:42:18 MRFRODO kernel: [    0.326693] PCI: Using ACPI for IRQ routing
Apr  1 11:42:18 MRFRODO kernel: [    0.326959] NetLabel: Initializing
Apr  1 11:42:18 MRFRODO kernel: [    0.326961] NetLabel:  domain hash size = 128
Apr  1 11:42:18 MRFRODO kernel: [    0.326963] NetLabel:  protocols = UNLABELED CIPSOv4
Apr  1 11:42:18 MRFRODO kernel: [    0.326980] NetLabel:  unlabeled traffic allowed by default
Apr  1 11:42:18 MRFRODO kernel: [    0.327021] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Apr  1 11:42:18 MRFRODO kernel: [    0.327028] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Apr  1 11:42:18 MRFRODO kernel: [    0.332039] Switching to clocksource tsc
Apr  1 11:42:18 MRFRODO kernel: [    0.334598] AppArmor: AppArmor Filesystem Enabled
Apr  1 11:42:18 MRFRODO kernel: [    0.334615] pnp: PnP ACPI init
Apr  1 11:42:18 MRFRODO kernel: [    0.334632] ACPI: bus type pnp registered
Apr  1 11:42:18 MRFRODO kernel: [    0.355737] pnp: PnP ACPI: found 10 devices
Apr  1 11:42:18 MRFRODO kernel: [    0.355740] ACPI: ACPI bus type pnp unregistered
Apr  1 11:42:18 MRFRODO kernel: [    0.355746] PnPBIOS: Disabled by ACPI PNP
Apr  1 11:42:18 MRFRODO kernel: [    0.355763] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
Apr  1 11:42:18 MRFRODO kernel: [    0.355767] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
Apr  1 11:42:18 MRFRODO kernel: [    0.355771] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
Apr  1 11:42:18 MRFRODO kernel: [    0.355775] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
Apr  1 11:42:18 MRFRODO kernel: [    0.355779] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
Apr  1 11:42:18 MRFRODO kernel: [    0.355782] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
Apr  1 11:42:18 MRFRODO kernel: [    0.355786] system 00:01: iomem range 0xfed40000-0xfed44fff has been reserved
Apr  1 11:42:18 MRFRODO kernel: [    0.355790] system 00:01: iomem range 0xfed45000-0xfed8ffff has been reserved
Apr  1 11:42:18 MRFRODO kernel: [    0.355799] system 00:04: iomem range 0xfed00000-0xfed003ff has been reserved
Apr  1 11:42:18 MRFRODO kernel: [    0.355809] system 00:06: ioport range 0x680-0x69f has been reserved
Apr  1 11:42:18 MRFRODO kernel: [    0.355813] system 00:06: ioport range 0x800-0x80f has been reserved
Apr  1 11:42:18 MRFRODO kernel: [    0.355817] system 00:06: ioport range 0x1000-0x107f has been reserved
Apr  1 11:42:18 MRFRODO kernel: [    0.355820] system 00:06: ioport range 0x1180-0x11bf has been reserved
Apr  1 11:42:18 MRFRODO kernel: [    0.355826] system 00:06: ioport range 0xfe00-0xfe00 has been reserved
Apr  1 11:42:18 MRFRODO kernel: [    0.355829] system 00:06: ioport range 0xff00-0xff7f has been reserved
Apr  1 11:42:18 MRFRODO kernel: [    0.390671] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
Apr  1 11:42:18 MRFRODO kernel: [    0.390677] pci 0000:00:1c.0:   IO window: 0x2000-0x2fff
Apr  1 11:42:18 MRFRODO kernel: [    0.390686] pci 0000:00:1c.0:   MEM window: 0xf6000000-0xf7ffffff
Apr  1 11:42:18 MRFRODO kernel: [    0.390692] pci 0000:00:1c.0:   PREFETCH window: 0x000000f0000000-0x000000f1ffffff
Apr  1 11:42:18 MRFRODO kernel: [    0.390703] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:04
Apr  1 11:42:18 MRFRODO kernel: [    0.390707] pci 0000:00:1c.1:   IO window: 0x3000-0x3fff
Apr  1 11:42:18 MRFRODO kernel: [    0.390715] pci 0000:00:1c.1:   MEM window: 0xf8000000-0xf9ffffff
Apr  1 11:42:18 MRFRODO kernel: [    0.390721] pci 0000:00:1c.1:   PREFETCH window: 0x000000f2000000-0x000000f3ffffff
Apr  1 11:42:18 MRFRODO kernel: [    0.390731] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:05
Apr  1 11:42:18 MRFRODO kernel: [    0.390736] pci 0000:00:1c.2:   IO window: 0x4000-0x4fff
Apr  1 11:42:18 MRFRODO kernel: [    0.390744] pci 0000:00:1c.2:   MEM window: 0xfa000000-0xfbffffff
Apr  1 11:42:18 MRFRODO kernel: [    0.390750] pci 0000:00:1c.2:   PREFETCH window: 0x000000f4000000-0x000000f5ffffff
Apr  1 11:42:18 MRFRODO kernel: [    0.390760] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:06
Apr  1 11:42:18 MRFRODO kernel: [    0.390765] pci 0000:00:1c.3:   IO window: 0x5000-0x5fff
Apr  1 11:42:18 MRFRODO kernel: [    0.390773] pci 0000:00:1c.3:   MEM window: 0xc8000000-0xc9ffffff
Apr  1 11:42:18 MRFRODO kernel: [    0.390779] pci 0000:00:1c.3:   PREFETCH window: 0x000000cc000000-0x000000cdffffff
Apr  1 11:42:18 MRFRODO kernel: [    0.390789] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:08
Apr  1 11:42:18 MRFRODO kernel: [    0.390792] pci 0000:00:1e.0:   IO window: disabled
Apr  1 11:42:18 MRFRODO kernel: [    0.390800] pci 0000:00:1e.0:   MEM window: 0xfc200000-0xfc2fffff
Apr  1 11:42:18 MRFRODO kernel: [    0.390806] pci 0000:00:1e.0:   PREFETCH window: disabled
Apr  1 11:42:18 MRFRODO kernel: [    0.390835]   alloc irq_desc for 17 on node -1
Apr  1 11:42:18 MRFRODO kernel: [    0.390838]   alloc kstat_irqs on node -1
Apr  1 11:42:18 MRFRODO kernel: [    0.390847] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Apr  1 11:42:18 MRFRODO kernel: [    0.390855] pci 0000:00:1c.0: setting latency timer to 64
Apr  1 11:42:18 MRFRODO kernel: [    0.390867]   alloc irq_desc for 16 on node -1
Apr  1 11:42:18 MRFRODO kernel: [    0.390869]   alloc kstat_irqs on node -1
Apr  1 11:42:18 MRFRODO kernel: [    0.390874] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Apr  1 11:42:18 MRFRODO kernel: [    0.390881] pci 0000:00:1c.1: setting latency timer to 64
Apr  1 11:42:18 MRFRODO kernel: [    0.390893]   alloc irq_desc for 18 on node -1
Apr  1 11:42:18 MRFRODO kernel: [    0.390895]   alloc kstat_irqs on node -1
Apr  1 11:42:18 MRFRODO kernel: [    0.390900] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Apr  1 11:42:18 MRFRODO kernel: [    0.390907] pci 0000:00:1c.2: setting latency timer to 64
Apr  1 11:42:18 MRFRODO kernel: [    0.390919]   alloc irq_desc for 19 on node -1
Apr  1 11:42:18 MRFRODO kernel: [    0.390921]   alloc kstat_irqs on node -1
Apr  1 11:42:18 MRFRODO kernel: [    0.390926] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Apr  1 11:42:18 MRFRODO kernel: [    0.390932] pci 0000:00:1c.3: setting latency timer to 64
Apr  1 11:42:18 MRFRODO kernel: [    0.390943] pci 0000:00:1e.0: setting latency timer to 64
Apr  1 11:42:18 MRFRODO kernel: [    0.390949] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Apr  1 11:42:18 MRFRODO kernel: [    0.390953] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
Apr  1 11:42:18 MRFRODO kernel: [    0.390956] pci_bus 0000:02: resource 0 io:  [0x2000-0x2fff]
Apr  1 11:42:18 MRFRODO kernel: [    0.390960] pci_bus 0000:02: resource 1 mem: [0xf6000000-0xf7ffffff]
Apr  1 11:42:18 MRFRODO kernel: [    0.390963] pci_bus 0000:02: resource 2 pref mem [0xf0000000-0xf1ffffff]
Apr  1 11:42:18 MRFRODO kernel: [    0.390966] pci_bus 0000:04: resource 0 io:  [0x3000-0x3fff]
Apr  1 11:42:18 MRFRODO kernel: [    0.390970] pci_bus 0000:04: resource 1 mem: [0xf8000000-0xf9ffffff]
Apr  1 11:42:18 MRFRODO kernel: [    0.390973] pci_bus 0000:04: resource 2 pref mem [0xf2000000-0xf3ffffff]
Apr  1 11:42:18 MRFRODO kernel: [    0.390976] pci_bus 0000:05: resource 0 io:  [0x4000-0x4fff]
Apr  1 11:42:18 MRFRODO kernel: [    0.390980] pci_bus 0000:05: resource 1 mem: [0xfa000000-0xfbffffff]
Apr  1 11:42:18 MRFRODO kernel: [    0.390983] pci_bus 0000:05: resource 2 pref mem [0xf4000000-0xf5ffffff]
Apr  1 11:42:18 MRFRODO kernel: [    0.390986] pci_bus 0000:06: resource 0 io:  [0x5000-0x5fff]
Apr  1 11:42:18 MRFRODO kernel: [    0.390989] pci_bus 0000:06: resource 1 mem: [0xc8000000-0xc9ffffff]
Apr  1 11:42:18 MRFRODO kernel: [    0.390992] pci_bus 0000:06: resource 2 pref mem [0xcc000000-0xcdffffff]
Apr  1 11:42:18 MRFRODO kernel: [    0.390996] pci_bus 0000:08: resource 1 mem: [0xfc200000-0xfc2fffff]
Apr  1 11:42:18 MRFRODO kernel: [    0.390999] pci_bus 0000:08: resource 3 io:  [0x00-0xffff]
Apr  1 11:42:18 MRFRODO kernel: [    0.391002] pci_bus 0000:08: resource 4 mem: [0x000000-0xffffffff]
Apr  1 11:42:18 MRFRODO kernel: [    0.391051] NET: Registered protocol family 2
Apr  1 11:42:18 MRFRODO kernel: [    0.391184] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr  1 11:42:18 MRFRODO kernel: [    0.391622] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Apr  1 11:42:18 MRFRODO kernel: [    0.392200] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Apr  1 11:42:18 MRFRODO kernel: [    0.392500] TCP: Hash tables configured (established 131072 bind 65536)
Apr  1 11:42:18 MRFRODO kernel: [    0.392503] TCP reno registered
Apr  1 11:42:18 MRFRODO kernel: [    0.392616] NET: Registered protocol family 1
Apr  1 11:42:18 MRFRODO kernel: [    0.392652] pci 0000:00:02.0: Boot video device
Apr  1 11:42:18 MRFRODO kernel: [    0.392843] Simple Boot Flag at 0x36 set to 0x1
Apr  1 11:42:18 MRFRODO kernel: [    0.393067] cpufreq-nforce2: No nForce2 chipset.
Apr  1 11:42:18 MRFRODO kernel: [    0.393103] Scanning for low memory corruption every 60 seconds
Apr  1 11:42:18 MRFRODO kernel: [    0.393253] audit: initializing netlink socket (disabled)
Apr  1 11:42:18 MRFRODO kernel: [    0.393266] type=2000 audit(1333260248.391:1): initialized
Apr  1 11:42:18 MRFRODO kernel: [    0.405318] highmem bounce pool size: 64 pages
Apr  1 11:42:18 MRFRODO kernel: [    0.405325] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Apr  1 11:42:18 MRFRODO kernel: [    0.407221] VFS: Disk quotas dquot_6.5.2
Apr  1 11:42:18 MRFRODO kernel: [    0.407297] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr  1 11:42:18 MRFRODO kernel: [    0.408015] fuse init (API version 7.13)
Apr  1 11:42:18 MRFRODO kernel: [    0.408120] msgmni has been set to 1716
Apr  1 11:42:18 MRFRODO kernel: [    0.408376] alg: No test for stdrng (krng)
Apr  1 11:42:18 MRFRODO kernel: [    0.408440] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Apr  1 11:42:18 MRFRODO kernel: [    0.408444] io scheduler noop registered
Apr  1 11:42:18 MRFRODO kernel: [    0.408446] io scheduler anticipatory registered
Apr  1 11:42:18 MRFRODO kernel: [    0.408449] io scheduler deadline registered
Apr  1 11:42:18 MRFRODO kernel: [    0.408495] io scheduler cfq registered (default)
Apr  1 11:42:18 MRFRODO kernel: [    0.408718]   alloc irq_desc for 24 on node -1
Apr  1 11:42:18 MRFRODO kernel: [    0.408721]   alloc kstat_irqs on node -1
Apr  1 11:42:18 MRFRODO kernel: [    0.408734] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
Apr  1 11:42:18 MRFRODO kernel: [    0.408748] pcieport 0000:00:1c.0: setting latency timer to 64
Apr  1 11:42:18 MRFRODO kernel: [    0.408932]   alloc irq_desc for 25 on node -1
Apr  1 11:42:18 MRFRODO kernel: [    0.408935]   alloc kstat_irqs on node -1
Apr  1 11:42:18 MRFRODO kernel: [    0.408946] pcieport 0000:00:1c.1: irq 25 for MSI/MSI-X
Apr  1 11:42:18 MRFRODO kernel: [    0.408959] pcieport 0000:00:1c.1: setting latency timer to 64
Apr  1 11:42:18 MRFRODO kernel: [    0.409140]   alloc irq_desc for 26 on node -1
Apr  1 11:42:18 MRFRODO kernel: [    0.409142]   alloc kstat_irqs on node -1
Apr  1 11:42:18 MRFRODO kernel: [    0.409153] pcieport 0000:00:1c.2: irq 26 for MSI/MSI-X
Apr  1 11:42:18 MRFRODO kernel: [    0.409166] pcieport 0000:00:1c.2: setting latency timer to 64
Apr  1 11:42:18 MRFRODO kernel: [    0.409345]   alloc irq_desc for 27 on node -1
Apr  1 11:42:18 MRFRODO kernel: [    0.409348]   alloc kstat_irqs on node -1
Apr  1 11:42:18 MRFRODO kernel: [    0.409358] pcieport 0000:00:1c.3: irq 27 for MSI/MSI-X
Apr  1 11:42:18 MRFRODO kernel: [    0.409371] pcieport 0000:00:1c.3: setting latency timer to 64
Apr  1 11:42:18 MRFRODO kernel: [    0.409499] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr  1 11:42:18 MRFRODO kernel: [    0.409654] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Apr  1 11:42:18 MRFRODO kernel: [    0.409812] ACPI: AC Adapter [ACAD] (on-line)
Apr  1 11:42:18 MRFRODO kernel: [    0.409886] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
Apr  1 11:42:18 MRFRODO kernel: [    0.409932] ACPI: Lid Switch [LID0]
Apr  1 11:42:18 MRFRODO kernel: [    0.409985] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
Apr  1 11:42:18 MRFRODO kernel: [    0.409988] ACPI: Power Button [PWRB]
Apr  1 11:42:18 MRFRODO kernel: [    0.410064] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Apr  1 11:42:18 MRFRODO kernel: [    0.410067] ACPI: Power Button [PWRF]


*****END *****

---

### Post by sagar_aarya on 2012-04-03
somebody help mee....

---

### Post by HiImTye on 2012-04-03
I completely forgot about this one

I dont see any issues in your kernel log there, maybe paste the output of
```
cat /var/log/apt/term.log
```

so we can see if there were any packaging errors

please use code tags this time (and maybe use them on your previous posts). highlight the output and click on the '#' above where you type here (for past posts, click on 'Go Advanced' first)

---

### Post by NikTh on 2012-04-03
Hello , if you want paste also 
```
ls -la /
```
maybe its a permissions problem . 
Thanks

---

### Post by sagar_aarya on 2012-04-11
> **HiImTye said:**
> I completely forgot about this one

I dont see any issues in your kernel log there, maybe paste the output of
```
cat /var/log/apt/term.log
```

so we can see if there were any packaging errors

please use code tags this time (and maybe use them on your previous posts). highlight the output and click on the '#' above where you type here (for past posts, click on 'Go Advanced' first)


this is what i am getting...

[B]sagar@MRFRODO:~$ sudo cat /var/log/apt/term.log
sagar@MRFRODO:~$[/B]

---

### Post by sagar_aarya on 2012-04-11
> **NikTh said:**
> Hello , if you want paste also 
```
ls -la /
```
maybe its a permissions problem . 
Thanks

[B]attached a file with it
[/B]

---

### Post by sagar_aarya on 2012-04-12
???
???
:confused::confused::confused::confused::confused:

---

