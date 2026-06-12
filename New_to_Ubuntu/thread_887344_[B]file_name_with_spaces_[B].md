---
title: "[B]file name with spaces [/B]"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by ellankavi on 2008-08-12
I wanted to copy few folders from my cd to hard disk but then noticed that they were write protected and only accessible by root! so in the terminal, i logged in as root and tried to copy just to realise that the folder name had spaces inbetween. How do i copy that?

sudo -i
cp folder_name destination

this'll not work right?

---

### Post by jordanmthomas on 2008-08-12
You have two choices.
```
cp -r "folder name" destination
```
or
```
cp -r folder\ name destination
```

The \ character escapes the next character, so you're able to use spaces in names.

---

### Post by ellankavi on 2008-08-12
thanks mate that solved my prob

---

