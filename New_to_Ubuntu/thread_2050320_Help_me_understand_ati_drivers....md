---
title: "Help me understand ati drivers..."
date: 2012-08-30
forum: New to Ubuntu
---

### Post by lopean on 2012-08-30
Hello All,

Ok, so I picked up ubuntu off an on again through college so I'd say my experience is minimal and in most cases skewed. That being said, Here's my question. If I'm interested in getting my Two Radeon HD 4870 (crossfired) graphics cards to work their best, should I be using the proprietary drivers (fglrx) that ubuntu offers or should I install the latest catalyst software & drivers off the ATI website? Which is better for my case? Whats the difference? How do I do this?

I ask this because I'm excited about steam being run natively under linux and want to have the best drivers setup for gaming. I already installed the proprietary drivers (not post release) because Ubuntu told me too. 

The drivers i have installed appear to be working but when i type "fglrxinfo" in the command prompt it only displays one card. How do I know its setup the crossfire correctly? 

If anyone could answer these questions or direct me to the correct threads I would greatly appreciate it. I am currently running Ubuntu 12.04LTS 64bit. If you need anymore system info I can provide more when i get home.

---

### Post by QIII on 2012-08-30
When you installed the driver, did you do 

```
sudo aticonfig --adapter=all --initial
```?  That initializes all of your cards in xorg.conf.

The driver in the Ubuntu repo is 12.4 and is the offical 12.4 ATI driver.  The current ATI driver is 12.8.  The problem with installing from the ATI website is that if the kernel is updated during your normal Ubuntu updates, you have to reinstall the driver.  Using the one in the repo does not require a reinstallation.

Also, the fglrx-updates (called Post Release Update in the GUI, I believe) often does not work, so I would avoid it.

---

### Post by lopean on 2012-08-30
> **QIII said:**
> When you installed the driver, did you do 

```
sudo aticonfig --adapter=all --initial
```?  That initializes all of your cards in xorg.conf.

The driver in the Ubuntu repo is 12.4 and is the offical 12.4 ATI driver.  The current ATI driver is 12.8.  The problem with installing from the ATI website is that if the kernel is updated during your normal Ubuntu updates, you have to reinstall the driver.  Using the one in the repo does not require a reinstallation.

Also, the fglrx-updates (called Post Release Update in the GUI, I believe) often does not work, so I would avoid it.

Wow! Thanks for the quick reply. No i didn't initialize the cards apparently. I thought ubuntu would have detected them automatically, hence the enticing hassle free option to update to proprietary drivers. :???:

So will this auto setup the crossfire or is there a way to access a catalyst like gui and make sure everything is good?

---

### Post by QIII on 2012-08-30
```
sudo apt-get install fglrx-amdcccle
```

Will install Catalyst Control Center.

But you need to do the initialization of xorg.conf and reboot first before using it.

---

### Post by lopean on 2012-08-31
> **QIII said:**
> ```
sudo apt-get install fglrx-amdcccle
```

Will install Catalyst Control Center.

But you need to do the initialization of xorg.conf and reboot first before using it.

Thanks again, I already had catalyst installed. After getting into the catalyst software (I just did a search from the start menu) I was able to successfully enable crossfire. It took a couple of reboots though. Everything appears to be working now. Thanks for your help mysterious linux superhero. :guitar:

---

