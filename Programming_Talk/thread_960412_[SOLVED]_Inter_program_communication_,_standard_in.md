---
title: "[SOLVED] Inter program communication , standard input output"
date: 2008-10-27
forum: Programming Talk
---

### Post by jit.sd on 2008-10-27
Hey , 

Is there a way for two programs to communicate using standard input/output . for example if i am running two c++ programs and one program generates the input for the other program . What are the different ways they could communicate ? If program1 were to write something to standard output is it possible for program2 to read that ? 

I dont know the keyword to search for , and thus am pretty stuck . 

Can someone help out ? 

Thanks , 
Jit

---

### Post by geirha on 2008-10-27
Start them like this: ```
 ./prog1 | ./prog2 
``` Both programs will be run at the same time, and the output of prog1 is connected to the input of prog2

---

### Post by jit.sd on 2008-10-27
Brilliant , it works perfectly .

thank you so much :)

---

