---
title: "Limewire blank beryl FIXED."
date: 2007-05-02
forum: Outdated Tutorials &amp; Tips
---

### Post by keagan on 2007-05-02
Hello
it is 3:20am in the morning finallly got the fix for the limewire/frostwire beryl blank hava crap

im new to linux (3 days actually) lol
im grasping pretty well condsidering im already posting tutes
so lets get down to buisness

Open terminal

type in

```
sudo gedit /usr/lib/LimeWire/runLime.sh
```

were assuming this is where you have runLime.sh if not correct so
also, you can use other editors, gedit is my favorite :D, (3 days and already got favorites *rolls eyes*)

ok so next
erase everything inside runLime.sh

and paste this

```
#!/bin/bash
java -jar LimeWire.jar
```

save it!

your done, how simple right?

if you on ubuntu goto, Aplications->Network->LimeWire

IT WORKS!
with beryl runnning of course :D

im figuring everyone knows how to do the same in frostwire :D
change a couple lines

hope this works for everyone like it did for me

---

### Post by julie_lebou on 2007-05-08
Hey! Well actually, I need help to do that with Frostwire... can you help me?

---

### Post by savagenator on 2007-05-08
> **julie_lebou said:**
> Hey! Well actually, I need help to do that with Frostwire... can you help me?

i agree, this has worked for limewire for me, but i need it more for frostwire.

---

### Post by savagenator on 2007-05-09
ok, well i tried it for frostwire, and unfortunately it does not start it at all, so i am at a loss of what to do....

---

### Post by cokehabit on 2007-05-15
doesn't fix it for me...

---

### Post by ljs662 on 2007-08-19
Thanks mate,
just a note, I didnt delete any of the other stuff which is in that file.

I just changed the first two lines to

#!/bin/bash
java -jar LimeWire.jar

Cheers

---

### Post by drutrax on 2007-12-06
How do i get it to work if im not using beyrl? im using compiz and i tried that code but it didnt work i still get a blank window......

---

### Post by ikt on 2007-12-13
I just installed Limewire, I am running 'extra visual effects' on and Limewire starts but it is blank.. can anyone help?

---

### Post by ikt on 2007-12-23
> **ikt said:**
> I just installed Limewire, I am running 'extra visual effects' on and Limewire starts but it is blank.. can anyone help?

Should be noted that the solution in the original post does not work.

---

