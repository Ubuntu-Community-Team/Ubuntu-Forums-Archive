---
title: "[SOLVED] Conky help"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by Inxsible on 2008-06-14
I lose all my desktop icons whenever I start conky on my Debian + Xfce setup.

Can someone tell me if there is a key/value pair or setting in conkyrc that will enable me to keep the desktop icons even when conky is running?

---

### Post by cheesypoof on 2008-06-14
Try this command.

own_window yes

---

### Post by iaculallad on 2008-06-14
> **Inxsible said:**
> I lose all my desktop icons whenever I start conky on my Debian + Xfce setup.

Can someone tell me if there is a key/value pair or setting in conkyrc that will enable me to keep the desktop icons even when conky is running?

Try this: In your conkyrc file

> own_window yes
own_window_type desktop
double_buffer yes
own_window yes


-Other values for own_window_type could also be 'normal' or 'override'

---

### Post by Inxsible on 2008-06-14
> **cheesypoof said:**
> Try this command.

own_window yesworked like a charm. Thanks !!

---

