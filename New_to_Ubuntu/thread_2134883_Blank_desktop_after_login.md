---
title: "Blank desktop after login"
date: 2013-04-12
forum: New to Ubuntu
---

### Post by bluebaron123 on 2013-04-12
Hello guys,i thought i could give Ubuntu a try,so i got the latest Wubi installer. I installed Ubuntu 12.10 32bit... Everything went smooth,i rebooted my PC,i tried logging in,but nothing would show on the desktop. I just get a wallpaper,no bars or anything,why? Can you guys help me?

PS: Is it because of Ubuntu? Should i uninstall Ubuntu,and install Lubuntu via wubi instead?

---

### Post by ShermW0829 on 2013-04-12
bluebaron. I had the same problem until I installed lubuntu. My host is an Intel pentium 4 1.70GHz 1700MHz. 

Sherman

---

### Post by bluebaron123 on 2013-04-12
If i install Ubuntu from a DVD , wil it fix this problem? Like launch unity in 2d,then install some graphic drivers for my ATI card?

---

### Post by BobosAbelMihai on 2013-04-12
You can't do nothing on the desktop after logging in? I mean i had the same problem after installing a wrong video driver one time, and another time after i made an update for kernel. Can you enter terminal? Ctrl+Alt+T.

---

### Post by Frogs Hair on 2013-04-12
12.10 has no 2D option it boots 3D from the open source driver with capible graphics.  Try to open the terminal as stated above. Ctrl+Alt+T . If the terminal opens. 

Unity Support Test:  ```
 /usr/lib/nux/unity_support_test -p
``` Unity Reset:```
setsid unity
```

---

### Post by bcbc on 2013-04-12
> **bluebaron123 said:**
> If i install Ubuntu from a DVD , wil it fix this problem? Like launch unity in 2d,then install some graphic drivers for my ATI card?
Boot with nomodeset: hold down Shift after selecting Ubuntu, when the Grub menu appears select Advanced options, Recovery mode. Then select Resume normal boot from the recovery menu.

Then look for a video card driver: [http://askubuntu.com/a/201524/14916](http://askubuntu.com/a/201524/14916)

---

### Post by Feathers McGraw on 2013-04-12
Had the same problem when I changed the driver for my ATI Mobility Radeon HD 5470 Graphics card in Ubuntu.

I think some graphics drivers are incompatible with certain desktop environments. For me, I couldn't get standard Ubuntu to work with the proprietary driver.

When I tried [Kubuntu]("http://www.kubuntu.org/getkubuntu") (ubuntu with KDE desktop environment), and enabled the proprietary driver, I had no problems.

If you have any DVDs or a USB stick, it's worth a go!

Please ask if you'd like additional help with this :)

Feathers

---

### Post by Feathers McGraw on 2013-04-12
Also, which graphics card are you using?

Feathers

---

### Post by bluebaron123 on 2013-04-13
Alright,i tried the Unity test,seems like my graphics card can't support 3D... Which is absolutely strange,because i ran Ubuntu 11.04 on my Virtualbox before,same computer specs. It worked like a charm... I still think its because i need to somehow update my drivers,so unity can work... I'm using ATI Radeon 9250.

I removed Ubuntu,and installed Lubuntu (I wanted to try Xubuntu,but i couldn't via wubi). Yeah Lubuntu works.

But i want to know, if i install Ubuntu from a DVD,would it work? The DVD is a RW,so if i can't get it to work,i can try Xubuntu or Kubuntu.

---

### Post by bcbc on 2013-04-13
There is no difference between Wubi and normal as far as the graphics. But a normal dual boot is better for other reasons (reliability, long term stability etc.) But did you try installing the graphics drivers after booting with nomodeset?

---

