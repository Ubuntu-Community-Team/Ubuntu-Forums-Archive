---
title: "C programing"
date: 2006-03-07
forum: Programming Talk
---

### Post by ubugoda on 2006-03-07
Hi there!!
Excuse me cause i am all new in this!!

i wanted to write a program uding the C language i do the followiong:

1-i used gedit to write my programe
2-i saved the file with the extension .c
3-i compiled the programe using the command :  g++ *.c -o *.o
4-i got the new file with the extension *.o

And now how i run it ,,i tried double clicking and also open with bash ,all i get is a blank screen for less than a second!!

Is there a better way to do it??please help

---

### Post by moberry on 2006-03-07
gcc -o <executable name> <file>.c

example:

gcc -o hello hello.c


./hello

---

