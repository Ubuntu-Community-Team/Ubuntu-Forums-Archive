---
title: "wireless driver recognition"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by tachyon4 on 2008-09-17
Hello, complete Ubuntu beginner here!  I'm looking forward to switching from Vista to Hardy, but I can't get my internet to "work."  Perhaps someone can walk me through...

My card/driver does not appear in the Network Manager.  I can enter my SSID and WEP, but the internet does not connect.  I have Broadcom 802.11a/b/g WLAN and BCMWL6.SYS.  Everything works on Vista.  I'm dual-booting two the OS's.

What other info do I need?  What can I try?

Thank a bunch!

---

### Post by S15_88 on 2008-09-18
look in the ubuntu help section to see if your card is supported, if it is and it's not working perhaps you need to go to: system>administration>restricted drivers

if nothing seems to work you may need to use ndiswrapper it uses the windows driver .inf file, i have used it in the past and it has worked well.
search google or this forum for ndiswrapper and you will most likely find a few how to's.

post back with your results!

Alain

---

### Post by rlzyoner on 2008-09-18
You can load the windows .inf file into ndiswrapper withe the following command

sudo ndiswrapper -i /path/to/inf/file

---

### Post by tachyon4 on 2008-09-18
thanks for the tips.

i had some problems with ndiswrapper but i manually edited blacklist with gksudo nautilus.  i'm 95% sure i did it correctly.

i rebooted.  the network icon indicates that ubuntu recognized my hardware.  but the network settings have changed from before.  "wireless networks" is no longer in the list of connections and i can't change preferences.  i'm not connected.

i think i'm almost there, but i need help finishing this off.  i'll google around and try to figure this out.  i'll post back if i find anything.  until then, i'd appreciate some more help.

i may try rlzyoner's technique in the meantime.

thanks again!

---

### Post by tachyon4 on 2008-09-20
problem solved

[http://ubuntuforums.org/showthread.php?p=5827892&posted=1#post5827892](http://ubuntuforums.org/showthread.php?p=5827892&posted=1#post5827892)

---

