---
title: "how to remove upgrade manager icon"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by faust99 on 2008-04-22
I just downgraded Audacity to version 1.3.3 because I couldn't get the upgraded version to playback. Now I have the orange update icon/applet constantly informing me of an upgrade I don't want. Could anyone suggest how to get rid of it?? :confused:

---

### Post by SOULRiDER on 2008-04-22
That will notify you of updates, since you downgraded a pckage its waiting to be upgraded. Aptitude is a package manager though, what was it bothering you with exactly?

You can use **hold,** that could help you hide those unwanted updates. To hold a package open a terminal and type:
```
sudo aptitude hold <package-name>
```
replacing <package-name> with the package's name.

---

### Post by faust99 on 2008-04-22
> **SOULRiDER said:**
> That will notify you of updates, since you downgraded a pckage its waiting to be upgraded. Aptitude is a package manager though, what was it bothering you with exactly?

Oops, sorry that was a typo. I mean to write 'Audacity', not 'Aptitude' 

> **SOULRiDER said:**
>  You can use **hold,** that could help you hide those unwanted updates. To hold a package open a terminal and type:
```
sudo aptitude hold <package-name>
```
replacing <package-name> with the package's name.

Thank you; will give it a go.

---

### Post by SOULRiDER on 2008-04-22
I hope it works. Theres probably a solution other than just hiding the icon. Hiding the icon will not only not tell you when there are upgrades, but if you ever happent o upgrade your system, audacity will be upgraded again and you will have to downgrade it once more.

---

### Post by faust99 on 2008-04-22
I've put it on hold through aptitude but the icon is still there...

                               BUT...

locking the package through synaptic has seemingly removed the update icon...

---

