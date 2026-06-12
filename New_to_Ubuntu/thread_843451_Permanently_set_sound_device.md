---
title: "Permanently set sound device"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by wrtpeeps on 2008-06-28
Xubuntu keeps using the wrong sound device on my system. It uses the onboard sound rather than the soundcard that has my speakers wired into it.

I couldn't find my onboard sound in the bios to disable it. Is there anyway to tell ubuntu to always use sound device #1 instead of #0?

---

### Post by Nexusx6 on 2008-06-28
What sound card do you have? Also, could you paste the result of 
```
cat /proc/asound/cards 

```
in a code block?

---

### Post by wrtpeeps on 2008-06-28
Never mind, got it sorted. 

Thanks anyway.

---

