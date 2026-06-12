---
title: "glib vs standard C"
date: 2010-02-09
forum: Programming Talk
---

### Post by JDShu on 2010-02-09
I'm writing a game and I needed to use hashtables. A nice person on this forum suggested that I try the hashtables in glib, and I've managed to figure out how to use them. However, I've noticed that glib seems to rename a lot of things in standard C although they appear to be the same thing. My question is, should I change all my variables in the program to the glib format, and if there are any advantages/disadvantages to this.

---

### Post by JDShu on 2010-02-09
Bump as well as another related question.

Can anybody tell me what the relative merits are for strtok and g_strsplit? I want to use strtok because its easier, but since I'm using glib should I stick to g_strsplit?

Very noob, I know, but I tend to learn best by diving into these personal projects :P

---

### Post by hessiess on 2010-02-09
I have very limited knowledge of glib, but from my understanding the glib types are just defined more strictly, smaller to the stdint.h types. They define types which always have a minimum number of bits.

---

### Post by JDShu on 2010-02-09
Thanks hessiess for replying! Hmm so I guess thats what helps portability. I guess I'll try to stick to glib types. However, I think I'll use strtok for now until something fails badly.

---

### Post by saulgoode on 2010-02-09
Many glib functions will return values ("objects") that have been allocated from heap space, whereas hardly any standard library functions will allocate memory for their return values. The glib approach allows greater flexibility in how functions operate but also requires that the programmer eventually free up that allocated memory (your example of strtok versus g_strsplit exemplifies this difference perfectly). 

Also, most of the glib string functions are i18n aware, whereas the standard library string functions assume ASCII encoding (one byte per char).

---

### Post by JDShu on 2010-02-10
Ahh I see. Thanks for the information, it is very helpful! So if I wanted the program to work with other languages I should use glib functions. Hmm better get used to dynamic memory allocation!

---

