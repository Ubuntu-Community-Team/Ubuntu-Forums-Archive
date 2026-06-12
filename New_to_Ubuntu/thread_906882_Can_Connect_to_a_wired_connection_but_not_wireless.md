---
title: "Can Connect to a wired connection but not wirelessly!"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by vivekv3 on 2008-08-31
Hey Guys,

I'm completely new to Ubuntu.  I think it's honestly great and I Love it.  I just got it last week.  Everything seems to be working except for my wireless.  I can see the wireless networks but can't connect to them.  Any help?

My laptop is the Toshiba Satellite A100 PSAA8C-0FH00E

---

### Post by pi.boy.travis on 2008-08-31
What card are you using?  Check out System-Administration-Hardware Drivers to see if there is a closed source driver that correct the problem.  You may also want to try connecting to a wired connection and installing any available updates.  You might want to see if there are any proposed or backported updates that might fix your problem.  System-Administration-Software Sources-Updates tab.

Hope this helps!

---

### Post by vivekv3 on 2008-09-01
Hey I'm a complete noobie to the pc.  How do I find out what card I have?  Is there a command in the terminal I can type in to find out?  Its been soo frustrating without having wireless, any help is greatly appreciated.

Thanks again in advance.

---

### Post by teryret on 2008-09-01
The command to tell you what wireless card you have is "lspci".  It'll print out a list of all your hardware, so you can either read through it and find your wireless card or simply paste it here and we can read it for you.

---

### Post by epiphonygirl on 2008-09-01
Since your card is displaying wireless networks that are available then that means that it is at least scanning for networks. If you go system>administration>network unlock it and then change your wireless connection to roaming. After that left click on the network connection by your clock and look for a list of wireless networks. When you find yours click on it and if it needs you to enter a wep-key or something (depends on the network) enter the additional information and see if it connects.

---

### Post by vivekv3 on 2008-09-01
hey I typed lspci in the terminal
this is what i got,

thanks again in advance

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
07:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
07:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)

---

### Post by teryret on 2008-09-01
> **vivekv3 said:**
> 05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

You have the same wifi card I do.  That's good news, because I happen to know that it works perfectly without having to worry about any closed source driver modules.

That it's listing wireless networks is a very good sign, and epiphonygirl's idea should be your next step.  If that doesn't work go find a wireless network that doesn't have any security (drive to panera bread if you have to) and manually configure the wifi card to connect to its ESSID.

If all else fails try using the wifi switch to turn off the wifi card then turn it back on (while the computer is booted).  I know this sounds crazy, but it's what I have to do with mine (though I blame HP, a problem you don't have, details on my adventure: [http://ubuntuforums.org/showthread.php?t=894120](http://ubuntuforums.org/showthread.php?t=894120)).

---

