---
title: "fun with binary.. c/c++, python,.."
date: 2007-09-13
forum: Programming Talk
---

### Post by bingo__ on 2007-09-13
Hi guys, 
does anybody have an idea on how to convert an int to ieee float without casting, i.e. by bit manipulation... in any language it doesn't matter

---

### Post by aks44 on 2007-09-13
If you really want to do that without using language features (ie. casting) then why don't you read the specification? By the time you finish reading it, you'll be able to write the correct algorithm.

IOW there's no point doing it by hand. Use the tools at your disposal.


EDIT: here is a dumbed down version of what you need: [http://en.wikipedia.org/wiki/IEEE_754](http://en.wikipedia.org/wiki/IEEE_754) (took me 15s to find it: "wikipedia ieee float", first result)

---

### Post by bingo__ on 2007-09-13
the IEEE specs are really confusing.. i wonder if some one has at least some algorithm.. 
I don't wanna use cast :) i wanna have fun

---

### Post by aks44 on 2007-09-13
> **bingo__ said:**
> the IEEE specs are really confusing.. [...] i wanna have fun

Real fun is all about making sense of confusing things. ;)

BTW check the link I just added, it may be easier to understand.

---

### Post by bingo__ on 2007-09-13
great :) 
but how the computer actually make since out of bits.. how does it convert a string of bits to a floating point number? 
how does the cast really work? 
these are the questions i'm really interested in?
any ideas?

---

### Post by pmasiar on 2007-09-13
> **aks44 said:**
>  (took me 15s to find it: "wikipedia ieee float", first result)

install wikipedia into your search engines and save typing 'wikipedia' every time :-)

---

### Post by aks44 on 2007-09-13
> **bingo__ said:**
> but how the computer actually make since out of bits...

Floating point operations are hardwired in the FPU (just as integer operations are in the CPU). A computer *never* makes sense of anything, it just performs blindly what it is programmed / hardwired for.


> **bingo__ said:**
> how does it convert a string of bits to a floating point number? 

A "string of bits" (sic) is not *converted* to a floating point number, it *is* a floating point number that the FPU's transistors know how to handle as is.


> **bingo__ said:**
> how does the cast really work? 

This is quite well explained in the article I linked. ;)

---

### Post by bingo__ on 2007-09-13
ok for example.. 
if you get something like 0x00786234 this might be an int and might be a float.. how do you display it as an int and then as a float?

---

### Post by aks44 on 2007-09-13
> **bingo__ said:**
> if you get something like 0x00786234 this might be an int and might be a float.. how do you display it as an int and then as a float?

```
#include <assert.h>
#include <iostream>

int main()
{
  // make sure both int and float are the same size,
  // or else the reinterpret below won't be safe
  assert(sizeof(int)==sizeof(float));

  int i = 0x00786234;

  // don't cast from int to float, just copy the raw bits
  float f = *reinterpret_cast<float*>(&i);

  std::cout << "As an int: " << i << std::endl;
  std::cout << "As a float: " << f << std::endl;
}

```

```
ysma@ysma:~/bin/test$ g++ -o test test.cpp
ysma@ysma:~/bin/test$ ./test
As an int: 7889460
As a float: 1.10555e-38
ysma@ysma:~/bin/test$
```


Now if you want the "float version" to print the same number as the "int version" then you have to:
- either use a cast, eg. **float f = i;** (implicit cast)
- or do some bit manipulations according to the specification I linked earlier


I personnaly won't bother to dig through the spec in order to cope for your relunctance to research by yourself, I know the basic principles of IEEE floats (fraction, exponent and sign) but most importantly *I don't need to know the details* (and neither do you).

If you insist on doing the bit manipulation by yourself instead of letting the language do it, well, I guess that in less than half an hour you'll get it right with the material provided on Wikipedia.


EDIT: I understand this may sound harsh. But really, my goal is to make you understand that, while it is ok to ask for help to get you started, once you have the material you should do your part of the work rather than waiting to be spoonfed with other people's work (again, no offence intended). Good luck with that Wikipedia reading, it looks quite boring, although quite easier I guess than the original IEEE spec... ;)

---

### Post by aks44 on 2007-09-13
> **pmasiar said:**
> install wikipedia into your search engines and save typing 'wikipedia' every time :-)

I'd rather type "wikipedia" while my hands are on my keyboard, than fetch my mouse and click *twice* to get the same result... ;)

---

### Post by pmasiar on 2007-09-13
ie "please read and explain that docs page for me" is answer of a leach.

Real hacker will ask: " I did read page ... and still cannot understand difference between foo and bar, any further reading suggestions?"

If someone cannot spend hour learnig it, why I should spend 15 minutes of my own time explaining it? Explaing anything to such a leach is waste of time. Please value time of other hackers as much as your own. 

I value time of **real** gurus **more** than my own. :-)

---

### Post by aks44 on 2007-09-13
> **pmasiar said:**
> If someone cannot spend hour learnig it, why I should spend 15 minutes of my own time explaining it?

Moreover, in this case most people will prefer spending those 15mn explaining you why you should learn to learn by yourself, rather than spoonfeeding you with a solution that you won't fully understand (the old "give a man a fish..." thing). :)

---

### Post by pmasiar on 2007-09-13
> **aks44 said:**
> (the old "give a man a fish..." thing). :)

or, as [http://en.wikipedia.org/wiki/Terry_Pratchet](http://en.wikipedia.org/wiki/Terry_Pratchet) famously said: "Give man a fire, you warm him for a day. Set man on fire, and you warm him for the rest of his life!"

If you don't know Terry Pratchet' Discworld books, you are missing a lot. Start with the "Last hero", the illustrated one.

---

### Post by AnRa on 2007-09-13
> **aks44 said:**
> I'd rather type "wikipedia" while my hands are on my keyboard, than fetch my mouse and click *twice* to get the same result... ;)
You may press Ctrl + K to go to the search bar and Ctrl + Up/Down to select the search engine. ;)

---

### Post by aks44 on 2007-09-13
> **AnRa said:**
> You may press Ctrl + K to go to the search bar and Ctrl + Up/Down to select the search engine. ;)

Thanks for the tip, I didn't know that. :)
Too bad Ctrl+Enter doesn't open the results page in a new tab like the [Clusty]("http://clusty.com") bar does (ok, just figured out that Alt+Enter does the trick... woot you just made my day :D).

---

### Post by ibbuntu on 2007-09-17
> **aks44 said:**
> ...
EDIT: here is a dumbed down version of what you need: [http://en.wikipedia.org/wiki/IEEE_754](http://en.wikipedia.org/wiki/IEEE_754) (took me 15s to find it: "wikipedia ieee float", first result)

Took me 15s to find the CTRL+K CTRL+UP/DOWN trick, before I even read the post pointing it out on here, by searching for "firefox search bar keyboard shortcut" ;-)

Made my day too :-)

---

### Post by Ragazzo on 2007-09-17
> **bingo__ said:**
> great :) 
but how the computer actually make since out of bits.. how does it convert a string of bits to a floating point number? 
how does the cast really work? 
these are the questions i'm really interested in?
any ideas?

The processor usually handles the conversion from int to float (at least in C). You can see how it happens in assembly by writing a C program (for example float.c) and compiling it with **gcc -S float.c**. This will give you float.s that contains the assembly code. Then look for instructions starting with an F.

[http://en.wikibooks.org/wiki/X86_Assembly/Floating_Point](http://en.wikibooks.org/wiki/X86_Assembly/Floating_Point)

---

