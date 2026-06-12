---
title: "Grub and booting problems"
date: 2013-01-20
forum: New to Ubuntu
---

### Post by Slimey on 2013-01-20
I recently installed the familiar Windows application Age of Empires with WINE. Following this a problem arose on start up. My computer would boot with Ubuntu and then go black before my login screen. Since then I have to press ENTER each time the black screen appears before my login screen appeared (even after uninstalling and removing the application). I searched around on wine and the interwebs and found a program that claimed to fix booting problems (I assumed that it was a booting problem). I installed and ran this program. Since then I have had what I think is known as a GRUB screen appear (is that right?) where I have to choose which OS to boot. I only use a Linux-Ubuntu 12.04 lts OS. I have no others installed. However, on this boot menu, I am offered a number of boot-repair options. I want to remove this GRUB menu. Perhaps all I need to do is remove these boot-repair options from my hard drive. Can somebody explain this situation to me, and suggest a solution? Also, the black screen thing didn't stop. I still have to press ENTER. Any suggestions? Cheers.

---

### Post by oldfred on 2013-01-21
Welcome to the forums.

Was it Boot-Repair that you ran? It tells you what changes it is proposing. 

Grub will also appear if the previous boot had issues. 

Have you looked into log files to see what the error may be. 
I would use Log File Viewer and look at dmesg. It is long and shows every line during the boot process. You want to see if you have anything that is an error, or repeated tries at loading and then failure or a long time before next task.

---

### Post by WanderingAlbatross on 2013-01-21
Also, your original problem does not seem to me to be able to be created by installing a program with wine.  The programs from windows are installed in a hidden folder inside your home directory.  They have little influence over the goings on of the operating system.  I have never seen one be able to affect anything on the system other than itself.  Are you sure you did not do something else before that caused the blank screen?

---

### Post by Slimey on 2013-01-22
Thanks for your replies,

oldfred: I documented what I did and I can tell you that it *was* boot-repair that I used. What are the log files? 

WanderingAlbatross: I don't think I did anything that could have caused this. I only noticed that it started happening when I installed Age of Empires. Do you have any ideas to fix this? Is more information needed?

---

### Post by audiomick on 2013-01-22
> **oldfred said:**
> I would use Log File Viewer ...

Just a quick question on the side: Oldfred, what is that? I've noticed a couple of references to Log File Viewer, but I reckon I hadn't seen any reference to it until just recently. Is it something new? If so, since which Ubuntu version? Where is it to be found?

---

### Post by oldfred on 2013-01-22
It has been there for a while. I use 12.04 with fall back so it is in System tools at that menu level. It is just called Log File Viewer and opens the log files. It looks in /var/log which you can do yourself. Now it seems to default to only one or two log files, and you have to know to open more in /var/log.

With Unity I have not opened it, but assume it is something you can just open with dash.

I may have installed it a long time ago, as now I have lost track of what is default anymore. I have a long list of apps from dpkg that I reinstall first thing with a new install. If not available try synaptic or Software Center.

---

### Post by audiomick on 2013-01-22
Ok, thanks. On this 10.04 install I can't find it in synaptic or the software centre. That may be a translation problem. My system is set to speak German. All I could turn up was Ksystemlog, which seems to be something similar. I'll have another look when I get around to installing 12.xx on one of my machines.

---

### Post by Slimey on 2013-01-25
I had a look at the log file suggested. The only thing that sounds like you explained was this piece of file:

[    1.247308] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    1.247336] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP07._PRT]
[    1.247372] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG0._PRT]
[    1.247440] \_SB_.PCI0:_OSC invalid UUID
[    1.247441] _OSC request data:1 1f 1f 
[    1.247445]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    1.247474] \_SB_.PCI0:_OSC invalid UUID
[    1.247475] _OSC request data:1 0 1d 
[    1.247479]  pci0000:00: ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d
[    1.247481] ACPI _OSC control for PCIe not granted, disabling ASPM
[    1.250528] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    1.250576] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 10 11 12 14 15) *7
[    1.250620] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *10 11 12 14 15)

Does anything look wrong with this?

---

### Post by oldfred on 2013-01-26
I do not think so with ACPI. But something similar or long time between entries.

ACPI is power control and has many options. Some are new and systems may not support all the new features.

---

