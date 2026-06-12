---
title: "Codeblock"
date: 2017-12-16
forum: New to Ubuntu
---

### Post by iblueflash on 2017-12-16
hello,

can someone give to me the terminal comands for installing Codeblock on ubuntu ( I am running the last LTS version of ubuntu)

---

### Post by oldos2er on 2017-12-16
```
sudo apt update && sudo apt install codeblocks
```

---

### Post by iblueflash on 2017-12-16
thanks

(.text+0x20)||undefined reference to `main'|

I tried to copile a program in c++ and this is what a get(the probram was done on a pc with win10 , before i installed ubuntu)

---

### Post by spjackson on 2017-12-16
> **iblueflash said:**
> (.text+0x20)||undefined reference to `main'|
This means that your program does not define a main function. A definition of main is required for all C++ programs.

---

