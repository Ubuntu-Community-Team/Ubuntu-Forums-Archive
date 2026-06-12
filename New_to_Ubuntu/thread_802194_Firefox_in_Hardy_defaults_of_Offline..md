---
title: "Firefox in Hardy defaults of Offline."
date: 2008-05-21
forum: New to Ubuntu
---

### Post by paddyboy on 2008-05-21
Every time I fire up Firefox it comes up with "Work Offline" enabled (Under the file option). Is there a conf file somewhere that needs looking at ?

Thanks.
pb

---

### Post by Calash on 2008-05-21
I found this while searching

[http://ubuntuforums.org/showthread.php?t=789463&highlight=Firefox+Offline](http://ubuntuforums.org/showthread.php?t=789463&highlight=Firefox+Offline)

The issue is related to the network-manager.  I managed to resolve my problems by adjusting the settings a bit, but I am running a bridged interface so the instructions may be of little use to you.

Search for Firefox Offline and you will find more information.

---

### Post by paddyboy on 2008-05-23
Thanks Calash that was a really useful link. 

Just for anyone else I fixed it by:

In Firefox go into Tools>Addons>Extensions then disable Ubuntu firefox modifications. 
Restart firefox (this fix courtesy of blakegrover).

Cheers,
pb

---

