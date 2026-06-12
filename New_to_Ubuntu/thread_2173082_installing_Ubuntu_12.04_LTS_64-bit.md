---
title: "installing Ubuntu 12.04 LTS 64-bit"
date: 2013-09-07
forum: New to Ubuntu
---

### Post by zoominguy on 2013-09-07
Hi,

I'm relatively new to Ubuntu and I recently got my first UEFI based laptop and I wanted to install Ubuntu on it alongside Windows 8. I created a live USB using Unetbootin and when I boot into the USB drive, a GRUB menu comes up. When I press Try Ubuntu or install Ubuntu, my screen either goes black or turns off entirely. I tried using the nomodeset option but that doesn't work. One time a sort of terminal window appeared but I had no idea what to do. I tried disabling secure boot but doesn't seem to help. I also tried using a different USB drive and also tried creating a live USB using Universal USB installer. I also tried Ubuntu 13.04. That doesn't work either.


I'm sorry if similar questions have been asked in the forum but I haven't been able to solve my problem

---

### Post by Drone4four on 2013-09-07
I personally have to enable the nomodeset parameter to get my PC to boot off my Ubuntu live media.  You said you tried that and it hasn't helped.  I'm not sure exactly what the problem is.  

To further narrow down other possibilities, have you tried using your Ubuntu live USB stick on other working PCs?  This would eliminate the possibility that there is something wrong with your USB stick.

---

### Post by zoominguy on 2013-09-07
The USB works on my older BIOS based laptop

---

### Post by oldfred on 2013-09-08
Are you using 64 bit version?

What system is this as some required other boot parameters and a few users have posted some that work with other systems.

See also link in my signature.

---

### Post by zoominguy on 2013-09-08
I am using 64 bit. My machine is a Toshiba Satellite P840t.

---

### Post by newb85 on 2013-09-08
I've installed several versions on my Satellite P755 (including 12.04) without having to use any special boot options.  Are you sure there's not a problem with the image used to create the USB stick?

---

### Post by oldfred on 2013-09-08
A Toshiba P50 user had this comment.
>  Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.



Is system using the Intel video?

Instead of nomodeset some have used these settings.
  i915.i915_enable_rc6=1
      
 acpi_osi=Linux
video=1280x1024-24@75 or whatever native resolution is

 acpi_osi=Linux 
acpi_backlight=vendor

And some systems are working but back light is off or down too low. Just use function key to make it brighter.

---

### Post by zoominguy on 2013-09-11
Just to be sure, to use those options mentioned, i have to press e on the GRUB 2 menu and then replace quiet splash with the option I want. Am I correct?

---

### Post by oldfred on 2013-09-11
Yes and when you replace quiet splash you should then see all the drivers and process of booting. If it stops then you may be able to see what caused the error. Often not the last thing posted but several lines above or something posted several times with message that it is not working or takes a very long time during boot. May go by fast, but same info is in log files for later review.

---

### Post by zoominguy on 2013-10-29
After I failed multiple attempts I gave up. Last night I tried again and this time I turned UEFI into Legacy mode. Ubuntu installer worked and I was able to try out Ubuntu however when I went on the install Ubuntu, the installer did not detect my windows installation and offered me to wipe it out and install over it. Also, my partitions are labeled something like ext1. ext2, ext3 etc. Does anyone know what I should do?

Thanks

---

### Post by mastablasta on 2013-10-29
ext1, ext2 are file systems like FAT32 and NTFS is in windows. 

if you mean /sda1 /sda2 these are partitions on disk (sda1 = first parittion on first disk etc., sdb2 = second parittion on second (b) disk ).

i would say it would help if you used windows disk manager to create empty (unformatted) disk space and then during install install there.
you can also make a screenshot of your disk paritioning in windows disk manager and post here. someone might have some valuable avice to offer based on that.

---

### Post by oldfred on 2013-10-29
Also if you used Windows to create partitions, it may have converted from basic partitions to dynamic partitions which do not work with Linux. In gpt partttioning dynamic may also be shown as LDM.

Even some Windows tools do not work with dynamic partitioning which is somewhat like LVM is in Linux. And with LVM you have to use LVM tools not standard partition tools.

---

