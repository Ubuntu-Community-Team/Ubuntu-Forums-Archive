---
title: "WiFi is disabled by hardware switch."
date: 2015-08-10
forum: New to Ubuntu
---

### Post by Ryan_ONeil on 2015-08-10
I just got Ubuntu up and running on my Toshiba Satellite laptop this morning.  I was using a wired network so that the internet portions of the install would run smoother.  Now that I have it up and running I want to get the WiFi working again.  After a bunch of work I have stumped myself.  I have tried the "rfkill list" and the "rfkill unblock all" if anyone could help me out with this it would be awesome!:guitar:

---

### Post by jim_deadlock on 2015-08-10
Laptops have a switch or a function key that enables/disables wifi, make sure yours is properly enabled.

If that doesn't fix it, make sure Ubuntu is completely updated (this will ensure your drivers are up to date). Once this is done, click on the wifi icon (top right on the panel in Unity) and see if you have any wifi networks available.

Err.. I just noticed your subject line - does this mean your hardware switch is broken and you can't enable wifi?

---

### Post by grahammechanical on 2015-08-10
What did rfkill list printout? Was it "hard blocked: yes?" Then you need to press a keyboard combination to switch the wireless adapter back on. Do you have Windows installed on this machine? If Wifi is switched off in Windows then it will also be switched off when you load Ubuntu. You could also try

```
sudo ifconfig wlan0 down
```

followed by

```
sudo ifconfig wlan0 up
```

Regards.

---

### Post by Ryan_ONeil on 2015-08-10
I have tried the fn+f8 (which enables and disables the wifi) but nothing seems to happen, i went in to the system settings and all it did was toggle the airplane mode.  I do believe that everything is up to date but I can look again.   When I ran the rfkill list it says soft block no hard  block yes

I do not have windows on this machine any more.  I completely replaced it with Ubuntu. When I ran the "sudo ifconfig wlan0 up" i got "SIOCSIFFLAGS: Operation not possible due to RF-kill"  I think i might just have to partition a portion again and put windows back on to fix this.  I have been doing some research before hand to try to fix the problem myself and I keep running in to the same solutions and fixes that haven&#8217;t worked.

---

### Post by Ryan_ONeil on 2015-08-10
Also would i have to reset my network connections through terminal after completing the code lines for them to take effect?  Or does it take effect immediately?

---

### Post by tgalati4 on 2015-08-10
Welcome to the forums.  Sometimes the wireless is switched off in BIOS.  Try booting into BIOS and look for a way to turn on wireless.  After booting, open a terminal and post:

```
rfkill list
```

Some wireless network cards are problematic in linux.  What card do you have?

```
lspci | grep Network
```

---

### Post by Ryan_ONeil on 2015-08-11
I tired going through my BIOS but i didn't come up with anything. I even went as far as resetting the defaults with in the BIOS any nothing happened.  I couldn&#8217;t say what card I have.  Its just the stock card that came with my Toshiba laptop

---

### Post by Hadaka on 2015-08-11
Hi, ,have you tried this...?
[http://ubuntuforums.org/showthread.php?t=2249263](http://ubuntuforums.org/showthread.php?t=2249263)

---

### Post by Ryan_ONeil on 2015-08-11
I have not but it is worth they try.  I will try that. Thank you.

---

### Post by Ryan_ONeil on 2015-08-11
Well ill be damned.  That worked.  Thank you everyone for helping me out.  :D    Case Solved!

---

### Post by Hadaka on 2015-08-11
While standing on one leg...facing north. ;)
Glad its fixed !

---

