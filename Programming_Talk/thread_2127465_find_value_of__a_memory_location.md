---
title: "find value of  a memory location"
date: 2013-03-20
forum: Programming Talk
---

### Post by ankt90138 on 2013-03-20
hello sir;

i just wanna know in this command

 sudo setpci -s 00:02.0 F4.B=40

if i want to read value of location (00:02.0 F4.B)before assigning a new value..

How could i do this??

---

### Post by spjackson on 2013-03-20
man setpci
> 
There  are  two kinds of operations: reads and writes. To read a regis&#8208;
ter, just specify its name. Writes have  the  form  name=value...


---

### Post by ankt90138 on 2013-03-21
doesnt help much..

---

### Post by spjackson on 2013-03-21
The man page for setpci tells you that if the command to change a value to 40 is
```

sudo setpci -s 00:02.0 F4.B=40

```
Then the command to read the current value is
```

sudo setpci -s 00:02.0 F4.B

```
If this "doesn't help much" then you will need to explain more clearly what you want to do.

---

### Post by conradin on 2013-03-21
lol I found the man page to not be too easy to read. searching "/read" in vim gave me nothing useful. 
Anyhow i found this thread helpful!

---

