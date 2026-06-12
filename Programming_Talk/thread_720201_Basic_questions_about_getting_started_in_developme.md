---
title: "Basic questions about getting started in development"
date: 2008-03-10
forum: Programming Talk
---

### Post by SpeakerForTheDead on 2008-03-10
Hello all.

I'm a relatively new Ubuntu user (about a month now I thinK), and I'm looking for some advice concerning the best way to go about learning the ropes and getting started with application development in the community. My short term goal, at the moment, is to be able to download the source of some existing programs and start picking them apart, making a couple basic changes here and there, in order to get a feel for the way real, complex, usable applications are structured and implemented. I figure at this point that'll be the quickest way to really get on my feet, and start linking more theory to real application.

I'm a first year computer science major, and relatively comfortable/competent once I actually get into the code (Java, C#, C++... I know how to *program).* What I'm running into at the moment is just a barier getting started... I'm still not clear on Ubuntu's "compile from the source" installation process, or even if that's entirely relevant to what it is I want to do. I've been reading up a lot recently on commands and such (gotta love google), but I can't seem to find anything that just outlines the basic concepts of getting started in open source development, things that seem to be assumed knowledge everywhere else. 
[B]
So to give this thread a little more concrete goal[/B]: I've downloaded and installed MonoDevelop, and I've downloaded the source code to Banshee, and now I'd like to make some trivial changes (again, just for the educational value of it) and compile it... how on earth do I go about doing that? I 

Sorry if this seems a little ridiculous, I just need a push in the right direction, or mabye a couple links to where I can find the information I'm looking for. 

Thanks,
Speaker

---

### Post by jespdj on 2008-03-10
The website for Banshee has a [Developers page](http://www.banshee-project.org/Developers) and there's a page named [Building Banshee from Source](http://www.banshee-project.org/Banshee_Source) that will get you started.

Many open source programs, especially for Linux and other Unix variants, use tools like [make](http://www.gnu.org/software/make/) and [autotools](http://sources.redhat.com/autobook/autobook/autobook.html#SEC_Top) to automate the build process.

---

### Post by pmasiar on 2008-03-10
Find a project, join devel mailing list, ask for help. Be prepared to be self-starter.

Another option is to join MOTU team and help with packaging.

---

### Post by mb108 on 2008-03-10
I'd rather recommend a free/online source, but I've been in your position and for some reason, as you said, there's just not that much out there. I ended up buying [this book]("http://www.amazon.com/Programmers-Toolbox-Prentice-Software-Development/dp/0132198576") and it's an excellent intro to all the basic tools/knowledge you need to get going.

Chapter 1 is about packages, chapter 2 is "Building from Source" including talk on autotools (and alternatives) and using diff for patches... goes on to give an intro to the kernel, processes, debugging. Good stuff.

A little more than what you're asking for here, but if you plan on pursuing open source and specifically Linux programming, it will be nice to have on the shelf.

---

### Post by SpeakerForTheDead on 2008-03-12
Thanks guys, I appreciate the help. Sorry I've been so slow about replying but I've been traveling the last couple days.

jespdj:
I've been spending a lot of time recently on that developers page, and specifically on the "Build banshee from source" page... but I still haven't managed to get it to work yet. I'd tried to follow those direction before posting the first time, and have tried again and again... and each time I try it seems that I get hung up on a different place. At the moment it's letting my run "svn co http://svn.gnome.org/svn/banshee/trunk/banshee" to download the source from the GNOME subversion, and then "./autogen.sh --prefix=/usr" from within the banshee directory. When I try to then run "make," it fails and gives me the following: 

```
...
Compiling Banshee.Services.dll...
./Banshee.Sources/DatabaseSource.cs(72,38): error CS0183: The given expression is always of the provided (`Hyena.Data.IFilterable') type
Compilation failed: 1 error(s), 0 warnings
make[4]: *** [../../../bin/Banshee.Services.dll] Error 1
make[4]: Leaving directory `/home/walker/banshee/src/Core/Banshee.Services'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/walker/banshee/src/Core'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/walker/banshee/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/walker/banshee'
make: *** [all] Error 2
walker@walker-laptop:~/banshee$ 
```

So I'm stuck at the moment. I've installed banshee before (from a package), but I'm not sure I have all of the necessary build dependencies installed... how do I go about checking that/installing those specific packages individually (I've looked on Synaptic without much luck)? By the way, thanks for the links to that information on make and automake... I'm curious though, is this the process that I'd follow to recompile such a program each time I go in and make changes, or is there a way to do it through some sort of IDE (at least when you're actively making changes)? It just seems like when there are errors compiling, this isn't giving much information.

pmasiar:
Absolutely no problems with having to be a "self-starter," that's how I learned most of my programming fundamentals in the first place. I'll look into joining a devel list, thanks for the advice.


mb108:
Good to know that it's not just me who's having (or has had) these kinds of problems. I'll check that book you suggested out as well.

Thanks again guys,
Speaker

---

