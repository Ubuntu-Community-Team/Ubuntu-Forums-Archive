---
title: "fopen() in C with directory"
date: 2011-02-11
forum: Programming Talk
---

### Post by layers on 2011-02-11
Alright, writing  

 ```
FILE *fp = fopen("text","wb")
``` will eventually be used to save a file named "text" in the  directory where the executable is. What if I want to specify a relative  or even an absolute directory. How would I be able to do it then?
 
FILE *fp = fopen("~/Desktop/folder/text","wb") does not work. // also...

---

### Post by cgroza on 2011-02-11
> **layers said:**
> Alright, writing  

 ```
FILE *fp = fopen("text","wb")
``` will eventually be used to save a file named "text" in the  directory where the executable is. What if I want to specify a relative  or even an absolute directory. How would I be able to do it then?
 
FILE *fp = fopen("~/Desktop/folder/text","wb") does not work. // also...

The "~" works only in bash. The standard library should provide a function to get the Homde Folder.

---

### Post by MadCow108 on 2011-02-11
relative and absolute directories work but the tilde(~) expansion is a shell feature and not directly available in C.

you'll have to write the path out (or, if available, use the environment variable HOME obtainable with getenv)

---

### Post by layers on 2011-02-11
You're right, of course. Thanks.

```
fp=fopen("./folder/t", "wb")
```

---

