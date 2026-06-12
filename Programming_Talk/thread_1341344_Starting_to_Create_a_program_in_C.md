---
title: "Starting to Create a program in C"
date: 2009-11-29
forum: Programming Talk
---

### Post by Venkat.yarl on 2009-11-29
Hey guys, 

I am an experienced programmer in Java but not in C and not on Linux, So I need some help about how to go about programming in c in Linux. 

How do I start Programming in C? Is there a specific editor u guys recommend? 

I am planning to write a C program for Ubuntu its kinda basically like a windows media center so I need some help with how to make sure the program is view in full screen, and Would I be able to play music and Movies on the full screen... and Do you have any suggestions of where I should go about starting the project.

---

### Post by MadCow108 on 2009-11-29
use the search
there are tons of threads about getting started. also look in the stickies.

why do you want to use C?
C is kind of low level and not really suited for application development.
Especially not for something security critical like a media center.

---

### Post by PmDematagoda on 2009-11-29
> **MadCow108 said:**
> C is kind of low level and not really suited for application development.
Especially not for something security critical like a media center.

There are plenty of applications developed in C, so I would disagree with you there. Also, I am not sure if C is that low level, because if you compare Xlib to GTK+(both in C) then Xlib is more "low level" compared to GTK+, so I think the low levelness depends on the libraries and API you use.

And how is a media center a security critical application? And even if it is one, then I would think that the kernel is one of the biggest security critical parts of an OS, but the Linux, Mac OS and *BSD kernels are mostly written in C.

---

### Post by MadCow108 on 2009-11-30
> **PmDematagoda said:**
> There are plenty of applications developed in C, so I would disagree with you there. Also, I am not sure if C is that low level, because if you compare Xlib to GTK+(both in C) then Xlib is more "low level" compared to GTK+, so I think the low levelness depends on the libraries and API you use.

And how is a media center a security critical application? And even if it is one, then I would think that the kernel is one of the biggest security critical parts of an OS, but the Linux, Mac OS and *BSD kernels are mostly written in C.

I know many applications are written in C. Thats why we need security patches all the time. Just have a look at security advisories. Most of them are related to programs written in C or bad C++ (aka C with classes).
C is a wonderful language for its use, but it is just to fragile for applications. Writing safe C code is a pain compared to writing safe code in higher level languages (not to mention the significant increase in development speed).

the kernel is written in C for a reason, the kernel is the low level part of the OS. So using a low level language is natural.
And kernel developers are highly skilled coders but still we have frequent security patches for the kernel (the last just a short while ago because of null pointer dereferencing)

and of course a media center is a security critical program. Media is number one reason for infection with malware under common users. (of course more frequent in the windows world, but also linux is not invulnerable)
Every program which handles random data from doubtful sources is security critical.

---

### Post by lisati on 2009-11-30
[http://ubuntuforums.org/showthread.php?t=333867](http://ubuntuforums.org/showthread.php?t=333867)

---

### Post by froggyswamp on 2009-11-30
@MadCow with all respect, give me a break lol you're starting another discussion where one emphasizes his own half truths and discards the other half truths. I pretty much agree with PmDematagoda. The other "higher" languages while solving some issues, introduce their own.
C++: Firefox, doesn't it have security issues? Go on and discard Firefox as being badly written or that you didn't mean C++.
Java: Give me a break, every update contains "security fixes"
whatever: bla bla
Use the right tool for the right job but there's no ideal tool.

---

### Post by MadCow108 on 2009-11-30
> C++: Firefox, doesn't it have security issues? Go on and discard Firefox as being badly written or that you didn't mean C++.
firefox is a browser with loads of features open to all kind of data and using tons of libraries (of which again quite a few are C)
Of course there will be security holes in such complex programs no matter which language you use. I never said there is the perfect language.
Just that some are more suited for certain tasks than others.

> **froggyswamp said:**
> 
Java: Give me a break, every update contains "security fixes"


java itself is not only written in java.

Applications written in java _less_ often have system compromising bugs which allow execution of arbitrary code.

> Use the right tool for the right job but there's no ideal tool.
exactly my point.
I just don't see why C should be considered as the ideal tool for a desktop application.
It is of course ideal for many many other tasks.

---

### Post by nvteighen on 2009-11-30
> **PmDematagoda said:**
> There are plenty of applications developed in C, so I would disagree with you there. Also, I am not sure if C is that low level, because if you compare Xlib to GTK+(both in C) then Xlib is more "low level" compared to GTK+, so I think the low levelness depends on the libraries and API you use.


Hm... Yes and no. A library can indeed increase your abstraction level, but always partially: No matter how abstract GTK+ is, you still need to use pointers and free memory manually. This means you still have to cope with the inherent lower-level aspects C has to deal with.

The only language where this doesn't happen is Lisp, because of its being a homoiconic language with a completely regular syntax. This makes that any extension done to Lisp makes it completely undistinguishable from the standard language, effectively modifying it instead of aggregating things on top of it. Another language that's quite near to this concept is Forth.

> And how is a media center a security critical application? And even if it is one, then I would think that the kernel is one of the biggest security critical parts of an OS, but the Linux, Mac OS and *BSD kernels are mostly written in C.

Well... if your media center conects to the Internet it is a security critical application. Of course the kernel should be safe enough to minimize the risk, but you can't pretend the kernel to secure everything...

> **MadCow108 said:**
> 
I just don't see why C should be considered as the ideal tool for a desktop application.
It is of course ideal for many many other tasks.

Well, it can be. I personaly don't like to generalize tasks under umbrella terms like "desktop application" or "system utility". I think those terms are more confusing than clarifying.

For example, C will be needed if you have to interface with the Linux kernel, no matter what are you writing. I tend to think "Interface with the Linux kernel" as a clear programming task in which a language makes sense. But, of course, you can separate that task from the rest of your application and have an interface for your kernel interface... and that can be done in Python or anyother language featuring a Foreign Function Interface.

---

### Post by Call My Function on 2009-11-30
I use GCC to compile my C++ code -- as far as I know, it compiles C too. Try checking it out. (Look for GCC in the Software Center, go [here]("http://gcc.gnu.org/"), or try Googling it. I don't recall exactly how I got mine, LoL.) It's completely free and works perfectly with Ubuntu.

As for editor, I use the gedit editor that comes with Ubuntu. (Applications -> Accessories -> gedit) It's basically notepad, but it has syntax highlighting for code. It'll automatically turn on highlighting when you save a file with the type extension, or you can tell it which highlighting type to use in the menus somewhere. It has served me well.

As for *learning* C, I'm sure there's a lot of good websites out there. Personally, I always prefer a good text book of some kind -- sometimes I find that web tutorials are lacking and don't point out those little issues that'll snag you. ;)

---

### Post by A_Fiachra on 2009-11-30
> **MadCow108 said:**
> I know many applications are written in C. Thats why we need security patches all the time. Just have a look at security advisories. Most of them are related to programs written in C ...


False attribution argument.

Since most linux applications involve C in one way or another, C is ubiquitous.  Saying C is the **[COLOR=black]cause [/COLOR]**of security problems is like saying 1's and 0's are the cause of security problems.  Your logic is backwards.  

C has been used since 1970.  Security patches for personal computers have become prevalent since the adoption of the Word Wide Web by non-technical users.  Open networking protocols expose users to malicious software irregardless of programming language.

---

### Post by Venkat.yarl on 2009-12-12
I am sorry if I am being rude but I am still confused if I should start writing the program in c or not, as  I said I am new to C. I forgot to mention before I have also programmed in c++ and C# (GUI) before but only windows systems using Visual Studio. 

I tried looking at the other forum about the programming beginnings but I got stuck on couple things.
```

[http://ubuntuforums.org/showthread.php?t=333867](http://ubuntuforums.org/showthread.php?t=333867)

```Basically this is my Idea for the project - 

-I have like 6 rooms in my house so what I want to do is get like 6 dell Hybrid with ubuntu running on all of them. 
-Each dell computer connected to a TV/ Audio device in that room.
-I Want to be able to start the program as soon as ubuntu starts without using anything else other than that.
-I want to  install a wireless keyboard/ remote to control the program.
-But the computers will not be used for anything else (so I would want to block out everything in the background, except for the updates)
-I want the program to be full screen (so everything else is blocked out)
-I want all these computers to search the entire harddrive to find the Audio/Video/Picture files.
-I want the computer to show if there are any additional/ portable devices plugged in, such as media cards/ ipods/ mp3players/ zune/ camera,  etc.
-If a cd/DVD is put in it should show those devices in the main menu and start playing them upon request.
-I want all the computers to search any additional devices plugged into them at that moment.
-I want the computers connected to the home network to search for any audio files present in the other computers but not in this, and only show the song once (if its present in all 6 of them instead of showing 6 copies)
-I also want it to search windows and mac computers that I have for any media as well.
-I would like to store the media info in an xml file or in a db so that i dont have to search the computer all the time (unless i am adding more media or if a device is plugged in)
-I want all the computers on the network to talk to each other and run my media center smoothly.


Any help on this tropic would be greatly appreciated.
Thank for all you help.

---

### Post by abhilashm86 on 2009-12-12
very cool thing!! hmm btw do u enjoy all 6 computers?? 
why is this concept, just curious!!

---

### Post by dwhitney67 on 2009-12-12
> **Venkat.yarl said:**
> I am sorry if I am being rude but I am still confused if I should start writing the program in c or not, as  I said I am new to C. I forgot to mention before I have also programmed in c++ and C# (GUI) before but only windows systems using Visual Studio. 

I tried looking at the other forum about the programming beginnings but I got stuck on couple things.
```

[http://ubuntuforums.org/showthread.php?t=333867](http://ubuntuforums.org/showthread.php?t=333867)

```Basically this is my Idea for the project - 

-I have like 6 rooms in my house so what I want to do is get like 6 dell Hybrid with ubuntu running on all of them. 
-Each dell computer connected to a TV/ Audio device in that room.
-I Want to be able to start the program as soon as ubuntu starts without using anything else other than that.
-I want to  install a wireless keyboard/ remote to control the program.
-But the computers will not be used for anything else (so I would want to block out everything in the background, except for the updates)
-I want the program to be full screen (so everything else is blocked out)
-I want all these computers to search the entire harddrive to find the Audio/Video/Picture files.
-I want the computer to show if there are any additional/ portable devices plugged in, such as media cards/ ipods/ mp3players/ zune/ camera,  etc.
-If a cd/DVD is put in it should show those devices in the main menu and start playing them upon request.
-I want all the computers to search any additional devices plugged into them at that moment.
-I want the computers connected to the home network to search for any audio files present in the other computers but not in this, and only show the song once (if its present in all 6 of them instead of showing 6 copies)
-I also want it to search windows and mac computers that I have for any media as well.
-I would like to store the media info in an xml file or in a db so that i dont have to search the computer all the time (unless i am adding more media or if a device is plugged in)
-I want all the computers on the network to talk to each other and run my media center smoothly.


Any help on this tropic would be greatly appreciated.
Thank for all you help.

Have you done anything yet to put you on the path to getting this done?

Do you have all of the computers yet?  Do you have a network setup?  Are all of the computers "talking" to each other?

What database and XML experience do you have?  Will you be able to produce code on your own, and merely need occasional assistance with syntax and/or bug issues?

If you are merely posting your "wish list", then you may also want to scribble it on paper, and mail it to the North Pole where, with luck, Santa will read it.

Anyhow, the project you are describing is beyond the scope of the forum.  I'm sure others will weigh in with opinions, but at the end of the day, you will probably still be staring at the wish list.

---

### Post by PmDematagoda on 2009-12-12
I think a media centre like moovida would be close to the kind of program you are looking for?

---

### Post by Venkat.yarl on 2009-12-13
> **abhilashm86 said:**
> very cool thing!! hmm btw do u enjoy all 6 computers?? 
why is this concept, just curious!!
Right now I have one Dell Hybrid to program once I get the basic Structure I will buy more.

> 
What database and XML experience do you have? Will you be able to produce code on your own, and merely need occasional assistance with syntax and/or bug issues?
As I said before I will be programming this on my own and need an occasional assistance. I was describing the check list for my project. I dont have much database experience just the basics, but I know how to use XML.

I am looking for somehelp trying to find out what language should I start this project in? and how would I be able to start this program once the computer starts.

---

### Post by Hellkeepa on 2009-12-13
HELLo!

I'd say pick the language you're most comfortable with, or the one you want to learn (if this is a learning experience). C or C++ would be ideal for this task, for a learning experience, considering how many similar GPLed applications there are out there.
Though, from your description, it seems as if you want to replace X as well..? I hope not, as that would really be reinventing the (square) wheel. You should probably take a look at the Qt library, for the graphical interface.

The whole "start as the computer starts" is easy, just add it to the correct runlevel's init-scripts.

Also; I hope you have a lot of time on your hands, and that you are not planning on having this up and running soon. Will probably take you a year or so, perhaps even more, to get this up and running as you'd like.
Personally, I'd find my favourite of the existing projects, and help them perfect it instead.

Happy codin'!

---

### Post by grayrainbow on 2009-12-13
> **Venkat.yarl said:**
> Right now I have one Dell Hybrid to program once I get the basic Structure I will buy more.

As I said before I will be programming this on my own and need an occasional assistance. I was describing the check list for my project. I dont have much database experience just the basics, but I know how to use XML.

I am looking for somehelp trying to find out what language should I start this project in? and how would I be able to start this program once the computer starts.
I don't know why people very often after decide(for unknown reasons) that they should do program that do 'that and that', and first thing they go is 'what language should I use?'. I'm sorry but that's, simply putted, stupid!You got a wish list - that's good, that's very good, many people won't be able to get even that. Now it's time to lookup in dictionary for definition of the word 'research'! Do you know the difference between client-server, and p2p model? Do you know the difference between various Linux desktop environments available? Do you know the difference between Linux distros?

Language is basicly the last thing to choose. And it's goes like: if I need flexibility, that include less resources waste(that on it's own include less money for power bills, and more 'green computing') - I need C/C++, otherwise it's more like what language with available libs for my needs I like.

---

### Post by Venkat.yarl on 2009-12-13
> 
Do you know the difference between client-server, and p2p model? Do you know the difference between various Linux desktop environments available? Do you know the difference between Linux distros?

Language is basicly the last thing to choose. And it's goes like: if I need flexibility, that include less resources waste(that on it's own include less money for power bills, and more 'green computing') - I need C/C++, otherwise it's more like what language with available libs for my needs I like.

I am quite Comfortable in Java, I have yet to master mysql (I just know the basics), I am thinking of programming this in java. I know about the client-server model. 

I have no clue about the linux desktop environments available, no clue abt the linux distros ( i am just going to use Ubuntu and keep upgrading it, and want to upgrade it automatically). I dont care about the power and money but I do care about the speed and the sleekness of the program.

---

