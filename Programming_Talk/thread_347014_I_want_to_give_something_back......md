---
title: "I want to give something back....."
date: 2007-01-26
forum: Programming Talk
---

### Post by Catsworth on 2007-01-26
.....eventually.

Anyway, I've just started with Ubuntu (made the shift to using Ubuntu for about 95% of what I do on the PC) and it occurs to me that I've got an opportunity like I never had with Windows - the opportunity to really give something back, and to contribute to the future of the OS.

I like programming (or at least, I enjoy what little bits of programming I do - I'm learning Java as part of my degree and I've got some experience in Visual Basic and VBA) so I figure that I'd like to expend some effort learning a new programming language alongside the effort I'm expending to learn a new OS.

There's a couple of reasons for this: a) I think that if I can learn more about the way that the languages that make up Ubuntu and its application set work I can gain a better insight into the workings of the OS, which should help me in my aim to learn more about the OS, and b) I would eventually like to contribute something towards the development of Ubuntu and the applications that can be used with it.

So, that's the waffle out of the way.

I found [this thread]("http://www.ubuntuforums.org/showthread.php?t=333867"), which gives some excellent starting points, but there are a huge number of languages out there and I have no idea which to start with.

Which language would fit in best with the aims I've stated above?  Which would allow me to contribute to the development/extension of Ubuntu and its applications (or just *nix applications in general)?

Or, if you prefer, am I over thinking this?  Does it really matter which language I start to learn?  

Thanks :)

---

### Post by viciouslime on 2007-01-26
Go with python :)

---

### Post by hod139 on 2007-01-26
I would suggest finding a specific project that interests you, and then contributing to that project.  The ubuntu wiki has a nice page on how you can contribute. [https://wiki.ubuntu.com/ContributeToUbuntu](https://wiki.ubuntu.com/ContributeToUbuntu).

---

### Post by Catsworth on 2007-01-26
> **viciouslime said:**
> Go with python :)

Is that because Python is the prevailant language in Ubuntu/*nix?

---

### Post by Catsworth on 2007-01-26
> **hod139 said:**
> I would suggest finding a specific project that interests you, and then contributing to that project.  The ubuntu wiki has a nice page on how you can contribute. [https://wiki.ubuntu.com/ContributeToUbuntu](https://wiki.ubuntu.com/ContributeToUbuntu).

Good call, will do.

---

### Post by po0f on 2007-01-26
Catsworth,

Actually C/C++ are the more prevalent languages for *nix development.  The kernel is written in C if you didn't know.  The majority of GNOME apps are written in C.  KDE is C++.

Python is easy to learn and available on a lot of platforms as well; it's a good choice for beginners.  There are bindings to a ton of libraries, and there are a couple of knowledgeable Python programmers on these forums.  Not to say there *aren't* good C/C++ programmers here.  ;)  We have a decent variety of language enthusiasts.

Whichever language path you choose to pursue, there is an enormous amount of help available, if not here then elsewhere on the net.

---

### Post by phossal on 2007-01-26
> **po0f said:**
> Catsworth,

Actually **C/C++ are the more prevalent languages for *nix development.  The kernel is written in C if you didn't know.**  The majority of GNOME apps are written in C.  KDE is C++.

Python is easy to learn and available on a lot of platforms as well; it's a good choice for beginners.  There are bindings to a ton of libraries, and there are a couple of knowledgeable Python programmers on these forums.  Not to say there *aren't* good C/C++ programmers here.  ;)  We have a decent variety of language enthusiasts.

Whichever language path you choose to pursue, there is an enormous amount of help available, if not here then elsewhere on the net.

Well done.

---

### Post by Catsworth on 2007-01-26
> **po0f said:**
> Catsworth,

Actually C/C++ are the more prevalent languages for *nix development.  The kernel is written in C if you didn't know.  The majority of GNOME apps are written in C.  KDE is C++.

Python is easy to learn and available on a lot of platforms as well; it's a good choice for beginners.  There are bindings to a ton of libraries, and there are a couple of knowledgeable Python programmers on these forums.  Not to say there *aren't* good C/C++ programmers here.  ;)  We have a decent variety of language enthusiasts.

Whichever language path you choose to pursue, there is an enormous amount of help available, if not here then elsewhere on the net.

Some great help there, thanks very much for that.

I didn't know that the kernel was written in C - knowing that now it makes sense to start looking at C as a language to learn.

---

### Post by lnostdal on 2007-01-26
#1: If you want more insight into the OS etc. learn C. What is compilation? What is linking - what happens when you link and/or load a library at runtime? Try to develop a .so library. Understand errors/warnings from the compiler and OS instead of ignoring them (as under Windows). What are libraries? What are the symbols within them? Mess with threading (pthreads), IPC and sockets. Learn to use GDB,  DDD and Valgrind. Learn a version control system - or many. Figure out where to find API-docs and learn to read them (man, info, apropos .. etc.). Know how to read source-code as documentation; header files. Know how to find developer-libraries and documentation using APT (almost everything is there). Study the Linux boot-procedure, the init-process, runlevels .. etc. .. a high-level overview gets you very far. Learn to use a build-tool like Scons.

..but move along to the next step ASAP when you feel you have enough understanding of how stuff works "down there". The point isn't to "know everything" but to know how to find information about, or possibly debug - most things. Do not be fooled and try to stretch C to solving higher level problems efficiently (read: stay away from C++). Skip to step two loong before you feel the need to do high-level stuff in either C or C++:

#2: If you want to extend and/or develop new (edit: application/tool-) stuff fast/efficiently learn something like Python, Ruby or Lisp. Also learn GTK+, pick a DB and learn SQL. 

Learn when and how to optimize. Sometimes you need to write parts of your software in different languages; learn how to do this also. Study the history and concepts of OSs and programming languages. A high-level overview or general idea gets you a long way and is "good enough" in most cases; you'll be able to look up stuff when needed.

You can skip parts of the first step and still manage quite well within the second one I think.

..simple; this should only take you a couple of years.. :)

---

### Post by phossal on 2007-01-26
> **Catsworth said:**
> I didn't know that the kernel was written in C - knowing that now it makes sense to start looking at C as a language to learn.

lol Oh, boy. This thread will be on fire within *minutes* ;)

---

### Post by Wybiral on 2007-01-26
It's generally pretty difficult to write device drivers or to actually help linux support other systems with HLL like python/ruby... You generally need knowledge of asm, C, or C++ for that.

I think this is one thing that linux really needs... Not more desktop apps.. A lot of people are turned off of linux because it doesn't support their wireless card or monitor... I think helping linux support these things are probably the biggest contributions you can make.

Not that adding to the software support isn't very helpful too, I just think that hardware support is probably a bigger issue than anything. Even writing one or two more device drivers could make the difference of many many new linux users... Writing a bunch of applications *probably* wont make that big of a change.

But once again... Applications are never bad, what's an OS without something to run? But hardware is probably of bigger necessity.

---

### Post by lnostdal on 2007-01-26
take a look at this site if kernel-hacking seems interesting [http://kernelnewbies.org/](http://kernelnewbies.org/) .. intimate knowledge of C is required knowledge for this, get the book "The C Programming Language": [http://www.amazon.com/C-Programming-Language-2nd/dp/0131103628](http://www.amazon.com/C-Programming-Language-2nd/dp/0131103628)

---

### Post by phossal on 2007-01-26
If it were your first language, I'd recommend: [Practical C Programming]("http://www.amazon.com/Practical-Programming-3rd-Steve-Oualline/dp/1565923065/sr=8-1/qid=1169847479/ref=pd_bbs_1/102-3190172-6568155?ie=UTF8&s=books"). It's a touch more gentle, but still gets you the important info.

---

### Post by jblebrun on 2007-01-27
> **Wybiral said:**
> It's generally pretty difficult to write device drivers or to actually help linux support other systems with HLL like python/ruby... You generally need knowledge of asm, C, or C++ for that.

I think this is one thing that linux really needs... Not more desktop apps.. A lot of people are turned off of linux because it doesn't support their wireless card or monitor... I think helping linux support these things are probably the biggest contributions you can make.

Not that adding to the software support isn't very helpful too, I just think that hardware support is probably a bigger issue than anything. Even writing one or two more device drivers could make the difference of many many new linux users... Writing a bunch of applications *probably* wont make that big of a change.

But once again... Applications are never bad, what's an OS without something to run? But hardware is probably of bigger necessity.

Unfortunately, the driver problem is not due to a lack of competent, brilliant C programmers. The lack of drivers results from the hardware manufacturer's lack of willingness to provide the necessary information about the hardware in question. So, writing a driver requires a LOT more work, because you need to reverse engineer its operation, either by hacking through binary code in windows, or doing LOTS of testing. 

So if you REALLY want to contribute to the driver problem, learn how to probe into hardware to figure out how it works.

If you want to learn to program, play around with a few languages, and focus on the one that you have the most fun with. A language like C will allow you to learn more about how the machine works, a language like Python or Lisp will allow you to quickly learn more about algorithms and programming theory.

---

### Post by amo-ej1 on 2007-01-27
> **phossal said:**
> If it were your first language, I'd recommend: [Practical C Programming]("http://www.amazon.com/Practical-Programming-3rd-Steve-Oualline/dp/1565923065/sr=8-1/qid=1169847479/ref=pd_bbs_1/102-3190172-6568155?ie=UTF8&s=books"). It's a touch more gentle, but still gets you the important info.

I really like the books by Steve Oualline, my first book about C++ was Practical C++ programming, the main advantage of these books is that they are extremely practical, they teach you how to program and they teach you how to do in in a Unix-like environment. The only disadavantage is that Practical C++ programming (although not my edition) didn't go very deep into OO and the STL wasn't mentioned at all but back than .... yeah I know ;-)

Another disadvantage is that Practical C++ and Practical C programming are extremely alike so read one of them but not both or you'll get bored ;-)

A third, more recent book by the same author is: How not to program in C++ ( [http://www.nostarch.com/frameset.php?startat=hownotc](http://www.nostarch.com/frameset.php?startat=hownotc) ) which I found extremely fun to read ;). If you have some C/C++ skills already I truly recommend this, as an appetizer there's the "Broken Hello World Gallery": [http://www.nostarch.com/extras/hownotc/index.html](http://www.nostarch.com/extras/hownotc/index.html)

But I'm afraid I'm going slightly off topic here so i'll now just shut up ;)

---

### Post by phossal on 2007-01-27
> **jblebrun said:**
> Unfortunately, the driver problem is not due to a lack of competent, brilliant C programmers. The lack of drivers results from the hardware manufacturer's lack of willingness to provide the necessary information about the hardware in question. So, writing a driver requires a LOT more work, because you need to reverse engineer its operation, either by hacking through binary code in windows, or doing LOTS of testing. 

So if you REALLY want to contribute to the driver problem, learn how to probe into hardware to figure out how it works.

If you want to learn to program, play around with a few languages, and focus on the one that you have the most fun with. A language like C will allow you to learn more about how the machine works, a language like Python or Lisp will allow you to quickly learn more about algorithms and programming theory.

jblebrun, wybiral, et. al., 

One of the first threads I started (regretfully) was Learn. Sacrifice. Contribute, which had learning C for the purpose of writing device drivers as its suggestion on how to contribute a valuable service to the Ubuntu (and general Linux) community. 

It degenerated into a war over languages and how manufacturers are at fault for not providing drivers, among other things, and made me my first few enemies here at the forums. 

I still feel the same way: writing drivers for otherwise non-supported hardware that is readily and widely available at the big corporate computer retailers is an *awesome* way to give back to the community. At the same time, I think it's a very time-consuming, complicated process that produces a relatively short-lived gift.*

I enjoy this discussion though, and hope that the group of us who spend so much time in Programming Talk *talking*, will find a way to better direct (or redirect) the energy we spend debating memory management into something concrete and valuable for a larger portion of the community.

Cheers!


[SIZE="1"][COLOR="DimGray"]*This is precisely why I would define it as a *sacrifice*. It's a big personal investment, and it doesn't grant you immortality. But it could potentially improve the experience of the users of your time. People who can do such things are considered valuable for a reason, because most of us - even if we *could* to it - would choose not to.[/COLOR][/SIZE]

---

### Post by Tomosaur on 2007-01-27
If you want to help Ubuntu - the developers themselves request Python, since it is easier to integrate into Ubuntu.

IF, on the other hand, you want to help a particular open-source software, you'll just have to write in whatever language that software is written in. New features and bug-fixes are always welcome for submission, but don't expect them to appear - the code is always peer-reviewed, and most submissions never make it into the final release, unless they're pretty exceptional, and maintanable. Bug-fixes are more likely to be used, but many people will be working on those - so only the very best are ever picked.

You don't HAVE to program though - many projects are in dire need of documentation and/or artwork rather than more programmers. You should find a project you actually care about, and then lurk around that project's dev-pages and mailing lists to see what needs doing. As Phossal has said, device drivers are almost always welcomed, but they need to be good, secure, and efficient. Driver development is complex and time-consuming, so whether you want to take on the challenge is something you should think about it.

---

### Post by pmasiar on 2007-01-27
> **phossal said:**
> One of the first threads I started (regretfully) was Learn. Sacrifice. Contribute, (...)It degenerated into a war over languages and how manufactures are at fault for not providing linux drivers, among other things, and made me my first few enemies here at the forums.

Was it a jab at me? :-) Sorry if it was not, if it was aimed to someone else. :-)

Looks to me (and I might be wrong) like your perception of this forum is in terms of friend/enemies. I do not look at the forum like that - I never met anyone and not likely even will meet, I try to evaluate every post what it says; and if I disagree, I try to write up why I disagree, and what is truth (in my POV ). I do not see how friends/enemies will help me to understand better issues at hand.

I know preferences of some people in forum, but friend/enemies? My only enemy in this forum in misinformation (and again, misinformation as I see it, other people can have other preferences). IMHO, YMMV.

Sorry,  if I misunderstood you again, my apologies.

---

### Post by Tomosaur on 2007-01-27
Pmasiar, he never mentioned you, and you'd do best to stop interpreting everything he says as an attack on you. You're not helping.

---

### Post by lnostdal on 2007-01-27
> **phossal said:**
> One of the first threads I started (regretfully) was Learn. Sacrifice. Contribute, which had learning C for the purpose of writing device drivers as its suggestion on how to contribute a valuable service to the Ubuntu (and general Linux) community. 

It degenerated into a war over languages and how manufactures are at fault for not providing linux drivers, among other things, and made me my first few enemies here at the forums. 

I find it hard to understand how there can be any language-wars within the context of writing device drivers under Linux. Device drivers under Linux must be written in C (#1). I thought this was a pretty non-controversial view. From what I understand you can't even use C++ (#2) without bumping into a lot of issues and potential problems.


> **phossal said:**
> I still feel the same way: writing drivers for otherwise non-supported hardware that is readily and widely available at the big corporate computer retailers is an *awesome* way to give back to the community. At the same time, I think it's a very time-consuming, complicated, and relatively short-lived gift.

I tend to somewhat agree. Especially when they consistently keep info to themselves and at the same time keep pumping out incompatible cards/hardware without even providing closed-source Linux-drivers, or providing ones that suck and pretend they have provided real support which only makes things worse. It's not a very good situation in the long run for users nor developers.

I'm using an IBM ThinkPad and everything Just Works. The problem is most efficiently solved at the "other end" IMHO. Don't support the companies that do business in this way in the first place. There is excellent hardware with backing companies out there that makes sure Linux is properly supported in some way or another.

hm .. btw .. somewhat related to this; does Ubuntu have an HCL or something?


> **phossal said:**
> I enjoy this discussion though, and hope that the group of us who spend so much time in Programming Talk *talking*, will find a way to better direct (or redirect) the energy we spend debating memory management into something concrete and valuable for a larger portion of the community.

*alt-tabs back to Emacs & some hairy SWGtk-code*

#1: That is of course not to say that device drivers under all other OSs must be written in C (Movitz?) for any reason. Linux just (intentionally) lacks support for anything else than C in a context like this. In other words the only concerns that have been taken in the context of users writing device drivers under Linux is the issues that might pop up while doing this in C. I'd be interested in seeing any non-trivial examples showing this isn't true.

#2: I know about the project some students/uni created to somewhat allow this but it just isn't something I'd recommend doing anyway. There are enough things going on behind the scenes in both the kernel and in C++ to mess up things very badly.

---

### Post by phossal on 2007-01-27
> **pmasiar said:**
> Was it a jab at me?
No. I think writing device drivers is an interesting topic. I'd like to know of someone in the forums who did it. If possible, I'd like to work on reversing some current hardware. I just want to be around if/when someone begins to make forward progress. I'm not currently in a position to *lead* such a project though.

Firing shots across *your* bow was fun before I realized you were more of a troller (pun intended) than a warship. You're not a prize. Instead, I'm actually *concerned* for you. I don't hop from thread to thread planting seeds of mischief, or spend any time thinking of ways to harass you. You know from experience that, when I'm upset, I tell you openly.

---

### Post by phossal on 2007-01-27
> **lnostdal said:**
> I find it hard to understand...
I've read some of your previous posts. You seem *enthusiastic* and knowledgeable, if not always pragmatic. Your response to me appears a fairly lengthy analysis of the little blurb I wrote. If you disagree with anything I said, I simply retract it. 

I hope you have a happy, productive day. Cheers!

---

### Post by lnostdal on 2007-01-27
> **phossal said:**
> If you disagree with anything I said, I simply retract it. 

Nono, it was just a casual comment. :)

---

### Post by jblebrun on 2007-01-27
> **phossal said:**
> No. I think writing device drivers is an interesting topic. I'd like to know of someone in the forums who did it. If possible, I'd like to work on reversing some current hardware. I just want to be around if/when someone begins to make forward progress. I'm not currently in a position to *lead* such a project though.

Firing shots across *your* bow was fun before I realized you were more of a troller (pun intended) than a warship. You're not a prize. Instead, I'm actually *concerned* for you. I don't hop from thread to thread planting seeds of mischief, or spend any time thinking of ways to harass you. You know from experience that, when I'm upset, I tell you openly.

I wrote some WDM drivers once, does that count? :-D
I've got a book on writing Linux drivers... it looks a lot more straightforward than it is in windows!

---

### Post by phossal on 2007-01-27
> **jblebrun said:**
> I wrote some WDM drivers once, does that count? :-D
I've got a book on writing Linux drivers... it looks a lot more straightforward than it is in windows!

Yes, it counts! ;) Which book? "Writing device drivers in linux"?

---

### Post by jblebrun on 2007-01-27
> **phossal said:**
> Yes, it counts! ;) Which book? "Writing device drivers in linux"?

Yeah... the one by Rubini and Corbet... 2nd edition.

---

### Post by phossal on 2007-01-27
lol I love that book. I started reading it shortly after it (2nd edition) came out. That seems like *ages* ago. Back then, Red Hat was blowing up. Oh, memories!

[edit] I just looked it up at the Oreilly site. I'm exited about the new version, out in 2005. I might check it out next time I'm in the store.

---

### Post by jblebrun on 2007-01-27
It goes well with "Linux Kernel Development" by Robert Love. I found it to be an incredibly good introduction to the inner workings of the kernel. It's so good, that I actually found myself thinking "Gosh, the kernel must not have been very hard to write!"

---

### Post by amo-ej1 on 2007-01-29
hehe, well the 3rd edition is on my desk now ;-). 
But I must say I also enjoyed Robert Love's book. 

But one point still stand (IMHO), when you are programming in Linux there's a steep learning curve to get started. But once you've reached a certain level everything rather stays the same not depending on the direction you go, everything stays in the same lines following the same ideas.

In windows, the deeper you go the more **** you encounter ;-) (**** being difficulties, bad documentation, fewer examples, things that aren't simply NOT logical).

---

