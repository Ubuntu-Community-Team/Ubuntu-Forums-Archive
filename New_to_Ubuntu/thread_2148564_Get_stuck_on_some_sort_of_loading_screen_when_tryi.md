---
title: "Get stuck on some sort of loading screen when trying to install ubuntu from boot"
date: 2013-05-25
forum: New to Ubuntu
---

### Post by peterspliid on 2013-05-25
Hi

I have loaded ubuntu to a 16GB usb drive using Universal USB Installer (provided by the official ubuntu site). I already have windows 7 64bit installed on my system (freshly installed has not been used at all), as I wish to dualboot. When I boot from my USB, I get to the screen where I choose whether to run or install ubuntu. Whenever I click run OR isntall, it goes to a black screen with a lot of text running through the screen until it gets stuck. I have attached a snapshot of exactly where it gets stuck.

I have tried with both ubuntu-12.04.2-desktop-i386 and ubuntu-12.04.2-desktop-amd64, no difference at all. In addition I have tried using two different USB drives, still no effect. I'm not installing on UEFI, meaning it's all being done on legacy mode. Please let me know if you need any more information. Thanks a lot in advance.

- Spliid

---

### Post by 2F4U on 2013-05-26
Can you provide some information about your hardware? I see that Ubuntu loads nouveau but there is also a line suggesting that vga_switcheroo is enabled, so you seem to have a switchable graphics card.

---

### Post by peterspliid on 2013-05-26
Sure

Intel® Core™ i7-3630QM Processor, Windows 8 64bit (replaced with w7 now), NVIDIA® GeForce® GTX 670MX with 1.536 MB RAM, 750 GB HDD, 16 GB RAM.

Thanks!

---

### Post by fantab on 2013-05-26
Try to boot your Ubuntu USB with "**nomodeset**" as instructed here: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

By the way, how did you replace Win8 with Win7? How did you remove UEFI and what else did you do?

---

### Post by peterspliid on 2013-05-26
Thanks, ill try that as soon as I can. To install w7 I went to the bios and changed uefi to legacy and disabled fast boot and secure boot

---

