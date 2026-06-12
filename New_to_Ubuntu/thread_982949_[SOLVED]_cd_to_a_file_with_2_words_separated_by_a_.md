---
title: "[SOLVED] cd to a file with 2 words separated by a space on a terminal"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by wstay on 2008-11-15
In a terminal, how do we cd to a file with 2 words separated by a space?
Normally, we would put/enclose these words in single inverted comma.
But I find that I cannot do this on a terminal in ubuntu.
It would say no such file or directory.
Is there a way to get around this?

---

### Post by issih on 2008-11-15
Use the escape character which is "\" So if you wanted to cd to something named "User Guide" you'd type:

```
cd User\ Guide
```

Basically the \ tells the shell not to interpret the following character, but instead to read it literally.

hope that helps

---

### Post by sharks on 2008-11-15
If u have a folder called ubuntu forums, you have to type :
> cd "ubuntu forums"

---

### Post by taurus on 2008-11-15
Or just type in the first word (or a few letters of the first word) and hit the Tab key and it will fill in the rest.  It's a little handy if you have a long name and don't feel like typing it all out.

---

### Post by CatKiller on 2008-11-15
You can also tab-complete program, directory and file names. So for the User Guide example above, you can type ```
cd Use
``` and then press the Tab key to autocomplete the rest. If there is more than one way of completing a given string, your computer will beep, and then pressing Tab twice will give you a list of the ways it can be completed.

Edit: what are the chances of being beaten to it at that point... :)

---

### Post by wstay on 2008-11-15
cannot use ¨ ¨
can use \
Thanks.

---

### Post by binbash on 2008-11-15
> **taurus said:**
> Or just type in the first word (or a few letters of the first word) and hit the Tab key and it will fill in the rest.

Yes but this will suck when there are two or more folders like :

ubuntu forums 333
ubuntu forums 444

---

### Post by CatKiller on 2008-11-15
> **binbash said:**
> Yes but this will suck when there are two or more folders like :

ubuntu forums 333
ubuntu forums 444

Not really. ubu<TAB>3<TAB> or ubu<TAB>4<TAB>.

---

### Post by wstay on 2008-11-24
> **sharks said:**
> If u have a folder called ubuntu forums, you have to type :
But this does not work on the terminal I am using.

---

