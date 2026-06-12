---
title: "Sony Ericsson P910i"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by shoaibi on 2008-06-07
The other day i was searching for softwares on how could i connect my P910i to Ubuntu 8.04LTS and i found couple of them, but nothing worked... I wanted a software suite like nokia.sony ericsson pc suit with utilities like backup, message send and receive and etc..
I have Datacable as well as bluetooth device... and ubuntu is recognizing my ubuntu so that not the problem, problem is the software...

---

### Post by briwood on 2008-06-08
Don't expect to find an open solution with all the bells and whistles of the Nokia suite.  For backing up the data on your phone you should try Wammu.   It works fine with my Ericsson K800.  To install it:

```
sudo apt-get install wammu
```

This next is consistent with my experience:

[http://ubuntuforums.org/showthread.php?t=598302&highlight=k800i](http://ubuntuforums.org/showthread.php?t=598302&highlight=k800i)
> When I connect the phone, I choose phone mode so that I can sync it. If I choose disk mode, then the phones memory card is mounted as an external drive (great for getting mp3's on it etc, no good for syncing). In phone mode, Wammu can detect it on the USB port

---

### Post by shoaibi on 2008-06-08
how can i connect my phone to wammu?
i tried:
symbian absed phone
sony ericsson phone

but didnt work, tried all the different connection types

---

### Post by shoaibi on 2008-06-16
i get this when i search for bluetooth connections in Wammu:
```

Wammu is now searching for phone:
Scanning for bluetooth devices using PyBluez
Checking 00:0F:DE:87:E9:2E (Shoaibi) - Guessed as Sony-Ericsson - ['blueat', 'blueobex', 'bluerfgnapbus']
Bluetooth device scan completed
Finished 00:0F:DE:87:E9:2E (Shoaibi) - Guessed as Sony-Ericsson - ['blueat', 'blueobex', 'bluerfgnapbus']
All finished, found 0 phones
No phone has been found!

```

---

