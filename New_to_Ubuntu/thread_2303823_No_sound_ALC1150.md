---
title: "No sound ALC1150"
date: 2015-11-21
forum: New to Ubuntu
---

### Post by irishhybridz on 2015-11-21
Hi, I just finished dual booting windows 10 and Ubuntu. On windows 10 my sound works no problem through my headphones, but on Ubuntu i only get sound through HDMI. im using realtek alc1150, my motherboard is msi g45, ive tried analog output and digital and they wont work. im running Ubuntu 15.10, would i need to download alsa drivers or is ubuntu 15.10 ok? please help as i cant use Ubuntu without sound

---

### Post by grahammechanical on 2015-11-21
I am going to say something that sounds stupid but it may not be. Have you plugged in the headphones?

 On Ubuntu 15.10 Sound Settings will not show an option for output to headphones. But if we plug in the headphones into the headphones socket an option to select Headphones Built-in Audio will appear in the Output tab panel labelled "Play sound through."  We can then change the setting from HDMI/Display port to Headphones.

It took me awhile to figure this out when I was using 15.10 during its development period.

Regards.

---

### Post by irishhybridz on 2015-11-22
yes they are plugged in. im connecting my headphones through the back panel of my motherboard, sound works in windows 10

---

### Post by irishhybridz on 2015-11-22
Dont know if this helps or not but my headphones are not shown as headphones on windows, its connected to a fiiO e09k amp through a 6.3mm cable, on the back of the amp its connected through rca to 3.5mm cable, the 3.55m cable goes into the back of my pc so its connected to the motherboard

---

### Post by mastablasta on 2015-11-24
maybe HDMI is set as default output and that setting saved in alsamixer !?

---

