---
title: "ubuntu 12.10 install problems"
date: 2013-04-08
forum: New to Ubuntu
---

### Post by jetint8ke on 2013-04-08
hello ,i tried to install unbuntu version12.10 desktp -i138 32 bit ,my screen turn off and on every 12 seconds during installation,it goes through the installation say it can't find the grub-install/dev/sda file ,i'm diong the install from an USB drive ,i used peguin to make the USB bootable at start up .i have an aleinware amd 64 bit proccessor an nvidia gforce 7600gs 512mb video card ,i have tried the amd 64 bit and the lt version as well and all do the same thing ,can anyone help ,maybe i'm doing some wrong ,if so, can anyone point me in the right direction ,i really like the look of ubuntu os .

---

### Post by Bucky Ball on 2013-04-08
Welcome to the forums. Try installing the 64bit Ubuntu and see if that helps. Not sure why you are going for the 32bit. ;)

---

### Post by jetint8ke on 2013-04-08
thank you for the welcome ,according to the spec it says it's an i386 architecture,( hope i spelled that word right),and it's considered to be a 32 bit

---

### Post by Bucky Ball on 2013-04-08
> **jetint8ke said:**
> i have an aleinware amd 64 bit proccessor ...

... then it's a 64bit machine. Sorry, didn't notice you'd already tried it anyway.

Does it run okay when you try Ubuntu from the USB stick? Sounds like perhaps it is installing grub somewhere other than sda drive. You might try boot repair:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You can install and run it while booted from the USB (but need to be online to do so).

---

### Post by jetint8ke on 2013-04-08
that's another problem it can't find my wireless connection either ,it does boot up from the USB and goes through the prcess of installing until it hits "can't find grub-install/dev/sda

---

### Post by ppjdee on 2013-04-09
You could try burning the .iso to a dvd. Simple and always worked for me.
I'm curious as how to do the USB method, I never tried it before...

---

### Post by mörgæs on 2013-04-09
Have you tried the alternate installer? A good almost-magic solution when something unexplained is going on...
[https://help.ubuntu.com/community/Lubuntu/Alternate_ISO](https://help.ubuntu.com/community/Lubuntu/Alternate_ISO)

Unfortunately Ubuntu dropped the alternate, but Lubuntu still has it.

Installing from USB is safer than CD/DVD.

Always remember to have wired internet access while installing.

---

### Post by ppjdee on 2013-04-09
> **mörgæs said:**
> Have you tried the alternate installer? A good almost-magic solution when something unexplained is going on...
[https://help.ubuntu.com/community/Lubuntu/Alternate_ISO](https://help.ubuntu.com/community/Lubuntu/Alternate_ISO)

Unfortunately Ubuntu dropped the alternate, but Lubuntu still has it.

[COLOR=#ff8c00]Installing from USB is safer than CD/DVD.[/COLOR]

Always remember to have wired internet access while installing.

Ah, I'm curious as to why that is.

---

### Post by jetint8ke on 2013-04-09
i'm such a blooming MORON ,i was tring to install  from the USB ,when  i decided to use the wubi.exe ,and the installation went through like a fart in a high wind ,and and ,i have nooooooo issues what so ever ,ubuntu is purring and running cherry ,i am loving this OS ,it's better than windows ,i've been with windows since dos ,but now 
i'm giong with linux ,awesome OS!!!!!!

---

### Post by mörgæs on 2013-04-09
Welcome to the free world!

---

