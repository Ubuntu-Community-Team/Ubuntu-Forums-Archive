---
title: "Wireless Network issue with 8.04"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by srbrowning on 2008-05-17
I bought a Dell Inspiron E1505 last year for the specific purpose of dual booting XP and Ubuntu.  I've dabbled in Ubuntu for about 2 years now, but couldn't get sound to work on my main PC (Blast Creative!!!) and this laptop just doesn't really like Ubuntu.  This brings me to my problem...

I have a wireless network in the house.  Security is WEP and router is a D-Link DI-624 with a Firmware version of 2.70 (Aug 19, 2005).  (I don't want to update the firmware.... please don't make me update the firmware!)   

I, of course, have had trouble getting the wireless to connect to my network.  I did the whole ndiswrapper tutorial and actually have my wifi light on... soooo, I "think" wifi is working.  I "think" the problem is software or network related.  I typed "iwlist scan" and found all the wireless networks in the neighborhood, including my own.  (Good sign, Bad sign???)  The blasted thing just won't connect to my network!

I've gotta say, I'm not a network guy; so, the dumbest solution will probably be the one that works.  Does anyone have any ideas?  I have searched this and other forums, but haven't found anything that has worked.

---

### Post by shifty_powers on 2008-05-17
first thing first, what is the network card in your laptop, and what version of ubuntu are you using?

---

### Post by alex_anthony on 2008-05-17
I would guess that he's using hardy (see thread title)
and 1501s generally use broadcoms

---

### Post by quelx on 2008-05-17
Have you tried it with WEP disabled on the router?  Turning it off for a few minutes and try with your laptop.

If that works try the suggestions from this page:
[http://mediakey.dk/~cc/howto-use-wep-encryption-with-ubuntu-linux/](http://mediakey.dk/~cc/howto-use-wep-encryption-with-ubuntu-linux/)

first find out the name of your adapter```
sudo iwconfig
``` note the adapter that has wireless extensions and do these steps substituting eth2 with the adapter from above and your essid name and key

```
sudo iwconfig eth2 essid yournetworkname
sudo iwconfig eth2 key yourwepkey
sudo ifconfig eth2 up
sudo dhclient3 eth2
```

If this works then try again with Network Manager

```
network-admin
``` unlock using your password and enter the settings.

If this goes well think about changing your network fromm WEP to WPA-PSK

[http://blogs.zdnet.com/Ou/index.php?p=41](http://blogs.zdnet.com/Ou/index.php?p=41)

---

### Post by srbrowning on 2008-05-17
Right and right.  Broadcom and 8.04

---

### Post by shifty_powers on 2008-05-17
heh, didn't even register the 8.04 in the title ;)

---

### Post by alex_anthony on 2008-05-17
also, you may be able to find some good advice [here]("http://www.ubuntu1501.com")

---

### Post by nowin4me on 2008-05-17
Did you type the correct WEP key in?
This has happend to me before and it was because I tyed it in incorretly.

---

### Post by shifty_powers on 2008-05-17
[http://www.ubuntu1501.com/2007/11/wireless-in-gutsy-gibbon-with.html](http://www.ubuntu1501.com/2007/11/wireless-in-gutsy-gibbon-with.html)

should hold lergely true for hardy ;)

---

### Post by srbrowning on 2008-05-17
Yup... I had two WEP keys set up and typed them both in multiple times.

After I did the whole ndiswrapper thing, I found a I had  a new "wireless interfact"  but when I click "configure" it says "the interface does not exist."

---

### Post by shifty_powers on 2008-05-17
[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

and here as well ;)

---

### Post by srbrowning on 2008-05-17
shifty_powers - I have done all that... correctly, I think.  (but, heck, you never know.)  If I didn't do it right, would I still be able to see the other networks?

---

### Post by shifty_powers on 2008-05-17
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

might be the best one i thgink ;)

---

### Post by shifty_powers on 2008-05-17
follow the last one, would be your best bet i think :D

---

