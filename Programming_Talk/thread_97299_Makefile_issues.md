---
title: "Makefile issues"
date: 2005-11-30
forum: Programming Talk
---

### Post by roguers79 on 2005-11-30
Hey,
I am having problems with my make files. I type in :$make helloworld. Yet I still get an error "helloworld command not found". I have no problems with makefiles from programs I have downloaded. My make file is as follows:
helloworld: helloworld.c
           gcc -o helloworld helloworld.c
Thanks in advance guys.

---

### Post by Houman on 2005-11-30
hello roguers79;

If you remove the dollar sign ($) and then type your command again i think it will work;
i think youre copying this from a tutorial and when they tell you to do:
```

$somecommand

```

you shouldnt actually type the dollar sign, its just there to tell you you should type it at a terminal;

good luck;
(and it really wouldnt make sense to have a makefile for a one file project, but im assuming youre just experimenting :razz: )

---

### Post by roguers79 on 2005-11-30
I have done it with out the $ sign. I was doing this during class tonight and my professor was as confused as I. I would like to point out this worked before i upgraded from hoary hedghog to breezy.

---

### Post by darth_vector on 2005-12-01
some versions of make are very pedantic about the tab. do you have:

helloworld: helloworld.c
<tab>gcc -o helloworld helloworld.c

in your makefile?

---

### Post by thumper on 2005-12-01
As an aside, the default target with make is the first one it finds, so in your case just typeing ```
make
```should build helloworld.

If you are still having problems, post the contents (I am assuming that they are small).

---

### Post by roguers79 on 2005-12-01
My make file does have the tab there.

---

### Post by darth_vector on 2005-12-01
are you using soft-tabs by any chance? these arent real tabs, they are spaces...

---

### Post by Houman on 2005-12-01
i dont think the tab is the problem, make usually gives a specific error when the tab is missing such as "missing seperator" or something of the sort;

i would suggest you ensure the name of your makefile is Makefile and then just type make at the terminal; (so dont do make helloeworld, just make)

also what happens if you just do :
gcc -o helloworld helloworld.c
at the terminal? (instead of using the makefile)?

regards

---

### Post by toojays on 2005-12-02
My guess is that when you run helloworld, you need to run it as ./helloworld for bash to find it. Try that.

---

### Post by Houman on 2005-12-02
Dear toojays;

he is not running the executable at any point, so that advice is kind of irrelevant;
he just gets an error when he tries to run make;

but yea if he was to run the executable you are right in that he would have to type ./helloworld;

regards;
Houman

---

