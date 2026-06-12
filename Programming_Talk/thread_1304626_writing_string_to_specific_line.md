---
title: "writing string to specific line"
date: 2009-10-29
forum: Programming Talk
---

### Post by aliahsan81 on 2009-10-29
I want to put a text string in file using any method on specific line


line number 30

text to be put %this is location /var/www/filename

---

### Post by Arndt on 2009-10-29
> **aliahsan81 said:**
> I want to put a text string in file using any method on specific line


line number 30

text to be put %this is location /var/www/filename

You can use 'sed':

```
sed -i '4i\
hi' file

```

adds "hi" as line 4 in the file "file".

What should happen if there are less than 30 lines in the file?

---

### Post by aliahsan81 on 2009-10-29
If there is less then 30 line.

it will not add any thing because EOF character is reached.

---

### Post by Arndt on 2009-10-29
> **aliahsan81 said:**
> If there is less then 30 line.

it will not add any thing because EOF character is reached.

The command I suggested will work, then.

---

### Post by ghostdog74 on 2009-10-29
> **aliahsan81 said:**
> I want to put a text string in file using any method on specific line


line number 30

text to be put %this is location /var/www/filename
see [here example 2]("http://ghostdog74.livejournal.com/36703.html") for a simple example. You can modify to suit your need

---

