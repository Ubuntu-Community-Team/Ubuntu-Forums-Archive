---
title: "Remove Lines p:q from text file w/o editor"
date: 2007-08-02
forum: Programming Talk
---

### Post by SNYP40A1 on 2007-08-02
Say I want to remove all lines 100,000 to 150,000 from a text file.  How can I do this without using a text editor?  Normally, this would be a trivial task, but not when working with a 490 MB text file.  I first tried to open in Notepad++ (Windows XP) program crashed.  Then I tried VIM on a Sun workstation, opened fine, but basically froze when trying to delete the lines.  Is there an efficient way to remove some sequence (consecutive) of lines from a text file using some Unix tool?  Sed looked close, but I did not find the remove command that I wanted.  

This is not really a programming question so mods, please feel free to move my post if necessary.  This looked like the best thread for it, but I could be wrong.

---

### Post by roncrump on 2007-08-02
> **SNYP40A1 said:**
> Say I want to remove all lines 100,000 to 150,000 from a text file.  How can I do this without using a text editor? 
I imagine sed wuold do the job, but I've never been a big sed user so I'll give an awk (or gawk)  solution instead:

```
awk 'NR < 100000 || NR > 150000 {print $0}' oldfile > newfile
```

should do the job of omitting lines 100000 to 150000, inclusive, of oldfile from newfile.

Hope this helps.

Ron.

---

### Post by roncrump on 2007-08-02
> **SNYP40A1 said:**
> Say I want to remove all lines 100,000 to 150,000 from a text file.  How can I do this without using a text editor?  <snip>  Sed looked close, but I did not find the remove command that I wanted.  


Second go, first worked but obviously sed should do it, so using sed this time:

```
sed '100000,150000d' oldfile > newfile
```

Ron.

---

### Post by SNYP40A1 on 2007-08-03
Thanks, that did the trick!!

---

