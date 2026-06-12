---
title: "Help with sed"
date: 2009-06-04
forum: Programming Talk
---

### Post by matrix4ever on 2009-06-04
After doing this:
>find $HOME -name '*.c' >>file1

I have stuff like this in file1:
/home/ivo/hello.c
/home/ivo/C/hashing.c

And I need to get only those files's paths
/home/ivo
/home/ivo/C

I suppose I should use sed but I can't find the right pattern

I succeded in doing the substitution in a variable with bash parameter expansion:
var="/home/ivo/hello.c"
V2="${var%/*.c}"      # deletes the shortest occurence of /*.c in var
echo $V2
but i don't know how to do this in files.

Thanx anybody for trying.

---

### Post by sisco311 on 2009-06-04
```
find $HOME -name "*.c" -printf "%h\n" | sort | uniq >> filename
```

---

### Post by matrix4ever on 2009-06-04
> **sisco311 said:**
> ```
find $HOME -name "*.c" -printf "%h\n" | sort | uniq >> filename
```

Thanx a lot!!! 
I've been spending hours (and days) trying with sed and it isn't even needed.
Now I can finally complete the rest of the 321-lines code with this and it's finally done (I started 6 months ago and this is my first script in UNIX).

---

### Post by ghostdog74 on 2009-06-04
if your sort have -u option, then no need uniq

---

