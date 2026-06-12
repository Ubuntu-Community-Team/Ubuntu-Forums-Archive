---
title: "Laptop get very Hot"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by Troca on 2008-05-23
hi i have a compay Presario F500 that gets very hot when iam running linux well atleast latley didnt use to have this problem be4 untill i did a update and yestorday i desided to do a clean installation of ubuntu 8.04 to get my broadcom wireless to work (witch it did due to a post on the forum that i followd) but still my Laptop gets very very hot. when iam in windows my fan is hardly working and the laptop is cool when i start ubuntu the fan speed goes up to max (ithink) i can hear it very loud and clear and the laptop gets very hot aswell (sometimes it auto shutsdown) 

Any help would be gr8

System

Ubuntu 8.04 (hardy)
Kernel Linux 2.6.24-16-generic
Gnome 2.22.1

Hardware 
Memory 940.9 mib
Processors 0: AMD athlon(tm) 64 x2 Dual-core processor TK-53
Processors 1: AMD athlon(tm) 64 x2 Dual-core processor TK-53

---

### Post by marufaberlin on 2008-05-23
[http://ubuntuforums.org/showthread.php?t=230556](http://ubuntuforums.org/showthread.php?t=230556)

---

### Post by Troca on 2008-05-23
well i get a 
/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

when trying to run it after isntall. Anyway i dont want my fan to be less noisy well i do but i dont want the laptop to get so hot in the first place if i would lower the fan speed the laptop would prob crash all the time.

---

### Post by marufaberlin on 2008-05-23
k, what does *top* give you?

---

### Post by sayakb on 2008-05-23
I don't know if this is relevant or not. I had the same problem with a nx6320. I found out that if I use it in an air-conditioned room having a temp below 22-24, it works fine. But it becomes unbearably hot (my temperature screenlet reports it to be around 100C). So I opened up power-management properties and set my processor policy to "Maximum power saving". The change in speed is negligible, but the temp doesn't go above 60C. If you do not have the processor power control, download a package called ubuntu tweak from getdeb.net and enable the power-management processor control option from the software.

---

### Post by billgoldberg on 2008-05-23
Laptops get hot, that's what they do.

:p

Mine got so hot that it would shut down by itself.

Thinking about it, it's still in the shop, might want to go and get it:p

---

### Post by Austin_KW on 2008-05-23
This is usually due to dust.

Laptops need to be cleaned regularly. Force air through the reverse airflow path; Blow in the air outtakes or vacuum at the air intakes.

If you blow air through the laptop you should see a cloud of dust and you will notice your laptop immediately run cooler.

---

### Post by Troca on 2008-05-23
so i windows its less dusty ? 

like i said my fan hardly works at all in windows and in ubuntu its working super hard and still the comp gets hot eaven tho iam just surfing the web

---

### Post by marufaberlin on 2008-05-23
so it's software based. can you post results of:

```

ps -aux

```

---

