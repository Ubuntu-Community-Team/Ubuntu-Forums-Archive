---
title: "[SOLVED] Kubuntu 8.10 wont boot?"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-10-12
Just installed the beta of kubuntu 8.10 on my pc but when I try to boot it up it will load the kubuntu splash screen with the logo and the loading bar but then it will try and start the gui with the little x in the middle of the screen then all I will get is a black screen with somthing like "checking battery charge    [Done]" and thats it although if i use the recovery boot option i will get to a text only login...

please help:(

---

### Post by aeiah on 2008-10-12
have you tried safe graphics mode?

what graphics card do you have in your laptop?

---

### Post by kamitsukai on 2008-10-12
Sorry it's a desktop pc with a built in Nvidia GF7050-M2 and how do try safe graphics mode? (is it a really obviouis boot option on grub? as if it is I've tried it lol)

---

### Post by kamitsukai on 2008-10-12
I think i might of found a bug report...[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/277452](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/277452)

and it appears the answer is to download the daily iso...but is there anyway to fix the problem from the install i already have? maybe download the driver from the command prompt?

---

### Post by aeiah on 2008-10-12
edit: nevermind, saw your update

---

### Post by SuperSonic4 on 2008-10-12
> **kamitsukai said:**
> I think i might of found a bug report...[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/277452](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/277452)

and it appears the answer is to download the daily iso...but is there anyway to fix the problem from the install i already have? maybe download the driver from the command prompt?

```
wget -c 'url'
```

This allows you to continue the installation if the internet dies

---

### Post by aeiah on 2008-10-12
if you find a driver or patch thats available you can download it via the commandline with wget, but after looking through that bug and the related one that's linked, it seems like the best thing to do would be to get the newest build, or perhaps even just install 8.04.

if you're a linux ninja you could try blacklisting the nv modules and editing your xorg.conf to point to vesa ones, or see if envy supports onboard nvidia drivers.

id just download the newest build or wait for 8.10 final

---

### Post by kamitsukai on 2008-10-12
Thanks for you help aeiah ill probably just download the newest build from cdimage.ubuntu.com...

---

