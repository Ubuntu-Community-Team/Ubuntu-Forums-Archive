---
title: "Wireless Suddenly Stopped"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by nina_aoki on 2008-07-28
Hi guys,

The wireless in my HP dv5000 notebook suddenly stopped working is morning and I have no idea how or where to begin looking.  Any direction or help in fixing this would be much appreciated.  I've searched the threads but can't seem to find something which I can understand.

Thanks much,

nina

---

### Post by kool_kat_os on 2008-07-28
Can you search for networks...or is the wireless icon completely gone?

---

### Post by nina_aoki on 2008-07-28
Hi.

No, I see nothing.  I used to be able to see a list of networks in my area and connect to my own.  Now that's gone-- the area which should enable me to select wireless networks when I click on that in my top bar is indented and I cannot select or hilite the wireless option, and I can't see any networks.  It's as if the wirless card radio isn't working.  Networking still works via ethernet.

nina

---

### Post by kool_kat_os on 2008-07-28
Ok...this may sound stupid...but if you have a laptop...is the wireless switch on?

---

### Post by nayanm on 2008-07-28
> **nina_aoki said:**
> Hi guys,

The wireless in my HP dv5000 notebook suddenly stopped working is morning and I have no idea how or where to begin looking.  Any direction or help in fixing this would be much appreciated.  I've searched the threads but can't seem to find something which I can understand.

Thanks much,

nina

This may sound kind of obvious, but have you accidentally turned off the wireless card? Most laptops have a switch to turn the wireless card on and off. I remember when I first got my laptop and the wireless card wasn't working. It turned out that I had accidentally turned the switch off.

If that's not the problem, go to System > Adminstration > Network and see if you can find your wireless card there. If you can, this probably means that for some reason, Ubuntu can't access your wireless router.

If that's the case, run
```
ifconfig
``` and
```
iwconfig
```

in a Terminal and post the output here.

---

### Post by kool_kat_os on 2008-07-28
> **nayanm said:**
> This may sound kind of obvious, but have you accidentally turned off the wireless card? Most laptops have a switch to turn the wireless card on and off. I remember when I first got my laptop and the wireless card wasn't working. It turned out that I had accidentally turned the switch off.


hey...thats what i said :)

---

### Post by nayanm on 2008-07-28
> **kool_kat_os said:**
> hey...thats what i said :)

haha. But mine had a story with it. =D (lol, sorry! you posted while i was typing my reply)

And also, nina: try restarting the laptop. I've heard cases where the wireless stops working after you come out of hibernation or sleep mode. And it can't hurt anyways.

---

