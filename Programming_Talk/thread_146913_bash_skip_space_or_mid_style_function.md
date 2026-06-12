---
title: "bash skip space or mid style function"
date: 2006-03-19
forum: Programming Talk
---

### Post by oly on 2006-03-19
i have been writting a script to setup a ldap directory i wanted to make it also set up samba as a PDC but have hit a snag with my scripting knowledge.

I am trying to get a SID number but i only want the number, i have managed to achieve this except it has a space in front of it is there a way i can remove spaces from the output ??

sudo net getlocalsid | awk -F: '{print  $2}'

that returns what i want but with a space at the start, can anyone help me with something that will also remove the space ???

---

### Post by LordHunter317 on 2006-03-19
Pipe it to cut, and tell it to remove the first character:```
| cut -c2-
```

---

### Post by oly on 2006-03-19
thanks for that just what i was after :)

---

