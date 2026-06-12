---
title: "[SOLVED] Need help translating bash statement"
date: 2007-10-23
forum: Programming Talk
---

### Post by dwhitney67 on 2007-10-23
Can someone help me translate the following bash statement into ash (or as I like to call it, pidgin bash), or just explain what it is doing:

LCD_OUT1="${1:0:$LCD_CHAR}"

I'm using BusyBox-1.2.2, and it does not understand the statement above.

---

### Post by wolfbone on 2007-10-23
Perhaps you could, as they say, "RTFM":

```
${parameter:offset:length}
              Substring Expansion.  Expands to up  to  length  characters  of
              parameter  starting  at  the character specified by offset...
```

---

### Post by dwhitney67 on 2007-10-23
Perhaps I could have gone the RTFM route, but why make an effort when there is someone like you to save the day.

Thanks.... I think?

---

### Post by wolfbone on 2007-10-23
> **dwhitney67 said:**
> ...but why make an effort when there is someone like you to save the day.

Doh!

:)

---

### Post by ghostdog74 on 2007-10-23
> **dwhitney67 said:**
>  but why make an effort when there is someone like you to save the day.


that's the wonderful thing about forums isn't it? however, you should also be aware that you will also encounter cases where you will not get any replies simply because the OP is too lazy to do his own homework.

---

