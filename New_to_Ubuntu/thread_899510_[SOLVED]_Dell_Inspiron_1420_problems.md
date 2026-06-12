---
title: "[SOLVED] Dell Inspiron 1420 problems"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by The ragman on 2008-08-24
Another newbie question. 

My Laptop is a Dell Inspiron 1420 with a few useful things that I can't get to work with Ubuntu. 

First is the internal wireless card, that I can happily live without, as I use a cable connected LAN. 

Second, is the media card reader. Stick the  photo memory card in from my camera, and Vista would bring up the card as a drive.  In Ubuntu, it is not recognized as existing.   This I would use regularly, Does anyone know any way of getting drivers for this?

Other than those two problems, I am very happy with Ubuntu - I have gotten the sound to be perfect, and everything else works great..

software problem, I did not the option to install Flash Player, but now wish to, how do I do that.

Not sure how I did it, but used the terminal and copied a couple of scripts, and second time, it found the memory card reader. Put in the card from my camera that would not display earlier this morning, and it is working...  Serendipity works.

---

### Post by halitech on 2008-08-24
if you open a terminal ( Applications - Accessories - Terminal) and type
```
lspci
```
can you post that back to us so we can see which wireless card you have

---

### Post by carnagex420x on 2008-08-24
I have a 1420 and it won't see a Pro 2 Duo but it will mount a SD card. Also the easy answer for the wireless is to install and enable the b43 driver within the restrictive driver manger. NDiswrapper shouldn't be needed.

---

### Post by The ragman on 2008-08-25
I don't know how it did it, but I followed suggestions from another thread, and got the image card reader working perfectly, the audio to rated output, and the wireless card recognized - I have to set up both the router and the 1420 to use the wireless network - to see if it works - can't do that until next week, as I don't have the code to get into the router - it comes back from vacation next week. 

Thanks for the input.

---

