---
title: "grep help"
date: 2012-07-26
forum: New to Ubuntu
---

### Post by nathanv221 on 2012-07-26
hey all, i am trying to grep search but im not interested in the contents of files, i just want to look for a directory name. is there a way to specify only directory names? or mabye should i be using the find command?

it may have been on the man page but if so i missed it.

---

### Post by HermanAB on 2012-07-26
$ find /home/joesoap -name whatever

---

### Post by papibe on 2012-07-26
Hi nathanv221.

You inkling is right. grep works better for file content, and find for file or directory names (although there are always ways to 'make' it work) .

Try this:
```
find -type d -iname '*pattern*'
```
where
   '-type d' will only match directories
   '-iname' will match a case insensitive expression.

I hope that helps. Let us know how it goes.
Regards.

---

### Post by nathanv221 on 2012-07-26
Thank you both,  i was using find to see if i had messed up my program build earlier. apparently i did. so it didn't go well but the find feature worked perfectly, so thanks.

---

