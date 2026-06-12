---
title: "help regarding c programming"
date: 2008-02-22
forum: Programming Talk
---

### Post by phanther on 2008-02-22
hi,

i've just started out doing c programs in ubuntu, but i am facing problems while executing them.the compiler is not detecting any of the header files i.e <stdio.h>, <conio.h> n so on.i want to know if there is any particular package to be installed for this particular problem or is there any alternative.

thanx in advance.:)

---

### Post by lnostdal on 2008-02-22
```
sudo aptitude install build-essential
```
 
..conio.h is an old non-standrad Borland header.. a similar library is ncurses

```

sudo aptitude install libncurses5-dev

```

---

### Post by Zwack on 2008-02-22
I think you might want build-eesentials to include everything you might need...

Look in /usr/include for them andif they're not there then you still need soemthing...

ls -l /usr/include/stdio.h

```
$ ls -l /usr/include/stdio.h
-rw-r--r-- 1 root root 28517 2007-10-24 17:42 /usr/include/stdio.h

```

Z.

---

### Post by pmasiar on 2008-02-22
Sticky explain this issue, and many more. Just read it. Answer is 3 mouseclicks away :-)

---

### Post by phanther on 2008-02-22
@Inostdal n Zwack

thnx for the replies, i got the answer.i had to install build-essential from the ubuntu installation cd because terminal was giving an error when i gave the command "sudo aptitude build-essential".it said "unknown command build-essential".So i had to search n install it from the cd.

thnx zwack, the path u were mentioning wasnt present at first, but its there now after installing build-essential.

One more thing, Inostdal u were mentioning about ncurses, but when i tried to install it some packages got installed n some didnt, it was saying tht some of the packages were not being installed(it gave a big list).

finally when i put tht header file(the way i gave was #include<ncurses.h>, i suppose its right if not correct me), it did not detect the header file

---

### Post by lnostdal on 2008-02-22
ah, that should have been ```
sudo aptitude install build-essential
```

> 
One more thing, Inostdal u were mentioning about ncurses, but when i tried to install it some packages got installed n some didnt, it was saying tht some of the packages were not being installed(it gave a big list).


don't worry about it .. it is just informing you about new versions of packages you might be interested in

> 
finally when i put tht header file(the way i gave was #include<ncurses.h>, i suppose its right if not correct me), it did not detect the header file


i don't think you understand .. you can't just add that to the code that previously used *conio.h* etc. and expect it to work by itself .. you must port the code/software ( [http://en.wikipedia.org/wiki/Porting](http://en.wikipedia.org/wiki/Porting) ) since the original authors have chosen to write code that is non-portable

---

