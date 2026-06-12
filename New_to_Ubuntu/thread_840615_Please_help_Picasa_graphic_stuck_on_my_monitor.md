---
title: "Please help Picasa graphic stuck on my monitor"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by bmann11 on 2008-06-25
I just downloaded picasa, but when I opened it up, the graphic got stuck on my monitor.  It won't let any other page occupy that space, including this one.  Also, picasa won't close, and I don't know how to force quit.  Any help is greatly appreciated.

---

### Post by billgoldberg on 2008-06-25
Just restart x

"ctrl + alt + backspace "

---

### Post by Darkade on 2008-06-25
try opening a terminal and type
```
xkil picasa
```

If that doesn't work go to System>Administration>System Monitor, look for picasa and kill it from there

If you just can't use your desktop try CRT+ALT+F1 this will take you to a command inteface and then type
```
sudo halt
```
that will restart you computer

you can also just restart the x server like billgoldberg said

---

