---
title: "Just a few small issues"
date: 2015-06-02
forum: New to Ubuntu
---

### Post by Reid_Huff on 2015-06-02
I have been using Ubuntu on my laptop for a few months and I decided to take the leap and install it on my desktop. I only have two issues. First of all my USB 3.0 ports do not do anything. The computer does not see them at all. Secondly the animations are sometimes laggy when minimizing and maximizing. Does anybody have any solutions to these problems?

---

### Post by kerry_s on 2015-06-02
specs, make, model, version ? something more than it don't work always helps.

---

### Post by Reid_Huff on 2015-06-02
I was hoping somebody would tell me how to compile a list with terminal. ;)

AMD FX 8320 8-core
XFX R9 290
64 bit
8 gigs of ram 
14.04 LTS

---

### Post by v3.xx on 2015-06-02
> **Reid_Huff said:**
> I was hoping somebody would tell me how to compile a list with terminal. ;)
```
sudo apt-get install inxi && inxi -b
```

---

### Post by Reid_Huff on 2015-06-02
```
Kernel: 3.16.0-38-generic x86_64 (64 bit) 
Desktop: Gnome Distro: Ubuntu 14.04 trusty
Mobo: Gigabyte model: 990FXA-UD3 
Bios: American Megatrends version: F2 date: 07/15/2013
CPU: Octa core AMD FX-8320 Eight-Core (-MCP-) clocked at 2300.00 MHz 
Graphics Card: Advanced Micro Devices [AMD/ATI] Hawaii PRO [Radeon R9 290] 
           X.Org: 1.16.0 drivers: ati,radeon (unloaded: fbdev,vesa) Resolution: 1920x1080@60.0hz 
           GLX Renderer: Gallium 0.4 on llvmpipe (LLVM 3.5, 128 bits) GLX Version: 3.0 Mesa 10.3.2
Network:   Card-1: Qualcomm Atheros AR9287 Wireless Network Adapter (PCI-Express) driver: ath9k 
           Card-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169 
Drives:    HDD Total Size: 3000.6GB (31.1% used)
Info:      Processes: 285 Uptime: 1:10 Memory: 2785.9/7949.5MB Client: Shell (bash) inxi: 1.9.17
```

---

### Post by slickymaster on 2015-06-02
> **v3.xx said:**
> ```
sudo apt-get install inxi && inxi -b
```
+1 on using inxi for what you want. It is a full featured system information script that will detect information about hardware specifications, including but not limited to vendor details, CPU info, graphic and sound cards.

 Here's a cheat sheet for its most common use:

[LIST=1]
[*]_System information_
[LIST]
[*]**inxi -b** » will output basic system information
[*]**inxi -F** » will output full system information
[/LIST]

[*]_Hard drive details_
[LIST]
[*]	**inxi -D** » will output information on your hard drives, like make, model and size
[/LIST]

[*]_Hard drive partitions_
[LIST]
[*]**inxi -p** » will output information about all mounted partitions, mount points and space usage
[/LIST]

[*]_Networking_
[LIST]
[*]	**inxi -n** and **inxi -ni** » will output information about the details of the network interfaces and configuration. When the i option is used with n, inxi will output IP address details (for both WAN and LAN).
[/LIST]

[*]_Hardware_
[LIST]
[*]	**inxi -AG** and **inxi -h** » the A and G options output information about the audio and graphics hardware respectively. You usually want to use them together. The h option outputs you the full list of options you can use to get even more information about your hardware.
[/LIST]
[/LIST]

---

### Post by Reid_Huff on 2015-06-02
Thanks for that. It annoys me that my cheap laptop runs better than my gaming rig lol.

---

### Post by sandyd on 2015-06-02
You are using the open source *radeon* drivers for your video card. The proprietary drivers may have better performance

To install the proprietary drivers, go to Unity Dash -> Search for "Additional Drivers" and open the app.

The app should offer you video drivers to install, choose the one that says "recommended"

If you don't see any video drivers offered, make sure you are connected to the internet.

---

### Post by CantankRus on 2015-06-02
> GLX Renderer: Gallium 0.4 on **llvmpipe** (LLVM 3.5, 128 bits)
Doesn't this indicate software rendering is being used which would cause the laggy animations?

---

### Post by CantankRus on 2015-06-02
> GLX Renderer: Gallium 0.4 on **llvmpipe** (LLVM 3.5, 128 bits)
Doesn't this indicate software rendering is being used, hence the laggy animations?

---

### Post by Reid_Huff on 2015-06-03
I am using the recommended drivers for my card. How would you suggest I go about enabling hardware rendering? That seems like what it could be.

Is it possible that the 15.04 update will give me more success?

Update: It seems to be doing fine for some reason. I started getting a swap error on startup and tried a fix for that but both fixes weren't working but I wont question why it isn't lagging. Is there a way to monitor swap to see if it is working properly?

---

### Post by v3.xx on 2015-06-03
> **Reid_Huff said:**
> Is there a way to monitor swap to see if it is working properly?
```
gnome-system-monitor
```
and/or
```
free -m
```
> I am using the recommended drivers for my card.
What driver?

---

### Post by Reid_Huff on 2015-06-03
Swap does not seem to be doing anything at all at the moment. hmmm. 

I am using the Driver for the amd graphics accelerators from fglrx (proprietary) currently. 

At the time of that post I was using the X.Orgserver driver wrapper.

I'm I right to guess my computer has just had no use for swap yet. It says active in Gparted

Also I did the Unity Support test and that all looks good but I still have some lag.

---

### Post by Geoffrey_Arndt on 2015-06-03
As pointed out by CantankRus, the Gallium (open source driver) vs fglrx (proprietary) is doing the 3d (GLX) rendering - - hence sub-optimal hardware performance.    Swap is not the issue.

---

### Post by Reid_Huff on 2015-06-04
So what is the fix for that?

---

### Post by matt_symes on 2015-06-04
Hi

> First of all my USB 3.0 ports do not do anything.

From the terminal, please post the output of 

```
lsusb
```

Put a usb pen drive into one of the usb 3 ports, wait for 5 seconds then post the output of

```
dmesg | tail -n 15
```

Let's see if those commands throw any light on the problem.

KInd regards

---

### Post by Geoffrey_Arndt on 2015-06-04
> **Reid_Huff said:**
> So what is the fix for that?

Did Sandy's instructions not work (post #9) . . . ?

---

### Post by Reid_Huff on 2015-06-05
> **matt_symes said:**
> Hi



From the terminal, please post the output of 

```
lsusb
```

Put a usb pen drive into one of the usb 3 ports, wait for 5 seconds then post the output of

```
dmesg | tail -n 15
```

Let's see if those commands throw any light on the problem.

KInd regards

> Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0bc2:3320 Seagate RSS LLC SRD00F2 [Expansion Desktop Drive]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 045e:028e Microsoft Corp. Xbox360 Controller
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 1532:0037 Razer USA, Ltd 
Bus 004 Device 002: ID 1532:0109 Razer USA, Ltd Lycosa Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


> [   40.769472] <6>[fglrx] IRQ 76 Enabled
[   40.792589] <6>[fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   40.792591] <6>[fglrx] Reserved FB block: Unshared offset:f6b4000, size:4000 
[   40.792593] <6>[fglrx] Reserved FB block: Unshared offset:f6b8000, size:548000 
[   40.792594] <6>[fglrx] Reserved FB block: Unshared offset:fc00000, size:100000 
[   40.792596] <6>[fglrx] Reserved FB block: Unshared offset:fff8000, size:8000 
[   40.792597] <6>[fglrx] Reserved FB block: Unshared offset:ffff3000, size:d000 
[   41.182427] init: plymouth-upstart-bridge main process ended, respawning
[   41.187388] init: plymouth-upstart-bridge main process (1358) terminated with status 1
[   41.187400] init: plymouth-upstart-bridge main process ended, respawning
[   55.770247] init: ureadahead-other main process (2762) terminated with status 2
[   67.090223] audit_printk_skb: 186 callbacks suppressed
[   67.090226] audit: type=1400 audit(1433511640.393:74): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=3022 comm="apparmor_parser"
[   67.090233] audit: type=1400 audit(1433511640.393:75): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=3022 comm="apparmor_parser"
[   67.090568] audit: type=1400 audit(1433511640.393:76): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=3022 comm="apparmor_parser"





It seems to be running fine now with all of the drivers for some reason as well. 


I am also continuing to get swap errors on startup. 

> The Disk drive for /dev/mapper/cryptswap1 is not ready yet or present.

I have no idea if this has anything to do with it. 

```
kingreid@Reid-Desktop-Ubuntu:~$ glxinfo | grep "direct rendering"libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
kingreid@Reid-Desktop-Ubuntu:~$ glxinfo | grep OpenGL
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: AMD Radeon R9 200 Series 
OpenGL version string: 1.4 (2.1 (4.4.13374 Compatibility Profile Context 15.20.1013))
OpenGL extensions:



```

```
kingreid@Reid-Desktop-Ubuntu:~$ glxinfo | grep "direct rendering"
direct rendering: Yes
kingreid@Reid-Desktop-Ubuntu:~$ glxinfo | grep OpenGL
OpenGL vendor string: VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.5, 128 bits)
OpenGL version string: 3.0 Mesa 10.3.2
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
```

I fixed that I think but still have lag

---

### Post by CantankRus on 2015-06-05
You should be searching your vid card and driver issues.
llvmpipe is a fallback software rendering mode when your card is unsupported or for some reason the driver for your card is not loading.
Because it's using software rendering and not rendering using your GPU, the performance you get now depends on the power of your CPU.
Here's an askubuntu thread for your card.
[http://askubuntu.com/questions/496912/how-to-install-msi-radeon-r9-270-graphics-card-driver](http://askubuntu.com/questions/496912/how-to-install-msi-radeon-r9-270-graphics-card-driver)

---

### Post by Reid_Huff on 2015-06-05
> **CantankRus said:**
> You should be searching your vid card and driver issues.
llvmpipe is a fallback software rendering mode when your card is unsupported or for some reason the driver for your card is not loading.
Because it's using software rendering and not rendering using your GPU, the performance you get now depends on the power of your CPU.
Here's an askubuntu thread for your card.
[http://askubuntu.com/questions/496912/how-to-install-msi-radeon-r9-270-graphics-card-driver](http://askubuntu.com/questions/496912/how-to-install-msi-radeon-r9-270-graphics-card-driver)

Awesome! That did it. Thanks. GLX is now my AMD 2XX. Now I just need to figure out swap and my usb 3.0.

---

### Post by CantankRus on 2015-06-05
For swap info...
[http://askubuntu.com/questions/103915/how-do-i-configure-swappiness](http://askubuntu.com/questions/103915/how-do-i-configure-swappiness)

---

### Post by Reid_Huff on 2015-06-05
> **CantankRus said:**
> For swap info...
[http://askubuntu.com/questions/103915/how-do-i-configure-swappiness](http://askubuntu.com/questions/103915/how-do-i-configure-swappiness)

I don't it is mounted correctly so I don't believe adjusting it will change anything.

---

### Post by CantankRus on 2015-06-05
> **Reid_Huff said:**
> I don't it is mounted correctly so I don't believe adjusting it will change anything.
Why don't you think it is mounted correctly?

```
cat /etc/fstab
```

eg my fstab file
```
**[COLOR="#008000"]glen@Trusty:~$[/COLOR] cat /etc/fstab**
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

# / was on /dev/sdb5 during installation
UUID=13d2a077-a534-4490-95e9-bf71dc2fe3b8 /               ext4    errors=remount-ro 0       1

# swap was on /dev/sdc3 during installation
[COLOR="#B22222"]UUID=ac6cb7ba-4f9b-4493-842f-0926a86e3a89 none            swap    sw              0       0[/COLOR]

# Data Drive /dev/sdc7
UUID=bb31761a-6d8a-4693-b7c1-97f95100a126 /media/Data ext4 defaults 0 0
```

---

### Post by Reid_Huff on 2015-06-05
I get this on startup. 

```
[COLOR=#000000]*The Disk drive for /dev/mapper/cryptswap1 is not ready yet or present.*[/COLOR]
```

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass># / was on /dev/sda5 during installation
UUID=7c9db23b-28a3-41a8-b1cd-52dcf4b92fa9 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=13ad313e-b5a9-4f95-885c-238a7d81f656 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
#UUID=c8d6ec5f-89ab-4fa9-a449-5fc96bb65b4b none            swap    sw              0       0
#/dev/mapper/cryptswap1 none swap sw 0 0
/dev/mapper/cryptswap1 none swap sw 0 0
UUID=05996fb9-6df1-4fed-82ec-31b9aaf78d98    none    swap    sw      0   0



```

I guess it is just not getting to a point to where it needs to use it. 

Maybe it is just a random error message.

---

### Post by CantankRus on 2015-06-05
Google is a wonderful thing.
[**_[COLOR="#B22222"]What to do about “the disk drive for /dev/mapper/cryptswap1 is not ready yet or not present”?[/COLOR]_**]("http://askubuntu.com/questions/341979/what-to-do-about-the-disk-drive-for-dev-mapper-cryptswap1-is-not-ready-yet-or")

---

### Post by Reid_Huff on 2015-06-05
I have already done that but I got to a point where things weren't showing up.

[COLOR=#111111][FONT=Consolas]/etc/initramfs-tools/conf.d/resume was no where to be found

I just tried again and there is nothing named resume in that file[/FONT][/COLOR]

---

### Post by CantankRus on 2015-06-05
> **Reid_Huff said:**
> I have already done that but I got to a point where things weren't showing up.

[COLOR=#111111][FONT=Consolas]/etc/initramfs-tools/conf.d/resume was no where to be found

I just tried again and there is nothing named resume in that file[/FONT][/COLOR]
If your not using an encrypted drive you can probably just comment out (#) the "**/dev/mapper/cryptswap1 none swap sw 0 0**" line in /etc/fstab

---

### Post by Reid_Huff on 2015-06-05
It is encrypted.

---

### Post by matt_symes on 2015-06-06
Hi

That's not seeing your USB3 hub at all.

I think there may be a fix for this thought.

Boot into your BIOS and look for an option called 

```
IOMMU Controller
```

This is the Input/Output Memory Management Unit.

If it is disabled then enable it. 

Save the BIOS settings and then reboot.

Post back on efficacy.

If it does not fix it then we'll take a deeper look at you dmesg log.

Kind regards

---

### Post by Reid_Huff on 2015-06-06
> **matt_symes said:**
> Hi

That's not seeing your USB3 hub at all.

I think there may be a fix for this thought.

Boot into your BIOS and look for an option called 

```
IOMMU Controller
```

This is the Input/Output Memory Management Unit.

If it is disabled then enable it. 

Save the BIOS settings and then reboot.

Post back on efficacy.

If it does not fix it then we'll take a deeper look at you dmesg log.

Kind regards

I have already attempted that. It has been enabled since the beginning.

---

### Post by matt_symes on 2015-06-12
Hi

Post back your dmesg log.

Add it as an attachment is it may be large.

Kind regards

---

