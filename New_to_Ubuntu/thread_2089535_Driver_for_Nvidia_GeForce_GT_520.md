---
title: "Driver for Nvidia GeForce GT 520"
date: 2012-11-29
forum: New to Ubuntu
---

### Post by Versacesl on 2012-11-29
Hello. I know there are alot insue's about that but can't find them and solve the problem. I swiched to Ubuntu 2 day's ago and install normal things like skype, playonlinux,wine(last version) and alot more. However majorly im a gamer and playing World of warcraft. With some tip's i installed corectly and everything was fine till i start the game. The i saw the ultra low fps in game so i check the info and realise i got wrong version or different video driver and my Video Card is(GeForce GT 520) 1GB DDR3. so when i start search for tip's from almost every ubuntu user websites/forums. i did alot i can say i get some expirience with that already but however. When i install or set up the nvidia driver and reboot there is only show up the desktop wallpaper. First i thinked i fked up the system (sorry for my word) but after that back in starting position with>  /system settings/Softwere sources/additional drivers and back privious driver. Then start to search how to fix the problem and in the end i come here. I try everything and still im stuck on this. So problem is how to connect nvidia drivers (last version) with ubuntu 12.10 and how to fix the problem with kernel sources which are > (Module build for the currently running kernel was skipped since the kernel source for this kernel does not seem to be installed.) That is coming from terminal after installing the nvidia drivers (nvidia-current) also from different ways. So after that when i type > $ sudo nvidia-settings come's that error 

> --- "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the X server. " --- If there is any good solution please help.

---

### Post by TheFu on 2012-11-29
Congratulations on your switch.  A few comments from an old-timer.
* Newer graphics drivers are not always better in Linux.  Do not get drivers directly from nvidia unless you are looking for pain. Stay with the drivers released from Canonical and the software repositories.
* Gaming on Linux will be a challenge for non-native games. You will be fighting an uphill battle if gaming is your main reason for computing.  Perhaps a dual-boot setup would make more sense for those times when you wish to game?
* Here's an old link (I don't run latest Ubuntu releases) that explains setting up nvidia drivers. [http://blog.jdpfu.com/2010/05/12/ubuntu-10-04-dual-monitor-with-nvidia-driver](http://blog.jdpfu.com/2010/05/12/ubuntu-10-04-dual-monitor-with-nvidia-driver)  Just be certain that you avoid specifying the exact driver version when installing and choose "stable" versions instead.

Rebooting may not be useful - this isn't Windows. You can probably just logout and log back in.  There are many, many, many forum posts about this type of issue. Chances are your issue is not 12.10 specific.

---

### Post by bogan on 2012-11-29
Hi!", **Versacesl,**

This is probably because the necessary kernel files did not get properly installed, there have been a lot of similar reports with 12.10.

Edit2: I also run a GT 520, and it runs well with nvidia-current, nvidia-updates and nvidie-experimental-304, as wellas with the Nvidia downloaded latest drivers, so it should not matter which version you choose.

Run the following and report results, - whether it says ' present  xxx installed is already the latest version', or actually installs them.```
 sudo apt-get update
sudo apt-get -f install --fix-missing
sudo apt-get install build-essential
sudo apt-get install linux-headers-generic
sudo apt-get remove --purge nvidia-current
sudo apt-get remove --purge nvidia-settings
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
sudo reboot
```Then run nvidia-settings.

Edit, after reading 'TheFU's Post: the Link he gave is way out of date and would not work with currently available drivers, xorgservers  and kernels.

Chao!,** bogan**.

---

### Post by Versacesl on 2012-11-29
Hello guy's thank's for reply's but follow the tip's and im still on same problem. Nothing work here about (driver's and kernel).

So maybe i must make dual boot with Ubuntu and Win7 which is a bit unlike but maybe is a solution till Ubuntu dev fix the issue's of that kind. So for game's maybe is not good yet but for everything else Ubuntu is better than microsoft softwere.

Thank's again and regards : Versavesl

---

### Post by galaxys on 2012-11-29
I am experiencing a similar problem it sounds like... Same graphics card too. I also ran through each of those steps with no luck..

---

### Post by bogan on 2012-11-29
Hi!, **versacesl & galaxys,**

1. Are you running a Wubi install?

2. What CPU do you have? Is it Integrated graphics as well as  the GT520?

3. Is nouveau running? or is it blacklisted in /etc/modprobe.d ?
4. Please Post:```
 lspci -nnk | grep -iA3 vga
/usr/lib/nux/unity_support_test -p
apt-cache policy nvidia-current
```Chao!, **bogan**.

---

### Post by galaxys on 2012-11-29
1. Yes, its Wubi installation; dual booted with Windows 8
2. Alienware M11xR3
*-display        
       description: VGA compatible controller
       product: GF108 [GeForce GT 540M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:d0000000-d0ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:6000(size=12:cool: memory:d1000000-d107ffff
  *-display
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:50 memory:d1400000-d17fffff memory:c0000000-cfffffff ioport:7000(size=64)

3. Not sure how to check for #3....

4. Here is what showed up with those commands

 lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
    Subsystem: Dell Device [1028:04c8]
    Kernel driver in use: i915
    Kernel modules: i915
--
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF108 [GeForce GT 540M] [10de:0df4] (rev a1)
    Subsystem: Dell Device [1028:04c8]
    Kernel driver in use: nvidia
    Kernel modules: nvidia_current, nouveau, nvidiafb
bobsalienware@ubuntu:~$ /usr/lib/nux/unity_support_test -p
Xlib:  extension "GLX" missing on display ":0".
Error: GLX is not available on the system
bobsalienware@ubuntu:~$ apt-cache policy nvidia-current
nvidia-current:
  Installed: 304.51.really.304.43-0ubuntu1
  Candidate: 304.51.really.304.43-0ubuntu1
  Version table:
 *** 304.51.really.304.43-0ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/restricted amd64 Packages
        100 /var/lib/dpkg/status


thanks for the help

---

### Post by bogan on 2012-11-30
Hi!,** galaxys**,

Right, that is pretty clear what the problem is:

You do have Intel HD3000 Integrated graphics running the i915 driver, as well as nvidia GT 540M running nvidia-current 304.

Two video cards like that conflict, and you need Bumblebee or to go into BIOS and choose which to use, according to your purpose. unfortunately I am no expert on that, but there are many threads from which you can get details.

Additionally, it appears that nouveau is running as well as nvidia, and they conflict as well.

When you run nvidia-settings does it show that the nvidia driver is in use or not?, lspci says it is, but there is no GLX available, presumably because of the conflicts.

Chao!, **bogan**.

---

