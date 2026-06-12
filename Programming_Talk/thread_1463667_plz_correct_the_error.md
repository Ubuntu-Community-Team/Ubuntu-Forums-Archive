---
title: "plz correct the error"
date: 2010-04-27
forum: Programming Talk
---

### Post by smartlogicsseo on 2010-04-27
#! /bin/bash
if [ $# -eq 0 && $# -gt 1 ]
then
        exit 0
else
echo "Hello World"
fi
~                                                                               
~                                                                               
~                                                                               
~            

plz correct the error. how to use && operator in if conditional in linux.

---

### Post by antenna on 2010-04-27
The && should go outside the brackets, so like:

```
if [ $# -eq 0 ] && [ $# -gt 1 ]
```

or alternatively you can use the syntax:

```
if [ $# -eq 0 -a $# -gt 1 ]
```

where -a is and, -o is or. 

Note that this condition as you have it will never equal true as you are testing that the number  of arguments is equal to 0 and greater than 1, which can't be true of course.

---

### Post by bapoumba on 2010-04-27
Moved to PT.
Please understand that hints on assignments are fine.

---

### Post by smartlogicsseo on 2010-04-27
> **antenna said:**
> the && should go outside the brackets, so like:

```
if [ $# -eq 0 ] && [ $# -gt 1 ]
```or alternatively you can use the syntax:

```
if [ $# -eq 0 -a $# -gt 1 ]
```where -a is and, -o is or. 

Note that this condition as you have it will never equal true as you are testing that the number  of arguments is equal to 0 and greater than 1, which can't be true of course.
 

thanks!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by smartlogicsseo on 2010-04-27
> **antenna said:**
> 

Note that this condition as you have it will never equal true as you are testing that the number  of arguments is equal to 0 and greater than 1, which can't be true of course.



yes hahahah newbie problem

---

### Post by Elfy on 2010-04-27
[http://ubuntuforums.org/showthread.php?t=1463729](http://ubuntuforums.org/showthread.php?t=1463729)

---

