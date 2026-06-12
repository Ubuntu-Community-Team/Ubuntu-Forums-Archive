---
title: "what programming language is Ubuntu written in?"
date: 2008-12-10
forum: Programming Talk
---

### Post by inxygnuu on 2008-12-10
what programming language is Ubuntu written in? I have searched google, but no answers appear.:(

---

### Post by fubbleskag on 2008-12-10
ubuntu itself is not a program, so the literal answer to your question is "none". linux programs are generally written in perl, python, c, c++, java, but can be written in other languages.

---

### Post by OutOfReach on 2008-12-10
Yeah, different components are written in different languages.
For example the Linux kernel is in C, GNOME and GTK is in C, the Ubuntu installer is written in Python and I think Update Manager is too.

So you would need to be more specific.

---

### Post by jacensolo on 2008-12-10
> **OutOfReach said:**
> the Ubuntu installer is written in Python and I think Update Manager is too.

So you would need to be more specific.

That explains the speed. Where can I find the osurce code for that? They should change it to C.

Note: I currently use and adore python. I just think that app is a little slow at times and may benefit from being compiled.

---

### Post by Darkhack on 2008-12-10
> **jacensolo said:**
> That explains the speed. Where can I find the osurce code for that? They should change it to C.

Update Manager is just a graphical front end.  All the heavy lifting is done with APT which is in C.  It's just that updating packages can take a bit of time and there isn't a lot you can do to get around it.

And as everyone else mentioned, an operating system isn't a single component.  It's a collection of software.  The kernel (which is Linux) is seen as the core of an OS.  It's written in C and most of the software on top is also C, but other parts of Ubuntu are written in other languages too.

---

### Post by mssever on 2008-12-10
> **jacensolo said:**
> That explains the speed. Where can I find the osurce code for that?```
apt-get source source-package-name
```Note: There's no need to use sudo with this command, and the source package name is sometimes different from the binary package (.deb) name, since sometimes a single source package is used to produce multiple binary packages. > They should change it to C.

Note: I currently use and adore python. I just think that app is a little slow at times and may benefit from being compiled.
It all depends on what the bottleneck is. I suspect (but I can't prove) that much of APT's slowness has to do with an inefficient database, which wouldn't be affected by switching to C. Plus, much of APT is already in C, after having been originally written in Perl.

---

### Post by thk on 2008-12-10
Visual Basic

---

### Post by tinny on 2008-12-11
> **fubbleskag said:**
> linux programs are generally written in perl, python, c, c++, java, but can be written in other languages.

Which programs are written in Java?

Dont forget Mono. (.Net port for Linux)

Banshee and F-Spot are written in C# on Mono

---

### Post by directhex on 2008-12-11
> **thk said:**
> Visual Basic

The only app written in VB.NET is the VB.NET compiler

---

### Post by Quikee on 2008-12-11
> **tinny said:**
> Which programs are written in Java?

Bootchart for example - but I don't know if this counts as a "Ubuntu" program. ;)

---

### Post by directhex on 2008-12-11
> **Quikee said:**
> Bootchart for example - but I don't know if this counts as a "Ubuntu" program. ;)

Nothing in the default install is written in Java - partly because Java is huge and there isn't room for it on the default media

Eclipse is the big example Java app people talk about though

---

### Post by Flimm on 2008-12-11
> **directhex said:**
> Nothing in the default install is written in Java - partly because Java is huge and there isn't room for it on the default media

Sun's Java has historically been closed source, and Ubuntu can't ship anything against the Ubuntu philosophy in the default installation.

---

### Post by pmasiar on 2008-12-11
> **jacensolo said:**
> That explains the speed. Where can I find the osurce code for that? They should change it to C.

Note: I currently use and adore python. I just think that app is a little slow at times and may benefit from being compiled.

This is common misunderstanding by clueless people: instead of measuring where the bottleneck is, guess (and do it without any understanding or relevant education on the issue). Results of such approach are adequate: garbage in, garbage out.

Everybody has a right for opinion, but not all opinion are worth the same: opinions are evaluated, not counted. 

Is better to remain silent and let other think you may not know much, than open your mouth and remove any doubt. ;-)

Unless, of course, such "opinion" is just disguised question, and opportunity to learn.

---

### Post by inxygnuu on 2008-12-11
thanks! I love the answers! That is because i am going to try to create my own OS soon, and i am going to start with one that is based off of Ubuntu, then move on to my own Linux distro, and If I am lucky enough, make my own kernel.:) so my main questions would now be: What is the best language to write a program in (I already know some C++), What is the main programming language found in Ubuntu at installation, and what would you most like to see an OS have in it? Thanks for the help, and answers would be greatly appreciated.

Regards,
3v4n

---

### Post by tinny on 2008-12-11
> **inxygnuu said:**
> thanks! I love the answers! That is because i am going to try to create my own OS soon, and i am going to start with one that is based off of Ubuntu, then move on to my own Linux distro, and If I am lucky enough, make my own kernel.:) so my main questions would now be: What is the best language to write a program in (I already know some C++), What is the main programming language found in Ubuntu at installation, and what would you most like to see an OS have in it? Thanks for the help, and answers would be greatly appreciated.

Regards,
3v4n

Wow! A very ambitious goal. 

Perhaps you should try this first.

[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

---

### Post by jespdj on 2008-12-11
I don't want to discourage you, but writing your own OS is a huge undertaking. For example, thousands of people have worked on the Linux kernel the past 15 years or so to get it where it is now. Even creating your own Linux distro is an enormous job that's not easy to do on your own. You'll have to be an expert in computers and Linux to do this.

If you really want to develop your own kernel, then C and assembly language are pretty much required.

---

### Post by mssever on 2008-12-11
> **tinny said:**
> Wow! A very ambitious goal. 

Perhaps you should try this first.

[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)
+1 to the Linux From Scratch suggestion.

@OP:
No offense, but the fact that you have to ask this question shows that you don't have nearly enough knowledge or experience to produce your own distro--let alone a kernel. If you learn how to make Debian packages, you can produce an Ubuntu derivative fairly easily provided you stay pretty close to Ubuntu. But if you have any awesome ideas on how to change Ubuntu, you'll probably need a lot more programming experience before you'll be able to make them a reality.

---

### Post by tinny on 2008-12-11
> **mssever said:**
> +1 to the Linux From Scratch suggestion.

@OP:
No offense, but the fact that you have to ask this question shows that you don't have nearly enough knowledge or experience to produce your own distro--let alone a kernel. If you learn how to make Debian packages, you can produce an Ubuntu derivative fairly easily provided you stay pretty close to Ubuntu. But if you have any awesome ideas on how to change Ubuntu, you'll probably need a lot more programming experience before you'll be able to make them a reality.

I didnt want to put it that bluntly :-)

---

### Post by fubbleskag on 2008-12-11
sorry, it was misleading of me to include java in that list. java is a supported language within any linux distribution, but I was mixing up two different thoughts in one sentence.

---

### Post by inxygnuu on 2008-12-11
(I expected this...) Ok, i know i sound naive, but give me a break. I am almost 13. I know what i am saying is a little beyond me, but I don't plan to make any sort of kernel for a while. I am still learning how to program. I get it when you guys criticize me, but I get the point that I am of little knowledge to be doing anything huge. That is why i have Ubuntu. Accidentally erasing my Copy of Windows Vista was one of the best things I have ever done. When i am, asking questions, i greatly appreciate that you answer, but these questions are simply to improve my understanding of computers. come to think of it, I just got the interest of computers this last summer, when I decided to speed up my old 1998 computer with  windows XP. So I understand that i am shooting too big for my experience level, but just realize that these are pieces to the puzzle.

Regards,
3v4n

---

### Post by slavik on 2008-12-11
better to try and fail than to never have tried. :)

Linus was very young when he first released the Linux kernel (version 0.01), he was 22 at the time (1991).

---

### Post by Delever on 2008-12-12
I remember myself trying to write my own versions of huge programs, like Word, AutoCAD. It's nice exercise and rewarding just to see the scope of things involved, even with no real result.

Advice from me: focus.

Good luck :)

---

### Post by Poyntz on 2008-12-12
> **fubbleskag said:**
> ubuntu itself is not a program

I would beg to differ. According to dictionary.com the definition of program for computers is:
> a.a systematic plan for the automatic solution of a problem by a computer.
b. the precise sequence of instructions enabling a computer to solve a problem.

according to these definitions is an OS not a program? An automatic solution to a problem - I need something done, I go to my comp (it fits). and coding or programming is a sequence of instructions, by which the operating system is formulated. Infact it draws a liason between multiple programs, thus making it a system of programs if not a super program.

---

### Post by Delever on 2008-12-12
> **Poyntz said:**
> I would beg to differ. According to dictionary.com the definition of program for computers is:


according to these definitions is an OS not a program? An automatic solution to a problem - I need something done, I go to my comp (it fits). and coding or programming is a sequence of instructions, by which the operating system is formulated. Infact it draws a liason between multiple programs, thus making it a system of programs if not a super program.

I would call group of programs software, that's what I prefer.

---

### Post by directhex on 2008-12-12
> **slavik said:**
> better to try and fail than to never have tried. :)

Linus was very young when he first released the Linux kernel (version 0.01), he was 22 at the time (1991).

The Linux kernel built up around a Minix userland, though. GNU grew up as a set of superior replacement UNIX tools, lacking only a kernel. What inxygnuu needs to do is the same thing - pick ONE thing, and try to reimplement its functionality.

The other thing to realise is that whilst aiming for the stars is good in that it allows you to reach the moon, be aware of the challenges involved. Start off with some programming (e.g. reimplement a tool of some kind in a different language, with extra features), take a look at package systems (and try making an rpm and a deb), even work on a "toy" kernel (many undergrad degrees these days include this as coursework). But realistically, there are myriad factors against you producing something which *other people* will want to use - e.g. how are you gonna write drivers for a graphics card you don't own?

I can only think of one successful 1-man OS, and I use the term "successful" loosely - [http://www.skyos.org/](http://www.skyos.org/). Linux doesn't really count, considering the GNU and Minix bases it had behind it, and the rapid influx of third party developers tinkering with the kernel

---

### Post by pmasiar on 2008-12-12
FYI for OP: Estimated cost of development of the software included in average a Linux distro (Fedora) is currently about [10.8 Billion USD](http://www.linuxfoundation.org/publications/estimatinglinux.php), which increased from 1.2B USD in 2002. With this rate of growth, in 9 years when you will be Linus' age, if will be worth more than 100B USD. 

So you better start quickly and get some good productivity tools (may I suggest Visual Studio? :twisted: ) or else you will be left behind ;-) ... and don't forget to recruit at least 2-3 of your equally smart friends ;-)

---

### Post by inxygnuu on 2008-12-12
> **pmasiar said:**
> FYI for OP: Estimated cost of development of the software included in average a Linux distro (Fedora) is currently about [10.8 Billion USD](http://www.linuxfoundation.org/publications/estimatinglinux.php), which increased from 1.2B USD in 2002. With this rate of growth, in 9 years when you will be Linus' age, if will be worth more than 100B USD. 

So you better start quickly and get some good productivity tools (may I suggest Visual Studio? :twisted: ) or else you will be left behind ;-) ... and don't forget to recruit at least 2-3 of your equally smart friends ;-)

I like the idea and yes, I need to get started soon and that is why I am asking these questions. Only one problem though... AFAIK, I am the only person in the school who uses Linux to begin with. Or even knows what Linux is... Not to mention computers...

Thanks for all of the support,
3v4n

---

### Post by Seq on 2008-12-12
I'll second the idea to start with smaller, targeted projects.

Think about what you would like your computer to do, break it down into sections, and figure out how you could test if part A works before you start on part B.

My brother started programming as an means to robotics. If you have a serial port, you could look at creating and controlling your own device. Go to a hobby shop and pick up a few small (cheap) motors and other interesting equipment. This will cost a bit up front (Plan out what you need first) but will be quite rewarding.

Good luck, and don't be afraid to ask for help if you have questions.

---

### Post by nvteighen on 2008-12-12
There's another issue... please, don't feel offended: but you're still too young. You'll have to madure a bit more intellectually before acomplishing such a project. This is not reserved to computer programming, but to anything: at the age of 13 you should try to set solid bases and, basically, learn (unless you're a prodigy, but then you wouldn't be posting here, right? ;)). Such big projects is far away from a normal 13-years old's brain state of intellectual development.

Some will say, hey! do it even if you know you'll fail because you'll anyway learn something. Yes, you may learn something if you're clever enough to get at least a bit... but you may be now learning other things that will help you in the future.

And never stop to ask questions!

---

### Post by inxygnuu on 2008-12-12
> **nvteighen said:**
> There's another issue... please, don't feel offended: but you're still too young. You'll have to madure a bit more intellectually before acomplishing such a project. This is not reserved to computer programming, but to anything: at the age of 13 you should try to set solid bases and, basically, learn (unless you're a prodigy, but then you wouldn't be posting here, right? ;)). Such big projects is far away from a normal 13-years old's brain state of intellectual development.
Some will say, hey! do it even if you know you'll fail because you'll anyway learn something. Yes, you may learn something if you're clever enough to get at least a bit... but you may be now learning other things that will help you in the future.

And never stop to ask questions!Bumpity bump for the heck of it...

Thanks, but I like to push myself, i mean I am smart (I am in advanced math, and everyone in the school calls me Albert Einstein) but i always will push myself beyond my limits when doing things like this. I even read a college math book once and could almost understand it. I know i should start small, I simply want to ask questions for big things, because answers to those questions will answer smaller ones. I know I am not a prodigy (even though my teacher says so), but these questions can get me the answers to a lot of things. Just the linux kernel made me realize how understanable, yet complicated computers can be.

Thanks,
3v4n

---

### Post by slavik on 2008-12-12
> **directhex said:**
> The Linux kernel built up around a Minix userland, though. GNU grew up as a set of superior replacement UNIX tools, lacking only a kernel. What inxygnuu needs to do is the same thing - pick ONE thing, and try to reimplement its functionality.

The other thing to realise is that whilst aiming for the stars is good in that it allows you to reach the moon, be aware of the challenges involved. Start off with some programming (e.g. reimplement a tool of some kind in a different language, with extra features), take a look at package systems (and try making an rpm and a deb), even work on a "toy" kernel (many undergrad degrees these days include this as coursework). But realistically, there are myriad factors against you producing something which *other people* will want to use - e.g. how are you gonna write drivers for a graphics card you don't own?

I can only think of one successful 1-man OS, and I use the term "successful" loosely - [http://www.skyos.org/](http://www.skyos.org/). Linux doesn't really count, considering the GNU and Minix bases it had behind it, and the rapid influx of third party developers tinkering with the kernel
Sorry, but at the time, there was Minix and GNU. They were separate. GNU had Hurd. Then Linus released Linux (no code borrowed from any other OS) and eventually people put GNU on top of it.

---

### Post by Darkhack on 2008-12-12
> **nvteighen said:**
> There's another issue... please, don't feel offended: but you're still too young. You'll have to madure a bit more intellectually before acomplishing such a project. This is not reserved to computer programming, but to anything: at the age of 13 you should try to set solid bases and, basically, learn (unless you're a prodigy, but then you wouldn't be posting here, right? ;))

I disagree.  Age has little to do with it.  There's no reason he couldn't write a kernel at his age.  The thing is that he shouldn't compare it to Linux or some other big project.  I was able to write a simple 'hello world' kernel with a VGA driver.

Personally, I think people under estimate kids.  And not to a minor degree either.  I see people who treat teenagers like they're helpless and empty minded and I find it rather insulting.  I see no reason that someone his age couldn't do most of what an adult does if they are able to read and write.  They might lack long term experience in an area, but they can learn equally as well as an adult.

---

### Post by inxygnuu on 2008-12-12
> **Darkhack said:**
> I disagree.  Age has little to do with it.  There's no reason he couldn't write a kernel at his age.  The thing is that he shouldn't compare it to Linux or some other big project.  I was able to write a simple 'hello world' kernel with a VGA driver.

Personally, I think people under estimate kids.  And not to a minor degree either.  I see people who treat teenagers like they're helpless and empty minded and I find it rather insulting.  I see no reason that someone his age couldn't do most of what an adult does if they are able to read and write.  They might lack long term experience in an area, but they can learn equally as well as an adult.

Thank You! i just need to know how to write one. as i have said, i have been into computers for about 6 months now. and stuff like this for less than a month. (any compliments would be appreciated;)) Just give me the resources and the time, and i might be able to do it!

Thanks,
3v4n

---

### Post by pmasiar on 2008-12-12
> **Darkhack said:**
> I disagree.  Age has little to do with it.  There's no reason he couldn't write a kernel at his age. 

It is not about age but about knowledge.

It takes years of study to get to the level to be able to hack kernel - especially now, when kernel is huge and complicated.

As they say, 10 years of experience means nothing only to someone lacking 10 years of experience.

Good luck with OP's efforts, but if he needs to sleep, it will take years to get there. There are few shortcuts, if any. Pretending it is otherwise will be misleading - regardless of how many times you youngsters thank each other.

[Teach Yourself Programming in Ten Years](http://norvig.com/21-days.html)

---

### Post by NathanB on 2008-12-13
**inxygnuu** - Start your journey at these links:

[http://wiki.osdev.org/Main_Page](http://wiki.osdev.org/Main_Page)
[http://www.azillionmonkeys.com/qed/os.html](http://www.azillionmonkeys.com/qed/os.html)

If coding your own OS wasn't so enjoyable, so educational, so profitable, etc., then there wouldn't be SO MANY people doing it!  The current count is somewhere in the hundreds of thousands for the number of operating systems available for the standard PC.  That means you will have plenty of source code and people to learn from.

When you finish your small OS, if you decide you'd like that for a career, jump into one of the bigger projects.  For instance, Microsoft has been known to recruit from here:

[http://www.reactos.org/en/index.html](http://www.reactos.org/en/index.html)

Enjoy the journey!

---

### Post by nvteighen on 2008-12-13
> **inxygnuu said:**
> 
Thanks, but I like to push myself, i mean I am smart (I am in advanced math, and everyone in the school calls me Albert Einstein) but i always will push myself beyond my limits when doing things like this. I even read a college math book once and could almost understand it. I know i should start small, I simply want to ask questions for big things, because answers to those questions will answer smaller ones. I know I am not a prodigy (even though my teacher says so), but these questions can get me the answers to a lot of things. Just the linux kernel made me realize how understanable, yet complicated computers can be.


Well, one thing is to learn about how an OS works internally and another very different one is to write it.

If you are smart, you have to push yourself out of your limits, otherwise your smartness will just stay as that and you'll never be wise. Smartness is an ability (a talent), not knowledge or expertise, wisedom, whatever you like to call it. But the problem is that at your age, the limits are far more nearer than you think, mostly because you haven't got enough experience (data) to improve the way you analyze stuff. What you now have to do, IMO, is to get that experience, not jumping steps. Without a fairly ordered method, you'll learn stuff but you won't be able to relate themselves.

At school I was at a similar situation like yours. At 14 I already could understand Calculus. Alhough my math teacher was very proud of it, he obliged me to review the most simple algebra, it was only after that that I could not only read, but also *do* Calculus and relate it to problems, trigonometry, etc. The same occured to me now at University: I could understand Linguistic stuff at a fairly early age (I even read Saussure...), but it's only now, being 20 and having being taught a lot of stuff, that I'm starting to analyze and write some midly interesting ideas (wrong or right, I don't know... but at least I feel I'm getting ideas).


Don't think I'm trying to underestimate you. I don't even know you, but, honestly, I'm fairly skeptical with your case... I hope to be proven wrong ;)

> **Darkhack said:**
> 
Personally, I think people under estimate kids.  And not to a minor degree either.  I see people who treat teenagers like they're helpless and empty minded and I find it rather insulting.  I see no reason that someone his age couldn't do most of what an adult does if they are able to read and write.  They might lack long term experience in an area, but they can learn equally as well as an adult.

I agree people underestimate them, but usually they overestimate themselves... Probably, all of us at that age thought we were wiser than we actually were... Note that I say "wiser", not "smarter"; as I said above, the ability is there and you know whether you have it or not. The issue is that learning is not only based on what previous knowledge you have, but also if you can actually relate that old knowledge with the new you learn. It's in this last step where usually younger people fail, mostly because of the natural impatience you have at that age... you don't sit down and meditate, you just want to do stuff and quickly (this thread seems to show what I mean).

Of course, that a 13 years old boy starts looking at intellectual challenges is not bad... it's actually satisfying, but the point is how. I'm a supporter of inductive learning (learning by doing), but to do correctly, you start doing the most basic stuff. It's important that you learn doing real stuff and not just simplified "exercises", but with some reasonable scalation from easiest to hardest.

I apologize if I'm being a bit hard or even offensive, but it's what I really think about this.

---

### Post by inxygnuu on 2008-12-13
> **nvteighen said:**
> Well, one thing is to learn about how an OS works internally and another very different one is to write it.

If you are smart, you have to push yourself out of your limits, otherwise your smartness will just stay as that and you'll never be wise. Smartness is an ability (a talent), not knowledge or expertise, wisedom, whatever you like to call it. But the problem is that at your age, the limits are far more nearer than you think, mostly because you haven't got enough experience (data) to improve the way you analyze stuff. What you now have to do, IMO, is to get that experience, not jumping steps. Without a fairly ordered method, you'll learn stuff but you won't be able to relate themselves.

At school I was at a similar situation like yours. At 14 I already could understand Calculus. Alhough my math teacher was very proud of it, he obliged me to review the most simple algebra, it was only after that that I could not only read, but also *do* Calculus and relate it to problems, trigonometry, etc. The same occured to me now at University: I could understand Linguistic stuff at a fairly early age (I even read Saussure...), but it's only now, being 20 and having being taught a lot of stuff, that I'm starting to analyze and write some midly interesting ideas (wrong or right, I don't know... but at least I feel I'm getting ideas).


Don't think I'm trying to underestimate you. I don't even know you, but, honestly, I'm fairly skeptical with your case... I hope to be proven wrong ;)



I agree people underestimate them, but usually they overestimate themselves... Probably, all of us at that age thought we were wiser than we actually were... Note that I say "wiser", not "smarter"; as I said above, the ability is there and you know whether you have it or not. The issue is that learning is not only based on what previous knowledge you have, but also if you can actually relate that old knowledge with the new you learn. It's in this last step where usually younger people fail, mostly because of the natural impatience you have at that age... you don't sit down and meditate, you just want to do stuff and quickly (this thread seems to show what I mean).

Of course, that a 13 years old boy starts looking at intellectual challenges is not bad... it's actually satisfying, but the point is how. I'm a supporter of inductive learning (learning by doing), but to do correctly, you start doing the most basic stuff. It's important that you learn doing real stuff and not just simplified "exercises", but with some reasonable scalation from easiest to hardest.

I apologize if I'm being a bit hard or even offensive, but it's what I really think about this.

No, it is not offensive, I actually enjoy listening what you guys have to say about my abilities and so-forth and i am not sure weather I just think I can do this, or if i can, but I seem to only learn what is taught to ,e on a limited subject. but on  subjects like pronouncing big numbers, it is different. I remember that in 3rd grade, nobody in my "advanced math" class could understand how to pronounce big words, and then my teacher said "100,023" and instantly, everybody. Then, I simply manipulated how to say that and i could now pronounce words as big as I wanted if i knew the place values. What i would need to do some of these things now like a kernel, would be to learn how to access hardware in it. for example, I know there is some special codes for each piece, I just need to know what those codes are.

---

### Post by CptPicard on 2008-12-13
I am generally in agreement with nvteighen here, although a really good 13-year-old is probably able to hack together something simple and kernel-ish. But to even get basic task-switching going takes some effort and understanding :)

Then there is the question of whether this exercise is worth it in general. Bare-metal stuff is overrated, and a 13-year-old is going to be served better in the long run by learning Lisp than learning assembly :)

---

### Post by lukjad on 2009-07-27
> **thk said:**
> Visual Basic

LOL. I can't help laughing.

---

### Post by Mirge on 2009-07-27
Jordy, thread necromancing _is_ happening more often recently...

---

### Post by JordyD on 2009-07-27
> **Mirge said:**
> Jordy, thread necromancing _is_ happening more often recently...

I had thought so.

I didn't even know lukjad007 hung around Programming Talk. I've never seen him post here.

---

