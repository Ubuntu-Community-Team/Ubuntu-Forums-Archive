---
title: "how to compile sourse code"
date: 2012-06-22
forum: New to Ubuntu
---

### Post by tahsin rahman on 2012-06-22
i have downloaded the sourse code of gnome-sudoku-0.7.1 . how can i compile it & play the game ?

---

### Post by tahsin rahman on 2012-06-22
i am new in linux . so tell me details .

---

### Post by steeldriver on 2012-06-22
you should look in the downloaded package for a README or some such file that gives specific instructions for that package

beyond that you can find general instructions for compiling programs in the following links

> **oldos2er said:**
> [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by chamber on 2012-06-22
```
tar zxvf package.tar.gz
cd package
make
sudo make install
./clean
```

---

### Post by CharlesA on 2012-06-22
There are sudoku games in the repos. Just do a search for sudoku in the software center.

That said, it is a newer version than the one you are trying to install:
gnome-sudoku 1:3.4.1-0ubuntu2

[http://apt.ubuntu.com/p/gnome-sudoku](http://apt.ubuntu.com/p/gnome-sudoku)

---

