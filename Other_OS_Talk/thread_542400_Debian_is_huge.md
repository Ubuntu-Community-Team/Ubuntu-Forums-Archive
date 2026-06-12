---
title: "Debian is huge"
date: 2007-09-03
forum: Other OS Talk
---

### Post by init1 on 2007-09-03
I installed Debian today from the the BBC ISO. The only packages I installed beyond the minimal were the "Laptop" and "Standard" ones. And it takes up > 600MB! Why? It doesn't even have X.

---

### Post by kerry_s on 2007-09-03
lol, you don't need laptop or standard either. my whole debian install is only 706mb, i'm using xfce4, iceweasel, pidgin, etc...

my starting line was>
apt-get install xserver-xorg-video-nv xorg synaptic xfce4

no gdm, i have autologin setup with rungetty and .bash_profile.

---

### Post by init1 on 2007-09-04
> **kerry_s said:**
> lol, you don't need laptop or standard either. my whole debian install is only 706mb, i'm using xfce4, iceweasel, pidgin, etc...

my starting line was>
apt-get install xserver-xorg-video-nv xorg synaptic xfce4

no gdm, i have autologin setup with rungetty and .bash_profile.
I removed standard, and that gave me a few hundred MB back, but whats in "laptop"? Does the base install have ACPI?

---

### Post by kerry_s on 2007-09-04
> **init1 said:**
> I removed standard, and that gave me a few hundred MB back, but whats in "laptop"? Does the base install have ACPI?

yes, the base install has acpi. it's much better to just grab the laptop stuff you need, instead of having it install all the laptop stuff no matter if it will works with yours or not. alot of stuff from the base install can be trimmed as well using aptitude or synaptic. i always trim further after i get my gui up. it's just like if you just install xorg, it will install all the video drivers, but if you select your video driver and then xorg it will only grab that driver and the rest of the stuff for X. the more you play with it, the better you'll get, i've had full working installs as small as 300mb, so it's just a matter of what you want in your system. you can even use the current install , compile smaller applications using check install, then just wipe and put a clean install with your built debs. just use the first couple of installs as a kinda learning thing try different things, get a feel.

---

### Post by init1 on 2007-09-04
Thanks, I wasn't aware that X was so easy to add. My system is fine now. Only 768MB. This configuration is disturbingly fast, compared to other distros.

---

### Post by kerry_s on 2007-09-04
> **init1 said:**
> Thanks, I wasn't aware that X was so easy to add. My system is fine now. Only 768MB. This configuration is disturbingly fast, compared to other distros.

hmm, a fluxbox fan huh. i'm running jwm on mine, i wanted something different this time around. mines at 614mb+ cache, total 381packages installed, pic->

---

### Post by init1 on 2007-09-05
I'm interested in fluxbox for the moment, but I might change later.

---

### Post by kerry_s on 2007-09-05
> **init1 said:**
> I'm interested in fluxbox for the moment, but I might change later.

master the fluxbox first, it's the best 1 out there. i've used fluxbox for a long time, i just like to see how other things are coming along from time to time, eventually i always go back to fluxbox. i just boned that install this mourning, so now i'm playing with xfce4 now.
trust me when you get use debian, you'll realize how easy it is. i keep important stuff on a external so i don't mind wiping and trying something different. :)

---

### Post by daveshields on 2007-09-05
I'm not sure what you mean by huge. 

A 250GB disk costs just over $50 these days. A dollar can buy you almost 5GB, so your "huge" 600MB of Debian is taking less than $0.25 worth of  disk space.

Unless you are working in  the embedded space, I wonder if this really matters.

---

### Post by init1 on 2007-09-06
> **daveshields said:**
> I'm not sure what you mean by huge. 

A 250GB disk costs just over $50 these days. A dollar can buy you almost 5GB, so your "huge" 600MB of Debian is taking less than $0.25 worth of  disk space.

Unless you are working in  the embedded space, I wonder if this really matters.
It wasn't the cost that I was concerned about, I just didn't know what was taking up the space. But I do now. Whatever was in those other packages, I don't seem to need them.

---

### Post by init1 on 2007-09-06
> **kerry_s said:**
> master the fluxbox first, it's the best 1 out there. i've used fluxbox for a long time, i just like to see how other things are coming along from time to time, eventually i always go back to fluxbox. i just boned that install this mourning, so now i'm playing with xfce4 now.
trust me when you get use debian, you'll realize how easy it is. i keep important stuff on a external so i don't mind wiping and trying something different. :)

I recently re-did my entire HD, so that I could have many distros on there at once. I am running out of room already. Debian is /dev/sda9.

---

### Post by mips on 2007-09-07
> **init1 said:**
> I recently re-did my entire HD, so that I could have many distros on there at once. I am running out of room already. Debian is /dev/sda9.


Why not just use VirtualBox ?

---

### Post by init1 on 2007-09-07
> **mips said:**
> Why not just use VirtualBox ?
I assume it's not as fast. Is it?

---

### Post by rsambuca on 2007-09-07
> **daveshields said:**
> I'm not sure what you mean by huge. 

A 250GB disk costs just over $50 these days. A dollar can buy you almost 5GB, so your "huge" 600MB of Debian is taking less than $0.25 worth of  disk space.

Unless you are working in  the embedded space, I wonder if this really matters.

You are obviously missing the point of the statement dave.  Simply buying new hardware for every problem is not a practical solution, nor possible for some people. I know you are a newegg fanboi, but please.

---

### Post by mips on 2007-09-08
> **init1 said:**
> I assume it's not as fast. Is it?

Probably not but it aint slow either. Hard to see the difference but I suppose there will be a performance knock. For me it beats the hell out of rebooting the whole time.

---

### Post by init1 on 2007-09-08
> **mips said:**
> Probably not but it aint slow either. Hard to see the difference but I suppose there will be a performance knock. For me it beats the hell out of rebooting the whole time.
Maybe I'll try it sometime, but for now I am content. It's not like reboot takes hours, only about 30 seconds.

---

