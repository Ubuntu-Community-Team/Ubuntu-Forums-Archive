---
title: "Perfect Programming Langauge (???)"
date: 2011-09-25
forum: Programming Talk
---

### Post by AZBoy28 on 2011-09-25
Hey.

I'm a 12 year old kid who is interested in programming for a career.

I'm looking for a programming language for me to study and create applications with.

I want to use one of the languages from the Visual Studio Express suite. I'm mainly focussing on either Visual C# or Visual Basic. 

Which one is better? C# or VB.

Thanks =)

---

### Post by WinterMadness on 2011-09-25
theres really no such thing as a best language. some people really hate vb, but theres very little reasoning behind it. apparently c# and vb are similar, so just play around with both.

---

### Post by AZBoy28 on 2011-09-25
Thanks, Is C# more complicated to learn?

---

### Post by WinterMadness on 2011-09-25
im not really a c# user, however, i have a pretty good amount of experience with VB, and ive been told that c# is very similar to vb. So if thats true, I can at least say that its not very difficult at all. Perhaps a bit wordy, but thats no big deal.

Dont get too caught up on the syntax, spend more time learning the concepts of programming that can be applied across many different languages

---

### Post by PaulM1985 on 2011-09-25
I work using C#. I cant say how difficult it is to learn compared to vb, I learned it after using java. I would recommend buying a book on C# and working through some of the exercises. After that, when you are comfortable with the language, buy a book on object oriented design.

Good luck.

Paul

---

### Post by MG&amp;TL on 2011-09-25
I'm 15, and I've found that C-based languages can be Very boring and frustrating until you get the hang of them-I suggest python:

```
sudo apt-get install python
```and *processing* language.

Python is a very easy, interpreted, language which will get you ready for the trials of C, C++, C#, VB etc.

Processing:

[http://processing.org/](http://processing.org/)

..is a very versatile graphical language that can be interactive from the very start. It seems to be a cross of Java and C++. The best bit about it is that you can draw a circle to a screen in a line, and make it follow your mouse in 5.

Although search these forums for "programming language" and you'll get literally hundreds of hits. Just a thought, though, so if you're sold on C# or VB go right ahead. :)

---

### Post by simeon87 on 2011-09-25
Of those two, I'd choose C# as it's closer to "programming in 2011" than VB really.

---

### Post by karlson on 2011-09-25
> **AZBoy28 said:**
> Hey.

I'm a 12 year old kid who is interested in programming for a career.

I'm looking for a programming language for me to study and create applications with.

I want to use one of the languages from the Visual Studio Express suite. I'm mainly focussing on either Visual C# or Visual Basic. 

Which one is better? C# or VB.

Thanks =)

Having used both I can't say one is better then the other.  I would suggest doing the following since your development environment seems to be Windows I would suggest something like a simple form in VB and the same one in C#.  At that point you judge for yourself whether you like one better then the other.

---

### Post by AZBoy28 on 2011-09-26
Thanks, Might go with C#, I have a VB and C# book. More help is appreciated =)

---

### Post by sanderd17 on 2011-09-26
C# looks more like Java.

C# follows a better philosophy than VB. VB is mainly event-driven. That means it's easier to create simple GUI (you'll get a pretty program in no time), but it will also be more difficult to maintain. C# is mainly object-oriented. Object-oriented programs are easier to maintain afterwards.

So if you will use C#, you do need to get the concept of an "object".

As a short intro (don't worry if you don't get the concept, it takes some time):

In an object-oriented language, everything is represented as an object.

Let's take a mathematical drawing program as a start.

You can haver several objects there: points, lines, squares, rectangles ...

An object always has
[LIST=1]
[*]properties (aka attributes). for a point this could be the coordinates, for a line, the properties could be two points where it passes through
[*]actions (aka methods or functions), these are used to change the properties, like "move the point 2cm to the left".
[/LIST]

As you see, an object can have other objects as properties (a line has two points as properties). This has the advantage that everything stays consistent. If you move a point, the line will move with it.

Now, to write such a structure to code, you will define for every type of object a class. So you will have a class called "Point", one called "Line" etc. Right under the class definition, you normally say what the attributes look like (two numbers for a point, two points for a line ...)
And under that, you make the functions, where the real work happens. A function like "move the point 2cm to the left" will substract 2 from the second coordinate.

This was a very short intro, it's very normal you don't get the power of the concept this fast, but when it's in your mind, it will probably be a bit easier to read an object-oriented book.

---

### Post by Jiggle156 on 2011-09-26
16 here, I started out by learning Python, and then moved on to C++. Python is a nice, simple language to start out with. Personally I find it's syntax annoying, but its definitely a good place to start out from. Never really used VB or Java, so I can't comment there - but once you've learned one language and got a firm grasp on the concepts, learning another will be fairly easy.  Good luck OP!

---

### Post by Arndt on 2011-09-26
> **AZBoy28 said:**
> Hey.

I'm a 12 year old kid who is interested in programming for a career.

I'm looking for a programming language for me to study and create applications with.

I want to use one of the languages from the Visual Studio Express suite. I'm mainly focussing on either Visual C# or Visual Basic. 

Which one is better? C# or VB.

Thanks =)

I'd say just pick one and take it to its limits. Or, as the case may be, become bored with it, and try another.

It's not just syntax and semantics, it's documentation, programming environment, the whole culture of a language, and there's nothing wrong with getting some preconceived notions now, it will simply give you a platform to stand on. Later, learn new things and revise some of what you thought was true. Learning a catalogue of what other people think is good or bad will not bring much, until you know what they are talking about by having tried it yourself.

But planning all that in advance now is the wrong idea, I think. Pick any one, and be creative.

I program as a profession, and I don't use only one language, but the one which seems best for the current task (which depends on a lot of things, not just the problem itself). Sometimes I'm wrong, and have to rewrite in another language, and sometimes I learn a new language.

---

### Post by nvteighen on 2011-09-26
@OP:
There's no perfect language, as you've already been told.

I'd rather suggest any language that's not dependent on some GUI designer over VB. Programming is not just about GUIs and the "VB mindset" leads to very bad "interface-based" coding, where everything is thought up from the interface rather than basing the interface from the implementation or backend.

> **WinterMadness said:**
> theres really no such thing as a best language. some people really hate vb, but theres very little reasoning behind it. apparently c# and vb are similar, so just play around with both.

IMO, the problem with VB is similar to what happened with Javascript some years ago. It's true that the VB language isn't that terrible, but its users were so bad programmers that their bad reputation "contaminated" the language's reputation.

---

### Post by GenBattle on 2011-09-26
Don't be afraid to start with a technology that isn't necessarily considered the best; I started with QBASIC and VB when I was about 12, and I've since move up through Delphi, C#, Python, and now Go.

Once you understand the underlying concepts of languages like functions, variables, objects, etc. and know a few different programming methodologies, everything else becomes syntax. I would say general knowledge about programming gets you 80% of the way to being a decent programmer, while the last 20% of language-specific features and syntax makes you an expert.

Pick something that flows naturally for you. give C# and VB a try, and see which one enables you to learn more and get further with your programs, then use that until you run up on some limits or until you feel like learning something different. Don't get too hung up on a particular language.

---

### Post by jerenept on 2011-09-26
AZBoy, as a fellow newb and teenager, I can tell you, do not try to learn any specific programming language. You should instead try to learn the concepts and the logic behind programming, like GenBattle said above.

Personally, I use Pascal to learn concepts because it's fairly beginner-friendly, and there is an excellent [open-source compiler]('http://freepascal.org'), but you could use anything else; perl, python, C#, VB, even JavaScript :P

---

### Post by sammiev on 2011-09-26
> **jerenept said:**
> AZBoy, as a fellow newb and teenager, I can tell you, do not try to learn any specific programming language. You should instead try to learn the concepts and the logic behind programming, like GenBattle said above.

Personally, I use Pascal to learn concepts because it's fairly beginner-friendly, and there is an excellent [open-source compiler]('http://freepascal.org'), but you could use anything else; perl, python, C#, VB, even JavaScript :P

I programmed in C++ and a few others but using many different programs over the years I found that learn concepts is what it's about. 

Jerenpt is a very smart person. :popcorn:

---

### Post by shawnhcorey on 2011-09-26
I would recommend you start with one of the scripting languages: Perl, Python, Ruby. They're all free to download.

---

### Post by Rich78 on 2011-09-27
There's no such thing as a perfect programming language, they're all tools to get a job done, and each one has it's benefits.

In terms of the .NET environment, VB and C# are equal, however C# is a much nicer language to work with in terms of structure and makes a lot of sense when you're developing web apps with javascript as it's so similar.

Coming from a VB background, I progressed to VB.NET, and the learning curve was probably as steep as was my cross train to C# as it's more the .NET environment you're learning.  The language differences are almost negligiable in a managed environment.

I often now just convert VB.NET code on the fly to C# if I happen to drop on a sample I need some code for and can't find a C# equivalent, it's pretty easy to convert as there are only subtle type and structure differences.

I'd also say C# is the more desirable language now for most businesses, I've seen more C# jobs than VB ones, where as before .NET VB was definately more popular.

With express versions, it's free to start learning C#, so no reason to learn some of the other scripting based languages unless you're particularly interested in them.  Again they have their place, but I'd say for getting a job C# is currently a good one to learn.

I've also developed in mono and used the mono develop studio, which is actually really good now, and again free, as well as being able to develop on your beloved Linux box :).

---

### Post by alegomaster on 2011-09-27
I myself started programming at 12 too. I decided to program in C because the book I had was about C. Right now I am teaching myself C++ so I can program for my local FIRST robotics team. I am finding C++ easy to learn, because I had previous knowledge of C. So my advice to you is too learn programming concepts with C, and when you are good at programming, teach yourself C#. It will be easier to learn, because C# is based on C, and therfore concepts that you learn in C can be applied in C#.
 
Python is really great for scripting due to its ease of use, so if you want to you can start there, then go into C. I never used any scripting language, so it proves that you don't need to learn a scripting language first, but it can help you learn some programming concepts.
 
About the perfect programming language: That language is assembly, but assembly typicly is hard to learn(And needs more code then just using a high-level program), so not many people use it, but it is the fastest, and you know evrything the computer is doing.

---

