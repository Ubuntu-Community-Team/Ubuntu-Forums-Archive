---
title: "error while loading ubuntu from live CD"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by hiperactive on 2008-06-17
Hi 

I just downloaded the last ubuntu for desktop 8.04 i386, but when I try to run it using the live CD, this error appears.

[IMG]http://www.hostdump.com/host/out.php/i27116_error.JPG[/IMG]

I guess it is related to the hard drives in this computer. What can I do?

And by the way, this computer came along with windows vista, but I installed winxp, vista is still in the computer but I can't boot vista anymore. What can I do to boot vista. I guess linux booting could help or isn't it?

Greetings

PC:


     Storage:
      IDE Controller                                    NVIDIA nForce 430/410 Serial ATA Controller
      IDE Controller                                    Standard Dual Channel PCI IDE Controller
      Disk Drive                                        WDC WD1600BEVS-07RST0  (149 GB, IDE)
      Disk Drive                                        WDC WD1600BEVS-07RST0  (149 GB, IDE)
      Optical Drive                                     Optiarc DVD RW AD-7540A  (DVD+R9:4x, DVD-R9:4x, DVD+RW:8x/8x, DVD-RW:8x/6x, DVD-RAM:5x, DVD-ROM:8x, CD:24x/24x/24x DVD+RW/DVD-RW/DVD-RAM)
      SMART Hard Disks Status                           OK

    Partitions:
      C: (NTFS)                                         94418 MB (55522 MB free)
      D: (NTFS)                                         152625 MB (146192 MB free)
      E: (NTFS)                                         46205 MB (46119 MB free)
      Total Size                                        286.4 GB (242.0 GB free)

Motherboard:
      CPU Type                                          Mobile DualCore AMD Turion 64 X2 TL-64, 2200 MHz (11 x 200)
      Motherboard Name                                  FUJITSU SIEMENS AMILO Xa 2528
      Motherboard Chipset                               nVIDIA GeForce Go 6100, AMD Hammer

---

### Post by MasterSander on 2008-06-17
Normally it shouldn't be related to your HDD because it runs from the cd. Did you check your cd for defects? 

It could be a problem with your hardware as well. You can always try to download the alternate version.

And indeed, normally the grub will find your vista and xp and list them. (GRUB has morge problems finding other distros --> seperate /boot partition advised here)

---

### Post by hiperactive on 2008-06-17
thank you master !

well the cd has no problems, what alternate version should I try?

---

