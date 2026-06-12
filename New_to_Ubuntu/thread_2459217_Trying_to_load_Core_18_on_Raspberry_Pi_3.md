---
title: "Trying to load Core 18 on Raspberry Pi 3"
date: 2021-03-13
forum: New to Ubuntu
---

### Post by bradhansen1 on 2021-03-13
Hi All, I'm trying to get Core 16 up and running on my Raspberry Pi 3. I chose that OS because it is 32 bit. I have no idea about anything else
on that version.  Got thought to "To Login in: ssh bradhansen1@(ip address) and then it says "Personalize your account at, [http://login.ubuntu.com](http://login.ubuntu.com). I went there on my
mac and am logged in... Nothing happens on the Ubuntu system won't take any keyboard inputs?? So how do I move on from here?
Appreciate any help that available.
Thank you
Brad Hansen

---

### Post by Holger_Gehrke on 2021-03-13
Ubuntu Core is meant for building 'Internet of Things' devices. You're supposed to develop and (cross-)compile your app on another machine and install that app as a snap via ssh. Basically all access to a machine running Ubuntu Core is going to go through ssh from another computer, unless you install some app that does something else (like read buttons connected to GPIO or read a keyboard connected to USB or react to an RFID reader or ...). So if you're trying to use the raspberry pi as a "normal" computer, Ubuntu Core isn't for you.

Holger

---

### Post by bradhansen1 on 2021-03-13
Holger, Well Things have gotten a lot more sophisticated since the last time I used the OS, 2016, And I appreciate you taking the time to
explain that to me. Now just what would be a good version of Ubuntu to use for my Raspberry Pi 3B?
Thank you,
Brad Hansen

---

### Post by DuckHook on 2021-03-13
The site I use: [https://ubuntu.com/download/raspberry-pi](https://ubuntu.com/download/raspberry-pi)
 
You have a few decisions to make. The Pi3 will take either 32-bit or 64-bit. 32-bit will give you a bit more leeway with cross compatible PI OS drivers and such (PI OS is 32-bit), but 64-bit is where Canonical is taking Ubuntu, so there's a bit of a dilemma.

You will also have to decide if you want bleeding edge (20.10) that lasts only for 9 months and puts you on the upgrade hamster wheel, or the LTS (I believe it's 3 yrs for RPis) though one of those years is pretty much gone. The LTS has had a year to squash bugs so it is more stable/mature.

Don't be too concerned that "desktop" is only available for Pi4s running 20.10. I always install server, then if I want desktop, simply sudo apt install blah-blah-desktop. For DE options and caveats, please see the link in my sig: The Best 'buntu Flavour.

---

### Post by Holger_Gehrke on 2021-03-13
AFAIK the only Ubuntu flavour to directly offer a downloadable image that should work on a raspi 3 is [Ubuntu Mate]("https://ubuntu-mate.org/download/"). Ubuntu itself only offers a server image but of course you should be able to install one of the desktops on that ('apt install lubuntu-desktop', for example). With the raspi B3 having only 1 GB of RAM I'd not expect any Ubuntu Desktop to work well on it. I've tried Ubuntu Mate on my Raspberry Pi 4 with 8 GB RAM and quickly went back to Raspbian / Raspberry OS simply for the speed.

Holger

---

