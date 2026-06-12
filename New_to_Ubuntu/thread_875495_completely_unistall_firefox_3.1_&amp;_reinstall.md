---
title: "completely unistall firefox 3.1 &amp; reinstall ?"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by smooth3006 on 2008-07-30
firefox seems so slow today for me, it takes 30 seconds to load web pages. i know it's not my internet because i ran a speed test and it works fine in my vista install. 

i have a feeling it something to do with firefox. i know i can download the package from mozilla but how can i do a fresh clean install ? the file mozilla gives me is a tar.gz.

---

### Post by Separ on 2008-07-30
Try doing this in a terminal:
```
sudo apt-get purge firefox
```
and then
```
sudo apt-get install firefox
```
The purge will remove firefox completely, including config files so anything you have changed will be lost.

---

### Post by scragar on 2008-07-30
```
sudo apt-get install --reinstall firefox
```?

---

### Post by InfinityCircuit on 2008-07-30
I would suspect something is wrong with your profiles.  Try: 

```
mv ~/.mozilla ~/.mozilla-old
```

This should revert you to the equivalent of a fresh install.

---

### Post by smooth3006 on 2008-07-30
thanks guys ill try it, it's weird as i made no changes.

---

### Post by JoneYee on 2008-07-30
> **scragar said:**
> ```
sudo apt-get install --reinstall firefox
```?

maybe try

```
sudo aptitude purge firefox && sudo aptitude install firefox
```

---

### Post by pi.boy.travis on 2008-07-30
Wouldn't reinstalling Firefox be a bad thing to do, because lots of other Ubuntu components need Firefox and the Gecko rendering engine it provides?

---

### Post by scragar on 2008-07-30
ubuntu won't let you uninstall something if something else needs it without telling you first, that's part of the advantage of a good package manager.

---

### Post by pi.boy.travis on 2008-07-30
This is true. . .  I still have my bad habits from the Windows days. . .

---

### Post by smooth3006 on 2008-07-30
no i couldn't totally remove it at all, i just reset it back to default settings. still didn't help, it's gotta be my internet carrier or something ? im going to play around a bit in vista and see if i notice a problem too.

---

### Post by smooth3006 on 2008-07-30
well im in vista now and firefox 3.1 is running fast as ever, no issues. so we can rule out my internet carrier / cable modem / onboard Ethernet adapter. this is going to be a big issue for me as im always online. id love to stick with ubuntu but if i can't resolve this issue i may have to use vista. 

i did enable the "uncomplicated firewall" in ubuntu the other day, i wonder if that's not the issue ?

---

### Post by pi.boy.travis on 2008-07-30
> **smooth3006 said:**
> no i couldn't totally remove it at all, i just reset it back to default settings. still didn't help, it's gotta be my internet carrier or something ? im going to play around a bit in vista and see if i notice a problem too.

Are you using a wireless connection?  My experience shows that Ubuntu is faster with a wired connection, while Windows has the upper hand in wireless world. . . 

. . . wireless world. . . .I like it!

ufw caused me significant performance problems, but now I'm behind a hardware firewall.

---

### Post by smooth3006 on 2008-07-30
> **pi.boy.travis said:**
> Are you using a wireless connection?  My experience shows that Ubuntu is faster with a wired connection, while Windows has the upper hand in wireless world. . . 

. . . wireless world. . . .I like it!

nope, it's a wired connection.

---

### Post by smooth3006 on 2008-07-31
i disabled ufw via the terminal and now firefox works great. :confused:

by doing that, does that mean im unprotected now ?

---

### Post by scragar on 2008-07-31
well you would have disabled IPtables, so yeah, wonder what rule was causing it to run slow...

---

### Post by smooth3006 on 2008-07-31
> **scragar said:**
> well you would have disabled IPtables, so yeah, wonder what rule was causing it to run slow...

 i installed gufw and turned the firewall on and blocked incoming now the net seems to work fine. i don't know what was going on ?

---

### Post by smooth3006 on 2008-07-31
i dont know what was going on before? i installed gufw and enabled the iptables firewll, disabled incoming and checked the box for ipv6. everything seems to work fine now. very weird if i do say so myself. and yes i know gufw is just a graphical interface but it did the trick for me.

---

