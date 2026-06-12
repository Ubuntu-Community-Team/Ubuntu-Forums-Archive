---
title: "linux-image-3.0.0-7 Borked Install?"
date: 2011-08-06
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by moore.bryan on 2011-08-06
When I upgraded this morning, installing linux-image-3.0.0-7 seemed to bork my install... can't log-in to Ubuntu with any of my other kernels, either, now. I tried purging it, but nothing... the Plymouth screen doesn't show and the text stops at 
```

Checking battery status                                    [ok]

```
and just hangs there. dmesg output is useless and shows no errors.

Any ideas?

---

### Post by dino99 on 2011-08-06
have got this issue too and i finally found that lightdm-gtk-greeter was not installed but lightdm-qt-greeter was, so i made the change, then i got the logging stuff as expected.

---

### Post by moore.bryan on 2011-08-06
Hmm... I though it interesting the upgrade removed lightdm-gtk-greeter, but thought that was part of the "bigger plan." ;-)

Let me see what I can do; thanks for the thoughts.

---

### Post by moore.bryan on 2011-08-06
That did it, thanks!

---

