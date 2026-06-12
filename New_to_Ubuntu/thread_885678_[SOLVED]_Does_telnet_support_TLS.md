---
title: "[SOLVED] Does telnet support TLS?"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by Sydius on 2008-08-10
Does the telnet program that comes default with Ubuntu support TLS? I read the man page, but didn't see anything about it, other than the section on encryption (is that TLS related?).

If so, how do you enable it?

---

### Post by brian_p on 2008-08-11
> **Sydius said:**
> Does the telnet program that comes default with Ubuntu support TLS? 

Maybe there is some help here:

```
apt-cache search telnet ssl

```

---

### Post by Sydius on 2008-08-11
Ah, thank you.  I suppose the answer is that no, the default telnet does not, but that there is another implementation available (telnet-ssl) that does.

---

