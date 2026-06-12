---
title: "Stick with Java?"
date: 2011-05-12
forum: Programming Talk
---

### Post by UbuNoob001 on 2011-05-12
Situation: this semester I took an class called Introduction to Software Design with Java. It was my first intro to programming.  The class had a very odd structure: 
1. The text was extremely high level. The first few chapters were all about object oriented programming, how objects interact, all about specification, etc (without ever talking about implementation). 
2. The lecture simply followed (directly) the text. And as a result was rather uninteresting. 
3. While highly theoretical (in that it was very high level approach), we never talked about how the computer was dealing with the information, etc. It was all very "hand waving/magic" approach. 



Okay so enough of the complaints: 


Question: This summer I'd like to dive a bit more into a language mainly out of frustration and lack of a good book. I'm thinking perhaps a lower level language. 

1. Would C++ be a good second language? Or should I give Java more time? 
2. If I am going to go with something else, is C++ sufficiently different, or should I go with C?
3. Going the other way, how about Python ? 

Some friendly suggestions would be great.

---

### Post by sanderd17 on 2011-05-12
Java is good if you want to make programs. If you want to understand how java works, you should learn some kind of assembly. I learned the basics of MIPS past semester and now I really know  how java, C, or any other language could do what it does.

MIPS is not so widely used as ARM or x86, but it's a simple language to learn (only basic and clear commands) and you can use SPIM on linux to write and run MIPS code. I used the book "Computer organisation and Design" from Patterson and Hennessy, but I guess that there will be good things on the internet too.

---

### Post by UbuNoob001 on 2011-05-12
> **sanderd17 said:**
> Java is good if you want to make programs. If you want to understand how java works, you should learn some kind of assembly[...]

Indeed, my interest is not in design of any sort of program or application but more to understand how things work within a program, and how it interacts with things outside of itself. I certainly don't want to ignore high-level ideas, as theoretical computer science and language appeal to me.
    I just feel that given the way I learn, I would learn more with a more bottom-up approach rather than by simply learning about objects right away. 


(as a side question, can C++ get as low level as C if you want it to?)

---

### Post by TheStroj on 2011-05-12
> **UbuNoob001 said:**
> (as a side question, can C++ get as low level as C if you want it to?)

Windows is written in C, C++ and C#. And by saying Windows I don't mean apps, but the OS itself. So the answer is yes, C++ can do lots of stuff. But I prefer C myself.

---

### Post by cgroza on 2011-05-12
> **TheStroj said:**
> Windows is written in C, C++ and C#. And by saying Windows I don't mean apps, but the OS itself. So the answer is yes, C++ can do lots of stuff. But I prefer C myself.
Did you look at the source code?:)

---

### Post by IWantFroyo on 2011-05-12
> **TheStroj said:**
> Windows is written in C, C++ and C#. And by saying Windows I don't mean apps, but the OS itself. So the answer is yes, C++ can do lots of stuff. But I prefer C myself.

Hmmm. Wikipedia lists it as C, C++, and Assembly. There are different sources, and I may very well be the wrong one here, though.

---

### Post by DangerOnTheRanger on 2011-05-12
I'd say Python. No, it's not a low-level language, but that doesn't sound like what you'd want. Python makes it easy to see how programs interact with other programs (through UNIX pipes, the GNOME VFS, and the like), and you can see how languages like Java and Python work (they both work on essentially the same principle), with getting bogged down in syntactic salt.

There is a Python interpreter written in Python, called PyPy, that enables you to see how interpreted languages (Java, Python, Lua, and basically everything besides C/C++) work at a high level, without using too much "magical code".

Having said all that, "how things work within a program" is somewhat ambiguous, could you please clarify on that?

---

### Post by muteXe on 2011-05-12
To be honest, sounds like you want a java (or other language) course, and *then* maybe a software design course

Personally I'm a c++ chap, but if you wanna learn java, then cool. But when i was younger I've been on a few OO design courses, and, well, they were hand-wavey as well.
You can talk about software design principles without even mentioning a language.

So, to answer your question, I'd probably stick with java. but learn the language first, and don't even worry about software design in depth.  At least not yet :)

Hope that helps,

mute

---

### Post by LoneWolfJack on 2011-05-13
> Indeed, my interest is not in design of any sort of program or application but more to understand how things work within a program, and how it interacts with things outside of itself.

Learn C, then Assembly. If you don't have a good understanding of any other programing language as of yet, take a PHP or Python course first.

---

### Post by CoffeeRain on 2011-05-13
I put my vote in for python. It is very useful because it is focused on data and that is really what a lot of things use. You can also use system commands in it so you can store lists as variables and things like that.

---

### Post by leg on 2011-05-13
Tend to agree with muteXe.

I would stick with Java and learn it better if I were you. Use the sun tutorials (Sorry Oracle) and don't worry about the Object oriented stuff until you have too. I think though the trick to learning to program is to stick with just one language until you are fairly used to it and are starting to get the deeper topics such as OO, Generics etc.

You will hit a plateau occasionally but stick with it and plough through the barriers .

---

### Post by KdotJ on 2011-05-13
I'd say stick with java, especially if you're going to be doing further classes using it. To be honest, in my opinion, doing it for a short amount of time teaches you just a small scratch on the surface. Switching to another language immediately is not necessarily the answer, java has more to know about it than you can possibly imagine and java is great for learning the object-oriented paradigm in great depth. If it was me (and this is my own opinion) I'd spend the time learning more about java as it will definately teach you about programming and topics like generics and OO and interfaces etc... It just takes time.

---

### Post by UbuNoob001 on 2011-05-13
> **DangerOnTheRanger said:**
> I'd say Python. No, it's not a low-level language, but that doesn't sound like what you'd want. Python makes it easy to see how programs interact with other programs (through UNIX pipes, the GNOME VFS, and the like), and you can see how languages like Java and Python work (they both work on essentially the same principle), with getting bogged down in syntactic salt.

There is a Python interpreter written in Python, called PyPy, that enables you to see how interpreted languages (Java, Python, Lua, and basically everything besides C/C++) work at a high level, without using too much "magical code".

Having said all that, "how things work within a program" is somewhat ambiguous, could you please clarify on that?

Well I suppose thats just it, I don't have a clear understanding of how a program (supposed a program in Python) interacts with another programs (or set of programs/OS- suppose in another language like C). How does it grab information from and communicate with the other programs, and what handles this interaction? 

> **LoneWolfJack said:**
> Learn C, then Assembly. If you don't have a good understanding of any other programing language as of yet, take a PHP or Python course first.

Yup, only a basic intro to OOP w/Java, basic implementation, specification, I/O Streams, Interfaces etc. But very little low level understanding. 

So it seems like a common suggestion is getting some play: start with something easy to learn/understand, get a good base of knowledge then move to something low(er) level like C. This sounds good to most of you guys?

---

### Post by Maheriano on 2011-05-13
You've scraped about 1% of what Java can do. Wait until you get into struts, MVC architecture and web services, it'll make your head spin. If you want to see what Java is capable of, I did the [www.westjet.com](www.westjet.com) website last year and it's completely written in Java and JSP.

---

### Post by simeon87 on 2011-05-13
> **Maheriano said:**
> You've scraped about 1% of what Java can do. Wait until you get into struts, MVC architecture and web services, it'll make your head spin. If you want to see what Java is capable of, I did the [www.westjet.com](www.westjet.com) website last year and it's completely written in Java and JSP.

While you're proud of your work, as an example it doesn't mean anything as it also could have been written in PHP or some other language.

---

### Post by Maheriano on 2011-05-13
> **simeon87 said:**
> While you're proud of your work, as an example it doesn't mean anything as it also could have been written in PHP or some other language.

Ya and it could have been written in Cobol, what's your point? I was just displaying the abilities that Java has beyond the basics of Object Oriented fundamentals to give you an idea of what it can do if you stick with it.

---

### Post by worseisworser on 2011-05-13
Since your main goal here is to understand internals and low-level stuff (and only that), going for C which is small and directly to the (your) point is good.

You don't need what C++ adds to C to do this; it'd be a waste of time IMHO.

Later you can combine C + Java (JNI) or C + Python (Ctypes) in a single program as a sort of bonus added to your extra knowledge about internals. Using C++ trying to do the same you'd have to wrap your code in C wrappers to do the same; kinda removing the point of C++ in that context.

---

### Post by UbuNoob001 on 2011-05-13
> **worseisworser said:**
> Since your main goal here is to understand internals and low-level stuff (and only that), going for C which is small and directly to the (your) point is good.

You don't need what C++ adds to C to do this; it'd be a waste of time IMHO.
[...]

Will a standard course in C++ (most texts or online tutorials (say like learncpp etc)) ignore the lower level C subset? Or is it just that the superset (including things I am less interested in) will add more time and complexity?

---

### Post by LoneWolfJack on 2011-05-14
> 
So it seems like a common suggestion is getting some play: start with something easy to learn/understand, get a good base of knowledge then move to something low(er) level like C. This sounds good to most of you guys?


Definitely. As I posted in another thread, most programmers started with a simple programming language. Back in the 80s it was BASIC. Nowadays it's something like PHP or Python.

I'd go for PHP because the syntax is heavily influenced by C.

It makes absolutely no sense to jump at the complex issues you want to address without first preparing your tools (learning the programming basics). Starting with OOP (especially Java) isn't a good idea.

---

### Post by jamesjenner on 2011-05-14
I'm surprised no one has mentioned learning about operating systems. It appears that you wish to understand the nuts and bolts, which I totally understand. It's the way I learn as well. When I'm told something I wish to understand why, being told "just because" is not enough for me.

That said, for a modern day operating system there are so many layers it's not funny. You wish to write programs and understand how they interact with the environment around them, well first you have to understand the environment.

As for language, well if you wish to understand the absolute lowest level then you should study chip architecture and do some assembler. You cannot get lower than this. But if you wish to learn what a programing language can do, how it interacts with the user via mouse/keyboard/etc, how it interacts with other software, software on other computers, file systems (for writing files, etc), then you really should learn a 'basic' language. C and C++ are pretty heavy. C++ is an extension from C and the name is actually a joke about how you can increment a variable in C++ (it lit. means C + 1). I would recommend C# or Java, although python is also quite handy. That would give you a good foundation and in all three you can branch into C or C++ if you wish later.

However I really recommend learning as much about operating systems and associated technology first.

just MHO.

Cheers,

James.

---

### Post by UbuNoob001 on 2011-05-14
> **jamesjenner said:**
> I'm surprised no one has mentioned learning about operating systems. It appears that you wish to understand the nuts and bolts, which I totally understand. It's the way I learn as well. When I'm told something I wish to understand why, being told "just because" is not enough for me.

That said, for a modern day operating system there are so many layers it's not funny. You wish to write programs and understand how they interact with the environment around them, well first you have to understand the environment.

As for language, well if you wish to understand the absolute lowest level then you should study chip architecture and do some assembler. You cannot get lower than this. But if you wish to learn what a programing language can do, how it interacts with the user via mouse/keyboard/etc, how it interacts with other software, software on other computers, file systems (for writing files, etc), then you really should learn a 'basic' language. C and C++ are pretty heavy. C++ is an extension from C and the name is actually a joke about how you can increment a variable in C++ (it lit. means C + 1). I would recommend C# or Java, although python is also quite handy. That would give you a good foundation and in all three you can branch into C or C++ if you wish later.

However I really recommend learning as much about operating systems and associated technology first.

just MHO.

Cheers,

James.

Very helpful. Thanks James. 

I think that I'm going to take the advice of lots of you guys and dive into Python for the summer, in addition to learning about OSs. Then maybe take a course in the fall on C/C++.   Many thanks for all your suggestions.

---

### Post by TheStroj on 2011-05-16
> **IWantFroyo said:**
> Hmmm. Wikipedia lists it as C, C++, and Assembly. There are different sources, and I may very well be the wrong one here, though.

My source is from Windows forums tho, the developer wrote it itself.

---

