---
title: "New Programming Language (Seriously)"
date: 2011-06-24
forum: Programming Talk
---

### Post by Grenad on 2011-06-24
As the title says, I want to create a COMPLETELY NEW programming language. I have read very many sites, articles, and tutorials on how to do this, I know that this is a very large undertaking, and I know that it is difficult and probably above my head but I still want to try, so dont tell me to give up or anything like that. I know from my research that I need to create a compiler that takes my language and turns it into something the computer can read. I know the compiler consists of a scanner, a parser, a AST (or something like that), and a Code Generator.

So, I already know the basic grammar that I want for my language. All I need is to make a working compiler. I dont know exactly how to code this but my best language is c# so I would probably need to make the compiler in this language. Any help is appreciated so please give me any advice you have!:D Thanks in advance!

---

### Post by NovaAesa on 2011-06-25
It's not that really hard to design and implement (i.e. write a compiler for) a language. I did that exact task in a compiler design subject I took last semester. I would recommend "Compilers, Principals, Techniques, and Tools" by Aho et al (it's also known as "The Dragon Book").

Designing a *good* language on the other hand will be much more difficult.

---

### Post by Grenad on 2011-06-25
I see... Well would you mind sharing some of that information with me? I would like to know how to make a basic compiler for my basic language and then I hope to build on from there.

---

### Post by NovaAesa on 2011-06-25
I would highly recommend sorting out the language specification before starting on the compiler, rather than getting a compiler running for a small subset of the language and then having to add onto it. Either that, or write a compiler for your basic language, and then start again when you have the entire language sorted out (this is a legitimate approach, especially since you haven't written a compiler before - the first write of the compiler would be a "practice run").

When getting the specification of the language sorted out, the most important things are:

1) For the scanner: what are the keywords? what are legal identifiers.
2) For the parser: what is the grammar of the language? Make sure there is no ambiguity in the grammar (Aho explains this in great detail, cf the famous "dangling else" problem).
3) For the semantic analyzer, what are the semantic rules? There will be lots of these.
4) For code generation, you will need to know intimately the target architecture. This means you will probably need to know in great detail assembly language.

Code optimization is put in the compiler as well, but I've omitted that for simplicity.

Just so you know, there's alot of work involved in the total design process, and most of the effort goes into the actual design of the language rather than implementing the compiler. I've been told by my professors that there is about a PhD's worth of work involved, i.e. 4 man years. This isn't meant to discourage you, just to let you know this won't be a walk in the park. Implementing a quickly devised language should be fairly quick though, i.e. a few weeks if you work on it consistently.

---

### Post by GeneralZod on 2011-06-25
For the actual code generation, LLVM is really nice; check out the tutorial, which actually builds a working compiler for a simple language in a few hundred lines:

[http://llvm.org/docs/tutorial/LangImpl1.html](http://llvm.org/docs/tutorial/LangImpl1.html)

It has a C API interface (in addition to its "native" C++ one), and it should be easy to write C# bindings, if none exist already.

---

### Post by Grenad on 2011-06-25
Thank you for the help. I really appreciate it! For the code (language) itself, I want it to be pretty basic. I want it to be OO and have strings, ints, etc., loops such as for, foreach, while, if...else, and all the other essential stuff with a syntax similar to c# (this is just to have a base; I plan to make a completely different language once I learn enough). In the future, I still want to be able to keep adding to it, even if I need to rewrite the compiler every time. For the semantic analyser, I kinda forgot what the semantic rules are. I probably learned them as something else. And I want to assemble for linux.

As for the work involved, I am fully aware of the immense effort this takes, especially with only a man and his laptop. However, I am fully willing to do this because i feel this will make me a much better programmer (and its pretty neat to be able to make your own language).

---

### Post by pbpersson on 2011-06-25
Please make your language platform independent like Java so it will run on Linux, Unix, Macintosh, and Windows - code once, run anywhere!  :)

Please also code it so it makes sense and is easy to use.

For instance, if you want to change the title bar on a frame, it would be:

**MyFrame.Title.setText("This is my title bar");**

Trying to do something extremely simple like this is nearly impossible in Java  :(

---

### Post by Grenad on 2011-06-25
@pbpersson, I am just learning the basics of creating a language right now but once I get that down and begin work on a legitimate new language, simplicity is going to be a priority. I always get frustrated at gui design in my favorite languages so that will be a big one! I will be sure to post my progress (on the real language;)). Also, I am going to try to make it platform independent but I dual boot vista and natty, and natty is far superior for development so I plan to do my "experiment" on natty, hence the linux target.

---

### Post by kagov on 2011-06-25
> **pbpersson said:**
> Please make your language platform independent like Java so it will run on Linux, Unix, Macintosh, and Windows - code once, run anywhere!  :)

Please also code it so it makes sense and is easy to use.

For instance, if you want to change the title bar on a frame, it would be:

**MyFrame.Title.setText("This is my title bar");**

Trying to do something extremely simple like this is nearly impossible in Java  :(

myFrame.setTitle("This is my title bar"); // After of course you create the instance of a Frame or something similar.

In my opinion the way you specified above would be far more irritating anyway.

---

### Post by simeon87 on 2011-06-25
It's easier if your compiler transforms your language to C, rather than assembly language for a specific platform. That way, you can use GCC to target various platforms instead of studying all the books about processors yourself.

---

### Post by Grenad on 2011-06-25
That is true. I just need to learn how to build a compiler first!!! I know what each part does, i just have no idea how to code it! (i should probably code it in c# since thats my best language)

---

### Post by Tony Flury on 2011-06-25
Most compilers use an architecture called recursive descent - i.e. that you use recursion to traverse the stream of tokens that your tokeniser generates.

If i were you I would start with a tokeniser - i.e. a small set of functions/classes to take the text input and split it into lexical tokens - i.e. string, integer, floating point number - and maybe identify some other key punctuation tokens, and reserved words.

The recursion part is essentially identifying the syntax - whether a string is a keyword, or a variable etc - and whether it is legal where it is.

I would start by reading the book suggested above - and good luck.

---

### Post by cgroza on 2011-06-25
I think you should learn a few text parsing techniques first.

---

### Post by alegomaster on 2011-06-25
> **Grenad said:**
> That is true. I just need to learn how to build a compiler first!!! I know what each part does, i just have no idea how to code it! (i should probably code it in c# since thats my best language)

I have this book about computer that talks about computer in every level: From the simple logic gates and ALU's to Making a compiler and an OS (This is not the title). The link of the book is here: [http://www.amazon.com/Elements-Computing-Systems-Building-Principles/dp/026214087X]("http://www.amazon.com/Elements-Computing-Systems-Building-Principles/dp/026214087X")

---

### Post by pbpersson on 2011-06-25
> **kagov said:**
> myFrame.setTitle("This is my title bar"); // After of course you create the instance of a Frame or something similar.


This code did not give any errors when I typed it and the application ran:

```
JFrame mainFrame = EmailComposerApp.getApplication().getMainFrame();
mainFrame.setTitle("This is a test");
```

However, it did not change the title text and when I stopped the application it gave me a StackOverflowError exception

In Java I think a frame can have a mainpanel or it can have a scrollpane and somehow all these items overlap and I am always confused as to which one I am dealing with.

For instance, in another project I have a JTable and I wanted to change the column header but there are three different ways to accomplish this and none of them seemed to work.  Here again, there was no error when I was typing this into the IDE or at runtime.  It just does what I tell it to do even if it makes no sense.

There should be way for the compiler to see what you are trying to do.  "I see that you are changing the title of your frame, however your frame is hidden behind your mainpanel - did you mean to instead change the title property of your mainpanel?"

I don't know if this is the actual problem but I have run into situations like this.  This would be SO helpful!

---

### Post by LoneWolfJack on 2011-06-25
> That is true. I just need to learn how to build a compiler first!!!

Compilers are nothing fancy. They're just programs. Many (most?) Compilers are written in C. So:

* create a text file with a simple program written in your fancy new language
* write a C program that parses this file and "understands" what your language does, performing the desired tasks in C language, writing the results to stdout
* make this C program accept files as arguments
* compile it

There's your compiler.

---

### Post by Grenad on 2011-06-25
I want to make my compiler in c# because that is the language I understand the most. My problem is that I dont know how to code it to understand my language. I am not asking for someone to write my code for me; I just need to know specifically what to tell the computer to do in each step. For example, I dont know how to tell the compiler what to do for, say, a for loop. How would I get the compiler to see the word "for" and then execute the iteration?

---

### Post by schauerlich on 2011-06-25
> **Grenad said:**
> I want to make my compiler in c# because that is the language I understand the most. My problem is that I dont know how to code it to understand my language. I am not asking for someone to write my code for me; I just need to know specifically what to tell the computer to do in each step. For example, I dont know how to tell the compiler what to do for, say, a for loop. How would I get the compiler to see the word "for" and then execute the iteration?

I think you'll find that if you actually click on links and read the stuff that people have talked about in this thread, you will have a much better chance at learning what you're trying to learn than asking someone to retype it all for you. Writing a compiler isn't a simple task that can be neatly packaged into one thread on a forum.

---

### Post by unknownPoster on 2011-06-25
> **LoneWolfJack said:**
> Compilers are nothing fancy. They're just programs. Many (most?) Compilers are written in C. So:

* create a text file with a simple program written in your fancy new language
* write a C program that parses this file and "understands" what your language does, performing the desired tasks in C language, writing the results to stdout
* make this C program accept files as arguments
* compile it

There's your compiler.

That's not a compiler. That's an interpreter. That's essentially how python works.

---

### Post by Grenad on 2011-06-25
@ saurelich,
I am only trying to get basic information. I am not requesting an extremely detailed answer that will solve my problems for me; I am just trying to understand HOW to get it done. I cant use the most recent Dragon Book because I cant throw that kind of money without thinking about it first. I have a downloaded sample of the book alegomaster suggested and I am considering purchasing it. I know that this is a hard task, and I know that there is too much information to put in a single thread. I just want to make a simple compiler for a simple language so that I can understand how its done and perhaps develop better languages in the future. Please do not assume that I am not following the links because I cannot view everything immediately and I want to look at them when I have time to read thoroughly and actually learn the material.

---

### Post by CptPicard on 2011-06-25
Why not write an interpreter first? Learn a language like Scheme, and then start writing other languages in terms of that (Lisps are awesome for general interpreter-writing). It should get you going in an interesting way. Compilation is then a matter of adding a kind of "serialization" step from your interpreter data structures into an actual compiled file...

---

### Post by cyberslayer on 2011-06-25
I'd also recommend learning a lisp dielect if you want to write a compiler.  Once you are a good lisp programmer, it is easy to create simple languages very quickly using lexer and parers generators (ie, lex and yacc).  One of the main advantages is that in lisp, code can be treated as data (and data can be treated as code).  This means that instead of generating assembly or bytecode, your compiler/interpreter can simply translate your source language into lisp which greatly simplifies code generation.  It also allows you to use lisp namespaces and data structures in your target language which can save you a lot of trouble since then you don't have to write your own.

---

### Post by Arndt on 2011-06-25
> **Grenad said:**
> I want to make my compiler in c# because that is the language I understand the most. My problem is that I dont know how to code it to understand my language. I am not asking for someone to write my code for me; I just need to know specifically what to tell the computer to do in each step. For example, I dont know how to tell the compiler what to do for, say, a for loop. How would I get the compiler to see the word "for" and then execute the iteration?

You need to decide what the target language is. It may be machine instructions for some processor (usually passing through an assembler), or byte code for some byte code interpreter that you invent, or one that exists, like the Java virtual machine, or you can generate source code in some other language, like C or C# or Lisp.

Once you know this, it will be relatively easy to answer the question "how is a FOR loop translated?".

---

### Post by trent.josephsen on 2011-06-25
So let me get this straight.

You have *very little* practical programming experience, the *only* language you claim knowledge of is C#, you don't have a target domain in mind, your only stated motivation is "i feel this will make me a much better programmer", you aren't willing to spend a few bucks on the book that is *most* likely to help you, you don't have any apparent understanding of parsing or what an interpreter is, you're explicitly ignoring the experienced people who tell you (very sensibly) that you're going about this all wrong, and you even seem to believe that OO is a feature of a "pretty basic" language!

I'm going to say this as nicely as I possibly can:  You are being very foolish.  Don't give up on your idea, but at least put it on hold until you don't have to turn to the Ubuntu Forums for instruction.  If [your only language was C# six days ago](http://ubuntuforums.org/showthread.php?p=10959032#post10959032), you are not capable of writing a compiler for a new language within the next two years (even if you are exceptionally smart).

---

### Post by LoneWolfJack on 2011-06-25
> That's not a compiler. That's an interpreter. That's essentially how python works.

Well, you're right of course, but as soon as you think JIT, there's really not much of a difference.

---

### Post by Grenad on 2011-06-26
@trent,
i dont know what makes you think i have very little programming experience. i develop and HAVE developded games and personal desktop applications, and i know more than c#. I am best with c# but i also know python and the basics of java and c. i can develop very well in c#; i just dont know how to build a compiler or the functions of c# for building compilers. i bought the book i sampled, but i havent bought the dragon book because the latest edition is near $100 and i cant spend that money this quickly. and i know that oo is complex so i have drifted away from that ideal. and if you must know, i feel that a specialized language will be much more efficient for my current project, so i have motivation other than my very valid reason of learning about programming. now, quite frankly, i dont respect people trying to tell me that i am not qualified to do this. i am well aware of my skill level and i think that i am capable to do this. so please, if i fail, i would at least want to have an attempt to learn from.

---

### Post by NovaAesa on 2011-06-26
> **Grenad said:**
> i havent bought the dragon book because the latest edition is near $100 and i cant spend that money this quickly
You could always get the first edition second hand. It's dirt cheap on amazon. According to wikipedia, the main things added to the second edition are parallel machines, JIT, and garbage collection (which are all very advanced features that generally don't make their way into simple languages).

---

### Post by Grenad on 2011-06-26
It is! thank you. that is a much better price; i will order it tomorrow. i  think i will read both of the books that i purchase and then i will first attempt an interpreter and then a compiler since an interpreter seems to be slightly simpler (although still complex). Thanks to everyone for their help. I can always count on the ubuntu community for help. i am going to leave this thread open because i will most likely still have problems even after reading the books.

---

### Post by hakermania on 2011-06-26
> **kagov said:**
> myFrame.setTitle("This is my title bar"); // After of course you create the instance of a Frame or something similar.

In my opinion the way you specified above would be far more irritating anyway.

that's what we call object orientation, don't we?

---

### Post by slavik on 2011-06-26
lex and yacc

---

### Post by pbpersson on 2011-06-26
> **Grenad said:**
> @ saurelich,
I am only trying to get basic information. I am not requesting an extremely detailed answer that will solve my problems for me; I am just trying to understand HOW to get it done. 

If you look at the source code of an application you will find that it typically begins with include statements.

Procedures or Functions begin with a type, then a name, then a list of parameters.  The body of the procedure or function begins with a brace and ends with a brace.

Within the procedure or function body you have statements that begin with keywords such as:

FOR
WHILE
IF
SWITCH

You parse the text of the source code based upon these rules.  

If you are expecting to process includes you might be inside an include routine which executes "WhileValidInclude" which would be a Boolean test which would be set to false when you hit a function or procedure.

If you are processing a function or procedure you would parse the first line to get the type of the function or procedure and the parameters until you hit the first brace.  Then you would get into a switch statement where you key on the first word which would then send you to specialized routines to process the 

IF
FOR
WHILE
SWITCH

These would be my ideas on how to start this project.  I could be totally off base because I have never thought about doing such a thing but I thought I would give you my thoughts.

I am assuming that while you are parsing the text you are building some bytecode output file which will then be interpreted on the host machine by a JIT compiler.

---

### Post by nvteighen on 2011-06-26
I think you should first learn a couple of different languages first in order to grasp different approaches to programming languages. Otherwise, you'll be doomed to clone C# poorly.

Ok, you may learn how to write a compiler, but not how to design a language. So you won't get into half of the experience.

For language design, I think Scheme is a great option to work with. Lisp programming is essentially expanding/modifying the programming language to your needs, using the interpreter as your own's. It is way more powerful than creating functions and libraries in other languages. You better give it a shot. It's true that Common Lisp is better for "real" stuff and is a better platform to work with, but Scheme is cleaner and IMO, more suited for this.

---

### Post by trent.josephsen on 2011-06-26
> **Grenad said:**
> i dont know what makes you think i have very little programming experience.
Well, let's see...

> I am best with c# but i also know python and the basics of java and c.

That'll do to start with.

Also, forgive me if I don't believe your self-assessment "i can develop very well in c#", especially when it is bookended by comments that don't really make sense to come from an experienced programmer.

Oh, well.  It's perfectly within your rights to ignore my advice.  Godspeed, and may your imminent failure teach you something valuable.

---

### Post by Thewhistlingwind on 2011-06-26
The world has enough programming languages. Go do something useful.

Linux is still missing a lot of functionality, go learn a language that won't infect people with mono and join the effort.

> 
Oh, well.  It's perfectly within your rights to ignore my advice.   Godspeed, and may your imminent failure teach you something valuable.

This too, I think you have serious delusions of grandeur as to the extent of your skill.

---

### Post by Simian Man on 2011-06-27
I think learning to write a compiler is the best project you can do to learn computer science and programming.  It will teach you high-level concepts like regular expressions, context-free grammars, graphs, recursion and many algorithms and also low-level details like stack frames, instruction sets and optimizations.

Keep in mind though, like others have said, that the language and compiler you produce won't be used by anybody but yourself :).

> **simeon87 said:**
> It's easier if your compiler transforms your language to C, rather than assembly language for a specific platform. That way, you can use GCC to target various platforms instead of studying all the books about processors yourself.
Since this is just a learning exercise, portability and performance don't really matter.  You could just pick one architecture to target.  Other options include LLVM, Java byte code or MSIL - which would probably be the best bet because then his language could use the .NET/Mono libs he already knows :).


> **Tony Flury said:**
> Most compilers use an architecture called recursive descent - i.e. that you use recursion to traverse the stream of tokens that your tokeniser generates.
No, actually the only compilers that use recursive descent are toy ones.  My first compiler was recursive descent, and it works well for learning projects (because you don't have to mess with yacc or table drive compiling).  Nearly all serious compilers use bottom-up parsing however.

> **LoneWolfJack said:**
> Well, you're right of course, but as soon as you think JIT, there's really not much of a difference.
But JIT still compiles to the target machine, whereas interpreters, like what you describe, do not.

> **Thewhistlingwind said:**
> Linux is still missing a lot of functionality, go learn a language that won't infect people with mono and join the effort.

Don't be a troll.

---

### Post by Grenad on 2011-06-27
Yes, Im fully aware that my language will most likely never be used by anyone except me, if i even get that far. Just one question: when I compile my language it compiles to the language that the compiler is written in, correct?

---

### Post by cgroza on 2011-06-27
> **Grenad said:**
> Yes, Im fully aware that my language will most likely never be used by anyone except me, if i even get that far. Just one question: when I compile my language it compiles to the language that the compiler is written in, correct?
It can compile in any language you want to, it is your compiler remember, you decide what to do.

---

### Post by schauerlich on 2011-06-27
> **Grenad said:**
> Yes, Im fully aware that my language will most likely never be used by anyone except me, if i even get that far. Just one question: when I compile my language it compiles to the language that the compiler is written in, correct?

Think of a compiler as a translator. It takes in a language (yours), does some black magic, and spits out another language. Generally, this means it compiles to assembly language, which is then converted to an actual binary executable. However, it can theoretically compile to whatever language you want. There are [some](http://en.wikipedia.org/wiki/Chicken_(Scheme_implementation)) compilers that output C code. The compiler itself, however, can be written in whatever language you want. It's just like any other program.

---

### Post by Grenad on 2011-06-27
Trent and whistlingwind,

Of course it doesnt sound like I am an experienced programmer when I am asking about something which Ive never dealt with before. If I was going to comment on the things Im good at I wouldnt be on the forums. Also, as I said before, I do expect to fail many times before I actually get something done. I dont care. It will teach me much about programming and eventually, I WILL get it. I know that this is a very difficult project and perhaps it is above my skill level, but I believe that I can get it with some time. So please, stop with the cynical comments.


> **schauerlich said:**
> Think of a compiler as a translator. It takes in a language (yours), does some black magic, and spits out another language. Generally, this means it compiles to assembly language, which is then converted to an actual binary executable. However, it can theoretically compile to whatever language you want. There are [some]("http://en.wikipedia.org/wiki/Chicken_%28Scheme_implementation%29") compilers that output C code. The compiler itself, however, can be written in whatever language you want. It's just like any other program.

Thank you. This makes sense.

I am making my way through "Lets Make a Compiler" by Jack Crenshaw (because its going to take a while for the Dragon Book to be delivered). Too bad Pascal is practically dead. Now im trying to find some good languages for building compilers. I found an article for building a c# compiler. However, I heard somewhere that there are better options, such as scheme (nvteighn), but somewhere I read that Haskell would be better. So, I researched Scheme, Haskell, and OCaml. Which of these would be best for building a compiler? Or is any language equal for this application.

---

### Post by CoffeeRain on 2011-06-28
I've just got to tell you to not be disheartened by people telling you that it would be too hard. I made a small one that just simplifies my daily tasks at the computer and it can do math also. When I made it, I was not thinking that anyone would even want to use it. It was just for me and to get some more experience coding.:D

---

### Post by Grenad on 2011-06-28
Well isnt that refreshing to have an encouraging comment once in a while;). Thanks to everyone who helped me. For people I haven't directly referenced, I did read your posts, but my crippled phone browser would make it take an hour to write a sentence. I thank you too. I really like how I can ask the ubuntu community anything and actually get help.

---

### Post by CptPicard on 2011-06-29
You know, the reason why writing a compiler/interpreter is useful is that it makes you think a bit differently about programming languages, their structure and nature... it's about evaluating structure in a certain context.

That said, this is also the reason why I'd recommend you to learn some Lisp dialect, perhaps Scheme. Scheme is already a kind of generic interpreter, with all the needed stuff in the abstract that you need to easily implement other languages. It's also remarkably simple, so you get what you need but nothing more.

It is not surprising that GCC's internal data structures already are a kind of Lisp...

---

