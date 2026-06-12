---
title: "Read element from input line"
date: 2012-01-31
forum: Programming Talk
---

### Post by beligor on 2012-01-31
Hi,
I am using bash to read a text file line by line. I then want to access element number i from that line, but don't know how to do it (so something like
 ```
 
if [$line[i]=="a"] then
echo "wawawiwa"
fi

```Probably a very naive question, but anyone know how to access it ?

---

### Post by ofnuts on 2012-01-31
> **beligor said:**
> Hi,
I am using bash to read a text file line by line. I then want to access element number i from that line, but don't know how to do it (so something like
 ```
 
if [$line[i]=="a"] then
echo "wawawiwa"
fi

```Probably a very naive question, but anyone know how to access it ?
You are not far:
```
items=($line)
```
creates a "items" array from the words in the line. You can address item at index $i (0-based) using
```

${items[$i]}

```
You can tell how many items by:
```

${#items
[*]}

```
Google for "bash arrays" for more.

---

### Post by sisco311 on 2012-01-31
Check out BashFAQ 001, 005, 073 and 100 (link in my signature).

---

