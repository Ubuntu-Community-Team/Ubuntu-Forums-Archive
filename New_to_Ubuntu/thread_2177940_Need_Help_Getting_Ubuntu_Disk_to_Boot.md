---
title: "Need Help Getting Ubuntu Disk to Boot"
date: 2013-10-01
forum: New to Ubuntu
---

### Post by AyJJ7fd on 2013-10-01
I'm trying to install Ubuntu 13 onto one of my PC's internal drives. I currently have Ubuntu 12 on a 160gb internal drive, and two 1tb internal drives both formatted to ext4. I have 8000mb swap space on both of the 1tb drives. I have Ubuntu on a flash drive, and I can go through the install process fine, installing Ubuntu onto one of my 1tb drives through the Advanced section and setting that drive to be the bootloader drive. It installs smoothly, tells me to reboot, and I do so but whenever I try to boot to the drive I just installed Ubuntu onto, I get a black screen with a bleeping underscore in the corner. Going into BIOS and changing the boot order doesn't help.
Any help? I'm at a loss.

---

### Post by sharathcshekhar on 2013-10-01
It's possible you might have corrupted the grub. Have you tried installing grub on your HDD (boot from a livedisk/flashdrive to do so).  There are plenty of posts explainins howto install grub from livedisk. Post back if you find it hard to follow those.

---

### Post by oldfred on 2013-10-01
Welcome to the forums.

Often a video issue. What video card/chip do you have?
Do you get grub menu or can you hold shift key down from BIOS boot and get grub menu. The add nomodeset to linux line. Use e for edit, scroll down to linux line in grub boot stanza and replace quiet splash with nomodeset. It also then will show boot process.

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

---

### Post by newb85 on 2013-10-01
Boot-repair is a powerful utility for this kind of problem. I believe it's in the repos for 13.04, so running it from the live disc should be easy. 

Alternatively, you might try this: boot from the live disc, mount and chroot into the Ubuntu partition, then update grub.

---

### Post by AyJJ7fd on 2013-10-01
> **sharathcshekhar said:**
> It's possible you might have corrupted the grub. Have you tried installing grub on your HDD (boot from a livedisk/flashdrive to do so). There are plenty of posts explainins howto install grub from livedisk. Post back if you find it hard to follow those.


I followed this guide to install grub onto /dev/sdc. Everything went smooth except executing 'update-grub' was only targetting /dev/sda, and I don't know how to update /dev/sdc. I tried booting the drive with Ubuntu installed on it and same black screen with blinking underscore. 


> **oldfred said:**
> Welcome to the forums.

Often a video issue. What video card/chip do you have?
Do you get grub menu or can you hold shift key down from BIOS boot and get grub menu. The add nomodeset to linux line. Use e for edit, scroll down to linux line in grub boot stanza and replace quiet splash with nomodeset. It also then will show boot process.

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

I have a Radeon HD6950 video card. I don't get to the grub menu; I'm not sure what you mean by holding the shift key down from BIOS boot. Do you mean while booting into BIOS?

---

### Post by AyJJ7fd on 2013-10-01
> **newb85 said:**
> Boot-repair is a powerful utility for this kind of problem. I believe it's in the repos for 13.04, so running it from the live disc should be easy. 

Alternatively, you might try this: boot from the live disc, mount and chroot into the Ubuntu partition, then update grub.
Trying Boot-repair now. I went to Advanced options > Main options > Reinstall GRUB, GRUB Location > OS to boot by default: sdc2. Should I separate /boot partition and/or /boot/efi partition? Here is my BootInfo summary (I thought maybe it'd be helpful)
[BootInfo summary]("http://cl.ly/RiCh")

Edit: I tried reinstalling GRUB onto dev/sdc and it gives me an error saying "GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). I opened GParted but im not sure how to make a BIOS-Boot partition and which disk to make it on.

---

### Post by oldfred on 2013-10-01
I do not know AMD, as I have nVidia.

When computer first starts BIOS posts, then grub loads. From BIOS until grub menu appears hold shift key down. Some say left key. If UEFI system some also find escape key works.

Not sure if still current or not.
 [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)

---

### Post by AyJJ7fd on 2013-10-01
> **oldfred said:**
> I do not know AMD, as I have nVidia.

When computer first starts BIOS posts, then grub loads. From BIOS until grub menu appears hold shift key down. Some say left key. If UEFI system some also find escape key works.

Not sure if still current or not.
 [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)

My issue is that grub is not loading. So I'm not given any opportunity to hold the shift key after BIOS.

---

### Post by oldfred on 2013-10-01
You have an efi partition and are booting in UEFI mode with your install. But Boot-Repair indicates you current version is not UEFI capable? Did you install again with the 32 bit version? Only the 64 bit version is UEFI capable.

But you must have booted Boot-Repair in BIOS boot mode as then you need a bios_grub partition. Boot the Boot-Repair live installer or repair disk in UEFI mode and rerun repairs, if you have installed with 64 bit version and use a 64 bit version in UEFI mode with Boot-Repair.

since two of your three drives are now gpt, I might suggest making all three gpt.

       GPT Advantages (older but still valid)  srs5694 post #2:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

---

### Post by morgan4 on 2013-10-02
Try this....

[https://coderwall.com/p/ydbldg](https://coderwall.com/p/ydbldg)

---

