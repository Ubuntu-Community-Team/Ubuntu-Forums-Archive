---
title: "Code for custom arrow keys (shell script)"
date: 2010-04-05
forum: Programming Talk
---

### Post by sasnfbi1234 on 2010-04-05
this is my code c=12322123;x=85;y=20;while read -sn1 p;do k=${c:(p-1)*2:2};let x+=$((k/10-2));let y+=$((k%10-2));echo -en \ \033[$y\;"$x"HX;done


it a shell script it makes a etch a sctech

if some one could walk me throguht (or just do)

make it so you use arrow keys for derction instead of  1234


sorry for bad english it my third languge

---

### Post by lisati on 2010-04-05
Moved to "Programming Talk"

Suggestion: use the [noparse]```
 and 
```[/noparse] tags around your code snippet, it will help preserve the formatting.

---

### Post by sasnfbi1234 on 2010-04-05
```
c=12322123;x=85;y=20;while read -sn1 p;do k=${c:(p-1)*2:2};let x+=$((k/10-2));let y+=$((k%10-2));echo -en \\033[$y\;"$x"HX;done

```


all right now if soee one could help

---

### Post by sasnfbi1234 on 2010-04-12
help?

---

