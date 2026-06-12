---
title: "zenity issue with special character"
date: 2014-03-10
forum: New to Ubuntu
---

### Post by ken18 on 2014-03-10
Following works fine:
 > zenity --info --text='This is a test'

but this fails:
> zenity --info --text='This is a test <=='

with a markup error message.  How can I include the string '<=='??  I've tried /<==, $<==, $(<==), $("<=="), &lt== and everything else I can think of, but nothing works.

Ken

---

### Post by steeldriver on 2014-03-10
Have you tried the --no-markup switch?

```
zenity --info --no-markup --text='This is a test <=='
```

From the manpage

```

       **--no-markup**
              Do not enable pango markup

```

---

### Post by ken18 on 2014-03-10
Thanks, that partially solves the issue, but not entirely.  What I really want is multiple lines and only one with '<==':

```
zenity --info --text="This is line 1 \n and line 2 \n and line3 <== \n and final line"
```

---

### Post by steeldriver on 2014-03-10
Well it appears to accept &lt;

```
zenity --info --text="This is line 1 \n and line 2 \n and line3 **&lt;**== \n and final line"
```

See [https://mail.gnome.org/archives/gtk-i18n-list/2009-June/msg00005.html](https://mail.gnome.org/archives/gtk-i18n-list/2009-June/msg00005.html)

---

### Post by ken18 on 2014-03-10
Thank you, thank you, thank you!  I've spend hours trying everything I could think of.  I actually tried &lt== but not &lt;==.  The extra ; was the trick!

Ken

---

