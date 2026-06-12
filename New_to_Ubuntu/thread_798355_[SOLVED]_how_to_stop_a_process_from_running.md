---
title: "[SOLVED] how to stop a process from running"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by paydaydaddy on 2008-05-18
Tried to install updates but the gui update manager just sits there with the little wheel spinning. How do I kill the process so I can start over?

---

### Post by TeoBigusGeekus on 2008-05-18
System->Administration->System Monitor
Tab processes, find the application and end/kill it.

---

### Post by kwacka on 2008-05-18
There's probably a way using a graphic interface, but I just use a terminal and type 
```
killall -9 application
```

If you are using an application like update-mamanger which uses root you wpould have to prefix with sudo, of course.

If you are unsure of the application name:
```
ps -A
kill PID
```

ps -A gives a list of running applications with their PID, the first number on the line, kill XXXX kills it

---

### Post by brujoand on 2008-05-18
Best way to kill an application _ever_ is:

alt + f2 --> gives you "run application" --> type "xkill" --> use the mouse and press whatever you want to kill. 

Works for almost everything and it's really fun to use :P

---

### Post by paydaydaddy on 2008-05-18
Thanks for the useful info. I like the xkill solution. Easy for my peabrain to remember.

---

### Post by markbuntu on 2008-05-18
How do you kill a process that locks up the keyboard and the mouse?
Is there some sort of watchdog I can get that times out misbehaving processes?

---

### Post by markbuntu on 2008-05-18
dp sorry!

---

