---
title: "Press any key during bash script..."
date: 2012-07-29
forum: Programming Talk
---

### Post by Fxy on 2012-07-29
Hi

I'm writing a bash script, but would like to be able to have a press any key to continue option in part.  My trouble is I do not know the command for how to accomplish this !!  Can anyone tell me the correct command :?



Fxy...

---

### Post by spjackson on 2012-07-29
```

echo Press a key...
read -n 1
echo
echo Continuing...

```

---

### Post by Bachstelze on 2012-07-29
What's the "any" key? :o

---

### Post by Fxy on 2012-07-30
> **Bachstelze said:**
> What's the "any" key? :o

The any key could be any key on the keyboard or being more specific the enter key...



Fxy...

---

### Post by sisco311 on 2012-07-30
BashFAQ 065 (link in my signature).

---

### Post by Habitual on 2012-07-30
```

echo -n "Press any key..."
read ANSWER

```

---

### Post by nmaster on 2012-07-30
> **Bachstelze said:**
> What's the "any" key? :o
lol, i don't think everyone got the joke...

---

### Post by Pinoy Tux on 2012-07-31
```
read -n 1 -p "Press any key to continue..."
```

---

### Post by hakermania on 2012-07-31
> **Bachstelze said:**
> What's the "any" key? :o

[CENTER][IMG]http://static.desktopnexus.com/thumbnails/45292-bigthumbnail.jpg[/IMG][/CENTER]

---

