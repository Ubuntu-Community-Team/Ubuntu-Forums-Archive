---
title: "Qt"
date: 2010-04-11
forum: Programming Talk
---

### Post by manojboopathi on 2010-04-11
i am developing an app. like system restore in ubuntu using QT.
 
while doing restoration i need some idea that stops user from closing the program.
 
for example when a program is being executed in terminal it can be stopped by ctrl+ z
 
i want some means that restricts user from stopping the program...
 
waiting 4 reply.....

---

### Post by Slim Odds on 2010-04-11
> **manojboopathi said:**
> i am developing an app. like system restore in ubuntu using QT.
 
while doing restoration i need some idea that stops user from closing the program.
 
for example when a program is being executed in terminal it can be stopped by ctrl+ z
 
i want some means that restricts user from stopping the program...
 
waiting 4 reply.....

fork the important stuff and run it in the background, not in the GUI thread

---

### Post by vijushimpi on 2010-04-11
while chosen for exit or quickquit program may emit a signal, catch it in program connect it to a dialog , saying something in process.

---

