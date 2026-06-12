---
title: "VNC gave me root"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by colofnature on 2008-09-25
So I VNC'd into the Ubuntu box from my mum's Vista machine, and the prompt said "root@..."etc I was only checking that I could get VNC to work, so IA quit before thinking to ask: was I really root? Does anyone know why this happened, and if it's anything to worry about?

---

### Post by ashmew2 on 2008-09-26
Normally , you should not be root....I dunno why it is happening..

I am sure you must have created an account on your ubuntu box ..Ill call it ***username***.

So when you see the root@machine prompt , simply do

```
sudo -i -u ***username***
```

I think it should fix up things for you!

---

