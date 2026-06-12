---
title: "Can't get wireless connected!"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by ello2003 on 2008-11-07
This is the Spec of my PC, 

[http://www.ciao.co.uk/HP_Pavilion_Media_Center_TV_m7680_uk_Core_2_Duo_E6600_2_4_GHz__6688426](http://www.ciao.co.uk/HP_Pavilion_Media_Center_TV_m7680_uk_Core_2_Duo_E6600_2_4_GHz__6688426)

I don't no which drivers or (linux equiv) to get this to work.  I am assuming that the wireless adapter is apart of the intel express board??

cheers

---

### Post by B34ST1Y on 2008-11-07
I don't see a posted spec of your computer. If you're having trouble with your wifi, try installing the madwifi drivers

---

### Post by ello2003 on 2008-11-07
added url to spec of pc thanks for fast response

---

### Post by B34ST1Y on 2008-11-07
> **B34ST1Y said:**
> I don't see a posted spec of your computer. If you're having trouble with your wifi, try installing the madwifi drivers

try installing the madwifi drivers 

[http://madwifi-project.org/wiki/news/20081106/new-primary-project-domain](http://madwifi-project.org/wiki/news/20081106/new-primary-project-domain)

---

### Post by ello2003 on 2008-11-07
ok , ive fired my desktop up installed it onto my hard drive rather than booting for disk transered that tar file thing to my desktop and now have loads of files how do i install?

is it not like a packaged installer like windows
or drag and drop like OSx?

---

### Post by ello2003 on 2008-11-07
all I want to do is install a wireless adapter to get on the net so i can play with ubuntu

Cant see me switching at this rate, far too complicated just to install a prog got to be missing something here cos my god over 2 hours of reading and pulling my hair out and still no further forward

on my mac i download drag and drop jobs a good un
shame i can't install that onto my desktop pc

PLEASE HELP A NEWB!

---

### Post by poldie on 2008-11-07
> **ello2003 said:**
> all I want to do is install a wireless adapter to get on the net so i can play with ubuntu

Cant see me switching at this rate, far too complicated just to install a prog got to be missing something here cos my god over 2 hours of reading and pulling my hair out and still no further forward

on my mac i download drag and drop jobs a good un
shame i can't install that onto my desktop pc

PLEASE HELP A NEWB!

This page explains how to install madwifi drivers:
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

It's for a different pc to your but perhaps the process (and end result) is the same.

---

### Post by Crafty Kisses on 2008-11-07
What are the results of this command?
```
lshw -C network
```

---

### Post by ello2003 on 2008-11-07
> **Codename said:**
> What are the results of this command?
```
lshw -C network
```

hardware kister (kshw) - B.02.12.01

usage: lshw and then loads of other options

---

### Post by newbee70 on 2008-11-08
I am a newbee also so take my advice with a grain of salt.

1. have you gone into system admin, drivers to see if your wifi card is enabled?

2. are you online via nic so that if drivers are needed ubuntu can search for them?

---

