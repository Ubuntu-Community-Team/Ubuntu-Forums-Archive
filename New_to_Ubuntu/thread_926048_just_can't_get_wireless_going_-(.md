---
title: "just can't get wireless going :-("
date: 2008-09-21
forum: New to Ubuntu
---

### Post by iwannalearn on 2008-09-21
Story so far

Acer 3000

i downloaded restricted drivers Broadcom B43 wireless driver. Then the orange wireless light came on but still could not connect to my router even with roaming.

then tried Windows wireless driver

Installed ndisgtk
System > Admin > Windows Wireless Drivers 
Installed bcmwl5.inf

i can see the driver with Hardware present: Yes in GUI

Then edited blacklist in /etc/modeprobe.d

# replaced by b43 and ssb.
blacklist bcm43xx
blacklist b43
blacklist ssb

Rebooted and now the orange wireless light is off!

And i am lost from here!

Please help

---

### Post by linux5uper on 2008-09-21
I had exactly the same problem. Broadcom drivers are tricky, and you need the exact driver for your card model (it won't necessarily work with the same driver that works under windows on your machine).

Follow carefully the following guide. It will setup ndiswrapper with the correct driver for your model (at step 2, choose carefully):

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Instructions](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Instructions)

I also had to apply the Hardy fix.

---

### Post by twitch2197 on 2008-09-21
yea that's my suggestion... try ndiswrapper

---

### Post by willca on 2008-09-23
If you end up back using Broadcom firmware by 

$ sudo apt-get install b43-fwcutter 
and follow the rest of the prompts...

to check if your wifi nic is working..

$ sudo iwconfig wlan0 
or
$ sudo iwlist wlan0 scan

---

### Post by Crafty Kisses on 2008-09-23
I'd like to see the results of this command:
```
lshw -C network
```

---

