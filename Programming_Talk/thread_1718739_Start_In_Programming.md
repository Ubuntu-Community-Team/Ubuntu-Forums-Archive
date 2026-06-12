---
title: "Start In Programming"
date: 2011-03-31
forum: Programming Talk
---

### Post by khaos1985 on 2011-03-31
[FONT=Arial Black][COLOR=DarkRed]**I've Been wanting to get in to coding and programming but don't know much about it so I guess my Question is. "What is the best way to start and easiest to learn at first? " Cuz I wanna start with Unix based code and work in to other forms.  I ain't a total newb and pick stuff up quick. **[/COLOR][/FONT]

---

### Post by patryk77 on 2011-03-31
I'd recommend C++ and [reading the stickies ;)](http://ubuntuforums.org/showthread.php?t=333867)

---

### Post by stchman on 2011-03-31
Many colleges and universities have switched from C/C++ to Java as Java promotes better programming practices.

The choice is yours.

---

### Post by khaos1985 on 2011-03-31
Thanks for the suggestion as well as what kind of stuff would be better to start with, like simple type programs or just random stuff?  And Any suggestions on what to start with maybe?

---

### Post by Some Penguin on 2011-03-31
Read the stickies.

---

### Post by matt_symes on 2011-03-31
> And Any suggestions on what to start with maybe?

Python. 100 different answers ?

---

### Post by slavik on 2011-03-31
read the stickies.

---

### Post by kurum! on 2011-03-31
> **khaos1985 said:**
> [FONT=Arial Black][COLOR=DarkRed]**  I ain't a total newb and pick stuff up quick. **[/COLOR][/FONT]

No need to search any more. see [here]("http://www.ruby-doc.org/docs/ProgrammingRuby/")

---

### Post by slavik on 2011-04-01
> **stchman said:**
> Many colleges and universities have switched from C/C++ to Java as Java promotes better programming practices.

The choice is yours.
Not to start an argument, but I see java code that goes OOM all the time. As well as threads that don't finish in a web app.

Java apps are responsible for more unavailability than C based front-end apps (web servers)

---

### Post by nvteighen on 2011-04-01
What you need is a language that helps you to learn the general concepts of programming while also learning the specific aspects of the chosen language. IMO, if you start with a language that's simpler (not "dumber" :)) so that it doesn't come in your way, you'll have an easier time learning the general stuff... which applies to any language and any kind of project. After that, you can learn the specifics that you need or want.

I'd recommend any of the dynamic high-level programming languages. "High-level" is short for "High level of abstraction" and means that the language hides how the machine does everything so that you concentrate in what you want to be done. So, e.g. if you want a string "Hello, " concatenated with "world!", these languages won't make you bother about allocating the needed space in memory or whether those strings are stored in the .data section or are stored in the call stack... A language like Python or Perl will allow you to concatenate two strings to create a new one, without any additional "hassle". The opposite of "high-level" is "low-level" (of course). Low-level languages expect you to do a lot of work to control some internal aspects of the computer; obviously, you gain a lot of control, but at the cost of having to write a lot of auxiliary code. Not that low-level is worse: it's meant for system or efficiency-critical programming... IMO, not quite what a beginner really needs because it distracts from learning stuff that's general to all languages and all aspects of programming.

"Dynamic" is referred to the type-discipline. Maybe you won't get it now, but I'll try to explain it the best I can. Programming languages classify into types the data the program will manage. Dynamic typing means that the language deduces the type of things by what they do during runtime and not by any other means. And this to have generic functions that work with different types of data but without having to write a different version for each of them. Static typing is the opposite and has the programmer set the type of everything in the code; this is something that allows way better optimization before the program even starts, but it leads to a very rigid coding style... not sure if you've ever heard about one classic complaint against Java: that it's too bureaucratic... well, static typing is like that, though it's necessary (as bureaucracy is also necessary as nasty as we all think it is).

IMO, Python or Perl are good options. Then, there's Scheme, which is a Lisp dialect, which has the advantage of being the language used in the great and popular MIT SICP books and videos... but the big disadvantage of the massive amount of incompatible implementations.

But don't forget to read the stickies.

---

### Post by matt_symes on 2011-04-01
Hi

> **nvteighen said:**
> What you need is a language that helps you to learn the general concepts of programming while also learning the specific aspects of the chosen language. IMO, if you start with a language that's simpler (not "dumber" :)) so that it doesn't come in your way, you'll have an easier time learning the general stuff... which applies to any language and any kind of project. After that, you can learn the specifics that you need or want.

I'd recommend any of the dynamic high-level programming languages. "High-level" is short for "High level of abstraction" and means that the language hides how the machine does everything so that you concentrate in what you want to be done. So, e.g. if you want a string "Hello, " concatenated with "world!", these languages won't make you bother about allocating the needed space in memory or whether those strings are stored in the .data section or are stored in the call stack... A language like Python or Perl will allow you to concatenate two strings to create a new one, without any additional "hassle". The opposite of "high-level" is "low-level" (of course). Low-level languages expect you to do a lot of work to control some internal aspects of the computer; obviously, you gain a lot of control, but at the cost of having to write a lot of auxiliary code. Not that low-level is worse: it's meant for system or efficiency-critical programming... IMO, not quite what a beginner really needs because it distracts from learning stuff that's general to all languages and all aspects of programming.

"Dynamic" is referred to the type-discipline. Maybe you won't get it now, but I'll try to explain it the best I can. Programming languages classify into types the data the program will manage. Dynamic typing means that the language deduces the type of things by what they do during runtime and not by any other means. And this to have generic functions that work with different types of data but without having to write a different version for each of them. Static typing is the opposite and has the programmer set the type of everything in the code; this is something that allows way better optimization before the program even starts, but it leads to a very rigid coding style... not sure if you've ever heard about one classic complaint against Java: that it's too bureaucratic... well, static typing is like that, though it's necessary (as bureaucracy is also necessary as nasty as we all think it is).

IMO, Python or Perl are good options. Then, there's Scheme, which is a Lisp dialect, which has the advantage of being the language used in the great and popular MIT SICP books and videos... but the big disadvantage of the massive amount of incompatible implementations.

But don't forget to read the stickies.

:popcorn: Listen to this reply.

Kind regards

---

### Post by simeon87 on 2011-04-01
Don't start with Java, it cultivates a mindset that everything is an object which is hard to unlearn afterwards. I suggest starting with Python.

---

### Post by khaos1985 on 2011-04-01
Thank you for the well stated replies so really my best bet is to start with is python and read all the stickies right ok got it thank you lots and I will let you all know how it goes

---

### Post by slavik on 2011-04-02
> **nvteighen said:**
> What you need is a language that helps you to learn the general concepts of programming while also learning the specific aspects of the chosen language. IMO, if you start with a language that's simpler (not "dumber" :)) so that it doesn't come in your way, you'll have an easier time learning the general stuff... which applies to any language and any kind of project. After that, you can learn the specifics that you need or want.

I'd recommend any of the dynamic high-level programming languages. "High-level" is short for "High level of abstraction" and means that the language hides how the machine does everything so that you concentrate in what you want to be done. So, e.g. if you want a string "Hello, " concatenated with "world!", these languages won't make you bother about allocating the needed space in memory or whether those strings are stored in the .data section or are stored in the call stack... A language like Python or Perl will allow you to concatenate two strings to create a new one, without any additional "hassle". The opposite of "high-level" is "low-level" (of course). Low-level languages expect you to do a lot of work to control some internal aspects of the computer; obviously, you gain a lot of control, but at the cost of having to write a lot of auxiliary code. Not that low-level is worse: it's meant for system or efficiency-critical programming... IMO, not quite what a beginner really needs because it distracts from learning stuff that's general to all languages and all aspects of programming.

"Dynamic" is referred to the type-discipline. Maybe you won't get it now, but I'll try to explain it the best I can. Programming languages classify into types the data the program will manage. Dynamic typing means that the language deduces the type of things by what they do during runtime and not by any other means. And this to have generic functions that work with different types of data but without having to write a different version for each of them. Static typing is the opposite and has the programmer set the type of everything in the code; this is something that allows way better optimization before the program even starts, but it leads to a very rigid coding style... not sure if you've ever heard about one classic complaint against Java: that it's too bureaucratic... well, static typing is like that, though it's necessary (as bureaucracy is also necessary as nasty as we all think it is).

IMO, Python or Perl are good options. Then, there's Scheme, which is a Lisp dialect, which has the advantage of being the language used in the great and popular MIT SICP books and videos... but the big disadvantage of the massive amount of incompatible implementations.

But don't forget to read the stickies.
I was reading the first paragraph and though "definitely going to say Python." Then I read the second paragraph and though "yeap, I was right." Then I saw Perl listed ... wtf?! :P

Guess those IRC chats are finally turning you around. :P

---

### Post by TheCompBoy on 2011-04-02
If you whant to start programing and you have no idea where to start.. There is guides all over internet if you not going to buy books and such i recomend C++ it has guides everywhere i started with a youtube guide when i learned C++ but then i started with Java and this language has like no guides on the internet atleast not what i found and you can buy books to Java its easier than C++ too :) But for start i recomend C++ realy..

---

### Post by dazman19 on 2011-04-04
I went back to university, and started with "C".
The main thing i learned was programming was about 3 main things:
1) Sequence
2) Selection
3) Repetition

Learned hello world through to towers of hanoi, then on to writing my own text editor, It was pretty cool. 

Learn about arrays, variables, basic structures the basic types 
int, char, float 

Then get into loops, (for, while and do), and switches (if & switch case) 

and then onto more advanced types:
arrays and structures.

After you got this you need to learn about pointers, and memory allocation. malloc and free.

Finally learn about recursion.

Once you have mastered the basics of C, you can go in any direction. 

I went on to learn:
Java
C++
Haskell
PHP

Python is also another one worth learning. But if you understand the basics i listed above, then you can move onto Object Oriented Programming.

---

### Post by jrd2 on 2011-04-04
I've been programming for over 5 years and have used various different languages. For Linux My recommendation is python. It's easy to learn, it's common, and there are plenty of resources available.

---

### Post by cgroza on 2011-04-04
Learning C/C++ gives you a boost in learning other languages because many inherit a great deal of their syntax. And their concepts are easy transferable too. Me, after C++, I can learn a new language in 3 days.
Of course, to get deep into that language standard library you need a real project.

---

### Post by stchman on 2011-04-05
> **simeon87 said:**
> Don't start with Java, it cultivates a mindset that everything is an object which is hard to unlearn afterwards. I suggest starting with Python.

Yes, a horrible thing in an object oriented language.

---

### Post by simeon87 on 2011-04-05
> **stchman said:**
> Yes, a horrible thing in an object oriented language.

Was that sarcastic? Even in an OO language that doesn't mean everything needs to be wrapped in a class. Many things naturally lend themselves for objects, such as an Image, a Car or a Connection. If you start with Java then everything, even things that are clearly not an object, are molded into a class. I regulary see code which has been influenced by that view :(

When OO was introduced, many programmers had difficulty grasping the concept which resulted in massive classes that did everything. This was because they kept thinking in a procedural mindset. It's the same thing today: if you start with OO, you'll have difficulty unlearning that mindset.

---

### Post by WinterMadness on 2011-04-05
just learn C++ first. 

[www.cplusplus.com/tutorial](www.cplusplus.com/tutorial)

and buy a book on it

---

### Post by cgroza on 2011-04-05
Why unlearn it? Things will evolve from now one in a OOP perspective. Besides, in is easier to work in OOP since it emulates a little the real world objects.

---

### Post by simeon87 on 2011-04-05
> **cgroza said:**
> Why unlearn it? Things will evolve from now one in a OOP perspective. Besides, in is easier to work in OOP since it emulates a little the real world objects.

OOP is good but it's not the magical tool that people make out of it. For example, OOP was recently removed from the introductory curriculum at Carnegie Mellon University for new computer science students ([source]("http://developers.slashdot.org/story/11/03/26/0016229/CMU-Eliminates-Object-Oriented-Programming-For-Freshman")). Yes, people should learn OOP but I don't think a OO-only language such as Java is the best language for beginners. The assumption in Java is that *everything* must be part of some class/object. For many programs, that assumption strangles your code, although it may work well for other applications.

---

