---
title: "[SOLVED] Little script needed"
date: 2008-10-17
forum: Programming Talk
---

### Post by Qtips on 2008-10-17
Hi,

I'm new to Ubuntu and script programming with the command line interface. I have a simple task. I have a folder with all my ebook listed. I want a way to take this list of ebooks and put them in a text file. Can Linux do this with something like the cat commands and pipe commands ?

Thanks for all.

---

### Post by snova on 2008-10-17
I'm not quite certain what you want. If it's to write a list of ebooks to a file, this would do:

```
ls -1 > file-with-list
```

That's a 1 (one), not l (L).

---

### Post by Qtips on 2008-10-17
So many thanks !

Linux is so great ;)

---

### Post by geirha on 2008-10-17
Just a minor clarification, ls will detect whether the output is going to a terminal or not. If the output is going to a terminal, it will check the width of the terminal and display the files in columns if possible, and you can use the -1 to force it to display each file on a line by itself if you wish. If the output is not going to a terminal (e.g. a file or through a pipe) ls will put each filename on a line by itself automatically, so "ls > file-with-list" will yield the exact same result as "ls -1 > file-with-list".

---

