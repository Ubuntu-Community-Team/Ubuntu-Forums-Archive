---
title: "Help with sed"
date: 2009-10-21
forum: Programming Talk
---

### Post by c2483 on 2009-10-21
I'm trying to replace spaces with backslash space.  I tried 
```
file=`echo "m n b v" | sed -e 's: :\\ :g'` | echo $file
```
but I get this as a result
```
m n b v
```
I expect 
```
m\ n\ b\ v
```

I'm using 9.10 beta

---

### Post by John Bean on 2009-10-21
You're doing something odd there, but it's not sed that's giving the problem. Just type:
```
echo "m n b v" | sed -e 's: :\\ :g'
```into a terminal and see.

If you want the result in a variable by all means use the backquotes (or $(command) syntax) but the rest of your line is... odd ;-)

Try something like
```
 file=$(echo "m n b v" | sed -e 's: :\\ :g') ; echo $file 
```instead.

---

### Post by c2483 on 2009-10-21
thanks

---

### Post by ghostdog74 on 2009-10-21
awk 
```

# echo a c d | awk '{gsub(" ","\\ ")}1'
a\ c\ d

```
you can even do it with bash itself
```

# a="a b c"
# echo ${a// /\\}
a\b\c
# echo ${a// /\\ }
a\ b\ c


```

---

