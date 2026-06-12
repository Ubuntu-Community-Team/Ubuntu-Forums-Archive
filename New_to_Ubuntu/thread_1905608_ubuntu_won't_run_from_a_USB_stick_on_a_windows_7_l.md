---
title: "ubuntu won't run from a USB stick on a windows 7 laptop"
date: 2012-01-07
forum: New to Ubuntu
---

### Post by bmori on 2012-01-07
I have ubuntu 11 on a USB stick. I can run it from the USB if the laptop is a windows XP but if I try to run it from the USB on a laptop with a windows 7 installation it doesn't work.

Works from a windows XP toshiba and acer.
Doesn't work from a windows 7 samsung and acer

Any thoughts - I was hoping that this would be a useful tool if the hard-drive failed

cheers
Bill

---

### Post by jtarin on 2012-01-07
Is the USB visible as a selection in the F11 boot menu in all computers? 
The Operating system as to XP or 7 should be immaterial.

---

### Post by jockyburns on 2012-01-07
You have to enter the bios and select the first boot device and set that to USB. If you don't then the computer will only boot from the first device listed that has a bootable OS on it. (Usually HDD )

---

### Post by bmori on 2012-01-07
I press F2 at switch on and set to USB   - the samsung just eventually bypasses and loads from the hdd - the acer just hangs.  With an XP pc I do the same and I get the ubuntu try or install menu.
 
thanks for your inputs
bill

---

### Post by blackbird34 on 2012-01-07
What about just trying with a CD?

---

### Post by jtarin on 2012-01-07
> **bmori said:**
> I press F2 at switch on and set to USB   - the samsung just eventually bypasses and loads from the hdd - the acer just hangs.  With an XP pc I do the same and I get the ubuntu try or install menu.
 
thanks for your inputs
billWere you able to use that USB stick to boot something else before, other than Linux? What did you use to install Ubuntu on the USB?

> samsung just eventually bypasses and loads from the hdd - the acer just hangsDuring this time do you get any output from the screen...like a blinking cursor or "boot:" option?

---

### Post by bmori on 2012-01-07
> **blackbird34 said:**
> What about just trying with a CD?
 
Haven't tried a CD. I have an old cd I used to use a couple of years ago, but I might try burning a newer ISO image

---

### Post by bmori on 2012-01-07
> **jtarin said:**
> Were you able to use that USB stick to boot something else before, other than Linux? What did you use to install Ubuntu on the USB?
 
[COLOR=darkred]I booted a couple of laptops that had an XP system resisdent on the hardrive.[/COLOR]
[COLOR=darkred]The USB stick I have is an 8GB Kingston. A month ago I was using a 16GB Sandisk Cruzer. Identical happenings with both sticks. I changed sticks because I needed the 16gb for something else. I followed the procedure on the Ubuntu website.[/COLOR]
 
During this time do you get any output from the screen...like a blinking cursor or "boot:" option?
 
[COLOR=darkred]Nothing on screen.[/COLOR]
 
[COLOR=darkred]Basically I am curious if anyone has successfully booted the "Try UBUNTU" from a USB stick onto a machine that had windows 7. Or is there something funny about the BIOS on windows 7 machines that prevents trial installs of Ubuntu from a USB stick.[/COLOR]
 
cheers
Bill

---

### Post by Karlchen on 2012-01-07
Hello, Bill.

The question whether a machine boots Ubuntu from a USB stick successfully does not depend on the operating system which has been installed on the machine's harddisk at all.

Yes, I use this notebook where I am typing my reply right now pretty frequently to boot various Ubuntu and other Linux systems from various USB sticks. This notebook runs Windows 7 Enterprise Edition SP1 32-bit. This notebook is the machine which causes no trouble to me at all when trying to boot from USB sticks. By the way, this notebook is a Dell Latitude E6400. 
Other machines do cause trouble to me, because they are equipped with outdated Bios versions that do not fully support booting from USB sticks.

Kind regards,
Karl

---

### Post by bmori on 2012-01-07
> **Karlchen said:**
> Hello, Bill.
 
The question whether a machine boots Ubuntu from a USB stick successfully does not depend on the operating system which has been installed on the machine's harddisk at all.
 
Yes, I use this notebook where I am typing my reply right now pretty frequently to boot various Ubuntu and other Linux systems from various USB sticks. This notebook runs Windows 7 Enterprise Edition SP1 32-bit. This notebook is the machine which causes no trouble to me at all when trying to boot from USB sticks. By the way, this notebook is a Dell Latitude E6400. 
Other machines do cause trouble to me, because they are equipped with outdated Bios versions that do not fully support booting from USB sticks.
 
Kind regards,
Karl
 
danke schoen Karl
 
I think you have answered my question - my samsung is an i5 64 bit and it has too many smart features for it's own good.  
 
cheers
Bill

---

### Post by oldfred on 2012-01-07
Besides issues of BIOS not booting, some systems have different video and need some help with a parameter. Some very old or very new systems also need other parameters to boot.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)
Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

---

### Post by oldfred on 2012-01-07
If you have an i5, your motherboard probably is UEFI/BIOS. So you need to know what mode the system is in. It seems that it cannot be set, but UEFI checks for efi partition as first partition with boot files, and if not found defaults to BIOS mode and boots from MBR.

Windows 64bit can work with UEFI and then only with gpt partitioning. Or it can be MBR(msdos) partitioning and boot with BIOS/MBR.

---

### Post by bmori on 2012-01-08
Thanks Fred for all the info - much appreciated
 
cheers
Bill

---

### Post by oldfred on 2012-01-08
+1 on Karlchen comments that it is not Windows 7, but system.

On my desktop system all the USB boot choices will not boot a flash drive, but do boot a flash drive as if it is another hard drive.

I tried every USB alternative and there were a lot. I booted flash from my portable, so I knew I had a bootable flash drive. Then I gave up. For some reason I had flash plugged in and was selecting a different drive to boot with my one time boot key (f12 for my system) and under hard drives was the flash drive.

Some have reported issues with certain brands of flash drives, but if it boots from your XP machine, I would expect it to boot on your newer system.

---

