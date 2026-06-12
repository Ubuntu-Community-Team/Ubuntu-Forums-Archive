---
title: "[SOLVED] sound problem"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by pasargad on 2008-06-13
hello there
i have a inboard sound card,so when i play a music i hear the voice from speakers(creative sound system) and tower,how can i disable the tower sound?

---

### Post by k33bz on 2008-06-13
I personally never heard of that problem before, but you might want to try and use the alsa-mixer
just go into the terminal and type alsa-mixer, play with some of the variables there, and see if that corrects your problem.

---

### Post by pasargad on 2008-06-13
> **k33bz said:**
> I personally never heard of that problem before, but you might want to try and use the alsa-mixer
just go into the terminal and type alsa-mixer, play with some of the variables there, and see if that corrects your problem.

```
bash: alsa-mixer: command not found

```

---

### Post by _sphinx_ on 2008-06-13
May be it's ```

alsamixer

```

---

### Post by pasargad on 2008-06-13
solved,thanks a lot.
i change the 100 value for "MASTER M" in presences to 0:)

---

### Post by k33bz on 2008-06-13
> **_sphinx_ said:**
> May be it's ```

alsamixer

```
yes, thats what it is, sorry bout that.

---

