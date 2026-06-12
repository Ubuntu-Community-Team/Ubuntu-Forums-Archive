---
title: "Help with a Script"
date: 2012-05-15
forum: New to Ubuntu
---

### Post by bikefreakvinnie on 2012-05-15
Hi everyone,

i just started experimenting with shell scripts and using the command line... 
I've realised that command line doesn't like spaces so i'm changing all my file replacing spaces with underscore with this script:

for files in *; do mv "$files" `echo $files | tr ' ' '_'`;done

its working fine but since my directories have very long names i want to avoid typing out each individual directory name...
So it'd be very useful if i could add a bit on the end of this script that would move to the next directory after its been done remaning the files. Failing that if i knew how to simply move to the next directory it'd be very useful...
thanks in advance

---

### Post by rai4shu2 on 2012-05-15
Have you looked into using rename?

```
rename 's/ /_/' *
```

---

### Post by Lisiano on 2012-05-15
It's way easier. Just type ```
rename 's/ /_/' */*
```The amount of *'s shows how deep to go. So say you start at ~/ and you put only * then it will only do files in ~/, put */* and it will do only files in ~/Folder/ ~/Folder2/ etc. */*/* ~/Folder/AnotherOne/ ~/Folder2/Stuffs/

EDIT: Darn rai4shu2, ninjad me while I was typing.

---

### Post by bikefreakvinnie on 2012-05-15
thanks a mil for that -much easier!

---

### Post by codingman on 2012-05-15
please set this as solved!

---

