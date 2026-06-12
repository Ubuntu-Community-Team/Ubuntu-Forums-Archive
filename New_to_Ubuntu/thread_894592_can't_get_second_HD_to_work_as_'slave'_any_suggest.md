---
title: "can't get second HD to work as 'slave' any suggestions?"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by gusteman on 2008-08-19
Hi there, I recently mounted a second HD into my Dell Optiplex GX-1. The original HD having 3,7 Gigs and the second one 80 Gigs. Now I can find the icon of this second HD in the system files manager where it is named > hdb1.
I successfully mounted it using [COLOR="Red"]):P[/COLOR] but when I want to write to it I get told that this drive is > read-only.
Now I noticed that is is recognised as > hdb1 where it should in fact be > sdb0 if I'm not mistaking (or am I?:confused:). The jumpers on the two harddisks are set as they should be, namely primary hd on the initial HD and slave disk on the second one.
I have to add that for the time being my system is launched from the cd-rom drive *(Feisty Fawn CD)* because in regular boot-up it doesn't find the second hard drive, nor the second cd-rom drive from which it's operating now.
Probably I missed something along the way. Can anyone refer me to an earlier post where the solution may be found, or simply show me how to deal with this problem? :confused:
Many thanks in advance!!

---

### Post by fahadsadah on 2008-08-19
hdb1 DOES mean first partition of ide primary slave
There is no sdb0, but sdb1 would mean first partition of second sata, scsi or raid disk

---

