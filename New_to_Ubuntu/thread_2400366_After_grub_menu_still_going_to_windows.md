---
title: "After grub menu still going to windows"
date: 2018-09-05
forum: New to Ubuntu
---

### Post by harrygoode22 on 2018-09-05
I am attempting to dual boot Ubuntu 18.04 onto my hp Envy 13, with Window 10 already installed. I have partitioned the hard drive and created a bootable usb using Rufus 3.1. I have disabled the Legacy and Secure boot, as well deselecting the fast boot option in power setting. 

I get to the grub menu, select "Install Ubuntu", then I see the Ubuntu loading screen and then Windows 10 starts.

I am completely confused by the situation as I have done nothing different to the last two machines I install Ubuntu on, and yet this will not work.

---

### Post by oldfred on 2018-09-05
Does the try Ubuntu work?

What are specs.  I think Envy 18 model name has been used for various configurations.

---

### Post by harrygoode22 on 2018-09-05
I am trying to install Ubuntu on my new laptop. I have not had a problem with my last two laptops but I cannot seem to get this to work. Is it possible that Ubuntu is simply not going to work on my machine?

---

### Post by harrygoode22 on 2018-09-05
No, the try Ubuntu takes me back to the grub menu. Hopefully the specs you need are here?
 [ATTACH=CONFIG]280993[/ATTACH]

---

### Post by 8h567t20 on 2018-09-05
Hello i am not sure if it will run on you machine but my myc laptop is hp noteboo g5 an linux works fine. You could boot in the live enviorment  make sure legacy boot is on if you are going to install linux on your laptop and back up whats ever on you laptop now

---

### Post by Autodave on 2018-09-05
Are you trying to dual boot with Windows?  Did you disable *fastboot *in the BIOS?

---

### Post by oldrocker99 on 2018-09-05
If you're doing a full installation, and the BIOS allows legacy boot, not just UEFI, choose legacy. In my experience, if you boot UEFI,the installation will appear to work just fine, then GRUB will not install, making the computer unbootable. Using legacy boot works every time.

---

### Post by oldfred on 2018-09-05
Issues are often common for similar configurations by brand, even if different models.
Bigger difference if Intel or AMD with same brand.

[https://ubuntuforums.org/showthread.php?t=2379728](https://ubuntuforums.org/showthread.php?t=2379728)

While I do not recommend using a version that is not yet released, I just noticed my test copy of 18.10 has a newer kernel. Often with very new hardware it takes a release or two before all the updates are in a standard  distribution. If willing to experiment you could try 18.10 daily. It may not even always work as sometimes changes are not sync'd but in last couple years that is now rare.  But always best to keep a LTS version as main working install. I have 18.04, 16.04 & 14.04 still bootable on my system and then have 18.10 just to see if it still works on my system.

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by oldfred on 2018-09-05
Theads merged since same issue.
Please do not post same issue in two threads.

---

### Post by GMeister on 2018-12-01
Just bought this laptop.  Had similar issues described here with 18.04 - I always opt for the LTS by default.  Couldn't even "Try Ubuntu" from the Grub menu as after the splash it would crash out and return to the Grub menu.  Pressing escape on the splash menu I was able to see that it appears to die after running the irqbalance.service.  Note that I was only able to get the Grub menu when burning the USB with Rufus in DD mode (as opposed to ISO mode).
Knowing that this is a relatively new machine, I tried 18.10, which appears to have worked.  Will try to install and let you know.

---

