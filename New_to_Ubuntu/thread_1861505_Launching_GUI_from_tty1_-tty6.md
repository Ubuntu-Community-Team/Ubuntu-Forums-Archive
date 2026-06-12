---
title: "Launching GUI from tty1 -tty6"
date: 2011-10-15
forum: New to Ubuntu
---

### Post by LinTux on 2011-10-15
I Know this is probably a stupid question, but is it possible to launch a window manager(like dwm or wmii or enlightment) from tty1-6 (launched from CTRL-ALT-F(1-6)?

---

### Post by wildmanne39 on 2011-10-15
Hi, whatever desktop environment that is installed will load if you hit f7.
Thank you

---

### Post by LinTux on 2011-10-15
I know, but can you somehow load it from CTRL-ALT-F1

---

### Post by wildmanne39 on 2011-10-15
Hi, I am sorry I do not know that, I thought the answer I gave would fix your problem, I did not realize you wanted to customize your keys for some reason.
Thank you

---

### Post by Hairy_Palms on 2011-10-15
you can yes, but you must redirect to the active screen, for example with metacity its

```
metacity --replace -d :0
```

assuming its screen 0 that you want if not just use :1 or :2 etc

---

