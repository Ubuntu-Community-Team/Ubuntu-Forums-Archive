---
title: "Cannot Display Error"
date: 2006-02-23
forum: Packaging and Compiling Programs
---

### Post by Das Ein on 2006-02-23
Error:
[[IMG]http://img60.imageshack.us/img60/9874/screenshot6lz.th.png[/IMG]](http://img60.imageshack.us/my.php?image=screenshot6lz.png)

Program:
[[IMG]http://img60.imageshack.us/img60/5539/screenshot15ir.th.png[/IMG]](http://img60.imageshack.us/my.php?image=screenshot15ir.png)

---

### Post by gord on 2006-02-23
.o files are 'object' files, you don't run them.

you need to press the 'build' button, then an executionable file will be created with the same name as your project (by default)

---

### Post by Das Ein on 2006-02-23
Heh, I'm new to Ubuntu programing :r

Anyways now I see: [[IMG]http://img113.imageshack.us/img113/7789/screenshot25mj.th.png[/IMG]](http://img113.imageshack.us/my.php?image=screenshot25mj.png), but when I double click 'helloworld' nothing happens. Yet again sorry if I am missing something obvious.

---

### Post by gord on 2006-02-23
you need to run it from a console
make sure you are in your home directory (the one with the helloworld application)
```

./helloworld

```

---

### Post by Das Ein on 2006-02-23
Thank you very much. 

Another question: Is there a way I can make a 'launcher' for the program?

---

### Post by gord on 2006-02-23
im not sure what you meen by launcher. if you are looking for a quick way to run it from anjuta, just press F3. if you meen a desktop laucher (shortcut), just make one like normal but check the 'run in console' button

---

