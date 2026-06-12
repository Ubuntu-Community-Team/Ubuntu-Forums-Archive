---
title: "Python linking; ode to executables"
date: 2009-06-12
forum: Programming Talk
---

### Post by kumoshk on 2009-06-12
I once was a strong advocate for being able to create Python executables (and I know how to do that, but it's not ideal, especially as it's not cross-platform).

Anyway, part of my reason for wanting binaries really is a separate issue. What I really wanted was a linker for a scripting language (Python in this case). You might wonder what I mean by that (as it might not be what you think).

I don't mind requiring the Python interpreter. What I do mind is having dependencies beyond that. For instance, if I use several libraries (e.g. WxPython, PyX, Cairo, Pango, PyGame, etc.) I don't want everyone else to have to install all those things&#8212;let alone every part of them (especially in a cross platform environment including operating systems that are not Debian-based).

So, the idea is to have a Python linker that gathers all the code used from the libraries, and links (or bundles) it into pyc files in your program's folder such that imports outside of the pyc files in your program are no longer required. This should not include all of every library you use, but only those parts of them that you do use.

Is there anything like this out there? If so, how does one use it? If not, how difficult would it be to write, and why hasn't it been written yet? It seems fairly simple&#8212;is it not? Has there been no demand for it? It would sure solve a lot of those dependency problems and reduce total download size to get a program going. I'm not saying everyone should do things this way (as that would go against the package systems for Linux), but it would sure make things a lot more portable (and that way if a package you needed ever went out of style, you wouldn't have to worry).

Of course, this might require linking header files and such, too, but that doesn't /seem/ much more difficult, except that it might make things so they're not cross-platform, due to compiling them and all. Anyway, there has to be a solution, though. Whatever the case, even if it weren't cross-platform, it would probably be easier to make than a Python executable.

Something like this, I think, should at least be available for libraries that don't rely on compiled C and such (such as some or all of PyGame, for instance).

---

### Post by nvteighen on 2009-06-12
Hum... Maybe some sort of Python preprocessor would be handy and do the job (and it would also make some macro-support possible... something that I really miss in Python). So, you could have a single temporary .py file containing all needed code and then compile it into .pyc. The issue with that is that if you need to modify your code, you'll have to recompile the whole thing again...

---

### Post by kumoshk on 2009-06-12
> **nvteighen said:**
> So, you could have a single temporary .py file containing all needed code and then compile it into .pyc. The issue with that is that if you need to modify your code, you'll have to recompile the whole thing again...

I wouldn't mind having to recompile (this would probably only be used in distribution, and not during the initial coding/testing).

---

### Post by scooper on 2009-06-12
It sounds a little like overkill to me.  You can already write Python code so that you can supply whatever dependencies you have in a subdirectory tree.  You would just need to have users unzip it where ever they want and run it.  I've written a few Python programs this way.

For example I included a copy of python-xlib with a tool I did.  The important thing is to check the license.  But you have the same problem if it's automatically packaged together.

What's the great motivation to automate the process of discovering the dependencies?  There shouldn't be that many.  Plus I think it's good to be quite aware of them and to minimize dependencies to the greatest extent possible.

Maybe I'm not quite understanding the need.

---

### Post by kumoshk on 2009-06-12
> **scooper said:**
> You can already write Python code so that you can supply whatever dependencies you have in a subdirectory tree.

But is there a way to put them there automatically without having to snoop around for ages through modules to find out all the packages they inherit from so you can include everything? How do you do this, if that's what you did?

That would be enough. I don't really care if it's all shoved in a single pyc file&#8212;just as long as they're in your program's folder somewhere, in some form, it should be fine.

> **scooper said:**
> What's the great motivation to automate the process of discovering the dependencies? There shouldn't be that many.
The motivation is to help those who are only partly computer literate who may want to use a program here and there (that's probably most computer users). It's all well and good for people like us to rely on the current excepted methods, but you can't really expect 'most' people to do it (especially people who don't use Linux, don't program, or don't use computers much). Windows doesn't have anything like apt-get or deb files to gather dependencies for you, and doing it manually isn't a job for your every day email user (besides, deb files are a pain to make with Python in Linux, anyway&#8212;even if it's doable). Granted, a lot of these people might have trouble installing even Python&#8212;but hardly all of them. I think a fair percentage of computer users can handle that.

The motivation is that I don't want people to have to do anything they think is complicated before they can use my programs (or else they might not use it). The motivation is to speed up the process of installation (i.e. instant versus the time it takes to download and install dependencies&#8212;not to mention taking care of any problems that come up in the process).

I like to use libraries beyond what Python offers by itself, quite a bit. I don't generally write a lot of programs for the command-line, and I'm not into Tkinter. So, at the very least I tend to use some GUI library or other, such as WxPython or GTK. PyGame is easy to snag code from, though&#8212;so I don't need to require that as a dependency if I use it.

Anyway, I don't know if that's the sort of answer you were looking for, but it is a concern for a lot of people.

I know that licensing is an issue, depending on what libraries you use. Isn't that just as much of an issue for compiled languages that make executables, though? Or is there something special to keep in mind if we don't encrypt the code, somehow?

---

### Post by Greyed on 2009-06-13
> **kumoshk said:**
> Is there anything like this out there?

Yes, there is.  No, I don't have the name of it off the top of my head because I haven't used it in approximately a year.  It really is a non-issue when you get down to it.  This is not a problem unique to Python.  They are called dynamic link libraries for a reason...

---

### Post by benj1 on 2009-06-13
> **kumoshk said:**
>  (besides, deb files are a pain to make with Python in Linux, anyway&#8212;even if it's doable). 

theres an easy .deb guide in the programming talk stickies, thats easier than any other way i know to make installation scripts.
they can handle dependencies, ie pygame, but it wouldn't be able to pull in part of pygame

---

### Post by scooper on 2009-06-13
> **kumoshk said:**
> I like to use libraries beyond what Python offers by itself, quite a bit. I don't generally write a lot of programs for the command-line, and I'm not into Tkinter. So, at the very least I tend to use some GUI library or other, such as WxPython or GTK. PyGame is easy to snag code from, though—so I don't need to require that as a dependency if I use it.

Anyway, I don't know if that's the sort of answer you were looking for, but it is a concern for a lot of people.

I know that licensing is an issue, depending on what libraries you use. Isn't that just as much of an issue for compiled languages that make executables, though? Or is there something special to keep in mind if we don't encrypt the code, somehow?

I hope I didn't come across as negative on the idea.  I think that the best installer is no installer.  So the desire to package everything an application needs to be self-sufficient is a noble one.

To be clear, I was really only talking about pure Python modules.  The python-xlib one I supply is Python-only.  Nothing is compiled to a platform-sensitive binary.  So I was basically saying that if your dependencies are all Python-only you can just zip everything up from a single directory tree and tweak your code to find modules in that tree first, rather than only looking for everything in /usr/lib/python....

GUI libraries all have compiled code or dependencies on other compiled binary libraries.  WX/GTK/QT all present huge problems in the size of the dependencies they bring in.  I never tried to package one of them with an application.  I imagine it being difficult, unless there's a clever tool.

As far as licensing goes, I was only stating the obvious.  You need to check that anything you redistribute allows redistribution, and that you adhere to the terms.  Sorry for bludgeoning the obvious. ;)

---

### Post by CptPicard on 2009-06-13
> **scooper said:**
> So the desire to package everything an application needs to be self-sufficient is a noble one.

I really do not quite understand why. I mean, even in Windows it would seem awkward to collect all of one's apps into some directory where they would live as massive, humongous statically compiled single-file binaries that you would then click to launch them. 

Applications need some configuration as regards the OS, they have their own data files that need to live somewhere, and so on... the Windows installer approach certainly has always sucked, but IMO, Linux package managers are a very good solution from the user's -- and system maintenance -- perspective.

---

### Post by kumoshk on 2009-06-13
> **scooper said:**
> … [last post by scooper]

It's all right. Thanks for the clarification and information.

Maybe my best bet (if I can't find that package that the other person said exists) is to learn how to do native GUI programming in Python. Is that possible? Doing unique code for each operating system should circumnavigate the whole library-inclusion issue as far as GUIs go (and, admittedly, GUIs are often a small part of a program). Plus, WxPython still has some important bugs to work out (i.e. text controls don't center on Mac OS), but they *are* working them out, I've come to find.

---

### Post by kumoshk on 2009-06-13
> **CptPicard said:**
> I really do not quite understand why. I mean, even in Windows it would seem awkward to collect all of one's apps into some directory where they would live as massive, humongous statically compiled single-file binaries that you would then click to launch them. 

Applications need some configuration as regards the OS, they have their own data files that need to live somewhere, and so on... the Windows installer approach certainly has always sucked, but IMO, Linux package managers are a very good solution from the user's -- and system maintenance -- perspective.

I did not mean to say that I like the system Windows uses. They don't do what I'm talking about any more than Linux does, although scripting languages may be less common on Windows (and hence they might get this reputation of having a plethora of stand-alone programs, which I might add they don't any, or at least much, more than Linux does). I do actually like the way Linux works with packaging and all, quite a bit more than the Windows sytem, and if Windows did that, too, I wouldn't have as much to complain about.

Having said that, I still don't necessarily see either system as the ultimate solution for all cases, but I'm not saying we should discard the Linux solution, either (perhaps not even the Windows one, as it does have occasional advantages). I'm not proposing that all apps be statically compiled—but the ability to make occasional ones so (at least as far as libraries and modules go—bundled interpreters aren't my thing), in my opinion. One reason is that it would make writing portable applications easier. I mean, if you have an app on your USB drive and move it from computer to computer, you're probably not going to want to install dependencies on every computer you visit (and you probably won't be able to, either, given not all of them would likely be yours).

Part of me is tempted to convert to a compiled language like D or objective C for the purpose, but that increases the issues I'd have to deal with. I just wish D had some GUI libraries that could work easily on Ubuntu with straight gdc and Phobos (no dmd and no Tango required)—at least for the 32-bit version, and that C++ had more convenient text-parsing functions—the problem there is that everyone wants to be efficient and that seems to takes precedence over programming-speed in the C++ culture (despite the fact that execution-speed isn't generally an issue when it comes to text parsing in a compiled language, except maybe for a ridiculously sophisticated random name generator that needs to produce hundreds of thousands of names per second).

Is there a compiled language more like Python (string-wise) than D?

---

