---
title: "can't boot Ubuntu 14.04.1 LTS after installing"
date: 2014-08-07
forum: New to Ubuntu
---

### Post by Jun_Felce on 2014-08-07
Hi,

I'm new to Ubuntu and this is my first time installing this OS. I've installed Ubuntu 14.04.1 LTS recently replacing my previous Windows 7 OS. I've successfully installed Ubuntu but it won't boot. I've run the Boot-Repair thru the terminal by booting into the USB and 'Try Ubuntu'. After running the boot-repair it gives me this link: [http://paste.ubuntu.com/7978542](http://paste.ubuntu.com/7978542).

Right now, my laptop (Compaq Presario CQ40-108TU) doesn't have any running OS installed in its hard drive. I'm booting Ubuntu thru the USB just to get around with my files. Hoping someone could help me get through this problem. Thank You.

---

### Post by sotiris2 on 2014-08-07
Did you actually select to auto-repair via the Boot-Repair program? Did it make any difference?

When you say that Ubuntu doesn't boot we need a bit more information. 
Does it stay on a blank screen? Is there a white line or dash flashing?
Does it actually say something like "Disk Error: No OS installed" ?
Does holding down the SHIFT button during boot (after bios messages) make a menu named [GRUB](https://help.ubuntu.com/community/Grub2) appear?

---

### Post by grahammechanical on 2014-08-07
The recommended repair of Boot Repair was this

> [COLOR=#BB4444]Recommended-Repair[/COLOR]
[COLOR=#BB4444]This setting will reinstall the grub2 of sda2 into the MBR of sda.[/COLOR]
[COLOR=#BB4444]Additional repair will be performed: unhide-bootmenu-10s[/COLOR]


[COLOR=#BB4444]Unhide GRUB boot menu in sda2/etc/default/grub[/COLOR]

The only thing Boot Repair could do was re-install the boot loader (Grub) because there was nothing wrong with the first part of the boot process. That is the part where Grub loads and then loads Linux. When Ubuntu is the only OS we do not see a Grub menu and Grub automatically loads Ubuntu after a time-out of 10 seconds.

The failure to load to a Ubuntu desktop must be happening after the Grub boot loader has passed control over to Linux. And without the information requested by sotiris2 we can only guess what the cause is.

If you bring up the Grub boot menu open the Advanced Options for Ubuntu sub-menu and select Recovery mode. At the Recovery menu select Resume. That will load Ubuntu using an open source video driver. If that gets you to a desktop go to System Settings>Software and Updates>Additional Drivers tab. Allow the utility time to search for drivers and experiment.

This link might be of interest to you depending on the Intel graphic chip set in your machine.

[http://www.omgubuntu.co.uk/2014/08/intel-graphics-installer-linux-updated-1-0-6](http://www.omgubuntu.co.uk/2014/08/intel-graphics-installer-linux-updated-1-0-6)

Regards.

---

### Post by Jun_Felce on 2014-08-07
sotiris2 and grahammechanical, thank you for taking time with my problem. Hoping that the following information below will help solve my concern. 

To: sotiris2,

> Did you actually select to auto-repair via the Boot-Repair program? Did it make any difference?
I did select "Recommended Repair" from the Boot-Repair program but after it says restart the system, no difference noted.

> Does it stay on a blank screen? Is there a white line or dash flashing?
Every after a restart (after bios messages), a GRUB menu appears with the following option to select:
[LIST]
[*]Ubuntu
[*]Advanced options for Ubuntu
[*]Memory test (memtest86+)
[*]Memory test (memtest86+. serial console 115200
[/LIST]

After selecting Ubuntu from the Menu, a blank screen appears and a white dash flashing continously. I've timed the flashing and it took more than 20 minutes. Growing impatience and don't know what to do, I've restarted my laptop manually.

> Does it actually say something like "Disk Error: No OS installed" ?
I've encountered nothing that says "Disk Error: No OS installed".

> Does holding down the SHIFT button during boot (after bios messages) make a menu named [GRUB]("https://help.ubuntu.com/community/Grub2") appear?
Yes, the GRUB menu appears every after a restart. Though I haven't tried holding the SHIFT button during boot.

To: grahammechanical,

> If you bring up the Grub boot menu open the Advanced Options for Ubuntu  sub-menu and select Recovery mode. At the Recovery menu select Resume.  That will load Ubuntu using an open source video driver. If that gets  you to a desktop go to System Settings>Software and  Updates>Additional Drivers tab. Allow the utility time to search for  drivers and experiment.

I've tried getting into the the Recovery Menu and selected Resume, but it did not get me into the desktop. Though after restarting there is a message that says, sort of like to Fix Errors press 'F'. After pressing F key, a message that says
"The disk drive for /tmp is not ready yet or not present." appears with the following options to select:
[LIST]
[*]Continue to wait
[*]Press S to skip mounting or
[*]M for manual recovery
[/LIST]
In this part, I've waited until it automatically restarted by itself and after the restart the usual blank screen and flashing white dash appears.

---

### Post by JKyleOKC on 2014-08-07
As I mentioned recently in another thread about a similar problem, the black screen you are seeing most often indicates a problem between the video driver and your video hardware. The fact that you were able to get to a visible display and operate in the recovery mode tends to confirm that this is your problem.

Possible cures for this vary widely, depending on exactly what hardware is involved. If you can get to a command-line prompt in recovery mode, run the command **lshw** and look in the rather extensive output for a section labeled "display." One line in that section will start with "product:" and that will tell us the manufacturer and model number of the video hardware in your machine. Once we know that, we'll be able to provide much more meaningful suggestions!

---

### Post by Jon_Goiri on 2014-08-07
Hi Jun_Felce, I was having a very similar problem. I had successfully gotten Ubuntu 14.04 on my laptop but decided to switch to Lubuntu. The installation appeared successful but when I booted it'd go into grub, select Ubuntu and give me a flashing cursor until an error message appeared complaining about no partition being present.

I changed the boot mode in my BIOS from legacy to UEFI, reinstalled Ubuntu (wiped the disk clean) and then it worked. I'm not sure it will fix your problem, but it's worth checking.

---

