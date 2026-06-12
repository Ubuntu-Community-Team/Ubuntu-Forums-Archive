---
title: "[SOLVED] xubuntu 8.10 buggy installation"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by jlbr21 on 2008-11-23
hi, i installed xubuntu in an old laptop, but it has not turned  out very well, it has been very buggy, it has given me many problems and some have been fixed by updated, others persist, for example, it doesnt recognize caps lock key, so i can write in capital letters, and another issue is the fact i cant install the gstreamer codecs for wav, web streaming, etc. i keep getting the message quoted below.

anybody else having similar issues, should i reinstall, would that help at all 'sorry, can't write question marks'


> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


---

### Post by Michael.Godawski on 2008-11-23
What happens if you run this command as suggested in the message:

```
sudo dpkg --configure -a
```The error message you get is often connected with an interrupted update process or install process during the updates.

---

### Post by jlbr21 on 2008-11-23
Hi Michael, I just went ahead and made another LiveCD and reinstalled, it seems to be working fine now, seems it was just a faulty installation disc.

---

### Post by Michael.Godawski on 2008-11-23
Glad to hear everything is working now:).

---

