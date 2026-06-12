---
title: "output of a commend in a veriable ???"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by just_linux on 2008-08-10
Ok :popcorn:
here is the issue : I wrote a program and I want inside of the program check if a file called "ADDRESS" has any line or it is empty and if it is, do something ...

I know I might need to use wc -l Adrress or something But I do not know how should I put it in a variable like $output? or how can I just get the number instead of number   address?


how can I put 
output= wc -l address? and how can I just get the number?:lolflag:
Please help :guitar:

---

### Post by scorp123 on 2008-08-10
```
export VARIABLE=`wc -l file_to_be_counted.txt | awk '{ print $1 }'`
``` ```
> echo $VARIABLE
567
```


Voila :)

---

### Post by lisati on 2008-08-10
Some versions of C have a function to set environment variables. If memory serves correctly, it's usually called something like setenviron()
The corresponding function to read the variable is getenviron()

---

