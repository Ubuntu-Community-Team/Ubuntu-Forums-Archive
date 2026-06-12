---
title: "What Is the Most Suitable Programming Language for a Beginner?"
date: 2006-08-10
forum: Programming Talk
---

### Post by Christmas on 2006-08-10
Following threads like [this](http://www.ubuntuforums.org/showthread.php?t=231815) and [this](http://www.ubuntuforums.org/showthread.php?t=216476), I decided to make a poll that would clear somehow what programmers think about what should be the best or a good language to learn for a beginner.

---

### Post by [h2o] on 2006-08-10
I voted python.
My own programming background is QBasic -> Pascal -> C++ -> Lisp -> Ada -> Java -> Python

I think python is a good language to start learning **programming** because I think the most important is to learn how to solve general programming problems.
If the problem at hand is "Write a program that checks wheter a word taken from keyboard input is a palindrome" then I think it is better if the first thing the new programmer thinks is "Then I should probably check the first and last character in the string for equality and move towards the middle" instead of "How do I get input from the keyboard"?

There is plenty of time for a programmer to dive into lower level languages and memory management, and that is in no way unimportant, but I don't think it's the best way to start for most people. Yes, some people go directly to C or assembler or whatever, but that doesn't mean it's the best choice for everybody.

---

### Post by Tomosaur on 2006-08-10
I wish I'd started with shell scripting first. It'd work very well as a lightweight introduction to OO, but it's pretty neat as it is. I marvel at how much I can do with a script, when I see people struggling getting compiled programs working.

However, I cut my teeth on YaBasic for the PS2 (which was horrible, don't bother with it), and then Java and little bits of C at the same time.

---

### Post by mostwanted on 2006-08-10
Ruby is the most intuitive language to me. Examples:

```
exit unless "restaurant".include? "aura"
```

```
email = if at_hotel
           address = "why" 
           address << "@hotelambrose" 
           address << ".com" 
         end
```

> print( if at_hotel.nil?
          "No clue if he's in the hotel." 
        elsif at_hotel == true
          "Definitely in." 
        elsif at_hotel == false
          "He's out." 
        else
          "The system is on the freee-itz." 
        end )

---

### Post by Tomosaur on 2006-08-10
Yeah actually, Ruby is definately a great language to begin with. I haven't used it much, but when I have, it's very enjoyable. Things just seem so smooth with it.

---

### Post by eukhost.com on 2006-08-10
I would say Python, because it's a very clear language and it often reads like pseudocode. Its clean, simple and elegant and can do procedural or object-oriented. Ruby is abother good choice. With either one you'd have a good foundation for both system level scripting and web development.

---

### Post by skymt on 2006-08-10
I'd say Ruby. Python probably isn't the best choice because of the syntax idiosyncrasies (whitespace, list comprehensions). Ruby is a good introduction to OO (very important to get used to), and has similar enough syntax to other languages that learning those others (Java, C, Python, etc) wouldn't be too hard.

---

### Post by javarunner on 2006-08-10
java and then ruby:D

---

### Post by OneSeventeen on 2006-08-10
I guess I'll be the odd-ball and say PHP.

Mainly because it seems easy to get started with, and once you get the hang of it, you can grow to learn advanced concepts such as Object Oriented Design, inheritance, type-hinting, exceptions, class abstraction, overloading, reflection, and stuff like that.

It is very much a work from the ground-up type of language.

Now, with that said, I'm playing with python right now, and it looks pretty decent too, but I'd still have chosen to start with PHP then move to python.

I also wouldn't recommend PHP for stand-alone apps, so in that respect python might do better, but I'd still use PHP for web apps even after I get used to python, mainly because of the wide adoption of PHP and overabundance of tutorials and help sites out there.  (plus their manual is simple and very useful)

---

### Post by ifokkema on 2006-08-10
Have voted for PHP as well. As with most people, starting with an interpreted language seems best to me. PHP is very easy to learn, and can be used for many things. That said, it might be good to look at other languages after a while, because after learning PHP by taking code from forums and such, you may find yourself writing butt-ugly code :)

---

### Post by afilonov on 2006-08-10
I voted Python. It allows to start programming fast, and doesn't slow you down later. I wanted to vote Pascal, but I think Python is easier to learn and it gives you more powerful tools and three approaches to programming at the same time: procedural, functional and object-oriented.

---

### Post by Note360 on 2006-08-10
Python by far. I after a few days already have a nice little application out called UEC Ubuntu Easy Compiler. You either love or hate it.

---

### Post by LordHunter317 on 2006-08-10
> **skymt said:**
> I'd say Ruby. Python probably isn't the best choice because of the syntax idiosyncrasies (whitespace, list comprehensions).I'm not sure which is worse, idiosyncrasies or just ugliness.  The industry seems to perfer the later over the former.

> and has similar enough syntax to other languages that learning those others (Java, C, Python, etc)In that it shares some common operatores, {} to delimit blocks, and some common keywords, sure.

I'm linking to this post I made: [http://www.ubuntuforums.org/showpost.php?p=1357281&postcount=87](http://www.ubuntuforums.org/showpost.php?p=1357281&postcount=87), because it accurately sums up my feelings on the matter.

---

### Post by xtacocorex on 2006-08-11
I put Python, but wanted to put FORTRAN.

FORTRAN was the second language I learned after BASIC. It has easy to remember syntax, but OOP isn't supported unless you get a F2003 compiler and they're not out yet.

I tried grasping OOP with C++, but couldn't. Python got me to understand it. Python is very easy to grasp, IMO.

---

### Post by Frostmourne on 2006-08-11
Though PHP was the first language I learned, I would say Ruby is the best language to learn first.

---

### Post by Note360 on 2006-08-11
I would say (I already said Python) any of the interpreted languages (Python, Perl, Ruby, Java). 

Perl is a weird language that is weird and has weird statements much like the weird one here (Perl can be super efficient though to it is up to your mind really Perl does everything its just their are 500000000 ways to do something and if you use the wrong way the community beats you up). Perl 6 looks to be promising but it looks to be a long wait to.

Ruby is a nice elegant language that used to contain many Perl-isms. I learned it first (kinda), but I moved to Perl for some reason. Ruby is OO unlike Perl. However, it is currently slow and the community is mostly Japanese at the moment.

Python is a super elegant language. The community is amazing and the syntax is simple. It is powerful, and fast, the only thing it suffers is the fact that their are only a hand full of ways to do each operation.

Java is C on steroids. It is much cleaner than C and is OO. I personally would learn Python or Jython instead of Java for a first language. Oh, Java seems to be a popular Enterprise language used by big companies.

---

### Post by LordHunter317 on 2006-08-11
> **Note360 said:**
> Java is C on steroids.It is nothing of the sort.  It shares some syntax and that is really it.

---

### Post by mostwanted on 2006-08-11
> **Note360 said:**
> I would say (I already said Python) any of the interpreted languages (Python, Perl, Ruby, Java). 

Java isn't interpreted, it's precompiled. Compare Java to C#, not to scripting languages.

---

### Post by neilp85 on 2006-08-11
Another vote for Python. Not only is it simple to pick up, I love the fact that there's a library for just about everything.

---

### Post by themusicwave on 2006-08-11
I voted for Java and thats not just because it's my favorite.

First off, learning good Object Oriented Programming(OOP) is important.  And from my experience, Java makes it pretty easy to implement good OOP.

Second, The Java API is the best I have ever seen.  The MSDN libraries are just awfule in my opinions, the Java API makes them look terrible.  You can lok up any of Java's built in classes in the API and get lists and explainations of everything.  You can even see what functions return an instance of that class.  Here is a link to the API [http://java.sun.com/j2se/1.5.0/docs/api/]("http://java.sun.com/j2se/1.5.0/docs/api/")

Finally, you can learn good high level programming without all the details.  Learn loops, inheritance, polymorphism, if/then, ect.  Without needing to learn lots of low level stuff.  You can learn that later when you have a good grasp of the big concepts.

My second choice would be C++ as it is widely used and is powerful and native compiled.

As a side note, if you plan on obtaining a degree in Computer Science, Software Engineering(like me!) or Computer Engineering in the U.S., don't learn python.  In my 3 years of college thus far it has not even been mentioned.  All my assignments were mainly in C++ or Java.  We also learned Perl, C#, Scheme and Assembly.

I've learned/used several languages over the past 6 years or so.  Including C++, C, C#, Perl, Assembly, Scheme, VB, and Java.  I'm no guru in most of them(Really only good with C++, C#, Java), but Java was easiest for me to learn.

---

### Post by Christmas on 2006-08-11
Up to now 61 voters and Python has 49% of the voters, which makes it preffered by 50% of the users who chose from at least ten languages.
[quote=themusicwave]As a side note, if you plan on obtaining a degree in Computer Science, Software Engineering(like me!) or Computer Engineering in the U.S., don't learn python. In my 3 years of college thus far it has not even been mentioned.[/quote]
That's exactly what happens to me. Only C/C++/Pascal/C# and Java were mentioned at my university, I didn't even hear about Python until I switched to Linux. It looks like it's used almost only on Linux machines.

---

### Post by LordHunter317 on 2006-08-11
> **themusicwave said:**
> And from my experience, Java makes it pretty easy to implement good OOP.It makes it possible to implement good OOP.

However, the Java API is rarely an example of good OOP.

> Second, The Java API is the best I have ever seen.It's vastly inferior to the C++ standard library everywhere they overlap.

---

### Post by ember on 2006-08-11
> **Christmas said:**
> 
That's exactly what happens to me. Only C/C++/Pascal/C# and Java were mentioned at my university, I didn't even hear about Python until I switched to Linux. It looks like it's used almost only on Linux machines.

Well, that depends. Here in Germany there are several universities that teach python. For me it has been a topic in my third semester.

---

### Post by Note360 on 2006-08-11
Java is technically interpreted. When I say C on Steroids I just meant it is powerful and easier to use than C (in some ways).

---

### Post by LordHunter317 on 2006-08-11
> **Note360 said:**
> Java is technically interpreted.Sure, in the same manner all languages are interpreted.  It's certainly not *source* interpreted, which is what most people say when they say interpreted (ignoring things like bsh).

Being compiled to bytecode doesn't make you an interpreted language.  By that definition, all languages are interpreted because the machine code on any modern processor is decoded before it's execution.

> When I say C on Steroids I just meant it is powerful and easier to use than C (in some ways).That still doesn't make any sense.  When I say they have nothing in common but some syntax, I really meant it.

---

### Post by MoxJet on 2006-08-12
I began with QuickBasic, it worked quite well, but I still have some problems to make classes more naturally in C++.
However, I vote for Python. As mentioned in earlier replies, it looks like pseudocode and it also forces the user to write code that's easy to read with the indentations.
I don't know Ruby and I looked on the code posted here and to me it looks rather confusing.

---

### Post by ifokkema on 2006-08-12
> **MoxJet said:**
> I don't know Ruby and I looked on the code posted here and to me it looks rather confusing.
I have to agree, when I look at that code, it makes me wonder what would happen if someone, even with years of experience in Ruby, would try to learn any of the other popular languages... quite a learning curve then, I suppose.

---

### Post by tbrownaw on 2006-08-12
If you're completely new, I'd say start wish shell, or even just playing with a command line for a while. Then once you have a basic idea of how things work (or aren't completely new), move up to some more solid scripting language, like perl or ruby (or python). Later if you're writing programs big enough to be annoyed by the lack of static checking and type safety, move on to a real language that provides these.

---

### Post by [h2o] on 2006-08-13
> **LordHunter317 said:**
> Being compiled to bytecode doesn't make you an interpreted language.  By that definition, all languages are interpreted because the machine code on any modern processor is decoded before it's execution.
Isn't that a little far fetched? Sure, the machine code is translated to a lower level (micro instructions, or directly to control signals) but that layer is very seldom visible or even available to a software programmer.
Java is by my definition interpreted since it requires a Java Virtual Machine to interpret the compiled bytecode. A program compiled to machine code do not require this, since the processor is able to read and "interpret" this all by itself without the help of another program.

---

### Post by LordHunter317 on 2006-08-13
> **'[h2o] said:**
> Isn't that a little far fetched?Not really.  It meets the definition that allow Java and any other JVM language to be considered "Interpreted".

> but that layer is very seldom visible or even available to a software programmer.JVM bytecode isn't directly available to the program either, at least in Java proper.  You can't do "inline bytecode" or anything of that sort.  It would be possible to generate raw bytecode if you really wanted to, but there's little point.

> Java is by my definition interpreted since it requires a Java Virtual Machine to interpret the compiled bytecodeAnd machine language requires the proper CPU to interpret it's compiled bytecode.  Like I said, the definition is poor.

BTW, you don't have to compile Java to JVM bytecode.  It's not a requirement.

> A program compiled to machine code do not require this,Yes, it does. I can't run IA-32 assembly on PPC.  The proper hardware (or emulation thereof) must be present.

> since the processor is able to read and "interpret" this all by itself without the help of another program.See, you just proved my point.  You can't seperate the scenearios.  Your seperation is that one is done by software and one by hardware, but that's frankly a crap reason.  It's possible to emulate CPU hardware in software (e.g., bochs).  And it's possible to write a Java CPU that run java bytecode, removing the need for a JVM.

---

### Post by TheAberrant on 2006-08-13
For anyone thinking of comparing languages, I highly suggest this link:
[http://www.cabochon.com/~stevey/blog-rants/tour-de-babel.html](http://www.cabochon.com/~stevey/blog-rants/tour-de-babel.html)

I agree with mostly everything there, but I have only a little experience with a few of the languages.  Personally I like the idea of python, since I despise poorly formatted code, but I understand that people don't like that.  However, as a beginner, one should be forced into formatting otherwise he/she won't learn it properly.  I also liked Java, simply for its simplicity and ease in creating GUIs, though truthfully I haven't done any GUI work except for that and Visual Basic.

One thing to look at is what are the goals of a beginning programmer?  My personal experience is that I wanted to see results, and see them now.  The prettier it looked, the better, too.  I always hated spending hours on a project only to see it spit out one line of output.  For this, VB is definitely a good thing, though also a poorly designed language.

Anyways, just my two cents.

---

### Post by [h2o] on 2006-08-13
> **LordHunter317 said:**
> See, you just proved my point.  You can't seperate the scenearios.  Your seperation is that one is done by software and one by hardware, but that's frankly a crap reason.  It's possible to emulate CPU hardware in software (e.g., bochs).  And it's possible to write a Java CPU that run java bytecode, removing the need for a JVM.
Sure, but the case is that we have CPU:s that run machinecode instrusctions, and a JVM that interprets java (bytecode or source) to machincode for execution. You can't really get away from the fact that Java (or any language requiring an interpreter to run on a general CPU (x86, PPC, M68k, or whatever) has an extra layer of interpretation. I can agree with you that all languages are interpreted in some way, but some are interpreted at different levels. Special hardware is not really interesting since that is not what people in general use.

What matters is that code compiled to native machine code is executed by the CPU directly, and interpreted languages such as Java or Python take a detour through an interpreter.

---

### Post by LordHunter317 on 2006-08-13
> **TheAberrant said:**
> For anyone thinking of comparing languages, I highly suggest this link:
[http://www.cabochon.com/~stevey/blog-rants/tour-de-babel.html](http://www.cabochon.com/~stevey/blog-rants/tour-de-babel.html)Unfortunately, that link has a number of technical errors:> [Tour De Babel](http://www.cabochon.com/~stevey/blog-rants/tour-de-babel.html)
You just have to know C. Why? Because for all practical purposes, every computer in the world you'll ever use is a von Neumann machine, and C is a lightweight, expressive syntax for the von Neumann machine's capabilities.This is incorrect.  C requires more than what the "formal" definition of a von Neumann machine requires (e.g., pointers).  At the same time, it doesn't require shared storage of text and data, which is the only requirement to be a von Neumann machine.

> The von Neumann architecture is the standard computer architecture you use every day: a CPU, RAM, a disk, a bus.Just to reemphasize the above, this is a totally wrong definition.  A von Neumann architecture is one that uses shared storage for program code and data.  That's it.  Disk, bus architecture (obviously there must be a bus for data transfer) and type of memory don't play into it.  There's no requirement for the memory to be random-access (though it's difficult to imagine how you'd have shared memory for code and data that wasn't) nor any requirements imposed on the CPU beyond a program counter.

> There are other kinds of machines too. For instance, there are Lisp Machines, which are convenient 1950s realizations of Lisp, a programming language notation based on the lambda calculus, which is another model for performing computations.This just further demonstrates the author's confusion about hardware architecture. AFAIK, all Lisp machines every build were von Neumann machines.  Generally, you compare von Neumann architecture to Harvard architecture (code and data are in seperate storage).  LISP has nothing to do with machine type.  


> You also have to know C because it's the language that Unix is written in, and happens also to be the language that Windows and virtually all other operating systems are written in, because they're OSes for von Neumann machines, so what else would you use?There are a few problems here:[list][*]The argument is circular.  You have to know C because the OSes were written in C.  They were written in C because they operate on von Neumann machines.  Can't do that.[*]You don't need to know C to do UNIX or Windows programming anymore.  You never really *had* to, though that's what most of the standard libraries were in.  But the people doing Win32 programming on Windows is shrinking by the day, so it's obviously not a requirement anymore.   MS hasn't shipped a dedicated C compiler in ages.[/list]

> They teach Scheme at MIT and Berkeley to new students for a semester or two, and the students have absolutely no clue as to why they're learning this weird language. It's a lousy first language, to be honest, and probably a lousy second one too. You should learn it, eventually, and not as your first or second language.This pretty much shows that he's missed the point of what MIT and Berkeley teach Scheme to *computer science* students.  It's also pretty telling that he probably doesn't know what computer science is.  Computer scientists don't need to be able to write applications, much like a physicist doesn't need to understand how to phyiscally construct an atomic bomb.  That doesn't make the job any less important, but there's a distinction between study of computation (CS) and application of computation (software engineering and programming).

Even still, you have to study theory first.  No engineering major in the world started studying applied stuff first.  They started with PHYS 101 and 103, which is classical Newtonian physics.

>  Neither is C, but C isn't "Object-Oriented", and object orientation is in no small measure about making your programs know about themselves. This is totally wrong.  Object-orientation is about providing a method for combined code and data encapsulation and a method for providing a convinent way to select different implementations to operate on the same data (i.e., polymorphism).

Introspection has nothing to do with it.  Simula and original versions of Smalltalk (the original OOP languages) didn't support any sort of introspection mechanism, in the sense of what Java or C# provides.

> C++, on the other hand, is essentially un-parseable, so if you want to write smart tools that can, for example, tell you the signatures of your virtual functions, or refactor your code for you, you're stuck using someone else's toolset, since you sure as heck aren't gonna parse it. And all the toolsets for parsing C++ out there just plain suck.I realize this was probably written well before these tools existed, but C++ is LR(infinity) parsable.  Efficent LR(infinity) parsers have only come about in the last few years or so.

> C++ is dumb, and you can't write smart systems in a dumb language.C is dumber than C++ in all aspects, so this is utter hypocrisy.

>  Languages shape the world. Dumb languages make for dumb worlds.Computers are rather dumb machines.  I mean, they can only add '1' and '0'.

> The biggest thing you can reasonably write in C is an operating system, and they're not very big, not really. They look big because of all their apps, but kernels are small. Kernels aren't small, unless they don't do much.  And there is way more to an OS than the kernel.

> But operating system kernels are at most, what, maybe a million lines of code? So I'd argue the biggest system you can reasonably write in C++ is maybe 10 million lines,If I can write 10x more C++ than C, then I know it's possible to write at least 100 million lines.  The problem with assumptions is that they tend to make an *** out of you, but not so much me.

> Stuff takes forever to do around here. An Amazon engineer once described our code base as "a huge mountain of poop, the biggest mountain you've ever seen, and your job is to crawl into the very center of it, every time you need to fix something."
...
It's all C++'s fault. Don't argue. It is. We're using the dumbest language in the world. That's kind of meta-dumb, don't you think?He's treating bad software design, a possibility in any language, as a flaw of the language.  It's obviously.  Such people aren't to be trusted.

> And when I heard that the inventor of STL was on record as saying he hated OOP, I thought he was cracked. How could anyone hate OOP, especially the inventor of STL?Seeing as virtually all of the STL doesn't use OOP techniques, it makes sense.  And his justification is quite sensical: you can create far higher-order abstractions using parametric polymorphism than you can with what OOP's runtime polymorphism (dynamic binding).

It's impossible without parametric polymorphism to write STL algorithms that worked on plain C pointers and pointer math.  You can't do with OOP, because pointers aren't objects.  That's just one practical example, but there are more.

What this shows is he just plain out-right doesn't understand C++ at all.  Which is sad, because despite all the language's problems, C++ probably has the best standard library of any language out there.

> On the one hand, Java frees you up from many mundane and error-prone details of C++ coding. No more bounds errors, no more core dumps. Exceptions thrown point you to the exact line of code that erred, and are right 99% of the time. Objects print themselves intelligently on demand. Etc., etc.Wrong, wrong, wrong, wrong, and wrong, all quite obviously so.  Jesus, has this guy programmed in any of these languages?

> Compared to C++, Java as a language is about even. Well, scratch that, it's a lot better, because it has strings, oh man, how can you use a language with lousy string support. C++ strings are vastly superior to Java strings.  Only someone who hasn't looked at the actual implementation details would say otherwise.

> But Java's missing some nice features from C++, such as pass-by-reference(-to-stack-object),Java doesn't have pass-by-reference period.

> You can get stuff done really fast in Perl, which is what really matters, in the end.This is terribly and fundamentally wrong.  Code spends more time (and costs more) to maintain then to write the first time.  As such, what really matters is doing fast so that future maintaince is easy.

Frankly, that article was poor trash.  He clearly doesn't really understand the languages he's supporting or railing against, which is oh-so-common in industry.

---

### Post by LordHunter317 on 2006-08-13
> **'[h2o] said:**
> You can't really get away from the fact that Java (or any language requiring an interpreter to run on a general CPU (x86, PPC, M68k, or whatever) has an extra layer of interpretation.Yes, I can.  I can compile it to machine code directly.  There's no requirement in any of these languages to use the bytecode format.  Not Java.  Not .NET (in fact, .NET 2.0 on Windows includes a precompiler and precompiles every .NET standard library on install.  Look at the docs for ngen.exe)  Not Python.  Not Perl/Parrot.  Emacs-Lisp does, but it would be possible to write a Emacs fork that executed native code Lisp libraries.  

> I can agree with you that all languages are interpreted in some way, but some are interpreted at different levels.In this case, the distinction isn't interesting.

Source interpretation is interesting because it means an actual change in my build process and development lifecycle.  Bytecode intepretation does not mean that in any, shape, or form (unless maybe I'm targeting multiple physical architectures, because I don't have to build for every one of them.  But that's really a minor detail, as that can be handled *automagically*).

> What matters is that code compiled to native machine code is executed by the CPU directly, and interpreted languages such as Java or Python take a detour through an interpreter.But it doesn't.  That really doesn't change anything about how we write code or our development processes.  It only changes it in the case of source interpretation.

---

### Post by Jessehk on 2006-08-14
I learned C first (loved it), then C++ (nice features, but feels awkward), then Python (fantastic), and finally Ruby (amazing design, but increasingly Perl-like in practise. Not good.).

If you want to get things done in a good (if slightly inconsistent) language, then use Python.

I know it makes no sense, but I still like C. Something about combining several "raw" parts into a structured whole is very satisfying.

---

### Post by [h2o] on 2006-08-14
> **LordHunter317 said:**
> But it doesn't.  That really doesn't change anything about how we write code or our development processes.  It only changes it in the case of source interpretation.
Sorry, I agree with most of what you write here, and I admire your obvious knowledge of this stuff. But I really can't agree on this. The development process isn't interesting in this case. It does not change the fact that Java bytecode is run through an interpreter to be executed (if we assume that we are speaking about general hardware, which I was since specialised hardware isn't really interesting in this case).

I think it is "important" to separate languages that compile to native machine code from those requiring an interpreter. The fact that the difference in theory might not be huge (I admit that) the practical difference is quite big. A program compiled to x86 machine code should run on any x86 compatible processor. A program compiled to Java 5.0 bytecode requires a JVM that can handle Java 5.0 (but does on the other hand don't need a specific processor).

I guess you could compile Java directly to machine code (I don't see why shouldn't be able to) but the question is why would you? And is there anyone doing it? If you have any information on people who are actually doing this, and why, then I am happy to read about it.

Nice bashing of the article above. :)
I actually think Lisp is a quite nice first language of choice. My university teaches it as a first language as well, to teach functional programming paradigms.

---

### Post by LordHunter317 on 2006-08-14
> **'[h2o] said:**
> The development process isn't interesting in this case.Yes, it is, because it's the only thing that changes in the whole process.  It is the only meaningful difference that exists.

> It does not change the fact that Java bytecode is run through an interpreter to be executed**But no, that's not necessarily true.**

GCJ, for example, compiles to native code directly unless you explictly tell it not to.

> I think it is "important" to separate languages that compile to native machine code from those requiring an interpreter.I don't.  You haven't given a single valid reason why we should seperate them.

> he fact that the difference in theory might not be huge (I admit that) the practical difference is quite big.But it's not.

> A program compiled to Java 5.0 bytecode requires a JVM that can handle Java 5.0But a program written in C requires the C standard library.  A program written in C++ requires the C++ standard library.

> (but does on the other hand don't need a specific processor).Again, that's not necessarily true anyway.  JNI makes it easy to tie yourself to a specific architecture without any trouble.

> I guess you could compile Java directly to machine code (I don't see why shouldn't be able to) but the question is why would you?Because the runtime cost of JIT is too high?

I'm not sure it makes practical sense, since it's not possible for most server applications (you can't do it for a servlet web application, for example).  But it certainly can be done and some people do it.

---

### Post by [h2o] on 2006-08-14
Haha, okay, I admit to be defeated :)
I did not know that GCJ compiles to native code, I'll try to remember that.
I will probably still think of java, python, etc as interpreted languages inside my head, but at least now I will think of it a bit differently.

Thanks for a nice debate. :cool:

---

### Post by LordHunter317 on 2006-08-14
The other thing to remember is that the definition is blurred anyway.  One can interpret C and there are C interpreters out there.  However, that's never done in production software.

One can interpret Java source anad there are Java source interprerters out there (bsh).  That actually sees more use, but not much use.  It's also limited in what it can do.

One can compile Python to bytecode, but it's rarely done except on the local machine.

---

### Post by JAwuku on 2006-09-13
I haven't programmed in ages, the last time was when I used BBC Basic.:)
It was the best natural procedural programming BASIC when it was in use 20 years ago. I still yet am trying to understand the concept of OO programming, and thus I'm now looking into Python.

---

### Post by Avenue on 2006-09-15
Alright so, as a beginner myself (been at this programming thing for 9 months now), my honest opinion for a newbie is to learn a newer yet non-OOP version of the BASIC language.  I started with Liberty BASIC which is both functional and has an IDE for event-driven GUI design.  LB is only a few years old and allows a newbie to get the hang of conditional statments, looping, etc without getting all turned around over namespaces, classes and objects.  The LB forum is extremely helpful and surprisingly large (reminds me of this forum, actually).  

When I decided that I wanted to pursue programming further and consider it as a career switch, I went to a local college for C# and OOP training.  I'd already been building my own small personal programs in LB at this point but I have to be honest and say that at first OOP *REALLY CONFUSED THE LIVING HELL OUT OF **ME*. Having some experience with BASIC allowed me to focus on the syntax and rules of C# and not have to worry about the basics of programming (like the aforementioned conditional and looping statements).  Some folks in the classes did not have any exposure to programming at all, and they were terribly confused to the point of tears.  My opinion is that the C family and even Visual Basic can be a bit much at first, ease into it with a "lighter" language to build confidence and keep it FUN, then move on from there.  

Also, as you begin to build on concepts (which will not take long at all), practice, Practice, PRACTICE!!!  You will need to do a little bit every single day, like learning to play the guitar.  

As I am a newbie programming student the above advice worked for me.

---

### Post by Garyu on 2006-09-15
PASCAL is definitely the best one to start with in my opinion, like buying a copy of Borland Delphi and *kapow* you got yourself your very own program. Also, pascal makes for fast and small executables on compilation, much better than BASIC.

Then again, I haven't tried Python yet...

---

### Post by chris hyperstring on 2006-11-17
i would vote lisp if it was there, but i had to vote other! i find lisp interesting i have been it about 2 months (mostly cos i couldn't work out html!) and i have got started on a couple of projects, java is a dog same as c++, yeah they are both crap, you can't do anything like what we have done with  in the same amount of lines of code! and with lisp you start from the bottom up!

---

### Post by engineer on 2006-11-17
completely depends on what you want to do. 

simple automation tasks can be done easily with python or bash

when it comes to user interface programming, i would recommend c# or java. though i don't like the concepts, but i think they're easy to learn

---

### Post by chris hyperstring on 2006-11-17
personelly i think all the c family and java should burn in hell, but still can't have everything! lol, lisp can do what ever you want! you just gotta build it from the bottom up! which totally screws c and java programmers!

---

### Post by Steve Pullman on 2006-11-17
Well I am new to Linux and programming.
I am learning Scheme because it will (hopefully) teach me programming concepts without drowning me in syntax.
If I later need to use another language I can concentrate on learning the 'language' having already learnt the 'programming'.

---

### Post by dataw0lf on 2006-11-17
> **Steve Pullman said:**
> Well I am new to Linux and programming.
I am learning Scheme because it will (hopefully) teach me programming concepts without drowning me in syntax.
If I later need to use another language I can concentrate on learning the 'language' having already learnt the 'programming'.

That's an excellent point, and one that isn't brought up too often.  This is why I endorse Python as a great first-time language;  as a 'pragmatic' language, it isn't loyal to one programming paradigm, and you spend much less time learning language idiosyncracies than most other languages.  This transparency of the language to actual design practices is excellent.  For beginners, learning Perl, PHP, Java, etc and the multitude of language specific barriers can be quite hampering.

---

### Post by shawnhcorey on 2006-11-17
6502 mini-assembler on the VIC 20.

Why? Because there is nothing like the lack of resources to focus the mind. How do you implement your glorious idea in just 2K of RAM? How do you multiply with only three 8-bit registrars? The answer: you learn to ask for help.

I have been working as a Senior Programmer for many years and the one thing I would like to see from recent graduates is the ability to ask for help. Our education institutions stresses individuals efforts; which is great for determining the competence of their students, but is lousy at getting them to work as a team. Since I can't get them to change their ways, I would prefer a junior programmer that asks lots of questions over one that tries to solve everything on their own. Someone who asks early on how to do something is more likely to get things correct; rather than someone who replies, when asked how things are going, "Fine." With that person, it is only after they turn their work over to you do you realize there are some serious flaws in it; flaws that could have been avoided if they had asked earlier.

The best programming language for a beginner is one that makes them realize that they are part of a greater community. One that is not only prepared to help them, but one that is eager to do so.

---

### Post by The Warlock on 2006-11-17
I'd say get started with C or C++ and once you've got the basics down, learn some assembly language. You get a really good grasp on how everything interacts at a very deep level that way.

On the other hand, that way is very difficult (not least of which because x86 asm has around eleventy grillion different instructions). I guess it depends on how serious you are. That's the way I got started, mostly because that was how my college decided to run things.

EDIT: Avenue, I hate to say this, but the likely reason why OOP confused you is because you were used to BASIC. BASIC is really a terrible place to start; you'll develop horrible habits that really shouldn't carry over into any other language.

---

### Post by Steve Pullman on 2006-11-17
> **shawnhcorey said:**
> 6502 mini-assembler on the VIC 20.

Why? Because there is nothing like the lack of resources to focus the mind. How do you implement your glorious idea in just 2K of RAM? How do you multiply with only three 8-bit registrars? The answer: you learn to ask for help.

Oh heck yes! Today its so easy as RAM isn't a problem.
Gosh I remember my Sinclair days with 1K of RAM! Just stop and think about that everyone one...whole...kilobyte.
I wonder how many of todays code-monkeys could cope?
Not just coding, but for graphics too...sprites anyone?
You try designing an evil monster on an 8x8 grid.
Hah! programmers today never had it so good.

---

### Post by THaugland on 2006-11-17
ML/SML/LISP. You will never truly learn to make the best of recursive code before you are fluent in a function programming language. At work we use OOP, but when I look at my colleagues code, it is pretty easy to see who has any FP experience.

6502 mini-assembler on the VIC 20 or maybe 6510 mini-assembler on the C64 if you are the lazy sort.

---

### Post by shawnhcorey on 2006-11-17
Sigh. You read the first part of my message but ignored the second part.

There is no best language. What is best is to learn how to cope with many other developers working on the same project as you are. Learn to communicate.

Languages come and go. Operating Systems come and go. But what is truly useful is learning to use those facilities that are available to you. Learn to ask questions when you don't know. Learn to say the words, "I don't understand." Or, "I don't think that is right."

There are many languages out there, each with its strong points and its weak points. But language does not a programmer make.

Like I said, I would prefer to put up with a beginner programmer who asks a lot a questions, than one who tries to solve all problems without saying a word.

---

### Post by stalefries on 2006-11-19
Python, because I feel left out when I don't go with the crowd. :) Also, seems to be pretty good (from what little I've dabbled)

---

### Post by deanlinkous on 2006-11-19
pascal

---

### Post by pgatrick on 2006-11-19
I can't make up my mind.. I'd say either lisp, ruby, or c. Lisp, because why not? It's not so hard, and it's different. Any language you learn afterwards will likely be quite different from it, and seeing how to do the same thing in wildly different ways will probable help you understand programming in general better. Ruby I'd reccomend just because it's looks nice and clean, it's ridiculously simple, and powerful enough for most things. And then c, because it's probably the most useful language you can learn. And how can something be difficult if you have nothing with which to compare it? It's a small language too, so it shouldn't take long to learn, after which you can concentrate on doing it well. :)

---

### Post by handy on 2006-11-20
I voted Python, which I'm currently enjoying learning.

Programming for my own pleasure & nothing else.

In the Amiga days I used a horrible AmigaBASIC & a beautiful CanDo.

After moving on to a windoze machine, I bought Visual Basic 5.0 when it was released, & thought it was so ugly, after using CanDo, that I gave it to an ex-friend!

I'm looking forward to creating with Python, it will keep my mind growing as my body *matures*...

---

### Post by cantormath on 2006-11-20
> **Christmas said:**
> Following threads like [this](http://www.ubuntuforums.org/showthread.php?t=231815) and [this](http://www.ubuntuforums.org/showthread.php?t=216476), I decided to make a poll that would clear somehow what programmers think about what should be the best or a good language to learn for a beginner.

I say python then c++

---

### Post by handy on 2006-11-21
**I agree with Roger Penrose 100%!**

---

### Post by deanlinkous on 2006-11-21
I would also say ruby.....

---

### Post by adamkane on 2006-11-21
Asking what's the best programming language is like asking what's the best flavor of ice cream. There isn't one!

This same comes up over and over. It's silly.

I like ruby and python.

---

### Post by rahaman on 2006-11-21
i'll vote for C Language. because its a system level programming language. if u learn this language its easy for you to learn the other languages like C++ or JAVA.

---

### Post by handy on 2006-11-21
> **adamkane said:**
> Asking what's the best programming language is like asking what's the best flavor of ice cream. There isn't one!

This same comes up over and over. It's silly.

I like ruby and python.

I agree with you. 

But the question was "What is the *Most Suitable* Programming Language for a Beginner?"

We have different ideas about what & how we want to program, & different reasons for doing it, for some (like me) its a purely recreational creative outlet, for other's its a means to an end.  Lots of different ends out there, money for some, a problem that needs to be solved for self, for others, the possibility of  enhancing other peoples lives through the results of your programming, & on it goes.

There will be as many different points of view as there are people to have them, & they are all valid. 

:)

---

### Post by chris hyperstring on 2006-11-22
in reality i don't think there is a suitable language for a beginer, which ever you try its still like climbing a vertical mountain! at least thats what i think anyway!
        chris

---

### Post by Ansible on 2006-11-22
I'd recommend an interpreted language like python or ruby.  NOT C++, a friend of mine took an intro to programming course that used C++, and I saw first hand the needless confusion and discouragement that produced.  C++ is a cool language and all, but it has a high percentage of BS-to-get-together to make it work.  Hello world is far more difficult with C++ than with an interpreted language like ruby.

The main point with a beginner's language is to get used to the concepts of flow of control, variables, and maybe objects.  A first language should be fun, and you should be able to get some results out of it quickly without messing around with a bunch of extra junk.  You shouldn't have to bother with tedious stuff like namespaces, makefiles, IDE projects, includes, etc, before you can get into the fun part, getting creative and getting some quick feedback from the code.

---

### Post by daz4126 on 2006-11-22
I can't believe Ruby isn't there as an option - it has such a great syntax, almost like English at times, and helps to develop good OO practises since everything is an object. 'Learn to Program' by Chris Pine is a great introduction to programming that uses Ruby.

DAZ

---

### Post by handy on 2006-11-22
A Python g'day...

**print "Hello, World!"**

It can't get any easier or more straight forward than that!

---

### Post by chris hyperstring on 2006-11-23
well lisp is damn strait forward, you don't even need to put print in front of hello world --> "hello, world" <-- thats all you need (without the arrows) but its putting everything together to make the program that has to be the complicated bit about it! and the same must go for every language difficult until its fluent, it kinda like learning a foreign language, up hill untill you start understanding it fluently, oh well
           
             chris

---

### Post by kinson on 2006-11-23
I've done some Java, C++, Prolog(?), VB6, and just touched on C#.

I'd say it'll depend on what the person whats to program for. If its just to do some simple stuff, then I'd suggest Java. If its for getting more in depth knowledge of computers/programming. I'd say C/C++.

I personally fall into the latter category, but I'm struggling sometimes with C++ :( So I was thinking of giving Python a try soon.

Cheers,
Kinson

(Btw, I voted Java :p )

---

### Post by pedrotuga on 2006-11-23
One more vote for PHP. I knew from the beggining python and ruby would have al of votes... don't take this in the bad way but in my opinion that's a bit due to some hype around these languages.

I never understood why is php so hatted.

Anyway, i learned PHP by mysealf and i worked for one year as a php programmer, it's dead easy. No i am learing python, it's cool, i like the way the code gets so clean. But, i am having sooooo much more troubles to learn it. PHP was a lot more simple, at least for me.

Aren't we all here assuming that POO is the only way to go? In my opinion that's the biggest error of basically every new language. If one wants to make little scripts for simple tasks what's the POO for?

Shellscript is a good option for begginers as well.

---

### Post by earobinson on 2006-11-23
IMO java and python (or any other interactive language) is a good place to start

---

### Post by Paul-hyperstring on 2006-11-24
I think Common Lisp is a great language for a novice, but not if you want to learn anything else because it is quite different.

(print "hello world")

Thats common lisp.... but try this in another language

(defvar *store* (make-hash-table))

(defun store-it (name value)
    "Store value in hash table"
    (setf (gethash name *store*) value)))

(defun find-it (name value)
    "Get value from hash table"
    (gethash name *store* value)))

(store-it harry "This is a value")
(store-it sally 35)

(print (find-it harry))
(print (find-it sally))

I'll leave you to work out what's going on here, Lisp is full of functions and we have some links on our site to places you can get info at [http://www.hyperstring.net](http://www.hyperstring.net) (lisp software house)!

Paul.

---

### Post by ifokkema on 2006-11-24
> **pedrotuga said:**
> I never understood why is php so hatted.
Well, my vote was for PHP as well, but I do understand that compared to other languages there are some "general" functionality that doesn't work or doesn't work properly in PHP. No threading/concurrency, no namespaces, good OOP support took a while, idem with exception handling etc. Also, some programmers have a problem with PHP being so easy to learn, causing non-experienced programmers to produce Very Bad code including lots of Very Serious sercurity issues :)

> **pedrotuga said:**
> Aren't we all here assuming that POO is the only way to go? In my opinion that's the biggest error of basically every new language. If one wants to make little scripts for simple tasks what's the POO for?
Sometimes when I POO I can think my program over properly. When I PEE I don't have the proper time to think about the structure.

Sorry, that was a joke. I take it you meant OOP, Object Oriented Programming.

I agree that OOP can make learning a language harder, if you are forced into it (i.e. Java). For simple tasks, one does not need OOP. I created relatively large projects without ever touching OOP, nowadays I use it in the places I see a big advantage for it. OOP in PHP4 is relatively slow, though.

> **earobinson said:**
> IMO java and python (or any other interactive language) is a good place to start
Do you mean interactive as in with a shell or did you mean interpreted?

---

### Post by addicted68098 on 2006-11-24
I think PERL would be the best, many people program PHP in an odd way and Ruby is confusing, and PERL has C++/C like conventions. Python is also a good language like that, but ruby is also a web language and people can "results" faster with that.

---

### Post by ifokkema on 2006-11-25
> **addicted68098 said:**
> many people program PHP in an odd way
What's odd to you? Lack of coding style? Not efficient?

> **addicted68098 said:**
> ruby is also a web language and people can "results" faster with that.
Somehow it seems easier to think of something to program when it comes to the web. Simple things to extend your website (e.g. telling you "good morning", "good afternoon", "good evening" based on the time) are quickly done, more fun than "hello world" and can get you to know a language a bit.

---

### Post by gga73 on 2006-12-24
Ruby.

---

### Post by Verminox on 2006-12-24
I voted for PHP as well. Learning an interpretted language with good error reporting that is related with web design serves as a good start point for beginners, especially if they have already taken intrest in learning HTML/Javascript.

You can learn the basic style of programming (control structures, conditional statements, for/while loops, arrays, functions, etc.) without much of a hassle. Due to its dynamic typing and automatic garbage collection, you don't have to worry about that as well. You also get an introduction to OOP (although PHP OOP is painfully pathetic). Also, as PHP is a very common language there are a lot of people out there who can help you in forums, etc. and loads of user-friendly tutorials.

I guess this is a similar concept to Pyhton but I never got around to learning Python :\

I guess once PHP is done, C/C++ becomes really easy. At least for me it was, that was the same route I took. All i had to learn extra in C was strong typing (which I actually like, and makes me dislike PHP now) and memory management (which was my only hurdle in learning C, but C++ helped me tackle that too).

Without inviting a flamewar, I just want to state an *opinion*.... I don't think Java is a good start for beginners. Someone who doesn't know what arrays and if() statements are shouldn't have to learn the concepts of OOP before making a Hello World program *opinion* Those who started with Java and ended up wiz-programmers... hats off to you guys :D

---

### Post by samjh on 2006-12-25
A very difficult question.  It all depends on the person who is wanting to learn.

My own background is:
MS-Basic -> Turbo Pascal -> Java -> assembly (Motorola, AVR, and Pic) -> C -> C++ (inc. Visual C++) -> VB (inc. VB.NET) -> C#
(Also HTML, various SQL dialects, Javascript, and JSP.)

For a serious student of programming, with a view to a future career in IT, I would suggest C.  It provides a solid basis for procedural and structured programming, and learning it can also give the student some knowledge lower-level workings of a computer system, which can be important in some disciplines.  C is only a small language, so the student doesn't need to be distracted by complicated external libraries or APIs.  After C, I'd suggest a move to C++ or Java, depending on career direction.  C++ for those who wish to focus their career on desktop application programming or system-level programming, and Java for those wishing for a career in e-commerce or enterprise development.

For a casual programmer who wants to take it up as a hobby, I'd suggest Python for Linux.  I've never used it, but it has a reputation for being readable, easy-to-learn, and has a strong user community.  It's not widely used in mainstream software development, but it is popular as a utility language by hobbyists and in the FOSS communities.  There are also no required knowledge (nor a need to learn) lower-level workings of a computer, so that makes programming pretty straight forward for a beginner.
But for Windows, I'd suggest VB.NET.  For a beginner to programming, VB.NET is a language that can be learned in a matter of a few hours, and the learner can create fancy programs with it, which can be motivating for a lot of beginners.  It is also a prolific language for mainstream IT, which might be a good thing if the learner has a mind to seek an IT career in the future.  The code for VB.NET is easy to read and understand, and the Visual Studio IDE is superb for organising projects and designing GUI.

---

### Post by Patrick-Ruff on 2006-12-25
I started with C, though, I kinda stopped after the initial concepts and basic syntax.  it's helping me learn other languages already. I'm moving on to Python now.

---

### Post by HokeyFry on 2006-12-25
i started with BASIC in school (True Basic to be exact). Even though BASIC isnt my first choice to use, it does teach basic programming logic and the keywords are easier for a beginner to remember than say, oh, C++ or Java. i dont know if there are any versions of BASIC for linux, though, but im sure there are.

or download a DOS boot floppy and use qbasic like i like to do sometimes :)

---

### Post by Patrick-Ruff on 2006-12-25
I always found BASIC to be really lacking in fetures, options, and efficiency.

---

### Post by gh0st on 2006-12-26
> **samjh said:**
> A very difficult question.  It all depends on the person who is wanting to learn.

Yeah this is very true. It's hard to say what language will suit people, its a very individual thing really. I voted for Python for beginners because it's quite friendly and easy to pick up but you can scale it to more difficult tasks as you progress.

---

### Post by lnostdal on 2006-12-26
I voted "other"; Lisp/Scheme

* [http://www.htdp.org/](http://www.htdp.org/) and [http://www.drscheme.org/](http://www.drscheme.org/)
* ..then move on to [http://www.gigamonkeys.com/book/](http://www.gigamonkeys.com/book/) and SBCL+Slime

hm .. but an understanding of low-level stuff is important too; so "The C Programming Language" and [http://download.savannah.gnu.org/releases/pgubook/](http://download.savannah.gnu.org/releases/pgubook/) ..   but do move on quickly to higher-level stuff once you understand how the low-level mechanics work

---

### Post by Wybiral on 2006-12-26
I vote python... Not only is it a breeze to learn, it's also very easy to apply to other languages. I notice it's really easy to take stuff from python and port it to another language (like C++).

It really depends what you want to do.
C would also be a nice language to learn for a lot of reasons.
I've learned all of these languages (and dabbled in some more), and would rate them in this order from Low-level to high-level. (Note that this doesn't have anything to do with favorites, just about abstraction from the machine).

Low-Level (closer to computer)
ASM
BASIC
C
C++
Python
High-level (more abstract, further from computer)

So you see... From C it's really easy to move in any direction (not that you can't just dive in to either side). I think it's important to learn ASM, python, and a couple of languages in the middle.

---

### Post by ifokkema on 2006-12-27
> **lnostdal said:**
> I voted "other"; Lisp/Scheme
Just out of curiosity? Why would you recommend those? Their syntax is absolutely nothing like any of the top-10 most popular programming languages and as far as I know these languages are designed to do things most starting programmers would never even care to solve... or am I missing something? :)

---

### Post by lnostdal on 2006-12-27
> **ifokkema said:**
> Just out of curiosity? Why would you recommend those?

Because they are the best languages out there for both beginners and advanced programmers of course.

> **ifokkema said:**
>  Their syntax is absolutely nothing like any of the top-10 most popular programming languages

Syntax is not content nor understanding. Lisp actually has no syntax. That's the whole point; code is trees/lists -- which are built in data-types like char or int is in C.

> **ifokkema said:**
>  and as far as I know these languages are designed to do things most starting programmers would never even care to solve... 

What things do you have in mind? Take a look at HTDP which I link to above.

> **ifokkema said:**
> or am I missing something? :)

It wouldn't come as a shock. People who do not grok Lisp usually have major holes in their understanding of programming in general -- regardless of language(!).

---

### Post by StarsAndBars14 on 2006-12-27
Uh. . .BASIC? 

(pun intended :P)

But really *cough* you can try either PHP or Perl.

---

### Post by rplantz on 2006-12-27
> **Ansible said:**
> I'd recommend an interpreted language like python or ruby.  NOT C++, a friend of mine took an intro to programming course that used C++, and I saw first hand the needless confusion and discouragement that produced.  C++ is a cool language and all, but it has a high percentage of BS-to-get-together to make it work.  Hello world is far more difficult with C++ than with an interpreted language like ruby.

The main point with a beginner's language is to get used to the concepts of flow of control, variables, and maybe objects.  A first language should be fun, and you should be able to get some results out of it quickly without messing around with a bunch of extra junk.  You shouldn't have to bother with tedious stuff like namespaces, makefiles, IDE projects, includes, etc, before you can get into the fun part, getting creative and getting some quick feedback from the code.

This is a common attitude I saw during my 21 years of teaching computer science (in the U.S). I don't understand it. I started as an electrical engineer. As LordHunter317 points out, I learned math and physics first. I don't recall ever building anything "fun" or "creative" during my undergraduate years. It was a lot of hard work. I was expected to learn the concepts so I could understand how to work on "fun, creative" projects.

Did it work for me? Yes. My first job out of college was designing part of the guidance system for the Gemini space capsule. Standard transformer design guidelines produced one that was way too big and heavy. I went back to fundamental concepts. By using very thin wire, it worked. And we even eliminated the usually required protection resistors in the power supply. But students today want instant results. It should be fun and flashy, and they should be rich immediately.

Enough of my "old man rant." I also had the opportunity during my teaching career to teach the second (or higher) language to quite a few students. (I've taught Pascal, C, C++, Java, and four different assembly languages.) I don't think it really matters what the first language is. I think it's more important to learn several languages, especially very different ones. Different people find different languages more natural for their thought processes.

I can assure you that learning how to program in a language that supposedly encourages good programming practices does not carry over to other languages. That carry over is done by the student, not by the language.

Finally, I assert that nobody can squeeze the most performance out of a computer without a good understanding of its architecture, starting with its instruction set. I further assert that performance is the only reason for using a computer.

---

### Post by ifokkema on 2007-01-02
> **lnostdal said:**
> Syntax is not content nor understanding. Lisp actually has no syntax. That's the whole point; code is trees/lists -- which are built in data-types like char or int is in C.
This would then be a different interpretation of "best language to start with" - I would recommend a language that is quick to learn, produces results fast (i.e. can easily do various relatively useful things), and allows you to more quickly "step up" to a more powerful, yet more difficult, language - thus has a similar syntax. Also, I'm thinking about self-taught programmers, not computer science students as they usually don't have a choice which language to learn first.

> **lnostdal said:**
> What things do you have in mind? Take a look at HTDP which I link to above.
With my interpretation of "beginning programmers" - I'm thinking about a small program that will tell you "good morning", "good afternoon", "good evening" or "good night" depending on system time. Or a quick-and-dirty program that would take a password and then prints "OK" on success or asks you again if you failed. And little web apps, like forms that send out emails. That sort of stuff. That at least interested me when I started looking around on the web for programming languages.

> **lnostdal said:**
> It wouldn't come as a shock. People who do not grok Lisp usually have major holes in their understanding of programming in general -- regardless of language(!).
Hmmm..... that could be taken as an insult ;)
I would say a different interpretation of the question - I answered this thead's question out of my viewpoint five years ago when I started programming. Only one and a half year ago I started taking actual classes about programming in University. There I got introduced with Scheme. Lisp and Scheme just don't help me solve the day-to-day programming issues I have to deal with, so I wouldn't recommend them to others...

---

### Post by pmasiar on 2007-01-02
> **lnostdal said:**
> Because they are the best languages out there for both beginners and advanced programmers of course.

Circular logic: I recommend X because X the best. Proof? I recommended it, therefore it *must* be true, otherwise I lied. I did not lied, so X is best. ](*,) 

> Syntax is not content nor understanding. Lisp actually has no syntax. That's the whole point; code is trees/lists -- which are built in data-types like char or int is in C.

Then [Whitespace ]("http://en.wikipedia.org/wiki/Whitespace_%28programming_language%29") may be even better language for you - even simpler than Lisp.

LOL, now seriously. Syntax is *good* if it hints what is the semantic. Syntax is *bad* when very different things looks very simmilar - it is easier to make a mistake and harder to see it, how *that* might be good for beginner? :confused:  Lisp syntax is too simple to guide especially the beginner what is going on. Finishing program with 7 closing ) is not very friendly either. :-) 

> It wouldn't come as a shock. People who do not grok Lisp usually have major holes in their understanding of programming in general -- regardless of language(!).

I looked at the lisp in college. I understand beuty (and lot of pain) of functional programming. But I am not perverse enough to inflict lisp as first language on impressible young mind of beginner :twisted:   

BTW did you know that lisp was not intended to be real programming language - just a theoretical concept to *think* about computations?

For me, implementing Forth was real eye opener - you can see what is happening on all layers, down to bare metal. that was really cool - and also simple enough to understand.

---

### Post by Mirrorball on 2007-01-02
> **rplantz said:**
> I further assert that performance is the only reason for using a computer.
The programmer's performance is important too.

---

### Post by manilodisan on 2007-01-02
I'll go for PHP all the way down.

---

### Post by phossal on 2007-01-02
[edited]

---

### Post by phossal on 2007-01-02
[edited]

---

### Post by pmasiar on 2007-01-02
> **phossal said:**
> By the way, I prefer KTurtle. :)

I was afraid to reply - I really don't enjoy when old experienced wise programmers like phossal calls me names. Oh well. Just my opinion. I think I still live in free country and I am entitled to express my opinion politely. I might be wrong... Whatever. 

I tried to hook my son on Turtle - did not worked. Tutle looks like a toy, and even kid can tell it is not a "real" language. And it is hard to motivate when you know kids are right.

I had better luck with introducing my son to programming via [Game Maker]("http://en.wikipedia.org/wiki/Game_maker") - a program with *very* easy GUI and *very* intuitive way to build programs. It does not feel like programming - more like building from lego blocks. Highly recommended for programming games (and games only), sadly Windows freeware only. Lots of fun too. 10 year old kid can (with some guidance) make playable game and share it with friends, pretty cool.

Where is my flame-resistant underwear - I disagreed with mighty phossal and  unleashed his wrath again :p

---

### Post by Wybiral on 2007-01-02
> Where is my flame-resistant underwear - I disagreed with mighty phossal and unleashed his wrath again 
LOL

I've messed with game maker too. Also RGD2 is pretty good... But, linux has cube, which isn't bad... But, it seems like linux is in need of an easy to use game designer. I'm pretty experienced with C++/python and OpenGL, if anyone else would like to pitch in, starting a linux game designer wouldn't be a bad idea. Something simple and easy for even kids to use. Anyway, respond/email/pm me if you're interested.

---

### Post by Wybiral on 2007-01-02
Perhaps the reason you and pmasiar keep running into each other is because you share interest in the same types of threads. I notice I run into the same people a lot too (pmasiar certainly being one of them) but it's nothing to get hostile about. Calling someone a moron over a simple debate isn't very friendly or productive. Quoting is pretty common on forums like these, so if you don't want quoted, perhaps it's best to just watch what you say.

Which language someone starts with is pure opinion, if you don't agree with python, say it... But expect someone out there is disagree (python is a very common learning language these days, and a lot of people will probably disagree). But please, civil debate is a good thing, it allows everyone to voice their opinion, but it should never escalate into calling people stupid.

---

### Post by phossal on 2007-01-02
[edited]

---

### Post by pmasiar on 2007-01-02
> **Wybiral said:**
>  linux is in need of an easy to use game designer.... Something simple and easy for even kids to use. 

For kids, exactly. On top of pygame?

I would be reluctant to go C++ route - performance is not critical (yet), it feels like a typical scripting task. GUI code editor is hard to do right, but IMHO good start cold be converting a XML/YAML text file into a simple game... And add GUI game editor later. If only I had more time... :-(

---

### Post by Wybiral on 2007-01-02
I think python isn't a bad idea. I'm kindof thinking of making this a 3d game editor, don't get disappointed, it will still be simple enough for kids. I can assemble a small collection of models and they will have a cubical grid to place the models where they want. Then there can be some kind of simple scripting language (I might even use python embedding for this) where they can use objects that exist in the game engine to create small logical situations...

The scripting could look like this...
```

if PlayInContact(Door1) and PlayerHasObject(Key1):
    Use(Key1)
    Activate(Door1)

```

And then they would just be able to move around prebuilt objects like doors, characters, scenery and build 3d scenes. They wouldn't have to use the scripts right away, only when they want to add dynamic actions to the game.

I'm juggling 1000 projects right now, but this ones sounds worthy to squeeze in, I think I'll start writing some base code for it very soon and see what I can come up with.

---

### Post by aysiu on 2007-01-03
It's possible to talk about programming without fighting and personal insults. Please give that a try.

I've moved some of the offending posts to the Jail.

---

### Post by Ansible on 2007-01-04
> **rplantz said:**
> This is a common attitude I saw during my 21 years of teaching computer science (in the U.S). I don't understand it. I started as an electrical engineer. As LordHunter317 points out, I learned math and physics first. I don't recall ever building anything "fun" or "creative" during my undergraduate years. It was a lot of hard work. I was expected to learn the concepts so I could understand how to work on "fun, creative" projects.


Interesting, rplantz.  Our attitudes reflect our experiences.  I approached programming with almost no formal instruction, at age 13 or so, programming in BASIC on apple IIs and then a trs-80 clone.  I learned programming because it was fun, and I could write video games.  Having had no interest in physics previously, suddenly I was consulting my physics books.  I approached programming as a game and not an academic discipline.  Of course, my program of learning didn't prepare me for many advanced topics, and without formal instruction I didn't get beyond a certain level.  But my experience was that programming was fun, and that initial perception carried me into a professional programming career.  I have to admit, though, that a lack of the basics has been a handicap for me at times.  I still tend to want to work on the 'interesting' stuff and let the rest slide; I'm more interested in AI than in kernel coding.  

Anyway, I think there's a lot of room out there for programmers who are not at the most elite level, for whom the most advanced algorithms are on the order of balancing a checkbook.  To me, its sad that a programming language is no longer bundled with windows.  I think everyone who uses a computer should be able to access some easy programming environment, to do batch type tasks like converting all their FLAC files to MP3, or sorting their emails, etc.  I just don't believe that people should have to go through the rigorous training of a professional NASA engineer before being allowed to program.  

That being said, some programming projects SHOULD be restricted to elite engineers.  Ultra reliable code in medical or aerospace systems, high performance code, OS kernels - these are not areas for the casual programmer.  But that shouldn't mean that we prevent casual programmers from doing ANY coding, there is a place for this kind of programmer.

---

### Post by randomnumber on 2007-01-05
I am a cs student that has taken too long to graduate and I have seen a change at our school on how to best prepare the students. When I started the degree (2000), our cs degree concentrated in C++ and was trying to move to Java. I took too long and ended up taking Java and C++ classes. The school is concentrating on Java now but has plans to move back to C++.

I am told that in the past the school did ..., C , C++, Java and that every time they switched they had significant increases in failure rates. I am told that our intro and intermediate class now have on average over 50% failure rates. 

I take the opinion the reason the failure rates are increasing is that the demands in the class are increasing. For example, when they used C++ they had no GUI but when the went to Java every program has to have a GUI. Every program Java has to have all exceptions taken care of. This sounds all great but it leads you away from the concepts at hand.

One of the most annoying things to hear is people talk about how much better C++ programmers are. The only reason for the C++ programmers being better programmers is that they concentrate on concepts. Java is actually a harder language to learn for a beginner. The languages are taut in entirely different ways. The Java classes begins with object oriented approach and tries to teach you how to use repositories and link programs together before you know how to add two numbers or run a loop. We actually have professors that think this approach is reasonable. 

People also make the comment that Java is a easier language to program in. This is and is not true. It keeps you from making mistakes that other languages are plagued with like memory leaks but it also only passes arguments by value. These limits are good and bad. 

As much as everyone is talking about python I am going to have to take a look at it eventually. I hope to learn more C and C++ in the future. 

I like the poll. Thanks

---

### Post by geek_Man on 2007-01-05
Wow, Tcl's a hit...

---

### Post by chris hyperstring on 2007-01-09
in my opinion c++ and java suck! i like lisp but it still feels like im climbing a mountain! 
cool
      chris

---

### Post by SubWolf on 2007-01-23
Aren't I late to the party. My learning path was BASIC -> Pascal -> PHP -> Java -> TCL -> Python.

I voted for PHP, because it's what my boss would call a 'very forgiving language'. It has plenty of leeway with such things as variable types & comparison, for example.

```
$a = "5"; // A string
$b = 10; // An integer
if ($a < $b) echo "It's less!";
```

Is this a good thing for the new programmer? There are arguments on both sides, while giving the new guy less to worry about, PHP's simplified nature can lead to some bad habits or strange problems, such as a float comparison I had to hack around a few months back.

**Python:** Gorgeous language, the syntax/whitespace standards could be annoying to newbs though.
**Java:** Well structured, can get very complex if you don't understand a bunch of core fundamentals.
**TCL:** Easy to write if you don't slip into PHP multi-line style, bloody single-line interpreters.

---

### Post by loconet on 2007-01-23
> **Tomosaur said:**
> I wish I'd started with shell scripting first. It'd work very well as a lightweight introduction to OO, but it's pretty neat as it is. ....

introducing to OO via shell scripting? Which shell are you referring to?

---

### Post by runningwithscissors on 2007-01-23
If you want to real Real Programming(TM) then C.

If you want to develop stupid little card games/accounting software/boring websites then you may bother with those modern flavour of the month languages that managers cream themselves over while thinking about "10000000000% increase in productivity!!!1111!!11!oneoneneeleventyone". Like Java or Ruby or ASP.NET/C# etc.

Yes, I work as a professional programmer. Yes, it takes almost the same time to develop an application in Java as it takes in C++. And the same time to develop one in modern PHP (version 5 and later) than one in ASP.NET/C#.

And no, your program _does not have to be_ object oriented for it to be reusable or maintainable.

---

### Post by neoflight on 2007-01-24
can php be used to write a wrapper for c++/fortran/c???
if yes, how does it compare with python in similar footing?

---

### Post by Dygear on 2007-01-24
Where I started :
Batch -> SmallC -> C -> C++ -> PHP.

I would have to say PHP, just do to the fact it teaches you to bear necessities like how to setup a programs structure, logic, and basic OOP. I would say once you've gotten used to that, you should go stright to a Strongly-typed programming language such as C, then move on to C++ to give you a good handle of OOP Porgramming.

Python has it's place, but I don't like the general look and fell of it, I would not recommend it to anyone off hand. Yeah, I know PHP teaches you some REALLY bad habits, but so does Python. It's up to the persion to really decide what they want to do. Application programming on Shell stuff. C, C++, and PHP are more towards the application side of things (Thanks in part to VC++, and GTK(+)). Where as Python would be more like Perl, or Batch.

Speaking of Batch, as any one seen MONAD? Microsoft's Power Shell looks to be freaking awesome, I'm running on my gaming box, and I'd really like to play with that some more.

---

### Post by chris hyperstring on 2007-02-13
(post deleted)

---

### Post by pmasiar on 2007-02-13
> **chris hyperstring said:**
> i have come to the conclusion that computers for work are genrally crap! 

Ultimate word of wisdom from a XHTML haxor expert :-)

---

### Post by thomasmallen on 2007-02-13
I would say javascript, actually. Tons of resouces online, completely free, no need to compile, no need for a server. Edit, save, refresh. I actually learned JS first and it was a very good starting point. It's also very useful immediately.

---

### Post by unipal on 2007-02-13
I voted other, I would recommend the D programming language. 

I have looked for an alternative programming language. I looked at C++, Java, Python and Ruby until I found D programming language. This is a really great!!! 

Some usefull text and links:

From de site of Digitalmars:
D is a systems programming language. Its focus is on combining the power and high performance of C and C++ with the programmer productivity of modern languages like Ruby and Python. Special attention is given to the needs of quality assurance, documentation, management, portability and reliability.

DMD compiler for Win32 and Linux...

The front end for D is open source, and the source comes with the compiler. The runtime library is completely open source. David Friedman has integrated the D frontend with GCC to create gdc, a completely open source implementation of D.

D vs Other Languages:
[http://www.digitalmars.com/d/comparison.html](http://www.digitalmars.com/d/comparison.html)

Complete overview of the D programming language:
[http://www.digitalmars.com/d/lex.html](http://www.digitalmars.com/d/lex.html)

Wiki:
[http://www.prowiki.org/wiki4d/wiki.cgi?FrontPage](http://www.prowiki.org/wiki4d/wiki.cgi?FrontPage)

Check it out!!

---

### Post by tesuki on 2007-02-22
I too would recmmend D before the other. just started with it gone from C/C++ to D.
D is so simpel and have thing from java. C# and well D is just a perfect beginner. and still usefull when you need to do advanced things fast. if I woulden't say D java or ruby is a good language to learn.

---

### Post by Klipt on 2007-02-22
> **themusicwave said:**
> As a side note, if you plan on obtaining a degree in Computer Science, Software Engineering(like me!) or Computer Engineering in the U.S., don't learn python.  In my 3 years of college thus far it has not even been mentioned.  All my assignments were mainly in C++ or Java.  We also learned Perl, C#, Scheme and Assembly.

I can't be sure since I went the other way, but I'd hazard a guess that it's fairly easy to learn other languages once you've grokked the concepts from python.

For ease of introduction I think Python is today what BASIC was a few decades ago - very easy starting language, and even more powerful. I just wish it had proper lexical scoping / closures. Even C# has those now! (Although a 'let' keyword or different assignment operator may be necessary for that...)

---

### Post by Tomosaur on 2007-02-22
Just had my first taste of D today, it's great :D

Here's my first D program, using assertions, C functions, and CLI args :)
```

import std.stdio;
import std.c.stdlib;


int main(char c[][]){
        assert(c.length > 1, "You must supply a radius.");
        assert(c.length < 3, "Too many arguments.");
        char * cp = & c[1][0];
        char ** cpend = & cp;
        double pi = 3.14159265;
        double r = strtod(cp, cpend);
        double a = pi * r * r;
        writefln("Area of this circle: %s", a);
        return 0;
}

```

---

### Post by pmasiar on 2007-02-22
> **themusicwave said:**
> As a side note, if you plan on obtaining a degree in Computer Science, Software Engineering(like me!) or Computer Engineering in the U.S., don't learn python.  In my 3 years of college thus far it has not even been mentioned.  

This is the biggest piece of BS I seen in a long time. :evil:

themusicwave's advice is from POV of 3 years in college, and opinions of Professors living in ivory tower, not concerned about solving problems, but creating publishable science. It is well known (and I experienced it first hand) that academia will often prefer more compicated solution, which yields something publishable over simpler solution.

So yes go ahaed and *dont* learn Python. It is not used in academia - it is used in real companies what need real solutions in real production, like Google, NASA, and Ubuntu's parent, Canonical. Python is also main development language for Ubuntu, and will be the only development environment installed in OLPC (for OLPC users).

Everybody who cares more about having results quickly does it in Python or Ruby (and of course C/C++ for time-critical parts). Don't look to professors for advice what tool to use to solve problems - they don't care too much about solving problems, they care about doing nice complicated science, and if it easy they are *not* interested. Look at what language successful hackers use. Hint: not java :-)

And even learning Python in Universities is about to change - MIT is switching from Schema to Python, see [http://www.amk.ca/diary/2006/11/mit_to_try_python_for_introduc.html](http://www.amk.ca/diary/2006/11/mit_to_try_python_for_introduc.html) . And our own university supercluster uses Python to glue together couple dozens of CPUs running C/C++ tools.

BTW having poll to decide which language is most popular is pointless excercise in pseudo-democracy. You need opinnions of experts, not random people. Like Bruce Eckel, who wrote the best-selling books Thinking in C++ and Thinking in Java (and is world leading expert in those languages), and read why he prefers Python: [http://www.artima.com/intv/aboutme.html](http://www.artima.com/intv/aboutme.html) and slides: [http://www.mindview.net/FAQ/FAQ-012](http://www.mindview.net/FAQ/FAQ-012) . 

Read up opinions of experts, then set your own priorities, and make your own mind.

---

### Post by Alasdair on 2007-02-22
[QUOTE="pmasiar"]And even learning Python in Universities is about to change - MIT is switching from Schema to Python, see [http://www.amk.ca/diary/2006/11/mit_..._introduc.html](http://www.amk.ca/diary/2006/11/mit_..._introduc.html) . And our own university supercluster uses Python to glue together couple dozens of CPUs running C/C++ tools.
[/QUOTE]

Do you actually think that replacing Scheme with Python in universities is a good thing? I'm not saying python isn't a useful language for solving real world problems (it's more useful than scheme in that regard), but I think that Scheme is a far better language with which to learn the fundamental principles of computer science with. For example by writing functions and macros such as defclass or defmethod in Scheme, the student not only gets to use object orientated methods in their programming, but also add object-orientation to a language (which doesn't support it by default) giving a far deeper insight into how it works. In scheme this stuff is easy, doing similar things to python would be far harder, if not impossible.

Check out this article on 'The Perils of JavaSchools'; you could go through it and replace all instances of Java with Python - the message would be the same.
[http://www.joelonsoftware.com/articles/ThePerilsofJavaSchools.html](http://www.joelonsoftware.com/articles/ThePerilsofJavaSchools.html)

Again, I'm not saying that python isn't worth learning. It's certainly more useful that Scheme in a real world setting, but simply learning the latest hyped technologies isn't what CS is really about imho.

---

### Post by Mirrorball on 2007-02-22
At schools professors won't be concerned about teaching different programming languages. If the students already know (C or Java) and Assembly, why waste their time teaching another language? The students can learn them easily by themselves. In the classroom they should be learning computer science, which goes much beyond programming languages.

But I bet that if you ask your professors if Python is worth learning, they will say yes. I wouldn't be surprised if they use the language themselves.

---

### Post by pmasiar on 2007-02-23
> **Alasdair said:**
> Do you actually think that replacing Scheme with Python in universities is a good thing? I'm not saying python isn't a useful language for solving real world problems (it's more useful than scheme in that regard), but I think that Scheme is a far better language with which to learn the fundamental principles of computer science with. (...)

Check out this article on 'The Perils of JavaSchools'; you could go through it and replace all instances of Java with Python - the message would be the same.
[http://www.joelonsoftware.com/articles/ThePerilsofJavaSchools.html](http://www.joelonsoftware.com/articles/ThePerilsofJavaSchools.html)

Again, I'm not saying that python isn't worth learning. It's certainly more useful that Scheme in a real world setting, but simply learning the latest hyped technologies isn't what CS is really about imho.

We almost agree. We agree that Java is not a silver bullet. We disagree what we consider the audience for "first programming language". You consider CS students. I consider every student - or at least every student of scientific discipline, not only Computer Science department.

1) Yes, I believe that Python is better first language than Scheme - even for CS students.
2) Good article - I am subscribed to Spolsky's mailing list, he is smart, good - but known Lisp lover :-)

I agree with Spolsky that dumbing down CS is wrong. But Lisp is certanly not the only language which may tax your understanding on computing. I am open for discussion, but IMHO much better candidate for such language is FORTH [http://en.wikipedia.org/wiki/Forth_%28programming_language%29](http://en.wikipedia.org/wiki/Forth_%28programming_language%29) Forth allows you to define functions in assembler as easy as define your own types, or even change command interpreter and define your own language. Forth is really *very* dangerous language - you have access to all internals of the compiler/interpreter, including return stack, and patching  body of functions is possible if you need it. Try it. Such basic concepts as "variable" and "constant" are easily defined in Forth (they are standard part of language, but strictly speaking, not necessary).

As special bonus, Forth runtime is really tiny (around 6K binary includes incremental compiler and interpreter and can run on bare metal), excellent for drivers and embedded systems.

I looked into the Lisp, even for a pet project was trying to implement it in Forth. It is at least possible - implementing Forth in Lisp would be harder :-)

But understanding of basic programming concepts is important for *all* students, way beyond CS - biology is becoming driven by CS, they even have "computational biology" now. But even if they have microscopes, they don'y have "microscope science" - programming is a *tool*, not the goal. And ability to design objects is overrated IMHO - it is not important in first year, and *using* objects will be just fine for most scientist. CS students can learn it in 2nd semester after understanding the basics. :-)

All professional programmers (includind CS students) should be ready to learn *many* new languages during their career and pick the best one for the job.  Starting with Python will let them get into basic programming faster, *after that* they can learn other languages, even Schema if desired. or ML, Forth, Java, C++, assembler. Important thing is to understand which part of the problem is inherent to area you want to model, and which part is caused by the language you decided to use to solve it. Because language forces your thinking about the problems  into "patterns", and if you are not aware of it, you are slave of patterns of your language. Every language was designed to be good for solving some kind of problems, and less than optimal for other problems. Denying it will not make it go away.

For *non-programmers*, IMNSHO Python is the best option as the first and if needed the only language. They have problems to solve, so better don't bother them with quirky syntax and "everything must be an object" as java does. Let me parse my data result files and get out of my way :-)

So I think we basically agree. Programming is hard and fun :-)

---

### Post by hod139 on 2007-02-23
Slighty off topic from the original question, but seems to fit with the recent posts.  Let me ask this question, "why are we teaching programming languages as the intro course to computer science in the first place"?  More succinctly, where does programming fit into introductory courses?

For example, instead of doing programming first (you can argue separately about imperative/functional/Objects first), why not teach algorithms.  I'm a fan of the algorithms first approach since it uses a pseudocode for the language and introduces students to concepts without any particulars of a specific language.  It requires more reasoning and students must explain their algorithms. Non CS majors taking the intro courses get a taste of some of the science in CS instead of just the programming.  And CS majors get exposed to the theory from the onset instead of considering the theory to be irrelevant after learning how to use a particular languages libraries.

---

### Post by lnostdal on 2007-02-23
i am also convinced scheme/lisp is much more suitable for people focusing on learning concepts than both java _and_ python .. and i believe they are making a mistake, possibly being influenced by external forces; while actually going backwards, or lowering the standards(!) by making this switch

take a look -- sicp is extremely good:
* [http://mitpress.mit.edu/sicp/full-text/book/book.html](http://mitpress.mit.edu/sicp/full-text/book/book.html) 
* [http://swiss.csail.mit.edu/classes/6.001/abelson-sussman-lectures/](http://swiss.csail.mit.edu/classes/6.001/abelson-sussman-lectures/)

---

### Post by lnostdal on 2007-02-23
[quote=hod139]ch since it uses a pseudocode for the language and introduces students to concepts without any particulars of a specific language.[/quote]
there is a leak here and this is it; what pseudocode should you use, and why should not that pseudocode run on a computer so you can actually see it happen, with actual output generated - then experiment with it?

..but still algorthims is already a separate course isn't it? the course at mit we're talking about has a lot of focus on design which is hard to describe using mathematics/algorithms .. it's a software-thing; "Structure and Interpretation of Computer Programs" it just has to be about code, the understanding and design of it :)   (see the TOC in the book i link to above)

edit: well, i see you're asking a different kind of question than i thought ...  i don't know what is smartest to learn first; software-design or algorithms - but maybe the "leak" as i see it implies that i prefer being able to run pseudocode when experimenting with implementation and understanding of algorithms in software

---

### Post by cantormath on 2007-02-23
C and C++..
Learn it the right way the first time.

---

### Post by hod139 on 2007-02-23
> **lnostdal said:**
> 
edit: well, i see you're asking a different kind of question than i thought ...  i don't know what is smartest to learn first; software-design or algorithms - but maybe the "leak" as i see it implies that i prefer being able to run pseudocode when experimenting with implementation and understanding of algorithms in software
You're not alone in this desire to implement algorithms, and this is one of the reasons why I think most computer science programs still focus on languages first.  It is a way to keep students interested since they get to "build" stuff and see results. 

The 2 big drawback to programming first are 1) it pushes the science to secondary status, and by the time computer science students finally face it they are unprepared[1] and don't want to be bothered by it and 2) non computer science majors taking the introductory course only see computer science as computer programming, they never see the science aspects of the field.

[1] There is a high major drop rate for data structures and analysis which is a 2nd year course

---

### Post by pmasiar on 2007-02-23
> **hod139 said:**
> instead of doing programming first (you can argue separately about imperative/functional/Objects first), why not teach algorithms.  I'm a fan of the algorithms first approach since it uses a pseudocode for the language and introduces students to concepts 

Python *is* the executable pseudocode  (/me ducks)

---

### Post by hod139 on 2007-02-23
Ha, got a good laugh from reading that!!

---

### Post by Mirrorball on 2007-02-23
You can teach algorithms with a real language just as well as with pseudo code, with the advantage that you can execute them too. You can time a real implementation of insertion sort and compare it with a real implementation of quick sort. It's much more instructive.

---

### Post by hod139 on 2007-02-23
> **Mirrorball said:**
> You can teach algorithms with a real language just as well as with pseudo code, with the advantage that you can execute them too. You can time a real implementation of insertion sort and compare it with a real implementation of quick sort. It's much more instructive.
I don't completely agree with this. With pseudocode you can use whatever expressive method is most clear and concise to specify a given algorithm.  Sometimes this is English.  Also, pseudocode is not concerned with  software engineering: data abstraction, modularity, error handling are ignored to convey the meaning of the algorithm.  This is why some of the best algorithm books do not use a language.

For example, here is pseudocode for insertion sort
```

INSERTION-SORT(A)
for j <-- 2 to length[A]
  do key <-- A[j] 
    //Insert A[j] into the sorted sequence A[1 .. j-1]
    i <-- j-1
    while i > 0 and A[i] > key
      do A[i + 1] <-- A[i]
        i <-- i - 1
    A[i + 1] <-- key

```  The above code was taken from the [CLRS Algorithms book]("http://theory.lcs.mit.edu/%7Eclr/").

What I do agree with is that with a real language the students can implement, run, and analyze "real" performance. This is why I think most schools use a real language, so the students can build/test a real thing.  But, in computer science, what is more important: being able to time insertion sort on a computer or evaluate loop invariants, correctness, and  expected running time of it?

---

### Post by Mirrorball on 2007-02-23
> **hod139 said:**
> I don't completely agree with this. With pseudocode you can use whatever expressive method is most clear and concise to specify a given algorithm.
Teachers can also explain an algorithm through pseudocode, if it makes their work easier. But languages like Java and Python have a clear syntax already, and Python is concise.
> **hod139 said:**
> Also, pseudocode is not concerned with  software engineering: data abstraction, modularity, error handling are ignored to convey the meaning of the algorithm.
You can write a Python or a C program with no error handling, no modularity, no data abstraction.
> **hod139 said:**
> This is why some of the best algorithm books do not use a language.
And/or maybe the authors don't want their books to be tied to a particular language that no one will use in the future, or they don't want to be criticized for the language they chose. ;)
> **hod139 said:**
> But, in computer science, what is more important: being able to time insertion sort on a computer or evaluate loop invariants, correctness, and  expected running time of it?
The latter, but you can have both. Students will be impressed when they see that their insertion sort function takes 2 minutes to sort a list and their quick sort function does it in 2 seconds.

---

### Post by Patrick-Ruff on 2007-02-25
you need to put ruby on this poll.

---

### Post by geakMonkey on 2007-02-26
BASH is the most suitable because unless you are root, you cannot do too much damage.:lolflag:

---

