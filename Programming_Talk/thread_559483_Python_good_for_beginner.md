---
title: "Python good for beginner??"
date: 2007-09-25
forum: Programming Talk
---

### Post by weedeatr on 2007-09-25
hello there

I started programming this year and started of with qbasic..

Now i want to go to python or i have started reading about it is this a good choice since i am only a beginner???

---

### Post by samjh on 2007-09-25
Short answer: Yes.

Longer answer: If you actually did a search with "python" and "beginner", the answer should have been obvious.  This is a question that has been answered many times. :)

---

### Post by LaRoza on 2007-09-25
Look in the sticky for Windows Programmers, or just use my wiki link in my sig.

---

### Post by weedeatr on 2007-09-25
ok thanks i will check...But i wanted to know if there arent better languages for beginners than python?? :)

but thanks for the reply!

---

### Post by LaRoza on 2007-09-25
> **weedeatr said:**
> ok thanks i will check...But i wanted to know if there arent better languages for beginners than python?? :)

"Better" is relative.

I, and many others recommend Python first because:

* It is easy to learn
* It is very useful
* It is cross platform
* It teaches good habits

Then, many recommend to learn C. (I am of this school, top-down)

Others will recommend learning bottom-up. Assembly first, then C, then Python.

Also, Perl is a poweful language, and many will recommend that, because it is wide spread.

BASIC like languages are evil, don't use them unless you must, then only under protest. (Don't take this literally people, I try to avoid flaming, but VB just attracts it)

---

### Post by weedeatr on 2007-09-25
thanks alot this helped me :)

i think i will continue with python..

---

### Post by Compyx on 2007-09-25
Nobody seems to recommend Pascal anymore. It's a pretty clean language which also teaches good habits, although I agree these days you'll get a lot more out of Python or Perl.

When I was in my first year of computer science, our programming classes where all done with Pascal (Turbo Pascal actually), but that was 13 years ago.

These days, I too, would recommend Python, followed by C. Assembly is way too platform-specific to be of any general use, it's nice to be able to at least read some of it to check how a compiler optimizes certain code, but I wouldn't put much effort in it. Not that I dislike assembly, I still use it quite often (with 6502-systems of course).

The only thing I don't like about Python is the 'whitespace is relevant' part. I'd rather see Python use good old curly braces to create blocks.

---

### Post by LaRoza on 2007-09-25
> **Compyx said:**
> Nobody seems to recommend Pascal anymore. It's a pretty clean language which also teaches good habits, although I agree these days you'll get a lot more out of Python or Perl.

These days, I too, would recommend Python, followed by C. Assembly is way too platform-specific to be of any general use, it's nice to be able to at least read some of it to check how a compiler optimizes certain code, but I wouldn't put much effort in it. Not that I dislike assembly, I still use it quite often (with 6502-systems of course).

The only thing I don't like about Python is the 'whitespace is relevant' part. I'd rather see Python use good old curly braces to create blocks.

Pascal is not a good language, in many people's opinions. Python is easier to learn, and is much more useful. Many large games have Python code, many applications are written in it, and it can also be used to make small scripts. It is interpreted, unlike Pascal, but can be compiled.

It is also in modern development, and can be used in many area, and all platforms. Windows seems to be the only OS that doesn't include it. (HP's and Compaq's will have it)

Assembly is a very good way to get to understand how the computer works. I agree, most of the time, you won't use it. But knowledge is power, and Assembly is a very good thing to understand, especially if you learn C, and C is good to know if you know Python...

The whitespace rule grows on you... try:

```

from __future__ import braces

```

If you think about it, Python's rules make the most sense, no "end if", or braces, when we already indent, and if we already indent, why use those extra symbols?

If you want weird indentation rules, try Fortran 77 :D. I like the language, but it whitespace matters in a unique way.

I found out why when I bought a very old book, from when structured programming was new, and it assumed you were using punch cards, and didn't even mention the column rules.

---

### Post by pmasiar on 2007-09-25
> **Compyx said:**
> Nobody seems to recommend Pascal anymore. It's a pretty clean language which also teaches good habits, 

The only thing I don't like about Python is the 'whitespace is relevant' part. I'd rather see Python use good old curly braces to create blocks.

Although [Pascal](http://en.wikipedia.org/wiki/Pascal_%28programming_language%29) was designed to be easy to learn, its age (37 years!) shows. 
- Years ago, guessing types like Python does would be too expensive, but now dynamic typing is becoming mainstream. And typing is one huge and important difference between Pascal (static) and Python (dynamic). 
- Literals to build more complicated constructs, like lists, tuples or hashes (dictionaries): Pascal lacks them, and they are very convenient for learners.

Language designers learned quite a lot in those 37 years (at least **some** did :-) ) and languages now can be less obsessed about using CPU in most efficient way, and focus instead on the productivity of the developer.

White space is confusing for first 15 minutes, trust me, I disliked it also before learning Python :-)  If your code has proper structure (including indent), syntax is valid, case closed.

And try comparing communities: for better or worse, nobody uses Pascal anymore, but Python community is alive and thriving, producing gems like PythonChallenge to help you learn python and have fun at the same time!

---

### Post by scooper on 2007-09-25
There may be equally good languages to learn as a first language, but I think Python is somewhat unique in being easy to learn and very useful.

As mentioned, Pascal is good, but not popular or current.  BASIC is easy to learn, fairly useful, but promotes bad habits and bad code.

Java and C# are also pretty good, clean and useful, but not quite as clean and easy as Python.  Getting started with Java and C# requires putting together a more complex environment, e.g. with Eclipse or some other IDE.  On the other hand, with a good IDE you get a better ability to do exploration and get help, e.g. with auto-completion.

So, to summarize...  I'd go with Python for the fasted start and the nicest/simplest language.  I'd go with Java or C# if you want to ultimately work in an "enterprise" environment where they would be useful.  It may be worth a bit more effort to choose a language you might stick with.

Good luck.

---

### Post by LaRoza on 2007-09-25
> **scooper said:**
> 

Java and C# are also pretty good, clean and useful, but not quite as clean and easy as Python.  Getting started with Java and C# requires putting together a more complex environment, e.g. with Eclipse or some other IDE.  On the other hand, with a good IDE you get a better ability to do exploration and get help, e.g. with auto-completion.


* Not clean, java is messy, even when written cleanly
* Not complicated to get started, no IDE neccessary, I never used an IDE for Java

---

### Post by scooper on 2007-09-25
> **LaRoza said:**
> * Not clean, java is messy, even when written cleanly
* Not complicated to get started, no IDE neccessary, I never used an IDE for Java

For a beginner I'd definitely recommend an IDE for Java/C#.  The APIs and class structures are very intricate and hard to navigate without assistance IMO.  The same is not true for Python libraries, which tend to have flatter organization.

---

### Post by Joeb454 on 2007-09-25
I'm in my 1st year of a Computer Science degree, and we're doing C.

Though having said that we have been told by one lecturer that it's a messy language, lol

---

### Post by rybu on 2007-09-25
Python is an excellent 1st language.  Lots of universities use Python, Java or C++ as intro languages nowadays.  I had the unfortunate experience of going from BASIC to Pascal to Microsoft C++ (which had non-standard implementations of near everything) to GNU C++ (which I'm pretty happy with).  I've been learning bits of Python and Perl as neccessary/useful since.    I envy anyone who can start off with something as easy and *useful* as Python.

---

### Post by LaRoza on 2007-09-25
> **Joeb454 said:**
> I'm in my 1st year of a Computer Science degree, and we're doing C.

Though having said that we have been told by one lecturer that it's a messy language, lol

It isn't a messy language, at least, not as messy as Java. It can be very cryptic, like assembly, but as a whole, it is neat.

---

### Post by slavik on 2007-09-25
IMO, it's never good to focus on the language when learning to program ... you want to focus on the concepts.

take a simple problem and write out in english the steps needed to solve it ... then translate it to a programming language.

I have been told that because I speak two languages, it is easier for me to handle new (computer) languages and go from the problem solution in one language (natural) to another one (computer).

---

### Post by weedeatr on 2007-09-26
ok thanks for all your help!:)

---

### Post by samjh on 2007-09-26
Although I would generally recommend Python, I would also recommend C for those who come from electronics or computer-systems engineering backgrounds.  In fact, for those people whose ambitions lie in the area of microelectronics and computer systems engineering, I'd say machine opcodes should be first, followed by assembly, and then C.

[quote=Compyx]Nobody seems to recommend Pascal anymore. It's a pretty clean language which also teaches good habits,[/quote]Another person who likes Pascal!  It was my first serious programming language, which I learned in senior high school, and it has a special nostalgic value in my memory. :)

---

