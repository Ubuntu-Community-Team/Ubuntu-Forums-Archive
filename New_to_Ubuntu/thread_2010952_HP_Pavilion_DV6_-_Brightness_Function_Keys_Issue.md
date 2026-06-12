---
title: "HP Pavilion DV6 - Brightness Function Keys Issue"
date: 2012-06-26
forum: New to Ubuntu
---

### Post by PhibreOptix on 2012-06-26
Hi there,

I have recently purchase a HP pavilion dv6 laptop and have installed ubuntu 12.04 onto it.

Almost all the function keys work correctly except for the brightness keys which function strangely.

When at full brightness, pressing either brightness up or brightness down the screen dims to minimum brightness. Once at minimum brightness if I try to turn the brightness up again it will flash at the higher brightness and then turn back down to minimum.

The only way to get it to go brighter is to hold the function key down, at which point it kind of flashes abruptly between low and high brightness and then settles on the max brightness.

Does anybody have any ideas on how to fix this?

Thanks,

---

### Post by Redblade20XX on 2012-06-26
Have you tried installing the proprietary driver for your graphics card?

-Red

---

### Post by PhibreOptix on 2012-06-26
Yes I am currently using the nVidia proprietary video drivers however the open source version exhibits the same issue.

---

### Post by LowSky on 2012-06-26
what model dv6? The Dv6 is a large selection of models. We cant help without knowing the hardware.

For example: Mine is a DV6-6117dx and has an AMD processor.

---

### Post by PhibreOptix on 2012-06-26
It's a HP PAVILION dv6 2120TX with i5 first gen processor and nVidia gt230m graphics card.

---

### Post by PhibreOptix on 2012-06-27
Here is the output of lspci if that assists:
```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1c.7 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 8 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GT216 [GeForce GT 230M] (rev a2)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
02:00.0 Network controller: Broadcom Corporation BCM43225 802.11b/g/n (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
04:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
04:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
04:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
04:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
04:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```

---

### Post by PhibreOptix on 2012-06-28
Bump

---

### Post by NikTh on 2012-06-28
Try to set the ***acpi_osi=Linux** *or ***acpi_backlight*=*****vendor** *parameter to the kernel (via grub) and see if this strange behaviour change. 
Take a look at here for setting parameter -> [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by PhibreOptix on 2012-06-29
Hi NikTh, I have tried the vendor and backlight settings for the grub command line however when booting with these enabled the display is stuck on max brightness and completly unable to change it.

---

### Post by NikTh on 2012-06-29
> **PhibreOptix said:**
> Hi NikTh, I have tried the vendor and backlight settings for the grub command line however when booting with these enabled the display is stuck on max brightness and completly unable to change it.

Ok , it was a suggestion only. You can remove parameters if not works for you. 
This is strange you know.. cause recently i installed Ubuntu 12.04 64bit on HP pavilion g6 (a friends laptop not mine) and everything worked out of the box. I was (and my friend also) very happy about it. 
Of course its not the same  pavilion.. but ..
 
what drivers you use ? nouveau or nvidia ?

---

### Post by PhibreOptix on 2012-06-29
I am using the proprietary nVidia drivers but this behaivour also occurs with the open source nouveau driver.

---

### Post by josian_220 on 2012-06-30
I've had this issue for quite a long time too... I have a hp dv6-2160ep. Interesting thought while using Fedora (up from Fedora 15 to Fedora 17) brightness keys have been working out of the box ever since. I'm currently using Fedora 17, let me know if there is some kind of information I can give to try to solve this issue (I would also like to be able to fix this and use Ubuntu :P).

BTW - Brightness keys work the same with either nouveau or the nvidia proprietary drivers.

---

### Post by PhibreOptix on 2012-07-01
Bump

---

### Post by josian_220 on 2012-07-29
bump

---

### Post by josian_220 on 2012-08-08
bump still having this issue.

---

### Post by VoltManEXE on 2012-08-29
> **josian_220 said:**
> bump still having this issue.

It might be an issue with the key bindings. See if you can manually edit the brightness by editing this file:
```
/sys/class/backlight/acpi_video0/brightness
```(I'm on Linux Mint Debian Edition, so the exact file path for you will  most likely be different.) It's a regular text file with a number in it ranging from 0 to 10. When in a text editor with root permissions, changing the value and saving the file will change the screen's brightness.

If that doesn't give you any trouble, then it's a key binding issue. I'm having this issue as well, but in my case, the brightness shortcut keys are not being detected by the Linux kernel at all. I wasn't able to find scancodes for them, which means you can't map them as keys. Oddly enough, the "HP Media" button (or something like that, it looks like a wavy line) wasn't mapped as a key either, yet it was detected by the kernel and I was able to correct that and map it as a regular key. I used the ArchLinux article <<[here]("https://wiki.archlinux.org/index.php/Extra_Keyboard_Keys")>> to figure this out, but that was about all I could do.

If the brightness keys actually do something, even if they don't work correctly, see if you can use that article to fix the functions of the keys.
If you have CompizConfig, you can also find the brightness settings and change the shortcut keys for increase/decrease brightness.

---

### Post by NikTh on 2012-08-29
Hi , 
give the result of this command 
```
ls /sys/class/backlight/*/
``` 

Thank you

---

### Post by magtrask on 2012-09-21
I use an HP Pavilion dm3 and had the same problem. Tried a lot of suggestions. Easy fix  for me with the link:

[HTML][http://www.techjail.net/solved-brightness-problem-in-ubuntu-12-04-precise-pangolin.html](http://www.techjail.net/solved-brightness-problem-in-ubuntu-12-04-precise-pangolin.html)[/HTML]

My f2 and f3 keys work as intended for brightness up and down.

---

