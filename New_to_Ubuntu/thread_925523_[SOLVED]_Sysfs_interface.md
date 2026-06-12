---
title: "[SOLVED] Sysfs interface??"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by Khalis7 on 2008-09-20
Greetings to everyone.

I'm not sure if this is the right section to ask question. But anyway today I had installed iwl3945 driver patch in order to use aircrack-ng which I compiled the source code and installed it. But I encountered problem when trying to run ```
sudo airmon-ng start wlan0
``` which it spits out this
```
Interface	Chipset		Driver

wlan0		Intel 3945 a/b/g	iwl3945 - [phy0]

ERROR: Neither the sysfs interface links nor the iw command is available.
Please download and install iw from http://dl.aircrack-ng.org/iw.tar.bz2
```

Then, I make my way download the iw.tar.bz2 file and now I don't have any idea on how to make use of this file. :confused:
Can someone please give me instruction on this matter? Any help would be really great for me.

---

### Post by Khalis7 on 2008-09-20
Funny though, finally I figured out the problem myself. Did some google-ing a bit and found the solution:
[HTML]http://www.aircrack-ng.org/doku.php?id=mac80211&DokuWiki=afca843b5c58a99930406b7aa45e2dd2[/HTML]

---

