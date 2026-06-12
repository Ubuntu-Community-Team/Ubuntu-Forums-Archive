---
title: "Unable to Install or Try Ubuntu 12.0.4"
date: 2013-12-12
forum: New to Ubuntu
---

### Post by bradleyswain1 on 2013-12-12
I'm running 64 bit Windows on an SSD right now. I have 200GB of un-formatted space set aside on a separate hard drive for Ubuntu.

My system specs are:

[LIST]
[*]ASRock Z77 Extreme4 motherboard
[*]i5-3570k CPU
[*]GeForce GTX 670 GPU
[/LIST]

I downloaded the x64 iso "ubuntu-12.04.3-desktop-amd64" and I've used 3 different services to create a bootable USB with that iso. When a boot to the USB the purple Ubuntu screen comes up. From there if I select "Try Ubuntu before Installing" or "Install" it scrolls through some text and gets stuck here: [http://i.imgur.com/2OjsWag.jpg](http://i.imgur.com/2OjsWag.jpg)

I've read around and tried a couple things already. Booting from the USB in UEFI mode takes me to a black and white GRUB screen with three options; "Install", "Try", and "Check Memory". Selecting "Try" or "Install" takes me to a black screen where nothing happens.
I've also tried the nomodest boot option from the regular purple Ubuntu screen. It gets stuck in the exact same place.


Thanks in advance for any help.

---

### Post by fantab on 2013-12-13
What version of Windows?

Sounds to me like a graphic card related issue, use '[**nomodeset**]("http://ubuntuforums.org/showthread.php?t=1613132&p=10069997#post10069997")' option and tell us if it helps.

---

### Post by mörgæs on 2013-12-13
How does a live boot of 13.10 work?

---

### Post by buzzingrobot on 2013-12-13
Google on "usb failed command identify packet service" from the image you posted.  I see reports of similar errors being attributed to motherboards with ports that don't fully support ATAPI.  Dunno if that will help, but it might be worth a look.

---

### Post by bradleyswain1 on 2013-12-13
> **buzzingrobot said:**
> Google on "usb failed command identify packet service" from the image you posted.  I see reports of similar errors being attributed to motherboards with ports that don't fully support ATAPI.  Dunno if that will help, but it might be worth a look.

I found what looks like a  solution: [http://askubuntu.com/questions/228927/ubuntu-12-04-install-failed-command-identify-packet-device](http://askubuntu.com/questions/228927/ubuntu-12-04-install-failed-command-identify-packet-device)

I'm booting from a USB so I can't really change the SATA ports but I'm also not sure how to edit the iso or the files on the bootable USB. Not really sure where to go from here.

---

