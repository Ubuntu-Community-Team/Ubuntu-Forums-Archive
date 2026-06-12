---
title: "blank alsa mixer"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by tonymoloney on 2008-07-13
I installed alsa mixer using the synaptic package manager and when I run it, all I get is a blank screen? What's happening?

---

### Post by ChameleonDave on 2008-07-13
> **tonymoloney said:**
> I installed alsa mixer using the synaptic package manager and when I run it, all I get is a blank screen? What's happening?
Try running it with "-s":

```

alsamixer -s

```

To exit, press Esc.

Does it work?

---

### Post by Bubba64 on 2008-07-13
If the last post doesn't work install it from add remove there are probably multiple dependencies. Gnome alsa mixer search with alsa and have the show be all available packages.

---

### Post by tonymoloney on 2008-07-15
Soory guys about the late response. I got called away and then forgot I had made a post!
I tried alsamixer -s and it did indeed give me a graphical screen, but not what i was looking for. Maybe I'm using the wrong package.
i am trying to get a GUI that shows all my audio inputs/outputs with controls over them. I thought I had seen it before in alsamixer but it looks like I was wrong.
can you steer me in the right direction?

---

