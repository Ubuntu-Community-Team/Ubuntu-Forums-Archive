---
title: "Is mono right for a newbie?"
date: 2006-04-17
forum: Programming Talk
---

### Post by Darkness3477 on 2006-04-17
Hey, I've been programming on and off, mostly with Python and a little bit of C++ -Which I dropped quite soon, as it was just a bit too much... Overkill. Anyway, I was looking at Java the other day, and whilst searching on google I found a fair few comparisons with it to C#, A language I have been interested in.

I've found a good book on Java and it goes through everything in a nice, easy to read and understand, but not dumbed down, way. However, I really don't like the idea about having to have a JVM to run my programs... Also, Java seems to be used more in web development, whist fun, it isn't exactly what I want to move into. 
So, I'm just wondering if Mono has enough documentation and possibly a newbie friendly book out that one could learn the basics of the langiuage and the syntax.

If anyone could tell me about such a book and a place where I could prehaps get it for free (Ebook, obviously) , I would be most greatful.

Thanks,
--Michael Maver.

---

### Post by sapo on 2006-04-18
I dont think mono would be a good choice for a first language, i always advice all newbies to start with python, you will learn very fast, but have the risk to fall in love with it and hate all the other languages after trying python :mrgreen:

---

### Post by Ozitraveller on 2006-04-18
Try this thread:

A good starter guide to C# and Mono? 
[http://ubuntuforums.org/showthread.php?t=153040](http://ubuntuforums.org/showthread.php?t=153040)

---

### Post by mostwanted on 2006-04-19
[QUOTE=sapo]I dont think mono would be a good choice for a first language, i always advice all newbies to start with python, you will learn very fast, but have the risk to fall in love with it and hate all the other languages after trying python :mrgreen:[/QUOTE]

Mono is not a language....

C# is probably not the most newbie-friendly language, but Boo (which also runs on Mono) could very well be. Unfortunately, it doesn't have a lot of documentation.

I think you should learn Ruby. It's a great language - everything is very "fits into places" about it and everyone who learns it comes to love it (tm).

---

### Post by LordHunter317 on 2006-04-19
[QUOTE=mostwanted]C# is probably not the most newbie-friendly language,[/quote]With the exception of it's generics (and not because generics are complicated, but because C#'s have major issues) it's far eaiser to learn than Java and that's taught everywhere.

However, I don't know any good introductory books for programmers that leverage .NET.

If you're really interested in learning to program correctly, go read *How to Design Programs* or *Structure and Interpretation of Computer Programs*.

Then, learn .NET and any language you wish.

---

### Post by SteveGeorge on 2006-04-19
I can understand why you dropped C++ as a first language ;-)  But why did you drop Python?

It's very friendly for new programmers as you've got the interactive command line, the syntax is straightforward and there's a good set of general modules you can use in your programs.  There's also great tutorial like [Dive into Python]("http://diveintopython.org/"), and [Think Like a Computer Scientist]("http://www.ibiblio.org/obp/thinkCSpy/") along with the mailing list [Tutor]("http://mail.python.org/mailman/listinfo/tutor").  If you want an IDE try PIDA.

Python is definitely easier to learn than C# or Java if you have no particular background.  There are some benefits to both of them particularly if you come from a C background or are going to do large projects.  C# using the mono runtime and the integrated tools (like [Monodevelop]("http://www.monodevelop.com/")) is easier to get on with in my opinion.  There's also a good books by O'Reilly like [Programming C#]("http://www.oreilly.com/catalog/progcsharp2/") and the [Mono Developers Handbook]("http://www.oreilly.com/catalog/monoadn/index.html") if you want to try some desktop development.

Steve

---

### Post by wyk on 2006-04-21
people, plzz help me out.
from the start i am a newbee in linux.
i downloaded the latest mono installer(1.1.15) for linux, installed using the instructions from mono project, now i got a mono directory, and try to run the MonoDevelop icon(a hammer on it), it doesn't do anything.
i've read in installerinstruction that the etc/profile must contain some 4 more lines, i opened it and it did not have the specified lines.

can anyone help?

---

### Post by SteveGeorge on 2006-04-21
[QUOTE=wyk]people, plzz help me out.
from the start i am a newbee in linux.
i downloaded the latest mono installer(1.1.15) for linux, installed using the instructions from mono project, now i got a mono directory, and try to run the MonoDevelop icon(a hammer on it), it doesn't do anything.
i've read in installerinstruction that the etc/profile must contain some 4 more lines, i opened it and it did not have the specified lines.

can anyone help?[/QUOTE]

Wyk you'd be better off to install the mono package that is in Ubuntu, rather than using the source installer from the mono site.  That way when you upgrade latter Ubuntu will upgrade everything from you.

The best way is to use synaptic and do a search for mono.  At a minimum you want mono, monodoc and monodevelop.  There are also some documentation packages but I can't remember their names.

Steve

---

### Post by wyk on 2006-04-21
that's what i did finally. but i wanted to have the latest version :(

---

### Post by SteveGeorge on 2006-04-21
You should be fine with the slightly older version.  You probably don't really need the latest version to learn mono.  And if you start mixing packages (src/deb) you'll probably spend more time trying to get your system fixed than learning mono ;-) ... that happens to me all the time!

Steve

---

### Post by wyk on 2006-04-22
it turned out that i actually did install mono from .bin . but when i double click the MonoDevelop icon, the program doesn't start. can anyone tell how to add it to the applications menu> prorgamming. the monodoc is there, but i want to add monodevelop. or is it at leas posible?

and p.s> did anyone try to import an visual c# express 2005 project in monodevelop, cose i get some strange error.

---

### Post by Darkness3477 on 2006-04-23
> **SteveGeorge]I can understand why you dropped C++ as a first language  said:**
> Dive into Python[/URL], and [Think Like a Computer Scientist]("http://www.ibiblio.org/obp/thinkCSpy/") along with the mailing list [Tutor]("http://mail.python.org/mailman/listinfo/tutor").  If you want an IDE try PIDA.

Python is definitely easier to learn than C# or Java if you have no particular background.  There are some benefits to both of them particularly if you come from a C background or are going to do large projects.  C# using the mono runtime and the integrated tools (like [Monodevelop]("http://www.monodevelop.com/")) is easier to get on with in my opinion.  There's also a good books by O'Reilly like [Programming C#]("http://www.oreilly.com/catalog/progcsharp2/") and the [Mono Developers Handbook]("http://www.oreilly.com/catalog/monoadn/index.html") if you want to try some desktop development.

Steve

I dropped C++ because it was a tab too much at the time. However, looking over some of the stuff... I feel now that I could probably take it on -maybe even win!

Python is a great language, and I love to use it. However, I want something more out of learning to program then just a hobby. I wish to get into a CS course in Uni when I finish High School and end up in a Computer related job after that. Maybe not Programming, but I definately see Programming as a skill that would be useful in any computer related job.

And, after searching around on certain websites, I've noticed that C++, VB, Java and C# are some of the most common programming languages that are requirements for jobs. C++, java and C# would be great to learn, whilst VB is a no go as I don't have a computer with Windows on it apart from a Latop whihc is crappy at best. So, after already trying out C++, i thought I would look at Java and C#. After looking at a few basic program (source code) I was wondering which one would be better to learn. I know that some people think Java is great, whilst others don't like it and I know the same to be true for C#. So, i thought I might read a book on both, and then deicde. However, I realised that C# might be a problem, then I heard of Mono... So i was just wondering if it would be friendly to learn for a newbie. 

I mean, I wouldn't even consider trying to learn C# if Mono wasn't easy to use... So, really, this thread is just for me to figure out if I want to try to learn the most basics of C#, so I can then make pick what language to learn (C#, C++ or Java).

---

