---
title: "Consequences of limiting myself to my laptop's integrated graphics chip"
date: 2013-11-24
forum: New to Ubuntu
---

### Post by lesliek2 on 2013-11-24
I have an H-P dv7-4223ca laptop, running Ubuntu 12.04.
 

 The result of running “lspci | grep VGA” is as follows:
 

 “01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS880M [Mobility Radeon HD 4225/4250] 
 02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Robson CE [Radeon HD 6370M/7370M] (rev ff)”
 

 I use the open source driver called, I think, radeon.
 

 I have the heat sensing software packages installed and I get readings from three sensors: first, acpi-tz-virtual-0; secondly, radeon-pci-0200; and, thirdly, k10temp-pci-00c3.
 

 I figured out two things: first, how to change the BIOS setting that had the laptop’s fan running constantly; and, secondly, how to turn off my discrete graphics card.
 

 As a result of those changes, the fan is very much quieter and the usual readings from the first and third sensors dropped from about 80 degrees Celsius to about 60 degrees Celsius. (The second sensor shows a constant -128 degrees Celsius.)
 

 I have two questions.
 

 First, despite the gains so far as heat and fan noise are concerned, will I lose too much in graphics performance by limiting myself to the integrated graphics chip?
 

 Secondly, can I make up for that loss of performance to any extent by switching from the open source driver to the proprietary one?

---

### Post by Mark Phelps on 2013-11-24
> Secondly, can I make up for that loss of performance to any extent by switching from the open source driver to the proprietary one? 

Probably NOT -- because the drivers at the AMD site do not support the hybrid graphics setup on your laptop.  Those drivers only come from the manufacturer (of the laptop) and those only support MS Windows.

---

### Post by lesliek2 on 2013-11-24
Thanks very much for your reply Mark.
So far, I've only turned off the discrete graphics card temporarily after the computer's booted up, although the place where I got the commands to turn it off also gave information on a file to edit so that the discrete graphics card would automatically be turned off during every bootup.
I don't know whether this is possible, but I'm wondering whether, if I can get the discrete card turned off during bootup before the relevant driver loads, the driver would then think that I had only the integrated graphics chip. (Of course, that assumes that the proprietary driver even works with the particular integrated graphics chip that I have, something I don't know.)
As to the first question I asked, since my original post, I've found glmark2, installed it and run it successfully with only the integrated graphics chip operative. I've now got a lot of results, but I have no real idea what they mean. If you have any thoughts on how I should understand the results, I'd be very grateful to hear them.

Thanks again,

Leslie

---

### Post by Bashing-om on 2013-11-24
lesliek2; Hi !

Maybe of some help, there has been a lot of progress made on the hybrid graphics front lately by the open source developers:
[http://test.ubuntu-discourse.org/t/hybrid-graphics-with-amd-and-nvidia-in-ubuntu-13-10-and-12-04-3/1144](http://test.ubuntu-discourse.org/t/hybrid-graphics-with-amd-and-nvidia-in-ubuntu-13-10-and-12-04-3/1144)

we have worked to officially support Hybrid graphics in Ubuntu 13.10 and in 12.04.3 LTS.
[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)

Linux now supports Hybrid Graphics Systems with Ubuntu 13.10
[http://rudrageek.com/linux-now-supports-hybrid-graphics-systems-ubuntu-13-10/](http://rudrageek.com/linux-now-supports-hybrid-graphics-systems-ubuntu-13-10/)

[INDENT][INDENT]just my little bit
[/INDENT][/INDENT]

---

### Post by lesliek2 on 2013-11-25
Thanks for taking the trouble to reply Bashing-om.

The coolness and quiet of my laptop when I have just the integrated graphics chip running are such a relief to me that I'd prefer to use my computer with the discrete graphics card always off, unless I'm told that the performance of the integrated graphics chip is so bad that I absolutely have to have the discrete graphics card on. So far, admittedly, just a couple of days, I haven't noticed any difference at all in what appears on my screen. In fact, now I'm wondering whether the discrete graphics card was ever called into action. Maybe all it ever did was just sit there, throwing off tremendous heat!

Thanks again,

Leslie

PS On this question of using the proprietary driver, I found that version 13.1 of it, not the latest, is said to work with my integrated graphics chip.

---

### Post by Yellow Pasque on 2013-11-25
> **lesliek2 said:**
> First, despite the gains so far as heat and fan noise are concerned, will I lose too much in graphics performance by limiting myself to the integrated graphics chip?

It depends on what tasks you use it for. It should run Unity fine, but don't expect a lot of FPS on demanding games.
 
> Secondly, can I make up for that loss of performance to any extent by switching from the open source driver to the proprietary one?
That's probably not an option since AMD dropped support for that card. You would have to do a fresh install of 12.04.1 to use the proprietary driver since newer kernels and Xservers won't work with the legacy Catalyst driver.

---

### Post by lesliek2 on 2013-11-25
Thanks for the reply Temujin.

The only and therefore most demanding game I play is solitaire! I did try to play some video and it seemed exactly as usual.

I understand what you're saying about using an old version of the proprietary driver, so I'll just give up on that idea.

Thanks again,

Leslie

---

