---
title: "screen freeze with wired iphone hotspot"
date: 2019-05-09
forum: New to Ubuntu
---

### Post by aaron-celeste1 on 2019-05-09
When I connect my iPhone (model: SE) wired USB hotspot and use more than 1 or 2 mb/sec, after 2-10 minutes, whatever is on the screen freezes / stops moving. 

Using a different USB outlet on my laptop does not help. I bought a brand new cable and it did not help. Completely  fresh reinstalling ubuntu on my hard drive does not help. I was able  to reproduce the freeze while running ubuntu from a bootable USB. I have a second internal hard drive running Windows 10 OS and it  runs great with no freezing.

Details of the freezing:
The only thing that works while frozen is Fn+F4 which changes the keyboard backlight. 
alt+SysRq+reisub does nothing while it's frozen. 
alt+f1 & alt+f7 seems to make "holding down the power button to hard shut it off" ("hard shutdown" from now on) not as traumatizing... what I mean by this is that when I hard shutdown, there is some big string of zeros in the system logs at the moment  when I hard shutdown. (I got a log generator from my manufacturer (www.system76.com)), but when I alt+f1&f7 while frozen before hard shutdown, there is no long string of zeros in the logs.

Also: sometimes it does this freezing thing while on the grub screen,  but only immediately after a hard shutdown that I did because of freezing. 
Also: I can not open system monitor since doing heavy testing with the freezing a couple days ago. 

Any help is greatly appreciated!!!!!

---

### Post by aaron-celeste1 on 2019-05-10
Today I was unable to make it freeze while on wireless hotspot on Ubuntu, and also unable to make it freeze on wired hotspot in windows OS.

---

### Post by swissz on 2019-07-09
I am having the exact same issue. Is there any news regarding this?

BTW: I run Ubuntu 18.04 with kernel 4.15.0-54-generic + iPhone 6S with iOS 12.3.1

---

### Post by aaron-celeste1 on 2019-07-10
My fix: every time I plug my phone in to my computer while connected to wireless phone hotspot, I make sure to immediately disconnect the wired internet connection that automatically establishes, in the menu near wifi

---

