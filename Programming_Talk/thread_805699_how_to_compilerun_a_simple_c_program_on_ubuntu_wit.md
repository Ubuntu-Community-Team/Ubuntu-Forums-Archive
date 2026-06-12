---
title: "how to compile\run a simple c program on ubuntu without using the terminal"
date: 2008-05-24
forum: Programming Talk
---

### Post by seanbeltrami on 2008-05-24
Hi 
i'm new to programming.
I need to work the following simple program called somma(or any):

#include<stdio.h>
  main()
  {
  int a,b,somma;
  printf("INSERIRE I NUMERI DA SOMMARE");
  scanf("%d%d,&a,&b);
  somma=a+b;
  printf("la somma di a+b e':\n%d \nArrivederci!\n",somma);
  }
I really would not know where to start, i installed gcc (through terminali with gcc apt get install...)
Even better for me at the moment would be having a way not to use the terminal at all,as i did with devc++ or turbo c
where all u had to do was punch a button.
Can anybody help me step by step
Thanks

---

### Post by unutbu on 2008-05-24
Save the program as somma.c.
Then type

```
gcc -o somma somma.c
./somma

```

I suspect there is a GUI that can do this for you, but I'm sorry, I don't know what it is. Perhaps someone else here will know.

---

### Post by brettg on 2008-05-24
hmmm, "Absolute Beginner Talk" is probably not the best forum to post this question.

However, if you install Eclipse you can compile and run C programs "without using the terminal"

---

### Post by barnex on 2008-05-24
Netbeans is a simpeler alternative to eclipse, it's also an IDE for C++ (and java, ...). Just see which one you like best.

---

### Post by Hospadar on 2008-05-24
I also like Kdevelop for C/C++ development.  It's a very nice IDE from KDE, but it runs well under gnome.

---

### Post by whitethorn on 2008-05-24
Hi, you can also try geany out.  It's a really nice small program.   It lets you compile and test run different kinds of programming languages.


[http://geany.uvena.de/](http://geany.uvena.de/)    Link to the homepage

It's available in the repositories.

---

### Post by catanzag on 2008-05-25
I use command line or eclipse, but just to complete the list, also Anjuta should be cited; it is the IDE for C/C++ in gnome, if I'm not wrong.

regards

---

### Post by shankhs on 2008-05-28
u can use anjuta 
download from here:
[http://anjuta.sourceforge.net/downloads](http://anjuta.sourceforge.net/downloads)

---

### Post by iaculallad on 2008-05-28
Before compiling your source codes, you might as well install the "essential" files.

Code:

```
sudo apt-get install build-essential
```

---

### Post by LaRoza on 2008-05-29
See the sticky in the Programming Talk. It has a link to two threads which explain everything.

---

### Post by LaRoza on 2008-05-29
Thread Moved.

---

