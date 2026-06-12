---
title: "Is this within normal range?"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by skymera on 2008-05-14
Hi i just checked my laptop Load_Cycle_Count and i can't tell if the result is normal or not :???

here is the output of the terminal

```
 scott@cott-laptop:~$ sudo smartctl -a /dev/hda | grep Load_Cycle_Count
193 Load_Cycle_Count 0x0032  060  060  000 Old_age Always -
         80201 
```

Normal? or worrying?

---

### Post by Kevbert on 2008-05-14
Hi.  This article might help: [http://ubuntuforums.org/showthread.php?t=591503&highlight]("http://ubuntuforums.org/showthread.php?t=591503&highlight")

---

### Post by Nepherte on 2008-05-14
There's no need to worry with a load cycle of 80.000

---

### Post by skymera on 2008-05-14
o 80:P
I assumed it was 80,000 :lol:

Thanks for link too Kevbert

---

