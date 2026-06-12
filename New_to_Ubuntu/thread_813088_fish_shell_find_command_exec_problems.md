---
title: "fish shell find command exec problems"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by sp3ctum on 2008-05-30
I used to search for mp3 files on my box and move them with

[SIZE="1"]find . -maxdepth n -iname "" -exec mv {} /directory \;[/SIZE]

but now that I've switched to using the fish shell, the command returns the following error:

[SIZE="1"]mv: cannot stat `': No such file or directory[/SIZE]

What am I doing wrong?:confused:

ps. the command works with bash like it used to.

---

### Post by spiderbatdad on 2008-05-30
Maybe related to this:
```
There is one important piece of syntax that is not yet implemented, namely full IO redirection for blocks and functions. It is currently possible to use functions in pipelines and to redirect the output of functions, but functions cannot output binary data, and input redirection is not supported. It is not possible to pipe or redirect the input/output of blocks of code.

A future version of fish will allow code like this:

for i in (find . -name "*.c"); echo $i; grep "mbstowcs" $i; end | less

```

---

### Post by sp3ctum on 2008-05-30
I don't get it. Are you saying it's not possible? :S

---

### Post by spiderbatdad on 2008-05-30
From my limited understanding...it looks, to me, like your command wants to redirect input to to a file. Based on this:
>  input redirection is not supported.  I'm guessing maybe not.
Have you tried wrapping the file name in quotes?

---

### Post by sp3ctum on 2008-05-30
That works. Great idea :)
Thanks a bunch!

"{}" is the solution, if anyone else wonders about it.

---

