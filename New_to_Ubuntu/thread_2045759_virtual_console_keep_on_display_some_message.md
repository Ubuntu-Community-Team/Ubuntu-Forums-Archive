---
title: "virtual console keep on display some message"
date: 2012-08-21
forum: New to Ubuntu
---

### Post by howsiyu on 2012-08-21
When I go to virtual console, it keeps on display something like
[ 2930.964408] [drm] 0000:01:00.0: nouveau unknown i2c port 51
[ 2930.965055] [drm] 0000:01:00.0: nouveau unknown i2c port 54
for like every 5 seconds.
I can do everything normally like log in and use vim in it but the message keep coming out and is very annoying.
What does this mean and how can I fix it?
I am using ubuntu 12.04 LTS on Intel® Core™ i5-2450M CPU @ 2.50GHz × 4.

---

### Post by simonwatsonsjw on 2012-11-07
Hi howsiyu,
First - apologies, I'm a newbie and this is my first post ever on ubuntu forums. As such I am happy to be corrected by wiser minds. 

These days, graphics processing is usually carried out in a separate standalone chip called a graphics processing unit (GPU) outside of your CPU. I think your log entry means your open source graphics driver (nouveau) isn't working with your GPU. The result is that your computer falls back to using your CPU to process your graphics instead. This works fine these days but means you are wasting the muscle you have available via your GPU. The solution (assuming you are ok with using non open source drivers) is to go to the website of the manufacturer of your GPU and get their proprietary driver. Otherwise, if your computer is working as needs be, leave your GPU unused and don't worry about it.

Regards,

Simon

---

