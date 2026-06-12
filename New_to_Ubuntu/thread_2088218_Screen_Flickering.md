---
title: "Screen Flickering"
date: 2012-11-25
forum: New to Ubuntu
---

### Post by yunesj on 2012-11-25
I just upgraded to 12.04.1. Once I get to the login screen, there is severe flickering.

I've followed the advice suggested in [http://ubuntuforums.org/showthread.php?t=2061180](http://ubuntuforums.org/showthread.php?t=2061180) and other threads, but I haven't had any luck.

Here is the output of those informational commands (run via SSH).

```

jeff@remotehost:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
jeff@remotehost:~$ uname -a  
Linux remotehost 3.2.0-33-generic #52-Ubuntu SMP Thu Oct 18 16:29:15 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
jeff@remotehost:~$ lspci -nnk | grep -iA2 vga 
0f:00.0 VGA compatible controller [0300]: NVIDIA Corporation G98 [Quadro NVS 295] [10de:06fd] (rev a1)
    Subsystem: NVIDIA Corporation Device [10de:062e]
    Kernel driver in use: nvidia
jeff@remotehost:~$ env | grep DESK
jeff@remotehost:~$ 

```If you have any suggestions, I'd greatly appreciate it.

Thanks!
-Jeff

---

### Post by daslinkard on 2012-11-25
By chance have you reset your Unity?  You can do so by the following command
```

unity --reset
```

---

### Post by yunesj on 2012-11-25
> **daslinkard said:**
> By chance have you reset your Unity?  You can do so by the following command
```

unity --reset
```

Yes, I have. Here's what I get. Although, I'm not sure if I only ran it remotely, or I ran it locally in text mode.

```

jeff@remotehost:~$ unity --reset
WARNING: no DISPLAY variable set, setting it to :0

(process:2860): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
//bin/dbus-launch terminated abnormally with the following error: No protocol specified
No protocol specified
Autolaunch error: X11 initialization failed.

WARNING: environment is incorrect: No D-BUS daemon running

Did you just try to reset in a tty?
unity-panel-service: no process found
No protocol specified
No protocol specified
compiz (core) - Fatal: Couldn't open display :0

```

---

### Post by daslinkard on 2012-11-25
What is the output of the following command:

```
 lspci
```

---

### Post by yunesj on 2012-11-25
> **daslinkard said:**
> What is the output of the following command:

```
 lspci
```

```

jeff@ucsf2-90-19:~$ lspci
00:00.0 Host bridge: Intel Corporation 5520 I/O Hub to ESI Port (rev 13)
00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 13)
00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 13)
00:07.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 (rev 13)
00:10.0 PIC: Intel Corporation 5520/5500/X58 Physical and Link Layer Registers Port 0 (rev 13)
00:10.1 PIC: Intel Corporation 5520/5500/X58 Routing and Protocol Layer Registers Port 0 (rev 13)
00:11.0 PIC: Intel Corporation 5520/5500 Physical and Link Layer Registers Port 1 (rev 13)
00:11.1 PIC: Intel Corporation 5520/5500 Routing & Protocol Layer Register Port 1 (rev 13)
00:14.0 PIC: Intel Corporation 5520/5500/X58 I/O Hub System Management Registers (rev 13)
00:14.1 PIC: Intel Corporation 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 13)
00:14.2 PIC: Intel Corporation 5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 13)
00:15.0 PIC: Intel Corporation 5520/5500/X58 Trusted Execution Technology Registers (rev 13)
00:1a.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6
00:1d.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA Controller [RAID mode]
01:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe (rev 10)
0f:00.0 VGA compatible controller: NVIDIA Corporation G98 [Quadro NVS 295] (rev a1)
3e:00.0 Host bridge: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture Generic Non-Core Registers (rev 05)
3e:00.1 Host bridge: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture System Address Decoder (rev 05)
3e:02.0 Host bridge: Intel Corporation Xeon 5500/Core i7 QPI Link 0 (rev 05)
3e:02.1 Host bridge: Intel Corporation Xeon 5500/Core i7 QPI Physical 0 (rev 05)
3e:02.4 Host bridge: Intel Corporation Xeon 5500/Core i7 QPI Link 1 (rev 05)
3e:02.5 Host bridge: Intel Corporation Xeon 5500/Core i7 QPI Physical 1 (rev 05)
3e:03.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller (rev 05)
3e:03.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Target Address Decoder (rev 05)
3e:03.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller RAS Registers (rev 05)
3e:03.4 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Test Registers (rev 05)
3e:04.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Control Registers (rev 05)
3e:04.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Address Registers (rev 05)
3e:04.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Rank Registers (rev 05)
3e:04.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Thermal Control Registers (rev 05)
3e:05.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Control Registers (rev 05)
3e:05.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Address Registers (rev 05)
3e:05.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Rank Registers (rev 05)
3e:05.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Thermal Control Registers (rev 05)
3e:06.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Control Registers (rev 05)
3e:06.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Address Registers (rev 05)
3e:06.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Rank Registers (rev 05)
3e:06.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Thermal Control Registers (rev 05)
3f:00.0 Host bridge: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture Generic Non-Core Registers (rev 05)
3f:00.1 Host bridge: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture System Address Decoder (rev 05)
3f:02.0 Host bridge: Intel Corporation Xeon 5500/Core i7 QPI Link 0 (rev 05)
3f:02.1 Host bridge: Intel Corporation Xeon 5500/Core i7 QPI Physical 0 (rev 05)
3f:02.4 Host bridge: Intel Corporation Xeon 5500/Core i7 QPI Link 1 (rev 05)
3f:02.5 Host bridge: Intel Corporation Xeon 5500/Core i7 QPI Physical 1 (rev 05)
3f:03.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller (rev 05)
3f:03.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Target Address Decoder (rev 05)
3f:03.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller RAS Registers (rev 05)
3f:03.4 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Test Registers (rev 05)
3f:04.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Control Registers (rev 05)
3f:04.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Address Registers (rev 05)
3f:04.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Rank Registers (rev 05)
3f:04.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Thermal Control Registers (rev 05)
3f:05.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Control Registers (rev 05)
3f:05.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Address Registers (rev 05)
3f:05.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Rank Registers (rev 05)
3f:05.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Thermal Control Registers (rev 05)
3f:06.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Control Registers (rev 05)
3f:06.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Address Registers (rev 05)
3f:06.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Rank Registers (rev 05)
3f:06.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Thermal Control Registers (rev 05)


```

Thanks for your help!
-Jeff

---

### Post by daslinkard on 2012-11-25
See what happens when you run the following command:

```
sudo apt-get install --yes nvidia-current
```

Then after this run

```
sudo nvidia-xconfig
```

Followed by rebooting your system....see if this gives you some good luck...

---

### Post by yunesj on 2012-11-25
> **daslinkard said:**
> See what happens when you run the following command:

```
sudo apt-get install --yes nvidia-current
```Then after this run

```
sudo nvidia-xconfig
```Followed by rebooting your system....see if this gives you some good luck...

I did that too. I got
```

nvidia-current is already the newest version.

```and restarting didn't help.

However, my ```
 jockey-text 
``` looks different:
```

root@remotehost:/var/log# jockey-text -l
kmod:nvidia_current - nvidia_current (Proprietary, Enabled, Not in use)
kmod:nvidia_current_updates - NVIDIA binary Xorg driver, kernel module and VDPAU library (Proprietary, Disabled, Not in use)

```Although I don't seem to be able to enable kmod:nvidia_current (and I'm pretty sure it was another type besides kmod before I upgraded).

Thanks!

---

### Post by yunesj on 2012-11-26
I think I might have found it, but I won't know until tomorrow.

The logs have the message:
```

NVRM: API mismatch: the client has the version 295.40, but this kernel module has the version 304.43.  Please make sure that this kernel module and all NVIDIA driver components have the same version.
gdm-binary[19526]: WARNING: GdmDisplay: display lasted 0.042921 seconds

```Searching for that message, I found that I just had to
```

apt-get purge nvidia*

```I'll follow-up tomorrow morning.

Thanks!

---

### Post by yunesj on 2012-11-26
Unbelievable! There's been no improvement. I still have exactly the same problem.

I don't see any errors, warnings, or other concerns in any of the logs (syslog, xorg, jockey).

Thoughts?

---

### Post by yunesj on 2012-11-26
I removed the nvidia drivers and switched xorg.conf to use nouveau.

```

0f:00.0 VGA compatible controller [0300]: NVIDIA Corporation G98 [Quadro NVS 295] [10de:06fd] (rev a1)
    Subsystem: NVIDIA Corporation Device [10de:062e]
    Kernel driver in use: nouveau

```

Still no luck. It's not flickering per se, but it still displays a corrupted screen of some sort.

---

### Post by yunesj on 2012-11-26
> **yunesj said:**
> I removed the nvidia drivers and switched xorg.conf to use nouveau.

```

0f:00.0 VGA compatible controller [0300]: NVIDIA Corporation G98 [Quadro NVS 295] [10de:06fd] (rev a1)
    Subsystem: NVIDIA Corporation Device [10de:062e]
    Kernel driver in use: nouveau

```Still no luck. It's not flickering per se, but it still displays a corrupted screen of some sort.

Following another restart, the display worked with the nouveau drivers. I tried re-enabling the nvidia drivers via the graphical UI. It caused a text only OS on restart, so I ran nvida-xconf and restarted. Unfortunately, the flickering resumed.

---

### Post by monkeybrain2012 on 2012-11-26
The Nvidia driver is buggy in 12.04, try to install the one from xorg-edgers ppa.

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

Add the ppa and upgrade everything.

But before you do this, install ppa-purge, in case anything goes wrong, purge the ppa. See instructions on the xorg-edgers page.

I am using nouveau in 12.04 (upgraded via xorg-edgers), it is smooth and fast and considerably less buggy. I am not a gamer but I can watch 1080p with high frame rate without lags with just nouveau.

---

### Post by BicyclerBoy on 2012-11-26
Some users have found that manually installing the linux-headers package allows the std distro nvidia packages to work okay..

sudo apt-get install linux-headers-generic


The ppa versions of the nVidia driver require version matched kernel headers because it has to build an open source kernel interface, then it inserts a kernel module with dkms.

---

### Post by yunesj on 2012-11-26
Thank you all for your assistance.

I ran the following commands:
```

add-apt-repository ppa:xorg-edgers/ppa
apt-get update
apt-get install linux-headers-generic
apt-get dist-upgrade
nvidia-xconfig

```On restart, I got the following errors in Xorg.0.log:
```

   21.092] (II) NVIDIA(GPU-0): Display (Lenovo Group Limited LEN D221 Wide (DFP-1)) does not
[    21.093] (II) NVIDIA(GPU-0):     support NVIDIA 3D Vision stereo.
[    21.093] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    21.093] (**) NVIDIA(0):     device Lenovo Group Limited LEN D221 Wide (DFP-1) (Using
[    21.093] (**) NVIDIA(0):     EDID frequencies has been enabled on all display
[    21.093] (**) NVIDIA(0):     devices.)
[    25.231] (EE) NVIDIA(0): Failed to initialize DMA.
[    25.231] (EE) NVIDIA(0):  *** Aborting ***
[    25.231] (EE) NVIDIA(0): Error recovery failed.
[    25.231] (EE) NVIDIA(0):  *** Aborting ***

```The monitor displayed a pleasant checkerboard pattern for a while before turning off.

Thanks!
-Jeff

---

### Post by BicyclerBoy on 2012-11-26
I would have done those things one at a time with a logout/login or a reboot just to know where the problems started..
And I would have just tried the headers & nvidia driver activate first..

Reboot and run
sudo nvidia-xconfig

The nvidia driver has kernel module that may or may not be magically loaded by dkms (without reboot)..

---

