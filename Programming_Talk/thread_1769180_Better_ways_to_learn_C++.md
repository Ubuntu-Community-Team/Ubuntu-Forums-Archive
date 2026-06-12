---
title: "Better ways to learn C++"
date: 2011-05-27
forum: Programming Talk
---

### Post by rpmp on 2011-05-27
Im a beginer to learning C++ i learned some stuff but the more i read my tutorial the more i realize it isnt for complete beginers like and would like to know of a simpler C++ tutorial.

---

### Post by doas777 on 2011-05-27
it sounds like you are less interested in learning C++, as you are in learning TO program (coincidentally in C++).

my recommendation is when you learn a new language, use a tutorial and web resources, but to learn TO program, you are likely better off taking a class. unless you are in a traditional academic environment, the choice of language is far less important.

sry that doesn't directly answer your question, but I hope it helps you achieve your goal.

---

### Post by rpmp on 2011-05-27
im learning C++ to learn to program so i can learn to make games with C++.

---

### Post by ApOgEEs on 2011-05-27
> **rpmp said:**
> im learning C++ to learn to program so i can learn to make games with C++.

Go ahead... you can do it! 

Here's my tips:

1. Start small by re-writing small games source code in C++ you can find on the internet. Search for game code which match your interest, related to what you dream to make. 

2. Do not copy-paste. By re-writing, you will see why each lines are coded. When you mistyped, you will notice what will happen. You are going through each characters of the code. You can also try to change the variable name when you have confidence. After you have successfully compile your first re-wrote code, you may have already learn something. Remember to keep backup files to revert when you passed each success stages.

3. After that, try to change the small program. The easiest part would be changing some constants. Then, learn what is changing when you change something. For games, mostly you would like to change things related to image and graphics. Just do it and see what happens after you compile. 

4. Add new features. You can add new features to your small re-wrote apps. Use your imagination. When you stuck, just go to sleep and dream more.

5. By the time you pass this stage, I bet you already learn how to write your own game program in C++. Go ahead, write a new one... Have fun, and share the codes with the spirit of open source.

---

### Post by JupiterV2 on 2011-05-27
> **ApOgEEs said:**
> 2. Do not copy-paste...

100% agree. Type everything out yourself.

---

### Post by nvteighen on 2011-05-28
> **rpmp said:**
> im learning C++ to learn to program so i can learn to make games with C++.

That is part of the problem. But first let me answer your question, before anything else.

1) What tutorial are you using? IMO, the best one out there is this one: [http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/) It's updated, very clear and teaches things in a quite reasonable order.

But IMO, when learning any programming language, you should use tutorials as guides. Whenever you wonder how to do X, google for it and even if you don't understand it yet, you'll eventually get familiar with terms and stuff. You'll even learn how to recognize languages visually. 

And always **try** things. Learning how to crash a program can be very enlightening :) Programming is a craft, and 90% is learned by doing things, even the most basic ones. Don't worry if all you can do is a simple calculator; that's certainly teaching you something.

2) Now onto C++ as first language.

C++ is a fairly complex language. IMO, the best example of a badly designed language, but let's leave that aside (there are zillions of post here by CptPicard, myself and others exposing some reasons).

The problem with using C++ as first language is that, by design, it is both low-level and high-level. On one hand it gives you pointers, stack/heap distinction, very basic data types. etc.; on the other, it gives you classes, overloading, a high-level standard library, a rudimentary metaprogramming system, etc. But those high-level features are implemented on top of those low-level ones, in order to keep things more or less compatible. This means that the perception of high abstraction level in C++ is quite lower than what you get in other high-level languages (Lisp, Python, Perl, Ruby, JavaScript, Java, a long etc.).

Is this a bad thing? Well, not exactly. Objective-C does it too and there you have Mac OS X written in it :P Win95 was written in C++ ;) Jokes aside, the problem with C++ is the how, rather than the what. But I promised I wouldn't get into my personal opinions and focus on your problem.

The issue of any low-level language as a first language is that it makes you learn quite complex stuff that's actually secondary to what programming really is. Programming is about solving computable programs and using a computer for that is just a convenient formality. But, of course, 99% of programming is done in computers (1%, in sheets of paper or classroom chalkboards), so it's obvious that there has to be a way to program a computer. Making a computer run is also a computable problem you can solve by programming and that's where low-level programming came in.

Low-level programming is a very specific kind of programming. High-level programming is actually about the general ideas that drive all programming (including low-level). For example, in C and C++ automatic variables are stored in a stack, but a stack is a high-level concept, completely independent of computers (you can have a stack of coins).

IMO, this makes C and C++ very bad choices as first languages. Well, Forth and ASM would be worse, of course. But specifically, C++ makes it worse than C because it's very complex in itself because it attempts to mix high-level and low-level programming... There's someone in these forums that once proposed to teach C++ starting from the STL (the higher-level parts), but I don't know if that'd be possible. And if you only taught the low-level parts, you'd be teaching C...

All of this doesn't mean you're "doing it wrong". Everyone's different and C++ may suit you well. I insist on what I said in the first "part" of this post: learn by experience. The only thing I suggest you is that after learning C++, you keep learning other and different programming languages, even if you don't use them for anything serious. That will give you more insight to take your own decisions and form your own opinions.

---

### Post by Petrolea on 2011-05-28
> **nvteighen said:**
> That is part of the problem. But first let me answer your question, before anything else.

1) What tutorial are you using? IMO, the best one out there is this one: [http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/) It's updated, very clear and teaches things in a quite reasonable order.

But IMO, when learning any programming language, you should use tutorials as guides. Whenever you wonder how to do X, google for it and even if you don't understand it yet, you'll eventually get familiar with terms and stuff. You'll even learn how to recognize languages visually. 

And always **try** things. Learning how to crash a program can be very enlightening :) Programming is a craft, and 90% is learned by doing things, even the most basic ones. Don't worry if all you can do is a simple calculator; that's certainly teaching you something.

2) Now onto C++ as first language.

C++ is a fairly complex language. IMO, the best example of a badly designed language, but let's leave that aside (there are zillions of post here by CptPicard, myself and others exposing some reasons).

The problem with using C++ as first language is that, by design, it is both low-level and high-level. On one hand it gives you pointers, stack/heap distinction, very basic data types. etc.; on the other, it gives you classes, overloading, a high-level standard library, a rudimentary metaprogramming system, etc. But those high-level features are implemented on top of those low-level ones, in order to keep things more or less compatible. This means that the perception of high abstraction level in C++ is quite lower than what you get in other high-level languages (Lisp, Python, Perl, Ruby, JavaScript, Java, a long etc.).

Is this a bad thing? Well, not exactly. Objective-C does it too and there you have Mac OS X written in it :P Win95 was written in C++ ;) Jokes aside, the problem with C++ is the how, rather than the what. But I promised I wouldn't get into my personal opinions and focus on your problem.

The issue of any low-level language as a first language is that it makes you learn quite complex stuff that's actually secondary to what programming really is. Programming is about solving computable programs and using a computer for that is just a convenient formality. But, of course, 99% of programming is done in computers (1%, in sheets of paper or classroom chalkboards), so it's obvious that there has to be a way to program a computer. Making a computer run is also a computable problem you can solve by programming and that's where low-level programming came in.

Low-level programming is a very specific kind of programming. High-level programming is actually about the general ideas that drive all programming (including low-level). For example, in C and C++ automatic variables are stored in a stack, but a stack is a high-level concept, completely independent of computers (you can have a stack of coins).

IMO, this makes C and C++ very bad choices as first languages. Well, Forth and ASM would be worse, of course. But specifically, C++ makes it worse than C because it's very complex in itself because it attempts to mix high-level and low-level programming... There's someone in these forums that once proposed to teach C++ starting from the STL (the higher-level parts), but I don't know if that'd be possible. And if you only taught the low-level parts, you'd be teaching C...

All of this doesn't mean you're "doing it wrong". Everyone's different and C++ may suit you well. I insist on what I said in the first "part" of this post: learn by experience. The only thing I suggest you is that after learning C++, you keep learning other and different programming languages, even if you don't use them for anything serious. That will give you more insight to take your own decisions and form your own opinions.

Must agree to this post and all of those before me. Seriously, don't start with such a complex language. If you won't understand your code you will never be a great programmer (and by this I mean copy-pasting parts of code). 

I started with C++ too, back then I thought it was the only programming language in the world. I noticed I can't do much if I don't understand the code, I didn't know how to fix errors, make the code better or anything. I believe things like that might happen to you also.

To your primary question: there are lot's of tutorials on internet about C++. BUT, many of them are just badly written C code that runs with C++ compilers also. And some tutorials will teach you bad programming habits like using 'system("pause");' which is incredibly stupid if you ask me. Some tutorials will tell you to use functions like clrscr() which won't work on all compilers. If you have to learn C++, learn it from GOOD tutorials.

---

### Post by Sophont on 2011-05-28
Programming in general and programming in a particular language is not exactly the same skill.

If you understand how to program you can pick up another language in a very short time.

C or C++ will probably make this harder for you than need be.
Also you don't necessarily need to learn C/C++ to program games.
Though it helps a lot if you want to do graphics intensive stuff.
But even then you'll probably be better off to do a lot of the framework in a more productive language like Python and then add C/C++ modules where you really need the speed or low level access.

Programming is about how to translate real world objects and their interactions into something the computer understands.

Most languages have the same building blocks to do so. Variables, expressions, loops, if/else branching, functions, etc..

The language you use to learn those fundamentals doesn't matter very much.
C/C++ gets you closer to the metal - but also more rope to hang you with - a lot.
It will also take much more boiler plate lines to get useful programs done than it would take in Python.

---

### Post by Oliphant on 2011-05-28
The New Boston has some good tutorials on C++ amongst other languages.  

[www.thenewboston.com]("http://thenewboston.com")

---

### Post by ratcheer on 2011-05-28
My recommendation would be to first tackle a friendlier language with which to learn object-oriented design and programming practices before taking on a language behemoth like C++. My first recommendation would be to try **Smalltalk**, but if that doesn't suit you, then **Ruby** or **Python**. But maybe that's just me.

Tim

---

### Post by JupiterV2 on 2011-05-28
My learning path was BASIC -> C++ -> C -> Java. 

I never enjoyed BASIC. I started when I was 14 (almost 20 years ago...) and the only thing I feel I got out of it was the basic logic (if/else, loops, etc). Many years later I decided to take another tackle at programming and tried C++, which was a major jump in difficulty from BASIC. I finally decided to take a step down (literally) and learn C first before moving back to C++. I really enjoyed C and would sooner program in that language over C++. After several years of self-learning I decided I was ready to fully learn a second language. Rather than turn back to C++ I elected to go with Java. Java may not be perfect, and I do have some reservations about the "openness" of it but I would describe it as "C++ done better." I wish, in many ways, that I'd started with a language like Java (It never existed when I started programming). Python, Tcl, Perl, Lisp, etc would have been just fine too.

A word of caution: If you come from the "Microsoft" world, don't get hung up on building executable binaries like I did. I felt for many years that if you couldn't produce an .exe file, it wasn't a true program. What a load of...-but I digress. Don't shy from the other "scripting", interpreted, languages. You will learn so much more in a shorter period of time than taking the round-about way I did. I don't regret the path I choose because, well, it could not have happened any other way. I just wish that I knew then what I know now. =)

P.S. I also feel like I should give a special shout out to Tcl. It's a very neat language and I really enjoyed tinkering with it. I think it's a sadly neglected language.

---

