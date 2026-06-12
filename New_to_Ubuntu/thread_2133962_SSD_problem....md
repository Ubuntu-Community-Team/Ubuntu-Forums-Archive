---
title: "SSD problem..."
date: 2013-04-09
forum: New to Ubuntu
---

### Post by Erik The Pope on 2013-04-09
I have a Intel SSD with major problem. Here's quickly what I did: Installed XP Pro to it. Installed Unbuntu to another mech. HD with Grub to dual-boot. Restarted but it went to XP w/o Grub.  I assume that Ub put Grub on the mech HD so when it booted it did so from the XP partition. All the stuff I read on SSDs said to use ACHI; did that in BIOS setup. Used GParted to format an NTFS partition with the 1 mb offset. Fine. XP wouldn't load. Decided to not load XP. Tried to change the SSD partition to Linux with GParted & a couple other Linux CDs but none of them would load, they just stopped with a blinking cursor on the top-left. Couple questions: Do you have to set BIOS to ACHI for Linux? Did I lunch the SSD? I am knowledgeable on Win but this is the first time I've tried to use Linux/Ubuntu. Thanks!

---

### Post by oldfred on 2013-04-09
I had to stop booting XP on my hard drive, when I got my SSD. My install of XP did not have drivers for AHCI and it was my understanding I had to do a new install to get those to work. Also some need drivers for SATA. I can still boot my old XP, but have to go into BIOS turn off AHCI.
I do not think XP will work well with SSD. It just is too old to correctly support trim and other features needed.

Ubuntu booted fine with AHCI on or off, It was my XP that would not boot with it on. And it is also my understanding you need AHCI for trim to work. Not sure about Windows?

       Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
Arch suggests gpt for SSD. Only if installing Windows on older system may you want MBR as Windows only boots from gpt with UEFI. 
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

I did not turn trim on initially, so I used the fstrim command. Some say that is preferred way, but I do not know.


 fred@fred-Precise:~$ sudo fstrim -v /
/: 23267893248 bytes were trimmed
[https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing](https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing)
sudo hdparm -I /dev/sdX
Alternate to discard, call fstrim via cron
[http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html](http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html)
test if trim working using hdparm
[http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2](http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2)

---

### Post by Erik The Pope on 2013-04-09
I'm more interested in making the SSD work with Ubuntu. I've decided not to put XP on it at all. Did I fry the SSD?

Erik The Pope

---

### Post by Paqman on 2013-04-09
No, you didn't fry the SSD. Software doesn't kill hardware.

If you're not bothered about installing Windows any more, boot up into your Ubuntu live disk/USB and choose the option to use the whole disk to install. Yes, you will need to set BIOS to AHCI, like you should with any SATA drive.

---

### Post by Erik The Pope on 2013-04-09
Paqman said: "B[COLOR=#000000]oot up into your Ubuntu live disk/USB and choose the option to use the whole disk to install." Well, I've already tried this but I will again with a different disc. Also make sure that AHCI is set. BTW, I didn't know that you were supposed to set ANY SATA drive to AHCI. I don't believe I ever did until I started using an SSD. My other computer has an SSD but since I read about them, I did set AHCI on the BIOS. D'oh![/COLOR]

---

### Post by Erik The Pope on 2013-04-11
So I disconnected the other two HDs & took out the sound card so there's only the SSD & the video card with 4 MB RAM. Still all the discs I tried (64 bit Dream Studio, Ubuntu Studio, 12.04 & 12.1) and (32 bit 12.04 & 12.1 plus a 12.04 LTS that I D/L today) failed to complete booting so I couldn't tell it to use the whole disc or anything. Also tried a few Linux partition managers. Reset the BIOS to defaults except setting the SATA to ACHI. Checked to see if my MB P5E3 Premium would do 64 bit (Core 2 Extreme quad-core chip) and I'm pretty sure it will but even so, I tried to install the 32 bit Ubuntu. Did the RAM check, OK.

So what the hell have I missed here? After doing my taxes, I will re-seat the RAM just in case. Help me Obi-Wan Kenobi, you're my only hope...

Erik The Pope

---

### Post by zrdc28 on 2013-04-12
I have loaded several different versions of linux onto my asus eee901 with the ssd's and have never used anything but SATA as my drive type.
I loaded ubuntu with no problems whatsoever but it did not have the resources  for a large distro and it was just slow. The last one was lubuntu
and it runs fine. You might just try the sata setting!

---

### Post by Erik The Pope on 2013-04-18
Solved. Well, hallelujah brothers & sisters! Problem solved - I think. It was some kind of memory problem. I had 4 sticks of 1 GB ram in there & thought if might be faulty so I did the memtest on one of the partition CDs that I had & it passed several times. So I took out the two that I just added (same exact memory) and this time Linux loaded. Took the memory out & substituted the other, still worked. Added the extra 2 GB & still worked. I guess it was just seated wrong or something. Or maybe the gremlins got tired of messing with me!  :P

---

### Post by Erik The Pope on 2013-04-18
Still had the BIOS set to SATA, not ACHI. Might try setting it to AHCI & see what happens.

---

### Post by d4m1r on 2013-04-19
> **Paqman said:**
> No, you didn't fry the SSD. Software doesn't kill hardware.

Yes it can actually and SSDs are especially susceptible to OS issues causes hardware failures.

@Erik, it also doesn't mean your RAM was bad. By reseating RAM, it also clears all your (BIOS) settings, so if you had configured something incorrectly, it would have restored all the defaults. Just another possible explanation for why it is now seemingly working...

---

