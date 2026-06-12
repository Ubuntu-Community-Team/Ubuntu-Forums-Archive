---
title: "problem with gdm"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by ET! on 2008-06-13
i accidentally switched off the graphical login manager in the services. now linux is booting in command prompt. what can i do to get the gui back.....thanks to everyone who answers

---

### Post by iaculallad on 2008-06-13
> **ET! said:**
> i accidentally switched off the graphical login manager in the services. now linux is booting in command prompt. what can i do to get the gui back.....thanks to everyone who answers

Login with your credentials when on the terminal prompt. Then issue startx to get back to your GUI, turn on the graphical login manager afterwards.

```
startx
```

---

### Post by _sphinx_ on 2008-06-13
OR you can also do simply
```

sudo gdm

```
on the place mentioned by "iaculallad"

---

