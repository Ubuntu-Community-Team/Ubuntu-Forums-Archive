---
title: "Key-mon not working in ubuntu 12.10"
date: 2013-01-14
forum: New to Ubuntu
---

### Post by anandharaja on 2013-01-14
hi
i want to install key-mon but none of the version not working for me, i tried the version in software center and latest one 1.15 none of them not opening please help me to install the latest version 1.15

Thankyou

---

### Post by Kevin McCready on 2013-01-14
Is screenkey worth trying?

---

### Post by anandharaja on 2013-01-14
> **Kevin McCready said:**
> Is screenkey worth trying?

Yes. why not opening?

---

### Post by anandharaja on 2013-01-14
open in terminal i got the following error

Traceback (most recent call last):
  File "/usr/bin/key-mon", line 3, in <module>
    km.main()
  File "/usr/lib/pymodules/python2.7/keymon/key_mon.py", line 1032, in main
    keymon = KeyMon(opts)
  File "/usr/lib/pymodules/python2.7/keymon/key_mon.py", line 123, in __init__
    self.enabled = dict([(img, self.get_option(cstrf(img.lower))) for img in self.IMAGES])
  File "/usr/lib/pymodules/python2.7/keymon/key_mon.py", line 80, in cstrf
    locale.setlocale(locale.LC_CTYPE, OLD_CTYPE)
  File "/usr/lib/python2.7/locale.py", line 547, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting


what can i do now?

---

### Post by anandharaja on 2013-01-16
No one is using key-mon, help please.

---

