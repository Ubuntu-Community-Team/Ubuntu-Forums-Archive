---
title: "Brightness of the screen"
date: 2013-08-22
forum: New to Ubuntu
---

### Post by KylePhys on 2013-08-22
I have dual boot on my laptop with windows and ubuntu. When I log in on windows and adjust the brightness then restart and log in on Ubuntu the brightness seems to be the one adjusted on windows, sliding the brightness bar on ubuntu doesn't make it brighter if i dimmed to the lowest on windows, I guess the maximum is set as the one that is currently set on windows. Any idea what's going on and what to do with that?

Thanks.

---

### Post by monkeybrain20122 on 2013-08-22
What is your graphic card? What driver do you use?

It seems that brightness is not adjustable for Nvidia cards if use the proprietary driver, but it can be changed with the open source driver. But I have tried that only on two laptops.

---

### Post by KylePhys on 2013-08-23
VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Device 9647.

But there is a brightness bar, it just doesn't work (it worked some time ago, before updating).

---

### Post by aditya8892 on 2013-08-23
Is it Hybrid graphics?
if yes there is a quick fix [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1007765/comments/95](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1007765/comments/95)
It just works not really a bugfix.

---

### Post by KylePhys on 2013-08-23
what is hybrid graphics? Where should i look for it?

---

### Post by aditya8892 on 2013-08-24
Newer processors like intel core i series have a gpu. When coupled with dedicated gpu they form hybrid graphics.
What is you hardware?

---

### Post by Jonathan Andrew Upton on 2013-08-24
The brightness in Ubuntu is different to Windows because of the quality of the graphics card that Ubuntu usually runs off of. It could be because Ubuntu has not been tried and tested on the particular model of computer during the development process, but all I can think of is that it is down to not all systems being the same. Nevertheless, as long as you can see what is said on the screen, does it really matter?

---

### Post by KylePhys on 2013-09-01
Amd a6

---

