---
title: "Running slow"
date: 2013-01-05
forum: New to Ubuntu
---

### Post by itlane on 2013-01-05
Hi All

Downloaded ubuntu this morning and love the look of it. However it is running painfully slowly. Running on old pc with xp still installed.  Also, can't connect to Wifi. 

Apologies if this question has appeared hundreds of times previously! 

Ian

---

### Post by Pjotr123 on 2013-01-05
Speed up your Ubuntu:
[https://sites.google.com/site/easylinuxtipsproject/speed](https://sites.google.com/site/easylinuxtipsproject/speed)

Wifi problem:
[https://sites.google.com/site/easylinuxtipsproject/internet](https://sites.google.com/site/easylinuxtipsproject/internet)

---

### Post by Bucky Ball on 2013-01-05
Welcome to the forums.

Have you actually installed Ubuntu to the hard drive or you are running from the CD? If the latter, that will account for both issues, probably. It will for the wifi as you can't install drivers to the LiveCD but will be able to when you install (is it showing there are drivers available?).

If the former and you have installed to the hard drive, maybe the specs are too slim to run the latest Ubuntu with the Unity desktop. There are other workarounds (that I know little about as I don't like Unity and use Xubuntu) but you could try installing a lighter flavour, say Xubuntu or Lubuntu, or just install their desktop environment. Look for xfce4 or lxde in Software Centre, install, logout, choose either from the 'Session' pop-up, log in. You can change back to Unity DE the same way.

---

### Post by itlane on 2013-01-05
> **Bucky Ball said:**
> Welcome to the forums.

Have you actually installed Ubuntu to the hard drive or you are running from the CD? If the latter, that will account for both issues, probably. It will for the wifi as you can't install drivers to the LiveCD but will be able to when you install (is it showing there are drivers available?).

If the former and you have installed to the hard drive, maybe the specs are too slim to run the latest Ubuntu with the Unity desktop. There are other workarounds (that I know little about as I don't like Unity and use Xubuntu) but you could try installing a lighter flavour, say Xubuntu or Lubuntu, or just install their desktop environment. Look for xfce4 or lxde in Software Centre, install, logout, choose either from the 'Session' pop-up, log in. You can change back to Unity DE the same way.
Many thanks - would wiping xp help re: the slow running issue?

---

### Post by 2F4U on 2013-01-05
Could you post your hardware specifications so that we have an impression whether this is the root of the problem? What version of Ubuntu are you currently looking at?

---

### Post by Impavidus on 2013-01-05
> **itlane said:**
> Many thanks - would wiping xp help re: the slow running issue?
No, the presence of xp doesn't have any influence on linux (except for messing with your clock and things like that. They might both want to switch it to dst in spring).

Could you tell which ubuntu version and flavour you're using? And you specs? CPU, RAM, graphics card.

---

### Post by itlane on 2013-01-06
Hi

I'm running Celeron More processor 1.4G, 480MB RAM and a VIA/S3G Unichrome products card. Trying with 12.10

Many thanks 

Ian

---

### Post by Bucky Ball on 2013-01-06
> **itlane said:**
> Hi

I'm running Celeron More processor 1.4G, 480MB RAM and a VIA/S3G Unichrome products card. Trying with 12.10

Many thanks 

Ian

Post a new thread with a descriptive title outlining your issue rather than hijacking this one. Unfair to those looking to be helped and those helping ... thanks.

---

### Post by Impavidus on 2013-01-06
480 MB RAM is not enough for the default Ubuntu. Xubuntu just works (I'm using 314MB right now), but not comfortably, Lubuntu is better. You will basically get the same system, but with a desktop environment that's less resource hungry and a lighter set of default applications. The look, however, will be completely different. There are other light versions, but as they're unofficial support for them will be more complicated.

---

### Post by Bucky Ball on 2013-01-06
> **Impavidus said:**
> 480 MB RAM is not enough for the default Ubuntu. Xubuntu just works (I'm using 314MB right now), but not comfortably, Lubuntu is better. You will basically get the same system, but with a desktop environment that's less resource hungry and a lighter set of default applications. The look, however, will be completely different. There are other light versions, but as they're unofficial support for them will be more complicated.

+1. Well said. The voice of experience.

---

### Post by itlane on 2013-01-06
Many thanks everyone. That has saved me time and hassle. Time to upgrade my hardware 


Ian

---

### Post by Calinou on 2013-01-06
> **itlane said:**
> Hi

I'm running Celeron More processor 1.4G, 480MB RAM and a VIA/S3G Unichrome products card. Trying with 12.10

Many thanks 

Ian

Buy new hardware, ???, PROFIT!

That is REALLY too old, even Lubuntu would be slow. Also, VIA graphics cards suck.

---

### Post by mysteriousdarren on 2013-01-07
This old box could be used for a server instead of going straight into the landfill. I've several old laptops running Ubuntu Server 12.04 that work great for what they are doing. I am not worried about electricity use(minimal) and have been working flawlessly for years. If one break, no worries.

---

### Post by Calinou on 2013-01-07
> **mysteriousdarren said:**
> This old box could be used for a server instead of going straight into the landfill. I've several old laptops running Ubuntu Server 12.04 that work great for what they are doing. I am not worried about electricity use(minimal) and have been working flawlessly for years. If one break, no worries.

Avoid running a 24/7 server. This will save money (electricity) and time. It's not like games are in a shortage of servers, same for file hosting or any other kind of stuff.

---

### Post by Bucky Ball on 2013-01-07
If you're going to run anything 24/7 get a decent, 85+ certified power supply. I would not leave a generic silver box PSU unattended for any length of time and your old computer probably depends on one of those. (Silver box = -70% efficiency, which means electricity is turned into heat rather than powering your machine, and unlikely has any safety switches.)

If it dies, it won't go alone. Get a good PSU with reliable safety switches if you go 24/7.

PS: The title of this thread is 'Running Slow' and that is the issue we are dealing with. Nothing to do with the pros and cons of running a server (but nice suggestion mysteriousdarren ;)). Let's stay on topic. ;)

---

