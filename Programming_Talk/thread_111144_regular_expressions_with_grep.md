---
title: "regular expressions with grep"
date: 2006-01-01
forum: Programming Talk
---

### Post by Swab on 2006-01-01
I want to search for any occurance of 45104 following any tabs or spaces... I'm new to regular expressions and don't understand why the following is not working.

egrep  '\t+45104' input.txt

Any pointers?

---

### Post by toojays on 2006-01-01
I just had a try of this myself, and it seems like the tab escape isn't being interpreted properly for some reason. For me, it worked when I used a literal tab instead of a '\t'. You can type a literal tab in the shell by pressing Control-V and then hitting TAB.

To do what you really want, you need:

egrep '[<literal-tab><literal space>]+45104' input.txt

so that it can be tabs OR spaces in front of the number.

---

### Post by Swab on 2006-01-01
That worked! Thanks for the help, much appreciated!

---

### Post by crazycrazyeco on 2012-06-27
ctrl-v and tab. Great. It works. thanks.

---

### Post by sisco311 on 2012-06-27
Old thread closed.

---

