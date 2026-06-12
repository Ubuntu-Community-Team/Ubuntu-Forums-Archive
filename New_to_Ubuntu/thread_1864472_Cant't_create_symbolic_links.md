---
title: "Cant't create symbolic links"
date: 2011-10-19
forum: New to Ubuntu
---

### Post by bball2601 on 2011-10-19
Hey, 
I'm having trouble creating symbolic links.  If I understand correctly, symbolic links are essentially pointers to directories or files.  I have tried many times to create a symbolic link to both files and directories, and each time when ever I would try to open them it would say there are too many levels of the symbolic link.  I have tried this with files and directories from both my linux partition and windows partition of my hard drive.

This is the format I used to try to create the links:

:~$ ln -s ./eBooks ./test/eBooks

If this way doesn't work, what is the correct way to do this?

---

### Post by Lars Noodén on 2011-10-19
In your example the directory "test" must exist.  Does it?

---

### Post by mcduck on 2011-10-19
...also the "./" part is not really doing anything in the command, as the period only tells the shell to look for those items in your current directory. Which it does anyway. ;)

Assuming that a file or directory called "eBooks" and a directory called "test" both exist in your current directory:
```
ln -s eBooks test/eBooks
```

Note that you can't create links on Windows filesystems. And also, in case you can't get the commands working, if you use Gnome you can create symbolic links from the file manager by drag&dropping items with middle mouse button. That gives you a popup asking if you want to copy, move or link the item.

---

### Post by bball2601 on 2011-10-19
Yes all of these directories exist.  And I typed ./ as a variation of the command that would maybe work...but it didn't change anything

---

### Post by matt_symes on 2011-10-19
Hi

```

matthew@matthew-Aspire-7540:~$ pwd
/home/matthew
matthew@matthew-Aspire-7540:~$ touch eBooks
matthew@matthew-Aspire-7540:~$ ls eBooks
eBooks
matthew@matthew-Aspire-7540:~$ mkdir test
matthew@matthew-Aspire-7540:~$ ls -d test
test
matthew@matthew-Aspire-7540:~$ ln -s eBooks test/eBooks
matthew@matthew-Aspire-7540:~$ ls -l test
total 0
lrwxrwxrwx 1 matthew matthew 6 2011-10-19 08:27 eBooks -> eBooks
matthew@matthew-Aspire-7540:~$ readlink -f test/eBooks 
matthew@matthew-Aspire-7540:~$ rm test/*
matthew@matthew-Aspire-7540:~$ ln -s ./eBooks test/eBooks
matthew@matthew-Aspire-7540:~$ ls -l test
total 0
lrwxrwxrwx 1 matthew matthew 8 2011-10-19 08:30 eBooks -> ./eBooks
matthew@matthew-Aspire-7540:~$ readlink -f test/eBooks 
matthew@matthew-Aspire-7540:~$ rm test/*
matthew@matthew-Aspire-7540:~$ ln -s ../eBooks test/eBooks
matthew@matthew-Aspire-7540:~$ ls -l test
total 0
lrwxrwxrwx 1 matthew matthew 9 2011-10-19 08:31 eBooks -> ../eBooks
matthew@matthew-Aspire-7540:~$ readlink -f test/eBooks 
/home/matthew/eBooks
matthew@matthew-Aspire-7540:~$ cd test
matthew@matthew-Aspire-7540:~/test$ readlink -f eBooks 
/home/matthew/eBooks
matthew@matthew-Aspire-7540:~/test$
```Does this help ? Or use full paths.

Kind regards

---

