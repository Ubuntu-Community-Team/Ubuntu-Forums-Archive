---
title: "dialog prgbox - doesn't seem to work"
date: 2013-02-28
forum: Programming Talk
---

### Post by sebastian.s on 2013-02-28
Hey all, im stuck working on a script where i use dialog, and im trying to use a **dialog prgbox** to print out-put from a command and it's simply not working.

The syntax is:
```
dialog --prgbox "cal" 10 20
```

In my understanding the ouput from the cal command should be printed inside the dialog box, but it's not, it is empty.
I have read the man page and have looked up examples on the internet, but i can't figure this one out.

Thanks in advance.

---

### Post by schragge on 2013-03-05
Hmm, you're right. Weird. :confused:
As a workaround, *--programbox* still seems to work a bit better
```
cal|dialog --programbox 12 24
```
*--calendar* works as expected
```
dialog --calendar CALENDAR 0 0 `date +%d %m %Y`
```

---

### Post by sebastian.s on 2013-03-06
Ah that's nice, your first example worked perfectly.

Thanks mate :-)

---

