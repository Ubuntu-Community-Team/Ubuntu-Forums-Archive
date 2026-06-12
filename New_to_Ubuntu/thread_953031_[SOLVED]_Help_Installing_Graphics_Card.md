---
title: "[SOLVED] Help Installing Graphics Card"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by suomalainen on 2008-10-19
Hello Ubunteros!

I recently purchased a VisionTek X1050 x16 PCI Express Graphics Card. ATI Radeon. I'm running Ubuntu 7.10.

I'm following the install instructions found at:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

But am having problems.

Firstly, if I install the card I'm unable to boot up Ubuntu. The system just hangs. This means that I have to power down my system, remove the card and use the VGA connection built onto the Motherboad to be able to boot into Ubuntu.

When I follow these steps. I.E.:

Instructions for Ubuntu 7.04 (Feisty) and Ubuntu 7.10 (Gutsy)

    * Install linux-restricted-modules and restricted-manager provided in the restricted repositories: 

sudo apt-get update
sudo apt-get install linux-restricted-modules-generic restricted-manager

Open the restricted drivers manager in "System -> Administration -> Restricted Drivers Manager" and select "ATI accelerated graphics driver". This will hopefully enable fglrx in a painless way. If not, follow the instructions for Edgy.

AFTER THIS part of the exercise I can't see the restricted driver because it isn't installed. If it was then I couldn't boot up my PC...

I'm at a loss as to what to do next or how to proceed. WOuld anyone happen to have any ideas?

Thanks!

---

### Post by Ryadt on 2008-10-19
When booting, try to boot in the recovery mode. Then type```
startx
```
Restricted Drivers is known as Hardware Drivers in Hardy.;)

---

### Post by suomalainen on 2008-10-19
Ryadt,

Thanks for the reply. First off I think 7.10 is Gutsy?

Secondly what does "startx" mean and do? And exactly when and where is this command entered. Sorry for the step by step question but I'm lost.

Thanks.

P.S. is it possible for the graphics card to be recognised by Ubuntu while in safemode?

---

### Post by Ryadt on 2008-10-19
Oops... sorry I didn't see the 7.10.
startx will start the x server. When you boot into the recovery mode, after entering your username and password then do the command.

---

### Post by suomalainen on 2008-10-19
Ryadt,

When I go into recovery mode I get line:

root@joe-desktop:~# 

When I enter startx here nothing happens is this the right command for gutsy?

---

### Post by Ryadt on 2008-10-19
Can you see the restricted drivers when you boot are able to get into ubuntu? And have you just installed Gutsy?

---

### Post by suomalainen on 2008-10-19
Ryadt,

I've used Gutsy for almost a yeAR NOW.

I cannot boot up in recovery mode when the graphics card is installed. When it is removed I can only then boot in recovery mode. I just discovered this 2 minutes ago.

Anyway, if the card isn't installed it won't be recognized. Any suggestions?

---

