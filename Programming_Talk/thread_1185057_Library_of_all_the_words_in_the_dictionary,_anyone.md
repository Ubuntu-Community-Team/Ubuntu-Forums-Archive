---
title: "Library of all the words in the dictionary, anyone pls?"
date: 2009-06-11
forum: Programming Talk
---

### Post by superpink99 on 2009-06-11
ok im making a program in python, and i need all the words of the dictionary to use it as a cross reference, the problem is it would take me years if i write everything manually.

so does anyone have a better way of obtaining all of the words?
or maybe the python package includes a library of all the words in a dictionary? Does it?

im kinda new so i hope i explained the problem well..........

thanks in advance...........

---

### Post by Mirge on 2009-06-11
Look in /usr/share/dict

---

### Post by superpink99 on 2009-06-11
uhmmmmmmm hi Mirge, would you mind putting more details on how to look at that please......thanks.....

---

### Post by Mirge on 2009-06-11
Heh, open a terminal... type:

ls -la /usr/share/dict

you'll see something similar to:
```

mike@mike-kubuntu:/usr/share/dict$ ls -la
total 1840
drwxr-xr-x   2 root root   4096 2009-04-20 09:41 .
drwxr-xr-x 229 root root  12288 2009-06-10 20:53 ..
-rw-r--r--   1 root root 931467 2008-11-05 17:03 american-english
-rw-r--r--   1 root root 929603 2008-11-05 17:03 british-english
-rw-r--r--   1 root root    199 2009-02-20 14:09 README.select-wordlist
lrwxrwxrwx   1 root root     30 2009-06-07 18:53 words -> /etc/dictionaries-common/words
lrwxrwxrwx   1 root root     16 2009-06-07 18:53 words.pre-dictionaries-common -> american-english
mike@mike-kubuntu:/usr/share/dict$

```

Those are all files containing many, many words.. obviously :).

---

### Post by superpink99 on 2009-06-11
nice! i think that might just work....thanks a bunch......;)

---

### Post by Mirge on 2009-06-11
No worries.;)

---

### Post by superpink99 on 2009-06-11
Ok one last question:), how do i open those so i can see what it contains? (or can i even open them in a text editor or something)

i tried to open it with 'open' but it doesn't work

---

### Post by Girya on 2009-06-11
> cat /usr/share/dict/american-english |less

then hit the space bar to scroll a page ata time

---

### Post by ad_267 on 2009-06-11
> **Girya said:**
> then hit the space bar to scroll a page ata time

Why not just "less /usr/share/dict/words", seems kind of pointless to use cat. You should be able to use any text editor though.

---

### Post by Girya on 2009-06-11
> **ad_267 said:**
> Why not just "less /usr/share/dict/words", seems kind of pointless to use cat. You should be able to use any text editor though.

good point

---

