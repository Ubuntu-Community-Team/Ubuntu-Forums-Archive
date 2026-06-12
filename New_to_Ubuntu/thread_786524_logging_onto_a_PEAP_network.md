---
title: "logging onto a PEAP network"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by betterthanjordan79 on 2008-05-08
im at college and i asked at the computer helpdesk how do you connect to the college network and they didnt know...yes....im at like the biggest IT in Ireland and they dont know how to connect linux to the network...anyways i was wondering id anyone here knew how to connect to it. I scanned the booklet that helps you connect both macs and xp. hopefully with this booklet someone will be able to point out what i need to do. Thanks to anyone who is willing to help me out here.

---

### Post by betterthanjordan79 on 2008-05-08
anybody have any ideas at all??

---

### Post by Whiffle on 2008-05-08
Wow those books are pretty useless lol.  Yeah it can be done, probably with networkmanager.  I havn't used NM in forever though.  I've got a wpa_supplicant.conf file that connects to my school's PEAP network that I'll post up in a minute once my laptop boots.  You should be able to take the options listed in it and use them in network manager, although I would recommend testing it out using wpa_supplicant first on the command line.

wpa_suppliant -c <configuration_file> -i <wireless interface> -D <wireless driver>

---

### Post by Whiffle on 2008-05-08
Here ya go:

---

### Post by betterthanjordan79 on 2008-05-09
cheers man-ill c how i get on next day im in college.

---

### Post by betterthanjordan79 on 2008-05-23
ok i tried this 2day but i cant seem to get it to work...anyone else able to help me...

---

