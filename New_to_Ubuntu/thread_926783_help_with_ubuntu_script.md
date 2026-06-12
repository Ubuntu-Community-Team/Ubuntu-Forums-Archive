---
title: "help with ubuntu script"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by brian123321 on 2008-09-22
i am writing a script for ubuntu. i want to have it multiply two numbers. how do i go about writing a line of code for this because i can not use the "*" symbol

---

### Post by stump138 on 2008-09-22
```
VARIABLENAME=$((x*y))
```
you mean that your * is broken? or just not the right syntax?

---

### Post by brian123321 on 2008-09-22
i thought that i heard that you cannot use "*" by itself in a script to have something multiply bc it will not use it as a multiplication symbol, it will use it for something else.

---

### Post by brian123321 on 2008-09-22
this is what is currently in my script and it does not work properly

if [ $2 = "*" ]; then
   ANSWER=`expr $1 * $3`

   echo $ANSWER
fi

---

### Post by stump138 on 2008-09-22
try ANSWER=$(($1*$3))

---

### Post by Mornedhel on 2008-09-22
Quote the *, like this :

2 '*' 3

Otherwise Bash thinks it's a glob for "every file in the folder" and expands it before passing it to the script.

---

