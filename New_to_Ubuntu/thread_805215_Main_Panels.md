---
title: "Main Panels"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by vettexl on 2008-05-23
Hi, I started using Ubuntu about a month and a half ago. The main panels at the bottom 
and the top have suddenly disappeared, they have never dont that before. Is there anything I can do to get them back?

Thanks in advance

---

### Post by PinkFloyd102489 on 2008-05-23
Hit Alt+F2 and enter gnome-panel.

---

### Post by vettexl on 2008-05-23
I have tried that multiple times and nothing comes up. :(

---

### Post by PinkFloyd102489 on 2008-05-23
Drop to a console by pressing Ctrl+Alt+F1, log in, then enter the following:

```

export DISPLAY=:0 && gnome-panel

```

Then press Ctrl+Alt+F7 to get back to the GUI.

---

### Post by vettexl on 2008-05-23
Ok, thanks, this worked. :) Thank you for helping out.

---

