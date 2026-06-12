---
title: "sound problems in ubuntu 8.04"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by santhust on 2008-10-22
hi. i am having very low (inaudible) sound while operating ubuntu. however when i use vista, the sound there is fine. i have tried pulling up all the sound levels but it hasn't worked. i have also searched through the threads, other persons having the same problem haven't been able to fix it. is there any solution that exist for this? please help

---

### Post by SteveNorman on 2008-10-22
did you try alsamixer?

open a consol and at the command prompt type

```
$ alsamixer
```

looks like you may have already tried this

---

### Post by Orange_and_Green on 2008-10-22
+1 SteveNorman's suggestion.

Also, try unmuting all channels (helps in some cases), or maybe muting the ones to the far right (on my laptop for example, the sound is inaudible as well unless I mute the "external amplifier" channel).

Good luck :KS

---

### Post by Duck2006 on 2008-10-22
What sound card are you using?

---

### Post by santhust on 2008-10-24
hi steve norman. it has worked.the alsamixer worked! thanks!

---

### Post by SteveNorman on 2008-10-27
sweet!

---

