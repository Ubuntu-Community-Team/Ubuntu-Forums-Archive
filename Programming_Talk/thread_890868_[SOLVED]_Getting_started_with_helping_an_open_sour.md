---
title: "[SOLVED] Getting started with helping an open source project"
date: 2008-08-15
forum: Programming Talk
---

### Post by Predator106 on 2008-08-15
Hi, I would like to know how to "get involved" in an existing open source project, I have checked out launchpad, but it is incredibly overwhelming (maybe it's just at first sight). But could somebody provide me with any kind of tips or a small tutorial/guide of what to do, what to know if you do use Launchpad, it seems like it would be more organized than any other method.

---

### Post by tamoneya on 2008-08-15
first I would pick a project which you like.  Then you should try and get in contact with the developers of that project.  If they happen to use launchpad they can help you get familiarized with what you need to know.  Out of curiosity what is it that you are trying to contribute.  What languages do you know (spoken or programmed).

---

### Post by Predator106 on 2008-08-15
English :)

Visual Basic (ick), C#, and some C++ (still learning).

---

### Post by bruce89 on 2008-08-15
First, you need to find something that interests you (or something with a bug that is easily fixed). There's no point in generally saying "I want to help out" unless you know what you want to actually do.

After this, it's a simple case of downloading the source, compiling it, monkeying with it and repeat. After you've done something, submit a patch to the project.

---

### Post by Kadrus on 2008-08-15
I don't think you're gonna find a lot of Visual Basic open source projects.
go to code.google.com
and search around,you might find some C# open source projects.
same goes in sf.net
and continue learning cpp,because there are plenty of open source program written in cpp.

---

### Post by bruce89 on 2008-08-15
> **Kadrus said:**
> and continue learning cpp,because there are plenty of open source program written in cpp.

I wouldn't say that any one language is more used than any other. Having said that, C is probably pretty well used, but not so much these days.I don't think you're gonna find a lot of Visual Basic open source projects.

In other words, learn languages if you have to for a project.

---

### Post by Predator106 on 2008-08-15
Yeah, well, I'm actually more interested in C++ projects than anything, as it is a more high level language, and I can also stay away from the managed-microshaftiness.

But the thing is, I'm not sure which project I could help with, and it seems like the bugs that people submit are very complex (unless that was just first-glance). It appears that the bugs require things like "back-tracing" (no idea how to do that).

Would that really be a necessity? Another problem is, I'm not sure *which* project I would be interested in, I'm assuming things relating to Gnome and other higher-up projects are out of my league, so where could I start? I'm unsure of what to do.

---

### Post by Kadrus on 2008-08-15
Well head to [www.sourceforge.net](www.sourceforge.net) and search around,see what interests you,download it's source code and start hacking it.
many open source code hosting websites.
And Google,you will find more results than you think.

---

### Post by pmasiar on 2008-08-15
> **Predator106 said:**
> Hi, I would like to know how to "get involved" in an existing open source project, 

you have first bonus point: joining existing project instead of starting new!

any project would be glad to have new developer. It's up to you to decide what is so exciting you want spend hundreds of hours learning it.

But before you sign off your soul in C++, I would advice you to learn Python: hackers like it because it is 10 times more productive than C++. Learn it to understand why.

BTW, sadly I need to remove your bonus point :-) you need to learn using google and search archives:

[ Entry Point into Open Source Development](http://ubuntuforums.org/showthread.php?t=883130)

---

### Post by Predator106 on 2008-08-16
Okay, and btw, I did search, I use google frequently, and came across nothing of any interest-or importance. The thread that you directed me to was not of much help either, but was more or less serving as an argument for people with a difference in opinions.

As for python, I don't know, it doesn't feel like a high-level language to me, I don't like the structure of it, it reminds me more and more of Basic.

---

### Post by pmasiar on 2008-08-16
> **Predator106 said:**
> As for python, I don't know, it doesn't feel like a high-level language to me, I don't like the structure of it, it reminds me more and more of Basic.

I will be interested in Basic with OOP, list comprehension, generator expressions, operator overloading, and decorators. Which one is it? :-)

---

### Post by Predator106 on 2008-08-16
I was basically comparing the syntax and structure to Basic, not the functionality. I hate to say it, but I really miss things like the brackets and things, that's part of the reason why I didn't go back to Visual basic after I have been at C#, it just seemed more productive and more clean.

---

### Post by pmasiar on 2008-08-16
> **Predator106 said:**
> I was basically comparing the syntax and structure to Basic, not the functionality.

I know, that's the only way to consider them alike: both are easy to learn for beginners. But syntax is just skin deep. Real power of any language is not in it's syntax, so looking at syntax only you miss the important part. Python is much deeper than Basic.

Consider reading "Beating the Averages" if you want to understand what 'high level language' might mean, and how to become above-average programmer (if you care about learning and want to challenge and expand your thinking of course). We just had big discussion about it [ It's not wrong not knowing, but it's wrong not wanting to know](http://ubuntuforums.org/showthread.php?t=890695) in case you missed it :-)

---

### Post by NathanB on 2008-08-16
> **Predator106 said:**
> Hi, I would like to know how to "get involved" in an existing open source project, I have checked out launchpad, but it is incredibly overwhelming (maybe it's just at first sight). But could somebody provide me with any kind of tips or a small tutorial/guide of what to do, what to know if you do use Launchpad, it seems like it would be more organized than any other method.

Maybe your first contribution could be taking the knowledge you've gained from this thread and create this missing "small tutorial/guide" so that others will have an easier passage.  Maybe LaRosa can suggest a way to incorporate the information into a sticky and/or wiki.

Here is my "short list" of references I believe are essential for anyone thinking about contributing to F/OSS:

**Autotools**
[http://en.wikipedia.org/wiki/GNU_build_system](http://en.wikipedia.org/wiki/GNU_build_system)
[http://sources.redhat.com/autobook/](http://sources.redhat.com/autobook/)

**ftp and sftp**
[http://tldp.org/HOWTO/FTP.html](http://tldp.org/HOWTO/FTP.html)
or do 'man ftp'
or use a GUI front-end

**pgp**
[http://en.wikipedia.org/wiki/Pretty_Good_Privacy](http://en.wikipedia.org/wiki/Pretty_Good_Privacy)

**ssh**
[http://www.openssh.org/](http://www.openssh.org/)
[http://en.wikipedia.org/wiki/Secure_Shell](http://en.wikipedia.org/wiki/Secure_Shell)

*Version Control/Repositories*

"Old-school" Centralized (client-server)

**Concurrent (CVS)**
[http://www.nongnu.org/cvs/](http://www.nongnu.org/cvs/)

**Subversion (SVN)**
[http://subversion.tigris.org/](http://subversion.tigris.org/)

"New-fangled" Distributed

**Git**
[http://git.or.cz/](http://git.or.cz/)

**Bazaar**
[http://bazaar-vcs.org/](http://bazaar-vcs.org/)

*Hosting Services*

**SourceForge**
[http://www.sourceforge.net/](http://www.sourceforge.net/)
o No platform restriction (can host a Windows-only product)
o Webpage (can use some of this as filespace if you wish)
o Code Repository:  CVS and SVN
o Trackers
o Task Management
o Wiki
o Mirrored file-release system
o Mailling lists/Forums

**Google Code**
[http://code.google.com/hosting/](http://code.google.com/hosting/)
o No platform restriction (can host a Windows-only product)
o Webpage (via [http://pages.google.com/](http://pages.google.com/) )
o Code Repository:  SVN
o Tracker
o Wiki

**Alioth**
[http://alioth.debian.org/](http://alioth.debian.org/)
o Webpage
o Code Repository:  CVS
o Trackers
o Task Management
o Mailling lists/Forums

**Launchpad**
[https://launchpad.net/](https://launchpad.net/)
o No web hosting
o Code Repository:  Bazaar
o Tracker
o Task Management
o Messaging/Feedback system

**Public Git Hosting**
[http://repo.or.cz/](http://repo.or.cz/)

**GNU Project Hosting**
[http://savannah.gnu.org/](http://savannah.gnu.org/)

**Freshmeat (announcing only -- they don't host anything)**
[http://freshmeat.net/](http://freshmeat.net/)
o Product MUST be *nix-, BSD-, or Mac-related

Also, if your project is aimed at Joe User, they are unlikely to want to do the "./configue..make..make install" routine -- so someone on your team will need to know how to build binary packages.  From Ubuntu, hold Alt and press F2 to get the command dialog, then type "yelp" to get good reference material on packaging.

Nathan.

---

### Post by Colbrac on 2008-08-17
To come back to the question, which project to pick: Look at the programs that you use now. Find one that still has little quirks? Do you wish there was some extra feature in it that would help you a lot? If that is the case, find out if the program is written in a language you know or want to start knowing and go help out that project.

As an example: At the beginning of 2008 I knew a little matlab and had some basic knowledge of what programming is about. I started learning python and soon I found myself wanting to version control small python scripts. I picked bzr to do that and found Olive to handle bzr branches through a gtk interface. 'Unfortunately' Olive (now part of bzr-gtk) had a lot of quirks and rough spots and when I found out it was actually a python program it didn't take long before I made my first changes in the source. Within a month I was made bzr-gtk maintainer, completely replaced the olive glade interface with a pure gtk one and gave the looks of Olive some changes. See the 0.95.0 release for that. Thanks to Olive I now know gtk ui building, event handling, and much more.
Similarly, I recently bought a bluetooth + Java ME capable phone. I want to use it as a remote control for my desktop so I find several options (bluepad, ganyremote, lbrc) and finally pick lbrc as my favorite. Again, it has rough spots and is written in Python so before I know it, I'm a developer with writing rights on trunk and now I am learning about D-Bus, bluetooth interfacing, maybe even J2ME! :)

---

### Post by dje on 2008-08-17
what languages do you know? html, css, php and python developers are welcome to help out with [Ubuland]("https://launchpad.net/ubuland")

dje

---

### Post by Predator106 on 2008-08-17
Well, let's say if I did learn python, what open source projects are available, I don't like google code, launchpad is really hard to find things in, are there any projects that I may like, I would probably prefer smaller ones, I don't want to be writing any huge application or kernel code :) (even though it isn't in python, but you get my point).

Why does it seem like every site that tries to offer bug tracking, and have sourcecode available, is very, very hard to navigate and find something (when you don't know what it is that you are looking for).

---

### Post by pmasiar on 2008-08-17
> **Predator106 said:**
> Why does it seem like every site that tries to offer bug tracking, and have sourcecode available, is very, very hard to navigate and find something (when you don't know what it is that you are looking for).

because all projects need to fix bugs and share code?

You are expected to be self-starter, maybe ask some questions on mailing list but then read the code and make sense of it (and possibly write a how-to docs for people who will come after you, blazing the trail). So if you cannot, maybe you are not ready yet? Try to solve simpler training tasks, see wiki in my sig.

---

### Post by adamogardner on 2008-08-17
> **Predator106 said:**
> Well, let's say if I did learn python, what open source projects are available, I don't like google code, launchpad is really hard to find things in, are there any projects that I may like, I would probably prefer smaller ones, I don't want to be writing any huge application or kernel code :) (even though it isn't in python, but you get my point).

Why does it seem like every site that tries to offer bug tracking, and have sourcecode available, is very, very hard to navigate and find something (when you don't know what it is that you are looking for).

you can always try the project I'm working on: [http://ubuntuforums.org/showthread.php?t=892483](http://ubuntuforums.org/showthread.php?t=892483)  At the very least, an interesting read.

---

### Post by cszikszoy on 2008-08-17
Gnome-Do is written in C# (Mono) and the developers are very welcoming to new contributions and plugins.  Check out the IRC channel sometime at #gnome-do on Freenode.  Speak with some of the people there, I'm sure they'd love some help.

---

### Post by jespdj on 2008-08-18
1. Find a project that you would like to contribute to.
2. Read the developer documentation for the project.
3. Get the source code for the project and try building it yourself . Read the documentation for all the tools that you need to build it.
4. Subscribe yourself to the developers mailing list for the project, and look through the archives of the mailing list to see what the developers are doing.
5. Look through the bug database for the project and pick some bug that you think you could handle.
6. Discuss on the developers mailing list or on IRC what you want to work on.
7. Dive into the source code, and take your time to figure out how it is structured.
8. Try to find out the source of the bug, maybe use debugging tools to discover what's happening.
9. Fix the bug.
10. Submit your patch to the bug database.
11. Discuss your patch with the other developers.

Etc...

As pmasiar already said, on most projects you're expected to find out the majority of stuff yourself; most other developers don't have the patience to explain every little step to newcomers. Do a lot of reading and learning about the tools that you need to use, and try to figure out how things work yourself.

---

