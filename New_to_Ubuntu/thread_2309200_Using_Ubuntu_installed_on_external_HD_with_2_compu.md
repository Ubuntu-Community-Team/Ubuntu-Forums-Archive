---
title: "Using Ubuntu installed on external HD with 2 computers"
date: 2016-01-08
forum: New to Ubuntu
---

### Post by sonicwind on 2016-01-08
Can I install Ubuntu on an external hard drive and take it to more than one computer? Does that present issues with anything such as fstab?

The fstab Wiki says removable devices are usually mounted by gnome-volume-manager? Is that still true if the Ubuntu OS is on it? Also, a UUID stays with the drive no matter what computer, is that right?

To be clear, the Ubuntu OS would be on the external hard drive. Windows 7 on both internal drives on the computers.

Thank you guys.

---

### Post by grahammechanical on 2016-01-08
Running Ubuntu from an external drive would be no different from runing Ubuntu from a USB memory stick. There are 2 things to watch out for.

A) By the default the installer installs the Linux boot loader (Grub) on the MBR of the first hard disk (sda). And it will look for its configuration files in /boot on the drive Ubuntu is installed on. If the boot loader gets installed on the internal drive (sda?) then whenever the external drive is removed loading Windows will fail & the external drive will not load Ubuntu when put in another machine.

You need to make sure that Grub is installed onto the external drive.

b) Do not install a proprietary video driver as you may get a video adapter - driver mismatch when connecting to another computer. So, during installation do not tick the box Install third party software as that will install a proprietary video driver. The open source video driver will be used instead and that should work with various video adapters.

Alternatively, after installation go to System Settings>Software & Updates>Additional Drivers tab and change the video driver to the open source video driver.

Regards.

---

### Post by Bucky Ball on 2016-01-08
> **grahammechanical said:**
> You need to make sure that Grub is installed onto the external drive.

And you need to make sure that you change the boot order in the BIOS of whatever machine you boot it from so it boots from your external device. There may be an issue with UEFI and BIOS installs, but don't really have the knowledge to confirm either way.

---

### Post by sonicwind on 2016-01-08
Thank you guys.

Grahammechanical - A) If there's one thing that's been drilled into my head after reading these forums and the Wiki's the last few weeks, this is it! I've got that down. I will click "Something Else" and put GRUB on the external. :D

B) Both computers are the exact same model and hardware components, so I think I will be good with this one as well.

Bucky - Or I could just f12 (boot menu) and select the one I want, right?

I should have mentioned both systems use BIOS.

---

### Post by Bucky Ball on 2016-01-08
Then install Ubuntu on the 'mobile' drive in BIOS mode and all will be fine there. All looks fine. Give it a go.

---

