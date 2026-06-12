---
title: "Can't shutdown laptop?"
date: 2015-10-23
forum: New to Ubuntu
---

### Post by c1529g on 2015-10-23
I am running Ubuntu-14.04 MATE LTS on an ACER ASPIRE laptop and i am very happy with the OS. But for some reason when i tried to shutdown the machine it reboots within a few seconds and i'm back where i originally started. I did do a Google search on the subject and tried openning the terminal and typing: ```
 sudo shutdown -h now 
``` and, also, ```
 sudo poweroff 
``` but neither worked. The only way i can close the machine down is by holding down the power button and even a noob like myself knows that's wrong. I hope someone can help?

---

### Post by vasa1 on 2015-10-23
Is it possible that you deleted some software? You have another thread in which you mention removing unnecessary packages. Maybe something critical was inadvertently deleted?

---

### Post by c1529g on 2015-10-23
hi vasa1
 i'm lost. Ain't got a clue?

---

### Post by QIII on 2015-10-23
Hello!

The question asked by vasa1 was diagnostic and referred to [http://ubuntuforums.org/showthread.php?t=2299814](http://ubuntuforums.org/showthread.php?t=2299814)

If you uninstalled things inadvertantly, knowing that might lead to a resolution.  Without information, we can only guess at possible answers.

---

### Post by howefield on 2015-10-23
> **c1529g said:**
> i'm lost. Ain't got a clue?

If you aren't sure which packages you uninstalled, you might get a clue in the following logs..

```
/var/log/history.log
```
```
/var/log/term.log
```

---

