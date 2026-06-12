---
title: "Dell 8500/WPC54G pcmcia card and ubuntu 11.10...can't get it working"
date: 2012-02-22
forum: New to Ubuntu
---

### Post by Louey on 2012-02-22
Hi all,

I have scoured the forums and tried all kinds of suggestions but just can't get my wpc54g to work. If I highlight wireless in the network settings it shows a hardware address but says the firmware is missing. 
Any help would be greatly appreciated..

Thanks...

---

### Post by primevci on 2012-02-25
hey this worked for me open up terminal and type this

sudo apt-get install firmware-b43-installer

---

### Post by gopher38 on 2012-02-25
primevci, you should probably post the card version that you have, because I think that the different versions (1-5) of the WPC54G card are very different.  

I'm in the same boat as you.  I had WPC54G v2 wireless working on Jaunty, but I set it up probably 5 years ago. I don't remember which steps I had to take, but I remember that it took me forever to get it to work, changing things back and forth, installing and removing this and that.  I never updated my ubuntu version just because every time I did, the wireless stopped working and I couldn't get it back.

Finally decided to change to lubuntu oneiric this week, hoping that they would have this worked out by now, but no luck.  I suppose that this card is so old that no one cares about it any more.

I tried the command above (sudo apt-get install firmware-b43-installer), but that didn't do anything.

---

### Post by primevci on 2012-02-26
i have version 1

---

### Post by gopher38 on 2012-02-27
Just wanted to say that I got mine to work with ndiswrapper.  wpc54g ver 2, lubuntu, oneiric, hp n5430.  Search the forum for wpc54g ndiswrapper technique.  The post doesn't say oneiric, but it works.  Not sure for version 1.

---

