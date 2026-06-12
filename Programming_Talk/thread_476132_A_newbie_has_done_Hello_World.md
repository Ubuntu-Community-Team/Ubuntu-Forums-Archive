---
title: "A newbie has done Hello World"
date: 2007-06-16
forum: Programming Talk
---

### Post by mocqueanh on 2007-06-16
Hi, i've come to Programming. My job isnt relate to programming, but i like it and want to learn for myself.

I dont know anything of programming, i've bought some books that teach myself in C (beginning C forNovice).

But unfortunately, all my books i have only teach me program on Windows, not on Linux, or it only say: use GCC in Linux to program C. I've done the very first practice for programming newbie: Hello World, but done in Windows

I want to learn programing both on Windows and Linux, can you recommend me some books teach me C on Linux, free or shareware, no problem, i can buy ;)

---

### Post by danhm on 2007-06-16
The langauge is the same, regardless of the operating system. Go and get yourself an C IDE (see the "what's your favorite IDE" thread, or just get Geany, Anjuta or Code::Blocks) and you'll be all set. Alternatively, you can just write up your programs in Gedit/Kate/any text editor, and then type **gcc main.c -o helloworld** in your terminal, and then run it with **./helloworld**, replacing "main.c" with your source file's name and "helloworld" with whatever you'd like the binary to be called. Should you move on to C++, replace gcc with g++.



Good luck learning!

---

### Post by mocqueanh on 2007-06-16
Yeah, thank you

---

### Post by pmasiar on 2007-06-16
> **mocqueanh said:**
> Hi, i've come to Programming. My job isnt relate to programming, but i like it and want to learn for myself.

In opinion of many, Python is better language for a programmer beginner than C, and is multiplatform too. In wiki in my sig you have plenty of links to get you started.

---

### Post by RadenMuaz on 2007-06-17
You must learn C because you already buy some C books or else it will be a waste.
Anyway I have learned Python last year and created games with Pygame.

Preferrable languages for beginners: Ruby or Python.

---

### Post by ankursethi on 2007-06-17
You can use gcc on Windows using MinGW.

---

### Post by Lux Perpetua on 2007-06-17
> **pmasiar said:**
> In opinion of many, Python is better language for a programmer beginner than C, and is multiplatform too. In wiki in my sig you have plenty of links to get you started.C is not a bad language for a beginner. There's nothing wrong with wanting to learn C.

---

### Post by Paul820 on 2007-06-17
I don't know why people keep saying C and C++ are difficult languages for first time programmers. C++ is my first programming language, and i am doing fine. If you work hard at it and do plenty of reading, practicing ( most important, write code ), and study code that others have done it isn't that bad. There are always forums if you get stuck. Where was python when C was first introduced? People managed to write C back then without first learning python, and still do.

---

### Post by CptPicard on 2007-06-17
Just because people built stuff out of sticks and stones in the olden days, doesn't mean we still have to :)

I am firmly in the camp of those who believe the added complexity of manual memory management and pointers and the much harder debugging of C/C++ is not worth the effort for a beginner, and just hinders the development of the more immediately useful programmers' skills you need to get something done so you can get your instant gratification that keeps you wanting for more.

Moreover, if you want classes so you can develop your OO design skills you should go for Java instead of C++, which requires a lot of best-practices style knowledge to actually not get hung by "all the rope you need" that comes with the language. My favourite example is the intricacies with returning large objects from factory methods that is trivial in Java but requires all sorts of auto_ptr reference counting in C++. All of this is unneccessary for a beginner to bother with.

I did start with BASIC, Pascal and C on DOS, but since the early 90s, software complexity on top of the hardware has increased substantially, meaning that doing things in a low level language is much more of a pain as you aren't running straight on top of the CPU anymore, but need all sorts of APIs which, IMO, are far cleaner in Java/Python/whatever else. It was cool to get a 3D cube rotation running on DOS in some VGA mode and a simple line-drawing routine, but as these days there just are layers and layers of OS and user-space libraries on top of the hardware, I see less point in C every day...

---

### Post by Smygis on 2007-06-17
My first language was C and then C++, And a can defenitly say that i think Python is a better language for beginners. You spend more time learning programming and less time fighting the syntax.

---

### Post by Lux Perpetua on 2007-06-17
> **danhm said:**
> The langauge is the same, regardless of the operating system. Go and get yourself an C IDE (see the "what's your favorite IDE" thread, or just get Geany, Anjuta or Code::Blocks) and you'll be all set. Alternatively, you can just write up your programs in Gedit/Kate/any text editor, and then type **gcc main.c -o helloworld** in your terminal, and then run it with **./helloworld**, replacing "main.c" with your source file's name and "helloworld" with whatever you'd like the binary to be called. Should you move on to C++, replace gcc with g++.I think it's a good idea *not* to use an IDE when you're starting with a language. Once you have the basics down, you can pick up any IDE. On the other hand, if you start out with an IDE, then the language and the IDE will be connected in your mind, and you'll be less flexible. It's better to start out doing things yourself rather than having things done for you. In other programming forums, I often see questions like "How do I make a binary tree in Borland C++ builder?" The poster doesn't know where C++ ends and the IDE begins, so he lumps the two together.

---

### Post by rbprogrammer on 2007-06-17
> **CptPicard said:**
> 
I am firmly in the camp of those who believe the added complexity of manual memory management and pointers and the much harder debugging of C/C++ is not worth the effort for a beginner, and just hinders the development of the more immediately useful programmers' skills you need to get something done so you can get your instant gratification that keeps you wanting for more.


i understand that pointers are not the greatest thing for a beginner, but who's to say that a beginner has to use pointers?  a program that does not use pointers can do everything that programs with pointers can do.  although it may not be the most efficient or fastest, but as a beginner, i dont think speed and efficiency is really a problem.

i started out learning c/c++ as my first language(s), and i did not use pointers till much later when i got my bearings on the concept of programming.

i'm just saying in my opinion, that c/c++ (without pointers) as a first language is just as good as python.

---

### Post by pmasiar on 2007-06-17
> **RadenMuaz said:**
> You must learn C because you already buy some C books or else it will be a waste.
.

This concept is called "throw away good money after bad". :-) Widely used BTW

C was not good choice for a beginner. Keep the books - you may want to learn C later. For now, get Python books (printed or free online - good links are in wiki in my sig). Don't waste time on C now, C is *not* for beginners, but for kernel hackers. 

Get Python, pygame, and have some fun!

---

### Post by CptPicard on 2007-06-17
> **rbprogrammer said:**
> i understand that pointers are not the greatest thing for a beginner, but who's to say that a beginner has to use pointers?  a program that does not use pointers can do everything that programs with pointers can do.  although it may not be the most efficient or fastest, but as a beginner, i dont think speed and efficiency is really a problem.

An interesting suggestion... considering that originally I came from C to C++ and probably never really completely got into the C++ way of doing things which I hear does indeed discourage the use of raw pointers, it's well possible that I love pointer arithmetic a bit too much in my thinking. It's just that all you need to do is to, say, pass an array, and you already need to deal with the idea...

A major case for use of pointers is of course the avoidance of passing huge values on stack, and I feel you do indeed run into that quite soon (I have). Associated with this, I am also personally really allergic to copy constructors that shift massive amounts of data around, and try to write them into something a bit fancier -- an art form in itself :) and then related to this there is of course the reference, which is a pointer-like construct that I found tough to comprehend 10 years ago when I first met C++... then someone told me it's just a masqueraded pointer ;) Something as simple as passing something (value/ptr/reference) into a function and writing the "=" operator can require a lot of thought and insight into what is going on compared to, say, Python... 

And if you want to be really clean in your code and further avoid pointers, you'll want to be using STL and Boost... then you need to deal with templates ;)

Ok, this was a bit of stream of consciousness, sorry, but you'll catch my drift...

---

