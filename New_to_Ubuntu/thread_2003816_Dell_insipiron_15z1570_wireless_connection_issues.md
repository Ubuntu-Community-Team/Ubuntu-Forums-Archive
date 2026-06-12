---
title: "Dell insipiron 15z/1570 wireless connection issues"
date: 2012-06-14
forum: New to Ubuntu
---

### Post by Shinifish on 2012-06-14
I am new to linux and have managed to install the 12.04 version of ubuntu on my laptop with no problems, however when I try to connect to my wifi it says that there  is a hardware switch  preventing me from using wifi.

The way I installed ubuntu was to make a seperate partion for ubuntu and I kept a partion with windows on it, and when I boot windows the wireless is working without me touching a hardware switch.

I could not find something that I thought would help with this through searching, and I have found nothing about using this specific model of laptop. 

when I ran the 
[FONT=monospace]lspci | grep wireless
function it returned nothing.

If I posted this in the wrong area moderators I am very sorry I thought this should be posted here.
[/FONT]

---

### Post by migs73 on 2012-06-15
Hi there,
You say you don't to use a hardware switch in windows. Do you have a switch? Have you tried it? 
If you do not have a physical switch, you may need to press Fn F2 to enable the wifi (it may not be F2 but it is on my dell, it will probably have a picture of a transmitter on it).
If this does not work, please run the code
```
lspci
```
on its own with out the grep command. This will return quite a big list, but will let us see all the hardware on on the pci bus.
If you could post the output in code tags (use the # symbol at the top of the message box when writing your post) it'll make easier to read.

---

