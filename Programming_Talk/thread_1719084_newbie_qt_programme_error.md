---
title: "newbie qt programme error"
date: 2011-04-01
forum: Programming Talk
---

### Post by Praveen30 on 2011-04-01
i am new in qt programming.i have downloaded qt4 now i am trying to run a simple "hello world" application.after making the .cpp files i put it inside the home folder.now i go to my terminal and type this-

qmake -project
 
on typing this it just comes to next line and keeps on blinking....and nothing comes...plz tell me why it is happening???is there specific location where i have to put this .cpp file???

---

### Post by bdfhjk on 2011-04-01
Remember, that You should have a .pro file in directory. qmake work only after create it. 

The best way to do this (especially for beginner) is create a project in any IDE. I recommend QTCreator for start. 

If You want to create a one file qt program, you don't have to use qmake.

---

