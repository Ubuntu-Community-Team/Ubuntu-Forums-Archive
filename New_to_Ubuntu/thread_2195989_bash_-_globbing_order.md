---
title: "bash - globbing order"
date: 2013-12-27
forum: New to Ubuntu
---

### Post by Previous1 on 2013-12-27
While following this tutorial I created a few files

[http://linux-training.be/files/books/html/fun/ch14s04.html](http://linux-training.be/files/books/html/fun/ch14s04.html)

[I]touch file1 file3 File55 fileab FileAB fileabc file2 File4 FileA Fileab fileab2

[/I] I'm using the nl_NL.UTF-8 locale, so when using glob brackets I expected it to be case insensitive. This works when doing

[I]ls [A-Z]ile* 
[/I][I]**f**ile1 file3 **F**ile55 fileab FileAB fileabc file2 File4 FileA Fileab fileab2

[/I]but when I use the brackets at the end it's case sensitive

[I]ls File[A-Z]*
File**A** FileAB[/I] (no File**a**b)

Google has quite a bit on globbing but I haven't found specifics to this behaviour. What am I missing?

OS: Xubuntu 12.04
Bash: 4.2.25(1)-release (i686-pc-linux-gnu)

---

### Post by bluefrog on 2013-12-27
ls [[:upper:]]ile*      should work

you have to change the locale if you want to use [A-Z]
[http://pubs.opengroup.org/onlinepubs/007908799/xbd/locale.html](http://pubs.opengroup.org/onlinepubs/007908799/xbd/locale.html)

---

### Post by Previous1 on 2013-12-28
Using [[:upper:]] or [A-Z] with LANG=C did give consistent case sensitivity, and [[:alpha:]] case insensitivity. Though I was wondering how a supposed case insensitive locale (UTF8) seems to depend on the position of the [A-Z]..

---

