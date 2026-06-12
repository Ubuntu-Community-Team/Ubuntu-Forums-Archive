---
title: "boot-repair did not work - &quot;An error occurred during the repair&quot;"
date: 2017-03-18
forum: New to Ubuntu
---

### Post by luxini on 2017-03-18
This is my first post here, so if I made a mistake please let me know to repair it.
Well, I have a problem with boot my system, I ran boot-repair but it did not work.
The program appear do all process good but finish with error message "An error occurred during the repair."LINK: [http://paste2.org/mdtFBZ9H](http://paste2.org/mdtFBZ9H)



As  a possible clue, my system (ubuntu 16.04 and windows 10) come wrong for  nothing, I was using ubuntu and in just a moment the terminal does not  open more, so I decided to restart my system, from this point the system  does not started more. It appear that I lost my GRUB, because it didn't displayed more when start my pc.


I hope you can give me some advices!


Thank a lot.


Regards.

---

### Post by oldfred on 2017-03-18
You have an UEFI system with Windows booting in UEFI mode on sda.
It looks like you have an Ubuntu install on sdb, which also is gpt partitioned.
But you have grub installed to gpt's protective MBR for a BIOS boot, but if you really want BIOS boot you have to have a bios_grub partition.
But better to install in UEFI mode.

Are you using Boot-Repair ISO or Ubuntu installer with Boot-Repair added?
Better to use Ubuntu live installer booted in UEFI mode.
In BIOS boot mode it does not have all the UEFI tools you need to correctly reinstall grub in UEFI mode.

You should have two boot options in UEFI boot menu for Ubuntu live installer. Just be sure to choose UEFI boot.
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by luxini on 2017-03-18
Hi oldfred!
thank for your help. If I understand correct, you are tell me that I need to install my system again? 
I may a mistake when installed the program because I do not have much experience installing in UEFI mode (my pc is new and the previous didn't have this), but my pc worked good by 6 month, so I thought that I installed all ok...
Well this said, the problem is that I have a lot information in my PC and I would like avoid reinstall all again.

Answering your question, I use Ubuntu live with boot-repair added, I also tried boot-repair ISO but it just worked forever.
Finally, the boot system on sda was a surprise for my, I formatted this unity in order to use it as a storage disk and all OSes in my SSD disk. How I should format this unity if I want delete the UEFI system?

---

### Post by oldfred on 2017-03-18
You want UEFI.

And you do not need to reinstall Ubuntu, just use Boot-Repair booted in UEFI mode to run the full uninstall/reinstall of grub from Advanced options.
Just be sure to boot in UEFI mode.

---

### Post by luxini on 2017-03-19
thanks oldfred!
Sorry for been so slow, but I do not know how do what you tell me. I am sure that run mi liveUSB ubuntu in UEFI mode (I see the black windows when start), also check that is disable the point given in **General principles **from [https://help.ubuntu.com/community/UEFI ]("https://help.ubuntu.com/community/UEFI")
Mi problem begun when I need to change the advance options from boot-repair, I try to search in other page, but I do not want make a bigger mistake.
I saw in other page that if I have a EFI partition I should see something like this: 

[IMG]http://imgh.us/Screenshot_from_2017-03-19_11-10-28.png[/IMG]


The bad of this image is the partition with UFI, it show me sda when I want my EFI partition is in sdb (sda is my hdd and sdb is my ssd). If I uncheck this option it show me a option to place GRUB in the unity that I want:

[IMG]http://imgh.us/Screenshot_from_2017-03-19_11-18-53.png[/IMG]

But I am not sure if that is correct.
well, if you can give some advices whether I am in good or bad direction (or give me a link to follow), I would be very grateful.

Thanks a lot for you time!

---

### Post by oldfred on 2017-03-19
The problem is with Ubuntu's grub, it only installs to the ESP on sda.
Does not matter what you say during install of grub.

I have installed to sdb and various flash drives & everytime it overwrites my main working install of grub in the ESP of sda.

---

### Post by luxini on 2017-03-19
Thanks oldfred, so (if I understood) there is no option to do what I want... 
What happen if I delete the sda partition in sda? may it possible to recover the system?
Finally, with the configuration that I show you (last message) the system give me the error that upload in the log file ([http://paste2.org/mdtFBZ9H](http://paste2.org/mdtFBZ9H)), or I am bound to use the second picture configuration but with sda?

Thanks again!

---

### Post by oldfred on 2017-03-19
I have yet to see a system with Ubuntu work in UEFI mode without the ESP on sda.

I have seen systems where when installing drive order does get switched, often causing issues.
And many systems do not directly boot from /EFI/ubuntu folder and ubuntu entries in UEFI, but have to boot fallback or hard drive entry which is /EFI/Boot/bootx64.efi. I copied my shimx64.efi to be bootx64.efi just as a backup.

 Intel NUC
Running The Intel NUC6i7KYK On Linux With Skylake Iris Pro Graphics 16.10
[http://www.phoronix.com/scan.php?page=article&item=intel-sklnuc-pre&num=1](http://www.phoronix.com/scan.php?page=article&item=intel-sklnuc-pre&num=1)
Intel's Braswell NUC Trips On Fedora 22 But Runs Fine On Ubuntu 15.04
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-Braswell-Fedora-Ubuntu](http://www.phoronix.com/scan.php?page=news_item&px=Intel-Braswell-Fedora-Ubuntu)
NUC NUC5i3RYB - openSUSE Tumbleweed vs. Manjaro vs. Debian 8.0 vs. Fedora 21 vs. Ubuntu 14.10
[http://www.phoronix.com/scan.php?page=article&item=intel-5010u-5way&num=1](http://www.phoronix.com/scan.php?page=article&item=intel-5010u-5way&num=1)
NUC Sleep issues:
[http://ubuntuforums.org/showthread.php?t=2265342](http://ubuntuforums.org/showthread.php?t=2265342)
[https://communities.intel.com/message/277645#277645](https://communities.intel.com/message/277645#277645)
Nuc Install
[http://blog.dustinkirkland.com/2013/12/everything-you-need-to-know-about-intel.html](http://blog.dustinkirkland.com/2013/12/everything-you-need-to-know-about-intel.html)
[http://blog.dustinkirkland.com/2013/12/why-i-returned-all-of-my-i3-intel-nucs.html](http://blog.dustinkirkland.com/2013/12/why-i-returned-all-of-my-i3-intel-nucs.html)
[http://www.phoronix.com/scan.php?page=article&item=intel_baytrail_nuc&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_baytrail_nuc&num=1)
UEFI - in efi partition Manual copy grubx64.efi to bootx64.efi to make it work.
[http://arstechnica.com/gadgets/2014/02/linux-on-the-nuc-using-ubuntu-mint-fedora-and-the-steamos-beta/](http://arstechnica.com/gadgets/2014/02/linux-on-the-nuc-using-ubuntu-mint-fedora-and-the-steamos-beta/)
BIOS update fixes some issues
[http://arstechnica.com/gadgets/2014/02/new-intel-nuc-bios-update-fixes-steamos-other-linux-booting-problems/](http://arstechnica.com/gadgets/2014/02/new-intel-nuc-bios-update-fixes-steamos-other-linux-booting-problems/)

---

