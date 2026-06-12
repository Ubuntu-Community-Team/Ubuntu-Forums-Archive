---
title: "Programming"
date: 2010-11-19
forum: Programming Talk
---

### Post by Drenriza on 2010-11-19
What is the difference in

C
C#
C++ ??

If i was to learn one, which one should it be. Any books/websites you would propose?
Kind Regards

---

### Post by worseisworser on 2010-11-19
> **Drenriza said:**
> What is the difference in

C
C#
C++ ??

If i was to learn one, which one should it be. Any books/websites you would propose?
Kind Regards

Do you have some particular context? What do you want to do or use the language for?

---

### Post by dv3500ea on 2010-11-19
C is a procedural, statically typed, compiled language.
C++ is like C and C++ programs can use C code but it has added object orientation.
C# is a multi paradigm C like language that is compiled to bytecode.

C and C++ are both painful to work with and the object orientation of C++ feels bolted on and bloated. C# has a much nicer object oriented programming model but has worse performance due to the run time library.

If you want to use a C like language, I would recommend [Vala]("http://live.gnome.org/Vala"). It is a language that has similar language features and an almost identical syntax to C# but doesn't have the performance penalty of the run time environment. It compiles down to C code and from there it compiles to native binaries. There is also a programming language called [Genie]("http://live.gnome.org/Genie") which is basically an alternative (python like) syntax to Vala.

Yet another option is the [D]("http://www.digitalmars.com/d/") programming language which is basically what C++ should have been.

If you are developing programs that do not need to be very fast or are IO bound, you should consider the advantages, in terms of increased development speed, of an interpreted language such as [Ruby]("http://www.ruby-lang.org/"), [Python]("http://www.python.org/") or [Perl]("http://www.perl.org/").

---

### Post by Drenriza on 2010-11-19
> **worseisworser said:**
> Do you have some particular context? What do you want to do or use the language for?

That is a good question, maybe one i should have answered from the start ,)

I would like to learn how to make programs, that i can use under the Linux environment. This could be anything, rly.

*Small games
*Monitoring programs
*Installation scripts
Maybe be able to help out in projects under ubuntu like (way out in the future, but i think you get what i mean) Open office (now libery office, or how it is spelled) and so on.

I have always liked to program scripts. I would just like to know what language could take it to the next level when the time comes.

---

### Post by leg on 2010-11-19
> **Drenriza said:**
> That is a good question, maybe one i should have answered from the start ,)

I would like to learn how to make programs, that i can use under the Linux environment. This could be anything, rly.

*Small games
*Monitoring programs
*Installation scripts
Maybe be able to help out in projects under ubuntu like (way out in the future, but i think you get what i mean) Open office (now libery office, or how it is spelled) and so on.

I have always liked to program scripts. I would just like to know what language could take it to the next level when the time comes.C or C++ will be the best for that. Java is similar to C# in that it is compiled to bytecode and (I think) simpler to understand Object Oriented programming than C++. Learn one and then learn others once you have got the hang of it. The first one is generally the hardest to learn as a lot of concepts travel across the languages.

---

### Post by worseisworser on 2010-11-19
> **Drenriza said:**
> That is a good question, maybe one i should have answered from the start ,)

I would like to learn how to make programs, that i can use under the Linux environment. This could be anything, rly.

*Small games
*Monitoring programs
*Installation scripts
Maybe be able to help out in projects under ubuntu like (way out in the future, but i think you get what i mean) Open office (now libery office, or how it is spelled) and so on.

I have always liked to program scripts. I would just like to know what language could take it to the next level when the time comes.

Ok, I would not use C or C++ for small games, monitoring programs and/or installation scripts; it would be something I'd try to avoid as far as possible. C# would be better, but in general you can really use a whole range of *much more* dynamic and flexible languages than C or C++ (and also C# really) for most of these kinds of tasks.

E.g., Python, Ruby, .. etc..

While OpenOffice (LibreOffice) is written in C++, it does support these more dynamic/flexible languages, e.g., Python ( [http://wiki.services.openoffice.org/wiki/Python](http://wiki.services.openoffice.org/wiki/Python) ).

---

### Post by stefangr1 on 2010-11-19
> **dv3500ea said:**
> C and C++ are both painful to work with and the object orientation of C++ feels bolted on and bloated. 
Not everyone is going to agree with that. I like C a lot, and I know many others that like it as well.

> If you want to use a C like language, I would recommend [Vala]("http://live.gnome.org/Vala").  
Many software is developed in C or C++. If you're not satisfied with a program you're using in a Linux environment, you may be able to change it's behaviour if you know these languages.

About four years ago, I asked the same question you're posing now to a good friend of my. He strongly recommended Ruby or Python, and especially warned me against learning C. This resulted in a disaster in one of my first "real" projects: I wanted to get a malfunctioning C library for a USB interface card working. Turns out that you can't use Python to do that...

I've never seen any advantages at all of using python. Usually, most of the development time goes in the conceptual stage. With C, you can make more or less any program you want.

---

### Post by dv3500ea on 2010-11-19
> **stefangr1 said:**
> 
About four years ago, I asked the same question you're posing now to a good friend of my. He strongly recommended Ruby or Python, and especially warned me against learning C. This resulted in a disaster in one of my first "real" projects: I wanted to get a malfunctioning C library for a USB interface card working. Turns out that you can't use Python to do that...


Yes, you should definitely use C for hacking the code of low level libraries, creating hardware drivers, working on the Linux kernel etc..

However, unless specifically stated, I'm not going to assume that someone has the intention of doing this.

Ruby and python are definitely suitable for: 
> 
*Small games
*Monitoring programs
*Installation scripts


---

### Post by Drenriza on 2010-11-19
So C and C++ is good for hardware, drivers, kernel work and such.

And Ruby / python is game development?

---

### Post by Iksf on 2010-11-19
About Vala, basicly afaik its made by GNOME for some integration into GNOME'y things, does Vala work without GNOME, KDE for example, and is it cross platform?

---

### Post by worseisworser on 2010-11-19
> **Drenriza said:**
> So C and C++ is good for hardware, drivers, kernel work and such.

And Ruby / python is game development?

Most big games are written in a combination of several languages; C++ and something like Lua or Python is common.

stefangr1:
Fixing malfunctioning software written in C via Python being impossible is sort of given; the same holds trying to fix malfunctioning software written in Python via C.

---

### Post by Drenriza on 2010-11-19
it's all interesting.

One of the things i do know, is that you need a compiler (C or C++) to turn the codes of text to something the computer can work with. What is the name of one under linux/ubuntu?

And if it is a bit complex to setup, if anyone has a guide on it that would be thumps up.

---

### Post by stefangr1 on 2010-11-19
> **worseisworser said:**
> stefangr1:
Fixing malfunctioning software written in C via Python being impossible is sort of given; the same holds trying to fix malfunctioning software written in Python via C.

Exactly. So if you know that most software in Linux is in C and not in Python, C seems to give the highest probability to enable you te tweak something...

Unfortunately, I had to find out this obvious logic the hard way. I bought this usb experimenting board, to find out that "Linux compatible" implied that they had included a (not very well working) C library...

PS: C is really not meant to write install scripts. That's really where the scripting languages come in handy.

---

### Post by matt_symes on 2010-11-19
Removed. Wrong thread

---

### Post by stefangr1 on 2010-11-19
> **Drenriza said:**
> it's all interesting.

One of the things i do know, is that you need a compiler (C or C++) to turn the codes of text to something the computer can work with. What is the name of one under linux/ubuntu?

And if it is a bit complex to setup, if anyone has a guide on it that would be thumps up.

The compiler is GCC. It should be installed by default, otherwise you can run```
sudo apt-get install build-essential
```to get everyting you need.

By the way, I PM-ed you some tips for books that may be handy.

---

### Post by worseisworser on 2010-11-19
> **stefangr1 said:**
> Exactly. So if you know that most software in Linux is in C and not in Python, C seems to give the highest probability to enable you te tweak something...

Unfortunately, I had to find out this obvious logic the hard way. I bought this usb experimenting board, to find out that "Linux compatible" implied that they had included a (not very well working) C library...

PS: C is really not meant to write install scripts. That's really where the scripting languages come in handy.

Ah, I hooked Lisp ([SBCL]("http://en.wikipedia.org/wiki/Steel_Bank_Common_Lisp")) up to this USB-based thingy:
  [http://www.phidgets.com/products.php?category=0&product_id=1018](http://www.phidgets.com/products.php?category=0&product_id=1018)

It only had a C library, but most languages can "talk with" C based libraries ("talking with" is still not the same thing as fixing of course) via some sort of [FFI]("http://en.wikipedia.org/wiki/Foreign_function_interface") mechanism or library.

In my case I used CFFI; [http://common-lisp.net/project/cffi/](http://common-lisp.net/project/cffi/) . Python can also do FFI.

---

### Post by Arndt on 2010-11-19
> **Drenriza said:**
> it's all interesting.

One of the things i do know, is that you need a compiler (C or C++) to turn the codes of text to something the computer can work with. What is the name of one under linux/ubuntu?

And if it is a bit complex to setup, if anyone has a guide on it that would be thumps up.

I suggest you visit the home pages of several languages (if they have one - otherwise try to find a tutorial) and look at their tutorials, reference manuals, examples and user support forums. Getting adequate support and feeling comfortable with a language may be at least as important as the technical excellence or market dominance of it.

For educational purposes, learning how the computer works, and how the majority of languages work, you can't learn just one. But start with one. If you start with C, you will soon notice that you need to do a lot of things right and know exactly what is happening, then you may want to switch to for example Python. If you start with Python, you may ask yourself what really is happening, or want more speed, then you may want to switch to C.

The common path for most programmers is probably being forced into one programming environment after another, and learning the full span of computer languages that way.

The name of the free compiler for C and C++ is gcc, by the way (invoked as g++ for C++).

---

### Post by Drenriza on 2010-11-19
Thanks for the tips stefangr1.
I have found a decent website with some tutorials, also i work in a building full of C / C++ experts, so they will be a great source of knowledge. 

> 
PS: C is really not meant to write install scripts. That's really where the scripting languages come in handy. 
I have spent some time getting to know, bash & awk. That is what im currently using for this.

Thanks all for the help.

---

### Post by trent.josephsen on 2010-11-19
I like C; it's small, clean and consistent.  I don't know much C++, but I'm under the impression that it suffers from poor design and an enormous userbase mostly composed of first-year CS students.  Objective-C is reportedly better in both aspects, but is not as popular.

Java is bytecode-compiled and enforces object-oriented programming.  This makes some things easy and a lot of things very difficult.  In general, I wouldn't use Java for anything under a thousand lines.  C# is very similar to Java, but devised by Microsoft.  I wouldn't recommend either of them to students or new programmers.

---

### Post by Drenriza on 2011-01-10
How do you use GCC. i cant really seam to find a explanation or howto on it.

---

### Post by worksofcraft on 2011-01-10
> **Drenriza said:**
> How do you use GCC. i cant really seam to find a explanation or howto on it.

It is command line compiler so say your source file is called hello.c then you compile it by typing:
```

gcc hello.c

```

If there are no errors that produces an exe file called "a.out" and you can run that by typing
```

./a.out

```

If you are happy with the way it works you can then rename it to hello if you want. gcc has many other options that you can use. Try:
```

gcc --help

```

;)

---

### Post by Drenriza on 2011-01-10
> **worksofcraft said:**
> It is command line compiler so say your source file is called hello.c then you compile it by typing:
```

gcc hello.c

```If there are no errors that produces an exe file called "a.out" and you can run that by typing
```

./a.out

```If you are happy with the way it works you can then rename it to hello if you want. gcc has many other options that you can use. Try:
```

gcc --help

```;)

Dont i need to state a source and destination?

Like ```
gcc /home/name/Desktop/hello.c /home/name/Desktop/
```

---

### Post by worksofcraft on 2011-01-10
> **Drenriza said:**
> Dont i need to state a source and destination?

Like ```
gcc /home/name/Desktop/hello.c /home/name/Desktop/
```

You can, but if you don't include the path it assumes your current working directory. I like to keep things simple... unless I need the extra bits :)

p.s. also the destination is specified with th -o flag meaning output:
```
gcc /home/name/Desktop/hello.c -o /home/name/Desktop/hello
```

---

### Post by worksofcraft on 2011-01-10
I just wanted to say regarding those languages...

I think of English as being a wonderful language because it has history and it evolved and assimilated many influences from other languages from all over the world :shock:
There are other languages like Esparanto that may well be much more logical and neater, but to me they feel artificial and dead... so anyway that's why I like C++ :popcorn:

---

