---
title: "[SOLVED] avr-gcc includes"
date: 2008-12-18
forum: Programming Talk
---

### Post by Line on 2008-12-18
Hi
We are trying to program a Atmel controller, then this thing comes up..
```
main.c:1:20: error: avr/io.h: No such file or directory

```
In witch directory should we put the .h include files? Tanks

---

### Post by Line on 2008-12-18
forgot to put in the command line ```
a@a-l:~/kontrollerlab$ avr-gcc -mmcu=attiny26 -O0 -c /home/a/kontrollerlab/main.c -o main.o
```

---

### Post by Line on 2008-12-18
Problem solved with the comand
```
avr-gcc -print-file-name=include
```
Then the path pupped up, witch in our case were
/usr/lib/gcc/avr/4.3.0/include
Thanks

---

### Post by lekastor38 on 2009-08-20
Hello !

Nice to see tha tyou had the same problem, but for me it is still not solved.

Can you explained in details what you did ?

I tried to copy all includes installaed by avr-libc from /usr/lib/avr/include, to /usr/lib/gcc/avr/4.3.2/include (directory given by the command : avr-gcc -print-file-name=include) but it doesn't work.

Can you help me ?

Thanks a lot.

---

### Post by knatten on 2010-06-02
Old thread, but is ranks high on Google, so if anyone else stumbles upon this:

Make sure you have the avr-libc package installed.

$ sudo aptitude install avr-libc

---

### Post by randumnumber on 2010-12-10
@knatten thank you very much i am using an arduino and adding that package solved my problem.

---

