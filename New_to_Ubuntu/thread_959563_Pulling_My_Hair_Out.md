---
title: "Pulling My Hair Out"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by brucey1st on 2008-10-26
Hi guys i'm hoping someone can help me here :confused:

First thing is i'm a total noob to linux, altho i have had pcs since windows 3.1

2ndly i absolutely love ubuntu OS, but i keep getting a blank screen after installing the Ati driver ..

I have googled this, and its a very common problem with ati, but can someone help me here please :)

Ive been trying to work this out  for the last 3 dayz (on and off) so if someone can have mercy and put me outa my misery :lolflag:

Any Replies Would Be Much Appreciated

Cheers Brucey

---

### Post by DrMelon on 2008-10-26
Have you tried downloading and running EnvyNG? That program should help you get the right ATi drivers and configure them properly.:KS

---

### Post by brucey1st on 2008-10-26
> **DrMelon said:**
> Have you tried downloading and running EnvyNG? That program should help you get the right ATi drivers and configure them properly.:KS

Yep tried that several times, still blank screen after restart


Brucey

---

### Post by phidia on 2008-10-26
Which ati model are you trying to enable?
That's important because some models are supported better than others.

You could try and install the driver from the ati site, but before you attempt that take a look at the guide [here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") particularly the section titled > Install from Ubuntu repositories (easier)
Hope that helps.

---

### Post by brucey1st on 2008-10-26
> **phidia said:**
> Which ati model are you trying to enable?
That's important because some models are supported better than others.

You could try and install the driver from the ati site, but before you attempt that take a look at the guide [here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") particularly the section titled 
Hope that helps.

Hi, Its an Ati Radeon 9800 All in wonder SE

Brucey

---

### Post by brucey1st on 2008-10-26
> **phidia said:**
> Which ati model are you trying to enable?
That's important because some models are supported better than others.

You could try and install the driver from the ati site, but before you attempt that take a look at the guide [here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") particularly the section titled 
Hope that helps.

Tried this in the terminal

> brucey@brucey-desktop:~$ sudo dpkg-reconfigure -phigh linux-restricted-modules-`uname -r`
update-initramfs: Generating /boot/initrd.img-2.6.27-7-generic
brucey@brucey-desktop:~$ sudo insmod /lib/modules/`uname -r`/volatile/fglrx.ko


No idea what it means lol

Brucey

---

### Post by brucey1st on 2008-10-26
> You could try and install the driver from the ati site

Hi ive downloaded the ati gfx driver from the site, can anyone give me some info in how to install it?

Cheers Brucey

---

### Post by brucey1st on 2008-10-26
> **brucey1st said:**
> Hi ive downloaded the ati gfx driver from the site, can anyone give me some info in how to install it?

Cheers Brucey

Anyone?

---

### Post by phidia on 2008-10-26
Make sure you are in the directory that contains the downloaded driver and enter "sudo sh <drivername>" you use can use the commandline completion feature-just enter a few letters of the driver name and press tab the CLI will fill in the rest.

---

