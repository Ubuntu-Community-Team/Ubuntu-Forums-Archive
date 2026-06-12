---
title: "&quot;grub rescue&quot; error after partition formatting"
date: 2012-05-02
forum: New to Ubuntu
---

### Post by Hairywings on 2012-05-02
I had problems booting Ubuntu 10.10 on my dual boot PC for a while and couldn't fix it, so I was using Win7. Next, I decided to reinstall Ubuntu, but it wouldn't recognize Ubuntu CD (I thought it was due to some system conflict). So I formatted a hard drive partition with Ubuntu system under Win7 and tried to reboot. It didn't boot neither with Win7 (it just doesn't give this option) from my hard drive, nor from Win live CD or Ubuntu CDs. It says "Unknown filesystem, Grub rescue". Would you, please, advise how do I manage this? Basically, I don' know how to access anything on my computer right now. Thank you in advance!!!

---

### Post by kc1di on 2012-05-02
give Boot Repair a try. 

you can find it here :

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

First you may want to fix your windows 7 boot loader by placing the windows 7 cd and booting form in the select fix MBR

then try to reinstall ubuntu again.

---

### Post by Hairywings on 2012-05-02
It doesn't want to boot from any live CD, including WinXP, Suse, U Debian and Maverick (that's what I've tried). I am currently making a boot repair disk. Thanks for the advise!

---

### Post by Hairywings on 2012-05-02
Boot repair worked out really well! **kc1di**, thank you for your help.

---

### Post by kc1di on 2012-05-02
> **Hairywings said:**
> Boot repair worked out really well! **kc1di**, thank you for your help.

Your Welcome , enjoy ;)

---

