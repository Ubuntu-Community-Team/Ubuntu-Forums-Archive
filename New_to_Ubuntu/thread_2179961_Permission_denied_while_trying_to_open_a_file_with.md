---
title: "Permission denied while trying to open a file with Terminal"
date: 2013-10-10
forum: New to Ubuntu
---

### Post by CRze3wD on 2013-10-10
Hello there, just learning linux/ubuntu

The problem is, I'm playing with the terminal, so I created a file using the line "> test.txt", and the file is alright, but when I try to open it using "./test.txt" it returns the message "bash: ./test.txt: Permission denied". I'm pretty sure I got all the essentials packages and stuff, so dunno what's going on

Thanks

edit: I'm using 12.04 btw

---

### Post by Bashing-om on 2013-10-10
CRze3wD; Hi ! Welcome to the forum .
a) What are the file permissions ? :
```

ls -l test.txt

```
b) Who owns the file ? (also from the above)
c) is the file an executeable file ?(also from the above) or just a text file (from the file extension use of ".txt" ?
d) is the file "test.txt" the same file to be executed located in your present working directory ?

see:
```

man ls
man chown
man chmod
man chgrp

``` for the documentation and for continued discussion.

security ->
[INDENT][INDENT]the strength of linux 
[/INDENT][/INDENT]

---

### Post by CRze3wD on 2013-10-10
barroso@ubuntu:~$ ls -l test.txt
-rw-rw-r-- 1 barroso barroso 0 Oct 10 19:30 test.txt

It's a text file, it opens with the gedit, but I can't open it with the terminal.
edit: also, I can't open any file at all using the command "."

---

### Post by sisco311 on 2013-10-10
By default, bash will try to execute the file. You need an editor like nano, vi or gedit to open it:
```
vi ./test.txt
```
```
nano ./test.txt
```
```
gedit ./test.txt
```

---

### Post by CRze3wD on 2013-10-10
Thanks, that worked. Now the question, what kind of files would bash open?

---

### Post by heir4c on 2013-10-10
For just reading use **cat** or for long files **less** or **more**
For the first 10 lines use **head** for the last 10 lines use **tail**
For options see the man-pages:
**man** *command*

---

### Post by ajgreeny on 2013-10-10
Or you can make the system use the default application for any file with command **exo-open filename** from the folder containing the file (or use full pathway)

PS:  **xdg-open filename** also will work.

---

