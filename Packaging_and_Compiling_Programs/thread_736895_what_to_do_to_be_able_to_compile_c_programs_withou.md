---
title: "what to do to be able to compile c programs without internet connection"
date: 2008-03-27
forum: Packaging and Compiling Programs
---

### Post by seleciii44 on 2008-03-27
hi, I am new in ubuntu and i have to write a c program related with threads. But i couldn't compile the code. I don't know what to do and i don't have much time left. My wireless connection doesn't work in ubuntu because it has no driver. Please help me to fix it.:confused::confused:

---

### Post by lloyd_b on 2008-03-27
> **seleciii44 said:**
> hi, I am new in ubuntu and i have to write a c program related with threads. But i couldn't compile the code. I don't know what to do and i don't have much time left. My wireless connection doesn't work in ubuntu because it has no driver. Please help me to fix it.:confused::confused:

Put the installation CD in the drive, and in a terminal type:
```
sudo apt-get install build-essential
```

Unless you've modified the "/etc/apt/sources.list" file, it should fetch the necessary files from the CD.

Lloyd B.

---

### Post by seleciii44 on 2008-03-28
thanks a lot. I can compile it now...

---

