---
title: "Way to check dvd movie playtime ?"
date: 2008-08-17
forum: Programming Talk
---

### Post by DamjanDimitrioski on 2008-08-17
Hi,
I'd like to count all my dvd movies from my collection, but they're too many, so I want to build some program which will do that for me.

This is the goal>
[FONT=Franklin Gothic Medium][I]for each cd:
    mount cd(if cdrom1 not mounted that is).
    check format
    get playtime
    add playtime to list
calculate list
print total play time(converted to hours or :D days)[/I]
[/FONT]
So does anybody know how to build this thing :confused: ?

---

### Post by DamjanDimitrioski on 2008-08-17
I forgot, the program is in Python and the total frames are extracted with pymedia, but how :) ?

---

### Post by mike_g on 2008-08-17
Well if you can get the fps the media is played at then it would just be a matter of doing: 
```

seconds = frames / fps
minutes = seconds / 60
seconds = seconds % 60
hours = minutes / 60
minutes = minutes % 60
days = hours / 24
hours = hours % 24

```
I cant remeber the exact syntax in python but % is meant to be the modulus operator. Also, I dont know how you would get the frames per second; maybe it can be done with pymedia?

---

### Post by DamjanDimitrioski on 2008-08-17
I know how to convert the units, but I need to get the number only, that's my problem :(.

---

