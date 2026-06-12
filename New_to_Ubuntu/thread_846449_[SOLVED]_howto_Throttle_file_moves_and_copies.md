---
title: "[SOLVED] howto Throttle file moves and copies"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by timandjulz on 2008-07-01
Everytime I move or copy files my system slows to a snails pace.  I have a quadcore CPU, 8GB memory and a 1TB SATA drive.  Obviously this is a problem with IO bus contention.

I want to move GB files around without hanging my system.  Does anyone know how to do this?

Thanks,
Tim

---

### Post by milosz.galazka on 2008-07-01
Maybe *ionice* command will help you...

---

### Post by shad0w_walker on 2008-07-01
As much as you shouldn't need to in this day and age, have you checked that DMA is enabled? It might simply be disabled and tying up the processor with transfering stuff when it should just be sat quietly in the background.

---

### Post by timandjulz on 2008-07-02
> **milosz.galazka said:**
> Maybe *ionice* command will help you...

This looks the most likely.  I have played with NCQ and other settings you can play with through /proc.  They don't seem to make much of a difference.  Will try ionice.

Thanks milosz.galazka!

---

### Post by timandjulz on 2008-07-02
Tested.  ionice is the answer and milosz.galazka rocks!

Example console:

```
tim@office:~/tmpsdi4$ cp -r -p largefolder ../targetfolder/ &
[1] 17384
tim@office:~/tmpsdi4$ sudo ionice -c 3 -p 17384
tim@office:~/tmpsdi4$ 

```

Note that adding "&" to the end of the cp command caused the process to run in the background and print the process ID.  In this case the pid is 17384.

Cheers,
Tim

---

