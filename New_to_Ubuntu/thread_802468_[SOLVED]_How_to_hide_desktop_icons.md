---
title: "[SOLVED] How to hide desktop icons?"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by AstralliS on 2008-05-21
Is there any way to hide desktop icons on Ubuntu?

---

### Post by fredfjr on 2008-05-21
> **AstralliS said:**
> Is there any way to hide desktop icons on Ubuntu?

I found a thread where someone had their icons disappear and they want them back, but the replies point to some ways you might go about hiding your desktop icons...

[http://ubuntuforums.org/showthread.php?t=762902&highlight=hide+desktop+icons]("http://ubuntuforums.org/showthread.php?t=762902&highlight=hide+desktop+icons")

---

### Post by nick_h on 2008-05-21
Run:
```
gconf-editor
```
and look under apps/nautilus/desktop

---

### Post by AstralliS on 2008-05-21
Nothing of that didn't help.

---

### Post by mick8985 on 2008-05-21
Astrallis Nick is right thats exactly how you do it, if you still have Icons on you desktop after unticking everything in gconf-editor, its because you put the icons there yourself, which is easily solved by moving those files

---

### Post by AstralliS on 2008-05-21
Okeydoke. I solved this. :D

Thanks.

---

### Post by anotherdisciple on 2008-05-21
Be sure to mark your thread as solved and thank the guys who helped you... just a friendly reminder :)

---

### Post by AstralliS on 2008-05-21
Ok. Done. :D

---

