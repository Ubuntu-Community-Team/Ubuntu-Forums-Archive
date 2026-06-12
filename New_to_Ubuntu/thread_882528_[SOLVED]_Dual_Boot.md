---
title: "[SOLVED] Dual Boot"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by gunner ra on 2008-08-07
Hi Guys I have Ubuntu and Vista in an dual boot and they are working great. However being new to Ubuntu I installed Vista on an 2nd hard drive for insurance,that I would still be able to access my computer in the case of an failure. My question is: the boot loader shows Ubuntu... Longhorn 1... longhorn 2 ...If I format my second drive in windows disk manager, would I have to delete references to Vista 2 in Grub/ Menu/ List: or would it just disappear automatically from the start up boot menu? I hope this post makes sense. Ps Please how do I add resolved to my posts. Many Thanks for the help you have already afforded me. Gunner

---

### Post by jmd9qs on 2008-08-07
not sure what you mean by your first question, bud... but you can mark your thread as solved by using the "thread tools" link

---

### Post by zvacet on 2008-08-07
If I understand you properly you have two Vista install and you want to remove one of them (one on second HD).

> .If I format my second drive in windows disk manager, would I have to delete references to Vista 2 in Grub/ Menu/ List

If doesn´t disappear edit menu list and delete it from there.

```
gksudo gedit /boot/grub/menu.lst
```

and you will probably find entries for your second Vista looking like this

title        Vista
root (hd1,0)

or something similar,but it will show you that Vista is installed on second HD.

---

### Post by gunner ra on 2008-08-07
Thanks Guys jmd9qs I did not think my post was too clear lol, however zvacet managed to decipher it lol  Thanks that is exactly what I meant Gunner:)

---

