---
title: "Java Tutorial"
date: 2007-02-26
forum: Programming Talk
---

### Post by Darkness3477 on 2007-02-26
OK, I looked in the various stickied threads, and also made use of the search feature of this website, but I couldn't find any Tutorials that catered to my specific needs. Perhaps I need something different from everyone else, or perhaps I was searching for the wrong thing, oh well.

Anyway, I'm starting to learn Java and have been using the tutorials off of the sun.java.com website (Or is it Java.sun.com? I also get it wrong). However, I'm trying to look for a tutorial or a book that just jumps straight into some _BASIC_ programming without explaining all the junk about OOP and various other things. I just feel I learn things like that better if I have actually done a bit of programming. I've looked around on google and I can't really find anything very useful. So, maybe one of you guys could help out. If so, thanks.

Thankyou for any and all help that you can offer,

     Maver

---

### Post by lnostdal on 2007-02-26
uhm, well - have you tried "hello world": [http://java.sun.com/docs/books/tutorial/getStarted/cupojava/unix.html](http://java.sun.com/docs/books/tutorial/getStarted/cupojava/unix.html) ..?

---

### Post by Darkness3477 on 2007-02-26
Yes, yes. I've tried out that. I understand it and can do slightly more complicated things than that. I've ready quite a large portion of what is on the Java.sun.com pages and understood a good majority of it. 

I'm just looking for some nice, simple, tutorials that'll teach me the basic syntax of the language and some other stuff without going into the intricancies of OOP, and other advanced Java subjects. 

I'm not a total noob at programming, I've had experience with some pretty basic Python, C++ and vb.net (For school)... So yeah. I just need help finding a good tutorial to look at before I start using some books I downloaded (Thinking in Java), I'd use it now but they seem to be aimed at people with a little bit of programming experience. And mine is limited to declaring variables and spitting them onto a console; well in java at least.

---

### Post by Tomosaur on 2007-02-27
Be sure to have a copy of the Java API to hand, or at least a web-page with it open. Then, visit this page:

[Clicky](http://www.csc.liv.ac.uk/~frans/COMP101/comp101.html#problems). That's my old professor's web page. It's very good for the Java basics, and it actually makes you work, rather then telling you how to do a million variations on Hello World.

---

### Post by Darkness3477 on 2007-02-27
Hey, thanks. That looks like it'll be pretty darn helpful. This should get me closer to my goal. Which is to be able to make a very simple game (dunno if it'll be an applet or a standalone) and also to be able to program a robot. Which i need to buy... :P 

Anyway, thanks again.

---

### Post by Tomosaur on 2007-02-27
No problem, good luck with your game (and your robot :O).

---

### Post by pmasiar on 2007-02-27
> **Darkness3477 said:**
> OK, I looked in the various stickied threads, and also made use of the search feature of this website, but I couldn't find any Tutorials that catered to my specific needs. Perhaps I need something different from everyone else, or perhaps I was searching for the wrong thing, oh well.

Anyway, I'm starting to learn Java and have been using the tutorials off of the sun.java.com website (Or is it Java.sun.com? I also get it wrong). However, I'm trying to look for a tutorial or a book that just jumps straight into some _BASIC_ programming without explaining all the junk about OOP and various other things. I just feel I learn things like that better if I have actually done a bit of programming. I've looked around on google and I can't really find anything very useful. 

You are absolutely right, it is hard to learn java without OOP -- because java is not object-oriented - it is object-obsessed :-)

IMNSHO you are much better off starting with simpler (and sneakily more powerful) language like Python. You can do lots of useful stuff without defining objects (possibly just using library objects), and switch to objects when you are ready and it makes sense.

Also, with dynamic typing of Python you are less focused on typecasting and more on that you need to solve.

Try [learn python wiki]("http://learnpydia.pbwiki.com/HowToStart") - you will find online books, and also intro to data structures and simple tasks to solve.

By opinion of many, Python is excellent first language. After you understand basics (loops, procedure calls, lists etc) you can quickly learn another language where the same concepts are used (but just language syntax is different - usually more verbose).

Compiled statically typed languages like Java, C/C++ are optimized for computer performance. They make programmer to work extra hard to gain speed in execution.

Dynamically typed languages Like Python, Ruby, Perl are optimized for programmers productivity, and they make computer work extra hard at runtime to figure many things whic they do not bother programmer. They might be not as fast when running program, but they allow the programmer to write program much faster, and require less detail.

BTW Ubuntu includes Guido van Robot - learn programming using logo-like robot.

---

### Post by Tomosaur on 2007-02-27
Pmasiar, no offence, but can you please just give your Python evangelism a rest? The guy wants to learn Java - you're just going to confuse him and/or irritate him. Let him decide if he wants to continue with Java or not, then he can come back and ask about different languages.

---

### Post by pmasiar on 2007-02-27
> **Tomosaur said:**
> Pmasiar, no offence, but can you please just give your Python evangelism a rest? The guy wants to learn Java - you're just going to confuse him and/or irritate him. Let him decide if he wants to continue with Java or not, then he can come back and ask about different languages.

no.

When answering questions sometimes in IMHO usefull to question unstated assumptions - if they are wrong, our answer might mislead in wrong direction.

Sun spent millions to hype up java. Lots of  [PHB's](http://en.wikipedia.org/wiki/Pointy_Haired_Boss) are still under spell of "java is the only language you will ever need" which is still regarded as true in management (my boss succumbed to it recently). I know I will not overturn the wave by myself, but I will die trying :-)  OK I will not die, i am learning java/Struts now, but to keep my sanity I promote Python to save innocent souls from the flames of hell :-)

Original poster mentioned he has problems with OO obsession of java - and my advice was to learn non-OO language first, and then continue with java. He never explained he need java and java only. If Java is the only language he plans to learn, he is under spall - and if not, he may as well pick with some language more friendly to beginners, like Python.

Python is c-like enough than he will have no problem transferring most of the Python knowledge to java, and no objects upfront like java.

maybe we need to wait for opinion of the original poster if java is the only true language, or if he is open to other opinions - but we will never know if we never ask, no?

IMHO, YMMV.

---

### Post by Tomosaur on 2007-02-27
> **pmasiar said:**
> no.

When answering questions sometimes in IMHO usefull to question unstated assumptions - if they are wrong, our answer might mislead in wrong direction.

Sun spent millions to hype up java. Lots of  [PHB's](http://en.wikipedia.org/wiki/Pointy_Haired_Boss) are still under spell of "java is the only language you will ever need" which is still regarded as true in management (my boss succumbed to it recently). I know I will not overturn the wave by myself, but I will die trying :-)  OK I will not die, i am learning java/Struts now, but to keep my sanity I promote Python to save innocent souls from the flames of hell :-)

Original poster mentioned he has problems with OO obsession of java - and my advice was to learn non-OO language first, and then continue with java. He never explained he need java and java only. If Java is the only language he plans to learn, he is under spall - and if not, he may as well pick with some language more friendly to beginners, like Python.

Python is c-like enough than he will have no problem transferring most of the Python knowledge to java, and no objects upfront like java.

maybe we need to wait for opinion of the original poster if java is the only true language, or if he is open to other opinions - but we will never know if we never ask, no?

IMHO, YMMV.

No he didn't, he said he couldn't be bothered reading about the theory behind Java, because he learns better using practical exercises. It's called kinesthetic learning, and it has nothing at all to do with programming language preference. He didn't mention any particular reason why he wanted to learn Java, just that that's what he was doing. As a matter of fact, he'd even stated that he has some experience with Python - so obviously he's already tried it and now he wants to start learning Java. There's nothing wrong with that, so you'd do better to actually read further than the first post before you go splurging all over python, when a python testimonial wasn't requested or even mentioned. I don't like reading about the intricacies of Java's OO, but that doesn't mean I don't like, or appreciate, Java. I just happen to have more interest, and learn quicker, by doing something rather than reading about it.

---

### Post by Darkness3477 on 2007-02-28
Yes, like Tomosaur said; I've had some experience with Python. Whilst I enjoyed the language quite a bit I now feel that I want to move on from that (And Vb.net) and get going with a language more suited (and used) in the business world. Also the fact that my programming course will be teaching java in the near future (We're using vb.net to teach the beginning stuff then moving onto Java) so i would like to get a head start with Java to continue the flow of me being the best/most experience programmer in the class except for the teacher.

Also, I have to say that people talking about Python being the miracle language and it being all that is kinda odd. I liked the language but never thought that it was that brilliant. 

I'm still looking for a nice simple tutorial. I like the one on vb.net found [here]("http://www.homeandlearn.co.uk/NET/vbNet.html"). It went through all the basic stuff with clear, precise example code. If I could find a tutorial like that, it'd be great. 'Cause as soon as I've gone through the basics of actually programming, I'll most likely be more comfortable with learning the more technical intrincacies(sp?) of the language.

EDIT: pmasiar, you say that Sun spent Millions on creating the java 'hype' yet everyone here seems to be creating a Python hype. Also, my need for java also comes from my personal programming goal. I want to be able to create a nice simple game by the end of this year (Or sooner, hopefully). Now, whilst java might not be the best language to create games (Or perhaps it is, i've no idea) I would really like to produce this game as an applet so my friends can play it online. It'd be a great addition to my website I'm developing. 

Reading further into your post(s), I can assure you that I am under no 'spell'. I never have been, nor will I be, under the influence that any language (or particular things) is the complete Bee's knees. As stated above. I chose java because it's going to be coming up in my Software Development & Design course, it will help me make a game that is suitable for the internet, it's quite a powerful language and most importantly, it's easthetically appealing. Also, on a resume, saying I'm productive in Java (Which is a fairly well known language outside of the computer world) looks better than Python. Whilst I won't be going for a programming job, stuff like that impresses general business owners. :p

---

### Post by phossal on 2007-02-28
> **Darkness3477 said:**
> Also, on a resume, saying I'm productive in Java (Which is a fairly well known language outside of the computer world) looks better than Python. Whilst I won't be going for a programming job, stuff like that impresses general business owners. :p
lol None of that is true, is it? Define general. Define business owners. Define *stuff.* ;) Just Kidding.

If you're finding yourself short on tutorials, and you feel comfortable with some basic building blocks (core language features), I suggest jumping right in to a personal project you think up. Start programming your robot *now*. You'll use at least some of the skills you've already learned right away, and you'll be forced to look for *specific* information when you find yourself struggling with the aspects of your project that are more difficult, or are beyond your current skill level. I've found it's difficult to aquire more than a surface level understanding of a language's features until I *need* them. Using different data structures, creating models for various swing objects, serializing objects, learning new API's like JavaMail, were all tasks that I had read a lot about, but improved my knowledge of by working with them. I was able to work with them in the beginning by defining a project for myself, like connecting to a database and creating a GUI to interact with it, and then learning what I needed to know to make it work.

---

### Post by pmasiar on 2007-02-28
> **phossal said:**
> If you're finding yourself short on tutorials, and you feel comfortable with some basic building blocks (core language features), I suggest jumping right in to a personal project you think up. Start programming your robot *now*. You'll use at least some of the skills you've already learned right away, and you'll be forced to look for *specific* information

I agree 100% - trying to implement something will motivate you to learn parts of API which are relevant to what you need - which is very different from learning abstract language concepts which you cannot relate to.

It is like learning new (human) language: you can read lessons etc, but you really start learning it when you try to *use it* to express yourself. Your solutions will not be perfect - but next time when you will read about some construct, you will see how it is relevant to something you struggled to solve.

"Dive-in" method of learning programming language has also downside: your solutions might work for your problems, but might be sub-optimal and you may learn bad habits which you will need broke later. Try to avoid [Cargo cult programming](http://en.wikipedia.org/wiki/Cargo_cult_programming) and [Voodoo programming](http://en.wikipedia.org/wiki/Voodoo_programming) - try to understand what code does and why, not just copy-paste it from how-to page. 

Later, when you will know more about proper Java usage, be prepared to redo parts of your code the right way, according to best practices.

---

### Post by pmasiar on 2007-02-28
> **Darkness3477 said:**
> I've had some experience with Python. Whilst I enjoyed the language quite a bit I now feel that I want to move on from that (And Vb.net) and get going with a language more suited (and used) in the business world. Also the fact that my programming course will be teaching java in the near future
(...)
Also, my need for java also comes from my personal programming goal. I want to be able to create a nice simple game by the end of this year (...) as an applet so my friends can play it online. 

OK no problem, java (and not Python) is obvious choice for you in this case - it was not mentioned in original post.

Another option for the game might be flash, just FYI.

> Also, I have to say that people talking about Python being the miracle language and it being all that is kinda odd. I liked the language but never thought that it was that brilliant.

I am perfectly OK if you prefer Java over Python for reasons you mentioned above, or other reasons, or for no reason at all... Up to you, good luck.

But: Please take no offense, but from what I know about your level of experience, IMHO you are *not* experienced enough to appreciate how simple and elegant Python is. Often when you learn some (more powerfull) language as second languge, for some time you do not use the more powerfull features, and you do not even miss them - because you think in your first language and have no use of those features, you learned workarounds.

Example: I was trying to define multi-line string literal in Java. Java doesn't have one, workaround is to build that string from many 1-line strings and +. Which is OK until your literal is 60 lines long. I can store string in a text file, but even slurping text file into a string is 3 lines of code - instead of 1 line in Python (which also has multi-line string literals). Java coder will never miss it.

I am not saying that Python is miracle language - but it is pretty simple and elegant. 

> pmasiar, you say that Sun spent Millions on creating the java 'hype' yet everyone here seems to be creating a Python hype. 
(...)
Also, on a resume, saying I'm productive in Java (Which is a fairly well known language outside of the computer world) looks better than Python.

... and this is exactly the proof of how Sun's hype was successfull. Why should business owner bother which tools craftsmen used to build a shed? Use best tool for the job, no? 

Interesting read about how languages evolve and possible future languages might be [The hundred year language](http://www.paulgraham.com/hundred.html)

And far from everyone hypes Python. First, we are not paid shills to hype python - we who praise it do praise it because *we* believe it is simple and elegant, for no financial reasons. Second, it is mostly me :-) - and it is my personal way to relieve  frustration while I have to switch my very simple Python-based web app to Java/Struts monster :-(

And again, I have no problen with you using java - it looks like best match to your needs. Just remember what you said about "the miracle language" :-)

---

### Post by Darkness3477 on 2007-03-01
Yeah, I can understand some of what you're saying, Pmasiar about Java having a lot of hype about it. But that's just fine with me. For what I want, I believe it to be the best choice for me regardless of it having features I won't need for a long time. 

I like learning things, I just wish I could find a tutorial that would go through the language basics (Loops I figured out easily, and other things) so I could put together my own application. I have a basic idea of what I want to do. In vb.net, I made a very simple encryption/decryption program that takes a string from the program or from a .txt file gives me the ascii value, then converts it into binary. Pretty simple, and anyone looking at it could tell it's binary and then change it, but it brang together all of the simple vb.net I had learnt and put it into a real world application... Well, kinda.

So, basically I'm just looking for a tutorial that goes throuf strugggh all the basic things (User input, output, simple mathematical operations and what not. Only difference is I probably won't be having using a nice pretty gui. Just seems like it would add a little too much complexity for my itty bitty brain to deal with. 

I think what I'll do is just find my vb.net source code, look at what I needed to know for that, then look up how to do it in Java. Seems like that'll be the easiest thing to do. Then I'll get started on doing some basic GUI stuff, like making a webbrowser.

---

### Post by pmasiar on 2007-03-01
> **Darkness3477 said:**
> I'm just looking for a tutorial that goes throuf strugggh all the basic things (User input, output, simple mathematical operations and what not. Only difference is I probably won't be having using a nice pretty gui.

The best Java intro book I found is Headfirst Java - it is fun to read, less boring than most programming books. Whole headfirst series is excellent. But I am afraid some mental heavy lifting to learn basic OOP ways is required: there is no way around learning Java objects  - as they say jokingly, Java is "object obsessed" and every action (verb) has to be chaperoned by a class. There is hillarious rant about it: [Execution in the Kingdom of Nouns](http://steve-yegge.blogspot.com/2006/03/execution-in-kingdom-of-nouns.html) - and you can tell the guy knows Java inside-out, just read the poem :-)

Another excellent book explaining *why* Java is as it is (explaining design decisions, to understand how to correctly use it): Bruce Eckel's Thinking in Java - you can tell that book is excellent if it is in 4th edition now. 3rd edition is online, free. Bruce makes living by teaching Java around the world.

O'Reilly has online Java course to teach you applet programming: [http://oreillylearning.com/courses/java/](http://oreillylearning.com/courses/java/) - you can try it for 7 days for free. It is rather easy - I finished it all in like 3-4 days (and got my money back) but I am no beginner :-)

One of the reasons for lack of good free tutorials for Java IMHO might be that Java is less "fun to use" than dynamically typed languages, and is mostly used by serious people for serious projects - who are used to get paid for the time, and get paid well. It is like user community of MySQL vs Oracle - Oracle guys are rich and less inclined to share tricks. IMHO, YMMV.

It does not mean there is lack of tutorials for java - your friend Google will find you plenty of them for any aspect and tool you will ask for. Keep in mind that Java is 12 years old now, many tutorials are for old versions of Java using old tricks. Thats why buying couple of books for java 1.5 might be good investment - you do not waste time learning old tricks.

Get used to pay for Java knowledge - java is used in money-making community :-)

---

### Post by yaaarrrgg on 2007-03-01
I thought this was useful (takes a cookbook approach):

[http://www.exampledepot.com/](http://www.exampledepot.com/)

Also, I thought the book "Learning Java" from O'reilly was good (don't forget many of these books are free at your public library ;) )

---

### Post by Darkness3477 on 2007-03-02
Pmasiar, I'll probably just go to the library. Where I live we have a pretty big library with reletively new books. Not sure about the tech section, but hopefully they'll have a nice Java book. 

I understand the basics of OOP programming, and how to actually program (reletively well, anyway) so hopefully I'll be able to find a lovely book somewhere. 

Yaaarrrgg: I'll go have a looky at that site in a little while. I'm just getting over my absolutely huge and wonderful dinner. I make the best Pizzas. Thanks for the help!

---

