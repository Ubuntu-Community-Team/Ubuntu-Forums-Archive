---
title: "about c#"
date: 2011-06-29
forum: Programming Talk
---

### Post by ddimit on 2011-06-29
hey my first year of university has ended 
i did the whole year c which i didnt like it all
now one friend told me to learn c#
i started one tutorial a couple of days ago and really i like it because is really beautiful
but anyway do you think is good language for  coding any program on windows?
like security systems download managers viruses etc
maybe i be sound  like a teenager for the next  but i would like to have skills making virus
i think all have or had that feeling  so if its not able to do something like that i will stop learning it as univercity will not teach us that language

---

### Post by Pierrick584 on 2011-06-29
C# is pretty much microsoft only, well, unless you take in consideration non-official project.

C++ is much more of a better choice, since its not made by a compagny that would do anything to keep their product only for themself

---

### Post by ddimit on 2011-06-29
so does c# gives you the chance for making viruses?

---

### Post by Pierrick584 on 2011-06-29
Well, a virus is not a particularity of some programming language, a virus is something that do harmfull action, and (in many case) would manage to keep doing it as long as possible and prevent you from removing it.

So... any language could do such action, anything that can do basic file manipulation at the very least, and realy... not much of languages does not allow that

---

### Post by trizrK on 2011-06-29
> **ddimit said:**
> 
maybe i be sound  like a teenager for the next  but i would like to have skills making virus
i think all have or had that feeling  so if its not able to do something like that i will stop learning it as univercity will not teach us that language
Well for viruses i would use Python because it great for shell programming and scripting.

---

### Post by cgroza on 2011-06-29
> **trizrK said:**
> Well for viruses i would use Python because it great for shell programming and scripting.
Yes, tell that to the user:
"Please go to that website, download that program and install it so my virus can run on your computer."

---

### Post by Pierrick584 on 2011-06-29
> **cgroza said:**
> Yes, tell that to the user:
"Please go to that website, download that program and install it so my virus can run on your computer."


Hacker's most important skill, Social Enginering.


But anyway, i'm far from beign a pro of python but, i though there's some way to make a standalone app with it? and some other way to binary compile your python script if i am right

---

### Post by ddimit on 2011-06-29
i know that with any programming language you can make almost any program
im just asking specific for that language because as you know you must have the latest .net framework installed
as many computers included windows seven and xp does not have it 
so what do you have to say about that
is there any way to skip that problem?

---

### Post by unknownPoster on 2011-06-29
> **ddimit said:**
> i know that with any programming language you can make almost any program
im just asking specific for that language because as you know you must have the latest .net framework installed
as many computers included windows seven and xp does not have it 
so what do you have to say about that
is there any way to skip that problem?

You can't avoid that with Python or Java. Python needs the interpreter and Java needs a run-time to be installed.

C or C++ applications can be cross platform but you have to be diligent in their creation.

---

### Post by ddimit on 2011-06-30
ok thanks so almost any new language need a program to run

the only think i can to is to built the program with a lower net framework version so most computers will have it

---

### Post by ve4cib on 2011-06-30
You are correct: most current programming languages need other software present on the target computer in order for programs written in said language to run.  You need runtime libraries, interpreters, frameworks, etc...  Even most typical C or C++ programs need an operating system present (and at the most basic level an OS is really just another big program).  You can't really get away from that, but it's not much of an issue.

Everybody has an OS, so you can expect the basics to be present.  If you're targeting Linux users then you can expect basic shell scripting languages (sh and bash are pretty universal), python 2.x is likely to be present, and you'll have access to standard POSIX nonsense like pthreads at a bare minimum.  More than likely there will be other libraries and interpreters available, and specifying dependencies when you package your software will ensure that if your program needs something uncommon or that not everybody will have (Qt/GTK, specialized libraries like FANN or OpenCV, etc...) the user's package manager will alert them of this.

For Windows there isn't a nice package manager that can automagically fetch dependencies for you, but you can make slightly more liberal assumptions about the user's environment.  You know the user will have the Windows Forms libraries present, and there is a very, *very* good chance the user will have the .NET framework v3.0 or later installed.

But again, good documentation, and telling the user that "You need the .NET Framework v3.0 or higher to use this software," is always a good idea.  You could create an installer that would check for .NET, and install it if necessary if you really wanted to make sure everything went well.

Generally-speaking though, if you just want to write a program, put it on a USB stick or a CD (or a floppy if anybody still uses those things) and pass it around to your friends, you can probably just compile the .exe (and whatever other .dll files you need), and tell them to do a copy-and-paste, and then run the program, without even mentioning the .NET dependency.


I do need to ask you though: what kind(s) of software are you actually interested in writing?  I'll admit that I'm slightly unnerved by your constant asking "can I make a virus with ____?"  Do you actually want to make a virus?  If not, why do you keep asking?

Depending on what specific application you want to make, and who your target audience is, you might want to pick a language based on those requirements, rather than picking the language first and the project second.

---

### Post by bapoumba on 2011-07-04
I'm known to come late at parties :)
Closed.

---

