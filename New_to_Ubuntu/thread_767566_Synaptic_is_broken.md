---
title: "Synaptic is broken"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by cnico88 on 2008-04-25
I get an error: 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I was updating something and since the servers are slow and nothing was loading I just quit out of it. Now when I go back I get this every time.

---

### Post by Oldsoldier2003 on 2008-04-25
> **cnico88 said:**
> I get an error: 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I was updating something and since the servers are slow and nothing was loading I just quit out of it. Now when I go back I get this every time.

```
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade
```


then carry on. the servers are swamped right now though , unless its something you really need I would wait a couple days.

---

### Post by ComputerExpertVK on 2008-04-25
when i entered sudo apt-get update
it put out E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by ComputerExpertVK on 2008-04-25
actually... when i entered sudo dpkg --configure -a
it said
///usr/share/gnome/help/blackjack/el/blackjack.xml:402: parser error : Entity '&#914;&#959;&#942;&#952;&#949;&#953;&#945;' not defined
                  <para><guimenuitem>&#928;&#961;&#959;&#964;&#953;&#956;&#942;&#963;&#949;&#953;&#962;&&#914;&#959;&#942;&#952;&#949;&#953;&#945;;</gui
                                                                           ^

---

### Post by SunnyRabbiera on 2008-04-25
still could be related to the server overload though

---

### Post by ComputerExpertVK on 2008-04-25
are you sure...
because ///usr/share/gnome/help/blackjack/el/blackjack.xml:402: parser error : Entity '&#914;&#959;&#942;&#952;&#949;&#953;&#945;' not defined
<para><guimenuitem>&#928;&#961;&#959;&#964;&#953;&#956;&#942;&#963;&#949;&#953;&#962;&&#914;&#959;&#942;&#952;&#949;&#953;&#945;;</gui looks like something on the system

---

### Post by EarloftheWest on 2008-04-25
Choose a different repository. Go into Synaptic > Settings > Repositories 
then change your 'download from' location (select other) to someplace closer to your home.

I had the same problems you did until I switched my repository location.

---

