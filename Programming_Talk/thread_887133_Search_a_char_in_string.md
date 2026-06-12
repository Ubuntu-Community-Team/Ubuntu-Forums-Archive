---
title: "Search a char in string"
date: 2008-08-11
forum: Programming Talk
---

### Post by just_linux on 2008-08-11
have some strings in variable, and I want to know if that string has "24" or space:lolflag:
How can I search through the string?
:guitar:
 For ex: if in $r I have sdfkjhsdf sdf564dsfds df s654  hjfn   
I wander if it has "25" or not if it have  do.... it dont .... 
So I want to put the retuen in if  else 
Please help :popcorn:

---

### Post by aloshbennett on 2008-08-12
> 
if echo $r | grep 'searchstring' > /dev/null ; then
  ...
else
  ..
fi


:)

---

### Post by Joeb454 on 2008-08-12
Moved to Programming Talk

---

### Post by NovaAesa on 2008-08-12
The algorithm is an easy one to impliment, but the specifics of doing so will depend on the language used. Which you seem to have forgetten to tell us.

---

### Post by Lster on 2008-08-12
In C, strstr is what you want:

[http://www.cplusplus.com/reference/clibrary/cstring/strstr.html](http://www.cplusplus.com/reference/clibrary/cstring/strstr.html)

In Python, find is what is needed:

[http://docs.python.org/lib/string-methods.html](http://docs.python.org/lib/string-methods.html)

In Java, indexOf is what is required:

[http://java.sun.com/javase/6/docs/api/java/lang/String.html#indexOf(java.lang.String)](http://java.sun.com/javase/6/docs/api/java/lang/String.html#indexOf(java.lang.String))

...

---

