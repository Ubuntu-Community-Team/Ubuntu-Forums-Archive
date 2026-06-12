---
title: "Programming, where should i start?"
date: 2010-05-10
forum: Programming Talk
---

### Post by rasmus91 on 2010-05-10
Hi there.

This basically is what the title says. Though, what I'd like to learn is programming C++ (people tell me that C/C++ are the most awsome to be able to program... and basic, as all hardware can understand C... or something)

(The program have to be something for Ubuntu. I don't have Visual Studio, and i don't care to buy it)

1. What program should i use? (user-friendliness, somewhat graphical editing for making windows & code finishing please!!)

2. A book or a online toturial.

3. a good mini project to start on when I've learned enough.

I know that there are some good programmers on this forum. But I'd just like some suggestions.

Rasmus

---

### Post by EarthMind on 2010-05-10
You really want to start with the hardest language? Why not go with an easier alternative to get the hang of it first? A language such as Python, or Java is worth learning too but I personally don't recommend it because it's WAAAY too much typing...

To program C/C++ apps on Linux you can use great GUI IDE's like Eclipse, Netbeans or Qt Creator, vim also seems to be very commonly used and I'm currently checking out if it's something that I can like.

---

### Post by rasmus91 on 2010-05-10
> You really want to start with the hardest language? 

Yes, besides from Assembler and binary i know this is very basic. 

> Why not go with an easier alternative to get the hang of it first? A language such as Python, or Java is worth learning too but I personally don't recommend it because it's WAAAY too much typing...

Because they're less powerful than C/C++
also, i have been told that if you can program C++ you can learn to program anything.

I have been told that Eclipse is very nice, Can anyone tell me Exactly which packages i need to be able to program C++ ?

---

### Post by AndyBoy_LV on 2010-05-10
Why not go with Web-programming? HTML/CSS + PHP + MySQL.

---

### Post by Kiske on 2010-05-10
Choose a programming language for yourself, and dont expect to be a pro in 5 minutes. PHP SQL AJAX JQuery XHTML CSS :)

---

### Post by MarcusW on 2010-05-10
I wouldn't say C/C++ are very hard to use, as long as you're doing basic things. (programs in the CLI) Here is a pretty good tutorial if I remember correctly:

[http://www2.its.strath.ac.uk/courses/c/](http://www2.its.strath.ac.uk/courses/c/)

This one is not as comprehensive, but probably easier to understand:

[http://www.cprogramming.com/tutorial.html](http://www.cprogramming.com/tutorial.html)

I'd use "geany" for the development, since it supports pretty much all languages (as long as you have a compiler installed) as well as some Linux system files.

I think the main thing to focus on is getting a good understanding of things like if, loops, variables, functions etc. Don't expect to do something really usable for a while, might still be fun though. :) Good luck.

---

### Post by rasmus91 on 2010-05-10
> Why not go with Web-programming? HTML/CSS + PHP + MySQL.

Because i want to write programs for Linux Desktop

> Choose a programming language for yourself, and dont expect to be a pro in 5 minutes. PHP SQL AJAX JQuery XHTML CSS

I'm not. But i have 6 weeks of vacation whereas only 2 weeks are planned. which means i potentially have four weeks of boredom...

> I think the main thing to focus on is getting a good understanding of things like if, loops, variables, functions etc. Don't expect to do something really usable for a while, might still be fun though.  Good luck.

i know. And if i run into trouble i have a friend who's a very good C/C++ programmer...

---

### Post by matthew.ball on 2010-05-10
In the future, you should ask programming-related questions in the [Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39") sub-forum of "Development & Programming" (though I suspect this will be moved there).

In answer to your questions though, I will try and be concise:
[quote=rasmus91]1. What program should i use? (user-friendliness, somewhat graphical editing for making windows & code finishing please!!)

2. A book or a online toturial.

3. a good mini project to start on when I've learned enough.[/quote]
1. This depends entirely on how much you currently know, and to an extent what it is that you desire to know.
From my personal perspective, I would recommend learning C before C++, start off with gcc and screen and use a simple text editor (like nano, or if you are keen go for emacs or vim), and do hand-compilation (or makefiles, but keep it simple to begin with).

If you're interested in GUI development, you'll be interested in three main(?) frameworks: GTK+, wxWindows and Qt. Whichever framework you use will no doubt have a version available for whatever language you have chosen.

For GTK+ you should look into Glade for the GUI designer, and a text editor for the coding. By default Glade produces C code I believe.
For wxWindows there is wxFormBuilder for designing the GUIs and again the text editor for coding. By default wxFormBuilder will export C++ code if I recall correctly.
I don't know much about Qt, I believe there is an IDE called QtCreator (mentioned in the previous post) which is good, but I have no experience.

2. I would recommend checking out Bruce Eckel's "Thinking in C++" book series; it's available free online (it should be first result on google).

One of the first chapters is "The C in C++" and I always thought that was a really good introduction to C.

3. I don't know about small projects. Have a go through project euler. But these problems won't need a GUI, they are focussed on an output (of course, you could make a GUI too!).

---

### Post by Meep3D on 2010-05-10
The language and platform is irrelevant.

The real question is, what do you want to do with your programming knowledge?  Why are you wanting to learn?  Essentially what do you want to create?  Most people learn to program because they want to create something (it's the whole point of it) and environments and languages generally have their specializations so if you wanted to, say, create a book organisation app (or anything where performance is not critical) C would be a bad idea, but if you wanted to create a complex game C would be a good idea.  Webapp is PHP or Ruby, simple games are probably best suited with Python.

The key to keeping motivated is to have a pet project you are working on that you can learn with, outside academic 'hello world' apps that real people can use and talk to you about.  I would say it is impossible to learn to program fully and then just start creating software - you need to create software to learn and if you are not really interested in what you are creating you are more likely to quit.

---

### Post by Dragonbite on 2010-05-10
Best way I learn is to give myself 2 things; a project and a "deadline".  Both can be flexible, but if it isn't for deadlines then nothing would get done ;)

I just did this recently with a PHP and MySQL project I put together for a church auction.  It gave me the chance to learn PHP and MySQL which I haven't used much of since at work I am using VB.NET, ASP.NET and MS SQL Server.

I've used books to learn Classic ASP years ago and that helped, but the classes my current employer has sent me to for .NET has helped me a lot with learning the non-syntax aspect of coding.

So when I moved to PHP, the conceptual portion of the project wasn't alien, only the syntax (which, surprisingly, was very easy to get used to and I see a lot of similarities between PHP and Javascript).

As for which language, that's a personal choice really.  If you want to do web programming that will be different than programming for, say, a program to run in Ubuntu with a GUI.

---

### Post by KdotJ on 2010-05-10
> **Meep3D said:**
> The language and platform is irrelevant.
...

+1
But I'd say pick a language and just stick with it while you learn the fundamentals of programming, program design and techniques. Then you can move to any language you want to, and only really focus on learning the syntax (depending of course on the language's paradigm).

As for wanting to the learn the most powerful language from the beginning, then yeah go for it. But bare in mind that as far as general programming is concerned (as especially for a beginner), you can get the same result in any language (check out the church-turing thesis). For example, languages such as Java, Python, C, C++, C#, Visual Basic etc etc all have toolkits for GUI programming too. So really it doesn't matter which one you learn.

As for good programs to write code with, honestly I suggest using something simple like vi or gedit. And the compiling and/or running the code via the terminal. This method will get you actually learning the syntax better and typing it out by hand will make you remember more in my opinion. Using an IDE will in some case bloat your code out quite a bit, and if you use it to create GUI's, then yeah sure it's simple enough to drag and drop buttons and textboxes onto a form, but you won't really understand how the coding behind it works. With using a basic text editor and creating the GUI yourself from code will give you a much better understanding on what's going on and how to change things.

This is all my opinion, but I first started with Visual Studio express back when I was in college. I could make programs quickly but not really know much about what was happening. In university we had to start off using gedit to code with and I now wish I started with this method to begin with.

---

### Post by Krupski on 2010-05-10
> **AndyBoy_LV said:**
> Why not go with Web-programming? HTML/CSS + PHP + MySQL.

He should probably first learn C (not C++, but plain K&R ANSI C).

Everyone uses C, and that knowledge will transfer over to JavaScript and PHP as they are fairly similar.

An EXCELLENT C book is "Practical C Programming" by Steve Oualline (published by O'Reilly Media) ([[COLOR="Blue"]**LINK**[/COLOR]]("http://oreilly.com/catalog/9781565923065"))

My copy is worn, dog eared and taped back together at the spine. I refer to it all the time.

-- Roger

---

### Post by piousp on 2010-05-10
> **rasmus91 said:**
> 
also, i have been told that if you can program C++ you can learn to program anything.


I dont think it works like that. To make good software, you need to design it without any specific language in mind, IMO. Besides, C++ is only 1 end of the spectrum. There are a LOT of languages out there.

But, back to topic, C++ its nice. Good luck with it

---

### Post by Dragonbite on 2010-05-10
Another idea is that if you have a project in mind, find projects that are similar and accessible and use the same language as that project codes in.

You would be able to use the existing program/code as a reference, possibly be able to contact a developer to ask some questions (at least it is a place to start) and have a feel for the "end result" you are working towards.

In this way, you may even learn enough to start contributing to the project and that is a win-win situation! They get help, and you learn actual code (not the theoretical stuff in the books)!

---

### Post by nvteighen on 2010-05-10
C and C++ more powerful? Write a domain-specific language (DSL) interpreter in them and you'll see they're no match for Lisp. Then write a kernel in Python and get yourself frustrated. 

No, there's no abstract power in programming. There's always a task to do and a more suited language for a specific task. Ok, it's true that all Turing-complete languages are able to express all computable procedures, but some will need thousands lines of code where other will need just a couple of hundred...

For the tasks all beginners do when learning how to program, C and C++ are way too complicated. Perfect, you start smoothly doing some math... but as soon as you want to deal with user input, in C you get horrible string manipulation (pointers, the whole gets() thing, buffering, NULL-termination...) and in C++, you either use C strings (really bad idea) or learn what OOP is and use STL strings... and all you wanted to learn is how you can ask information from the user...

Not only that, I really doubt that someone can appreciate C++'s advantages and disadvantages without a lot of proper programming experience (and knowledge on the history of programming... I mean, knowing what were C's flaws that lead to the development of C++).

I'd go for Python or some other high-level language (Smalltalk, Lisp, Perl, whatever) so you learn the general basics of programming. After that, you'll be able to understand (and you should) the specifics of low-level programming with C and C++ (no, C++ is not high-level: you still have to think how the stack behaives when programming in it).

---

### Post by EarthMind on 2010-05-10
And if you do learn C or C++ I suggest you pick C++ because of the ability to use the amazing Qt SDK, which can save you a lot of time and pain in your wrists.

---

### Post by madjr on 2010-05-10
first play this game (dont cheat! :)):

[http://www.kongregate.com/games/Coolio_Niato/light-bot](http://www.kongregate.com/games/Coolio_Niato/light-bot)


after this you need to move into these games
laby (repos)
robocode (repos)
robomind
kturtle (repos)


the easy part is coding, the harder part is logic and flow. once you have that, then writing the thing is so much easier.

and check python
[http://www.jonobacon.org/2010/04/08/making-programming-easier-for-kids-with-pyjunior/](http://www.jonobacon.org/2010/04/08/making-programming-easier-for-kids-with-pyjunior/)

fullcircle mag also has few guides

lots of linux programs are done in python, easier to use and even port.

programming can be crazy hard if you dont start from the base. So go slow and have fun :)

programming is a way of life, you try to understand the process and the logic of an universe that seems strange and chaotic by actually trying to recreate bits of it virtually. ^^

---

### Post by EarthMind on 2010-05-10
That game is fun :D

---

### Post by lostinxlation on 2010-05-10
> **rasmus91 said:**
> Hi there.
 
This basically is what the title says. Though, what I'd like to learn is programming C++ (people tell me that C/C++ are the most awsome to be able to program... and basic, as all hardware can understand C... or something)
 
(The program have to be something for Ubuntu. I don't have Visual Studio, and i don't care to buy it)
 
1. What program should i use? (user-friendliness, somewhat graphical editing for making windows & code finishing please!!)
 
 
If you're talking about programing environment, don't even bother for that in the beginning. Just learn how to program, and how to compile, and how to run by bare hands and that's how you learn the real basic part of programming.
 
C/C++ is a good start because you'd be more exposed to the basic concept of computers than scripting languages. Many people go against learning C/C++ as a beginner, but the truth is programming isn't rocket science, and if you read a book carefully, you should be able to understand it easily.

---

### Post by CptPicard on 2010-05-10
@lostinxlation, I would suggest you take a look at [this thread here]("http://ubuntuforums.org/showthread.php?t=851794"). This issue comes up over and over again, and it was discussed at length there.

> 
 Many people go against learning C/C++ as a beginner, but the truth is programming isn't rocket science, and if you read a book carefully, you should be able to understand it easily.

The issue really is that languages like C and C++ (they really are two different beasts) require detail that isn't really all that educational except that in those languages you have to deal with it. Programming can actually be quite intellectually interesting when you start working with all the various ways to look at different problems... but that is a much more high-level view than just learning the syntax of some given particular language.

---

