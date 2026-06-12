---
title: "C++ Ide , Compilers &amp; Tools"
date: 2019-05-06
forum: Programming Talk
---

### Post by radu19842 on 2019-05-06
Good morning and a great new week start to all , i have a fewquestion since i am a beginner in ubuntu , witch is the best **compiler / ide **and what** other tools **are best to be used in xubuntu 18.04 Bionic Beaver for development** of Software/IDE/Games**
All the best !

---

### Post by TheFu on 2019-05-06
Every Unix OS with X/windows is an IDE already.
[https://sanctum.geek.nz/arabesque/series/unix-as-ide/](https://sanctum.geek.nz/arabesque/series/unix-as-ide/)

You might want to read this: [https://isocpp.org/faq](https://isocpp.org/faq)  C++ Super-FAQ!

There are really only 3 popular C++ compilers used on Linux.  g++, Intel's commercial compiler and LLVM.  Almost everyone uses g++. You'll need to use the same C++ compiler that your libraries use so the object name munging between your compiler output and theirs are compatible. 
The list of tools used by C/C++ devs varies wildly.  All the developers that I know use vim as their editor, do builds in a terminal with gmake or cmake and a debugger window open. Since they use g++, the debugger is gdb. As part of their build, they will generate xref files using [ctags]("https://github.com/majutsushi/ctags"), documentation, automatically format the code and run the code through [linters]("https://invisible-island.net/personal/lint-tools.html") and automatic testing using different tools for memory management issues like [valgrind]("http://cs.ecs.baylor.edu/~donahoo/tools/valgrind/").

If you want the bloat of an IDE, then you'll need to setup the IDE with the compiler and debugger you select along with all the locations for libraries and include files on a per-project basis. Much easier to just have a Makefile.

---

### Post by radu19842 on 2019-05-06
[COLOR=#000000]**TheFu** thank you so much , i have installed trough terminal "**Visual Studio Cod**e" and then installed this tool for **C/C++** in the next link [http://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools](http://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools) but on the next link [http://code.visualstudio.com/docs/setup/additional-components](http://code.visualstudio.com/docs/setup/additional-components)  says to install [/COLOR][https://git-scm.com/]("http://git-scm.com/") **GIT ** is it necessary ??? Now as i told you that i installed VSC trough terminal but when i go to Software center and search for VSC as you see in the photo there is something called "Visual Studio Code - Insider" , shoud i install it or not ? Also what else should i instal (and how ?) in order to get started coding in c++ ? I installed before VSC the G++ compiler (hope that's alright ?) also what GUI editors you sugest ? I am a beginner in ubuntu (Xubuntu 18.04) and i never used in windows 7 at all visual studio from microsoft so i hope you understand ? Have a great evening !

---

### Post by TheFu on 2019-05-06
Looks like I'm not going to be any help. Sorry.

I don't touch Microsoft **anything** unless absolutely required.  I've been burned many, many, many, times and can easily avoid that.  Simple - don't use anything they look at, touch, sell, give away.  Don't.  Just don't.  You are free to do what you think is best, of course.  Linux people generally avoid Microsoft stuff. I'm one of the people who deleted their github accounts when MSFT bought them out. OTOH, I didn't have any professional code there. That stuff is private almost always.

I can't suggest anything/editors I've not used.  I use **vim** for coding.  In the hands of an expert, no other editor compares.  If you are planning to be a professional developer, know that GUI editors don't work on servers, so you'll need to know a minimal amount of vim anyway.  Also, I've **never** seen any editor except vi/vim on network devices.  For my first 6 months, I avoided using vi even though everyone else on my team was using it.  I insisted on using emacs, which at the time was the only other option on Unix for programming editors.  A few months later, I was having emacs switch into vi-mode all the time to get work done, so I decided to stop and just use vi/vim directly.
If you have any interest in vim, there is a built-in tutorial, then there are some intermediate videos on youtube.  After that point, you'll be well beyond what any other editor can accomplish.  Just learn 1 new thing every week and in a few years, you'll be freakin' amazing with it.  My use of vim is purely instinct at this point.

There are plenty of editors these days and fans for all of them.  I'm from this age: [https://dilbert.com/strip/1995-06-24](https://dilbert.com/strip/1995-06-24) .

---

### Post by spjackson on 2019-05-07
I can't say much in response to your original post. However, I can answer 2 specific questions.
> **radu19842 said:**
> **GIT ** is it necessary ???

To write your first simple program, a version control system such as git may not be strictly necessary, but you will find one helpful sooner than you think, even working alone. See [https://stackoverflow.com/questions/1408450/why-should-i-use-version-control](https://stackoverflow.com/questions/1408450/why-should-i-use-version-control) . There are other options but git is now far and away the most dominant.
> 
"Visual Studio Code - Insider" , shoud i install it or not ?

The "Insiders build" is a [nightly snapshot]("https://code.visualstudio.com/docs/supporting/faq#_can-i-run-prerelease-versions-of-vs-code"). You don't need that. If you really want to use Visual Studio Code then choose the current stable release.

---

### Post by radu19842 on 2019-05-08
> **spjackson said:**
> I can't say much in response to your original post. However, I can answer 2 specific questions.

To write your first simple program, a version control system such as git may not be strictly necessary, but you will find one helpful sooner than you think, even working alone. See [https://stackoverflow.com/questions/1408450/why-should-i-use-version-control](https://stackoverflow.com/questions/1408450/why-should-i-use-version-control) . There are other options but git is now far and away the most dominant.

The "Insiders build" is a [nightly snapshot]("https://code.visualstudio.com/docs/supporting/faq#_can-i-run-prerelease-versions-of-vs-code"). You don't need that. If you really want to use Visual Studio Code then choose the current stable release.

Thank you very much for your answer , it helped me allot since i'm still in the fog with ubuntu ! :)

---

### Post by TheFu on 2019-05-08
+1 on using Git - really any version control system that doesn't suck is fine.  

We didn't have Git when I started. For internet-based projects, git is pretty great.  For corporate projects, there are choices which use a server that would be run inside the company. Companies like to have control, or perceived control, by having the software source version control system on their network, on their computers, on their HDDs.

Git works only due to a social, human, agreement by all the project members.  There is no technical reason for any specific git repo to be "the source" for any project. It is just an agreement that the rest of the project follows, by choice.  Anyone can "fork" a project and just needs to convince others to use their repo instead of the prior repo.  If this is slightly confusing, there are some youtube videos that try to explain how git works.  Randall Schwartz gave an hour talk at Google about it long ago.

With all that said, **I use git.**  My company uses git for our 3-person development team.  We only use git for code related stuff, not for documentation. For that, we use a document management system, which is much easier for non-technical people to use, but 1000x harder to setup than git.  Git took me about 10 minutes to setup a shared repo for our team - that includes finding the 1 page I needed to read in ProGIT (free PDF book) for how to do it - and the time to download. ;)

Over the years, I've used about 10 version control systems. SCCS, RCS, MS-SourceSafe, StarTeam, CVS, SVN, and the rest were less popular, proprietary, solutions.  All have issues.  SourceSafe had data corruption issues much too often. We were always restoring from backups and redoing changes.

Learn git. 
Use git.
Love git.
It will save you from many of your dumbest mistakes. I speak from experience.  If you are using ZIP files or TGZ files as version control - stop that already.  Use git.

Learning Linux takes years, especially if you want to be a good programmer.  The OS matters. The GUI, in general, doesn't matter.  I'm using the same commands and scripts with few, if any, changes that I wrote in 1993. They still work today.  Don't get hung up about "ubuntu."  Unix is Unix is Unix 90% of the time.  AIX, Solaris, HP-UX, and all the Linux variants are 90% the same.  Where they different are in relatively minor places, close to the OS, that system admins care about.  And those differences are only slight, they use the same ideas.  Solaris has ZFS. Linux has ZFS.  All the others have a storage "volume manager" - Linux has LVM.  They all have package managers, each is a little different, uses different commands with different options, but they all install and update software.  They all need backups from a file system that has been quiesced.  With LVM, create a snapshot to freeze the blocks, then mount those frozen blocks somewhere and back them up while the rest of the system keeps running, changes are written to different blocks. When the backup finishes, remove the "snapshot", which unfreezes the blocks and everything keeps going as normal.  All the Unix systems have this idea, but only of you use a volume manager.  For binary files being written to all the time, this is absolutely critical to ensure the file doesn't change during backups.
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a good source for beginning Linux knowledge that won't be useless in 2 yrs because a new GUI is released.  Learning the ideas and commands in a specific order is best, since each command builds on the last one.  Learning Unix is like learning a new spoken language. Attack the process in the same way.  At least 1 hr a day, but 4+ hrs daily is better. Total immersion works best.  Even with total immersion, at least 6 months is needed.

---

### Post by radu19842 on 2019-05-17
I got it now about compilers and ide's for C++ , how about a little list of software for GUI building using C++ , thank you and a great wekend ! :)

---

### Post by anneranch on 2019-05-27
For what it is worth.
Investigate what you current OS version repository contains. 
You picked Linux as OS , the best is to stay with what it (natively) supports.
Some  OS are not too swift when "upgrading". 
Try to look for "GUI framework" ( for C++) 
Before you commit check "users forum" - that  tells you a lot about the software "quality" . 
Beware of "non profit foundations".

---

