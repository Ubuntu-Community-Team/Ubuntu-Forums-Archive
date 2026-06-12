---
title: "Switched from Windows to Ubuntu, problems persist"
date: 2015-10-27
forum: New to Ubuntu
---

### Post by james176 on 2015-10-27
Hi


I had an issue with my laptop and I sought advice on bleeping computer.com. Here is a paste of my posting:
Hi,
 
I recently bought a used Sony Vaio VPC-F22M0E (7 Ultimate x64) and it has been bluescreening with code 116 which I understand to be graphics related (NVIDIA GeForce GT540M GPU). I have tried downgrading the NVIDIA driver from the latest to the older version found on Sony's support site to no avail.
 
Using bluescreen viewer the following three sys files seem to be implicated.
 
dxgkrnl.sys&#8232;dxgmms1.sys&#8232;nvlddmkm.sys
 
Please could someone recommend a way to resolve these issues.
 
Thanks in advance.
 
 
Edit:
 
Just to make things even more depressing, I've just received stop code A
 
bluescreen viewer implicated the file below:
 
ntoskrnl.exe
Attached Files


*   SysnativeFileCollectionApp.zip  1.32MB   5 downloads


*   isometric.html   809.26KB   1 downloads


Edited by isometric, 18 October 2015 - 06:46 PM.


In the end I opted to install Ubuntu as virus scans, driver update attempts appeared fruitless considering the Windows itself seemed to be causing the issues. 


I've installed Ububtu and downloaded the latest basic updates. Issues remain with the display (it looks like small streaks of red horizontal lines) although it seems to be less severe than when I was running Windows7. 


If anybody can help I'd be grateful!

---

### Post by Bashing-om on 2015-10-27
james176; Hi ! Welcome to the forum .

Show us what we are working with.
Boot up ubuntu . At the desktop key combo ctl+alt+t will yield a terminal interface.
Post back - between code tags, please - the outputs of terminal commands:
```

lsb_release -a
sudo ubuntu-drivers devices
sudo ubuntu-drivers list
sudo lshw -C display

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

And we look about a possible/probable graphic's driver issue.

[INDENT][INDENT]we see
[INDENT][INDENT][INDENT][INDENT]what tale gets told
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by james176 on 2015-10-27
forgot to mention some difficulties booting up also. It just took apporx 20 attempts to boot up.
so in order, here's step 1 of what you've requested to see

```
james@james-VPCF22M0E:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty
james@james-VPCF22M0E:~$ ^C
```

step 2 
```
james@james-VPCF22M0E:~$ sudo ubuntu-drivers devices
[sudo] password for james: 
Sorry, try again.
[sudo] password for james: 
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
vendor   : NVIDIA Corporation
model    : GF108M [GeForce GT 540M]
modalias : pci:v000010DEd00000DF4sv0000104Dsd00009089bc03sc00i00
driver   : nvidia-340-updates - distro non-free
driver   : nvidia-304-updates - distro non-free
driver   : nvidia-346 - distro non-free recommended
driver   : nvidia-304 - distro non-free
driver   : nvidia-340 - distro non-free
driver   : nvidia-346-updates - distro non-free
driver   : xserver-xorg-video-nouveau - distro free builtin
```

step 3
```
james@james-VPCF22M0E:~$ sudo ubuntu-drivers list
nvidia-304
nvidia-340-updates
nvidia-346-updates
nvidia-346
nvidia-304-updates
nvidia-340
james@james-VPCF22M0E:~$ 
```

step 4
```
james@james-VPCF22M0E:~$ sudo lshw -C display
[sudo] password for james: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: GF108M [GeForce GT 540M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller cap_list
       configuration: latency=0
       resources: memory:f4000000-f4ffffff memory:d0000000-dfffffff memory:e0000000-e1ffffff ioport:d000(size=128) memory:f5000000-f507ffff
```

---

### Post by Bashing-om on 2015-10-27
james176; Hey hey ...

step 4 shows no graphic's driver loaded..

Let us see what results :
```

sudo apt update
sudo apt upgrade
sudo ubuntu-drivers autoinstall

``` where I am "assuming" no proprietary driver install attempt has been made on this install .
Reboot the system to see the effect . 
Advise please of the result.

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]no fuss
[INDENT][INDENT][INDENT]no muss
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by james176 on 2015-10-27
Hey hey

boot up was interesting.... Lots of screen glitches, failed to boot. Tried again, computer is unresponsive. There's a box that says "system program problem detected, do you want to report the problem now? The two options to either cancel or report are unresponsive.

---

### Post by Vladlenin5000 on 2015-10-27
Considering your reported issues in Windows and what happened now in Ubuntu, I'm 99.9% sure the hardware is defective. You better return it if you can because repairing an out of warranty Sony laptop is probably more expensive than buying a new one.

---

### Post by james176 on 2015-10-27
When I trialled the OS from a USB stick, it worked absolutely fine apart from a couple of times it failed to boot, but screen issues were absent.

---

### Post by Vladlenin5000 on 2015-10-27
> **james176 said:**
> When I trialled the OS from a USB stick, it worked absolutely fine apart from a couple of times it failed to boot, but screen issues were absent.

Yes, because in a live session you were using the generic non-3D non-demanding video driver.

---

### Post by james176 on 2015-10-27
Just booted up and a message read :

the he system is running in low graphics mode. Your screen graphics card and input device settings could not be detected correctly. You will need to configure these yourself.

options available at next box:
run in low graphics mode 
reconfigure graphics
triubleshoot the error
exit to console login

thabks for the help so far guys

---

### Post by Vladlenin5000 on 2015-10-27
That kinda confirms it but let's wait for Bashing-om's opinion on the matter. I have nothing to offer as help at this point.

---

### Post by Bashing-om on 2015-10-27
james176; Welp;

We can always look and see what the system may report .
Boot ubuntu and activate a terminal ( because a terminal is 'universal' and easier to work between) .
Post back the output of terminal command:
```

cat /var/log/Xorg.0.log

```
where in 'buntu X is that GUI layer and the log reflects what it is doing and why .
Maybe we are looking at a driver not being built and installed for some reason ?

[INDENT][INDENT]gots to be a cause
[/INDENT][/INDENT]

---

### Post by james176 on 2015-10-27
Failed to boot. Will try again and post update tomorrow. Thanks for support. Over n out.

Hi!

So booting was tricky! I managed to boot up via USB, 
```
[    24.532]     LinRsvdFieldPosition: 24
[    24.532]     MaxPixelClock: 229500000
[    24.533] Mode: 14b (1600x900)
[    24.533]     ModeAttributes: 0x3bf
[    24.533]     WinAAttributes: 0x7
[    24.533]     WinBAttributes: 0x0
[    24.533]     WinGranularity: 64
[    24.533]     WinSize: 64
[    24.533]     WinASegment: 0xa000
[    24.533]     WinBSegment: 0x0
[    24.533]     WinFuncPtr: 0xc0006971
[    24.533]     BytesPerScanline: 1600
[    24.533]     XResolution: 1600
[    24.533]     YResolution: 900
[    24.533]     XCharSize: 8
[    24.533]     YCharSize: 16
[    24.533]     NumberOfPlanes: 1
[    24.533]     BitsPerPixel: 8
[    24.533]     NumberOfBanks: 1
[    24.533]     MemoryModel: 4
[    24.533]     BankSize: 0
[    24.533]     NumberOfImages: 1
[    24.533]     RedMaskSize: 0
[    24.533]     RedFieldPosition: 0
[    24.533]     GreenMaskSize: 0
[    24.533]     GreenFieldPosition: 0
[    24.533]     BlueMaskSize: 0
[    24.533]     BlueFieldPosition: 0
[    24.533]     RsvdMaskSize: 0
[    24.533]     RsvdFieldPosition: 0
[    24.533]     DirectColorModeInfo: 0
[    24.533]     PhysBasePtr: 0xe1000000
[    24.533]     LinBytesPerScanLine: 1600
[    24.533]     BnkNumberOfImagePages: 1
[    24.533]     LinNumberOfImagePages: 1
[    24.533]     LinRedMaskSize: 0
[    24.533]     LinRedFieldPosition: 0
[    24.533]     LinGreenMaskSize: 0
[    24.533]     LinGreenFieldPosition: 0
[    24.533]     LinBlueMaskSize: 0
[    24.533]     LinBlueFieldPosition: 0
[    24.533]     LinRsvdMaskSize: 0
[    24.533]     LinRsvdFieldPosition: 0
[    24.534]     MaxPixelClock: 229500000
[    24.535] Mode: 14c (1600x900)
[    24.535]     ModeAttributes: 0x3bf
[    24.535]     WinAAttributes: 0x7
[    24.535]     WinBAttributes: 0x0
[    24.535]     WinGranularity: 64
[    24.535]     WinSize: 64
[    24.535]     WinASegment: 0xa000
[    24.535]     WinBSegment: 0x0
[    24.535]     WinFuncPtr: 0xc0006971
[    24.535]     BytesPerScanline: 3200
[    24.535]     XResolution: 1600
[    24.535]     YResolution: 900
[    24.535]     XCharSize: 8
[    24.535]     YCharSize: 16
[    24.535]     NumberOfPlanes: 1
[    24.535]     BitsPerPixel: 16
[    24.535]     NumberOfBanks: 1
[    24.535]     MemoryModel: 6
[    24.535]     BankSize: 0
[    24.535]     NumberOfImages: 1
[    24.535]     RedMaskSize: 5
[    24.535]     RedFieldPosition: 11
[    24.535]     GreenMaskSize: 6
[    24.535]     GreenFieldPosition: 5
[    24.535]     BlueMaskSize: 5
[    24.535]     BlueFieldPosition: 0
[    24.535]     RsvdMaskSize: 0
[    24.535]     RsvdFieldPosition: 0
[    24.535]     DirectColorModeInfo: 0
[    24.535]     PhysBasePtr: 0xe1000000
[    24.535]     LinBytesPerScanLine: 3200
[    24.535]     BnkNumberOfImagePages: 1
[    24.535]     LinNumberOfImagePages: 1
[    24.535]     LinRedMaskSize: 5
[    24.535]     LinRedFieldPosition: 11
[    24.535]     LinGreenMaskSize: 6
[    24.535]     LinGreenFieldPosition: 5
[    24.535]     LinBlueMaskSize: 5
[    24.535]     LinBlueFieldPosition: 0
[    24.535]     LinRsvdMaskSize: 0
[    24.535]     LinRsvdFieldPosition: 0
[    24.535]     MaxPixelClock: 229500000
[    24.537] *Mode: 14d (1600x900)
[    24.537]     ModeAttributes: 0x3bf
[    24.537]     WinAAttributes: 0x7
[    24.537]     WinBAttributes: 0x0
[    24.537]     WinGranularity: 64
[    24.537]     WinSize: 64
[    24.537]     WinASegment: 0xa000
[    24.537]     WinBSegment: 0x0
[    24.537]     WinFuncPtr: 0xc0006971
[    24.537]     BytesPerScanline: 6400
[    24.537]     XResolution: 1600
[    24.537]     YResolution: 900
[    24.537]     XCharSize: 8
[    24.537]     YCharSize: 16
[    24.537]     NumberOfPlanes: 1
[    24.537]     BitsPerPixel: 32
[    24.537]     NumberOfBanks: 1
[    24.537]     MemoryModel: 6
[    24.537]     BankSize: 0
[    24.537]     NumberOfImages: 1
[    24.537]     RedMaskSize: 8
[    24.537]     RedFieldPosition: 16
[    24.537]     GreenMaskSize: 8
[    24.537]     GreenFieldPosition: 8
[    24.537]     BlueMaskSize: 8
[    24.537]     BlueFieldPosition: 0
[    24.537]     RsvdMaskSize: 8
[    24.537]     RsvdFieldPosition: 24
[    24.537]     DirectColorModeInfo: 0
[    24.537]     PhysBasePtr: 0xe1000000
[    24.537]     LinBytesPerScanLine: 6400
[    24.537]     BnkNumberOfImagePages: 1
[    24.537]     LinNumberOfImagePages: 1
[    24.537]     LinRedMaskSize: 8
[    24.537]     LinRedFieldPosition: 16
[    24.537]     LinGreenMaskSize: 8
[    24.537]     LinGreenFieldPosition: 8
[    24.537]     LinBlueMaskSize: 8
[    24.537]     LinBlueFieldPosition: 0
[    24.537]     LinRsvdMaskSize: 8
[    24.537]     LinRsvdFieldPosition: 24
[    24.537]     MaxPixelClock: 229500000
[    24.539] Mode: 160 (1280x800)
[    24.539]     ModeAttributes: 0x3bf
[    24.539]     WinAAttributes: 0x7
[    24.539]     WinBAttributes: 0x0
[    24.539]     WinGranularity: 64
[    24.539]     WinSize: 64
[    24.539]     WinASegment: 0xa000
[    24.539]     WinBSegment: 0x0
[    24.539]     WinFuncPtr: 0xc0006971
[    24.539]     BytesPerScanline: 1280
[    24.539]     XResolution: 1280
[    24.539]     YResolution: 800
[    24.539]     XCharSize: 8
[    24.539]     YCharSize: 16
[    24.539]     NumberOfPlanes: 1
[    24.539]     BitsPerPixel: 8
[    24.539]     NumberOfBanks: 1
[    24.539]     MemoryModel: 4
[    24.539]     BankSize: 0
[    24.539]     NumberOfImages: 2
[    24.539]     RedMaskSize: 0
[    24.539]     RedFieldPosition: 0
[    24.539]     GreenMaskSize: 0
[    24.539]     GreenFieldPosition: 0
[    24.539]     BlueMaskSize: 0
[    24.539]     BlueFieldPosition: 0
[    24.539]     RsvdMaskSize: 0
[    24.539]     RsvdFieldPosition: 0
[    24.539]     DirectColorModeInfo: 0
[    24.539]     PhysBasePtr: 0xe1000000
[    24.539]     LinBytesPerScanLine: 1280
[    24.539]     BnkNumberOfImagePages: 2
[    24.539]     LinNumberOfImagePages: 2
[    24.539]     LinRedMaskSize: 0
[    24.539]     LinRedFieldPosition: 0
[    24.539]     LinGreenMaskSize: 0
[    24.539]     LinGreenFieldPosition: 0
[    24.539]     LinBlueMaskSize: 0
[    24.539]     LinBlueFieldPosition: 0
[    24.539]     LinRsvdMaskSize: 0
[    24.539]     LinRsvdFieldPosition: 0
[    24.539]     MaxPixelClock: 229500000
[    24.541] *Mode: 161 (1280x800)
[    24.541]     ModeAttributes: 0x3bf
[    24.541]     WinAAttributes: 0x7
[    24.541]     WinBAttributes: 0x0
[    24.541]     WinGranularity: 64
[    24.541]     WinSize: 64
[    24.541]     WinASegment: 0xa000
[    24.541]     WinBSegment: 0x0
[    24.541]     WinFuncPtr: 0xc0006971
[    24.541]     BytesPerScanline: 5120
[    24.541]     XResolution: 1280
[    24.541]     YResolution: 800
[    24.541]     XCharSize: 8
[    24.541]     YCharSize: 16
[    24.541]     NumberOfPlanes: 1
[    24.541]     BitsPerPixel: 32
[    24.541]     NumberOfBanks: 1
[    24.541]     MemoryModel: 6
[    24.541]     BankSize: 0
[    24.541]     NumberOfImages: 1
[    24.541]     RedMaskSize: 8
[    24.541]     RedFieldPosition: 16
[    24.541]     GreenMaskSize: 8
[    24.541]     GreenFieldPosition: 8
[    24.541]     BlueMaskSize: 8
[    24.541]     BlueFieldPosition: 0
[    24.541]     RsvdMaskSize: 8
[    24.541]     RsvdFieldPosition: 24
[    24.541]     DirectColorModeInfo: 0
[    24.541]     PhysBasePtr: 0xe1000000
[    24.541]     LinBytesPerScanLine: 5120
[    24.541]     BnkNumberOfImagePages: 1
[    24.541]     LinNumberOfImagePages: 1
[    24.541]     LinRedMaskSize: 8
[    24.541]     LinRedFieldPosition: 16
[    24.541]     LinGreenMaskSize: 8
[    24.541]     LinGreenFieldPosition: 8
[    24.541]     LinBlueMaskSize: 8
[    24.541]     LinBlueFieldPosition: 0
[    24.541]     LinRsvdMaskSize: 8
[    24.541]     LinRsvdFieldPosition: 24
[    24.541]     MaxPixelClock: 229500000
[    24.541] 
[    24.541] (II) VESA(0): Total Memory: 224 64KB banks (14336kB)
[    24.541] (II) VESA(0): <default monitor>: Using default hsync range of 31.50-48.00 kHz
[    24.541] (II) VESA(0): <default monitor>: Using default vrefresh range of 50.00-70.00 Hz
[    24.541] (II) VESA(0): <default monitor>: Using default maximum pixel clock of 65.00 MHz
[    24.541] (WW) VESA(0): Unable to estimate virtual size
[    24.541] (II) VESA(0): Not using built-in mode "1600x900" (no mode of this name)
[    24.541] (II) VESA(0): Not using built-in mode "1280x800" (no mode of this name)
[    24.541] (II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
[    24.541] (II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
[    24.541] (II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
[    24.541] (II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
[    24.541] (II) VESA(0): Not using built-in mode "320x400" (no mode of this name)
[    24.541] (II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
[    24.541] (II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
[    24.541] (WW) VESA(0): No valid modes left. Trying less strict filter...
[    24.541] (II) VESA(0): <default monitor>: Using hsync range of 31.50-48.00 kHz
[    24.541] (II) VESA(0): <default monitor>: Using vrefresh range of 50.00-70.00 Hz
[    24.541] (II) VESA(0): <default monitor>: Using maximum pixel clock of 65.00 MHz
[    24.541] (WW) VESA(0): Unable to estimate virtual size
[    24.541] (II) VESA(0): Not using built-in mode "1600x900" (hsync out of range)
[    24.541] (II) VESA(0): Not using built-in mode "1280x800" (hsync out of range)
[    24.541] (II) VESA(0): Not using built-in mode "640x400" (hsync out of range)
[    24.541] (II) VESA(0): Not using built-in mode "320x400" (hsync out of range)
[    24.541] (II) VESA(0): Not using built-in mode "320x240" (illegal horizontal timings)
[    24.541] (II) VESA(0): Not using built-in mode "320x200" (illegal horizontal timings)
[    24.541] (--) VESA(0): Virtual size is 1024x768 (pitch 1024)
[    24.541] (**) VESA(0): *Built-in mode "1024x768"
[    24.541] (**) VESA(0): *Built-in mode "800x600"
[    24.541] (**) VESA(0): *Built-in mode "640x480"
[    24.541] (==) VESA(0): DPI set to (96, 96)
[    24.541] (II) VESA(0): Attempting to use 60Hz refresh for mode "1024x768" (118)
[    24.542] (II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (115)
[    24.543] (II) VESA(0): Attempting to use 60Hz refresh for mode "640x480" (112)
[    24.543] (**) VESA(0): Using "Shadow Framebuffer"
[    24.543] (II) Loading sub module "shadow"
[    24.543] (II) LoadModule: "shadow"
[    24.543] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    24.543] (II) Module shadow: vendor="X.Org Foundation"
[    24.543]     compiled for 1.17.1, module version = 1.1.0
[    24.543]     ABI class: X.Org ANSI C Emulation, version 0.4
[    24.543] (II) Loading sub module "fb"
[    24.543] (II) LoadModule: "fb"
[    24.543] (II) Loading /usr/lib/xorg/modules/libfb.so
[    24.545] (II) Module fb: vendor="X.Org Foundation"
[    24.545]     compiled for 1.17.1, module version = 1.0.0
[    24.545]     ABI class: X.Org ANSI C Emulation, version 0.4
[    24.545] (==) Depth 24 pixmap format is 32 bpp
[    24.545] (II) Loading sub module "int10"
[    24.545] (II) LoadModule: "int10"
[    24.545] (II) Loading /usr/lib/xorg/modules/libint10.so
[    24.545] (II) Module int10: vendor="X.Org Foundation"
[    24.545]     compiled for 1.17.1, module version = 1.0.0
[    24.545]     ABI class: X.Org Video Driver, version 19.0
[    24.545] (II) VESA(0): initializing int10
[    24.545] (II) VESA(0): Bad V_BIOS checksum
[    24.545] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    24.615] (II) VESA(0): VESA BIOS detected
[    24.615] (II) VESA(0): VESA VBE Version 3.0
[    24.615] (II) VESA(0): VESA VBE Total Mem: 14336 kB
[    24.616] (II) VESA(0): VESA VBE OEM: NVIDIA
[    24.616] (II) VESA(0): VESA VBE OEM Software Rev: 112.8
[    24.616] (II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
[    24.616] (II) VESA(0): VESA VBE OEM Product: GF108 Board - 1079df40
[    24.616] (II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
[    24.616] (II) VESA(0): virtual address = 0x7f7900aca000,
    physical address = 0xe1000000, size = 14680064
[    24.639] (II) VESA(0): Setting up VESA Mode 0x118 (1024x768)
[    24.729] (==) VESA(0): Default visual is TrueColor
[    24.732] (==) VESA(0): Backing store enabled
[    24.732] (==) VESA(0): DPMS enabled
[    24.732] (==) RandR enabled
[    24.736] (II) AIGLX: Screen 0 is not DRI2 capable
[    24.736] (EE) AIGLX: reverting to software rendering
[    25.538] (II) AIGLX: Loaded and initialized swrast
[    25.538] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    25.617] (II) XKB: generating xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    25.739] (II) config/udev: Adding input device Sony Vaio Keys (/dev/input/event5)
[    25.739] (**) Sony Vaio Keys: Applying InputClass "evdev keyboard catchall"
[    25.739] (II) LoadModule: "evdev"
[    25.739] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.763] (II) Module evdev: vendor="X.Org Foundation"
[    25.763]     compiled for 1.17.1, module version = 2.9.0
[    25.763]     Module class: X.Org XInput Driver
[    25.763]     ABI class: X.Org XInput driver, version 21.0
[    25.763] (II) Using input driver 'evdev' for 'Sony Vaio Keys'
[    25.763] (**) Sony Vaio Keys: always reports core events
[    25.763] (**) evdev: Sony Vaio Keys: Device: "/dev/input/event5"
[    25.763] (--) evdev: Sony Vaio Keys: Vendor 0x104d Product 0
[    25.763] (--) evdev: Sony Vaio Keys: Found keys
[    25.763] (II) evdev: Sony Vaio Keys: Configuring as keyboard
[    25.763] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/SNY5001:00/input/input6/event5"
[    25.763] (II) XINPUT: Adding extended input device "Sony Vaio Keys" (type: KEYBOARD, id 6)
[    25.763] (**) Option "xkb_rules" "evdev"
[    25.763] (**) Option "xkb_model" "pc105"
[    25.763] (**) Option "xkb_layout" "us"
[    25.764] (II) config/udev: Adding input device Sony Vaio Jogdial (/dev/input/event6)
[    25.764] (II) No input driver specified, ignoring this device.
[    25.764] (II) This device may have been added with another device file.
[    25.764] (II) config/udev: Adding input device Sony Vaio Jogdial (/dev/input/mouse1)
[    25.764] (II) No input driver specified, ignoring this device.
[    25.764] (II) This device may have been added with another device file.
[    25.764] (II) config/udev: Adding input device Video Bus (/dev/input/event3)
[    25.764] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    25.764] (II) Using input driver 'evdev' for 'Video Bus'
[    25.764] (**) Video Bus: always reports core events
[    25.764] (**) evdev: Video Bus: Device: "/dev/input/event3"
[    25.764] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    25.764] (--) evdev: Video Bus: Found keys
[    25.764] (II) evdev: Video Bus: Configuring as keyboard
[    25.764] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1e/LNXVIDEO:00/input/input5/event3"
[    25.764] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    25.764] (**) Option "xkb_rules" "evdev"
[    25.764] (**) Option "xkb_model" "pc105"
[    25.764] (**) Option "xkb_layout" "us"
[    25.764] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    25.764] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    25.764] (II) Using input driver 'evdev' for 'Power Button'
[    25.764] (**) Power Button: always reports core events
[    25.764] (**) evdev: Power Button: Device: "/dev/input/event1"
[    25.764] (--) evdev: Power Button: Vendor 0 Product 0x1
[    25.764] (--) evdev: Power Button: Found keys
[    25.764] (II) evdev: Power Button: Configuring as keyboard
[    25.764] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[    25.764] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    25.764] (**) Option "xkb_rules" "evdev"
[    25.764] (**) Option "xkb_model" "pc105"
[    25.764] (**) Option "xkb_layout" "us"
[    25.765] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    25.765] (II) No input driver specified, ignoring this device.
[    25.765] (II) This device may have been added with another device file.
[    25.765] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event10)
[    25.765] (II) No input driver specified, ignoring this device.
[    25.765] (II) This device may have been added with another device file.
[    25.765] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event11)
[    25.765] (II) No input driver specified, ignoring this device.
[    25.765] (II) This device may have been added with another device file.
[    25.765] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event12)
[    25.765] (II) No input driver specified, ignoring this device.
[    25.765] (II) This device may have been added with another device file.
[    25.765] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event13)
[    25.765] (II) No input driver specified, ignoring this device.
[    25.765] (II) This device may have been added with another device file.
[    25.766] (II) config/udev: Adding input device USB2.0 Camera (/dev/input/event9)
[    25.766] (**) USB2.0 Camera: Applying InputClass "evdev keyboard catchall"
[    25.766] (II) Using input driver 'evdev' for 'USB2.0 Camera'
[    25.766] (**) USB2.0 Camera: always reports core events
[    25.766] (**) evdev: USB2.0 Camera: Device: "/dev/input/event9"
[    25.766] (--) evdev: USB2.0 Camera: Vendor 0x5ca Product 0x18c0
[    25.766] (--) evdev: USB2.0 Camera: Found keys
[    25.766] (II) evdev: USB2.0 Camera: Configuring as keyboard
[    25.766] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.0/input/input10/event9"
[    25.766] (II) XINPUT: Adding extended input device "USB2.0 Camera" (type: KEYBOARD, id 9)
[    25.766] (**) Option "xkb_rules" "evdev"
[    25.766] (**) Option "xkb_model" "pc105"
[    25.766] (**) Option "xkb_layout" "us"
[    25.766] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event7)
[    25.766] (II) No input driver specified, ignoring this device.
[    25.766] (II) This device may have been added with another device file.
[    25.766] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event8)
[    25.766] (II) No input driver specified, ignoring this device.
[    25.766] (II) This device may have been added with another device file.
[    25.766] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    25.766] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    25.766] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    25.766] (**) AT Translated Set 2 keyboard: always reports core events
[    25.766] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    25.766] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    25.766] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    25.766] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    25.766] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    25.766] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[    25.766] (**) Option "xkb_rules" "evdev"
[    25.766] (**) Option "xkb_model" "pc105"
[    25.766] (**) Option "xkb_layout" "us"
[    25.767] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event4)
[    25.767] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    25.767] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    25.767] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    25.767] (II) LoadModule: "synaptics"
[    25.767] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    25.768] (II) Module synaptics: vendor="X.Org Foundation"
[    25.768]     compiled for 1.17.1, module version = 1.8.99
[    25.768]     Module class: X.Org XInput Driver
[    25.768]     ABI class: X.Org XInput driver, version 21.0
[    25.768] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    25.768] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    25.768] (**) Option "Device" "/dev/input/event4"
[    25.792] (II) synaptics: SynPS/2 Synaptics TouchPad: ignoring touch events for semi-multitouch device
[    25.792] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5744 (res 49)
[    25.792] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4926 (res 87)
[    25.792] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    25.792] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    25.792] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    25.792] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    25.792] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    25.792] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    25.808] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input4/event4"
[    25.808] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 11)
[    25.808] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    25.808] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    25.808] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.036
[    25.808] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    25.808] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    25.808] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    25.808] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    25.808] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    25.808] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    25.808] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    30.426] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    37.107] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    37.119] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    37.132] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    37.168] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    37.171] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    37.174] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    37.240] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    37.243] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    37.252] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    39.921] (II) XKB: generating xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
```

---

### Post by Bashing-om on 2015-10-28
james176; UnGood;

So far as I can see. We must continue to maintain the probability of hardware issues:
> 
[    24.545] (II) VESA(0): Bad V_BIOS checksum


Even though the system is aware that a Nvidia graphic's card exist, no effort is made to build or install a driver - not even the expected nouveau driver. Instead the system is falling back to the kernel's 'vesa' driver ... huh ? We must question if this is a valid install medium that you used to install ubuntu .

Did you verify the .iso download integrity ?
Did you verify the burn ?
Can you boot the liveDVD(USB) in "try ubuntu" mode; and all functions as expected ?

Until we know the foundation is sound ->
[INDENT][INDENT][INDENT]not looking good for the home team
[/INDENT][/INDENT][/INDENT]

---

### Post by james176 on 2015-10-28
my friend guided me with the ubuntu download onto the USB, He has IT experience / fixing BSOD problems etc..
I am currently booted onto the "tru ubuntu" mode. Its running quite well but not perfect. there is still the odd screen glitch.

Thank you for all your help so far guys. I'd be clueless without it!

---

### Post by Bashing-om on 2015-10-28
james176; Hey !


Let us at the least verify that live(USB); then see what we may do.

Reboot the live(USB) and as soon as the bios screen clears depress and hold a shift key ( UEFI system it is the escape key and only a 3 second window - repeatedly depress/release the escape key) -> language screen, escape key to accept the default -> Boot options screen .
In this screen select " check disk for defects " will take some time for the check to complete.

Does it complete with no errors reported ?

[INDENT][INDENT]some things
[INDENT][INDENT][INDENT]are not to be taken for granted
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by james176 on 2015-10-28
[ATTACH=CONFIG]265218[/ATTACH]

---

### Post by Bashing-om on 2015-10-28
james176; Uh HUh !

So we have hope it is a software problem rather than hardware !
Now you know what comes next ... RE-burn the USB.

I do suggest that you do install 14.04 ... the .3 release -current - may do just fine and is the easier for a new user to deal with:
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows](http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

Now what assets do you have at your disposal to burn the .iso file - Burn as an image ! - to either a USB or DVD . If you need additional guidance to use the asset you have available; We sure try and guide .

Better this - RE-Burn && (RE-)install

[INDENT][INDENT][INDENT]than replace BIOS
[/INDENT][/INDENT][/INDENT]

---

### Post by james176 on 2015-10-29
I struggled to do all of the above, but I did another test of sorts, I ran the trial Ubuntu on a friends computer. It ran fine. Does that mean that the Ubuntu software on my USB is okay? Please advise. Many thanks.m

---

### Post by Bashing-om on 2015-10-29
james176; Nope;

All we know presently is that the live(USB) has 2 errors ... not a good thing at all !
We have to establish that our foundation is firm, that the install medium is sound .
My advise remains the same .. (RE-)burn the .iso .. verify every step of the way ... and 
(RE-)install the operating system.

Will not take that long - once you have done it a couple of times - and the experience of learning

[INDENT][INDENT][INDENT]will only do you good
[/INDENT][/INDENT][/INDENT]

---

### Post by james176 on 2015-10-29
Ok

installed onto dvd as per instructions 
dvd passed all the tests, the usb did not. 
Booting up from DVD now and there are screen issues occurring... Do you want to see a picture of it?

[ATTACH=CONFIG]265249[/ATTACH]

I managed to film it and caught a quick message that comes up on the display reading:

[    6.492640] ACPI PCC probe failed.

---

### Post by Bashing-om on 2015-10-29
james176; Hey,

Still that is good news .

Reboot, hold down shift until the GRUB boot menu shows. Highlight the Ubuntu entry, press 'E' to edit it. Navigate to the line starting "linux ...", where you see "quiet splash" insert BEFORE those the term "nomodeset" - with out the quotes - so the line end looks like "  nomodeset quiet splash ", THEN press either Ctrl+X, or F10, to boot with that change.

Can you now boot to a GUI ? If so we can consider installing a graphic's driver.

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by james176 on 2015-10-29
Yay!
reinstall in progress

do I want to:
erase u Ubuntu 14.04.3 LTS and reinstall
or
install alongside (I don't think so!)
or
erase disk and install Ubuntu ?

---

### Post by Bashing-om on 2015-10-29
james176; Hey !

As a 1st time user I do suggest " erase disk and install Ubuntu  " ; Take the easy way and let the wizard do all the work .

[INDENT][INDENT]making progress
[/INDENT][/INDENT]

---

### Post by james176 on 2015-10-29
Installation is complete. It wants to restart but the boot priority 1 is optical disk, so I need to remove the dvd before restarting?

---

### Post by Bashing-om on 2015-10-29
james176l Well ..

When you "restart" the DVD will eject . You will be prompted to close the tray and press the enter key .

You might want to consider changing in bios the boot priority to that of the hard drive . Will boot a tad bit faster.
However, I leave the boot priority as the DVD drive as 1st, as I boot DVDs many times . If there is no disk present, bios will default to the boot code on the hard drive .

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by james176 on 2015-10-29
Ok.... Successfully booted up. Little streaks still present on display.

cool.

what shall I test first and how? Thanks for getting me this far!

---

### Post by Bashing-om on 2015-10-29
james176; Great !

Still with a graphic's driver issue (?). Let get an overview of what is:
At the desktop key combo ctl+alt+t will yield a terminal:
post back the outputs - between code tags - of terminal commands:
```

sudo ubuntu-drivers devices
sudo ubuntu-drivers list
sudo lshw -C display

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

And we see what we can do .

[INDENT][INDENT]won't hurt to look
[/INDENT][/INDENT]

---

### Post by james176 on 2015-10-29
Sure, will do....
```
james@james-VPCF22M0E:~$ sudo ubuntu-drivers devices
[sudo] password for james: 
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
vendor   : NVIDIA Corporation
modalias : pci:v000010DEd00000DF4sv0000104Dsd00009089bc03sc00i00
model    : GF108M [GeForce GT 540M]
driver   : nvidia-304-updates - distro non-free
driver   : nvidia-340-updates - distro non-free
driver   : nvidia-346-updates - distro non-free
driver   : nvidia-346 - distro non-free recommended
driver   : xserver-xorg-video-nouveau - distro free builtin
driver   : nvidia-304 - distro non-free
driver   : nvidia-340 - distro non-free
```

```
james@james-VPCF22M0E:~$ sudo ubuntu-drivers list
[sudo] password for james: 
nvidia-346-updates
nvidia-346
nvidia-340-updates
nvidia-304
nvidia-340
nvidia-304-updates
```

```
james@james-VPCF22M0E:~$ sudo lshw -C display
[sudo] password for james: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: GF108M [GeForce GT 540M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller cap_list
       configuration: latency=0
       resources: memory:f4000000-f4ffffff memory:d0000000-dfffffff memory:e0000000-e1ffffff ioport:d000(size=128) memory:f5000000-f507ffff

```

---

### Post by Bashing-om on 2015-10-29
james176; Hey ...

still with no driver loaded .. very strange ... 
But ...
try:
```

sudo ubuntu-drivers autoinstall

```
reboot to see the effect.

Maybe
[INDENT][INDENT]yes
[/INDENT][/INDENT]

---

### Post by james176 on 2015-10-29
Ok so it all installed, I rebooted.... During reboot display issues were present and it failed to boot. Attempted to boot again, got the msg coming up: the system is running in low graphics mode. Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself.

And then I get the 4 options:
run in low graphics mode
rexonfigure graphics 
troubleshoot
exit to login

---

### Post by Bashing-om on 2015-10-29
james176 .... Yuk !

This is totally not normal !

OK, did the Nvidia driver build a config file ?
post back:
```

cat /etc/X11/Xorg.conf

```

[INDENT]now we may have a problem ?
[/INDENT]

---

### Post by james176 on 2015-10-29
But.... I can't select an option :-/

Ok will try and check that...

Managed to boot up, a warning popped up about the system not working, PC is unresponsive - not letting me use a terminal, and now the cursor won't move. Shall I try and start it in low graphics mode?

Failed to boot in low graphics mode

I'm reinstalling, as the changes made after the driver auto update make the computer too difficult to use. Perhaps I can go from that point?

Re installed, computer is usable. I'll reboot to check for start up symptoms.

```
james@james-VPCF22M0E:~$ cat /etc/X11/Xorg.conf
cat: /etc/X11/Xorg.conf: No such file or directory
```

---

### Post by Mike_Walsh on 2015-10-30
I concur with VladLenin5000; definitely defective hardware.


Regards,

Mike. :icon_frown:

---

### Post by james176 on 2015-10-30
Thank you for your opinion mate. Is it likely to be the graphics card? I might be able to get hold of parts.

---

### Post by Mike_Walsh on 2015-10-30
Knowing Sony, all they'll say is 'Replace it with a new one.' It obviously isn't new; probably out of warranty. Sony have had a few problems with the Vaios over the years; this sounds like yet another one to add to the catalogue. 

It's probably why the previous owner offloaded it..... As for obtaining parts, well, sure; if you don't mind stripping old laptops down, and if you're handy with a soldering iron. Sony will want an arm and a leg to fix it; they'll probably just replace the entire mobo with a re-conditioned one, and charge you a small fortune. Graphics cards on run-of-the-mill laptops are usually integrated, and therefore **not** replaceable.

You'd honestly be better off looking around on eBay or Amazon for another second-hand one; there's plenty out there that are in pretty good shape. You do need to keep your wits about you, though; if it sounds too good to be true, it usually is..!


Regards,

Mike. ;)

---

### Post by Bashing-om on 2015-10-31
james176; Morning;

Mike has  been around the block a time or two, and he has the experience to know. We should keep his and Vladlenin5000's advise and recommendations under consideration. However, to this time we have no proof that the hardware has failed. Looks to me as we have a graphic's driver issue of undetermined origin. 
As this is a laptop, maybe optimus technology, and video display components are disabled in bios ???
Take a look in bios and see what is set up for the display. As this is a used box there is no telling what the former owner may have changed ... might even be a good thing to revert bios back to defaults and start all over from scratch.
Though admittedly we do have indications from the former install that the system is flailing trying to get the interface working.

What specifically is this laptop, we look up the specs and see what we are dealing with here.

If you are running the nouveau graphic's driver, there will be no /Xorg.conf. Nvidia uses that file to configure how it relates to the kernel.


We need to develop a plan of attack and these plans always begin in bios, what is set in bios ?
Then does the system recognize the hardware
then is a driver loaded
then how does the the hardware, system, kernel interface ?

[INDENT][INDENT]we want to see
[/INDENT][/INDENT]

---

### Post by james176 on 2015-11-01
Hey! Almost resigned to admit hardware 99%.... Happy to check out BIOS and follow your lead Bashing om, am away from the machine until Monday evening when I can continue efforts. Thank you to all who have offered their much valued insight. Cheers!

[COLOR=#000000]Sony Vaio VPC-F22M0E[/COLOR]

Screen 16.4 inch, 1600x900
Graphics NVIDIA GeForce GT 540M
Processor Intel Core i7 2630QM @ 2.00 GHz
Memory 8GB
Hard disk 500GB


Optical drive DVD/RW


Webcam Yes
Card reader Yes
WiFi Yes
Extras Bluray, SD Card reader, 
USB, 2xUSB3, LAN, VGA, HDMI, Firewire Specs Sony VAIO F Series:
Specs Intel Core i7 2630QM/2GHz 4GB DDR3 SDRAM, 1333 MHz Serial ATA, 500 GB, Serial ATA-300, 5400rpm DVD±RW (±R DL)/DVD-RAM/BD-ROM 16.4" TFT, 1600x900 (WXGA++), 16:9 NVIDIA GeForce GT 540M 1.31 Megapixel webcam Touchpad, backlit keyboard IEEE 802.11b/g/n, Bluetooth 3.0 USB, 2x SuperSpeed USB 3.0, FireWire microphone, input, mini-phone stereo 3.5 mm Ethernet 10Base-T/100Base-TX/1000Base-T, RJ-45 Lithium Ion battery 399x272x33mm 3.1kg
Screen 16.4 inch, 1600x900
Graphics NVIDIA GeForce GT 540M
Processor Intel Core i7 2630QM @ 2.00 GHz
Memory 8GB
Hard disk 500GB


Optical drive DVD/RW


Webcam Yes
Card reader Yes
WiFi Yes
Extras Bluray, SD Card reader, 
USB, 2xUSB3, LAN, VGA, HDMI, Firewire Specs Sony VAIO F Series:
Specs Intel Core i7 2630QM/2GHz 4GB DDR3 SDRAM, 1333 MHz Serial ATA, 500 GB, Serial ATA-300, 5400rpm DVD±RW (±R DL)/DVD-RAM/BD-ROM 16.4" TFT, 1600x900 (WXGA++), 16:9 NVIDIA GeForce GT 540M 1.31 Megapixel webcam Touchpad, backlit keyboard IEEE 802.11b/g/n, Bluetooth 3.0 USB, 2x SuperSpeed USB 3.0, FireWire microphone, input, mini-phone stereo 3.5 mm Ethernet 10Base-T/100Base-TX/1000Base-T, RJ-45 Lithium Ion battery

---

### Post by Bashing-om on 2015-11-02
james176; Hey !

Impressive little box you have there, should run ubuntu just fine !
So we still have a graphic's driver issue ... huh ?
A few things we can do yet to isolate the problem.

Boot to the grub boot menu in the install ( as soon as the bios screen clears depress and hold  a shift key ) ; advanced options -> recovery -> "resume normal boot" .
Do you get a usable GUI ? ... degraded graphics at this point is OK .

If we have a usable GUI at this point, we consider again cleaning up the system from prior attempts to install a graphics driver, and try to properly install the Nvidia driver.

Else; well we boot to terminal and see what the system then looks like.

[INDENT]'til we find the cause
[INDENT][INDENT][INDENT]there ain't no quit
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by james176 on 2015-11-02
Hey Bashing Om

I followed your instructions to grub menu, no graphics issues, resumed to normal - still no graphics issues. This is really strange, before I went home for the weekend it was having the usual issues, now it isn't.

odd.

---

### Post by Bashing-om on 2015-11-02
james176; Welp ...

Now that is good news .. we DO have a driver issue !
The reason the GUI now behaves is the 'recovery mode' disables KMS (Kernel Mode Setting) and as such the kernel's graphic's driver is loaded.

So we are back to cleaning up the system from prior attempts to install a driver .. and then properly install a driver to handle the load you will place on the system with games and what-not .

So, with this in mind, the next small step is to look and see what is presently installed we want to remove :
```

cat /sys/module/nvidia/version
cat /proc/driver/nvidia/version
ls -ld /lib/nvidia*
cat /etc/modprobe.d/nvidia-graphics-drivers.conf
cat /etc/X11/xorg.conf 
sudo find / -name "NVIDIA-Linux-*"

```

And we see where we go from here .

[INDENT][INDENT]might be doable
[/INDENT][/INDENT]

---

### Post by james176 on 2015-11-02
This is fascinating. Thanks.
```
james@james-VPCF22M0E:~$ cat /sys/module/nvidia/version
cat: /sys/module/nvidia/version: No such file or directory
james@james-VPCF22M0E:~$ cat /proc/driver/nvidia/version
cat: /proc/driver/nvidia/version: No such file or directory
james@james-VPCF22M0E:~$ ls -ld /lib/nvidia*
ls: cannot access /lib/nvidia*: No such file or directory
james@james-VPCF22M0E:~$ cat /etc/modprobe.d/nvidia-graphics-drivers.conf
cat: /etc/modprobe.d/nvidia-graphics-drivers.conf: No such file or directory
james@james-VPCF22M0E:~$ cat /etc/X11/xorg.conf 
cat: /etc/X11/xorg.conf: No such file or directory
james@james-VPCF22M0E:~$ sudo find / -name "NVIDIA-Linux-*"cat /sys/module/nvidia/version

```

---

### Post by Bashing-om on 2015-11-02
james176; Hey hey !

So far so good ... does not appear there is any Nvidia files on the system.
One last thing to check - that I forgot -
```

dpkg -l | grep -i nvidia 

```

Then we see what happens when we have the system auto install the driver .

[INDENT][INDENT]it could happen
[/INDENT][/INDENT]

---

### Post by james176 on 2015-11-02
cool.

```
james@james-VPCF22M0E:~$ dpkg -l | grep -i nvidia
james@james-VPCF22M0E:~$ 

```

will autoinstall be ok? I think that last time autoinstall caused the computer to become very difficult to use, i dont know, you're the expert out of the two of us!

---

### Post by Bashing-om on 2015-11-02
james176; Welll ...

In this case I trust and have the greater faith in he system as opposed to my own thoughts.

As there is no vestige of 'nvidia' presently ..
Next is to see if the hardware is now seen :
```

sudo ubuntu-drivers devices
sudo ubuntu-drivers list

```

If/when that returns in a positive manner.
Then we have the system do it's thing.

[INDENT][INDENT]look'n more positive
[INDENT][INDENT][INDENT]alla the time
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by james176 on 2015-11-02
```

james@james-VPCF22M0E:~$ sudo ubuntu-drivers devices
[sudo] password for james: 
Sorry, try again.
[sudo] password for james: 
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd00000DF4sv0000104Dsd00009089bc03sc00i00
vendor   : NVIDIA Corporation
model    : GF108M [GeForce GT 540M]
driver   : nvidia-340-updates - distro non-free
driver   : nvidia-346-updates - distro non-free
driver   : nvidia-346 - distro non-free recommended
driver   : nvidia-304-updates - distro non-free
driver   : nvidia-304 - distro non-free
driver   : nvidia-340 - distro non-free
driver   : xserver-xorg-video-nouveau - distro free builtin

james@james-VPCF22M0E:~$ sudo ubuntu-drivers list
nvidia-340-updates
nvidia-340
nvidia-304-updates
nvidia-346-updates
nvidia-304
nvidia-346

```

---

### Post by Bashing-om on 2015-11-02
james176; Yepper;

System sees the hardware, and identifies what drivers are available ... look'n good !

Next in my slow plodding thought process is the make sure this freah clean install is all up to date with all the latest software :
```

sudo apt update
sudo apt upgrade
sudo apt full-upgrade

```

When these complete - with no errors ! - then we have the system install the driver;
```

sudo ubuntu-drivers autoinstall

```

when that completes, and the driver is installed;
verify that Nvidia's control file was generated, this file now exists:
```

ls -al /etc/X11/xorg.conf

``` IF this file exists ;

ReBoot the system and let's see the effect .

[INDENT][INDENT]it could happen
[/INDENT][/INDENT]

---

### Post by james176 on 2015-11-02
```
james@james-VPCF22M0E:~$ sudo apt update
[sudo] password for james: 
Ign http://gb.archive.ubuntu.com trusty InRelease                              
Hit http://security.ubuntu.com trusty-security InRelease                       
Ign http://extras.ubuntu.com trusty InRelease  
Get:1 http://gb.archive.ubuntu.com trusty-updates InRelease [64.4 kB]   
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://security.ubuntu.com trusty-security/main Sources                    
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://security.ubuntu.com trusty-security/restricted Sources              
Hit http://extras.ubuntu.com trusty/main amd64 Packages                     
Hit http://security.ubuntu.com trusty-security/universe Sources                
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://security.ubuntu.com trusty-security/multiverse Sources              
Get:2 http://gb.archive.ubuntu.com trusty-backports InRelease [64.5 kB]        
Hit http://security.ubuntu.com trusty-security/main amd64 Packages             
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages       
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages         
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages       
Hit http://security.ubuntu.com trusty-security/main i386 Packages              
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages        
Hit http://gb.archive.ubuntu.com trusty Release.gpg                            
Hit http://security.ubuntu.com trusty-security/universe i386 Packages          
Get:3 http://gb.archive.ubuntu.com trusty-updates/main Sources [242 kB]        
Ign http://extras.ubuntu.com trusty/main Translation-en_GB                     
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages        
Hit http://security.ubuntu.com trusty-security/main Translation-en         
Ign http://extras.ubuntu.com trusty/main Translation-en                    
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en   
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Get:4 http://gb.archive.ubuntu.com trusty-updates/restricted Sources [4,722 B]
Get:5 http://gb.archive.ubuntu.com trusty-updates/universe Sources [143 kB]
Get:6 http://gb.archive.ubuntu.com trusty-updates/multiverse Sources [5,145 B]
Get:7 http://gb.archive.ubuntu.com trusty-updates/main amd64 Packages [639 kB]
Get:8 http://gb.archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.4 kB]
Get:9 http://gb.archive.ubuntu.com trusty-updates/universe amd64 Packages [326 kB]
Get:10 http://gb.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [12.0 kB]
Get:11 http://gb.archive.ubuntu.com trusty-updates/main i386 Packages [619 kB]
Get:12 http://gb.archive.ubuntu.com trusty-updates/restricted i386 Packages [15.1 kB]
Get:13 http://gb.archive.ubuntu.com trusty-updates/universe i386 Packages [327 kB]
Get:14 http://gb.archive.ubuntu.com trusty-updates/multiverse i386 Packages [12.1 kB]
Hit http://gb.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://gb.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://gb.archive.ubuntu.com trusty-updates/restricted Translation-en      
Hit http://gb.archive.ubuntu.com trusty-updates/universe Translation-en        
Get:15 http://gb.archive.ubuntu.com trusty-backports/main Sources [7,541 B]    
Get:16 http://gb.archive.ubuntu.com trusty-backports/restricted Sources [28 B] 
Get:17 http://gb.archive.ubuntu.com trusty-backports/universe Sources [32.1 kB]
Get:18 http://gb.archive.ubuntu.com trusty-backports/multiverse Sources [1,898 B]
Get:19 http://gb.archive.ubuntu.com trusty-backports/main amd64 Packages [8,974 B]
Get:20 http://gb.archive.ubuntu.com trusty-backports/restricted amd64 Packages [28 B]
Get:21 http://gb.archive.ubuntu.com trusty-backports/universe amd64 Packages [38.3 kB]
Get:22 http://gb.archive.ubuntu.com trusty-backports/multiverse amd64 Packages [1,571 B]
Get:23 http://gb.archive.ubuntu.com trusty-backports/main i386 Packages [9,012 B]
Get:24 http://gb.archive.ubuntu.com trusty-backports/restricted i386 Packages [28 B]
Get:25 http://gb.archive.ubuntu.com trusty-backports/universe i386 Packages [38.3 kB]
Get:26 http://gb.archive.ubuntu.com trusty-backports/multiverse i386 Packages [1,552 B]
Hit http://gb.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://gb.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://gb.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://gb.archive.ubuntu.com trusty-backports/universe Translation-en      
Hit http://gb.archive.ubuntu.com trusty Release                                
Hit http://gb.archive.ubuntu.com trusty/main Sources                           
Hit http://gb.archive.ubuntu.com trusty/restricted Sources                     
Hit http://gb.archive.ubuntu.com trusty/universe Sources                       
Hit http://gb.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://gb.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://gb.archive.ubuntu.com trusty/restricted amd64 Packages              
Hit http://gb.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://gb.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://gb.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://gb.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://gb.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://gb.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://gb.archive.ubuntu.com trusty/main Translation-en_GB                 
Hit http://gb.archive.ubuntu.com trusty/main Translation-en                    
Hit http://gb.archive.ubuntu.com trusty/multiverse Translation-en_GB           
Hit http://gb.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://gb.archive.ubuntu.com trusty/restricted Translation-en_GB           
Hit http://gb.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://gb.archive.ubuntu.com trusty/universe Translation-en_GB             
Hit http://gb.archive.ubuntu.com trusty/universe Translation-en                
Fetched 2,628 kB in 10s (244 kB/s)                                             
Reading package lists... Done
james@james-VPCF22M0E:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  xserver-xorg-core-lts-vivid
1 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
Need to get 0 B/1,291 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 196011 files and directories currently installed.)
Preparing to unpack .../xserver-xorg-core-lts-vivid_2%3a1.17.1-0ubuntu3.1~trusty1_amd64.deb ...
Unpacking xserver-xorg-core-lts-vivid (2:1.17.1-0ubuntu3.1~trusty1) over (2:1.17.1-0ubuntu3~trusty1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up xserver-xorg-core-lts-vivid (2:1.17.1-0ubuntu3.1~trusty1) ...
james@james-VPCF22M0E:~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
james@james-VPCF22M0E:~$ sudo ubuntu-drivers autoinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  bbswitch-dkms dkms fakeroot lib32gcc1 libc6-i386 libcuda1-346 libfakeroot
  libvdpau1 nvidia-libopencl1-346 nvidia-opencl-icd-346 nvidia-prime
  nvidia-settings screen-resolution-extra
Suggested packages:
  bumblebee dpkg-dev debhelper nvidia-vdpau-driver vdpau-driver
The following NEW packages will be installed
  bbswitch-dkms dkms fakeroot lib32gcc1 libc6-i386 libcuda1-346 libfakeroot
  libvdpau1 nvidia-346 nvidia-libopencl1-346 nvidia-opencl-icd-346
  nvidia-prime nvidia-settings screen-resolution-extra
0 to upgrade, 14 to newly install, 0 to remove and 0 not to upgrade.
Need to get 75.9 MB of archives.
After this operation, 349 MB of additional disk space will be used.
Get:1 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libvdpau1 amd64 0.7-1ubuntu0.1 [23.9 kB]
Get:2 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main dkms all 2.2.0.3-1.1ubuntu5.14.04.5 [65.4 kB]
Get:3 http://gb.archive.ubuntu.com/ubuntu/ trusty/main libfakeroot amd64 1.20-3ubuntu2 [25.4 kB]
Get:4 http://gb.archive.ubuntu.com/ubuntu/ trusty/main fakeroot amd64 1.20-3ubuntu2 [55.0 kB]
Get:5 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libc6-i386 amd64 2.19-0ubuntu6.6 [2,206 kB]
Get:6 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/restricted libcuda1-346 amd64 346.96-0ubuntu0.0.1 [7,739 kB]
Get:7 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main lib32gcc1 amd64 1:4.9.1-0ubuntu1 [47.6 kB]
Get:8 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/restricted nvidia-346 amd64 346.96-0ubuntu0.0.1 [57.1 MB]
Get:9 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/restricted nvidia-libopencl1-346 amd64 346.96-0ubuntu0.0.1 [17.1 kB]
Get:10 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/restricted nvidia-opencl-icd-346 amd64 346.96-0ubuntu0.0.1 [7,829 kB]
Get:11 http://gb.archive.ubuntu.com/ubuntu/ trusty/main bbswitch-dkms amd64 0.7-2ubuntu1 [10.9 kB]
Get:12 http://gb.archive.ubuntu.com/ubuntu/ trusty/main nvidia-prime amd64 0.6.2 [11.2 kB]
Get:13 http://gb.archive.ubuntu.com/ubuntu/ trusty/main screen-resolution-extra all 0.17.1 [11.4 kB]
Get:14 http://gb.archive.ubuntu.com/ubuntu/ trusty/main nvidia-settings amd64 331.20-0ubuntu8 [774 kB]
Fetched 75.9 MB in 3min 16s (387 kB/s)                                         
Selecting previously unselected package libvdpau1:amd64.
(Reading database ... 196011 files and directories currently installed.)
Preparing to unpack .../libvdpau1_0.7-1ubuntu0.1_amd64.deb ...
Unpacking libvdpau1:amd64 (0.7-1ubuntu0.1) ...
Selecting previously unselected package dkms.
Preparing to unpack .../dkms_2.2.0.3-1.1ubuntu5.14.04.5_all.deb ...
Unpacking dkms (2.2.0.3-1.1ubuntu5.14.04.5) ...
Selecting previously unselected package libfakeroot:amd64.
Preparing to unpack .../libfakeroot_1.20-3ubuntu2_amd64.deb ...
Unpacking libfakeroot:amd64 (1.20-3ubuntu2) ...
Selecting previously unselected package fakeroot.
Preparing to unpack .../fakeroot_1.20-3ubuntu2_amd64.deb ...
Unpacking fakeroot (1.20-3ubuntu2) ...
Selecting previously unselected package libc6-i386.
Preparing to unpack .../libc6-i386_2.19-0ubuntu6.6_amd64.deb ...
Unpacking libc6-i386 (2.19-0ubuntu6.6) ...
Selecting previously unselected package libcuda1-346.
Preparing to unpack .../libcuda1-346_346.96-0ubuntu0.0.1_amd64.deb ...
Unpacking libcuda1-346 (346.96-0ubuntu0.0.1) ...
Selecting previously unselected package lib32gcc1.
Preparing to unpack .../lib32gcc1_1%3a4.9.1-0ubuntu1_amd64.deb ...
Unpacking lib32gcc1 (1:4.9.1-0ubuntu1) ...
Selecting previously unselected package nvidia-346.
Preparing to unpack .../nvidia-346_346.96-0ubuntu0.0.1_amd64.deb ...
Unpacking nvidia-346 (346.96-0ubuntu0.0.1) ...
Selecting previously unselected package nvidia-libopencl1-346.
Preparing to unpack .../nvidia-libopencl1-346_346.96-0ubuntu0.0.1_amd64.deb ...
Unpacking nvidia-libopencl1-346 (346.96-0ubuntu0.0.1) ...
Selecting previously unselected package nvidia-opencl-icd-346.
Preparing to unpack .../nvidia-opencl-icd-346_346.96-0ubuntu0.0.1_amd64.deb ...
Unpacking nvidia-opencl-icd-346 (346.96-0ubuntu0.0.1) ...
Selecting previously unselected package bbswitch-dkms.
Preparing to unpack .../bbswitch-dkms_0.7-2ubuntu1_amd64.deb ...
Unpacking bbswitch-dkms (0.7-2ubuntu1) ...
Selecting previously unselected package nvidia-prime.
Preparing to unpack .../nvidia-prime_0.6.2_amd64.deb ...
Unpacking nvidia-prime (0.6.2) ...
Selecting previously unselected package screen-resolution-extra.
Preparing to unpack .../screen-resolution-extra_0.17.1_all.deb ...
Unpacking screen-resolution-extra (0.17.1) ...
Selecting previously unselected package nvidia-settings.
Preparing to unpack .../nvidia-settings_331.20-0ubuntu8_amd64.deb ...
Unpacking nvidia-settings (331.20-0ubuntu8) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Setting up libvdpau1:amd64 (0.7-1ubuntu0.1) ...
Setting up dkms (2.2.0.3-1.1ubuntu5.14.04.5) ...
Setting up libfakeroot:amd64 (1.20-3ubuntu2) ...
Setting up fakeroot (1.20-3ubuntu2) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode
Setting up libc6-i386 (2.19-0ubuntu6.6) ...
Setting up libcuda1-346 (346.96-0ubuntu0.0.1) ...
Setting up lib32gcc1 (1:4.9.1-0ubuntu1) ...
Setting up nvidia-346 (346.96-0ubuntu0.0.1) ...
update-alternatives: using /usr/lib/nvidia-346/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-346/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/share/nvidia-346/glamor.conf to provide /usr/share/X11/xorg.conf.d/glamoregl.conf (glamor_conf) in auto mode
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia-346
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
Adding system user `nvidia-persistenced' (UID 116) ...
Adding new group `nvidia-persistenced' (GID 125) ...
Adding new user `nvidia-persistenced' (UID 116) with group `nvidia-persistenced' ...
Not creating home directory `/'.
Loading new nvidia-346-346.96 DKMS files...
First Installation: checking all kernels...
Building only for 3.19.0-31-generic
Building for architecture x86_64
Building initial module for 3.19.0-31-generic
Done.

nvidia_346:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.19.0-31-generic/updates/dkms/

nvidia_346_uvm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.19.0-31-generic/updates/dkms/

depmod........

DKMS: install completed.
Setting up nvidia-libopencl1-346 (346.96-0ubuntu0.0.1) ...
Setting up nvidia-opencl-icd-346 (346.96-0ubuntu0.0.1) ...
Setting up bbswitch-dkms (0.7-2ubuntu1) ...
Loading new bbswitch-0.7 DKMS files...
First Installation: checking all kernels...
Building only for 3.19.0-31-generic
Building initial module for 3.19.0-31-generic
Done.

bbswitch:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.19.0-31-generic/updates/dkms/

depmod....

DKMS: install completed.
Setting up nvidia-prime (0.6.2) ...
nvidia-prime start/running, process 8649
Setting up screen-resolution-extra (0.17.1) ...
Setting up nvidia-settings (331.20-0ubuntu8) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.19.0-31-generic
Processing triggers for ureadahead (0.100.0-16) ...
```
next bit coming...

```
james@james-VPCF22M0E:~$ ls -al /etc/X11/xorg.conf
ls: cannot access /etc/X11/xorg.conf: No such file or directory

```

---

### Post by Bashing-om on 2015-11-02
james176; Well ! and well again !

As the control file was not generated, (??) --- let's have nvidia generate one:
```

sudo nvidia-xconfig

```

"autoinstall" and no control file (Why not ?) goes a long way in explaining why the driver does not function !

does the file generate ?
```

ls -al /etc/X11/xorg.conf
cat /etc/X11/xorg.conf

```

Are we ready now
[INDENT][INDENT][INDENT]to ReBoot
[/INDENT][/INDENT][/INDENT]

---

### Post by james176 on 2015-11-02
ok....here's the 1st bit....
```
james@james-VPCF22M0E:~$ sudo nvidia-xconfig
[sudo] password for james: 

WARNING: Unable to locate/open X configuration file.

New X configuration file written to '/etc/X11/xorg.conf'


```

shall i carry on?

```
james@james-VPCF22M0E:~$ ls -al /etc/X11/xorg.conf
-rw-r--r-- 1 root root 1325 Nov  2 21:03 /etc/X11/xorg.conf
james@james-VPCF22M0E:~$ cat /etc/X11/xorg.conf
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 346.96  (buildmeister@swio-display-x64-rhel04-17)  Sun Aug 23 23:07:23 PDT 2015

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```

---

### Post by Bashing-om on 2015-11-02
james176; Huh ?

Yeah , looks to me like the file was generated .. now make sure that the control file really truly exists !
```

ls -al /etc/X11/xorg.conf
cat /etc/X11/xorg.conf

```
the ls -- 'list' to see that the file exists;
and 'cat' to see that it has content and we "might" want to examine that content.

[INDENT][INDENT]carry on, smartly
[/INDENT][/INDENT]

---

### Post by james176 on 2015-11-02
Following your lead mate
```
james@james-VPCF22M0E:~$ ls -al /etc/X11/xorg.conf
-rw-r--r-- 1 root root 1325 Nov  2 21:03 /etc/X11/xorg.conf
james@james-VPCF22M0E:~$ cat /etc/X11/xorg.conf
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 346.96  (buildmeister@swio-display-x64-rhel04-17)  Sun Aug 23 23:07:23 PDT 2015

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by Bashing-om on 2015-11-02
james176; Yepper !

Looks good !

Reboot now and
[INDENT][INDENT]let's see the effect
[/INDENT][/INDENT]

---

### Post by james176 on 2015-11-02
screen is doing some strange things. window keeps resizing. some areas of pixelation (like little blue patches, quite faint). boot up went well. interesting progress. Thanks for your continued support.

rebooted again, screen issues absent. window frequent resizing issue absent.

---

### Post by Bashing-om on 2015-11-02
james176; Hey ...

But is the GUI good ?

Artification "might" be in the translations of drivers as the system startup progresses .
Bios has a driver,
grub has a driver,
kernel has a driver,
GUI has a driver.

The end product is the 
[INDENT][INDENT][INDENT]focus of our interest
[/INDENT][/INDENT][/INDENT]

---

### Post by james176 on 2015-11-02
I think I can say the GUI is good, graphics wise, an improvement. New symptom, freezing and slowness.

the icons on the side bar are having graphics issues.

---

### Post by Bashing-om on 2015-11-02
james176; Yuk;

With your system specs " New symptom, freezing and slowness. " is unacceptable.

What does:
> 
the icons on the side bar are having graphics issues.

mean ? Please describe what you see and what happens when you select a icon (any/all icons demonstrate the same behavior ?) .

Maybe consider changing to the 340 version Nvidia driver .

[INDENT][INDENT]newer may not be better
[/INDENT][/INDENT]

---

### Post by james176 on 2015-11-02
All of the icons, as though bits of it go missing. Similar to previous screen issues. I selected the top left corner search utility, typed in "open off....", it froze, not allowing me to continue entering text. This lasted a few mins then resumed. At this point it was clear that there were issues with graphics and freezing type problems. I could select the Firefox icon, but all icons were "blurry" / pixelated / a mess. That help?

---

### Post by Bashing-om on 2015-11-02
james176; Yeah ...

Sure seems like a graphic's driver/hardware sloppyation.
OK, let's see what the logs have to say;
```

cat /var/log/Xorg.0.log
cat ~/.xsession-errors

```

Next up then after reading the above instructions, we see what the system has to say when we start the GUI from a terminal.

[INDENT][INDENT]no quit
[INDENT][INDENT]'til we know
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by james176 on 2015-11-03
Having trouble booting up, when it does boot up i got a browser woring but couldnt get a terminal working, it froze / crashed. am trying to get it going again.

---

### Post by Bashing-om on 2015-11-03
james176; K

Try'n to think how "recovery mode" or booting to terminal could help us in this situation.
We really want those logs from a 'normal' boot attempt though .

[INDENT][INDENT]trials troubles and tribulations
[/INDENT][/INDENT]

---

### Post by james176 on 2015-11-03
before reading your last post, i followed your prev steps to get the computer usable again "Boot to the grub boot menu in the install ( as soon as the bios screen  clears depress and hold  a shift key ) ; advanced options -> recovery  -> "resume normal boot"- i hope thats ok / not a hindrance?...this didnt work anyway. i'll try a normal boot.

repeated attempts at a normal boot up are failing. what do you advise? thanks for being online again this eve!

---

### Post by Bashing-om on 2015-11-03
james176; Well !!

Let's try and boot to terminal, then start the GUI - observing the terminal for reported errors.
You do have 14.04.3 install, correct ?

boot the install, and as soon as the bios screen clears ( hey this box, it is UEFI or BIOS based ? ; UEFI may make a huge difference) -
depress and hold a shift key -> grub boot menu
with the normal kernel selected as the booting kernel press the 'e' key for edit mode -> boot parameters screen.
Arrow down to the line starting with linux, and containing "quiet splash" , replace "quiet splash" with the term "text" - without the quotes - and remove all after so you have similar " linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=217ed9a7-e11a-4e32-8c05-992e8c8932b6 ro text " .
Key combo ctl+x to continue the boot process to terminal TTY1.
Login to the system here with username and password - there is no response to the screen when password is entered - enter password blindly and hit the enter key .
Once logged in .. what results when you start the GUI:
```

sudo service lightdm start

```
Paying attention here to what errors the system reports.

[INDENT][INDENT]see what we can learn
[/INDENT][/INDENT]

---

### Post by james176 on 2015-11-03
i did the above! its now a black screen with the underscore/cursor flashing in the top left corner.....

ah... i did it wrong.... wait out....

same result - black screen

FYI

linux    /boot/vmlinuz-3.19.0-31-generic root=UUID=37fab687-\885a-457b-9f29-a8607e340298 ro quiet splash $vt_handoff

thats what was on that line, so perhaps different version to what you thought?

---

### Post by howefield on 2015-11-03
Thread closed.... 

..and reopened.

---

### Post by Bashing-om on 2015-11-03
james176; HUMM ....

Let's try that boot parameter once more, and this time leave the $vt_handoff in place. Maybe we need it to hand off to a (V)irtual (T)erminal ?
```

linux /boot/vmlinuz-3.19.0-31-generic root=UUID=37fab687-\885a-457b-9f29-a8607e340298 ro text $vt_handoff

```

else .. well is the file system corrupted ?

[INDENT][INDENT]strange things can happen.
[/INDENT][/INDENT]

---

### Post by james176 on 2015-11-04
Hi. machine booted up fine first time today.
```
james@james-VPCF22M0E:~$ sudo service lightdm start
[sudo] password for james: 
start: Job is already running: lightdm
```

[ATTACH=CONFIG]265359[/ATTACH]

---

### Post by Bashing-om on 2015-11-04
james176; Morning.

That " start: Job is already running: lightdm " is a result of NOT booting to terminal from grub, and then once in terminal starting the GUI. When one logs in from the GUI login screen, the GUI is automagically started by the system. IF there are still problems with the display, It will behoove us to see the errors the system reports (Boot to terminal ).

I do much prefer to look at this from the perspective of what I expect to happen and then what really does happen. Else, I will follow your thought process and see what we can determine. However, If I can not follow what you are doing I can offer no advise.

Be advised this forum also functions as a institute of higher learning. If at any time you "want to know" or do not understand ; please ask for clarification. It has been many years since I began my own journey, and the little things I take for granted, and overlook in our relating, may be important in establishing your foundation of comprehension. We are never to busy to instruct and tell why and what we are doing.

And believe me, the more I learn, the more I realize how much I do not know ... This system is constantly evolving and no one person knows it all . 

[INDENT][INDENT]which way did he go, George
[/INDENT][/INDENT]

---

### Post by james176 on 2015-11-05
That's very well put Bashing-om, thank you for the higher learning; it's much needed here.

Following your lines of investigation, and trying not to deviate from them so that you may know what to expect etc... I started the machine and held done the shift key, edited the main kernel and altered the line you specified from "quiet splash" to "text".

I logged in when requested to do so and then entered the code you suggested:
```
sudo service lightdm start
```

The machine then immediately booted up to the GUI (correct me if I'm using the wrong terminology). The computer was unresponsive, I could not make use of or start any programs. No graphics glitches observed. I had to shut down by holding down the power button. The machine booted up normally after that and the display seems okay.

Thanks. James.

---

### Post by Bashing-om on 2015-11-05
james176; Well ...

Seems promising now, huh ?

On the learning curve:
> 
I had to shut down by holding down the power button.

Not a good thing to do as many files are left in an open condition, and file system corruption can and does result. There are "graceful" means to bring the system down.
Magic SysRq key method: hold down the Alt+SysRq keys and slowly run through the sequence R,E,I,S,U,B - after the B, your system will reboot (or if you want to shut it down, make the last letter o). For systems without a SysRq label on the key, it's the Prt Scr key.
Ubuntu distros all used to have this option natively, but if you want to see if yours has it, run
```
 cat /proc/sys/kernel/sysrq
```
If it returns a 1 (14.04 returns 176), you're in business. If not, you can edit the file /etc/sysctl.d/10-magic-sysrq.conf to set it to 1.
Mentonic: Raising Elephants IS Utterly Boring
See: [http://en.wikipedia.org/wiki/Magic_SysRq_key#Uses](http://en.wikipedia.org/wiki/Magic_SysRq_key#Uses) ; [http://unix.stackexchange.com/questions/31818/what-to-do-when-a-linux-desktop-freezes](http://unix.stackexchange.com/questions/31818/what-to-do-when-a-linux-desktop-freezes)

Let us run a simple file system check/repair.
Boot to terminal from the grub boot menu as before, login to the system and now run terminal commands:
```

sudo touch /forcefsck
sudo shutdown -r now

```
'touch' creates a file, and in this case if 'forcefsck' exists, a file system is run on next boot .
'shutdown -r' makes the reboot happen . where 'r' is 'reboot'; to bring the system down and shutoff ... ' sudo shutdown -h now '.

-------------------
So now when you boot up after running the file system check/repair .. does the system boot up to a good display ?

[INDENT][INDENT][INDENT]it could happen
[/INDENT][/INDENT][/INDENT]

---

### Post by james176 on 2015-11-05
The learning curve is steep but good and well appreciated.

I checked to see if that method of shutting down exists and got a 176, which is good! Thanks. 

I then booted up to the terminal, input the codes
```

sudo touch /forcefsck
sudo shutdown -r now
```

The check / repair went through, then the GUI was loaded. All looking good at this point, I opened the browser, then "freeze" type crashes began to occur, short duration ones at first then eventually a long one. 
Then I took the opportunity to practice a "graceful" reboot. It rebooted ok, but there are glitches and programs aren't opening.

---

### Post by Bashing-om on 2015-11-05
james176; Yuk !

That result is disappointing - to say the least.
I think now it is time to read the instructions and see what the log files relate to this situation.
Boot up normally to the login screen, here press key combo ctl+alt+F1 to gain a 'console' - Command Line Interface. In this environment the X layer is activated but the desktop is not - so let's look and see what the system reports for a status at this time. Here we do not have the amenities from a GUI terminal, and can not copy paste text. We do have a means available to us to see the requested log files. We have a pastebin site !
Install our tool:
```

sudo apt-get install pastebinit

```
Now we can redirect to the pastebin !
```

cat /var/log/Xorg.0.log | pastebinit
cat /var/log/syslog | pastebinit

```
where the output from 'cat' is "piped" ( that '|' operator ) to the site.
The result will be a URL, pass that link(s) back here and we will have access to the log file(s).
[try'n to make this as easy as possible, and still make sense]

We want to make sure we have a stable base system, and then look at the additional layers that get started .

[INDENT][INDENT]isolate the fault
[/INDENT][/INDENT]

---

### Post by james176 on 2015-11-05
Neat trick!

[http://paste.ubuntu.com/13114421/](http://paste.ubuntu.com/13114421/)

I'm enjoying the learning curve, perhaps not so much the use of my laptop! Fingers crossed.

---

### Post by Bashing-om on 2015-11-05
james176; Yeah ...

We been araound a while ... have learned a thing or two - it was, after all linux in the beginning.

Now as to your system - YUK !
I see:
> 
Nov  4 16:40:41 james-VPCF22M0E kernel: [    0.415117] mtrr: your CPUs had inconsistent variable MTRR settings
Nov  4 16:40:41 james-VPCF22M0E kernel: [    0.415118] mtrr: probably your BIOS does not setup all CPUs.
Nov  4 16:40:41 james-VPCF22M0E kernel: [    0.415119] mtrr: corrected configuration.
-bk-
Nov  4 16:40:41 james-VPCF22M0E kernel: [    0.424235] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
-bk-
Nov  4 16:40:41 james-VPCF22M0E kernel: [    1.829022] ACPI PCC probe failed.
-bk-
Nov  4 16:40:41 james-VPCF22M0E failsafe: Failsafe of 120 seconds reached.
-bk-
4 16:40:41 james-VPCF22M0E kernel: [    9.823137] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
-bk-
Nov  4 16:40:41 james-VPCF22M0E nvidia-persistenced: Failed to query NVIDIA devices. Please ensure that the NVIDIA device files (/dev/nvidia*) exist, and that user 116 has read and write permissions for those files.
-bk-
Nov  4 16:40:41 james-VPCF22M0E nvidia-persistenced: Shutdown (1044)
-bk-
Nov  4 17:34:16 james-VPCF22M0E kernel: [ 3224.864246] NVRM: Xid (PCI:0000:01:00): 69, Class Error: ChId 0003, Class 00009197, Offset 00002480, Data 3c5f1928, ErrorCode 0000000c
-bk-
Nov  4 17:41:54 james-VPCF22M0E kernel: [ 3682.031180] ACPI Warning: \_SB_.PCI0.PEGP.NGFX._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)
-bk-
-bk-
Nov  5 12:54:03 james-VPCF22M0E kernel: [    7.772564] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  346.96  Sun Aug 23 22:29:21 PDT 2015
-bk-

What is reflected in the syslog file is 4 boots, the last boot is much cleaner than the 1st ... hummm .. so what is different ? But still with problems.

I do think -- and will not hurt my feelings a bit to let this set a couple of days for others to have time to view and offer an opinion - that 
a) run a memtest from the liveDVD, and let it run overnight .. see if any errors are reported .
b) Back to the thought to revert bios back to defaults. consult the manual on the proper procedure !

Meanwhile, what is in the Xorg.0.log file ? Be good to see what X is relating to us .

Looks to me like the system is not happy with what bios is passing to it . Bear in mind, there is bunches I do not know .. and other opinions here are welcome.

but I do think ->
[INDENT][INDENT]this is what I would do
[/INDENT][/INDENT]

---

### Post by james176 on 2015-11-05
Ok, I think I understand. That must have taken  you some diggin there, nice one!

Now, do you want me to enter "Xorg.0.log" file into a terminal?

And may I ask, does this mean it's a software issue, and hardware can be ruled out?

Many thanks.

---

### Post by Bashing-om on 2015-11-05
james176; Well .. 

I still will not say this is a hardware issue . I have yet to see definitive proof. I would rather think that the former owner of this box messed about with bios, and 'somethings' are not set . The system just is not happy with what bios is passing it . However a memtest would be a good thing to do to KNOW memory is in good shape .

Xorg log file:
```

cat /var/log/Xorg.0.log | pastebinit

```
to see the state of X when the system is booted up . That log file is created anew at each boot up . Older boots logs are represented as Xorg.0.log.old, Xorg.1.log .. depending on cron settings, there may even exist compressed Xorg logs .

The directory  /var/log/ is the central location of log files. Many other logs may be kept in many other places  .. just depends.
```

ls -al /var/log/

```
to get an idea of all that the system tracks for you ..
" [color=red]d[/color]rwxr-xr-x  2 root   root      4096 Nov  1 07:13 apt "
that leading 'd' denotes this is a directory containing other files and/or directories . Logging can get deep .. The great thing here, is if You have a need to know what the system is doing , it is logged, somewhere .

[INDENT][INDENT]reading
[INDENT][INDENT][INDENT][INDENT]is a good thing
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by james176 on 2015-11-05
That's good clinical thinking right there mate.
```

james@james-VPCF22M0E:~$ cat /var/log/Xorg.0.log | pastebinit
http://paste.ubuntu.com/13115994/
```

```
james@james-VPCF22M0E:~$ ls -al /var/log/
total 10804
drwxrwxr-x 13 root              syslog    4096 Nov  5 21:22 .
drwxr-xr-x 13 root              root      4096 Aug  5 06:25 ..
-rw-r--r--  1 root              root     30938 Nov  2 20:43 alternatives.log
-rw-r-----  1 root              adm        773 Nov  4 17:41 apport.log
-rw-r-----  1 root              adm      14376 Nov  4 16:19 apport.log.1
drwxr-xr-x  2 root              root      4096 Oct 30 11:18 apt
-rw-r-----  1 syslog            adm     119305 Nov  5 21:22 auth.log
-rw-r--r--  1 root              root       412 Nov  5 21:22 boot.log
-rw-r--r--  1 root              root     61499 Aug  5 06:12 bootstrap.log
-rw-rw----  1 root              utmp       384 Nov  3 19:44 btmp
drwxr-xr-x  2 root              root      4096 Nov  4 16:36 cups
drwxr-xr-x  2 root              root      4096 Feb  4  2015 dist-upgrade
-rw-r-----  1 root              adm      60189 Nov  5 21:22 dmesg
-rw-r-----  1 root              adm      60579 Nov  5 18:23 dmesg.0
-rw-r-----  1 root              adm      16023 Nov  5 17:34 dmesg.1.gz
-rw-r-----  1 root              adm      16164 Nov  5 17:28 dmesg.2.gz
-rw-r-----  1 root              adm      16275 Nov  5 17:21 dmesg.3.gz
-rw-r-----  1 root              adm      16184 Nov  5 13:14 dmesg.4.gz
-rw-r--r--  1 root              root   1428945 Nov  5 18:25 dpkg.log
-rw-r--r--  1 root              root     32032 Nov  2 20:43 faillog
-rw-r--r--  1 root              root      3281 Aug  5 06:19 fontconfig.log
drwxr-xr-x  2 root              root      4096 Aug  5 06:12 fsck
-rw-r--r--  1 root              root      1394 Nov  5 21:22 gpu-manager.log
drwxr-xr-x  3 root              root      4096 Aug  5 06:16 hp
drwxrwxr-x  2 root              root      4096 Oct 30 11:26 installer
-rw-r-----  1 syslog            adm    3550004 Nov  5 21:24 kern.log
-rw-rw-r--  1 root              utmp    292292 Nov  5 18:24 lastlog
drwxr-xr-x  2 root              root      4096 Nov  5 21:22 lightdm
-rw-r--r--  1 root              root        55 Nov  5 21:22 nvidia-prime-upstart.log
-rw-r--r--  1 root              root     48333 Nov  5 21:22 pm-powersave.log
-rw-r--r--  1 root              root        55 Nov  5 21:22 prime-offload.log
-rw-r--r--  1 root              root        30 Nov  5 21:22 prime-supported.log
drwxr-x---  2 root              adm       4096 Jul  1 16:37 samba
drwx------  2 speech-dispatcher root      4096 Feb 19  2014 speech-dispatcher
-rw-r-----  1 syslog            adm    1362783 Nov  5 21:24 syslog
-rw-r-----  1 syslog            adm    3466208 Nov  4 16:36 syslog.1
-rw-r--r--  1 root              root    327216 Nov  5 21:22 udev
drwxr-xr-x  2 root              root      4096 Oct 30 11:35 unattended-upgrades
drwxr-xr-x  2 root              root      4096 Nov  4 17:42 upstart
-rw-rw-r--  1 root              utmp    212352 Nov  5 21:23 wtmp
-rw-r--r--  1 root              root     27405 Nov  5 21:24 Xorg.0.log
-rw-r--r--  1 root              root     24017 Nov  5 19:13 Xorg.0.log.old
-rw-r--r--  1 root              root     10733 Nov  3 20:14 Xorg.failsafe.log
-rw-r--r--  1 root              root     10733 Nov  3 19:57 Xorg.failsafe.log.old
```

Is this what you would like me to do next? [https://help.ubuntu.com/community/MemoryTest](https://help.ubuntu.com/community/MemoryTest)

---

### Post by Bashing-om on 2015-11-05
james176; Well ...

X appears to be real happy. likes Nvidia and builds and loads the Nvidia driver, not a whimper at all.
From X's perspective, all is good.
From this output, one would expect an excellent display .

So, we are back to bios ( and maybe a boot parameter to compensate for the ACPI errors - maybe !).
However, at this time we need to reset bios to the default configuration
and
.. run the memtest overnight.
Yeah that link is somewhat appropriate .. the option I think now is under advanced options in the install ... and I can see where running the test from the install might give a better result . Rather though than a single pass .. let it run overnight to have several passes.

Then we see what the system does .

[INDENT][INDENT]best I can say
[/INDENT][/INDENT]

---

### Post by james176 on 2015-11-05
ok
I've reset the BIOS to default, and I'm going to run the memtest overnight as suggested.
Could you elaborate on your suggestion regarding "the option I think now is under advanced options in the install" please. Thanks.

---

### Post by Bashing-om on 2015-11-05
james176; Sure;

In the grub boot menu I expect there to be "advanced options" - or some such heading. -> selecting this option should bring up the next screen containing the test utility.
I do not run a standard install, and my grub is customized to my use - so I do not have a ready means to confirm and my memory is a bit hazy on this.

Boot to grub and look around, you will find the memory test utility .

[INDENT][INDENT]all things are not equal, even in 14.04 installs
[/INDENT][/INDENT]

---

### Post by Mike_Walsh on 2015-11-06
@Bashing-Om, james176:-

A thought. Bashing's by far & away the better out of the two of us at software....I'm just a scratcher by comparison; I tend to be better at the hardware side of things. However...

Check the ACPI settings, in your BIOS. This is one of the few areas that tend to get messed about with, by amateur & expert alike. Difference is, the 'expert' has some idea what he's doing, and what he's trying to achieve; the amateur usually doesn't; they tap, and poke.....and hope.

With laptops, the ACPI settings control just about every aspect of the power management system (and are much more tightly integrated with the system as a whole, to a **far** greater degree than a desktop PC).....and this, along with Bashing's suspicion about the BIOS being 'tampered with', is starting to smell very fishy. This includes controlling what the laptop does when the lid's closed; and this is one of those questions we see again & again on the forums. Ex-Windows users bitching because their laptop won't behave identically under Ubuntu as it does under Windows; so they start 'playing around', altering this, changing that....and usually end up making a right 'dog's dinner' of it. 

"A little knowledge is a dangerous thing....." It's one of the very few occasions where the advice often given on the forums ("Have a good dig around before you post yourself") just occasionally backfires. People 'dig', find a solution to something which sounds vaguely like their own problem, & start 'experimenting'....with sometimes 'terminal' (sic) results. It does pay, really, to post your own thread, as you have done.....so as to get advice tailored, as far as possible, for your **own** problem.

They then end up somehow making it run **just** well enough to be able to stick some kind of OS on it (any kind!), so's they can flog it. Personally, I suspect the previous owner messed around with the ACPI (or related settings) in the BIOS.....and wasn't too certain what they were doing. As I say, it's just an idea.....but perhaps worth pursuing?

I could, of course, be totally wrong. I frequently am! Over to you.....


Regards,

Mike. ;)

---

### Post by james176 on 2015-11-09
Hi Mike, thanks for reading this thread and joining in :-)

Hi Bashing-Om, I reset the BIOS and ran the mem test overnight which completed 6 passes, no errors detected. 

Re: ACPI, interestingly on booting up the machine an error msg does poo up reporting an error with an ACPI probe (or a similar message, I can confirm later today). I will happily follow guidance for investigation that error. I will be back in front of this faulty machine in approx 6hours. 

Thank you very much guys. 
James.

---

### Post by Bashing-om on 2015-11-09
james176; Hey ...

All to the good then .
Let's look at this as an issue in  ACPI :
Advanced Configuration and Power Interface. It provides a way for the PC firmware (UEFI/BIOS) to declare to an Operating System how to control its platform-specific hardware.  ACPI provides several in-firmware 'tables'. One such is the Differentiated Services Description Table (DSDT). This actually contains executable code in a special ACPI 'language' which the OS has to execute.

```

sudo strings /sys/firmware/acpi/tables/DSDT | grep -i windows

```
Let us consider changing this interface language . Many laptop manufacturers just do not consider linux !

[INDENT][INDENT]change can be good
[/INDENT][/INDENT]

---

### Post by james176 on 2015-11-09
Cheers Bashing-om
```

windows 2001
windows 2001 SP1
windows 2001 SP2
windows 2001.1
windows 2006
windows 2009
```

The message about the ACPI failure often looks like this:
"[1.817235] ACPI PCC probe failed."

---

### Post by Bashing-om on 2015-11-09
james176; K,

Let's test, and this is only a test.

reboot the PC, hold down Shift to get the GRUB boot menu. highlight the default entry, press 'E' to edit it, navigate to the line starting "linux ..." ... where you see "quiet splash" insert BEFORE those the string (including double-quotations) "acpi_osi=Windows 2009"   - then press Ctrl+X or F10    immediately to boot with that change.
Make it like so:
```

"  "acpi_osi=Windows 2009" quiet splash"

```
4 quotation marks, they are important and required where they are .. syntax .. always syntax .
Where we change that interpretive "language" .

Test the system .. and if greatly improved..... we make it a permanent thing .

[INDENT][INDENT]maybe now finally YES
[/INDENT][/INDENT]

---

### Post by james176 on 2015-11-09
test result: display issues present.

---

### Post by Bashing-om on 2015-11-11
james176; Hey ;

Not forgotten, just nothing to add yet.
As you get a usable display with the 'nomodeset' boot parameter, and the system is fully functional it still points the finger at video issues.
Nvidia is well supported, so it is dismaying that the driver does not work and the xorg file does not indicate any problem.

Maybe we can garner some additional info from the system logs ?
```

cat /var/log/dmesg
cat /var/log/kern.log
cat /var/log/syslog

```

see what the system has to say ?

[INDENT][INDENT]just because I can not think
[INDENT][INDENT][INDENT]of a better thing to do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by james176 on 2015-11-11
Thank you for your persistent efforts with this frustrating problem.

```

cat /var/log/dmesg | pastebinit
http://paste.ubuntu.com/13232346/
cat /var/log/kern.log | pastebinit
http://paste.ubuntu.com/13232392/
cat /var/log/syslog | pastebinit
http://paste.ubuntu.com/13232406/
```
I hope this reveals something useful. Thanks. James.

---

### Post by Bashing-om on 2015-11-12
james176; Morning;

Ok, here goes what I find:
dmesg:
> 
0.000000] AGP: No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!

0.422065] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.422140] mtrr: probably your BIOS does not setup all CPUs.
[    0.422213] mtrr: corrected configuration.

0.431104] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored

1.270008] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug  ##<- Maybe we should take this advise !

 1.300095] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM

1.358532] vgaarb: setting as boot device: PCI:0000:01:00.0
[    1.358603] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    1.358697] vgaarb: loaded ## <- Looks good to me, we have display !

1.806264] usb usb2: We don't know the algorithms for LPM for this host, disabling LPM. ## <- WHAT have we here ??

1.846852] ACPI PCC probe failed. ## <- probably benign ??

1.860016] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found ## <- How old is this machine ? Should we consider updating bios ??

 7.272158] [Firmware Bug]: ACPI(NGFX) defines _DOD but not _DOS

 7.627850] nvidia: module license 'NVIDIA' taints kernel.
[    7.627853] Disabling lock debugging due to kernel taint
[    7.630705] nvidia: module verification failed: signature and/or  required key missing - tainting kernel ## <- UH Oh We do have a problem !

7.634555] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    7.634987] [drm] Initialized nvidia-drm 0.0.0 20150116 for 0000:01:00.0 on minor 0
[    7.634995] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  346.96  Sun Aug 23 22:29:21 PDT 2015


kernel.log:
> 
-------- Nov 10 18:11:10 james-VPCF22M0E kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-31-generic root=UUID=37fab687-885a-457b-9f29-a8607e340298 ro quiet splash
------------
 1525.766201] NVRM: os_schedule: Attempted to yield the CPU while in atomic or interrupt context

[ 1556.767814] NVRM: Xid (PCI:0000:01:00): 13, Graphics SM Warp Exception on (GPC 0, TPC 0): Out Of Range Register
Nov 10 17:23:47 james-VPCF22M0E kernel: [ 1556.767828] NVRM: Xid (PCI:0000:01:00): 13, Graphics SM Global Exception on (GPC 0, TPC 0): Physical Multiple Warp Errors

0.415444] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it0.415444] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it

0.416029] mtrr: probably your BIOS does not setup all CPUs.

9.607921] ACPI Warning: \_SB_.PCI0.PEGP.NGFX._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20141107/nsarguments-95)

35.186330] NVRM: Xid (PCI:0000:01:00): 13, Graphics SM Warp Exception on (GPC 0, TPC 0): Out Of Range Register
Nov 10 18:11:36 james-VPCF22M0E kernel: [   35.186344] NVRM: Xid (PCI:0000:01:00): 13, Graphics SM Global Exception on (GPC 0, TPC 0): Physical Multiple Warp Errors
Nov 10 18:11:36 james-VPCF22M0E kernel: [   35.186349] NVRM: Xid (PCI:0000:01:00): 13, Graphics Exception: ESR 0x504648=0xd 0x504650=0x4 0x504644=0x1beff2 0x50464c=0xf
Nov 10 18:11:36 james-VPCF22M0E kernel: [   35.186371] NVRM: Xid (PCI:0000:01:00): 13, Graphics SM Warp Exception on (GPC 0, TPC 1): Out Of Range Register
Nov 10 18:11:36 james-VPCF22M0E kernel: [   35.186376] NVRM: Xid (PCI:0000:01:00): 13, Graphics SM Global Exception on (GPC 0, TPC 1): Physical Multiple Warp Errors
Nov 10 18:11:36 james-VPCF22M0E kernel: [   35.186381] NVRM: Xid (PCI:0000:01:00): 13, Graphics Exception: ESR 0x504e48=0x1000d 0x504e50=0x4 0x504e44=0x1beff2 0x504e4c=0xf
Nov 10 18:11:36 james-VPCF22M0E kernel: [   35.186394] NVRM: Xid (PCI:0000:01:00): 13, Graphics Exception: ChID 0001, Class 00009197, Offset 00001b0c, Data 1000f010
Nov 10 18:11:36 james-VPCF22M0E kernel: [   35.209343] NVRM: Xid (PCI:0000:01:00): 13, Graphics SM Warp Exception on (GPC 0, TPC 0): Out Of Range Register
Nov 10 18:11:36 james-VPCF22M0E kernel: [   35.209352] NVRM: Xid (PCI:0000:01:00): 13, Graphics SM Global Exception on (GPC 0, TPC 0): Physical Multiple Warp Errors
Nov 10 18:11:36 james-VPCF22M0E kernel: [   35.209358] NVRM: Xid (PCI:0000:01:00): 13, Graphics Exception: ESR 0x504648=0x1000d 0x504650=0x4 0x504644=0x1beff2 0x50464c=0xf
Nov 10 18:11:36 james-VPCF22M0E kernel: [   35.209380] NVRM: Xid (PCI:0000:01:00): 13, Graphics SM Warp Exception on (GPC 0, TPC 1): Out Of Range Register
Nov 10 18:11:36 james-VPCF22M0E kernel: [   35.209385] NVRM: Xid (PCI:0000:01:00): 13, Graphics SM Global Exception on (GPC 0, TPC 1): Physical Multiple Warp Errors
Nov 10 18:11:36 james-VPCF22M0E kernel: [   35.209390] NVRM: Xid (PCI:0000:01:00): 13, Graphics Exception: ESR 0x504e48=0x1000d 0x504e50=0x4 0x504e44=0x1beff2 0x504e4c=0xf
Nov 10 18:11:36 james-VPCF22M0E kernel: [   35.209404] NVRM: Xid (PCI:0000:01:00): 13, Graphics Exception: ChID 0001, Class 00009197, Offset 00000100, Data 0fffcc00

----------Nov 11 22:26:29 james-VPCF22M0E kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-31-generic root=UUID=37fab687-885a-457b-9f29-a8607e340298 ro quiet splash
----------------------
8.783389] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042f conflicts with OpRegion 0x0000000000000400-0x000000000000047f (\PMIO) (20141107/utaddress-258)
Nov 11 22:26:29 james-VPCF22M0E kernel: [    8.783397] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Nov 11 22:26:29 james-VPCF22M0E kernel: [    8.783402] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20141107/utaddress-258)
Nov 11 22:26:29 james-VPCF22M0E kernel: [    8.783406] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Nov 11 22:26:29 james-VPCF22M0E kernel: [    8.783408] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20141107/utaddress-258)
Nov 11 22:26:29 james-VPCF22M0E kernel: [    8.783412] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Nov 11 22:26:29 james-VPCF22M0E kernel: [    8.783414] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20141107/utaddress-258)
Nov 11 22:26:29 james-VPCF22M0E kernel: [    8.783418] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Nov 11 22:26:29 james-VPCF22M0E kernel: [    8.783419] lpc_ich: Resource conflict(s) found affecting gpio_ich
Nov 11 22:26:29 

Nov 11 22:26:29 james-VPCF22M0E kernel: [    9.116525] Disabling lock debugging due to kernel taintNov 11 22:26:29 james-VPCF22M0E kernel: [    9.116525] Disabling lock debugging due to kernel taint

9.123322] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  346.96  Sun Aug 23 22:29:21 PDT 20159.123322] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  346.96  Sun Aug 23 22:29:21 PDT 2015

----------Nov 11 22:32:11 james-VPCF22M0E kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-31-generic root=UUID=37fab687-885a-457b-9f29-a8607e340298 ro quiet splash
------------------

*******seems same errors as before***********

---------Nov 11 22:34:39 james-VPCF22M0E kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-31-generic root=UUID=37fab687-885a-457b-9f29-a8607e340298 ro text
-------------------

Note .. booting to terminal here .. all we have is the ACPI warnings !------------


syslog:
> 
--------Nov 10 18:11:10 james-VPCF22M0E kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-31-generic root=UUID=37fab687-885a-457b-9f29-a8607e340298 ro quiet splash
------------------------

Nov 10 18:02:29 james-VPCF22M0E kernel: [ 3877.500367] SysRq : Emergency Sync ## <- what in the world happened here ??

*******still with ACPI warnings**********

7.912942] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  346.96  Sun Aug 23 22:29:21 PDT 2015

8:11:10 james-VPCF22M0E nvidia-persistenced: Failed to query NVIDIA devices. Please ensure that the NVIDIA device files (/dev/nvidia*) exist, and that user 116 has read and write permissions for those files.
Nov 10 18:11:10 james-VPCF22M0E nvidia-persistenced: The daemon no longer has permission to remove its runtime data directory /var/run/nvidia-persistenced
Nov 10 18:11:10 james-VPCF22M0E nvidia-persistenced: Shutdown (837)

----------Nov 10 19:49:30 james-VPCF22M0E kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-31-generic root=UUID=37fab687-885a-457b-9f29-a8607e340298 ro " acpi_osi=Windows" "2006 quiet splash"
--------------
********still with ACPI warnings**********

Nov 10 19:49:30 james-VPCF22M0E kernel: [    7.914754] nvidia: module license 'NVIDIA' taints kernel.
Nov 10 19:49:30 james-VPCF22M0E kernel: [    7.914763] Disabling lock debugging due to kernel taint

*******Nvidia errors continue for 346 driver*********
#####What is up with the emergency syncs ??##########
Nov 10 19:51:12 james-VPCF22M0E kernel: [  111.128224] SysRq : Emergency Sync

---------Nov 11 22:26:29 james-VPCF22M0E kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-31-generic root=UUID=37fab687-885a-457b-9f29-a8607e340298 ro quiet splash
----------------
Nov 11 22:26:29 james-VPCF22M0E kernel: [    1.344960] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none ## <- so far so good fir graphics hardware.

********still with ACPI warnings***********

*******Nvidia errors continue **************

-----------Nov 11 22:32:11 james-VPCF22M0E kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-31-generic root=UUID=37fab687-885a-457b-9f29-a8607e340298 ro quiet splash
-------------------

#######yeah, yeah .. ACPI warnings and Nvidia errors still present##########

----------Nov 11 22:34:39 james-VPCF22M0E kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-31-generic root=UUID=37fab687-885a-457b-9f29-a8607e340298 ro text
------------------


All I can say at this point is that bios and ACPI are not getting along .. AND the system is not happy with the Nvidia driver.

For now -- pending any other thought -
What returns:
```

sudo dmidecode -t bios

```

[INDENT][INDENT]does not look good for the home team
[/INDENT][/INDENT]

---

### Post by james176 on 2015-11-12
Thanks Bashing-om

```

sudo dmidecode -t bios | pastebinit
http://paste.ubuntu.com/13243194/

```

---

### Post by Bashing-om on 2015-11-13
james176; Well !

So much for my last thought that bios might need updating !

This has now gotten beyond my skill set, and we are both now in a learning mode.

More testing ... see if we can get a hint/clue of where the failure is ( ACPI is some kind of complex ):
Let's boot back to the grub boot parameter screen and this time rather than "  "acpi_osi=Windows 2009"

let's tell bios the truth and go  with the boot parameter :
```

acpi_osi="Linux"

```
and take a new look at the syslog file .. what changes are in the ACPI errors ?

[INDENT][INDENT]when I know better
[INDENT][INDENT][INDENT]I will do better
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Mike_Walsh on 2015-11-14
Hey, Bashing.

Hmm; 'tis an awkward one this, isn't it? I still say ACPI has been messed around with; and between me and thee, it's starting to look like this BIOS isn't even the original one for the machine. No **way** should it be throwing up **this** many errors. Somebody has been playing 'silly beggars' with this hardware, I feel.

I've got a horrible feeling this is going to end up a 'lost cause'.....but I'm willing yet to be proved wrong. Can't blame yourself; you've done everything **you **possibly can.

I've seen something like this once before, many years ago, back in the early 90's.. The machine in question had been used as a 'test-bed' for some **very** 'off-the-beaten-track' development stuff, and everything was being swapped around on a regular basis. And if you don't keep a very strict record of what's been altered where (and when), this kind of thing, unfortunately, can **all** too easily be the result.


Regards,

Mike. ;)

---

### Post by Bashing-om on 2015-11-14
@ Mike ...Hey ole friend .. Continued support is appreciated ...
And your views even more.

> **Mike_Walsh said:**
> Hey, Bashing.

Hmm; 'tis an awkward one this, isn't it? I still say ACPI has been messed around with; and between me and thee, it's starting to look like this BIOS isn't even the original one for the machine. No **way** should it be throwing up **this** many errors. Somebody has been playing 'silly beggars' with this hardware, I feel.

I've got a horrible feeling this is going to end up a 'lost cause'.....but I'm willing yet to be proved wrong. Can't blame yourself; you've done everything **you **possibly can.

I've seen something like this once before, many years ago, back in the early 90's.. The machine in question had been used as a 'test-bed' for some **very** 'off-the-beaten-track' development stuff, and everything was being swapped around on a regular basis. And if you don't keep a very strict record of what's been altered where (and when), this kind of thing, unfortunately, can **all** too easily be the result.


Regards,

Mike. ;)

@ james176; Backup and regroup.

Let's boot back in with the grub boot parameter 'nomodeset' to make sure we have not introduced additional problems. If you can still boot to a usable system - even with degraded graphics - then that will reinforce my concept that the issue is in the graphics layer . Maybe, all we have here is dust in the box, shorting out higher lever compositing ?? Clean the box .

Then we can see what results if/when we install the open source driver, or perhaps also try a different version of the proprietary driver.

Keep in mind, this too is a learning process for me as we seek to find the reason why.

[INDENT][INDENT]just do not know, yet
[/INDENT][/INDENT]

---

### Post by Mike_Walsh on 2015-11-14
Hi again, Bashing.

I can't speak from experience with this, as I've never owned a Vaio (in fact, I've never owned anything made by Sony, period!); as I said, I do know they have had 'issues' with the Vaio product line over the years.

You carry on with what **you're** best at :D ; I'm going to do some 'digging'. See what references, if any, I can unearth to do with this scenario in relation to the Vaios. Bear with me; I may be a while.....

EDIT: Well; almost straight away, on a Google search for 'Sony Vaio laptop graphics problems', I found this:-

[http://www.theinquirer.net/inquirer/news/1528907/sony-admits-failing-nvidia-chips-months-late](http://www.theinquirer.net/inquirer/news/1528907/sony-admits-failing-nvidia-chips-months-late)

And this is from 6-7 years ago. **Not** a good start! Looks like it **could** be hardware-related, after all. I'll keep digging....


Regards,

Mike. ;)

---

### Post by Bashing-om on 2015-11-14
@ Mike :)

As bios is from 2011, we redirect the focus.

Keep up your good work.

[INDENT][INDENT]ouch
[/INDENT][/INDENT]

---

### Post by Mike_Walsh on 2015-11-14
Hey, Bashing.

Well, now; too many references to quote here, but.....

The gist of it seems to be that the solder that Nvidia used in the manufacture of their graphics chips was the culprit. It had a higher than normal lead content, which gave it a lower than usual melting point, and the chips themselves ran far hotter than originally predicted (some references to individual chips reaching over 125C..!); you can guess what the rather obvious result of all this was.....especially inside laptops, which are not known for their excellent thermal solutions. Repeated heating & cooling cycles would first weaken, and then fracture the solder, and the chips, apparently, would begin to part company from the mother board..... with loss of contact, and subsequent loss of display.

Nvidia reckoned in 2010 that the problem was fixed once & for all, so.....you could well be right; with this having a later dated BIOS, it may be completely unrelated. Being the cynical old sod that I am, however, I **still** have my doubts..... :lol:

This post, on a forum set up at the time to help individuals file Small Claims against Nvidia, pretty much sums it up (scroll down to see the post):-

[http://www.nvidiadefect.com/what-exactly-is-the-nvidia-defect-t3.html](http://www.nvidiadefect.com/what-exactly-is-the-nvidia-defect-t3.html)

Furthermore, it appears that Nvidia were the recipients of a class action lawsuit, for violating the Federal Securities law.....leading to a record half a billion dollar fine, and subsequent 'tanking' of their share prices:-

[http://www.theinquirer.net/inquirer/news/1003508/nvidia-sued-violations-federal-securities-law](http://www.theinquirer.net/inquirer/news/1003508/nvidia-sued-violations-federal-securities-law)

Ya gotta realise that, as a Brit, this means absolutely zilch to me.....but at least you now know as much about the entire debacle as I do..! :)

How's **that** for detective work? :D


Regards,

Mike. ;)

---

### Post by Bashing-om on 2015-11-15
Hey Mike ! You said it :

> 
I tend to be better at the hardware side of things. However...


And ya done the homework

> 
How's that for detective work?


But remains, how to isolate and prove it is a hardware issue.

When you are good
[INDENT][INDENT][INDENT]you are good
[/INDENT][/INDENT][/INDENT]

---

### Post by Mike_Walsh on 2015-11-15
Hi, Bashing.

> **Bashing-om said:**
> But remains, how to isolate and prove it is a hardware issue.

That, old friend, is where** you** show **me** the way forward! Thou hast a touch more experience along those lines, I'll warrant...

> **Bashing-om said:**
> When you are good[INDENT][INDENT][INDENT]you are good
[/INDENT]
[/INDENT]
[/INDENT]


Hah! Now you're just embarrassing me...  :lol: If anyone can sort this out, I'll lay good money on it being **you**. Keep plugging...


Regards,

Mike. ;)

---

### Post by james176 on 2015-11-16
Hi Mike

Thanks ever so much for helping out. I feel this thread has continued quite far and as such it's easy to forget some of the original details of my computer problem. I could easily be wrong (if I wasn't likely to be wrong I probably wouldn't need much help fixing this laptop!) but these articles reporting defective Nvidia video cards don't apply to my model of laptop;

My laptop is a Sony Vaio VPC-F22M0E

Here's the list of Sony Vaio models affected:

VGN-FZ11x, VGN-FZ18x, VGN-FZ21x, VGN-FZ31x, VGN-FZ38x,

VGN-AR11x, VGN-AR21x, VGN-AR31x,

VGN-C1Zx, VGN-C2Zx,

VGC-LM1xx, VGC-LM2xx,

VGC-LT1xx, VGC-LT2xx.

However...... on the hardware vs software differentials note.... I think it necessary to remind ourselves that I was having 116 BSOD type crashes when this machine was running windows 7. Thats where my input ends on this topic. 

I hope that helps a little.

> **Bashing-om said:**
> 


@ james176; Backup and regroup.

Let's boot back in with the grub boot parameter 'nomodeset' to make sure  we have not introduced additional problems. If you can still boot to a  usable system - even with degraded graphics - then that will reinforce  my concept that the issue is in the graphics layer . Maybe, all we have  here is dust in the box, shorting out higher lever compositing ?? Clean  the box .

Then we can see what results if/when we install the open source driver,  or perhaps also try a different version of the proprietary driver.

Keep in mind, this too is a learning process for me as we seek to find the reason why.[INDENT][INDENT]just do not know, yet
[/INDENT]
[/INDENT]


Hi Bashing-om,
Once I've trained myself to dismantle the machine and clean the appropriate areas safely, I will so as suggested. Re - nomodeset boot - I'm unable to boot up this way. I followed the guide here [http://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu](http://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu) on how to do it. I just tried it a second time and the machine crashed after asking me to log in, whilst displaying graphics issues also.

Alos, re: 
sudo dmidecode -t bios
[http://paste.ubuntu.com/13299790/](http://paste.ubuntu.com/13299790/)

cheers

---

### Post by Bashing-om on 2015-11-16
james176; Welp ...

If you can not boot up to a terminal, we are dead in the water.
In the boot with nomodeset tutorial, let us drop down to a lower level yet .
Rather than adding the parameter 'nomodeset'  replace "quiet splash" with the term "text" - without the quotes. Key combo ctl+x to continue the boot process to a terminal, TTY1 .
Here can you log into the system - username and password ( no response to the screen when the password is entered, enter password blindly and hit the enter key ) ?

Here in TTY1 we are isolated from the graphical layer . It is not started at this time.

In regards to 'dmidecode' :
surprise surprise
> 
UEFI is supported

UEFI = Unified Extensible Firmware Interface. It replaces BIOS on the latest motherboards.
Is this an added level of complexity that we should be concerned with ?

How can we know what the firmware ( UEFI ) is passing off to the kernel ? Mind you I have no experience with this new type interface.
Will be a learning experience for all .

Let's see what results in booting to terminal . Then see what we can find out.

[INDENT][INDENT]If I know better
[INDENT][INDENT][INDENT]I would do better
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by james176 on 2015-11-16
Hey!
yes... Booting via adding "text" as a replacement to "quiet splash" works fine, and I can log in and enter codes okay.

---

### Post by Bashing-om on 2015-11-16
james176; Well, that is something .

Again, it appears the problems lie in the graphics layer .
To establish a baseline - do we still have ACPI errors in the logs ? - When booting to TTY1 .
Pastebin the outputs:
```

pastebinit /var/log/dmesg
pastebinit /var/log/kern.log
pastebinit /var/log/syslog

```
See if we can formulate a plan of where to go from here .

[INDENT][INDENT]oh boy; what to do, what to do
[/INDENT][/INDENT]

---

### Post by james176 on 2015-11-17
Hello there,

```

pastebinit /var/log/dmesg
http://paste.ubuntu.com/13317069/ 
pastebinit /var/log/kern.log 
http://paste.ubuntu.com/13317061/
pastebinit /var/log/syslog
http://paste.ubuntu.com/13317202/
```

Could it be a hardware and software issue?

---

### Post by Bashing-om on 2015-11-18
james176; Hey there;

I am still stuck, looking for a way forward. 


Edit #1: Do we want to compile the ACPI Tables ?? Now we are getting real deep !
 [https://forums.opensuse.org/showthread.php/502027-13-2-DMESG-Error-and-Warnings-Optimus-Laptop/page2](https://forums.opensuse.org/showthread.php/502027-13-2-DMESG-Error-and-Warnings-Optimus-Laptop/page2)

Edit #2:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1349740](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1349740)
> 
Hopefully these annoying messages can be suppressed because whilst one is looking for a REAL error these ones send him/her down a rabbit hole require hours of goggling update-initramfs and reboots only to discover a false-positive and move onto the next trial & error repair option.
 Kinda dis-heartening, implies this may take a long while !

> 
This error message occurs when the kernel runs the root PCI bridge _OSC control method in your firmware and the execution fails, perhaps due to a bug in the firmware or perhaps it does not exist. The kernel hence cannot determine the features supported or capabilities provided by the device (as specified by your firmware) and hence has to disable PCIe ASPM (Active State Power Management).

The downside of Active State Power Management not being enabled is that the machine is less power efficient, however, one can force this on with the kernel boot parameter "pcie_aspm=force" however, forcing this on may cause system lockups.

Colin Ian King (colin-king) wrote on 2015-10-09:	#18
So, just to add some more clarification, this is not a kernel bug, but a "feature" in your BIOS firmware and hence can't be fixed. The above notes do explain how to workaround this, but beware that it may not be a viable fix for your machine.
 Indicates we are with no other solution at this time (??)

Edit #3:
> 
Finally I tried to install again on UEFI instead of Legacy, problem solved.


When I know more
[INDENT][INDENT][INDENT]I will say more
[/INDENT][/INDENT][/INDENT]
---------------------
conclusion at this time:
Let's boot up (L)ubuntu release 15.10 . In this "try ubuntu" mode what now results in accordance to what the logs relate ? lubuntu has a different ACPI support structure. I do have some additional thoughts, but let's see how lubuntu performs out of the box .
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)
---------------------------------------

Hey, it could happen

---

