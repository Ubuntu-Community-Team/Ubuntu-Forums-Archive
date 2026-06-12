---
title: "javascript question"
date: 2009-03-17
forum: Programming Talk
---

### Post by tc101 on 2009-03-17
Suppose I have a function like this which calls a second function:
 
function Fun_1()
{
       Fun_2();
    }
 
How can I code this so I can pass the name of the second function

Fun_1(“Fun_2”)

function Fun_1(Fname)
{
      How do I call Fname here?
    }

---

### Post by Tibuda on 2009-03-17
You can define functions as variables.

```
var fun2 = function() {
  // Whatever
}

function fun1(f) {
  f();
}

fun1(fun2);
```

---

### Post by tenmilez on 2009-03-17
You could use the eval function. 

* not tested *

```

f1("f_2");

function f1(f2) {
   eval(f2 + "()");  
}

function f_2() {
// stuff
}

```

---

### Post by simeon87 on 2009-03-17
> **tenmilez said:**
> You could use the eval function.

Eval shouldn't be used when it's not needed.

---

### Post by soltanis on 2009-03-17
Store the function as a variable and pass the variable to the function, like in the first response.

---

### Post by tc101 on 2009-03-17
Thanks !

---

### Post by Reiger on 2009-03-18
You can tweak the store-as-a-variable behaviour a little:
```

function f1 () {
}

function f2 (funct) {
}

var fvar = f1;
f2(fvar);

```

---

