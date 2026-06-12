---
title: "Windows 7 boot option gone"
date: 2013-07-12
forum: New to Ubuntu
---

### Post by cholas on 2013-07-12
Hi every,

I'm new to Ubunutu, and have just installed it on my dell inspiron 14z by disabling intel rapid storage technology. After it was installed I went back and renabled irst through the gui on windows 7. I then went to look at the ubuntu, and now the boot option for windows 7 is no longer available. I have tried the boot repair tool to no avail. Here is what the boot info url says:


============================= Boot Info Summary: ===============================   => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of      the same hard drive for core.img. core.img is at this location and looks      for (,msdos5)/boot/grub on this drive.  => Windows 7/8/2012 is installed in the MBR of /dev/sdb.  => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.  => No known boot loader is installed in the MBR of      /dev/mapper/isw_cajcghahcc_Dev_Cache.

There is more which can be found here: [http://paste.ubuntu.com/5869768/](http://paste.ubuntu.com/5869768/)

I don't know what to do from this point on, and i do not know whether re-enabling irst raid is what caused the problem or if it is something else
all together. Any help will be appreciated. Thank you in advance. :)

---

### Post by oldfred on 2013-07-13
Standard desktop Ubuntu does not include RAID drivers. I have not seen Intel SRT with BIOS, but usually with the newer UEFI installs where it has worked. Some install Ubuntu to SSD to make it fast, others have re-enabled Intel SRT and it has worked.

Perhaps adding RAID drivers, mounting Windows partition(s) and then run update to grub:
sudo apt-get install dmraid
sudo update-grub

      
  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

---

### Post by cholas on 2013-07-13
Hello oldfred, thanks for the reply. Turns out that I have done more damge than originally thought because ubuntu is no longer loading either. The option for it was still there, but it got stuck when actually opening the OS. I have decided to just re-install Windows from a back. The only problem now is that I think ubuntu is still on the computer because I can see two different partitions with about 140 GB each. Now I need to figure out how to get rid of the right one. I'll mark this thread as solved anyways though. Thanks again.

---

