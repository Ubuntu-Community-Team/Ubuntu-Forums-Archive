---
title: "Compaq CQ50-110 Laptop"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by Matuku on 2008-08-31
Does anyone have this and does it work easily with Ubuntu? Or, if you don't have it can you see anything in the specs that, in your experience, would cause problems?

[http://www.pcworld.co.uk/martprd/product/seo/039078](http://www.pcworld.co.uk/martprd/product/seo/039078)

---

### Post by lenintorres on 2008-09-01
I have a Cq50-103LA, the main difference with the 110 being the Sound Card and the processor (Athlon 64 X2). I installed Ubuntu, 8.04. I tried the 64 bit version, but failed. Then I used the I386 version and worked fine, the system is dual boot now and Ubuntu Installer resized the Vista partition automatically. After Ubuntu installation, I restored the system using te software provided by Compaq (runs automatically after detects the "damage" after installing Ubuntu). 
Main Problems were (easier solved first):
* Video: Replaced the driver shipped with ubuntu with nvidia driver, using envy, very easy.
* Wireless. The 103 model has an Atheros chipset, well supported by the Linux community, but its necessary to download and configure some software.
* Sound. The 103 model has not the Sound Blaster and the sound is choppy, although it seems that using OSS instead of alsa worked fine for some users.

All in all, the system works fine, and in my case, Virtualization software (WinXP guest) qemu/kvm runs fine, but be aware that virtualization extension of processor came disabled in the BIOS of my computer.

---

### Post by cmat on 2008-09-02
Excellent laptop for the price but I've encountered many problems.
[LIST]
[*]No native driver for wireless, you need to use the Windows driver.
[*]NVIDIA driver installed but didn't work well.
[*]Sound was terrible and you have to revert to OSS.
[/LIST] 

These problems should get sorted out in later releases of the kernel, drivers, and Ubuntu.

---

### Post by Matuku on 2008-09-03
> **cmat said:**
> Excellent laptop for the price but I've encountered many problems.
[LIST]
[*]No native driver for wireless, you need to use the Windows driver.
[*]NVIDIA driver installed but didn't work well.
[*]Sound was terrible and you have to revert to OSS.
[/LIST] 

These problems should get sorted out in later releases of the kernel, drivers, and Ubuntu.

I'm having issues getting the LiveCD to work; will go to the busybox shell. Did you encounter this?

EDIT: Got it booted by using noacpi; did you have to do this?

And how did you get the wireless working?

---

### Post by cmat on 2008-09-04
> **Matuku said:**
> I'm having issues getting the LiveCD to work; will go to the busybox shell. Did you encounter this?

EDIT: Got it booted by using noacpi; did you have to do this?

And how did you get the wireless working?

I didn't get the wireless working (didn't bother trying), but most other people on other linux forums got it going. There is a GUI for it call "ndisgtk". You can get the windows driver from the vendors website. As for the busybox error... I downloaded the latest ISO of Ubuntu. Seemed to fix it since I think the bug was submitted to launchpad.

Seems the motherboard was made by nvidia and they don't have linux support for it. I'll contact them soon enough.

---

### Post by Matuku on 2008-09-05
For anyone else who buys this laptop here are the things I learnt:

1) The original 8.04 had serious issues with this laptop about even booting the LiveCD, it would keep going to a "Busybox" shell. This could be worked around by adding all_generic_ide to the boot options. However, the 8.04.1 .iso seemed to have fixed these issues.

2) Neither wireless nor ethernet would work by default in 8.04; however ethernet worked out of the box using 8.04.1 and wireless was fairly easily fixed (see [http://ubuntuforums.org/showpost.php?p=5732839&postcount=10](http://ubuntuforums.org/showpost.php?p=5732839&postcount=10) ).

3) The nvidia driver from the restricted hardware drivers section wouldn't work with the  x-server; it would boot to a black screen. Using EnvyNG enabled the nvidia driver to work but it wouldn't autodetect it; I just manually selected the most recent one (well, the one with the highest number which I assume was the most recent :P).

4) Alsa sound was badly choppy and "crackly"; switching to OSS decreases the occurrences of this but doesn't remove them entirely; I haven't found a solution for this yet.

---

### Post by neoplasticity on 2008-09-07
I have the same laptop and I got the wifi working with madwifi drivers

the alsa was driving the sound but it was very poor quality with a skipping, staticy sound so i tried to install OSS

however OSS failed

root@laptop:~/Desktop# osstest
Sound subsystem and version: OSS 4.0 (b1016/200807241529) (0x00040003)
Platform: Linux/i686 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008


NOTICE! You don't have any audio devices available.
        It looks like your audio hardware was not recognized
        by OSS. Please contact 4Front technologies for help
        ([http://www.opensound.com/support.cgi](http://www.opensound.com/support.cgi)). Don't forget to
        include your soundon.log file to the support request.


install seemed to go fine but when i tried to do OSS test.. that's what i got.

how did you sucessfully install OSS on this laptop?

this is how i got the wifi working

[http://ph.ubuntuforums.com/showthread.php?t=800686](http://ph.ubuntuforums.com/showthread.php?t=800686)

---

### Post by Matuku on 2008-09-07
Aha, I tried the madwifi drivers but just the default one from the madwifi main page, which wouldn't install properly; didn't realize they had a specific one for the 5007. Thank you for that, I shall keep it in mind for when I need to reinstall.

I didn't do anything special to install the sound (at least, not that I remember). I just tried entering osstest into the terminal but it didn't recognise the command; did you have to install something to enable that test?

---

