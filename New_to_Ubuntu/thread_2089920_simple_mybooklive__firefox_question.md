---
title: "simple mybooklive / firefox question"
date: 2012-11-30
forum: New to Ubuntu
---

### Post by CmdGabriel on 2012-11-30
Hi All,

I have got a new WD MyBook Live NAS hard disc. I can access it with firefox under windows xp (dual boot) with
[http://mybooklive](http://mybooklive)

Unfortunatly the same URL leads my with ubuntu firefox to a google search for "mybooklive", which is obviously not helpful.

If i would know how to detect the ip adress of the WD My Book Live, i could just enter
[http://192](http://192).... 
but I don't know how.

pls help!

Many thanks
Gabriel

---

### Post by dannyboy79 on 2012-11-30
can't you log into your router and look at the devices that are recieving an IP address? You could also just try the next in order IP from your ubuntu machine. Meaning, if your ubuntu is 192.168.0.2, you could try 192.168.0.3 so on and so on.

Very curious why entering [http://mybooklive](http://mybooklive) works in Windows but not Ubuntu.

You could also try these commands entered into a terminal session
```
findsmb
```
or
```
smbtree
```
This may show the ip address and the shares it has on it

---

