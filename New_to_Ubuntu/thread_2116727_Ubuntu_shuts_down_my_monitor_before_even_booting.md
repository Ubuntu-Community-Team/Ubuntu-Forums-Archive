---
title: "Ubuntu shuts down my monitor before even booting"
date: 2013-02-16
forum: New to Ubuntu
---

### Post by TaylorSte on 2013-02-16
I have attempted to installing Linux via Ubuntu, The one that is suppose to run with windows still installed. I have no disc, I downloaded it from the site.

System Manufacturer	MSI
System Model	 MS-7309
System Type	 X86-based PC
Processor	 AMD Athlon(tm) 5000 Dual-Core Processor, 2210 Mhz, 2 Core(s), 2 Logical Processor(s)
BIOS Version/Date	American Megatrends Inc. V9.5, 4/9/2009
SMBIOS Version	2.5
Windows Directory	C:\Windows

Name	NVIDIA GeForce 9500 GT
PNP Device ID	PCI\VEN_10DE&DEV_0640&SUBSYS_133E1462&REV_A1\4&210A641E&0&0048
Adapter Type	GeForce 9500 GT, NVIDIA compatible
Adapter Description	NVIDIA GeForce 9500 GT
Adapter RAM	512.00 MB (536,870,912 bytes)
Installed Drivers	nvd3dum.dll,nvwgf2um.dll,nvwgf2um.dll
Driver Version	9.18.13.697



Issue: Whenever I boot, and select "Ubuntu" in the boot menu, it sends me to a purple screen, then my monitor shuts down completely. I can not turn it back on. I have had no experience with ubuntu AT ALL. I haven't seen a single thing that isn't "Windows 7" on this computer. I have been looking up solutions but they mostly involve being able to see, and interact with the menus prior to booting up, but I have tried most of the key commands I've seen to no avail. My monitor just 100% shuts off whenever I boot it. And when I go back to Windows, everything is fine. 

The big issue is my being extremely new to anything Linux. I have no idea what the Grub menu is or how to access it. Some of the jargon used is hard for me to follow. Please help me out!

---

### Post by schragge on 2013-02-16
Do you hear something after the monitor goes off? Does it seem like the system continues to boot up?

---

### Post by TaylorSte on 2013-02-16
Actually, I had my speakers on. A drumming noise can be heard right after it goes to black. But I try to press the commands, and nothing happens.

---

### Post by arpanaut on 2013-02-16
You might want to take a look here:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by TaylorSte on 2013-02-16
That thread helped, but not completely.

I'm sure I have to set up the nomodeset option. But I have no idea how to do it. The megathread kinda just told you what the issue was and not the steps to solve it.

---

### Post by schragge on 2013-02-16
Try to hold the **Shift** key while booting into Ubuntu.

---

### Post by TaylorSte on 2013-02-16
It jumped me to a menu. It was in all purple, and have two options, "Ubuntu"
"Advanced Options with Ubuntu"

I clicked Ubuntu and it ran through the booting to turn off my monitor again, When I tried to get back to the menu, it didn't work.

---

### Post by schragge on 2013-02-16
When at menu, try to edit the *Ubuntu* boot entry by pressing **e** and appending *nomodeset* to the end of the line that starts with **linux**. To boot the edited entry, press **Ctrl**+**x**

---

### Post by TaylorSte on 2013-02-16
I got into ubuntu, But I haven't tried what you said, I will next time I boot it.

I was able to get into it by running it in Recovery mode. It was dog slow and I couldn't download steam. It sent me back and forth between Archieve Manager and Ubuntu download store BS. It was one of the slowest operating systems I've ever ran, but it was probably due to it being in Recovery mode.

---

### Post by oldfred on 2013-02-16
Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)

# You may need headers - meta package for 12.10 version:
sudo apt-get install linux-headers-generic

    Shows screens you should see.
       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

