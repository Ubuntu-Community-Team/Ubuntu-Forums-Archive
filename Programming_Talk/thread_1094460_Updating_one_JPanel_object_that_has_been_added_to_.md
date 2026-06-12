---
title: "Updating one JPanel object that has been added to two JFrames"
date: 2009-03-12
forum: Programming Talk
---

### Post by C-- on 2009-03-12
How come when a add a single JPanel object to two different JFrame objects and then change a JLabel inside that JPanel, it only updates for the last JFrame I added the panel to?

---

### Post by Psicolonia on 2009-03-12
u have to call repaint() on both jframes. it'll work ;)

---

### Post by C-- on 2009-03-13
> **Psicolonia said:**
> u have to call repaint() on both jframes. it'll work ;)

I tried calling repaint, but the first JFrame's panel is still disappearing.

---

### Post by issih on 2009-03-13
Probably won't help but try calling "revalidate", that often sorts out gui glitches in swing for me.

---

### Post by C-- on 2009-03-13
> **issih said:**
> Probably won't help but try calling "revalidate", that often sorts out gui glitches in swing for me.

Unfortunately calling the validate method on the panel or the window does not fix the issue: the panel is still being displayed on only one window.

Thanks for your help so far.

---

