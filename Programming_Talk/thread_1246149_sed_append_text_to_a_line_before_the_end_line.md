---
title: "sed: append text to a line before the end line?"
date: 2009-08-21
forum: Programming Talk
---

### Post by PryGuy on 2009-08-21
Good day to you all!
I have a question, I have to append a line to a line prior to end, so the text would look:> Old Line
Old Line
Old Line
NEW LINE!
Old LineIt's not as simple as I figured... Thanks in advance!

---

### Post by unutbu on 2009-08-21
```
awk '{new=$0; print old; old=new}END{print "NEW LINE!"; print old}' file
```

---

### Post by PryGuy on 2009-08-21
Thank you, unutbu! You help me for the second time! :)
But is it impossible for the sed almighty? It's such an easy task... :(

---

### Post by DaithiF on 2009-08-21
Hi,
In sed:
sed '$iNew Line!' somefile

---

### Post by PryGuy on 2009-08-21
> **DaithiF said:**
> Hi,
In sed:
sed '$iNew Line!' somefileThis will add line to the very end as far as I get it...

---

### Post by DaithiF on 2009-08-21
Hi, no $i inserts before the last line.  $a would append after the last line.

So:
```
xxx@xxx:~/tmp$ cat testfile
firstline
second line
third line
xxx@xxx:~/tmp$ sed '$iNew Line!' testfile
firstline
second line
New Line!
third line

```

---

### Post by PryGuy on 2009-08-21
Rule, Britain!!!
P.S. If you only knew how I miss London...

---

### Post by Albert Net on 2010-02-09
Re:unutbu

```
awk '{new=$0; print old; old=new}END{print "NEW LINE!"; print old}' file
```
This code quite tricky. Unfortunately, there is one bug that it insert one blank line at the first line of the file, for "old" is empty when gawk is processing the first line. 

```
sed '$i \
yourinsertedtext' file
```This one is the one that should be used, for it is rather simple.

---

