---
title: "I'm learning C++... a.out?"
date: 2009-07-27
forum: Programming Talk
---

### Post by Bradj47 on 2009-07-27
My dad bought me a book to learn C++ ([This one to be exact]("http://www.amazon.com/Primer-Plus-5th-Stephen-Prata/dp/0672326973/ref=sr_1_1?ie=UTF8&s=books&qid=1248717926&sr=1-1")) and it says that I can use the g++ command to compile. I use the command...
```

brad@rockstar:~/cplusplus$ g++ myfirst.cpp
brad@rockstar:~/cplusplus$ ls
a.out  myfirst.cpp  myfirst.cpp~

```
It produces an a.out file. I look in the book for what to do with it but it says nothing under the Linux section. When I look under the Unix section it says to run 'a.out' as a command. 
```

brad@rockstar:~/cplusplus$ a.out
bash: a.out: command not found

```
What do I do? :confused:

---

### Post by DGortze380 on 2009-07-27
./a.out

---

### Post by Bradj47 on 2009-07-27
Ah that worked perfectly. Thanks!

---

### Post by credobyte on 2009-07-27
Just a small tip for you:
```
g++ myfirst.cpp -o myfirst
```

Will make an executable called myfirst, not a.out ;)

---

### Post by Bradj47 on 2009-07-27
> **credobyte said:**
> Just a small tip for you:
```
g++ myfirst.cpp -o myfirst
```

Will make an executable called myfirst, not a.out ;)

That might be useful. Thanks a lot :)

Then do I run it by typing './myfirst'?

---

### Post by credobyte on 2009-07-27
> **Bradj47 said:**
> That might be useful. Thanks a lot :)

Then do I run it by typing './myfirst'?

Yap :)

---

### Post by t4thfavor on 2009-07-27
If you get into larger applications, you should look into learning how to use an IDE like eclipse, or anjuta. Both are pretty good, and have lots of cool tools that aid in development.

---

### Post by Bradj47 on 2009-07-27
> **t4thfavor said:**
> If you get into larger applications, you should look into learning how to use an IDE like eclipse, or anjuta. Both are pretty good, and have lots of cool tools that aid in development.

When at first I tried learning Java they told me to get an IDE called NetBeans. Will that work only for Java or does it also support C++? It ran really slow so I'll probably switch to Eclipse or something anyway but I'm just wondering.

---

### Post by Michael.Godawski on 2009-07-27
Moved to PT. ;)

---

### Post by JordyD on 2009-07-27
> **Bradj47 said:**
> When at first I tried learning Java they told me to get an IDE called NetBeans. Will that work only for Java or does it also support C++? It ran really slow so I'll probably switch to Eclipse or something anyway but I'm just wondering.

Netbeans does support C++.

Here's a nice list I ran into a while ago:
[http://en.wikipedia.org/wiki/Comparison_of_integrated_development_environments#C.2FC.2B.2B]("http://en.wikipedia.org/wiki/Comparison_of_integrated_development_environments#C.2FC.2B.2B")

It also lists IDEs for other languages, so you might want to remember it for future reference. 

Good luck.

---

### Post by Bradj47 on 2009-07-27
> **Michael.Godawski said:**
> Moved to PT. ;)

Oh sorry I put it in the wrong section :P

---

### Post by Bradj47 on 2009-07-27
> **JordyD said:**
> Netbeans does support C++.

Here's a nice list I ran into a while ago:
[http://en.wikipedia.org/wiki/Comparison_of_integrated_development_environments#C.2FC.2B.2B]("http://en.wikipedia.org/wiki/Comparison_of_integrated_development_environments#C.2FC.2B.2B")

It also lists IDEs for other languages, so you might want to remember it for future reference. 

Good luck.

Perfect. Thanks for all the support guys. If you're all wondering about my progress I'm just now getting into void functions.

---

### Post by Krupski on 2009-07-27
> **Bradj47 said:**
> My dad bought me a book to learn C++ ([This one to be exact]("http://www.amazon.com/Primer-Plus-5th-Stephen-Prata/dp/0672326973/ref=sr_1_1?ie=UTF8&s=books&qid=1248717926&sr=1-1")) and it says that I can use the g++ command to compile. I use the command...
```

brad@rockstar:~/cplusplus$ g++ myfirst.cpp
brad@rockstar:~/cplusplus$ ls
a.out  myfirst.cpp  myfirst.cpp~

```
It produces an a.out file. I look in the book for what to do with it but it says nothing under the Linux section. When I look under the Unix section it says to run 'a.out' as a command. 
```

brad@rockstar:~/cplusplus$ a.out
bash: a.out: command not found

```
What do I do? :confused:

(1) Since the executable file you made (a.out) is not in your PATH, you need to specifically tell Linux where it is in order to run it by typing "./a.out"

(2) If you put that file into a directory that already IS in your PATH (such as "/usr/bin"), you could run it merely by typing "a.out".

(3) If you compile other programs, they will also be called "a.out" unless you tell the compiler otherwise. A better thing to do is this:

```

g++ program.c -o program

```

That means "compile source code called 'program.c' and output the resulting executable program as 'program'".

Lastly... you should add a few things to your compiler command line... for example have it show you WARNINGS. Try this:

```

g++ -Wall program.c -o program

```

The "-o" means "output this name" and "-Wall" means "Warnings, all".

Have fun!

-- Roger

---

### Post by twright on 2009-07-27
> **Krupski said:**
> 
(2) If you put that file into a directory that already IS in your PATH (such as "/usr/bin"), you could run it merely by typing "a.out".

It is generally not a good idea to put manually compiled programs in /usr/bin/ , instead they belong in either /usr/local/bin/ or /opt/

I would recommend netbeans for c++ on any platform or vim is great if you want to learn at a lower level on the commandline.

---

### Post by Can+~ on 2009-07-27
I would recommend Geany as a first-time coder, as Netbeans/Eclipse+cdt is kinda overwhelming for starters.

---

### Post by Mirge on 2009-07-27
> **Can+~ said:**
> I would recommend Geany as a first-time coder, as Netbeans/Eclipse+cdt is kinda overwhelming for starters.

+1 for Geany.

Another book you may be interested in is [C++ Programming In Easy Steps]("http://www.amazon.com/Programming-Easy-Steps-Mike-McGrath/dp/1840783524/ref=sr_1_1?ie=UTF8&s=books&qid=1248734169&sr=8-1"). It's not as thorough as C++ Primer Plus, but it's still a pretty good read for the price.

---

### Post by Krupski on 2009-07-28
> **twright said:**
> It is generally not a good idea to put manually compiled programs in /usr/bin/ , instead they belong in either /usr/local/bin/ or /opt/

Agreed. What I said was just an example... I didn't tell him to actually put his code there.

---

### Post by twright on 2009-07-28
> **Krupski said:**
> Agreed. What I said was just an example... I didn't tell him to actually put his code there.
Just making sure and spreading the Unixy wisdom :KS.

---

### Post by Java Geek on 2009-07-28
+10 for Geany! =D

---

### Post by lisati on 2009-07-28
Suggestion: I'd recommend giving your C++ source files a .cc or .cpp extension instead of .c, this can help distinguish between c++ and c source files. It's more of a "style" thing than an absolute requirement.

---

