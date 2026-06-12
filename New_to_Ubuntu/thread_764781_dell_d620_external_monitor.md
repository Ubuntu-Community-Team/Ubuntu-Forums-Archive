---
title: "dell d620 external monitor"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by thomas.hoyland on 2008-04-24
Hi there,
havnt posted in a while, but im wondering if anyone is having problems using the external vga port on the dell d620 under 7.04 ubuntu?

i connect it to an external monitor and it outputs a signal, however the image is fuzzy and jittery with one side of the monitor appearing ok-ish but the other fizzing if you know what i mean?

ive got the intel mobile graphics controller 945gma with a laptop panel resolution of 1280/800 running using 915resolution

id like to get this working, as ive got a gorgeous monitor im not using as i should be, lol

any help is always appreciated.

regards,
tom

---

### Post by dokdoom on 2008-04-26
Although it's possible this problem is just with your dell, I can attest to the fact that intel hates having an external monitor. Using the intel or i810 drivers, I have never been able to have xinerama and rendering work. 

Also, when you first turn your computer on you have to make sure the other monitor isn't plugged in. That is only in my experience and may be different for you, but turning your machine on with the external monitor plugged in will ruin the resolution of your primary monitor. 

You may have the same problem I had, I installed 915resolution but turned out I never needed to. I hope this helped.

---

