---
title: "missing cc1obj"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by zman0 on 2008-06-13
It has been a few years since I have worked on a linux system, and I just built my very own box to play around with.

I have Ubuntu 8.04 installed, and when trying to make a file, I get the following:

gcc: error trying to exec 'cc1obj': execvp: No such file or directory

Does anyone know of a (fairly) simple fix for this?  My linux knowledge is fairly limited, so please bear with me :)

---

### Post by pedro_orange on 2008-06-13
cc1obj is the Objective C compiler I think.

Try installing either gobjc++ or gobjc

```
sudo apt-get install gobjc++
```

---

### Post by zman0 on 2008-06-13
That seems to have done it, thanks

---

