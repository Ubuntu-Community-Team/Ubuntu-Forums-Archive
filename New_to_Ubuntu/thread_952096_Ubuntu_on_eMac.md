---
title: "Ubuntu on eMac"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by ant2ne on 2008-10-18
I got this installed, but just as GDM is starting, the screen goes black. I assume this is an X problem.  I would like to edit the xorg.conf, but I don't want to do it from the recovery CD. How can I tell the computer to not boot directly to GDM, instead boot to a CLI?

---

### Post by phidia on 2008-10-18
Choose the recovery mode from the boot menu.

But actually you can just let it boot even if it fails you can get to a command line by pressing Alt+Ctrl+F1

---

### Post by SunnyRabbiera on 2008-10-18
Those were Power PC based macs, unfortunately Ubuntu no longer supports PPC actively anymore.
The best thing for you might be debian, debian works similar to Ubuntu.
its a bit rough to install and get multimedia working in it but it will work.

---

### Post by phidia on 2008-10-18
That doesn't make any sense a PPC processor wouldn't even begin to install x86 Ubuntu.

---

### Post by ant2ne on 2008-10-19
Yes it is PPC  

[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

Once it tries to load GDM, it locks up. Cntl+Alt+F1 does nothing. recover mode on the boot CD does not have nano. It has vi, and I hate vi. I would like to mod a conf or something to prevent GDM from loading by default. If it will get me to a CLI, then I can use NANO and I can install Samba and mount my shares, I can get this xorg.conf thing strait.

---

### Post by Dark006 on 2008-10-19
Not sure if you tried anything like this, or this will even help with your problem, but if your able to get to a CLI try ```
sudo dexconf
```
to reset your xorg.conf.

---

### Post by ant2ne on 2008-10-19
That is what I'm trying to do, get to CLI. Forget the Mac stuff, forget the xorg.conf stuff. Just tell me how I get it to boot without even trying to load X & GDM.

---

### Post by phidia on 2008-10-19
> **ant2ne said:**
> That is what I'm trying to do, get to CLI. Forget the Mac stuff, forget the xorg.conf stuff. Just tell me how I get it to boot without even trying to load X & GDM.

Can you select recovery mode from the boot menu?
If that isn't an option you can always press Alt+Ctrl+F1 (F2-F7 open ttys too) to get to CLI.

BTW what version of Ubuntu did you install?

---

### Post by ant2ne on 2008-10-19
Omg > **ant2ne said:**
> yes it is ppc  

[https://wiki.ubuntu.com/powerpcfaq](https://wiki.ubuntu.com/powerpcfaq)

[https://wiki.ubuntu.com/powerpcdownloads](https://wiki.ubuntu.com/powerpcdownloads)

once it tries to load gdm, it locks up. Cntl+alt+f1 does nothing. Recover mode on the boot cd does not have nano. It has vi, and i hate vi. I would like to mod a conf or something to prevent gdm from loading by default. If it will get me to a cli, then i can use nano and i can install samba and mount my shares, i can get this xorg.conf thing strait.

---

