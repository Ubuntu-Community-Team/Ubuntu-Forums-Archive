---
title: "[SOLVED] need lots of help"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by Modnar1 on 2008-06-03
hi this is the first time i've installed linux and i'm having some issues with a few things, so if someone can help with one or all of them then it would be much appreciated, anyway here's the list:
1. i can't install the darker ice theme, i have extracted the files from the download and put them in the.theme folder, but it still won't appear in the user interface settings
2. I can't get compiz working, according to synaptic manager everything is installed, but even after i've enabled effects and such from the settings menu nothing happens
3. I can't get the avant window navigator dock to work, it's installed but when i click to open it a small window opens in the top left corner of my screen for half a second and then closes, and that's all that happens, no dock appears
4. I have a sWeex usb WiFi adapter (uses RaLink rt2500 drivers) i can connect to my home network but i don't seem to be able to connect to the internet as every page just keeps on searching for ages before eventually timing out

---

### Post by KenBW2 on 2008-06-03
**1. i can't install the darker ice theme**
You don't put the theme in the .theme folder. To install a theme:
a) Download the theme. Don't extract the archive
b) Open System > Preferences > Appearance and click Install...
c) Browse to the file you downloaded and double-click it. The theme should now appear

**2. I can't get compiz working**
It could just be that your graphics card doesn't support it: I've certainately come across a couple that don't

I'm sorry, I can't help you on the other two :(

---

### Post by rbc on 2008-06-03
3. You need to have a compositor, like Compiz, running for AWN to work. Post some details about your graphics card. Honestly, I won't be able to tell you if the card is good enough, or compatible, but I'm sure some smarter folks out here can

---

### Post by lisati on 2008-06-03
4: If your home network goes through another computer, you might need to configure your other computer to share its internet connection

---

### Post by Modnar1 on 2008-06-04
okay, firstly i'm running xubuntu so there isn't a system > preferences > appearance folder, sorry i forgot to make it clear that i was using xubuntu. 
My graphics card is a 16mb ati rage ultra, so it probably isn't capable of running compiz, though the compiz test said it should work, but i'm not sure if that tested my graphics card's capability. and lastly my network goes through a wifi router, and all my other wireless devices work fine with it and can get internet with no problems, xubuntu can find the netwrok and connect to it but it just can't get the internet, and my router is setup to accept any new devices so long as they have the code so i don't think there are any issues with that. thank you all for your replies so far!

---

### Post by KenBW2 on 2008-06-06
Ah I didn't realise. *Boots Xubuntu laptop*. Yea, you're right about the themes folder. You might have been trying a non-xfce theme. [http://www.xfce-look.org/](http://www.xfce-look.org/) is a good place to look.

About your graphics card, the [ATI Graphics Card Support list]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti") is a good place to look. I can't find your specific card there, but you'll know more aboiut that I do. I did a quick search in Synaptic, and you might need to make sure you have xserver-xorg-video-ati xserver-xorg-video-ati-dbg installed:
> 
sudo aptitude install xserver-xorg-video-ati xserver-xorg-video-ati-dbg

This might be the solution to your Compiz problem

With regard to your wifi problem. I'm far from competent on this, but a good thing to try would be ifconfig. I think it's true that if you have a working connection you'd have an IP address displayed. But don't quote me on that

---

### Post by django0909 on 2008-06-06
A good way to discover if Compiz will work with your hardware setup is by using Compiz-Check, available here [http://forlong.blogage.de/article/pages/Compiz-Check]("http://forlong.blogage.de/article/pages/Compiz-Check")

If you have problems running it, let us know :)

---

### Post by Modnar1 on 2008-06-11
okay i ran compiz check and it said everything should work okay, btw i have now since made xubuntu useless and was forced to reinstall cept this time i choose ubuntu seeing as there generally seems more support for it and it is just easier to use, and i have also upgraded my graphics card to an ATI All-In-Wonder Radeon 9000. 
Can someone please give me a step-by-step guide to installing compiz on ubuntu using open-source ati drivers. and please don't give me a link to another thread cus i've looked at the thread and got confused and suceeded only in stopping the window manager (luckily i knew how to get it going again). Anyways if someone can compile the data into one thread, without the corrections which i'm not really sure where they go, it would be much appreciated

---

### Post by Forlong on 2008-06-12
Modnar1, please post the output of both Compiz-Check and ```
compiz
``` in a terminal.

---

