---
title: "replace &quot;%20&quot; with &quot;\ &quot;"
date: 2007-10-24
forum: Programming Talk
---

### Post by ryanchew on 2007-10-24
I'm trying to get my script to replace strings that contain "%20" to "\ "
I can't seem to be able to get it right...

I've tried echo New%20Folder | sed s#'%20'#'\ '#g but it simply just replaces it as a space without the \ character.

Anyone know how to get around this?

---

### Post by K.Mandla on 2007-10-26
Moved to Programming Talk.

---

### Post by nanotube on 2007-10-26
try the double-backslash. 

```
$ echo New%20Folder | sed s#'%20'#'\\ '#g
New\ Folder

```

---

### Post by ghostdog74 on 2007-10-26
```

# echo New%20Folder%20test |awk '{gsub("%20","\\ ");print}'
New\ Folder\ test

```
or
```

# v="New%20Folder%20test"
 # echo ${v//\%20/\\ }
New\ Folder\ test

```

---

