---
title: "split and Is a directory message"
date: 2013-04-18
forum: New to Ubuntu
---

### Post by smemamian on 2013-04-18
hi

when i use split command i get this message :
> 
split: /home/name/Desktop/test: Is a directory

```
split -b 1M /home/name/Desktop/test

```
Whereas test is a folder in my desktop !


```
ls -l /home/name/Desktop 
```

> drwxrwxr-x  2 name name    4096 Apr 18 11:53 test

---

### Post by schragge on 2013-04-18
What are you trying to achieve? Split every file in the folder into chunks of 1M? Then try
```
for file in /home/name/Desktop/test/*; do split -b 1M "$file" "$file".; done
```

---

