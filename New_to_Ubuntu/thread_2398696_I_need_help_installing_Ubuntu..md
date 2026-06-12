---
title: "I need help installing Ubuntu."
date: 2018-08-16
forum: New to Ubuntu
---

### Post by dogthehog on 2018-08-16
I am installing Ubuntu and it stopped working near the end of the install. Please tell me how to fix this and fully install Ubuntu.

---

### Post by ubname on 2018-08-16
Is it possible that you have some broken hardware?

---

### Post by kc1di on 2018-08-16
Hello dogthehog  and Welcome to the Ubuntu Forums,

Can you give us a little information on your system, make, model, ram, etc.  It's hard to help without any info.  In general the [Ubuntu installation wiki]("https://help.ubuntu.com/community/Installation") may help. And [this page]("https://help.ubuntu.com/lts/installation-guide/index.html") may be of help also.

---

### Post by NM5TF on 2018-08-16
@dogthehog....

did you run the MD5 checksum on your iso that you used to install Ubuntu ???

you may have a corrupt iso....

have you tried reinstalling ???

tommy

---

### Post by dogthehog on 2018-08-16
I do not know what aMD5 checksum is. Can you oxplain or tell me what to do

---

### Post by dogthehog on 2018-08-16
I have a 1050ti graphics card and I have a picture showing the mother board bios thing.

---

### Post by kc1di on 2018-08-16
your graphics card may be the problem.  It's a Nvidia card and with most of them you have to add a boot parameter to the grub boot like to get it to boot up.  plug in the live 
dvd /usb just as you system begins to boot , after the bios splash screen hit the shift key. This should bring up the grub boot menu.  once there hit the E key and it should open the boot line.  right after the entry "quiet splash" type nomodeset.  once you've done that press CRTL and X key and your system should boot, once boot try the install again. 

If the install is successful you may have to enter the nomodeset again to boot the installed system.  once in the new system go to software and updates and the other drivers tab and install the recommended driver for your card reboot and it should all then work.

---

### Post by dogthehog on 2018-08-16
I can&#8217;t seem to figure out the boot thing. I do have my old graphics card. It&#8217;s junk, but it still works. I am going to try installing with the old graphics card then switching cards after I have linux installed.

---

### Post by QIII on 2018-08-16
Family- and workplace-friendly language, please.

---

### Post by dogthehog on 2018-08-16
I just loaded my old graphics card and I still got this message. I do not know when to press shift while it’s booting. After the option to run bios setup before?

---

### Post by dogthehog on 2018-08-16
Ok, I did what you said, but I got here and there was no place to wright nomo something

---

### Post by oldfred on 2018-08-16
Why are you using grub4dos? That has not been supported for years, although a Windows BIOS boot tool uses it still.

You should be booting from UEFI boot menu, your post #6 says that is f8 for your system.
Is Windows installed in UEFI or BIOS boot mode? Your UEFI boot menu will give two boot options.

Many Asus need IOMMU setting in UEFI and a boot parameter & your nVidia card needs a boot parameter. Not sure what video card you are now using.
       Asus Sabertooth 990FX: Easy solution to get IOMMU working on mobos with broken BIOSes. 
[http://ubuntuforums.org/showthread.php?t=2254677](http://ubuntuforums.org/showthread.php?t=2254677) 
    
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by dogthehog on 2018-08-17
I am not very skilled with computers and do not understand all of what you said. You said I need a new boot menu? How do I get and install a new one?

---

### Post by oldfred on 2018-08-17
As I said above:
You should be booting from UEFI boot menu, your post #6 says that is f8 for your system.

Several examples attached, but yours may be slightly different.

---

### Post by dogthehog on 2018-08-17
This is all that shows up when I hit f8

---

### Post by NM5TF on 2018-08-17
> **dogthehog said:**
> This is all that shows up when I hit f8

it is asking you which device to boot from.....DVD ROM or an external USB device.....are you trying to boot
from a USB external disk or a USB thumb drive ???

or is your install medium on the DVD ROM ???

did you download the iso yourself, or did you use a commercial iso ???

if you downloaded it yourself you should have done a MD5 checksum to verify it is not corrupted....MD5 info here [https://help.ubuntu.com/community/HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")

tommy

---

### Post by dogthehog on 2018-08-17
I am using a external hard drive that conects to usb. Also I tried to figure out how to do the verification thing but I did not get it.

---

### Post by oldfred on 2018-08-17
The normal USB boot creators erase entire drive. That is why smaller USB flash drives are recommended for use as the installer for Ubuntu (and Windows).

So how are you creating the installer?
       Also link on how to create a  bootable DVD or USB flash drive, using Windows or Ubuntu, Min hardware requirements
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

---

### Post by dogthehog on 2018-08-19
I was using a thing called uui to &#8220;extract&#8221; the iso file. Are you saying I should have two things plugged into my computer to install? My hard drive, and my usb? And the usb has Ubuntu? Also I downloaded ubuntu off of the links you provided in the last post. (The desktop one)

---

### Post by dogthehog on 2018-08-19
Also, do you want to communicate through discord, so that there can be quicker and cleaner communication.

i am dogthehog#9234. post your username so I wnow who to accept.

---

### Post by oldfred on 2018-08-19
Are you wanting to install to the external hard drive?
And in UEFI or BIOS boot mode? It should be same as Windows if you have that on Internal hard drive.

If UEFI have you at least reviewed link in my signature? Yes it is a lot.

---

