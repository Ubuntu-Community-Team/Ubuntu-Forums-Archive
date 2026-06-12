---
title: "Lockup issues"
date: 2021-05-24
forum: New to Ubuntu
---

### Post by dbemowsk on 2021-05-24
So I am new to Ubuntu 20.04 migrating from being a long time Fedora user.  I recently bought a new computer with the following specs.


HP Z2 G4 Workstation Tower - 9th Gen Intel Core i7-9700 Upto 4.70 GHz - 32GB RAM, 1TB NVMe SSD – 2GB Quadro P620 4K 4-Monitor Support, Mini DisplayPort running 3 monitors.

The OS seems to run okay, but I am a multitasker that has a lot of things going on at the same time.  I do 3D printing, so I will sometimes have my Cura window open showing video of the webcam I have monitoring the print job running.  At the same time I may be on facebook or youtube watching a video in Chrome Version 90.0.4430.212.  Sometimes the video will start getting choppy and the machine will begin to go unresponsive to the point where I cannot hit CTRL+ALT+F(1-6) to get to a shell prompt.  It gets to the point where my only option is to hit CTRL+ALT+DEL which will then reboot the computer.  I thought that it might have something to do with running the nouveaux display driver, so I attempted to switch to the recommended NVIDIA driver (nvidia-driver-460).  That made things even worse.  When I would boot the machine after that it would boot to  a login prompt on one monitor, the other two monitors would get no signal and go into powersave mode,  On the one monitor showing the login screen, I could move the mouse for maybe 3 seconds at most before the machine would completely lock up and be completely unresponsive.  From there I had to get creative with my Ubuntu live USB drive to mount the drive and get myself back to the nouveaux driver, and I'd be back to the point I am at now. The only time it seems to get wonky and unresponsive is if I am plaing videos in Chrome, but it's not like it does it every time I play a video.  It seems kinda random.  If I am just doing general work, it seems to work fine.

I am at a loss at the moment for what I can try to fix this.  I would like to get to a point where I can use one of the NVIDIA drivers, but I am a bit hesitant to try any of the other driver options that it shows as available of which there are 6 other than the nouveaux.

Any help with this is greatly appreciated.  If you need more information, let me know and I'll do my best to get whatever you need.

TIA

---

### Post by TheFu on 2021-05-25
Which Ubuntu release?
What kernel?
How was the nvidia driver installed?  

The correct answers are:
```

lsb_release -a
uname -r
sudo ubuntu-drivers autoinstall
```

Don't go hunting for nvidia drivers on the web. Use the approved versions that can be auto-installed.
Rather than using chrome, perhaps chromium will work better?  It hasn't crashed here in some time, once I figured out how to deal with the snap (I don't use snaps).  I'm on nvidia proprietary drivers for a GT 1030 GPU.

My setup from the important parts:```

$ lsb_release -a
  Description:    Ubuntu 18.04.5 LTS
$ uname -r
  5.4.0-73-generic

$ lspci -vk |perl -lne 'print if /VGA|3d/i .. /^[\w]*$/'
        Subsystem: eVga.com. Corp. GP108 [GeForce GT 1030]
        Kernel driver in use: **nvidia**
        Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia
$ dpkg -l nvidia-kern*
ii  nvidia-kernel-common-460            **460.73.01-0ubuntu0.18.** amd64                  Shared files used with the kernel module
```

Depending on your GPU, a different driver might be installed.  Ensure only one, matching, version of all the tools is installed. Sometimes old versions of nvidia stuff is left behind.

---

### Post by dbemowsk on 2021-05-27
```
$ lsb_release -aNo LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 20.04.2 LTS
Release:	20.04
Codename:	focal
```

```
$ uname -r
5.8.0-53-generic
```


```
$ lspci -vk |perl -lne 'print if /VGA|3d/i .. /^[\w]*$/'
01:00.0 VGA compatible controller: NVIDIA Corporation GP107GL [Quadro P620] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company GP107GL [Quadro P620]
	Flags: bus master, fast devsel, latency 0, IRQ 134
	Memory at e2000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at e0000000 (64-bit, prefetchable) [size=32M]
	I/O ports at 3000 [size=128]
	Expansion ROM at e3080000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nouveau
	Kernel modules: nvidiafb, nouveau
```

```
$ dpkg -l nvidia-kern*
dpkg-query: no packages found matching nvidia-kern*
```

```
$ sudo lspci -vk |perl -lne 'print if /VGA|3d/i .. /^[\w]*$/'
[sudo] password for dbemowsk: 
01:00.0 VGA compatible controller: NVIDIA Corporation GP107GL [Quadro P620] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company GP107GL [Quadro P620]
	Flags: bus master, fast devsel, latency 0, IRQ 134
	Memory at e2000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at e0000000 (64-bit, prefetchable) [size=32M]
	I/O ports at 3000 [size=128]
	Expansion ROM at e3080000 [disabled] [size=512K]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [78] Express Legacy Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [250] Latency Tolerance Reporting
	Capabilities: [128] Power Budgeting <?>
	Capabilities: [420] Advanced Error Reporting
	Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
	Capabilities: [900] Secondary PCI Express
	Kernel driver in use: nouveau
	Kernel modules: nvidiafb, nouveau
```

---

### Post by TheFu on 2021-05-27
So, what we know from those commands:
Ubuntu 20.04.2 running the HWE kernel. Nouveau video drivers.
GPU is an older Nvidia Quadro P620, which is supported by 
Version: 	460.80
Release Date: 	2021.5.11 
 [https://www.nvidia.com/Download/driverResults.aspx/175203/en-us](https://www.nvidia.com/Download/driverResults.aspx/175203/en-us)

Did you run **sudo ubuntu-drivers autoinstall**?
That command should install the driver you need.

---

### Post by tea for one on 2021-05-27
I am also curious whether the OP has installed the nvidia driver.

---

### Post by dbemowsk on 2021-05-27
> **TheFu said:**
> So, what we know from those commands:
Ubuntu 20.04.2 running the HWE kernel. Nouveau video drivers.
GPU is an older Nvidia Quadro P620, which is supported by 
Version:     460.80
Release Date:     2021.5.11 
 [https://www.nvidia.com/Download/driverResults.aspx/175203/en-us](https://www.nvidia.com/Download/driverResults.aspx/175203/en-us)

Did you run **sudo ubuntu-drivers autoinstall**?
That command should install the driver you need.

I did not run the autoinstall. I did the install from Settings > Additional Drivers and selected the "nvidia-driver-460 (proprietary, tested)" which from some reading on other forums should be the "Recommended" driver.  I can certainly try the autoinstall, but if you read my original post, look for where I said "[COLOR=#000000]so I attempted to switch to the recommended NVIDIA driver (nvidia-driver-460). That made things even worse."  I am wondering if doing the autoinstall will do the same thing.  Could it be a problem with the video card?[/COLOR]

---

### Post by dbemowsk on 2021-05-27
> **tea for one said:**
> I am also curious whether the OP has installed the nvidia driver.

If you read through the entire original post, you will see that I did install the nvidia-driver-460 which was the recommended driver (proprietary, tested) under Additional Drivers in the Settings menu.  That only caused the machine to display the login window on one of the 3 screens (the right most screen) and seconds after showing the login window the machine locs up to the point of having to boot to the live CD, mount the hard drive and using chroot to switch to that mount point and reverting back to the nuveau driver from there.

---

### Post by tea for one on 2021-05-28
> **dbemowsk said:**
> If you read through the entire original post, you will see that I did install the nvidia-driver-460 which was the recommended driver (proprietary, tested) under Additional Drivers in the Settings menu.

Apologies, I missed that detail in your original post.

Does the proprietary driver work OK with just one monitor attached?

---

### Post by TheFu on 2021-05-28
> **dbemowsk said:**
> I did not run the autoinstall. I did the install from Settings > Additional Drivers and selected the "nvidia-driver-460 (proprietary, tested)" which from some reading on other forums should be the "Recommended" driver.  I can certainly try the autoinstall, but if you read my original post, look for where I said "[COLOR=#000000]so I attempted to switch to the recommended NVIDIA driver (nvidia-driver-460). That made things even worse."  I am wondering if doing the autoinstall will do the same thing.  Could it be a problem with the video card?[/COLOR]

Could be anything. 

There appears to be a solution here: [https://forums.developer.nvidia.com/t/version-460-nvidia-driver-stopped-loading-overnight-under-ubuntu-20-04/175374/4](https://forums.developer.nvidia.com/t/version-460-nvidia-driver-stopped-loading-overnight-under-ubuntu-20-04/175374/4)  Looks like a PPA is needed and the kernel headers.

If that doesn't work, can you drop back from the 20.04 HWE kernel (5.8.x) to the original kernel line?   That would be 5.4.0-73-generic today.  Are there any warnings about nvidia drivers and the newer kernels?  Just some ideas for testing.

I'm using that driver with a 18.04 HWE kernel (5.4.x) and it is working fine.  
```
$ uptime 
 07:55:47 up 12 days, 21:09,  4 users,  load average: 11.26, 6.47, 4.46
```

Seems the 5.8.x kernels are missing dependencies that nvidia was depending on.

---

### Post by dbemowsk on 2021-05-29
> **tea for one said:**
> Apologies, I missed that detail in your original post.

Does the proprietary driver work OK with just one monitor attached?
I did not try disconecting the other two monitors, but I suspect that that is not going to fix the lockup issue.

---

### Post by dbemowsk on 2021-05-29
> **TheFu said:**
> Could be anything. 

There appears to be a solution here: [https://forums.developer.nvidia.com/t/version-460-nvidia-driver-stopped-loading-overnight-under-ubuntu-20-04/175374/4](https://forums.developer.nvidia.com/t/version-460-nvidia-driver-stopped-loading-overnight-under-ubuntu-20-04/175374/4)  Looks like a PPA is needed and the kernel headers.

If that doesn't work, can you drop back from the 20.04 HWE kernel (5.8.x) to the original kernel line?   That would be 5.4.0-73-generic today.  Are there any warnings about nvidia drivers and the newer kernels?  Just some ideas for testing.

I'm using that driver with a 18.04 HWE kernel (5.4.x) and it is working fine.  
```
$ uptime 
 07:55:47 up 12 days, 21:09,  4 users,  load average: 11.26, 6.47, 4.46
```

Seems the 5.8.x kernels are missing dependencies that nvidia was depending on.
You say that it looks like a PPA is needed. He was only using a package archive because he temporarily switched to an older kernel version (still 4.8, but just a different patch numbe, 49 vs 50) and needed that archive to get the 460 driver built for that kernel.  At least that's the way I understood that.

---

### Post by dbemowsk on 2021-05-31
So I think I finally got this.

$ dpkg -l nvidia-kern*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                     Version                    Architecture Description
+++-========================-==========================-============-========================================
un  nvidia-kernel-common     <none>                     <none>       (no description available)
ii  nvidia-kernel-common-460 460.73.01-0ubuntu0.20.04.1 amd64        Shared files used with the kernel module
un  nvidia-kernel-source     <none>                     <none>       (no description available)
ii  nvidia-kernel-source-460 460.73.01-0ubuntu0.20.04.1 amd64        NVIDIA kernel source package

---

