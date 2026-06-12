---
title: "[SOLVED] Hardy Heron won't wake from Hibernation"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by RayArdia on 2008-06-12
Generally very pleased with HH, but one problem noted is a failure to come back to life when I switch on after period of hibernation.

---

### Post by schallstrom on 2008-06-12
I have made the experience that Hibernation generally works very poor on Desktop computers. I never had a Desktop computer where it really worked without flaws. That is true for both Windows and several different Linux distributions I tried. So I'm tending to blame the manufacturers of BIOS's for Desktop mainboards and not the OS developers.

---

### Post by RayArdia on 2008-06-18
Thank you, I don't know whether the BIOS can have anything to do with this problem for Hibernate worked perfectly with Gutsy.

---

### Post by schallstrom on 2008-06-18
I'm not an expert on this. It's just my experience that I never had problems with suspend and hibernate on laptops be it Windows or Linux and that it never worked properly on Desktop computers for me be it Windows or Linux either. I once had a Desktop where Hibernation worked sometimes, but using it is pretty pointless when the computer wakes up properly from hibernation only in 50% of the cases.

---

### Post by Rui Pais on 2008-06-19
Hi all.
For me at Hardy the only kernel that suspend/hibernates it's 2.6.24-16.

Try to install it (or boot from it if it's still installed) and check if it works.

BTW, i have a nvidia card. Here the only way to make it awake correctly it's using proprietary drivers. Opensource driver always fail... 
Kind of ironic, isn't it?

---

### Post by schallstrom on 2008-06-26
> **Rui Pais said:**
>  have a nvidia card. Here the only way to make it awake correctly it's using proprietary drivers. Opensource driver always fail... 
Kind of ironic, isn't it?

Why would that be ironic? It's rather obvious that the quality of a driver made by people who have no access to the hardware specifications is seldom better than the quality of a driver made the hardware manufacturer who of course has access to all the hardware specs. So blame Nvidia and buy graphics boards from AMD/ATI next time. They released their hardware specs some months ago and actively support the development of open source drivers for their GPUs.

---

### Post by suicidejack on 2008-06-26
I have a Dell Latitude D820 laptop and I've got the same problem with hibernation.  I found though that suspend works fine so I've been using that instead.  Hibernation has always worked fine for me before for both Ubuntu and Kubuntu previous releases so I tend to think somewhere in the HH release that hibernation got screwed up.  I haven't looked into this problem a lot through from what I have seen on the web everyone is having the same problem with hibernation.  I'm sure though that it is just a matter of time until someone solves this problem!

---

### Post by Rui Pais on 2008-06-26
> **schallstrom said:**
> Why would that be ironic? It's rather obvious that the quality of a driver made by people who have no access to the hardware specifications is seldom better than the quality of a driver made the hardware manufacturer who of course has access to all the hardware specs. So blame Nvidia and buy graphics boards from AMD/ATI next time. They released their hardware specs some months ago and actively support the development of open source drivers for their GPUs.

Who is blaming?

(And what graphics card had to do with the fact that with one ubuntu kernel suspends work and another ubuntu kernel won't?)

---

### Post by schallstrom on 2008-06-26
> **Rui Pais said:**
> Who is blaming?

(And what graphics card had to do with the fact that with one ubuntu kernel suspends work and another ubuntu kernel won't?)

I am blaming Nvidia for not supporting the development of open source drivers for their products.

I was explicitly referring to your statement, that the proprietary drivers work and open source drivers don't and that you find it ironic. That's why I quoted only that part.

---

### Post by RayArdia on 2008-07-10
Thanks to all for their input. Whilst all that was going on - and after updating Hardy on two occasions - it now hibernates OK.

---

