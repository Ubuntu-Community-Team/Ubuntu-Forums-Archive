---
title: "Dual boot issues"
date: 2013-01-11
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2013-01-11
Hi guys and Happy New Year!

   I haven't been here for a while, but I always found help when I needed it and today I need your counsel again.
   I have 2 machines, one running Windows 7 and the other one running Windows 8 and I want to dual boot with Ubuntu on both.
   The machine running Windows 7 is a Schenker P702 notebook. On this computer I have 3 separate physical drives: a 320 GB drive where Windows 7 is installed, a large 1 TB drive for data and a 60 GB SSD where I want to install Ubuntu. I have split the 60 GB SSD in 2 partitions: a 16 GB for swap (I have 8GB RAM) and the rest for the OS.I made a bootable USB stick with Ubuntu, and it booted fine from the live USB, so I don't expect any problems on this machine. My question for this computer is if there is something special that I should know (or do) before proceeding with the installment. The specifications for the notebook are as follows:

Intel Core i7 - 3630QM, 2,4GHz
AMD Radeon HD 7970M 2048MB GDDR5
8GB (1x8192) SO-DIMM DDR3 RAM 1600MHz CORSAIR Vengeance
320GB SATA-II 5400U/Min Toshiba (MK3276GSX)
1000GB SATA-II 5400U/Min Seagate Momentus (ST1000LM024)
60GB mSATA-II SSD OCZ Nocti (NOC-MSATA-60G)
Blu-ray Brenner (Blu-Ray Lesen- Schreiben / DVD Multinorm)
BIGFOOT Wireless LAN Killer N 1202 (inkl. Bluetooth)

And now for the tricky part. My second machine is an ASUS R500V notebook running a preinstalled version of Windows 8 64 bits.
This machine has the following specs:

Intel Core i7 - 3610QM, 2,3GHz
nVidia GeForce GT 635M 2GB
8GB SO-DIMM DDR3 RAM
750GB HDD

   On this machine I was not able to boot from the live USB. It took me to the boot menu, but after that, it was just a blank screen, regardless of which option I chose (try or install Ubuntu). I did a search on the internet and I saw that I'm not the only on with issues (something about "secure boot" or "fast boot") but I didn't understand exactly what is the problem.
   I've been dual booting with Ubuntu since Hardy Heron, and in the last 3 years I dropped Windows completely, so I kind of lost touch with dual booting. The problem is that now I need Windows at work, so I need to set up the dual boot.
  Can you please provide a step by step guide on how to do it? I am not a computer genius, but I know my way around and with a little guidance I'm sure I will succeed.
  Thank you in advance and sorry for the long post!

Cheers, Dan

PS: one last question: should I go for the LTS, or the 12.10?

---

### Post by audiomick on 2013-01-11
Regarding dealing with SSDs; Have a look through this thread. From about the fourth post, it gets into a discussion about getting the most out of your SSD, and there are some interesting looking links in there.
[http://ubuntuforums.org/showthread.php?t=2100088]("http://ubuntuforums.org/showthread.php?t=2100088")

I have not tackled a Win8 dual boot yet, but I know that some of the rules have been changed. Have a look at this post for some links to get you started in the right direction (I hope...)

[http://ubuntuforums.org/showpost.php?p=12445747&postcount=2]("http://ubuntuforums.org/showpost.php?p=12445747&postcount=2")

---

### Post by oldfred on 2013-01-11
I have not paid attention to video cards, but some of the very newest by both AMD & nVidia so not work as well as older ones with Linux as the drivers are not as current. With the new release of games, vendors are updating video drivers as they want to make sure it works well. I do not suggest 13.04 for your main install, but you can always instill more than one version. I mainly use 12.04, but have still have many old versions and the new versions on a drive or flash drive.
       Ubuntu 13.04 Desktop Comparison: 6 Desktops, 5 Driver/GPU Combinations
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_raring_desktops1&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_raring_desktops1&num=1)

With 12.04 you have Long Term Support. But the newest features are in 12.10 and 12.10 has the new grub2 2.00 that works with secure boot or pre-installed Windows 8. That version of grub will supposedly be added to 12.04 with the next point release.

I would not allocate any swap on SSD. Either have no swap, swap file or a swap partition on the rotating drive. With 8GB you may never use swap anyway. I do not find I use swap with 4GB of RAM, but do not load lots of apps at once nor edit videos. I have swap on rotating drive just to have some.

       [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

My 62GB SSD has two partitions, one for 12.04 and one for 12.10. I use gpt with a bios_grub partition as I only have BIOS. But your Windows 8 is gpt but uses efi partition for boot files.

Not your model Asus, but I expect Asus to use similar UEFI/BIOS on most systems. UEFI installs:

 Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)

 Asus S46CA Ultrabook Problems with Windows Recovery and grub after dual-boot install with Ubuntu 12.04
[http://ubuntuforums.org/showthread.php?t=2098477](http://ubuntuforums.org/showthread.php?t=2098477)> 
UEFI boot - In order to get into Windows Recovery, I had to hit F9 before GRUB appeared. My mistake was to wait for GRUB to appear, select one of the 2 working Windows options (Windows UEFI loader or Windows Boot UEFI bootx64.efi.bkp) and by that time I was past the possibility to get into Windows recovery system.
         
           ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)

Some additional technical info:
Systems need quick boot or fast boot turned off in UEFI settings. And you need the 64 bit Version of 12.10.
       [https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
            [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
            [https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)

---

### Post by Troll_the_Great on 2013-01-11
Thank you very much for your answers audiomick and oldfred! Looks like things really changed since the last time I needed a dual boot, and I will have allot of reading to do before I take the plunge (especially that on the ASUS I don't have the Windows DVD, the system was preinstalled and I didn't get anything). 
  I will keep you informed if I run into troubles.
  One last question for oldfred: why shouldn't I use the SSD for swap? I'd imagined that because the HDD is an SSD the swap will be as fast as the RAM, no? 

Cheers, Dan

---

### Post by audiomick on 2013-01-11
> **Troll_the_Great said:**
> 
  One last question for oldfred: why shouldn't I use the SSD for swap? I'd imagined that because the HDD is an SSD the swap will be as fast as the RAM, no? 

The SSD would have faster access, but an SSD has a limited number of read/write cycles. This is not really an issue, as is pointed out in this already old article
[http://www.storagesearch.com/ssdmyths-endurance.html]("http://www.storagesearch.com/ssdmyths-endurance.html")

The second thing is that, given a "modern" amount of RAM, you will probably almost never really be using the swap, apart from when you use the hibernate function. 

Put those two together, and it makes sense to put the swap on the HDD rather than the SSD. You would most likely have no real advantage from having it there, and might reduce the useful life of the SSD by using it for the swap.

---

