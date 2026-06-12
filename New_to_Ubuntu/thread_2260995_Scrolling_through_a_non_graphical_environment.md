---
title: "Scrolling through a non graphical environment"
date: 2015-01-15
forum: New to Ubuntu
---

### Post by Aphexlog on 2015-01-15
I am trying to figure out how I would scroll through an ls listing of my etc directory
I am running in multi-user-interface mode
any help would be greatly appreciated
- thanks in advance :)

---

### Post by Aphexlog on 2015-01-15
[COLOR=#000000]I am trying to figure out how I would scroll through an ls listing of my etc directory[/COLOR]
[COLOR=#000000]I am running in multi-user-interface mode[/COLOR]
[COLOR=#000000]any help would be greatly appreciated[/COLOR]
[COLOR=#000000]- thanks in advance [/COLOR]:smile:

---

### Post by Holger_Gehrke on 2015-01-15
You can either pipe ls to less or use Shift-PgUp / Shift-PgDwn to scroll through the Buffer.

---

### Post by schragge on 2015-01-15
**Shift+PgUp** and **Shift+PgDown**, but you also can pipe the long output through pager:
```

ls /etc | less

```
or even
```

ls /etc | column | less

```

[highlight]Update.[/highlight] **Holger_Gehrke** beat me to it.

---

### Post by Habitual on 2015-01-15
```
ls | less
``` ?

---

### Post by grahammechanical on 2015-01-15
No. I was right. A double post

[http://ubuntuforums.org/showthread.php?t=2260995](http://ubuntuforums.org/showthread.php?t=2260995)

It is not nice behaviour

---

### Post by oldos2er on 2015-01-16
Threads merged. From the posting guidelines: "Do not cross post, or post the same thing in multiple locations."

---

