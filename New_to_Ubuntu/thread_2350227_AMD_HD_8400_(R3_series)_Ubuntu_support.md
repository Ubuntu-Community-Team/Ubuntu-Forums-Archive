---
title: "AMD HD 8400 (R3 series) Ubuntu support"
date: 2017-01-22
forum: New to Ubuntu
---

### Post by torrero007 on 2017-01-22
Hi, I recently purchase an pc and I want to install Ubuntu

[FONT=verdana]Mobo:      ASROCK AM1B-ITX RETAIL
[/FONT]
[FONT=verdana]CPU: AMD Athlon 5350 AM1/2.05 GHz/2 MB
[/FONT]
GPU: AMD R3 Series (integrated) - HD 8400 (integrated)

I read that there is no support for AMD HD 8400 GPU on Ubuntu 16.04. Should I install Ubuntu 15.04?

---

### Post by DuckHook on 2017-01-22
Welcome to the forums, torrero007

> **torrero007 said:**
> I read that there is no support for AMD HD 8400 GPU on Ubuntu 16.04.This is news to me. Your GPU should easily be supported with the default open source *radeon* driver. If you mean that you can't install the old *fglrx* proprietary driver, then you are correct. However, the *radeon* driver is now established and quite stable. I have no problem running everything I need with it, although if you are a gamer or a 3D modeller, it may not run things as well as the old proprietary driver.

---

### Post by wildmanne39 on 2017-01-22
My new laptop with AMD 8700 works with the driver but it has a bug and my screen goes blank every few minutes and I have to do a hard reboot so I am running Ubuntu in virtualbox until 17.04 comes out.

14.04.1 is the version of Ubuntu you need to use until this issue is fixed if you are experiencing any issues and you have tried everything possible to fix it.

---

### Post by torrero007 on 2017-01-23
Well, I did try to install Lubuntu 16.10 and selected the option "Install 3rd party software" and I had a crash every time. So I installed it without the 3rd party software, it was properly installed but I have no AMD Catalyst or HD audio on the output. Doing a little search, there were no drivers for HD8400 and Ubuntu 16.4 or newer. Only 15.04 and 14.04. 

I will try with 14.04 and see.

---

### Post by mastablasta on 2017-01-23
correct is no proprietary drivers. 

there are still opensource ones. they get improvements but maybe are not there yet in your case. their support really depends on the chip. older chips Will have descent support, newer maybe not so good. ther eis no catalyst but that doens't mean you can't control the card with various parameters.

14.04.1 is supported until 2019. if you use 14.04.2 thru 14.04.5 you will get same issue as on 16.04, because they use a later kernel (core) of the OS (where all drivers are at) and xserver components.
[SIZE=2]http://old-releases.ubuntu.com/releases/14.04.0/

[I]edit: scroll down the linked page to select the correct image...
[/I]
just update it after install and you should have latest security patches and some apps updated. for other's there are PPA if needed. let us know if you need help with those in a spearate thread.

[/SIZE]

---

### Post by torrero007 on 2017-01-23
On AMD website, the drivers support up to 14.04.02 for HD8400 ([http://support.amd.com/en-us/download/linux](http://support.amd.com/en-us/download/linux))
I will go for that one first and if I have the same problems I will go for 14.04.01

Thank  you very much for the help

---

### Post by mastablasta on 2017-01-24
probably true, but when you do system updates the 14.04.2 will become 14.04.3 (as kernel and X get updated) at which point you will be back where you started.

with 14.04 and 14.04.1 kernel (and X stuff) will stay the same. i have (i think) radeon hd 6350 at home and am staying on 14.04.1 with closed source AMD drivers. i tried the new opensoruce and while drivers work just fine the issue is their power management. baterry lasts a lot longer using the closed source drivers. so like you i am wating for new LTS and hopefully better support (though i doubt there will be).

---

### Post by torrero007 on 2017-01-24
You are right, I didn't think that. 

I downloaded 14.04.01 and loaded in a USB stick using Universal-USB-Installer, but it doen'tboot in my pc and it gives me a screen with
 grub>
 waiting for command. 

Am I doing something wrong?

---

### Post by mastablasta on 2017-01-25
> **torrero007 said:**
> 
I downloaded 14.04.01 and loaded in a USB stick using Universal-USB-Installer, but it doen'tboot in my pc and it gives me a screen with
 grub>
 waiting for command. 

Am I doing something wrong?

either the downloaded image is bad or the burned image is bad (you can try unetbootin or startup disk creator or YUMI instead of universal USB installer)

the downloaded image is verified by checking the md5sum (already done for you if you use torrent): [SIZE=2]https://help.ubuntu.com/community/HowToMD5SUM
[/SIZE]

---

### Post by torrero007 on 2017-01-25
Thank you mastablasta, I will try downloading with torrent then. In the meantime, I installed 14.04.01-i386 and I have problem with the HD audio ([https://ubuntuforums.org/showthread.php?t=2350459](https://ubuntuforums.org/showthread.php?t=2350459)). Have you got any idea?

---

