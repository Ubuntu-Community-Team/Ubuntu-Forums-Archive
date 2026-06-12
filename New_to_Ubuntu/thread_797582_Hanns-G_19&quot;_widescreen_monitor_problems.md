---
title: "Hanns-G 19&quot; widescreen monitor problems"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by MattGEri on 2008-05-17
Hey Guys and Gals,

I just installed Ubuntu and I am having trouble with my monitor, I cant get it to display at 1440*900. It is currently display at 1024*768 (which is the highest res I can select). My graphics card is a Nvidia GeForce 7100 GS and it seems to be installed fine (I used Envy to install the Nvidia Settings tool as well.

Any help on how to get my monitor displaying at 1440*900 would be greatly appreciated!

Thanks a lot.

- Matt

---

### Post by dstew on 2008-05-17
Press Alt-F2 and enter```
gksudo displayconfig-gtk
```Click on the Monitor type, and you should get a list of manufacturers. Then, pick a manufacturer, and you can tell xorg.conf the exact monitor you have. It should then give you the resolutions you need. If you can't find your exact monitor, you can still enter new refresh rates and display resolutions for a generic monitor.

---

### Post by MattGEri on 2008-05-17
Hey,

Thanks for the help. I have tried that before and tried both plug and play monitor and 1440*900 LCD Panel but both only let me have a resolution of 1024*768. See the screenshot attached - it was take with LCD Panel 1440*900 generic monitor selected.

Any advice?

- Matt

---

### Post by dstew on 2008-05-17
Did you check the System --> Administration --> Hardware Drivers to see if a restricted driver is available?

---

### Post by MattGEri on 2008-05-17
Hi Again,

Yes I did. I enabled the restricted driver for my video card. See screenshot.

- Matt

---

### Post by MattGEri on 2008-05-17
I just got it working! The problem was that I did not click the "widescreen" option on the generic monitor. I have attached a screenshot for anyone who has the same problem in the future! Thanks dstew for your help!

---

