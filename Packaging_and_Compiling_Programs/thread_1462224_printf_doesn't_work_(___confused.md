---
title: "printf doesn't work :(   *confused*"
date: 2010-04-25
forum: Packaging and Compiling Programs
---

### Post by snoozy23 on 2010-04-25
Hi guys,
Just tried to make a little c program:
```

#include  <stdio.h>
int main(){
printf("Hello World!\n");
}

```
I compiled it with gcc:
gcc -o test test.c

but it does nothing :(

then i tried other names:
hello ==> command not found

and xyz was the same

thanks for reading

---

### Post by Jordanwb on 2010-04-25
Sorry but it works for me.

---

### Post by diesch on 2010-04-25
bash doesn't look in the current working folder for a program to run so you need to call it with the path prepended, like *./hello* or *./test*  (*./* always means the current working folder).

In your first case to bash buldin *test* is called which doesn't do anything if called without options.

---

### Post by snoozy23 on 2010-04-25
:-\" oh, i remeber :D

thank you, know it works :guitar:

---

