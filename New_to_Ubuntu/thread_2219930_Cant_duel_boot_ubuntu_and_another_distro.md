---
title: "Cant duel boot ubuntu and another distro"
date: 2014-04-26
forum: New to Ubuntu
---

### Post by czmacbudder on 2014-04-26
So I want to duel boot ubuntu 14.04 and another distro but my BIOS does no see it can you anyone help m?

---

### Post by monkeybrain20122 on 2014-04-26
What do you mean by the bios cannot see it? Do you mean it doesn't boot from the cd/usb or what?

---

### Post by suprleg on 2014-04-26
Do you need to change the boot order in the bios?

---

### Post by czmacbudder on 2014-04-26
> **czmacbudder said:**
> So I want to duel boot ubuntu 14.04 and another distro but my BIOS does no see it can you anyone help m?

I mean it isn't a option to boot from

---

### Post by monkeybrain20122 on 2014-04-26
Yes you do need to configure to boot from usb (usually it will boot from cd by default). How did you install Ubuntu?

---

### Post by czmacbudder on 2014-04-26
> **monkeybrain20122 said:**
> Yes you do need to configure to boot from usb (usually it will boot from cd by default). How did you install Ubuntu?

from a usb not the one I am using now but how do I switch to usb? instead of a dvd?

---

### Post by monkeybrain20122 on 2014-04-26
You should be able to get into bios settings by pressing fn key like f11 or something when boot, exactly whick key would depend on your computer. Usually they will tell you  during the first few seconds when you boot but it will flash by very quickly so pay attention at the screen when you boot. Once you get into the bios look for boot order. Instructions differ depending on hardware but you should be able to figure it out.

---

### Post by czmacbudder on 2014-04-26
> **monkeybrain20122 said:**
> You should be able to get into bios settings by pressing fn key like f11 or something when boot, exactly whick key would depend on your computer. Usually they will tell you  during the first few seconds when you boot but it will flash by very quickly so pay attention at the screen when you boot. Once you get into the bios look for boot order. Instructions differ depending on hardware but you should be able to figure it out.

Anyway I could install it from a cd?

---

### Post by QIII on 2014-04-26
Only the alternate .iso image will fit on a CD.  The others require a DVD because of their size.

---

### Post by monkeybrain20122 on 2014-04-26
Depending on the distro you want to dual boot with, some may fit into a cd, but I suspect you will need a dvd for the 'user friendly' ones.

---

### Post by suprleg on 2014-04-26
I'm sure there are various ubuntu variants that fit on a CD, however 14.04 LTS, the current release, requires a DVD. So once you change the boot order to boot from CD/DVD first rather than the HDD you should be able to begin an install. Hope that helps?

---

### Post by suprleg on 2014-04-26
> **monkeybrain20122 said:**
> Depending on the distro you want to dual boot with, some may fit into a cd, but I suspect you will need a dvd for the 'user friendly' ones.

Appears we're thinking along the same lines.

---

### Post by czmacbudder on 2014-04-26
> **monkeybrain20122 said:**
> Depending on the distro you want to dual boot with, some may fit into a cd, but I suspect you will need a dvd for the 'user friendly' ones.

So that means i'm suck in ubuntu and no duel booting? :(

---

### Post by monkeybrain20122 on 2014-04-26
> **czmacbudder said:**
> So that means i'm suck in ubuntu and no duel booting? :(

If your machine is not too old (~10 years) it should support booting from usb, it is not that difficult to change the BIOS's boot order.

---

### Post by czmacbudder on 2014-04-26
> **monkeybrain20122 said:**
> Depending on the distro you want to dual boot with, some may fit into a cd, but I suspect you will need a dvd for the 'user friendly' ones.

Well I want to use robolinux

---

### Post by LastDino on 2014-04-26
Let me see if I understood you correctly. 

>You've checked your BIOS boot sequence option and there is no option for USB booting?
>You want to dual boot with other Linux version?

You can still get latest Ubuntu if you've some time though, Just install latest Lubuntu first (Which is less that 700MB) and then update it to whichever version you want. But if your PC really is old enough to not have USB boot then I suspect you should be better of sticking with Lubuntu or at little stretch Xubuntu.


Since that's out of the way, next thing to check if your existing Linux supports dual booting or not, 99% it does. Just make sure original OS has Grub. 
Better option:  Just post asking ''how to'' on some forum with *that Linux distro* instead of here. They can help you more precisely.

---

### Post by stalkingwolf on 2014-04-26
you should be able to get a boot option menu on start up.  There is no "standard keystroke" for this each manufacturer uses a different key.  Could be esc , f8 f9 f10 f11 f12
ive seen all of those.

Usually it will say on the bottom of the initial splash screen that shows the manufacturers logo.

---

