---
title: "[SOLVED] I need Help with my ubuntu installtion"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by sadaruwan12 on 2008-09-23
I've tried to install ubuntu on a laptop that has this configuration

[LIST]
[*]Core 2 Duo T5800 2.0Ghz
[*]2Gb RAm
[*]160Gb HDD
[*]DVD-RW
[*]W/Lan
[/LIST]

The thing is I got the system installed after very painful hours but alas the system doesn't boot in to the GUI it hangs at the progress bar. So I went into recovery mode on the kernel from the GRUB menu and saw that when the system is booting it's not detecting the secondary CPU core. It says the CPU is not detected and the boot up process hangs there. I don't know why is there any thing I could do any thing to work around this 'coz I cant get to the GUI.

Thanks
Sadaruwan:confused:

---

### Post by roger_1960 on 2008-09-23
Hi

Are you using a 64 bit .iso to install from?  If not, that could be the problem.

---

### Post by Idefix82 on 2008-09-23
It really shouldn't be a problem. The 32 bit version should work just fine under 64 bit CPU architecture. In fact, with 2 gig RAM the 64 bit version might even be slower than the 32 bit one.

---

### Post by luckydeveloper on 2008-09-23
hey try asking this in Installation & upgrades froum in ubuntu forums. they might have a good answer for you

---

### Post by az on 2008-09-23
I would start by booting the live cd and seeing if this works fine. 

It sounds like you may have a bad cd.

---

### Post by Sef on 2008-09-23
> hey try asking this in Installation & upgrades froum in ubuntu forums. they might have a good answer for you


This forum is just fine for that question.

---

### Post by uberdonkey5 on 2008-09-23
> **az said:**
> I would start by booting the live cd and seeing if this works fine. 

It sounds like you may have a bad cd.

I agree. I have same specifications to yours (is it a Dell?) but bigger HD and it was fine. However on a reinstall using a different disk (downloaded from the internet) I had the same problem. If you can, download the CD with a good connection and try it as a live CD, or alternatively (and easier) borrow a CD off a friend whom you know installed ubuntu with the CD. Bad CDs has caused many problems for me with ubuntu.

---

### Post by sadaruwan12 on 2008-09-24
> I have same specifications to yours (is it a Dell?) but bigger HD and it was fine. However on a reinstall using a different disk (downloaded from the internet) I had the same problem. If you can, download the CD with a good connection and try it as a live CD, or alternatively (and easier) borrow a CD off a friend whom you know installed ubuntu with the CD. Bad CDs has caused many problems for me with ubuntu.
I tried the same CD on a toshiba Satellite lap it worked nicely and I used the same CD on several desktops and they also worked with out any trouble. So I thought the same thing just like you the CD might be giving problems. I tried a different distro called openGEU that also was based on ubuntu but it was same as ubuntu same problem but I got it to install by giving these command with live CD boot up options "ACPI=off" , "nopic" , "nolapic". after getting the installtion done when tried to boot from the HDD the OS hangs on the progress bar then I went to trouble shoot mode and went through the boot up process the same thing was happening only one of the two CPU's getting detected the other one is not getting detected.

This is my complete problem I don't know what to do.

---

### Post by Korijn on 2008-09-24
Run a CD Check and a Memory Check in the boot menu of the Live CD. See if that gets you anywhere.

---

### Post by Paqman on 2008-09-24
> **sadaruwan12 said:**
> I got it to install by giving these command with live CD boot up options "ACPI=off" , "nopic" , "nolapic". 

Then you'll need to boot it with those options every time. Boot into the recovery console and open the Grub menu for editting with:
```

nano /boot/grub/menu.lst

```

Scroll down to the bottom and you'll see your Grub menu options. You can add the above options to the boot line and you should be able to boot into a working desktop (although some advanced power management features won't work)

---

### Post by sadaruwan12 on 2008-12-29
I got this solved I'd to recompail the Ubuntu distro to mach the Laptops hard ware

THX to every one who helped

---

