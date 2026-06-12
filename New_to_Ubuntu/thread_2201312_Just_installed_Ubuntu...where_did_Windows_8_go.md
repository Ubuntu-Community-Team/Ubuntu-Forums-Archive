---
title: "Just installed Ubuntu...where did Windows 8 go?"
date: 2014-01-23
forum: New to Ubuntu
---

### Post by Jesse_Fulcher on 2014-01-23
Hey Guys,

The title said, Absolute Beginners Sectino, so that is where I started. Haha, I'm very new to this but very excited to learn today I just downloaded the latest version of Ubuntu onto a DVD and changed the UEFI settings on my windows 8 computer so that i could instal (it was a lot easier then expected). After getting it installed everything went great, but my quesiton is where is windows 8. When I restart my computer it doesn't give me the option to pick an OS like it does when you dual boot, did I delete Window's 8? Where did it go? How do I access it? Where are my documents and informaiton from windows 8?

Thanks for all of your help.

---

### Post by access1denied on 2014-01-23
did you try changing the UEFI settings back?

---

### Post by GaryTheCat on 2014-01-23
Click the Ubuntu logo in the top left of your screen and type Disks. Open Disks and it'll give you a summary of how each disk on your machine is partitioned - generally the partitions that aren't ext4 are something to do with windows (e.g. NTFS).

If it looks like there's evidence of Windows then tinker with the UEFI settings or try boot repair from a live DVD / USB

---

### Post by Jesse_Fulcher on 2014-01-23
I tried that and I changed the order back but it didn't seem to do the trick. Any other suggestions other then find a friend who knows what they are doing? haha

---

### Post by squakie on 2014-01-23
Try boot repair.  You can download it directly into your ubuntu installation if you want or use it on cd/dvd.  Just take the defaults.

---

### Post by mastablasta on 2014-01-24
and as mentioned first check in disks if windows 8 is still there (since you didn't explain how you installed it)

---

### Post by fantab on 2014-01-24
> **Jesse_Fulcher said:**
> 

The title said, Absolute Beginners Sectino, so that is where I started. Haha, I'm very new to this but very excited to learn today I just downloaded the latest version of Ubuntu onto a DVD and changed the UEFI settings on my windows 8 computer so that i could instal (it was a lot easier then expected). After getting it installed everything went great, but my quesiton is where is windows 8. When I restart my computer it doesn't give me the option to pick an OS like it does when you dual boot, did I delete Window's 8? Where did it go? How do I access it? Where are my documents and informaiton from windows 8?



If you can boot Ubuntu then open Terminal [ctrl+alt+T], run the following commands and post its output here:
```
sudo fdisk -l
sudo parted -l
```

If you can't boot Ubuntu then use Ubuntu DVD/USB, "Try Ubuntu" and post the output of the above.


Can you tell us how and what exactly did you "changed the UEFI settings"?

---

### Post by danny.techify on 2014-02-02
Try going into your boot menu by hitting the correct key(It's different for each manufacturer) and you should see a list check for something that says "Windows Boot Manager" or something related to Windows. If you don't see it boot into Ubuntu and go into gparted if you don't have it open the terminal and type.

> sudo apt-get install gparted

Then open it and look for your Windows partition. If you can't find it you may of replaced Windows with Ubuntu. It may be related to the UEFI settings being changed. So can you post what you changed?

---

