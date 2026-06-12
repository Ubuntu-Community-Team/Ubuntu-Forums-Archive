---
title: "DMA enabling problems"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by redtabulation on 2008-06-20
I know there are many threads on this one but, i am getting some problems.
When I run hdpram"" i get something like ""ioctl"" and it doesnt change the settings 
My drives run painfully slow incl. DVD
Help appreciated.

---

### Post by redtabulation on 2008-06-20
ANyone. I Am here ask me to do some diaganostics or whatever

---

### Post by redtabulation on 2008-06-21
Reply anyone. I really dont know what extra info to give. ASk me!!

---

### Post by RomeReactor on 2008-06-21
Hi. Did you run hdparm as root?
```
sudo hdparm -d1 -k1 /dev/dvd
```
(**/dev/dvd** is just an example).

---

### Post by forestpixie on 2008-06-21
This might help and might not - I had a dodgy cable do that to me - spent ages until I saw a boot message regarding Primary IDE cable error

---

### Post by mc4man on 2008-06-21
If your running 7.10 or 8.04 in most cases hdparm can no longer set anything but can give some info. ```
sudo hdparm -I /dev/dvd
```or /dev/dvd1, /dev/scd0 ect.
Dma should be enabled by default though I do remember a thread about where it was disabled due to a conflict - can't find atm
Maybe look for references in your logs or ```
grep ' DMA' /var/log/syslog
``` or .../dmesg, /debug ect.

---

