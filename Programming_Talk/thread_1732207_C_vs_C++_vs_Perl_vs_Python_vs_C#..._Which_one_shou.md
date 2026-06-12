---
title: "C vs C++ vs Perl vs Python vs C#... Which one should i chose?????"
date: 2011-04-17
forum: Programming Talk
---

### Post by bloodhacker2 on 2011-04-17
Ok guys this is the deal. 

I have been web coding for a while with PHP, Javascript, html, but now i would like to move into more os based coding. 

My goal is to keep everything linux based and also have a option to build on windows, but i don't exactly know which code to choose. which one is more flexible and faster, more secure and easier to understand.. 

see, when getting into web coding choosing PHP over ASP.NET was a no brainier. 

But now theirs so many to chose from and every time i search i get different opinions on each code.

So now what im looking for is real life experiences and opinions on theses types of coding. 

So what do you guys think?? 

C vs C++ vs Perl vs Python vs C#

---

### Post by unknownPoster on 2011-04-18
My advice will be the same as many other people's advice.

Read the stickies.

---

### Post by robro on 2011-04-18
I believe that Python and Perl is better for cross-platform as you don't have to recompile them,
C++ has a steap learning curve compared to Python and Perl, and as far as I know you have to have windows to compile it for windows,
as for C# I believe it is more windows based and is a bit hard to run with linux.

---

### Post by PaulM1985 on 2011-04-18
You don't *need* to have Windows to compile C++ for Windows.  This is called cross compiling.  However, I am lead to believe that this is quite difficult.

C# can be run on Linux and Windows.  Look into the Mono project for more information on C# programming on Linux.

Paul

---

### Post by bloodhacker2 on 2011-04-18
Ya and i was thinking the same thing with c, c++ and C#.
Now with Perl and Python which one would be better in a sense.

Like if i where to choose between asp.net and php i would chose php because it is more flexible and supported more that asp.net.

---

### Post by Sam White on 2011-04-18
Personally, I have only tried C# out of the languages you have listed, but I have heard that all the C languages are incredibly similar.

C# has very few keywords, which makes it easy to learn, and it also has great flexibility. Plus, the mono environment and support is great.

Sam

---

### Post by directhex on 2011-04-18
> **robro said:**
> I believe that Python and Perl is better for cross-platform as you don't have to recompile them,
C++ has a steap learning curve compared to Python and Perl, and as far as I know you have to have windows to compile it for windows,
as for C# I believe it is more windows based and is a bit hard to run with linux.

There have been C# apps out of the box in Ubuntu for over 5 years.

---

### Post by llanitedave on 2011-04-18
If you need to squeeze high performance out of your code, go with C or C++.  If you're looking for maintainability and rapid development, go for Python.

---

### Post by bloodhacker2 on 2011-04-18
lol i just did this test [http://www.awaretek.com/atesterea.html#](http://www.awaretek.com/atesterea.html#)

and they said that python is the code for me.

---

### Post by cgroza on 2011-04-18
It is just the right tool for the right job, I would learn all of them.

---

### Post by bloodhacker2 on 2011-04-18
Ya im staring to learn that as im doing my research. But it looks like C is very widely used.

---

### Post by andrew1992 on 2011-04-18
> **bloodhacker2 said:**
> Ya im staring to learn that as im doing my research. But it looks like C is very widely used.

Indeed, but it's also more frustrating and harder to learn. But if you'd like a challenge, go for it! If you're smart enough and willing enough, you can learn any language.

---

### Post by directhex on 2011-04-18
If you write a GUI app in C in 2011, you deserve a slap. Non-performance-critical code should not use a language which invites buffer overflow vulnerabilities and requires manual memory management.

---

### Post by andrew1992 on 2011-04-18
> **directhex said:**
> If you write a GUI app in C in 2011, you deserve a slap. Non-performance-critical code should not use a language which invites buffer overflow vulnerabilities and requires manual memory management.

How bout just for kicks? ;) I know what you mean though, and completely agree with you. But I did write a gtk app in C just for kicks. I thought it was worth-wile.

---

### Post by kurum! on 2011-04-18
> **bloodhacker2 said:**
> Ya and i was thinking the same thing with c, c++ and C#.
Now with Perl and Python which one would be better in a sense.

Like if i where to choose between asp.net and php i would chose php because it is more flexible and supported more that asp.net.

Python + Perl = [Ruby. ]("http://ruby-doc.org/docs/ProgrammingRuby/")

C/C++ has limited practical use in the 21st century, except if you want to do low level stuff. We are living in the internet age, remember? 
C is widely used, yeah sure, in the past. 

C# works only in Windows. true, you can use mono for use in Linux, but you still need to install mono, not true cross platform.

Final answer: [Ruby. ]("http://ruby-doc.org/docs/ProgrammingRuby/")

---

### Post by unknownPoster on 2011-04-18
> **kurum! said:**
> Python + Perl = [Ruby. ]("http://ruby-doc.org/docs/ProgrammingRuby/")

C/C++ has limited practical use in the 21st century, except if you want to do low level stuff. We are living in the internet age, remember? 
C is widely used, yeah sure, in the past. 

C# works only in Windows. true, you can use mono for use in Linux, but you still need to install mono, not true cross platform.

Final answer: [Ruby. ]("http://ruby-doc.org/docs/ProgrammingRuby/")

There is a ton of misinformation in this post. I'd ignore most of it.

C++ is the industry standard for games, so that renders your first point invalid.

And I guess your second point proves that neither Java and Python are not "true" cross platform.

Please get your facts straight before spreading FUD.

---

### Post by directhex on 2011-04-19
> **kurum! said:**
> C# works only in Windows. true, you can use mono for use in Linux, but you still need to install mono, not true cross platform.

Ruby does not work in Linux. Unless you install Ruby. Therefore Ruby is not true cross platform.
:???:

---

### Post by Vaphell on 2011-04-19
difference is that ruby, python and java are pretty much the same thing on both platforms and mono is like OpenOffice vs the one and only MSOffice. It lacks some features, plays catch-up game and is not 100% compatible.

---

### Post by directhex on 2011-04-19
> **Vaphell said:**
> difference is that ruby, python and java are pretty much the same thing on both platforms and mono is like OpenOffice vs the one and only MSOffice. It lacks some features, plays catch-up game and is not 100% compatible.

The only people who obsess about Mono not being Microsoft.NET are people with no interest in using either. Plenty of great Free Software apps are written first and foremost for Mono - if someone later spends time worrying about Microsoft.NET support, that's great, but it's also utterly irrelevant.

Again, Mono has been part of Ubuntu since Breezy (5.10) - at no point has anyone broken down crying saying "oh me oh my, if only we had Microsoft.NET, then Tomboy would be so very much better"

---

### Post by kurum! on 2011-04-19
> **directhex said:**
> Ruby does not work in Linux. Unless you install Ruby. Therefore Ruby is not true cross platform.
:???:
what rubbish are you talking about. Ruby works on Linux. What i mean by cross platform is code written in linux can run on Windows version of Ruby.

---

### Post by kurum! on 2011-04-19
> **unknownPoster said:**
> There is a ton of misinformation in this post. I'd ignore most of it.

that is your problem.

> 
C++ is the industry standard for games, so that renders your first point invalid.
I said limited. So its good for games and some low level stuff, what else in terms of practicality?  

> 
And I guess your second point proves that neither Java and Python are not "true" cross platform.
By cross platform, I mean code written in one platform can run on another using the interpreter. That is, there is a python binary as well as python.exe executable, in that sense.

> 
Please get your facts straight before spreading FUD.Same to you.

---

### Post by Jonas thomas on 2011-04-19
> **bloodhacker2 said:**
> Ya and i was thinking the same thing with c, c++ and C#.
Now with Perl and Python which one would be better in a sense.

Like if i where to choose between asp.net and php i would chose php because it is more flexible and supported more that asp.net.

Someone made a comment that C++ has a steep learning curve. +1 on that comment.
I haven't done Perl/Python... but my brother and law has.  He made the comment to me that Perl has many paths to solving a problem but Python is generally has one. 
OTH, he said that the Perl code repositories are centralized but Python is all over the place. (For me, I think learning Python is next on todo list.) The b-in-law likes Perl.

---

### Post by PaulM1985 on 2011-04-19
C++ also used for media players (look at xine and gstreamer), oh and computer aided design packages, and graphics packages.

Wow, there seems to be loads of C++ stuff out there.  Some would consider the possibilities limitless.

---

### Post by slavik on 2011-04-19
> **Jonas thomas said:**
> Someone made a comment that C++ has a steep learning curve. +1 on that comment.
I haven't done Perl/Python... but my brother and law has.  He made the comment to me that Perl has many paths to solving a problem but Python is generally has one. 
OTH, he said that the Perl code repositories are centralized but Python is all over the place. (For me, I think learning Python is next on todo list.) The b-in-law likes Perl.
Your brother in law is right.

---

### Post by Jonas thomas on 2011-04-19
> **slavik said:**
> Your brother in law is right.

It must be a genetic characteristic because my wife is always right also..:)

---

### Post by kurum! on 2011-04-19
> **PaulM1985 said:**
> C++ also used for media players (look at xine and gstreamer), 

there are players like that purely done in Python/Java etc...not just with C++

---

### Post by nvteighen on 2011-04-19
As much as I deeply hate C++, it'd just reveal huge ignorance if I stated that C++ has no uses. In fact, my main complain against it is that it was designed with almost every possible use in mind! But this is not a thread about C++ so I won't get into that; if interested on my views about this topic, look up for some posts of mine in these forums.

About choosing a language to learn coming from a web development background, like the OP.

If there's no hurry, I'd learn some high-level programming language (be it Python, Perl, Scheme, Smalltalk-80, Common Lisp, etc.) and then C. In a first stage, you need something that teaches you the fundamental and most general concepts of programming. After that, you should learn low-level programming which is a specific kind of programming; IMO is better to learn that after one has gained a reasonable level of confidence with the general concepts. There may be some exception I'm not aware of, but everything you are taught by high-level programming can be (or has to be) applied in low-level programming. e.g. you can always write a hashtable in C (I'm not saying it's easy or that you should... just saying that it is possible). 

IMO, learning the low-level part is compulsory. People here know I am very fond of taking a theoretical linguistics-driven approach towards programming and that I defend programming is completely independent of computers, e.g. because you can always write down some code in a piece of paper and an ideal programmer that knows the language and the APIs involved will understand it without needing a computer. But it's obvious that most programming is done on computers and you have to know how your tools work; there's where low-level programming comes in. And not only to know some stuff about hardware, but also for some basic OS features. Just that I believe one should learn these things after having learned the high-level part.

After learning C as your second language, you'll be quite ready to learn most languages according to your needs. And you'll find yourself getting the basic syntactic and semantic features in a couple of hours because you'll already know the general concepts involved in programming. Some languages may require some firther study; ASM, Forth and the Lisp dialects are which come to my mind.

---

### Post by directhex on 2011-04-19
> **kurum! said:**
> what rubbish are you talking about. Ruby works on Linux. What i mean by cross platform is code written in linux can run on Windows version of Ruby.

Just repeating your own nonsensical bollocks. And code written on .NET will run on Mono, and vice versa, unless you start putting OS-specific code in - but that's no different from calling "system 'c:\windows\sol.exe'" and claiming ruby is inherently not cross platform because that line won't run on linux.

---

### Post by bloodhacker2 on 2011-04-19
> **nvteighen said:**
> As much as I deeply hate C++, it'd just reveal huge ignorance if I stated that C++ has no uses. In fact, my main complain against it is that it was designed with almost every possible use in mind! But this is not a thread about C++ so I won't get into that; if interested on my views about this topic, look up for some posts of mine in these forums.

About choosing a language to learn coming from a web development background, like the OP.

If there's no hurry, I'd learn some high-level programming language (be it Python, Perl, Scheme, Smalltalk-80, Common Lisp, etc.) and then C. In a first stage, you need something that teaches you the fundamental and most general concepts of programming. After that, you should learn low-level programming which is a specific kind of programming; IMO is better to learn that after one has gained a reasonable level of confidence with the general concepts. There may be some exception I'm not aware of, but everything you are taught by high-level programming can be (or has to be) applied in low-level programming. e.g. you can always write a hashtable in C (I'm not saying it's easy or that you should... just saying that it is possible). 

IMO, learning the low-level part is compulsory. People here know I am very fond of taking a theoretical linguistics-driven approach towards programming and that I defend programming is completely independent of computers, e.g. because you can always write down some code in a piece of paper and an ideal programmer that knows the language and the APIs involved will understand it without needing a computer. But it's obvious that most programming is done on computers and you have to know how your tools work; there's where low-level programming comes in. And not only to know some stuff about hardware, but also for some basic OS features. Just that I believe one should learn these things after having learned the high-level part.

After learning C as your second language, you'll be quite ready to learn most languages according to your needs. And you'll find yourself getting the basic syntactic and semantic features in a couple of hours because you'll already know the general concepts involved in programming. Some languages may require some firther study; ASM, Forth and the Lisp dialects are which come to my mind.


Whats funny is that after reading everyone else's post i was thinking to myself "I need to start out with Python than Perl then move onto the C's."
I do appreciate your well thought out and explained theory, because your theory is actually my goal. The goal to have level of programing skill to where i can sit down with a pen and paper, hack out some code and have a product without touching a keyboard..

---

### Post by robots.jpg on 2011-04-19
I wish I had learned Python first. My education started with C, which in  retrospect was like teaching someone how to cook by first going to a  farm and harvesting wheat and milking cows to make ingredients by hand.   It was a huge distraction from all of the basic principles and methods I  was supposed to be learning at the same time.  I can understand that  school of thought for learning some things, but I don't think it works  well for software development.

---

### Post by PaulM1985 on 2011-04-19
I recommend C# or Java.  Something that deals with memory management for you and all you have to think about are the classes and how they interact.

---

### Post by unknownPoster on 2011-04-19
> **kurum! said:**
> that is your problem.

I said limited. So its good for games and some low level stuff, what else in terms of practicality?  


As other people are also refuting your points, I'm fairly certain you are in the minority here.
Here are some major applications written in C++:

OpenOffice is written in C++, I guess that isn't practical.
Most of the Adobe Suite is written in C++, again I guess you don't think that's practical.
Chromium and Firefox are written in C++, I guess that isn't practical either.
KDE is written in C++.

As  nvteighen expressed earlier, the biggest problem with C++ is that it tries to useful at everything but it's not exceptionally good at anything honestly.

So yeah, I'm surprised you claim I'm spreading FUD.

---

### Post by CptPicard on 2011-04-19
[http://www.winestockwebdesign.com/Essays/Lisp_Curse.html](http://www.winestockwebdesign.com/Essays/Lisp_Curse.html)

Today we had that linked to our intranet at work. I'm happy to work for a company where my skilled colleagues understand this sort of stuff. They're all excellent programmers. :)

---

### Post by nvteighen on 2011-04-19
> **CptPicard said:**
> [http://www.winestockwebdesign.com/Essays/Lisp_Curse.html](http://www.winestockwebdesign.com/Essays/Lisp_Curse.html)

Today we had that linked to our intranet at work. I'm happy to work for a company where my skilled colleagues understand this sort of stuff. They're all excellent programmers. :)

Great article :)

---

### Post by slavik on 2011-04-19
> **nvteighen said:**
> Great article :)
I am so sticking that one to lnostdal. :D

As for the sequence of learning languages ... I am of the opion of low-level -> high-level, simply because it makes you appreciate high-level. Otherwise, I feel, that you have no reason to learn low-level.

---

### Post by kurum! on 2011-04-19
> **directhex said:**
> Just repeating your own nonsensical bollocks. And code written on .NET will run on Mono, and vice versa, unless you start putting OS-specific code in - but that's no different from calling "system 'c:\windows\sol.exe'" and claiming ruby is inherently not cross platform because that line won't run on linux.
You are spouting rubbish again. Have you read my statement? I said code written in one language can run on another platform with the same language. You talk about .NET, now you find me VB compiler that can run in Linux without having to install Mono. Did Microsoft produce Mono? You write a python script in linux, and you can run it off in Windows version of Python. Same with Java/Ruby etc. That's where I am coming from.

---

### Post by kurum! on 2011-04-19
> **unknownPoster said:**
> 
OpenOffice is written in C++, I guess that isn't practical.
Most of the Adobe Suite is written in C++, again I guess you don't think that's practical.
Chromium and Firefox are written in C++, I guess that isn't practical either.
KDE is written in C++.

i did not say you can't do all these with C++.  The question is are the normal users going to be programming applications like that? No, they will be busy with data gathering, file/report formatting, doing web applications, doing every day system administration etc (these are what I call "practical". They are not , in their normal day, going to be programming  a full fledge word processing suite, or a OS desktop. They are just a minority

---

### Post by slavik on 2011-04-20
> **kurum! said:**
> i did not say you can't do all these with C++.  The question is are the normal users going to be programming applications like that? No, they will be busy with data gathering, file/report formatting, doing web applications, doing every day system administration etc (these are what I call "practical". They are not , in their normal day, going to be programming  a full fledge word processing suite, or a OS desktop. They are just a minority
Interestingly enough, Bloomberg and many other companies use C++ for applications which deliver services. The services include stock market data and trading applications in the least. Point being is that C++ is a rival to Java in the financial sector.

---

### Post by BenB1 on 2011-04-20
I am just starting out on learning to program. Have tried out various languages in the past year or so. Finally, chose to stick to the guns and learn C. My reasoning is pretty simple.

1. The Linux kernel is written in C.

2. C is the foundation into C++, learn C and ++ becomes easier to learn.

3. C is still used pretty universally, even if but to prototype programs. It can also give you fully workable software.

4. C will be taught in the two year degree course of computer science.

5. C is cross platform, thus portable.

6. Java is just C on steroids, learn C and Java is easier.

7. Learn C and most other languages are easier to master, such as, python, perl, awk, shell scripting.

8. C is adaptable. Developers came up with a library fixing the buffer overflow problem that occurs due to lack of bounds checking with input.

9. Just because it is C and there to learn.

10. Hacking code is enjoyable. :)

---

### Post by simeon87 on 2011-04-20
> **kurum! said:**
> i did not say you can't do all these with C++.  The question is are the normal users going to be programming applications like that? No, they will be busy with data gathering, file/report formatting, doing web applications, doing every day system administration etc (these are what I call "practical". They are not , in their normal day, going to be programming  a full fledge word processing suite, or a OS desktop. They are just a minority

Your definition of "practical" and "normal users" is rather lopsided. Everything that users need, with the possible exception of video games, can be considered "practical" and needed. You may choose to do web applications and system administration but many applications still need to raw power of C or C++. If you want to do Ruby then do Ruby but arguing that C/C++ have limited use today is just plain false. Remember Facebook's HipHop that turns PHP into C++ for speed? It doesn't matter that many are not going to write an operating system, knowledge of C/C++ can be useful in any field.

---

### Post by directhex on 2011-04-20
> **kurum! said:**
> You are spouting rubbish again. Have you read my statement? I said code written in one language can run on another platform with the same language. You talk about .NET, now you find me VB compiler that can run in Linux without having to install Mono. Did Microsoft produce Mono? You write a python script in linux, and you can run it off in Windows version of Python. Same with Java/Ruby etc. That's where I am coming from.

So your argument is that having multiple implementations of a standard is bad.

This might blow your mind: You can install Mono on Windows. Bam, Mono on Mac, Linux, Windows, Solaris, BSD.

---

### Post by ajackson on 2011-04-20
> **kurum! said:**
> You are spouting rubbish again. Have you read my statement? I said code written in one language can run on another platform with the same language. You talk about .NET, now you find me VB compiler that can run in Linux without having to install Mono. Did Microsoft produce Mono? You write a python script in linux, and you can run it off in Windows version of Python. Same with Java/Ruby etc. That's where I am coming from.

C# is the language, .NET and Mono are the applications of that language just as GCC is an application of the C language and Visual C++ of the C++ language. When the C# program relies on Window specific libraries (winforms or whatever it is called) then yes that stops the ability to easily just run on OS X/Linux/etc but no doubt that are platform specific libraries in Java or Ruby, just as there are in Python (try getting a Python script that uses PyQt to run on a Windows box without PyQt installed).

You find me a Python script that can run on Windows without Python being installed (note using stuff like py2exe installs the components of Python that script needs so Python is still installed). Show me a script in any language that can be ran without an interpreter being installed, sure some are installed by default but there are very few (if any) things that can run without the need for run time libraries and/or interpreters.

Don't accuse others of spouting nonsense when your own facts are up the swanny.

---

### Post by bloodhacker2 on 2011-04-20
So after reading the rants going on lol, im getting the idea that Python programs canot be run in windows without an interpreter, is this correct, or is it just Python scripts? 

See, most of my program building will be for linux based web servers and not for reproduction.

---

### Post by ajackson on 2011-04-20
> **bloodhacker2 said:**
> So after reading the rants going on lol, im getting the idea that Python programs canot be run in windows without an interpreter, is this correct, or is it just Python scripts? 

See, most of my program building will be for linux based web servers and not for reproduction.

You can use tools like py2exe to create "standalone" python programs but in truth all they do is bundle the bits of python needed together with your code, if you only have one it is probably ok that way but more than one it is easier to install python independent of your scripts.

In python terms scripts and programs are the same thing.

---

### Post by bloodhacker2 on 2011-04-20
OK i see now.

So since i will be using mostly linux to code with do you think python is a good starting point.

See, i am now convinced that i do need to learn all the C's after i am don't getting the fundamentals down of coding, but what i really want to know is which code is a good starting point?

Python?

---

### Post by lykwydchykyn on 2011-04-20
> **bloodhacker2 said:**
> OK i see now.

So since i will be using mostly linux to code with do you think python is a good starting point.

See, i am now convinced that i do need to learn all the C's after i am don't getting the fundamentals down of coding, but what i really want to know is which code is a good starting point?

Python?

I don't think you can go wrong learning python if you're coding applications on Linux or cross-platform.

I use it all the time at work, I code up pyqt stuff on my Kubuntu box, compile with py2exe in a vm and then put it on a Samba share to distribute to users.  Dragging all the python code across the network causes a little initial latency, but the ease of maintenance is worth it IMHO.

My only regret in learning python before getting a handle on C or C++ is that it's downright hard to go back and come to terms with all the rigamarole of those languages once you've been spoiled by python.  There are times when C++ would be a better fit (or else I want to work on a project written in C++), but I haven't the skills or the patience to figure it out.

But my standard advice is to learn a language for which you can find immediate practical application.

---

### Post by ajackson on 2011-04-20
> **bloodhacker2 said:**
> See, i am now convinced that i do need to learn all the C's after i am don't getting the fundamentals down of coding, but what i really want to know is which code is a good starting point?

Python?

Python is a very good starting point for learning programming, once you know how to program picking up new languages gets easier because all you are learning in the new syntax rather than the syntax and programming concepts.

As to whether you need to learn one of the many Cs, that depends a lot on what you want to achieve with programming. Each language will have it's strong areas and weak areas.

---

### Post by TheCompBoy on 2011-04-20
Maybe try read little more about em all and maybe try write the simple "Hello World" program with em all it might help you pick :)

---

### Post by Jonas thomas on 2011-04-20
One of the things, I'm thinking about reading the posts are what are the types of things you want to get out of your time investment learning to program.  Programming is a combination of skill and knowledge.  To get really good on some of the more complex languages takes time, practise and study. 

I think the extremes for justifying the time to learn how to program are  scratching an intellectual itch for pleasure versus the other end of the spectrum of needing to learn to program to put food on the table with minimun effort, 

  In the first post you said..

> My goal is to keep everything linux based and also have a option to build on windows, but i don't exactly know which code to choose. which one is more flexible and faster, more secure and easier to understand.. 

So... based on the opinions you've heard so far.. I'm sort of curious..
What are your thoughts about where you want to be in one year?
What kind of application do you want to be able to write?

You made some needs statements:
[LIST]
[*]Flexible
[*]Faster
[*]Secure
[*]Easy to understand
[/LIST]

Based on everything you've heard are these needs valid..

For myself, I spend a sizable personel investment trying to learn C++.  
I think I could train someone to be a function VB6 programmer in less than a week. I've been studying C++ for 1 year+ and I still feel like I've barely scratched the surface and producing a functional program for me seems to take a huge amount of effort. 

In hindsite, do I think I'm wasting my time? No.. I'm hoping that the experience will be like those guys who learned latin in high school... Spanish, French, Italian.. will come easy to those guys..  I'm not trying to steer you one way or another..  There been a bunch of thought provoking stuff said on this thread and I'm curious what you gotten out of it.

---

### Post by slavik on 2011-04-20
> **BenB1 said:**
> I am just starting out on learning to program. Have tried out various languages in the past year or so. Finally, chose to stick to the guns and learn C. My reasoning is pretty simple.

1. The Linux kernel is written in C.

2. C is the foundation into C++, learn C and ++ becomes easier to learn.

3. C is still used pretty universally, even if but to prototype programs. It can also give you fully workable software.

4. C will be taught in the two year degree course of computer science.

5. C is cross platform, thus portable.

6. Java is just C on steroids, learn C and Java is easier.

7. Learn C and most other languages are easier to master, such as, python, perl, awk, shell scripting.

8. C is adaptable. Developers came up with a library fixing the buffer overflow problem that occurs due to lack of bounds checking with input.

9. Just because it is C and there to learn.

10. Hacking code is enjoyable. :)
quoted for truth and sanity.

as for the rest ... just shut up and write code, who cares what language, design patterns are the same in any language, data structures are the same in any language. same design pattern or data structure fits the same problems better in any language ... this thread is getting closed, there is no way there will be an answer here.

---

