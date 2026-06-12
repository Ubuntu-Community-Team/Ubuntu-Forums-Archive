---
title: "Learning C before C++"
date: 2007-08-19
forum: Programming Talk
---

### Post by ablegreen on 2007-08-19
Hi,
I've learned VB...and would like to learn C++, but before I learn C++ is it recommended to learn C first? I think I've read that somewhere (not sure) but if so, why?

Thanks:)

---

### Post by Tuna-Fish on 2007-08-19
It's recommended, because c++ is horribly bloated and cluttered. Learning it as the first pl of it's kind can be quite hard, while c is quite clean and quick to learn. After you have learned c, you can always just extend what you already know with the new features of c++.

---

### Post by Alex Fernandez on 2007-08-19
> **Tuna-Fish said:**
> It's recommended, because c++ is horribly bloated and cluttered. Learning it as the first pl of it's kind can be quite hard, while c is quite clean and quick to learn. After you have learned c, you can always just extend what you already know with the new features of c++.

Except that if you learn C first you will always tend to develop bad C++, its much better to learn it the other way round.

---

### Post by Paul820 on 2007-08-19
[http://www.research.att.com/~bs/learn.html]("http://www.research.att.com/~bs/learn.html")

---

### Post by Wybiral on 2007-08-19
> **Alex Fernandez said:**
> Except that if you learn C first you will always tend to develop bad C++, its much better to learn it the other way round.

Prove it :)

---

### Post by rharriso on 2007-08-19
Ive found that C++ is a rather verbose OOP language. Rather than learning C, a procedural language, learn Java, If you're concerned. Java is a "user friendly" programming language, with a lot of help with the Java ATI at sun.com and the built in Garbage collector makes programming easier, it does however increase runtime. 

Try Java first, to get the OOP basics down, then move on to C++.

---

### Post by pmasiar on 2007-08-19
C++ is object-oriented, which is additional level of abstraction, but is (almost) backward-compatible with C. 

[Bruce Eckel](http://en.wikipedia.org/wiki/Bruce_Eckel) is known C++/Java guru and has good books about either ("Thinking in Java/C++", 2 books :-) ). He is pretty sharing, he sells books (and is good: has multiple editions), but previous version is available as free download. It is not easy reading, and maybe too deep as "learning" book: after you learn basic (what and how), use Eckel's book to gain understanding (why, and with what consequences).

IIRC in his website somewhere is intro course to C, as free prerequisites to his course of C++. Look around (read his blog!), and if you find link, post it here. :-)

That said, in opinion of many, best intro programming language is Python. It has much simpler syntax than C/C++/Java, because it makes compiler and CPU work harder for you. It does so for the price of 20%-50% less execution speed, but you don't care about program speed when learning and your code is wrong and doing anything :-) You can learn also OOP in Python, the C++ version will be much easier to learn after that (and again, C++ will need more details).

C is better as second language, when you understand variables, expressions, loops, and arrays, and of course debugging! Syntax  of Python is like C, but C need **much** more detailed instruction how to handle your code.

In wiki in my sig you find many links to free intro books and training task for Python learners. HTH

---

### Post by pmasiar on 2007-08-19
> **Alex Fernandez said:**
> Except that if you learn C first you will always tend to develop bad C++, its much better to learn it the other way round.

You cannot prove it, and it does not make sense at all: do you want me to believe that people who **wrote** C++ compiler (in C of course, what else), or who learned programming before C++ was even available, will write worse C++ code than random Joe who never even learned C? Don't be ridiculous.

Some programmers will never learn using proper C++, because they are different languages which by chance (or design) share big part of grammar, but syntax is skin deep! These are programmers who will learn idioms and approaches one language, and use them in all other languages they encounter. As saying goes, some programmers can code FORTRAN in any language :-)

Good programmers are not fooled by syntax, learn idioms native for each language, and use them appropriately. Bad programmers don't bother :-D

---

### Post by rbprogrammer on 2007-08-19
> **pmasiar said:**
> 
As saying goes, some programmers can code FORTRAN in any language :-)


lol but can you elaborate?  i dont know FORTRAN, so do i need to know how to code with FORTRAN to understand?

---

### Post by pmasiar on 2007-08-19
> **rbprogrammer said:**
> lol but can you elaborate?  

Original [Fortran](http://en.wikipedia.org/wiki/Fortran)  is more than 50 years old, rather primitive. [examples](http://en.wikipedia.org/wiki/Fortran_code_examples) Joke is, bad programmer will use from any language ony parts which FORTRAN has, writing ugly code, ignoring more advanced facilities and idioms.

---

### Post by Mirrorball on 2007-08-19
> **Alex Fernandez said:**
> Except that if you learn C first you will always tend to develop bad C++, its much better to learn it the other way round.
This is a myth, people are not that stupid. It's perfectly possible to be a good programmer in C++ after learning C first. There is room for both languages in most heads.

---

### Post by Jucato on 2007-08-20
But when you actually don't have the luxury of time or resources in learning both languages, wouldn't it be more reasonable to start with C++ immediately?

It would all depend on the reason for learning and the person learning. If he is only interested in C++, why should he begin learning with C, which he can just learn later on as an added topic if he needs or wants to? Besides, most, if not all, learning material on C++ start with the most basics programming concepts, most of which are both applicable to C and C++, give or take a few C++ idiosyncrasies.

While learning C before C++ doesn't mean you'll be a bad C++ programmer, it would mean that, once you jump to C++, there will be some things that you would need to unlearn in order to follow what would be considered good C++ practice, or in order to adjust to newer concept or to the C++ Standards. This only means that he would be exerting more effort than he would necessarily have to, **IF** his goal is to learn C++ (only) in the first place.

Of course, if he wanted to (and he might probably want to later on), he can always learn C as well. But just as you can learn C++ after you've learn C, you can also learn C after you've learned C++. IMHO, it all depends on where you're starting from, and where you want to go.

---

### Post by pmasiar on 2007-08-20
> **Jucato said:**
> But when you actually don't have the luxury of time or resources in learning both languages, wouldn't it be more reasonable to start with C++ immediately?

If something is worth doing, is it worth doing right?

Of course, as you said, it depends... If you know you have fix this C++ thingie in 2 months, **of course** you dive right to C++. But this is not OP original situation, IIUC.

C++ is used for system-level programming, where correct using of computer resources is critical. It is not for weenies - it is real meat. C is same niche, but even closer to the metal (so it has simpler abstractions). It depends on circumstances, but I believe that you should learn simpler language first: C is **simpler** (IMHO) in this sense than C++.

---

### Post by spyheart on 2007-08-20
I categorize C++ as a "object based" language rather than calling it as  a object oriented language.

This is because, as far as the concepts of object orientation are concerned, a program cannot be written out side a class, where as one can write a program in c++ with out a class too which is not the same case in java making it a "pure object oriented" language.

---

### Post by pmasiar on 2007-08-20
> **spyheart said:**
> as far as the concepts of object orientation are concerned, a program cannot be written out side a class, where as one can write a program in c++ with out a class too which is not the same case in java making it a "pure object oriented" language.

That makes Java "object-obsessed language"

Read for the [famous cautionary tale](http://steve-yegge.blogspot.com/2006/03/execution-in-kingdom-of-nouns.html), in Java-speak. :-)

Zen of python says: "practicality beats purity".

Of course, YMMV.

---

### Post by Sp4cedOut on 2007-08-20
Actually, I think learning C is harder than learning C++.  C++ has features such as stronger type checking, a better string library, and the new operator which are less error prone than the C alternative, thus making it easier for beginners to learn.

The C++ book I read started with basic variables and pointers, loops, if-else, and functions, so I was basically learning C, but with some convenient C++ features.

---

### Post by aks44 on 2007-08-20
I'd recommend one to learn C++ before learning C. IMHO it is way harder to unlearn than to learn, and learning C before C++ will require you to unlearn C (for a moment) in order to grasp the C++ concepts.


> **Alex Fernandez said:**
> Except that if you learn C first you will always tend to develop bad C++, its much better to learn it the other way round.

While this is not an unavoidable and definitive fate, I agree that C programmers who later learn C++ tend to have a period when they just continue to write C code in a C++ environment, not taking into account the structural differences (exception safety is the first thing that comes to mind). This makes for buggy, low quality code.

On the contrary learning C++ before C will allow one to correctly grasp the differences between the two, like "*wtf, I can't rely anymore on this high level stuff I am used to, fortunately I know the concepts behind them so I can do it by myself...*".


> **spyheart said:**
> I categorize C++ as a "object based" language rather than calling it as  a object oriented language.

This is because, as far as the concepts of object orientation are concerned, a program cannot be written out side a class, where as one can write a program in c++ with out a class too which is not the same case in java making it a "pure object oriented" language.

C++ is not an OOL. It is a multi-paradigms language, one of those being OOP.
BTW calling Java a "pure OOL" is a bit exagerated IMHO, knowing that Java doesn't even allow multiple inheritance. ;)

---

### Post by aks44 on 2007-08-20
> **pmasiar said:**
> Read for the [famous cautionary tale](http://steve-yegge.blogspot.com/2006/03/execution-in-kingdom-of-nouns.html), in Java-speak. :-)

Interresting read. Thanks for the link.

---

