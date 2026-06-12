---
title: "Dual-boot 2 Sata"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by Bakado on 2008-10-11
I've looked around and only found stuff with IDE or a mixture of IDE and SATA.

I just got finished building my computer(First one) and I had originally planned on partitioning Ubuntu and XP but during the installation of Ubuntu I just said forget it and made it entirely Ubuntu 8.04.  Afterwords I decided to get a second SATA and dual-boot XP on one and Ubuntu on the other.  Before I actually went out and bought the second HDD I decided to look up instructions to see what I had in store for my self, and haven't been successful in finding 2 SATA installation instructions.  Because I am a complete n00b with this kind of stuff is there someone who can give me an idiot proof run through?

After installing Ubuntu 8.04(My first time EVER using Linux of any type) I discovered it was a little harder to use than I'd originally expected and even considered removing it but after all the help on this site and others I've found I actually prefer it OVER Windows, I just want Windows but because I don't like not finishing projects I start I want to go thought the XP install, thanks for all the help in advance

---

### Post by handydan918 on 2008-10-11
> **Bakado said:**
> I've looked around and only found stuff with IDE or a mixture of IDE and SATA.

I just got finished building my computer(First one) and I had originally planned on partitioning Ubuntu and XP but during the installation of Ubuntu I just said forget it and made it entirely Ubuntu 8.04.  Afterwords I decided to get a second SATA and dual-boot XP on one and Ubuntu on the other.  Before I actually went out and bought the second HDD I decided to look up instructions to see what I had in store for my self, and haven't been successful in finding 2 SATA installation instructions.  Because I am a complete n00b with this kind of stuff is there someone who can give me an idiot proof run through?

After installing Ubuntu 8.04(My first time EVER using Linux of any type) I discovered it was a little harder to use than I'd originally expected and even considered removing it but after all the help on this site and others I've found I actually prefer it OVER Windows, I just want Windows but because I don't like not finishing projects I start I want to go thought the XP install, thanks for all the help in advance

I have a box with this setup, and 2 sata drives is really a non-issue. 
I would suggest doing the following;
1)Disconnect existing Ubuntu drive.
2)Connect new sata drive.
3) Install Windows to the new drive
4)Re-connect Ubuntu drive, and reinstall GRUB. I will automatically detect windows and allow you to select either O/S at boot time.

Post back if you get in trouble.

---

