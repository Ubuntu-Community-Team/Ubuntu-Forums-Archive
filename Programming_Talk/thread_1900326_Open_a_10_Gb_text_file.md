---
title: "Open a 10 Gb text file"
date: 2011-12-26
forum: Programming Talk
---

### Post by stalaei on 2011-12-26
Hi.

I have a 10 Gb text file.the default text editor in ubuntu doens't open it.

Does anyone know how can i open it??

Thanks

---

### Post by squenson on 2011-12-26
Quite a large file! I suggest that you write a small program, in python or C, that will make smaller pieces of it (10 MB or so). Use a parameter which defines the beginning position in bytes. Then you can open the extract with any text editor.

---

### Post by hakermania on 2011-12-26
Hello! Please read here about split: [http://ubuntuforums.org/showthread.php?t=1428089](http://ubuntuforums.org/showthread.php?t=1428089)

---

### Post by 2F4U on 2011-12-26
According to the limits on vi, it should be able to edit a file of that size:

[http://vimdoc.sourceforge.net/htmldoc/vi_diff.html](http://vimdoc.sourceforge.net/htmldoc/vi_diff.html)

---

### Post by The Cog on 2011-12-26
I don't suppose you want to actually read all that file. What do you want to actually do with it? There is probably a tool that will do what you want to do better than using an editor.

---

### Post by Petrolea on 2011-12-26
As suggested before, I recommend that you write a program that reads a file by chunks (you can specify the size if a chunk).

I think pretty much any programming language can do that.

---

### Post by Barrucadu on 2011-12-27
You don't need to write your own program for that: as suggested by hakermania you could use `split` to break it up into small chunks; then recombine them afterwards with `cat`.

---

