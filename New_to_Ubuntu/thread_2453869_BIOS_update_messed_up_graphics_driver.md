---
title: "BIOS update messed up graphics driver"
date: 2020-11-18
forum: New to Ubuntu
---

### Post by sakh on 2020-11-18
Hi,
I recently got an BIOS update for ASUS from my Windows partition (311 to 313). This messed up the graphics on my Linux partition. I am a newbie so please excuse me.
My laptop is ASUS X505ZA, with Ryzen 5 2500u, with Radeon Vega Graphics

```

[FONT=monospace][COLOR=#000000]$ inxi -G [/COLOR]
[COLOR=#5454ff]**Graphics:  Device-1:**[/COLOR][COLOR=#000000] AMD Raven Ridge [Radeon Vega Series / Radeon Vega Mobile Series] [/COLOR][COLOR=#5454ff]**driver:**[/COLOR][COLOR=#000000] N/A  [/COLOR]
           [COLOR=#5454ff]**Display:**[/COLOR][COLOR=#000000] x11 [/COLOR][COLOR=#5454ff]**server:**[/COLOR][COLOR=#000000] X.Org 1.20.8 [/COLOR][COLOR=#5454ff]**driver:**[/COLOR][COLOR=#000000] ati,fbdev [/COLOR][COLOR=#5454ff]**unloaded:**[/COLOR][COLOR=#000000] modesetting,radeon,vesa [/COLOR][COLOR=#5454ff]**resolution:**[/COLOR][COLOR=#000000] 1920x1080~77Hz  [/COLOR]
           [COLOR=#5454ff]**OpenGL:**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#5454ff]**renderer:**[/COLOR][COLOR=#000000] llvmpipe (LLVM 10.0.1 256 bits) [/COLOR][COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] 3.3 Mesa 20.1.5

```
[/COLOR]
And

```

[FONT=monospace][COLOR=#000000]$ vainfo  [/COLOR]
libva info: VA-API version 1.7.0 
libva error: vaGetDriverNameByIndex() failed with unknown libva error, driver_name = (null) 
vaInitialize failed with error code -1 (unknown libva error),exit

```

I tried reinstalling the AMDGPU drivers from the AMD website [https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-linux-20-10](https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-linux-20-10)

Please let me know if you require any other information!

Thank you!

[/FONT][/FONT]

---

### Post by ActionParsnip on 2020-11-18
If you uninstall the proprietary video driver, then reboot then reinstall it, does it help?

---

### Post by grahammechanical on 2020-11-18
> LLVMpipe is a Gallium3D graphics driver in Mesa that does all rendering  on the CPU for providing a software-accelerated fallback on Linux

[https://www.phoronix.com/scan.php?page=search&q=LLVMpipe](https://www.phoronix.com/scan.php?page=search&q=LLVMpipe)

I am guessing that you are running on LLVMPipe because the proprietary driver is not installed. Have you tried opening the Additional Driver tab in Software & Updates and allowing Ubuntu to search for a proprietary driver? Ubuntu will then install it for you.

If a UEFI/BIOS update has made this change then it might be worthwhile to check the UEFI/BIOS settings utility to see if something has been reset to default conditions. I am unfamiliar with your hardware, so I am also guessing that your system might have hybrid graphics or a combined CPU and graphic card in one integrated circuit chip that has the ability to switch output from a high power using mode to a low power using mode (switching between two different sets of video electronics)

Regards

---

### Post by sakh on 2020-11-18
Yes, I tried that, didn't change anything

---

### Post by sakh on 2020-11-18
I tried checking the proprietary drivers and it said, "No drivers available"
I checked the UEFI/BIOS but didn't find anything out of the ordinary, mind that I am not very used to this though. I didn't find any settings related to graphics, or power modes. And you're right, it is an integrated graphics.

---

### Post by Autodave on 2020-11-18
I am assuming that this is a laptop: correct?  Please give us the model #.

---

### Post by sakh on 2020-11-18
Exactly, this is a laptop, with model:
"VivoBook_ASUS Laptop X505ZA_X505ZA"

Is this what you wanted?

---

### Post by DuckHook on 2020-11-20
Please post the results of the following:
```
lsb_release -a
```
```
uname -a
```
```
cat /etc/default/grub
```
```
sudo lspci -vnn | grep -ia20 vga
```
```
ls -laH /etc/modprobe.d
```
```
cat /etc/modprobe.d/blacklist.conf
```
```
journalctl -b | egrep -i 'radeon|amdgpu' | egrep -i 'error|fail|kernel'
```
[list=1]
[*]Did you change any configs, settings or system files after the BIOS upgrade?
[*]What, exactly do you mean by "messed up the graphics"? You were able to post the diagnostics. How did you do that without video?
[*]Are you running Bionic or Focal? Whether you are or not, try booting from a LiveUSB of Focal.
[/list]

---

### Post by sakh on 2020-11-21
Hi,
1. No I did not change any settings at all.
2. Sorry my bad I should have mentioned the symptoms as well. They includes: brightness stuck at max level, Wayland missing from DE menu, screen tearing noticeable. Otherwise I can see and use the laptop.
3. I am using focal. I will try live booting and get back to you on it as soon as I can!

```

[FONT=monospace][COLOR=#000000]lsb_release -a [/COLOR]
No LSB modules are available. 
Distributor ID: Ubuntu 
Description:    Ubuntu 20.04.1 LTS 
Release:        20.04 
Codename:       focal[/FONT]

```

```

[FONT=monospace][COLOR=#000000]uname -a [/COLOR]
Linux X505ZA 5.4.0-54-generic #60-Ubuntu SMP Fri Nov 6 10:37:59 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
[/FONT]
```[FONT=monospace]

```

[FONT=monospace][COLOR=#000000]cat /etc/default/grub [/COLOR]
# If you change this file, run 'update-grub' afterwards to update 
# /boot/grub/grub.cfg. 
# For full documentation of the options in this file, see: 
#   info -f grub -n 'Simple configuration' 

GRUB_DEFAULT=0 
GRUB_TIMEOUT_STYLE=hidden 
GRUB_TIMEOUT=10 
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian` 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
GRUB_CMDLINE_LINUX="" 

# Uncomment to enable BadRAM filtering, modify to suit your needs 
# This works with Linux (no patch required) and with any kernel that obtains 
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...) 
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef" 

# Uncomment to disable graphical terminal (grub-pc only) 
#GRUB_TERMINAL=console 

# The resolution used on graphical terminal 
# note that you can use only modes which your graphic card supports via VBE 
# you can see them in real GRUB with the command `vbeinfo' 
#GRUB_GFXMODE=640x480 

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux 
#GRUB_DISABLE_LINUX_UUID=true 

# Uncomment to disable generation of recovery mode menu entries 
#GRUB_DISABLE_RECOVERY="true" 

# Uncomment to get a beep at grub start 
#GRUB_INIT_TUNE="480 440 1"
[/FONT]
```
[FONT=monospace]
[/FONT][/FONT]```
sudo lspci -vnn | grep -ia20 vga
[FONT=monospace][COLOR=#000000]        [FONT=monospace][COLOR=#000000]        Kernel modules: iwlwifi [/COLOR]

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15) 
        Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:200f] 
        Flags: bus master, fast devsel, latency 0, IRQ 51 
        I/O ports at f000 [size=256] 
        Memory at fe904000 (64-bit, non-prefetchable) [size=4K] 
        Memory at fe900000 (64-bit, non-prefetchable) [size=16K] 
        Capabilities: [40] Power Management version 3 
        Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+ 
        Capabilities: [70] Express Endpoint, MSI 01 
        Capabilities: [b0] MSI-X: Enable+ Count=4 Masked- 
        Capabilities: [100] Advanced Error Reporting 
        Capabilities: [140] Virtual Channel 
        Capabilities: [160] Device Serial Number 01-00-00-00-68-4c-e0-00 
        Capabilities: [170] Latency Tolerance Reporting 
        Capabilities: [178] L1 PM Substates 
        Kernel driver in use: r8169 
        Kernel modules: r8169 

03:00.0 [COLOR=#ff5454]**VGA**[/COLOR][COLOR=#000000] compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Raven Ridge [Radeon Vega Series / Radeon Vega Mobile Series] [1002:15dd] (re[/COLOR]
v c4) (prog-if 00 [[COLOR=#ff5454]**VGA**[/COLOR][COLOR=#000000] controller]) [/COLOR]
        Subsystem: ASUSTeK Computer Inc. Raven Ridge [Radeon Vega Series / Radeon Vega Mobile Series] [1043:1091] 
        Flags: bus master, fast devsel, latency 0, IRQ 255 
        Memory at e0000000 (64-bit, prefetchable) [size=256M] 
        Memory at f0000000 (64-bit, prefetchable) [size=2M] 
        I/O ports at e000 [disabled] [size=256] 
        Memory at fe700000 (32-bit, non-prefetchable) [size=512K] 
        Capabilities: [48] Vendor Specific Information: Len=08 <?> 
        Capabilities: [50] Power Management version 3 
        Capabilities: [64] Express Legacy Endpoint, MSI 00 
        Capabilities: [a0] MSI: Enable- Count=1/4 Maskable- 64bit+ 
        Capabilities: [c0] MSI-X: Enable- Count=3 Masked- 
        Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?> 
        Capabilities: [200] Resizable BAR <?> 
        Capabilities: [270] Secondary PCI Express 
        Capabilities: [2a0] Access Control Services 
        Capabilities: [2b0] Address Translation Service (ATS) 
        Capabilities: [2c0] Page Request Interface (PRI) 
        Capabilities: [2d0] Process Address Space ID (PASID) 
        Capabilities: [320] Latency Tolerance Reporting 
        Kernel modules: amdgpu[/FONT][/COLOR]
[/FONT]
```[FONT=monospace]

```

[FONT=monospace][COLOR=#000000]ls -laH /etc/modprobe.d[/COLOR]
total 64
drwxr-xr-x   2 root root  4096 Nov 18 09:45 [COLOR=#5454ff]**.**[/COLOR]
drwxr-xr-x 154 root root 12288 Nov 18 09:55 [COLOR=#5454ff]**..**[/COLOR]
-rw-r--r--   1 root root  2507 Jul 30  2015 alsa-base.conf
-rw-r--r--   1 root root   154 Feb 16  2020 amd64-microcode-blacklist.conf
-rw-r--r--   1 root root   325 Mar 12  2020 blacklist-ath_pci.conf
-rw-r--r--   1 root root  1518 Mar 12  2020 blacklist.conf
-rw-r--r--   1 root root   210 Mar 12  2020 blacklist-firewire.conf
-rw-r--r--   1 root root   677 Mar 12  2020 blacklist-framebuffer.conf
-rw-r--r--   1 root root   156 Jul 30  2015 blacklist-modem.conf
lrwxrwxrwx   1 root root    41 Jul 23 17:30 [COLOR=#54ffff]**blacklist-oss.conf**[/COLOR][COLOR=#000000] -> /lib/linux-sound-base/noOSS.modprobe.conf[/COLOR]
-rw-r--r--   1 root root    17 Jun 23 21:03 blacklist-radeon.conf
-rw-r--r--   1 root root   583 Mar 12  2020 blacklist-rare-network.conf
-rw-r--r--   1 root root   127 Jan 22  2020 dkms.conf
-rw-r--r--   1 root root   154 Feb 12  2020 intel-microcode-blacklist.conf
-rw-r--r--   1 root root   347 Mar 12  2020 iwlwifi.conf
[/FONT]
```[FONT=monospace]

```

[code]
[FONT=monospace][FONT=monospace][COLOR=#000000]cat /etc/modprobe.d/blacklist.conf [/COLOR]
# This file lists those modules which we don't want to be loaded by 
# alias expansion, usually so some other driver will be loaded for the 
# device instead. 

# evbug is a debug tool that should be loaded explicitly 
blacklist evbug 

# these drivers are very simple, the HID drivers are usually preferred 
blacklist usbmouse 
blacklist usbkbd 

# replaced by e100 
blacklist eepro100 

# replaced by tulip 
blacklist de4x5 

# causes no end of confusion by creating unexpected network interfaces 
blacklist eth1394 

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much 
# hardware on its own (Ubuntu bug #2011, #6810) 
blacklist snd_intel8x0m 

# Conflicts with dvb driver (which is better for handling this device) 
blacklist snd_aw2 

# replaced by p54pci 
blacklist prism54 

# replaced by b43 and ssb. 
blacklist bcm43xx 

# most apps now use garmin usb driver directly (Ubuntu: #114565) 
blacklist garmin_gps 

# replaced by asus-laptop (Ubuntu: #184721) 
blacklist asus_acpi 

# low-quality, just noise when being used for sound playback, causes 
# hangs at desktop session start (Ubuntu: #246969) 
blacklist snd_pcsp 

# ugly and loud noise, getting on everyone's nerves; this should be done by a 
# nice pulseaudio bing (Ubuntu: #77010) 
blacklist pcspkr 

# EDAC driver for amd76x clashes with the agp driver preventing the aperture 
# from being initialised (Ubuntu: #297750). Blacklist so that the driver 
# continues to build and is installable for the few cases where its 
# really needed. 
blacklist amd76x_edac[/FONT]
[/FONT]
```[FONT=monospace]

```

journalctl -b | egrep -i 'radeon|amdgpu' | egrep -i 'error|fail|kernel'
Nov 21 22:20:58 X505ZA kernel: smpboot: CPU0: AMD Ryzen 5 2500U with Radeon Vega Mobile Gfx (family: 0x17, model: 0x11, stepping: 0x0)

```


Thank you! :)
[/FONT][/FONT][/FONT]

---

### Post by CelticWarrior on 2020-11-23
I strongly recommend you revise the UEFI settings. Any firmware update tends to reset the settings, namely re-enable Secure Boot.
Secure Boot in particular shouldn't prevent loading open-source (signed) drivers like "radeon" or "amdgpu" but it'll prevent loading the proprietary (unsigned) "amdgpu-pro".
So, if you want to try the proprietary driver then 1) make sure it supports your hardware and 2) disable Secure Boot.

---

### Post by sakh on 2020-11-23
This worked! Thank you so much.
I apologize if this was a dumb/obvious question, in my defense I am still learning and did not think that secure boot would affect things after the OS boots. Well now I know.
I also would appreciate if Ubuntu would have provided some indication that there was a problem starting/loading the driver, rather I was just stuck with a screen at max brightness and had to locate the problem accordingly. Anyway, that's just my little rant because I am very grateful for all the work put in by the creators and the people on this forum.

Thank you!

---

