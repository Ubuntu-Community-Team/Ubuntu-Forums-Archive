---
title: "Boot error [0.000000] [firmware bug]"
date: 2018-03-22
forum: New to Ubuntu
---

### Post by fsrtraveler on 2018-03-22
I tried to install Ubuntu 16.04 ( had 16.10 it was a typo) last night and it would not boot to Ubuntu.  Below I have listed the link of the tutorial I followed and the results.  Please advise how I might fix this issue.


This is the link


[https://www.tecmint.com/install-ubuntu-16-04-alongside-with-windows-10-or-8-in-dual-boot/](https://www.tecmint.com/install-ubuntu-16-04-alongside-with-windows-10-or-8-in-dual-boot/)


Everything went well and I followed thetutorial exactly and after installation I selected &#8220;restart now&#8221;and got this error message.  [0.000000] [firmware bug] tsc_deadlinedisabled due to Errata: please update micro code to version  0X52 (orlater).  There were comments after this error that indicated someservices started which were:

[LIST]
[*]
[*]wpa supplicant
[*]snappy daemon
[*]network manager wait online
[*]crash report submission
[*]/etc/rc.local compatibility
[*]/etc/rc.local compatibility
[/LIST]
There was at this point a statementthat said a start job is running for ubuntu cd installer (2 min 5s/nolimit)




How would you suggest I fix it soUbuntu will boot properly?  I finally turned off the laptop and backon and it booted into Windows 10 where I checked partitions and theUbuntu home and root were created correctly.


Please give advice on how I can fix itso Ubuntu will boot properly?


My laptop is an HP Pavilion &#8211;15-cc563st,  i7-7500U, [COLOR=#000000]1 TB 5400 rpm SATA, 12GB DDR4-2133 SDRAM[/COLOR]

---

### Post by ajgreeny on 2018-03-22
There is no point installing 16.10 any more as it is now out of support, and has been so for several months.  You will get no updates to the OS and it is a big security risk.

Install 16.04 or 17.10, both of which are still supported and can be upgraded if you wish to the new 18.04 LTS version which will appear next month.

---

### Post by fsrtraveler on 2018-03-22
Thank you for the advice but that does not address my error.  I will upgrade to a newer version but need to get this laptop to at least let me log on.

---

### Post by fsrtraveler on 2018-03-22
I checked my dvd and it was the 16.04 version I tried to install.

---

### Post by ajgreeny on 2018-03-22
Ah! 16.04 is fine; it is what I'm using now, and have been since just after it appeared.

HP, unfortunately, is one of the computer manufacturers that do not follow the currently accepted standards for UEFI, which I assume your machine is using.

Was the Windows 10 pre-installed? If so it will definitely use UEFI, and Ubuntu must therefore also be installed using UEFI.
See [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295) for lots of info on how to workaround HP's UEFI installation problems

See also **Boot-Repair** in my signature below and follow the instructions there to run the **Boot-Info-Script**, which you can do from the live Ubuntu OS.	 

**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system and potentially show some possible solutions for you.

---

### Post by fsrtraveler on 2018-03-22
Thank you, I will do as you suggest asap.  Will be traveling for a couple of days but when stopped I will attempt your suggestion.

---

### Post by mkbhanu on 2018-03-24
The message you got: "[COLOR=#000000]firmware bug] tsc_deadlinedisabled due to Errata: please update micro code to version 0X52 (or later).[/COLOR]" seems to indicate that your system has an older version of BIOS (and other firmware, btw, BIOS itself is firmware) which needs to be updated before you can install Ubuntu 16.04 LTS. Basically you should perform it before you attempt installing. Unlike most of the program updates which are usually automatic, BIOS has to be updated manually. Updating the BIOS, also known as "flashing the BIOS," replaces the BIOS firmware. If you want to know more visit this [link]("http://www.dell.com/support/article/in/en/indhs1/sln284433/what-is-bios-and-how-to-update-the-bios-on-your-dell-system?lang=en") and this [link]("http://www.dell.com/support/article/in/en/indhs1/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en").

Unified Extensible Firmware Interface (UEFI) is firmware code from a chip on your motherboard that provides extra functionality, beyond the Basic Input/Output System (BIOS). If your computer will not boot, and the computer features a UEFI Startup Menu, you can update the system BIOS using UEFI. Since you have an HP system, I found this support document for you: [https://support.hp.com/in-en/document/c00042629](https://support.hp.com/in-en/document/c00042629). Though it talks about Windows, you can follow instructions for flashing your BIOS from the system start-up menu. Once you update BIOS, installing Ubuntu should be cakewalk. Hope it helps. All the Best :)

---

### Post by fsrtraveler on 2018-03-24
I agree that I need to update BIOS.  I did that plus chipset updates as well as the firmware.  I then reinstalled 16.04 and did not get the same error but when restarting Ubuntu I did not get a dual boot menu to choose ubuntu and my computer booted right into Win 10.  Is there a way to fix this?  I wonder if I need to turn off secure boot or something like that when doing a Ubuntu install.  Seems Microsoft has put in something to prevent dual boots?

---

### Post by ajgreeny on 2018-03-25
Once again, now you have reinstalled go to **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 

**Again, do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system.

---

### Post by fsrtraveler on 2018-03-25
Issue resolved. I updated all intel chipset related drivers and this allowed me to run Ubuntu manually by selecting the boot menu when booting my computer and then selecting ubuntu OS.  I will automate the boot file later to run Ubuntu automatically on startup.  Thanks all for the input to my boot error.

---

### Post by ajgreeny on 2018-03-26
Great news!

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

### Post by mkbhanu on 2018-03-27
@fsrtraveler, first of all, Congratulations for making it through! Just curious to understand if you updated the drivers from Windows and upon restart, you got Boot menu?

---

