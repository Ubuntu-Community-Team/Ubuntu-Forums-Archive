---
title: "problem with ubuntu 10.04 installation"
date: 2012-01-22
forum: New to Ubuntu
---

### Post by kiranmatrixlee on 2012-01-22
i have intel i5 system.when i try to install ubuntu 10.04 in my system,it sows the following error.
```
busy v1.13.3 (ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
```How can i install ubuntu 10.04?

---

### Post by 3rdalbum on 2012-01-22
Have you tried checking the CD's integrity?

If you downloaded the ISO file using Bittorrent, then you've already checked the integrity of the file automatically; if you downloaded the ISO using your web browser, then you should try checking the ISO file against the MD5 hashes provided at the Ubuntu download page.

If the check fails, you need to try downloading the ISO file again. This time use Bittorrent.

When the MD5 hashes match (or if you used Bittorrent to download), then boot up the Ubuntu CD and when it shows you a little icon of a keyboard and a man at the bottom of the screen, press the spacebar. You'll be given a menu where you can choose several options, including "Check CD for errors". Use this.

If the CD check fails, then you need to reburn the ISO file to CD. Use a good quality CD-R and burn at a low speed like 8x. Otherwise, if the CD check has worked fine, then you probably need a later version of Ubuntu. Try the latest, Ubuntu 11.10.

It might be a good idea to use the latest Ubuntu anyway as it has later bug fixes, and the latest desktop environment (Unity) that will be used in all future versions of Ubuntu. If you learn the Gnome 2 desktop used in Ubuntu 10.04, you'll basically be learning a dead-end desktop environment.

---

### Post by benpack101 on 2012-01-22
How have you been trying to install Ubuntu? USB disk, CD?

---

### Post by kiranmatrixlee on 2012-01-22
> **benpack101 said:**
> How have you been trying to install Ubuntu? USB disk, CD?


cd.
I checked more than one cds and the result is same.

---

### Post by kiranmatrixlee on 2012-01-22
> **3rdalbum said:**
> Have you tried checking the CD's integrity?

If you downloaded the ISO file using Bittorrent, then you've already checked the integrity of the file automatically; if you downloaded the ISO using your web browser, then you should try checking the ISO file against the MD5 hashes provided at the Ubuntu download page.

If the check fails, you need to try downloading the ISO file again. This time use Bittorrent.

When the MD5 hashes match (or if you used Bittorrent to download), then boot up the Ubuntu CD and when it shows you a little icon of a keyboard and a man at the bottom of the screen, press the spacebar. You'll be given a menu where you can choose several options, including "Check CD for errors". Use this.

If the CD check fails, then you need to reburn the ISO file to CD. Use a good quality CD-R and burn at a low speed like 8x. Otherwise, if the CD check has worked fine, then you probably need a later version of Ubuntu. Try the latest, Ubuntu 11.10.

It might be a good idea to use the latest Ubuntu anyway as it has later bug fixes, and the latest desktop environment (Unity) that will be used in all future versions of Ubuntu. If you learn the Gnome 2 desktop used in Ubuntu 10.04, you'll basically be learning a dead-end desktop environment.


My system configuration is high end.but the ubuntu 11.10 works very slowly.eg:while click on close button,there is some delay.every process make a delay.

---

### Post by kiranmatrixlee on 2012-01-22
this screen troubled me.

---

### Post by sudodus on 2012-01-22
Excuse the questions, that may be stupid! But too be sure of your situaton: Are you running a live session booted from your CD or have you installed Ubuntu and run from the internal HDD?

Sometimes there are problems with the graphics card, that slows things down even on high-end computers. Please let us know more about your computer specs, for example, the graphics chip or card.

---

### Post by kiranmatrixlee on 2012-01-22
> **sudodus said:**
> Excuse the questions, that may be stupid! But too be sure of your situaton: Are you running a live session booted from your CD or have you installed Ubuntu and run from the internal HDD?

Sometimes there are problems with the graphics card, that slows things down even on high-end computers. Please let us know more about your computer specs, for example, the graphics chip or card.

i have core i5 processor and a high end motherboard.no graphics card with my computer.

I am trying to install from a live cd.the loading graphics is not proper.after loading it shows the result as shown in the above picture. 

is there any idea?

---

### Post by sudodus on 2012-01-22
> **kiranmatrixlee said:**
> i have core i5 processor and a high end motherboard.no graphics card with my computer.

I am trying to install from a live cd.the loading graphics is not proper.after loading it shows the result as shown in the above picture. 

is there any idea?
1. Can you run Ubuntu just to test it, not yet trying to install it? I think that it is called 'Test Ubuntu' in the first menu, the way to run from the CD or USB drive that is commonly called 'Run a live session'.

2. If you have a working Windows installed, please use that, and (via the Control Panel) find out what graphics chip is on the motherboard (intel, nvidia, ati ...)

*. Don't give up yet! There are many things to try, and almost always there is a good solution, so that Ubuntu will run on your computer.

---

### Post by Demonjames on 2012-01-22
Could it possibly be a bad iso, I've had an issue with the iso somehow was corrupted and no matter what i burned it to, usb, cd, dvd it just caused an error i finally had to find a different mirror.

---

### Post by ld114 on 2012-01-22
Maybe check if the linux kernel in 10.04 will support the much newer i5 processor. I think I read somewhere that you may need to use a newer kernel - have you tried Ubuntu 11.10 (or even 11.04)?

---

### Post by sudodus on 2012-01-23
> **ld114 said:**
> Maybe check if the linux kernel in 10.04 will support the much newer i5 processor. I think I read somewhere that you may need to use a newer kernel - have you tried Ubuntu 11.10 (or even 11.04)?
This is a good idea, [I]kiranmatrixlee,

[/I]But it is hard for us to help, when we do not quite understand what you have done so far. Please tell if you have been trying to install or trying to run Ubuntu live! If you cannot tell the difference, let us know, and someone will explain.

---

### Post by 3rdalbum on 2012-01-23
Try a later version of Ubuntu, such as Ubuntu 11.10.

Ubuntu 10.04 is getting old now.

---

