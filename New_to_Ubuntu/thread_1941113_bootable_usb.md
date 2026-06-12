---
title: "bootable usb"
date: 2012-03-15
forum: New to Ubuntu
---

### Post by vagelism on 2012-03-15
Hello to all.
I use multisystem script to make a usb multiboot with various systems. So it works great with more of the small distributions like glonzilla or freeNas etc, but when it comes to Ubuntu I got the error of the screen. Even if I tried to make it work only with one OS , Ubuntu doesnt boot and comes with the error of the screen. 
Any possible solution?
Thank you!

---

### Post by LaptopLInux2 on 2012-03-15
What you do is to put the USB in (8GB or larger) and let the installation to do it for you,

---

### Post by vagelism on 2012-03-15
Thank you. So If I understood correct I have to plug the usb and then to select from Ubuntu OS that I run to make a valid usb bootable version of it?
Can you please tell me the steps. Now I use a 4gb USB drive so maybe is this the problem as you mentioned.

---

### Post by ixtok on 2012-03-15
I would use an 8GB stick. I would run the Ubuntu live CD and choose to install to that usb device. Make sure it installs grub to the usb also and not to your hard drive.

---

### Post by vagelism on 2012-03-15
> **ixtok said:**
> I would use an 8GB stick. I would run the Ubuntu live CD and choose to install to that usb device. Make sure it installs grub to the usb also and not to your hard drive.

Will I be able to make an installation after that from the USB to an other system?

---

### Post by Ghost_Mazal on 2012-03-15
> **vagelism said:**
> Will I be able to make an installation after that from the USB to an other system?

Only if you clone it. You will not have the "install Ubuntu" option as it will already be installed onto the usb.

---

### Post by C.S.Cameron on 2012-03-15
I have seen that error due to a bad iso download.
Check your iso's MD5SUM.

---

### Post by bodhi.zazen on 2012-03-15
> **C.S.Cameron said:**
> I have seen that error due to a bad iso download.
Check your iso's MD5SUM.

+1 

[https://help.ubuntu.com/community/VerifyIsoHowto](https://help.ubuntu.com/community/VerifyIsoHowto)

---

### Post by vagelism on 2012-03-15
> **bodhi.zazen said:**
> +1 

[https://help.ubuntu.com/community/VerifyIsoHowto](https://help.ubuntu.com/community/VerifyIsoHowto)

From this ISO I installed the Ubuntu in my pc!
You thing is possible?

---

### Post by sudodus on 2012-03-15
So you know the iso file is good. Then try another tool to make your USB boot drive. I have good experience of ***Unetbootin***. (But I have had good luck with Multisystem too on many computers).

It might be a good idea to have more than one USB stick for booting/installing, because the sticks are different, and the systems are installed in slightly different ways by different tools, and USB booting is not as standardized as CD booting.

---

### Post by vagelism on 2012-03-15
Unetbootin never worked fine for me! Instead Multisystem works pretty good!
I just confirmed the md5. Is correct:c396dd0f97bd122691bdb92d7e68fde5
I will try the classic step by step way that ubuntu forum give for fresh install from a usb drive.

---

