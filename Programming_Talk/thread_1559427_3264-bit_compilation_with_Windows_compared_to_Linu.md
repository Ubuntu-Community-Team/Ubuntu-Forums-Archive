---
title: "32/64-bit compilation with Windows compared to Linux"
date: 2010-08-23
forum: Programming Talk
---

### Post by Intrepid Ibex on 2010-08-23
Why is there (almost) always a additional 64-bit version of an application for linux but not for Windows, e.g. VMware Workstation, Firefox, Chromium, Thunderbird and VirtualBox.

Is it like so hard to compile a 64-bit version for Windows?

---

### Post by worseisworser on 2010-08-23
> **Intrepid Ibex said:**
> Is it like so hard to compile a 64-bit version for Windows?

Yes.

[http://news.cnet.com/8301-30685_3-20006380-264.html](http://news.cnet.com/8301-30685_3-20006380-264.html)

..Adobe with their Flash doesn't help.

---

### Post by Mike_IronFist on 2010-08-23
> **Intrepid Ibex said:**
> Why is there (almost) always a additional 64-bit version of an application for linux but not for Windows, e.g. VMware Workstation, Firefox, Chromium, Thunderbird and VirtualBox.

Is it like so hard to compile a 64-bit version for Windows?
Compiling stuff on Windows is already hard to begin with.

On Ubuntu, for example, if you need to compile Visualboy Advance (which I did recently), you just go to Synaptic and install the -dev versions of certain libraries that that particular application uses. Basically, installing stuff like libsfml-dev. Once I have the needed -dev libraries installed, I can compile a 64-bit version, since I run a 64-bit version of Ubuntu. That's pretty straightforward, right?

On Windows, you have to get a compiler, get the libraries you need, and basically set up an environment that is ideal for compiling. And not only do you have to do all of this yourself, but you have to find the stuff you need on the internet, because Windows doesn't use package managers and does not come with compilers or any of that stuff.

Now, most Windows applications are 32-bit because 32-bit has been the standard for years, and 64-bit is getting way more popular, but 32-bit remains popular because you can use it on a 64-bit system. So basically, few people see the need to compile a 64-bit version when the 32-bit version works already, regardless of which version you run.

So to conclude:
1. Yes, it is hard to compile ANYTHING on Windows, compared to Linux.
2. 32-bit apps are still being phased out anyway.
3. Because 32-bit is still so popular and still works, it's a tough sell to try and convince people to compile 64-bit versions.

---

### Post by kahumba on 2010-08-23
I'm wondering why they haven't shipped a final 64 bit solution yet.
Arguments like they've been busy with other products don't fly since the flash source code is sooo much smaller (compared i.e. to Photoshop) but the strategic impact it yields is sooo big for Adobe.

---

### Post by Intrepid Ibex on 2010-08-24
@Mike_IronFist ah, okay. Some years ago I thought the source code of a Windows application would need to be changed in order to get a 64-bit version but later years I figured that's not the case.
But the question remained of why then is there often a 64-bit version for linux but not for windows and finally I created this topic.

About the 64-bit Flash it wasn't too hard how quickly that would come to the table. They say that it's gonna be added for both Windows/Linux in the next 'major version', which I guess is either "10.2.x" or "11.x".
It _might_ just be "11.x" so that they can tell everybody how huge the change was.

---

### Post by Npl on 2010-08-24
unlike Linux, Windows always has the compatibility layer for 32bit. Most Applications dont get anything from compiling them for 64bit. Only drivers need to be 64bit.

And compiling is harder, primary because there is no over imposed compiler like gcc and its toolchain. There are various versions of MS Compiler, Intels and gcc - getting objects/libraries compiled by a couple of them to work together aint always easy.

Linux aint a saint either, if you tried fixing up autotools and configure scripts =)

Its a different philosophy, on Windows you should just use a binary and leave compilation unless you can deal with the problems. On Linux you often have to.

---

### Post by Sockerdrickan on 2010-08-24
A little bit off-topic here. Anyone knows how to compile SDL 1.3 successfully for a Windows x86_64 target?

---

### Post by Intrepid Ibex on 2010-08-24
Isn't mingw64 + needed libraries enough?

---

### Post by Sockerdrickan on 2010-08-24
> **Intrepid Ibex said:**
> Isn't mingw64 + needed libraries enough?

I got really weird errors, I think it's SDLs fault.

If someone has built SDL 1.3 for a Windows x86_64 target please respond :popcorn:

---

### Post by Intrepid Ibex on 2010-08-24
K then, can't help. Create a separate topic; this one is already solved.

---

