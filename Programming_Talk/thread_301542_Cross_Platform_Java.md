---
title: "Cross Platform Java"
date: 2006-11-17
forum: Programming Talk
---

### Post by Paul41 on 2006-11-17
I have a client that has asked me to write a desktop application for them that they want to run on Windows. I was thinking about doing this with Java since they say you can "write once run anywhere", but I have also heard "write one debug everywhere".

In you experience which of these is true. I don't want to have to use Windows just to write this for them. I normally do web applications so this isn't usually a problem for me.

---

### Post by Engnome on 2006-11-17
> **Paul41 said:**
> I have also heard "write one debug everywhere".


Write it once (on your platform of choice) and then try it on windows. Thats what it's saying so maybe you should try it. I would try it on windows if I wanted to make sure it worked for windows even if I believed in "write once run anywhere" There are exceptions though, if you are doing something very windows specific you might want to develop it in windows :) 

Disclaimer: I'm not very experienced in java portability issues, only developed in linux for linux.

---

### Post by Tomosaur on 2006-11-17
Write once, run anywhere is pretty accurate provided your code is tight.

---

### Post by amo-ej1 on 2006-11-20
Indeed but it would be my suggestion to keep a windows machine at hand to continuously see how the application behaves there at all time. That will probably save you some time in the end. Typical things that can differ can be  window placement, handling certain gui events which are thrown at different events and things like that.

---

### Post by Paul41 on 2006-11-20
Thanks everyone. I will give it a try and see what happens.

---

