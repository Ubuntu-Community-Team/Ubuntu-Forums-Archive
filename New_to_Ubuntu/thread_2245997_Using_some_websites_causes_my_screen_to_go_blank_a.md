---
title: "Using some websites causes my screen to go blank and computer to become unresponsive"
date: 2014-09-27
forum: New to Ubuntu
---

### Post by MyBigToe on 2014-09-27
I am a new user that has installed the Google Chrome browser (so I can use the same bookmarks and settings on all of my PCs) and have come into a strange bug. 
If I open TweetDeck within Google Chrome or visit certain links, one being:
[https://www.google.com/chrome/?platform=linux](https://www.google.com/chrome/?platform=linux)

The screen turns off and will not turn back on again until I restart my PC. 
I am using lubuntu on my laptop.

It is using Ubuntu 14.04.1 LTS and it is installed on a Dell Inspiron 1525.
I'm guess you geniuses will need some extra info than that, but I'm not sure what.

---

### Post by Richard_Elliott on 2014-11-11
I've experienced this issue using Firefox on Ubuntu 14.04 LTS, on a HP DV6700 laptop with Intel 965GM graphics. I can repeat the symptom by visiting the Google Chrome webpage in Firefox. The same page will load successfully in Opera.

he screen will go black, with no apparent way to recover other than to power off, then on. If I force the machine to sleep and wake, I get a partial recovery (mouse pointer, wallpaper and a message bubble or two), but dock, menu bar, and previously open windows are nowhere to be seen.

---

### Post by mollie4168 on 2014-11-11
The same thing was happening to me today in Firefox on Xubuntu 4.10.  Thank you Richard for the tip about other browsers, as that essentially covers this issue for me.  I was only going to use Chrome for one website, but I can get around it now.

---

### Post by claracc on 2014-11-12
I have not any problem with the web page addressed, using firefox 33.0 in ubuntu 12.04 fully updated and graphics card:

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)

I use adblock and flashblock as addons in the browser in order to stop the heavy load of images and animations, perhaps this is the problem with certain webpages.

---

### Post by naz3 on 2014-12-22
Hi
I'm having the same problems as described here, I've tried Firefox and chromium.

I also seem to get the issue on Linux Mint 14/17.1

My graphics driver.
VGA Compatible Controller: Intel Corporation Mobile GM965/Gl960 Integrated Graphics Controller (primary) (rev 03)

This is on a Samsung Q45 Laptop

---

### Post by christian51 on 2015-01-12
Is something going to be done about this? I have the same problem (running 64 bit with intel graphics over VGA but i can confirm it also happened during my 32 bit install). Maybe someone could put the bug on launchpad (I've got no experience with that) and its kinda annoying cause i cant change my hideous chrome theme because the store wont work...:mad: (for me i get the error on Chromium, Firefox and Midori) I feel like it might be a problem with the VGA and Intel graphics together as it doesnt happen if i just use my laptop without the external dislpay.

Cheers Guys

---

