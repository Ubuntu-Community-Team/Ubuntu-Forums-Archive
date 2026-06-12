---
title: "[SOLVED] please help (wireless) broadcom b43"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by nakama85 on 2008-11-20
I just installed ubuntu on my compaq laptop. I am having some wireless issues.

I already downloaded and installed the proprietary drivers and firmware for the broadcom b43. 
Now My wireless lite turns on however it does not detect my router.

does anyone know whats wrong?

---

### Post by tvtech on 2008-11-20
it's probably a driver issue with that wireless card, you should go over to broadcoms site and see if they have a driver for it for nix.  if not you might want to try using ndiswrapper on the windows driver, I had limited success with it on the same broadcom chipset in a dell laptop.

---

### Post by nakama85 on 2008-11-20
> **tvtech said:**
> it's probably a driver issue with that wireless card, you should go over to broadcoms site and see if they have a driver for it for nix.  if not you might want to try using ndiswrapper on the windows driver, I had limited success with it on the same broadcom chipset in a dell laptop.

thanks. what is ndiswrapper and how do i get it

---

### Post by securitynut on 2008-11-20
I'm in the same exact boat with the wireless. I also just installed Ubuntu om my presario v5000 laptop, and have been trying to get the wireless up and running. I found ndiswrapper through a tutorial for broadcom wireless nic's and had partial success with it. It picked up the card but couldn't find the router, guess i'll have to play around with it for it to find the router.

Here is the link for the ndiswrapper walkthrough i used, hope it helps

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Introduction](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Introduction)

---

### Post by ptn107 on 2008-11-20
> **securitynut said:**
> I'm in the same exact boat with the wireless. I also just installed Ubuntu om my presario v5000 laptop, and have been trying to get the wireless up and running. I found ndiswrapper through a tutorial for broadcom wireless nic's and had partial success with it. It picked up the card but couldn't find the router, guess i'll have to play around with it for it to find the router.

Here is the link for the ndiswrapper walkthrough i used, hope it helps

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Introduction](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Introduction)

My g/f has a v5000 presario with Ubuntu 8.10 on it.  System -> Administration -> Hardware Drivers, and enabling the proprietary drivers does work without the need for ndiswrapper.

---

### Post by nakama85 on 2008-11-20
> **securitynut said:**
> I'm in the same exact boat with the wireless. I also just installed Ubuntu om my presario v5000 laptop, and have been trying to get the wireless up and running. I found ndiswrapper through a tutorial for broadcom wireless nic's and had partial success with it. It picked up the card but couldn't find the router, guess i'll have to play around with it for it to find the router.

Here is the link for the ndiswrapper walkthrough i used, hope it helps

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Introduction](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Introduction)

Hey Thanks. I got it all working. I also have a v5000

I followed this tutorial.

[http://ubuntuforums.org/showthread.php?t=766560&highlight=broadcom+hardy](http://ubuntuforums.org/showthread.php?t=766560&highlight=broadcom+hardy)

even though my wireless card was a slightly different model this still worked perfectly. My computer now detects my router. Hope this helps you like it helped me:guitar:

---

