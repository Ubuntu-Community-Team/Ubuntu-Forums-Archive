---
title: "Best C/C++ Environment"
date: 2008-09-04
forum: Recurring Discussions
---

### Post by Sly-.- on 2008-09-04
Hey guys. I started learning C on Windows a few weeks ago. I've turned back to Linux once again, just love it. I'm wondering, whats the best C/C++ editors, compilers or IDE's I should use?

Also, my Ubuntu is out of the box so to speak, can anyone guide me to what packages I have to install and how to do so?

Cheers.

---

### Post by LaRoza on 2008-09-04
See this link for IDE's and editors: [http://ubuntuforums.org/showthread.php?t=752224](http://ubuntuforums.org/showthread.php?t=752224)

See this one for compiling: [http://ubuntuforums.org/showthread.php?t=689635](http://ubuntuforums.org/showthread.php?t=689635)

---

### Post by scragar on 2008-09-04
if your learning C or C++ I think it's fairly essential to install the build essentials package since it contains compilers and libraries for the most common requirements:
```
sudo apt-get install build-essential
```from a terminal, or just install the build-essential package from synaptic(System>Administration>Synaptic Package Manager)

gcc/g++ is generaly considered to be the best linux C/C++ compilers.

I've no idea for what IDE to use.



EDIT: To clarify, what I mean by best, was that it's by far the most likely to exist on any random linux system you were to pick.

---

### Post by Sly-.- on 2008-09-04
Thank you ver much, I've just installed that and will use the gcc/g++ compiler. I've heard good things about kate before, anyone got any editor preferences they would recommend?

---

### Post by LaRoza on 2008-09-04
> **Sly-.- said:**
> Thank you ver much, I've just installed that and will use the gcc/g++ compiler. I've heard good things about kate before, anyone got any editor preferences they would recommend?

yes, people will recommend what they use. We all use different things for personal reasons. Asking would just invite a bunch of "I use $EDITOR" responses which is less useful than the list in the wiki.

If you use Ubuntu, Gedit is the default text editor and its plugs (including terminal plug in) are very handy and suitable for programming without anything else needed.

---

### Post by Sly-.- on 2008-09-04
Yeah, I got you mate. Cheers anyway.

---

### Post by slavik on 2008-09-04
my recommended tools:
Geany (it's like gedit with buttons for compiling)
Anjuta (THE one and only IDE for GNOME/Linux apps)

There are also:
Kate (similar to gedit, now that gedit has a built in terminal)
KDevelop (great for QT(KDE) apps)
Eclipse with the C/C++ plugins
Komodo Edit
vim, emacs, etc.

---

### Post by Tyke91 on 2008-09-04
Eclipse is an amazing IDE, a little bit resource heavy, but feature rich. It can do java, C, C++ and more.

when I started learning C++ earlier this year, I used eclipse... But at the end, I didn't like the bulk. I've learned vi now and love it, but this is inviting a large debate and I don't want to evangelize.

I'd recommend Eclipse or Ajunta to start, and to also do some research into vi and emacs if you're interested in going the text editor/command line route.

---

### Post by mujambee on 2008-09-05
If you are learning C, don't use any IDE. Do every thing by hand, write your own makefiles and build and launch from the command line. :(

Now, that's crazy!!

As I see things, that's the way to really learn how a C program is built.  When you are used to that, and are proficient enough with your makefiles, then it's time to switch to an IDE and get the dirty work done for free. ;)

---

### Post by nvteighen on 2008-09-05
The best environment: a decent text-editor (Gedit is a great one... use the plugins) + a terminal where you call the compiler or make.

---

### Post by philip123 on 2008-09-05
C++ ("C Plus Plus", pronounced /&#716;si&#720;&#716;pl&#652;s&#712;pl&#652;s/) is a general-purpose programming language. C++ is regarded as a middle-level language, as it comprises a combination of both high-level and low-level language features.[1] It is a statically typed, free-form, multi-paradigm, compiled language where compilation creates machine code for the target machine hardware, supports procedural programming, data abstraction, object-oriented programming, and generic programming. [http://www.infysolutions.com](http://www.infysolutions.com)



[web application development]("http://www.infysolutions.com")

---

### Post by gnusci on 2008-09-05
> **philip123 said:**
> C++ ("C Plus Plus", pronounced /&#716;si&#720;&#716;pl&#652;s&#712;pl&#652;s/) is a general-purpose programming language. C++ is regarded as a middle-level language, as it comprises a combination of both high-level and low-level language features.[1] It is a statically typed, free-form, multi-paradigm, compiled language where compilation creates machine code for the target machine hardware, supports procedural programming, data abstraction, object-oriented programming, and generic programming. [http://www.infysolutions.com](http://www.infysolutions.com)



[web application development]("http://www.infysolutions.com")

WTH Spam???...

---

### Post by cb951303 on 2008-09-05
Here is the thing. If you don't care about code completion, code formatting, easy debugging and other major IDE capabilities use a simple text editor with syntax highlighting such as Gedit or Geany + Gnu Make (or maybe cmake which is easier). But if you feel like you are overwhelmed with things other then writing the actual code, go the IDE way. 

I currently use Eclipse and it's one good piece of software. I also tried the latest netbeans beta and it's faster then eclipse. it also have a more intuitive interface and easier plugin management but the fonts look like sh*t because of java. For now it's only usable on a windows machine for me.
You may also like anjuta. it's a very mature project. but it's not cross platform. if you come&go between linux and windows it's better you start with a cross platform ide...

cheers

---

### Post by Mickeysofine1972 on 2008-09-05
I recommend Code::Blocks as a good IDE although I do agree that if you want to learn first dont use a IDE use a text editor then switch later

Mike

---

### Post by scourge on 2008-09-05
I'd vote for KDevelop, even for GTK/wxWidgets projects. Unlike simple text editors like Gedit, it can manage whole projects, automatically finds function definitions, has a project-wide search & replace (with regexp too), good debugging features, support for Doxygen, CVS, SVN, etc. Best of all, it's easy to use.

---

### Post by cb951303 on 2008-09-05
> **mujambee said:**
> If you are learning C, don't use any IDE. Do every thing by hand, write your own makefiles and build and launch from the command line. :(

Now, that's crazy!!

As I see things, that's the way to really learn how a C program is built.  When you are used to that, and are proficient enough with your makefiles, then it's time to switch to an IDE and get the dirty work done for free. ;)

is it really that important to know howto write a makefile by hand?
I don't think so. for the learning curve of a programming language, knowing howto hand-write a makefile doesn't have any advantages. in fact I would recommend the managed project way (IDE way) for a beginner. Just because it's less confusing and it won't make him/her learn slower.

---

### Post by gnusci on 2008-09-05
> **mujambee said:**
> If you are learning C, don't use any IDE. Do every thing by hand, write your own makefiles and build and launch from the command line. :(

Now, that's crazy!!

As I see things, that's the way to really learn how a C program is built.  When you are used to that, and are proficient enough with your makefiles, then it's time to switch to an IDE and get the dirty work done for free. ;)

I agree with you... Write everything from scratch for introductory programs, using a simple editor such as vim or mcedit thats enough, then use directly gcc or makefile. You will learn a lot, and will make a lot easer to understand all the IDE's out there.

---

### Post by nvteighen on 2008-09-05
> **cb951303 said:**
> is it really that important to know howto write a makefile by hand?
I don't think so. for the learning curve of a programming language, knowing howto hand-write a makefile doesn't have any advantages. in fact I would recommend the managed project way (IDE way) for a beginner. Just because it's less confusing and it won't make him/her learn slower.
No way: it seems that IDEs don't get makefiles right or, at least, it's not trivial to get them right... given the amount of threads concerning linking and using an IDE.

<joke>Make is actually easy to learn, so don't be lazy! :p</joke>
<serious>IMO, you have to know how to learn them. I mean, if you don't know how to write Makefiles, you'll be ever depending on the IDE's features (i.e. you are "enslaved" to a piece of machine code); you'll have no freedom over your code. Maybe you don't have to write Makefiles always by hand, but know how to do it in case you need it.</serious>

EDIT: By the way, usually beginners' projects are single files, so they don't need any project manager or Makefile to be compiled...

---

### Post by ilrudie on 2008-09-05
> **cb951303 said:**
> is it really that important to know howto write a makefile by hand?
I don't think so. for the learning curve of a programming language, knowing howto hand-write a makefile doesn't have any advantages. in fact I would recommend the managed project way (IDE way) for a beginner. Just because it's less confusing and it won't make him/her learn slower.

I personally would say learn how to write c from scratch.  Learn how to use make.  Learn how to use gcc from the command line.  Learn vi.  Learn valgrind and checkstyle.  Learn to debug from the command line.  That way if you end up having to write/compile code on a system without your IDE you aren't helpless.  Nothing worse than a developer whining that they can't work without their gui.

If you just want to play around with a language and don't plan on doing anything serious with the knowledge or making a living programming then forget about my previous paragraph.

---

### Post by StOoZ on 2008-09-05
> **Mickeysofine1972 said:**
> I recommend Code::Blocks as a good IDE although I do agree that if you want to learn first dont use a IDE use a text editor then switch later

Mike

I recently moved from netbeans to C::B , since netbeans was slow as hell , and was pretty "hard" to configure for wxwidgets usage under windows (read many tutorials...).
but I found several issues with C::B , the most significant is that the code completion is very bad , it doesn't recognize stl stuff (typing std::    doesn't bring up anything..) , when I type :
foo. or foo->    while foo is my own class , its fine , when it comes to other libs , even C++ ones (stl..for e.g) nothing is being displayed. :(

---

### Post by cb951303 on 2008-09-05
> **nvteighen said:**
> No way: it seems that IDEs don't get makefiles right or, at least, it's not trivial to get them right... given the amount of threads concerning linking and using an IDE.

hmm actually it's not right at all. IDEs are not limited to gnu make. Visual studio and eclipse uses their own build system and it didn't failed me once. Also ANJUTA which is gnu make dependent seems to work pretty well too.

> 
<joke>Make is actually easy to learn, so don't be lazy! :p</joke>

according to who? make files can be very tricky as the project grows.

> 
...you'll have no freedom over your code...

please explain how writing make files by hand does that.

cheers

---

### Post by cb951303 on 2008-09-05
> **ilrudie said:**
> I personally would say learn how to write c from scratch.  Learn how to use make.  Learn how to use gcc from the command line.  Learn vi.  Learn valgrind and checkstyle.  Learn to debug from the command line.  That way if you end up having to write/compile code on a system without your IDE you aren't helpless.  Nothing worse than a developer whining that they can't work without their gui.

now imagine you don't know the first thing about programming and you have to do all that manually...

for a beginner, things should be easier. after gaining some experience everyone can learn *more easily* what you have stated above

---

### Post by ilrudie on 2008-09-05
> **cb951303 said:**
> now imagine you don't know the first thing about programming and you have to do all that manually...

for a beginner, things should be easier. after gaining some experience everyone can learn *more easily* what you have stated above

The OP did not say he has no programming experience.  He just said he is trying to learn c.  c (IMO) is not a good choice for a first language.  If this is the OP's first language and he is not taking a class (where he will get instruction in c) I would personally recommend he learn a different language first.  

That said if you are serious about learning c an IDE is a bad place to start.  A text editor (nano, gedit, vi*, emacs*) and a terminal are the best place to start.  Most IDE's are clogged up with buttons and functionality that beginners don't need anyway and take away valuable experience like writing makefiles for small projects and compiling from the command line.  An IDE is really the last thing you should learn.  Some IDE's (like Squeak's) are designed for learning and thats a different story but the majority are  high level tools for managing large projects and lots of code.

*if you already know vi or emacs great, use it.  If you don't already know one use a simple text editor because both vi and emacs will just add to your frustration.

---

### Post by nvteighen on 2008-09-05
> **cb951303 said:**
> hmm actually it's not right at all. IDEs are not limited to gnu make. Visual studio and eclipse uses their own build system and it didn't failed me once. Also ANJUTA which is gnu make dependent seems to work pretty well too.

Well, I was talking from the impression I have that people here asking for compilation errors through an IDE is rather common. 


> according to who? make files can be very tricky as the project grows.
According to me :) I meant about the make scripting language itself; it's rather easy to learn. Of course, as something grows up in complexity, be it a Makefile, a Python project or a recipe you're trying to prepare will 
be trickier. But the make language is very simple.

> please explain how writing make files by hand does that.
Writing anything by hand gives more control over your code. That's obvious: you don't have a program "interpreting" what you want to do things... any decision you take is going to be taken by the program and the quality of the result will depend on the quality of the IDE. But, I don't mean you need whole control always... and possibly never, that's why IDEs exist.

What I mean is that you should know what's a Makefile and how to write them, just in case the IDE doesn't get what you want to do. And keep in mind a bug in an IDE can appear anytime, so you better be prepared when that happens so you aren't tight up to what that program can or can't do. Also, what happens if for some reason you have to work in an environment (a job, for example) where your favorite IDE is not there?

Hope I've cleared my point out.

---

### Post by cb951303 on 2008-09-05
> **ilrudie said:**
> The OP did not say he has no programming experience.  He just said he is trying to learn c.  c (IMO) is not a good choice for a first language.  If this is the OP's first language and he is not taking a class (where he will get instruction in c) I would personally recommend he learn a different language first.  I think its safe to assume that OP is a beginner. that being said I agree that C is not a good "first" programming language nowadays, however it was once, before interpreted languages came to the scene. That's a different topic though...

> 
That said if you are serious about learning c an IDE is a bad place to start.  A text editor (nano, gedit, vi*, emacs*) and a terminal are the best place to start. Most IDE's are clogged up with buttons and functionality that beginners don't need anyway and take away valuable experience like writing makefiles for small projects and compiling from the command line. An IDE is really the last thing you should learn.
 I don't know where you get that idea. An IDE's first and almost only aim is to make things easier for the developer. I also don't agree with your idea of ides' complex user interfaces because I know *alot* of people started learning c/c++ with dev-c++ just because it was so easy to use. What you qualify as "valuable experience" is easily obatained once you actually get into the programming and start understanding things. There is absolutely no rule saying that we should learn handwriting makefiles and using command line compilers from the beginning. It simply doesn't have any advantage over learning it later (once you actually understand what programming is about)

---

### Post by mujambee on 2008-09-05
> **cb951303 said:**
> is it really that important to know howto write a makefile by hand?

Yes, it is, and I speak out of experience.

At work we have to develop C and C++ servers, running on different Ux flavours.  We have only telnet/FTP access, so no IDE for us.  Many programmers don't have a clue on how to edit a makefile, and most of them resort to copy and paste, carrying with them all switches and dependencies blindly.  Only a handful of people know really how to go on that, and most of us are their team managers, who learned it the hard way (and should be doing something else, not cleaning up their mess).

---

### Post by cb951303 on 2008-09-05
> **mujambee said:**
> Yes, it is, and I speak out of experience.

At work we have to develop C and C++ servers, running on different Ux flavours.  We have only telnet/FTP access, so no IDE for us.  Many programmers don't have a clue on how to edit a makefile, and most of them resort to copy and paste, carrying with them all switches and dependencies blindly.  Only a handful of people know really how to go on that, and most of us are their team managers, who learned it the hard way.

that was meant for beginners. That's the point. You don't have to learn writing makefiles form the beginning. Learn it after you gain some experience in programming.

---

### Post by SACHINVD on 2008-09-05
U can use Anjuta by Naba Kumar as C/C++ IDE

---

### Post by mujambee on 2008-09-05
> **cb951303 said:**
> that was meant for beginners. That's the point. You don't have to learn writing makefiles form the beginning. Learn it after you gain some experience in programming.

Once you start doing things the easy way there is no coming back, you'll never learn the hard way unless hardly pressed. ;)

---

### Post by cb951303 on 2008-09-05
> **nvteighen said:**
> Well, I was talking from the impression I have that people here asking for compilation errors through an IDE is rather common. 



According to me :) I meant about the make scripting language itself; it's rather easy to learn. Of course, as something grows up in complexity, be it a Makefile, a Python project or a recipe you're trying to prepare will 
be trickier. But the make language is very simple.


Writing anything by hand gives more control over your code. That's obvious: you don't have a program "interpreting" what you want to do things... any decision you take is going to be taken by the program and the quality of the result will depend on the quality of the IDE. But, I don't mean you need whole control always... and possibly never, that's why IDEs exist.

What I mean is that you should know what's a Makefile and how to write them, just in case the IDE doesn't get what you want to do. And keep in mind a bug in an IDE can appear anytime, so you better be prepared when that happens so you aren't tight up to what that program can or can't do. Also, what happens if for some reason you have to work in an environment (a job, for example) where your favorite IDE is not there?

Hope I've cleared my point out.

Having control over your code and having control over your build system is two different things. That's why I needed you to explain. It seems like you confused those. My point is, OP won't get any better in C programming by learning how to handwrite a makefile form the beginning. But he actually will get better by using an ide because IDE will make things easier for him and thus, he will learn quicker without the frustrations he may have while using a text editor + make + console

cheers

---

### Post by mujambee on 2008-09-05
> **cb951303 said:**
> My point is, OP won't get any better in C programming by learning how to handwrite a makefile form the beginning. But he actually will get better by using an ide because IDE will make things easier for him and thus, he will learn quicker without the frustrations he may have while using a text editor + make + console


That's true, but if they get to the IDE they never learn anything else, they never do... :cry:

---

### Post by cb951303 on 2008-09-05
> **mujambee said:**
> Once you start doing things the easy way there is no coming back, you'll never learn the hard way unless hardly pressed. ;)

thats wrong, at least for me and my students.
I actually believe that if you get better at programming, you understand its helper tools (such as makefile, svn ...etc) more easily. But it's not always valid viceversa...

---

### Post by mujambee on 2008-09-05
> **cb951303 said:**
> thats wrong, at least for me and my students.

Definitely right for my Spanish programmers... :-D

---

### Post by ilrudie on 2008-09-05
> **cb951303 said:**
> I think its safe to assume that OP is a beginner. that being said I agree that C is not a good "first" programming language nowadays, however it was once, before interpreted languages came to the scene. That's a different topic though...

 I don't know where you get that idea. An IDE's first and almost only aim is to make things easier for the developer. I also don't agree with your idea of ides' complex user interfaces because I know *alot* of people started learning c/c++ with dev-c++ just because it was so easy to use. What you qualify as "valuable experience" is easily obatained once you actually get into the programming and start understanding things. There is absolutely no rule saying that we should learn handwriting makefiles and using command line compilers from the beginning. It simply doesn't have any advantage over learning it later (once you actually understand what programming is about)

Its really 6 of 1, half dozen of the other.  I think IDEs are just extra complication and distraction when you are trying to learn preventing you from learning the basics.  Like learning to fly with a 747 (lots of great tools that make flying easier for pilots) without knowing how to fly a glider (simple operation).  You see it as an assistant like learning to drive a car with an automatic transmission instead of a 5-speed manual.  It keeps shifting off your mind while you are learning to not run into things.  I'm not convinced there is a right or a wrong answer here in reality.  I just think the anti-IDE point of view needed to be expressed here so the OP can make a truely informed decision.

---

### Post by monkeyking on 2008-09-05
I've never used anything that emacs and commandline in linux.
Mainly because when I started programming, there wasn't any real good ide's.

But the modern ide's, do they have code completion and api lookup?

Like when you type "this." a funky menu appears with a list of vars and methods related to the object?

Is't not that I don't like ide's, I wouldn't use anything less potent than bloodshed on windows.

---

### Post by cb951303 on 2008-09-05
> **ilrudie said:**
> I just think the anti-IDE point of view needed to be expressed here so the OP can make a truely informed decision.

valid point... that's also why I wanted to express the anti Text Editor point of view :lolflag:

---

### Post by nvteighen on 2008-09-05
Yeah! We all are happy now! :)

---

### Post by Can+~ on 2008-09-05
"The best enviroment" does not exist, depends on what you like, personally:

- Light: Gedit with all the settings and minimal plugins + an open shell with makefile, or just a plain .sh with the compile command. I liked geany before, but it's kinda limited.

- Heavy duty: Eclipse with the CDT plugin (And py plugin).

---

### Post by GeneralZod on 2008-09-06
> **monkeyking said:**
> 
But the modern ide's, do they have code completion and api lookup?

Like when you type "this." a funky menu appears with a list of vars and methods related to the object?


Most will, yes (Eclipse and KDevelop do, for example).

---

### Post by Canis familiaris on 2008-09-06
Codeblocks is worth a shot. I like it a lot.

---

### Post by Sly-.- on 2008-09-11
So would I have to install any plugins for Gedit? Because right now to me it just looks like notepad, I thought it had extra features, mind I haven't done anything to it though. 

I want to use a nice and simple editor, with helpful features, and the gcc/g++ compiler.

---

### Post by ilrudie on 2008-09-11
> **Sly-.- said:**
> So would I have to install any plugins for Gedit? Because right now to me it just looks like notepad, I thought it had extra features, mind I haven't done anything to it though. 

I want to use a nice and simple editor, with helpful features, and the gcc/g++ compiler.

I believe the syntax highlighting for a lot of languages (c and c++ included) is built in to gedit (Text Editor as Ubuntu calls it).  It should highlight based on extension or you can change the highlighting under the "View">"Highlighting Mode" menu.

What other features are you looking for?

Some more plugins can be found [here]("http://live.gnome.org/Gedit/Plugins")

---

### Post by cb951303 on 2008-09-11
> **ilrudie said:**
> 
Some more plugins can be found [here]("http://live.gnome.org/Gedit/Plugins")

actually I believe those are installed by default. he/she just needs to enable them from preferences

---

### Post by ilrudie on 2008-09-11
> **cb951303 said:**
> actually I believe those are installed by default. he/she just needs to enable them from preferences

It has a bunch that aren't installed by default as well as the standard ones that come with it.

---

### Post by hessiess on 2008-10-13
Q: Best C/C++ Environment
A: Vim ;)

---

### Post by jimi_hendrix on 2008-10-13
> **hessiess said:**
> Q: Best C/C++ Environment
A: Vim ;)

i normally like something a little bigger but vim is growing on me...

i normally use geany in linux because it has the compile button so i dont have to keep switching to terminal

on windows i use the microsoft ide because its what all the books ive read use so i learned with it and now am used to it and its bloat

---

### Post by yabbadabbadont on 2008-10-13
> **jimi_hendrix said:**
> i normally like something a little bigger but vim is growing on me...

i normally use geany in linux because it has the compile button so i dont have to keep switching to terminal

on windows i use the microsoft ide because its what all the books ive read use so i learned with it and now am used to it and its bloat

In vim, use the ":make" command.  In gvim, hit the make button...  ;)

---

### Post by master5o1 on 2008-10-13
Currently I just use gedit+gnome-terminal [not embedded terminal] for C. Simpy because it is simple [heh].

I would probably use an IDE when I get into more complex programs but currently, a one source file project for uni doesn't require it.

---

### Post by jimi_hendrix on 2008-10-13
> **yabbadabbadont said:**
> In vim, use the ":make" command.  In gvim, hit the make button...  ;)

couldnt figure out what happened after i hit the button so i still :wq and then ./file in terminal

---

### Post by lompa on 2009-11-24
Hi guys

After having tried Eclipse + CDT (which I find very good, but way too resource-consuming), Anjuta, Code::blocks, I finally gave a look to Codelite (after having relized the 2.0 release had just come out). Despite many things seem still immature (e.g. svn plugin, the documentation...) it immediately bacame my favourite C++ IDE:
- it has very nice **code completion, based on actual header file crawling** (no need to perform weird things such as fake .h file addition to the project)
- support for **custom makefiles** (this was a must in my case and previously eclipse was the only satisfying IDE with this regard)
- it's lightweight and fast! (unlike eclipse)
- ok gdb integration
- doxygen code generation
- even an svn plugin (not decently documented, yet)

I can only suggest you to have a try!

Lompa

---

