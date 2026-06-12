---
title: "Boot problems after installing Nvidia drivers"
date: 2018-11-02
forum: New to Ubuntu
---

### Post by npull on 2018-11-02
Hello :)

I have a ASUS Zenbook ux32vd with dual graphic cards. The integrated Intel graphics and a Nvidia Geforce 620M card.

I am trying to install the Nvidia driver so I can switch between them. I tried both via the ubuntu "software and updates" app and via the terminal with few different nvidia versions ```
sudo apt-get install nvidia-340 nvidia-prime
``` all have the same result, during bootup the screen turns on and off in an endless loop. I mange to revert it by purging the driver in recovery mode.

Here is some info about my system:

```

ps -efly | grep Xorg


S niklas    2976  2974  4  80   0 75584 94520 ep_pol 12:19 tty2     00:00:34 /usr/lib/xorg/Xorg vt2 -displayfd 3 -auth /run/user/1000/gdm/Xauthority -background none -noreset -keeptty -verbose 3
S niklas    4561  4537  0  80   0  1004  6074 pipe_w 12:33 pts/0    00:00:00 grep --color=auto Xorg

echo $XDG_SESSION_TYPE
x11


```

```

cat /var/log/gpu-manager.log


log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-nvidia-was-loaded file
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for nvidia modules in /lib/modules/4.15.0-38-generic/updates/dkms
Looking for amdgpu modules in /lib/modules/4.15.0-38-generic/updates/dkms
Is nvidia loaded? no
Was nvidia unloaded? no
Is nvidia blacklisted? yes
Is intel loaded? yes
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is amdgpu versioned? no
Is amdgpu pro stack? no
Is nouveau loaded? yes
Is nouveau blacklisted? no
Is nvidia kernel module available? no
Is amdgpu kernel module available? no
Vendor/Device Id: 8086:166
BusID "PCI:0@0:2:0"
Is boot vga? yes
Vendor/Device Id: 10de:1140
BusID "PCI:1@0:0:0"
Is boot vga? no
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card1", driven by "nouveau"
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card1", driven by "nouveau"
Skipping "/dev/dri/card0", driven by "i915"
Found "/dev/dri/card1", driven by "nouveau"
Number of connected outputs for /dev/dri/card1: 0
Found "/dev/dri/card0", driven by "i915"
output 0:
    card0-eDP-1
Number of connected outputs for /dev/dri/card0: 1
Does it require offloading? yes
last cards number = 2
Has amd? no
Has intel? yes
Has nvidia? yes
How many cards? 2
Has the system changed? No
Intel IGP detected
Desktop system detected
or laptop with open drivers
Nothing to do


```

```

dpkg -l | grep -i nvidia

rc  libnvidia-compute-390:amd64                390.87-0ubuntu0~gpu18.04.1                  amd64        NVIDIA libcompute package
rc  libnvidia-compute-390:i386                 390.87-0ubuntu0~gpu18.04.1                  i386         NVIDIA libcompute package

```

---

### Post by oldfred on 2018-11-02
If you have installed more than one nVidia driver, have you purged before installing another. Otherwise you get conflicts and nothing works.
Installing too old of a driver often will not work.
       Updated driver search by nVidia model, do not download, just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers) 
    And older cards/chips may get a fixed/frozen version of driver, that only gets security updates. New features to support newer chips are not required, so older driver is then correct.
       Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html) 

Shows your model but older versions of Ubuntu:
[https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime)

       Asus Zenbook Prime UX31A (UEFI)  Blank screen resolved by turning secure boot off, many tests of Boot parameters
[http://ubuntuforums.org/showthread.php?t=2086054](http://ubuntuforums.org/showthread.php?t=2086054)

---

### Post by npull on 2018-11-15
I have got it installed on this computer corectly in the pased on ubuntu 14.04, probably 4-5 years ago (in between I've been running windows without any linux boot for a few years) so it should not be a sofrware problem somehow. I did try a few more times to install this driver, reinstalled my ubuntu 3 times, 2 times after not being able to boot anymore after installing the driver. I've given up on this now, way to much effort for little gain, and I wont be needing the extra GPU power when running ubuntu anyways. So thanks for the effort of trying to help me, but I wont care to continue this endevour anymore.

---

