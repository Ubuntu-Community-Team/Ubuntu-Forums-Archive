---
title: "help need to understand command..."
date: 2012-02-16
forum: New to Ubuntu
---

### Post by jpjohnj on 2012-02-16
hi,

consider this 

d=`expr "${d?'not defined'}" + 1`


and 

d=`expr $d + 1`

where 

 * d will not defined.

here initially d doesn't have any value.so 
d=`expr $d + 1` should fail but i got 1 in the d variable.


please explain me how these two variable assignment are working

---

### Post by Zill on 2012-02-16
> **jpjohnj said:**
> ...please explain me how these two variable assignment are working
Homework question?

---

### Post by jpjohnj on 2012-02-16
now i am start learning shell script.these are all the doubt ...

---

### Post by lechien73 on 2012-02-16
No, $d shouldn't fail. You don't need to declare or initialise your variables before using them in BASH scripting (although it's good practice to do so), and by default, if no specifications are given, a variable can hold any type of data.

When an integer value is passed to $d, then BASH treats $d as an integer variable, initialised at 0. So the arithmetic operation + 1 works.

---

