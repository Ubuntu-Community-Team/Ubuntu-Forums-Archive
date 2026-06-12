---
title: "Quick Noob Question: Swapping Wireless Drivers"
date: 2011-09-14
forum: New to Ubuntu
---

### Post by Ritzbitts on 2011-09-14
Hey, so I've been using Ubuntu for a while, but I can't seem to figure this out, so advice is appreciated.

I recently set up my MacBook Pro to triple boot Windows, Linux, and OS X. No problems there. Ubuntu is working 100%, but when I tried to install the aircrack-ng suite, I ran into some problems.

My wireless chipset is Broadcom bcm4322. I understand there are issues with packet injection with this card, but the bcm43xx driver can be patched. When I ran Ubuntu from the LiveCD, I was given the option to install the b43 driver, or the Broadcom STA driver. After installing, I was only given the option for the STA driver.

It is my understanding that many of the issues I'm encountering with the STA driver are irrelevant when the b43 driver is present. I installed the b43 fcutter package, but beyond that I'm not sure how to enable it. I understand I have to blacklist the old driver and perform a modprobe, but I'm not 100% sure I've gone about this the right way and would greatly appreciate some guidance before I muck up my system.

=========
So in a nutshell, how do I remove the bcm43xx "Broadcom STA" driver and replace it with the Broadcom B43 driver? Thanks!
=========

---

