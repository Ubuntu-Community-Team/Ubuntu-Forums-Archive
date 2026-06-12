---
title: "default include directories /usr/local/include"
date: 2005-09-23
forum: Programming Talk
---

### Post by tsaphah on 2005-09-23
**General question: ** How do I add a path/directory to the default path that gcc/ld looks at?


**My problem:**
I'm observing that /usr/local/include is not searched by default when gcc/g++ is run.  I'm trying to include a header file from the Boost libraries that I've install there. 
[found at: /usr/local/include/boost/... ]  I'm trying to include with #include <boost/headerfile.h> 

EDIT: Ok, after a starting my laptop up again this morning its finding the my boost libraries...  I would still be curious to know if its possible to add a path to the default search directory.

-- 
>> time is swift <<

---

### Post by yccheok on 2005-09-29
You can use the 'I' flag in gcc -

gcc -I /usr/local/include/ myprogram.c

---

