---
title: "development environments"
date: 2007-09-15
forum: Programming Talk
---

### Post by frenchcr on 2007-09-15
ive been learning C, C++ and Perl for about 6 months now, so im still new to programming.

I usually just use kate text editor to write my scripts in as it uses good colours, has a tab bar extension and terminal plugin.

Are there any development environments that are good to use? What are they and whats the difference between using a text editor and command line to these special environment apps ??

---

### Post by CptPicard on 2007-09-15
Don't know about Perl, but for C/C++ look Eclipse's CDT, KDevelop, Anjuta, Code::Blocks. IDEs add to your productivity by making it easier to manage your project's source, and some of their editors also have nice additional features such as code completion... 

Especially in C/C++, often I find that I spend more time fighting the IDE than actually accomplishing things but YMMV :)

---

### Post by frenchcr on 2007-09-16
Thanks!

> Eclipse's CDT, KDevelop, Anjuta, Code::Blocks

Any others, anyone?

Or any preferences between these. Im just looking for one good one to stick with.

Code completion you said...does this really work...anyone used it before and can give feedback on how helpful.

---

### Post by ryno519 on 2007-09-16
> **frenchcr said:**
> Thanks!



Any others, anyone?

Or any preferences between these. Im just looking for one good one to stick with.

Code completion you said...does this really work...anyone used it before and can give feedback on how helpful.

I prefer Code::Blocks myself. It has a nice clean interface, code completion/suggestion, templates and it's nice and simple. The only thing that might be considered bad about it compared to other GNU/Linux C/C++ IDE's is it doesn't produce its own makefile. I prefer to produce them myself, however, so it's not a big deal for me.

You could always just try them all out and see what you prefer. No harm in doing that. I'll point out that you won't find Code::Blocks in the Ubuntu repositories however, so you will have to find instructions on installing that.

Code completion is a good feature. Basically you are typing, and it gives you a list of suggested variable names or methods that you could invoke. You can type out maybe three letters out of 8 or 9 and hit tab and it's there. Can cut some time off of your development once you get used to it. The best thing about it is you can see what methods are available as you code, you don't have to go look at the header file to remember what you named something, it's all laid out for you automatically.

---

### Post by nonewmsgs on 2007-09-16
i love anjuta.  i haven't touched the other ones but it has good tab completion things and will make you a makefile (once you do apt-get all the libraries it doesnt come with..they are listed at the bottom whenever you finish project wizards as errors or warnings.

---

### Post by frenchcr on 2007-09-16
Thanks.

Ok, looks like **Anjuta** and **code::blocks** are the favourites.

Anyone out there, any more. Or reasons why i should pick one over the other (**Anjuta** vs. **code::blocks**)

---

### Post by tzulberti on 2007-09-17
Geany...

Its very simple, and i like for very simple programs.

---

### Post by Smygis on 2007-09-17
code::blocks or geany, i dont realy like anjuta.

---

### Post by frenchcr on 2007-09-17
ok we now have a swing in opinion...

**code::blocks** or **geany** or **anjuta** or **gedit with terminal plugin**

with **code::blocks** out in the lead! :)

---

### Post by Wybiral on 2007-09-17
I'd vote Code::Blocks too (well, that's what I prefer in Windows because it lacks good command line tools, but in Linux I prefer Gedit with the terminal plugin).

---

### Post by frenchcr on 2007-09-17
OK folks the lines are closed, the votes are in and winner is....................................................................................................................................................................


[FONT="Arial Black"][COLOR="Red"]CODE::BLOCKS[/COLOR][/FONT]:KS

I off to get familiar with my new friend.

---

### Post by CptPicard on 2007-09-17
Remember to add the repository for nightly build and the newer wxwidgets... this way I get to follow the latest and greatest all the time by just an apt-get upgrade. :) It *is* after all code under development, so manually installing a nightly build and expecting to use it for a longer time doesn't make sense...

---

### Post by milaks on 2007-09-17
If anything, I've been searching for good IDE on Linux, so I'll present my experience in brief, in hope that will help someone.

I've been "spoiled" by MS Visual C++ 6 (not .NET, it came later), so one of the primary things I wanted was "CodeAid" (aka *IntelliSense*, *AutoCompletion*, *Code Hinting* and so on), and it proved to be very difficult task on Linux.

By *CodeAid* in short I imply at presenting information about function/method signature (mainly argument list), list for template arguments, list of class members, possibility to complete  function/method/variable... name just by typing just first few characters of its name, etc. at **global scope** (including standard libraries, feature know as *follow includes*).

To me personally the most helpful thing is presenting information about argument list and class member member list, I'm not to lazy to type the full name myself, and it somehow always does in a way I don't like it (inserting closing parenthesis for example).

Two commercial IDE's that have very good *CodeAid* are: **SlickEdit** and **CodeForge** (there's also some Borland's IDE which existence is uncertain).

**Anjuta** (almost dead as I see) never had **real** *CodeAid* or I haven't saw it. It had some fixed signature list of standard C functions and some rudimentary autocomplete support. That's it.

**Kdevelop**, does have... some *CodeAid* support. First parsing must be manually initiated by specifying directories that contain header files, but even then it's not even close to MS Visual C++. For example, among other things, it seems that it cannot recognize *typedef's*, so there wont be information for *std::string* variable. Also Kdevelop had some really nasty problems with GDB that took me quite some time investigating my program, just to get answer from some of the developers that it's a bug in Kdevelop. Nevertheless, bug existed in next release. Kdevelop also tends to crash frequently.

In **Code::Blocks** (with those big toolbar icons :)) no matter what I try, I never managed to get *CodeAid* working, only somewhat Automatic complete[/i] with local (project) files. Tried this on Windows, and in Slackware and Ubuntu, with the same result. Haven't tried recent versions though.

**Eclipse + CDT (C++ Development Tool)**, now also available as separate C++ Eclipse package, has (maybe after SlickEdit and with NetBeans) the most advanced *CodeAid* from all above mentioned IDE's. It also doesn't have information about template argument list like MS Visual C++ though. At least not in version 3.2, and can be kinda slow in parsing.

**Emacs + CEDET**, in short doesn't have working *CodeAid* at all. If it has then I don't know how to make it work, and I certainly don't want to learn whole new language (elisp) just to configure (!!) one editor/IDE.

**Vim**, has some *CodeAid* support, in "less graphical way" through some scripts, and there's also script for Widnows only, that does that. Haven't tried it though. Still I think that Vim isn't IDE after all, but I mentioned it her for "contrast" to Emacs ;)

...

And finally **NetBeans + C++ pack addon**. It has *CodeAid* support at Eclipse level, but is somehow faster in parsing. It also, doesn't have information for template argument list :)

Funny how after all this years Linux IDE's still cannot beat simplicity and usability of one MS Visual Studio 6 :) But things are getting better with Eclipse and NetBeans. I work with Java too, so these two are my choices besides the fact that they have more advanced *CodeAid* then the rest of Linux (non-commercial) IDE's.

Next I'll probably try new Eclipse 3.3, because I've heard that it's much more faster in parsing then before.

---

### Post by Wybiral on 2007-09-18
> **milaks said:**
> Funny how after all this years Linux IDE's still cannot beat simplicity and usability of one MS Visual Studio 6 :)

It's really a preference issue. I've spent a lot of time developing in Linux using just Gedit and a command line. Now I sort-of jump between them and I absolutely cannot stand that little autocomplete pop-up in MS. I'm sure I could get used to it, but I don't want to. I don't like the thought of becoming dependent on an IDE feature.

Now... Since this is flameware worthy material, I will say that I don't really have anything wrong with MS or Visual Studio in general... I just don't like code completion. Syntax highlighting is great, code collapsing/expanding is OK, but I hate having crap pop-up when I'm typing. I'm also not fond of autotab either.

It may be a different story if I only programmed in MS, but having to jump between as I do, I prefer not to restrict my comfort to the features of one IDE.

---

### Post by milaks on 2007-09-19
Well if you work with more than one library (or even only with one) it's much more faster (read productive) and you can better focus on problem itself if you can "in place" see method prototype in case where for example there are several overloaded get/set methods, or when one class has naming convention for its members different than "expected", or when you didn't remember exact name... then, when you have to leave solving of the problem, search docs for that relatively tiny bit of info and then return, only to again, if you don't know whether function's first argument is source or destination, leave the work once more and search the docs and so on.

No. *CodeAid* is not some MS IDE specific feature anymore, and that's for a reason.

But it's not just *CodeAid*, there is also simplicity and stability in comparison between MS Visual Studio (6) and (some) Linux IDE's.

Yes there is a thing about the habit, but there's also a thing about programmer's productiveness. When for example some project has more files, then it's much more effective to use IDE then some text editor, write error-prone Makefile manually, debug through *gdb* directly... then when two more files are added to the project, update Makefile where with each step more time is spent and chance for error is increased for which solving also much time would be spent instead of working on project - programming part...
IDE maintains scripting/repetitive non-programming parts of making some program, for which not much brain power is necessarry, like writing and maintaining Makefile (or whatever it uses of organizing projects/files) or displaying much more information during debugging session while programmer can focus on solving the problem... I mean, this is a vaste of time, we are talking about some obvious benefits, standard nowadays in programming, not some acrobatics to prove "something", because there will always be someone who will use *notepad-like* text editor, bare *gdb* where he must constantly type "print this; print that", maintaining Makefiles himself, two/three letters variable names (program would be that much big)... and who knows maybe he'll think that it's too much dishonor to use high-level programming languages and compilers so he'll start using bare *asm* instructions and converting opcodes.

Windows programmers are not ashamed to admit that they use IDE, and not only they are not worse then Linux programmers but are definitely more productive.

As for some IDE specific features, that stands. I also "jump" between these two platforms, and it's unpleasant to use ones IDE's feature's on one platform, and others on other platform, but that is eliminated if you can use same IDE on both platforms. That's the case with two (free) IDE's I mentioned in my previous post: ***Eclipse*** and ***NetBeans***.

Best regards.

---

