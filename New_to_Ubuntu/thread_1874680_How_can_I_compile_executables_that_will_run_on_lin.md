---
title: "How can I compile executables that will run on linux?"
date: 2011-11-03
forum: New to Ubuntu
---

### Post by ClientAlive on 2011-11-03
Hi,

I have a class right now where we're learning some C programming. We'd been using cygwin on a windows virtual machine to compile and run our programs but I was told it's ok for me to do the work on my own, linux machine if I want. I know I have gcc on here (Ubuntu 10.04 LTS) so I have the tools I need to do the assignments. My question is what is the equivalent to the ".exe" file you get for windows? Is it ".bin"? So if I use the "-o" flag with gcc I can just add ".bin" instead of ".exe" to the end of my file name and I'll be able to run the program in Ubuntu?

Oh, and can someone suggest a good, basic text editor that adds color, numbers the lines and characters, and helps with formatting, indenting and such? I've been using gedit because it's the default but I don't think it has some of those other features. If it does I'm not aware of it.


Thanks in advance for any help.

:)

---

### Post by anewguy on 2011-11-03
You may want to install and try code:blocks - it's one of the IDE's that are available.  It lets you have debugging windows, etc..  

As far as the executable name is concerned, there really aren't any "fixed" file associations in Linux as there are in Windows.  It can be simply "x".  It could be "imaprogramsorun.me" as long as it is set to executable.

Dave ;)

---

### Post by juancarlospaco on 2011-11-03
You can try [http://ninja-ide.org/](http://ninja-ide.org/)

---

### Post by Lars Noodén on 2011-11-03
> **ClientAlive said:**
> Oh, and can someone suggest a good, basic text editor that adds color, numbers the lines and characters, and helps with formatting, indenting and such?

[geany](http://www.geany.org/), [kate](http://kate-editor.org/about-kate/), or emacs are good basic editors with syntax highlighting.  Try them, you'll probably like them.

---

### Post by decoherence on 2011-11-03
given program 'hello_world.c' simply do

```
gcc hello_world.c -o hello_world

```
Linux systems don't care about file suffixes, at least not on the command line. Whether the file is executable or not depends on the permissions. So after you compile, run

```
chmod +x hello_world

```
then to run the program type (assuming you are in the same directory as the program)

```
./hello_world

```

or place the hello_world binary somewhere in your path so you don't have to specify ./ or whatever path.

ADD: +1 for geany. I don't use it for C but it's quite nice for bash and python. But try all the IDEs listed -- they're free, after all!

---

### Post by ClientAlive on 2011-11-03
Right on. Thanks fellas. I'll take a look around at some of those. Good to be clear on running the program too.

:D

---

### Post by Majorix on 2011-11-03
The C code you compile on Linux will NOT be compatible with Windows. Just so you know.

---

### Post by ClientAlive on 2011-11-03
> **Majorix said:**
> The C code you compile on Linux will NOT be compatible with Windows. Just so you know.


Yeah. That's cool. What we've been doing is submitting screenshots of the running program along with the source code - so it's all good.

:)

---

### Post by ClientAlive on 2011-11-04
If an ide says it's for C++ will it work for C I wonder?

Also, I had forgotten I downloaded mono develop before and had just never messed with it. Last night I worked with it to work on a project but something odd and messed up seemed to be going on. It's like the thing would continue to eat memory. More and more until pretty soon it was starting to gobble up my swap. After about 30 min (if I had to guess) it would freeze up the whole machine and I'd have to force it to quit. I'd look at "free -m" and even after closing the program still didn't seem to be releasing memory so I'd have to reboot to even continue using my machine. It's a shame because it seems like a fine ide to use.

Now there is one caveat. I'm not extremely experienced w/ Linux so I don't know how to investigate things like this. How to pinpoint and verify that mono develop was the cause of all this. I'm writing and running these programs and just learning to program. The programs I write are simple but often not very good at first and maybe they are the real culprit. Maybe the one I was working on last night was the real cause of the memory issue.

I'm gonna grab a couple of the ide mentioned in this thread today and check them out. I suppose if I get the same problem with other ide then its not the ide doing it. Idk.  :confused:

---

### Post by Paqman on 2011-11-04
> **ClientAlive said:**
> 
Oh, and can someone suggest a good, basic text editor that adds color, numbers the lines and characters, and helps with formatting, indenting and such? I've been using gedit because it's the default but I don't think it has some of those other features. If it does I'm not aware of it.


There's about a million plugins for Gedit that make it do all that. Line numbers is in the default version, just not enabled by default.

---

### Post by Mark Phelps on 2011-11-04
Having been through this myself, let me share some concerns ...

First, since "C" was first used in Unix (as far as I know), I find it ironic, to say the least, that your class is NOT using Linux to do development.

Second, in some programming classes, the biggest return you get is not writing code, but in sharing experiences with your classmates and forming study groups to work through problems.  But that's only possible if everyone is using the same "tools".  Using your own approach puts you "on your own" -- so if you have problems, you won't be able to turn to your classmates for help.  Something to consider.

---

### Post by ClientAlive on 2011-11-05
> **Mark Phelps said:**
> Having been through this myself, let me share some concerns ...

First, since "C" was first used in Unix (as far as I know), I find it ironic, to say the least, that your class is NOT using Linux to do development.

Second, in some programming classes, the biggest return you get is not writing code, but in sharing experiences with your classmates and forming study groups to work through problems.  But that's only possible if everyone is using the same "tools".  Using your own approach puts you "on your own" -- so if you have problems, you won't be able to turn to your classmates for help.  Something to consider.


That makes sense. it's an online class, and I've always struggled making connections w/ my classmates (my own fault). I know I could use some help right now. I've struggled through the last 3 weeks in this class, fear I may fail it, and am currently (right this minute) hopelessly stuck on an assignment that has already passed. (](*,) I still want to figure it out, passed or not). 

Well thanks for your advice Mark. I appreciate it. Maybe I should try to connect more.

:-k
----------------

Edit:

Oh, you mentioned irony. Add to it that we use cygwin to run our programs in. (cygwin is a program for windows that emulates linux, the linux terminal). Wow.

---

### Post by anewguy on 2011-11-05
Yeah, as far as I know when Ritchie, Dan Brown, Kerlligan (the spelling is WAY off) first worked with developing "B", then as things progressed they made this new thing called "C". I think you're right in Unix being the first OS that made use of "C" - I think that outside of some assembly it was actually written in "C", though I imagine (it's been so long now) that they used "C" for other darpa, etc., related things that were non-Unix.

ClientAlive:  I feel for you, buddy.  It's a tougher road to take classes like this without any real interaction with others.  Perhaps you should check for students at other schools (including high schools), support groups that may be local, including any college non-class groups and computer club groups.  Go to your nearest Radio Shack, Best Buy, what have you, and tell them you are looking for others who are learning "C" and wonder if they could help you find someone.

It can be done - and I really think you'll do fine.  It's just when you get stuck on something, and that something begins to play with your mind, which in turn makes you think "I'll never get this!".  Just tell yourself you CAN do it.  When all else fails, go back a step and start again.  Sometimes a fresh start can also give you a new perspective on the project and thereby a different solution path.

Dave ;)

---

### Post by ClientAlive on 2011-11-06
> **anewguy said:**
> Yeah, as far as I know when Ritchie, Dan Brown, Kerlligan (the spelling is WAY off) first worked with developing "B", then as things progressed they made this new thing called "C". I think you're right in Unix being the first OS that made use of "C" - I think that outside of some assembly it was actually written in "C", though I imagine (it's been so long now) that they used "C" for other darpa, etc., related things that were non-Unix.

ClientAlive:  I feel for you, buddy.  It's a tougher road to take classes like this without any real interaction with others.  Perhaps you should check for students at other schools (including high schools), support groups that may be local, including any college non-class groups and computer club groups.  Go to your nearest Radio Shack, Best Buy, what have you, and tell them you are looking for others who are learning "C" and wonder if they could help you find someone.

It can be done - and I really think you'll do fine.  It's just when you get stuck on something, and that something begins to play with your mind, which in turn makes you think "I'll never get this!".  Just tell yourself you CAN do it.  When all else fails, go back a step and start again.  Sometimes a fresh start can also give you a new perspective on the project and thereby a different solution path.

Dave ;)


Right on. That's a good idea (about places/ ways to solicit for connections). The first few weeks of the class were extremely simple and I got a little cocky. I though, 'boy, if this is all it is I can dance circles around this stuff.' Then came the dreaded for loop. Ouch! After about the third week stuff started to get a lot more complex (relative to someone with no previous exper. in C). I want to be involved w/ it though so I guess I'll have to tough it out and do whatever it takes. Apparently, there are no easy paths in life.

---

### Post by anewguy on 2011-11-06
When it comes to C or C++, there really isn't an easy path.  I know there are other languages the some call easier, which they are, but they don't have the inherit power that C or C++ does.  This also means that C or C++ will also sometimes allow you to do things because you think the syntax is correct for what you want to do, when in fact it's not - but it's correct for something completely different.  That's where any of the IDE's come in handy.  It's just personal taste, but I just like code:blocks.

There is also a programming forum in the ubuntu forums.  See the development and programming forum at: [http://ubuntuforums.org/forumdisplay.php?f=310]("http://ubuntuforums.org/forumdisplay.php?f=310")

The people there can probably provide you with help.  Let them know you're taking the on-course and need help.  Be sure to let them know you don't want them to do your homework for you (you'd be surprised how many people do) but that you need help with concepts and syntax.

Dave ;)

---

### Post by directhex on 2011-11-07
> **ClientAlive said:**
> If an ide says it's for C++ will it work for C I wonder?

Also, I had forgotten I downloaded mono develop before and had just never messed with it. Last night I worked with it to work on a project but something odd and messed up seemed to be going on. It's like the thing would continue to eat memory. More and more until pretty soon it was starting to gobble up my swap. After about 30 min (if I had to guess) it would freeze up the whole machine and I'd have to force it to quit. I'd look at "free -m" and even after closing the program still didn't seem to be releasing memory so I'd have to reboot to even continue using my machine. It's a shame because it seems like a fine ide to use.

Now there is one caveat. I'm not extremely experienced w/ Linux so I don't know how to investigate things like this. How to pinpoint and verify that mono develop was the cause of all this. I'm writing and running these programs and just learning to program. The programs I write are simple but often not very good at first and maybe they are the real culprit. Maybe the one I was working on last night was the real cause of the memory issue.

I'm gonna grab a couple of the ide mentioned in this thread today and check them out. I suppose if I get the same problem with other ide then its not the ide doing it. Idk.  :confused:

I've never heard of that kind of memory leak in MonoDevelop, in 6 years of using it.

---

### Post by ClientAlive on 2011-11-09
> **directhex said:**
> I've never heard of that kind of memory leak in MonoDevelop, in 6 years of using it.


Oh, it was prob something else then. I started using Geany though and that stopped happening. Idk.

---

### Post by alco75 on 2011-11-09
> **ClientAlive said:**
> If an ide says it's for C++ will it work for C I wonder?

Did anyone answer this?

Probably, yes. Since C is a subset of C++, any C program is also a C++ program. Which means any C++ compiler (and presumably C++ IDE too) should handle C just fine.

---

### Post by ClientAlive on 2011-11-09
> **alco75 said:**
> Did anyone answer this?

Probably, yes. Since C is a subset of C++, any C program is also a C++ program. Which means any C++ compiler (and presumably C++ IDE too) should handle C just fine.

Right on. I wasn't sure about that. I imagine if a guy just named the file with .c at the end you'd be golden. Run it through a C compiler an your set. I guess.

I had a decision to make. Whether to grab something that had a ton of advanced features I knew little or nothing about or go with something simple where maybe you had to do a lot manually. Since I don't know what a lot of the advanced feature are (or even what an ide includes/ what makes and ide "an ide") I grabbed the simple manual one for now. At least it has line and character numbers.

I thought it was supposed to have code completion, which, I guess it does - just not till I'm about one letter away from having it typed out anyway. And I thought it had something about matching your brackets or something but I'm not sure I've seen that. It would be nice if the thing would highlight/ select code between matching brackets though. Idk, maybe geany is almost the other end of the extreme. Unless it has some feature I'm not aware of (and it probably does) it'd be cool to find one that's kinda 'middle of the road'.

:)

---

