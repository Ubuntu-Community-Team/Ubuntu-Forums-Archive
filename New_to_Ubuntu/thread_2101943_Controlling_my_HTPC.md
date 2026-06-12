---
title: "Controlling my HTPC"
date: 2013-01-05
forum: New to Ubuntu
---

### Post by moist gusset on 2013-01-05
Hi, I've been using ubuntu on laptop for several months and have just set up  a set up an old pc, now also running ubuntu as my HTPC. Rather than buying a wireless keyboard/touchpad can I easily remotely control the HTPC with my laptop?
 Cheers.

---

### Post by tgalati4 on 2013-01-05
Yes.  But not easily.  You can install ssh and log in to the machine to start and stop media.  You can install one of several clients that work with mythtv to control it remotely from other machines.  

In a terminal:

```
apt-cache search mythtv
```

mythtv requires some effort on your part to get it configured and running correctly.

---

### Post by sandy8925 on 2013-01-06
If you have a phone, you can set up XBMC on the HTPC and use XBMC remote on the phone to control XBMC through a common Wifi connection.

---

### Post by gnuser12 on 2013-01-06
Hello,
if you have a remote control you can use the rc to control your htpc
I use the windows media center remote control with easyvdr
Furthermore it is possible to power on the pc with a additional board
more here [http://www.atric.de/IR-Einschalter/index.php](http://www.atric.de/IR-Einschalter/index.php)
The Page is in german
If you have more questions ask again ...

I hope this helped a bit sorry for the eh

---

### Post by steeldriver on 2013-01-06
Not sure how it works if you install mythtv on top of an existing ubuntu HTPC, but at least in the 'clean' install of mythbuntu it gives you an option to enable x11vnc at install time - that autostarts the VNC server when the primary mythtv user is logged in and gives you desktop sharing out of the box

---

