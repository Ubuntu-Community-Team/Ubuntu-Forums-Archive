---
title: "Explain Bash command"
date: 2008-09-30
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-09-30
```
tar cf - ./folder | ssh IP_ADDRESS "cat > /folder"
```

it tars a folder and pipes it over the net. but the syntax if foreign


After explaining it please argue about whether it would be more efficent to use a plain tar archive or a .gz or .bz2

keep in mind that (to my knowledge) tar can compress as it reads through and bz2 is dictionaried and i don't know about gz

---

### Post by CptPicard on 2008-09-30
The way you put it makes it really look like it's a homework assignment...

---

### Post by LaRoza on 2008-09-30
> **Mr.Macdonald said:**
> ```
tar cf - ./folder | ssh IP_ADDRESS "cat > /folder"
```

it tars a folder and pipes it over the net. but the syntax if foreign


What don't you understand? You seem to know what it does, without being able to read it...

> 
After explaining it please argue about whether it would be more efficent to use a plain tar archive or a .gz or .bz2

You mean "discuss". For .tar, read this (it almost explains the command you posted specifically): [http://en.wikipedia.org/wiki/.tar](http://en.wikipedia.org/wiki/.tar)

---

