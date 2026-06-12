---
title: "Compiling Python programs for Linux"
date: 2009-06-01
forum: Programming Talk
---

### Post by Volt9000 on 2009-06-01
I've recently been getting into Python, and really liking it. But it kind of bothers me that it's an interpreted language, as opposed to a native binary executable. Is there a way to compile a Python program into a native binary for a particular platform?

I know there's py2exe for Windows. Does something similar exist for Linux and MacOS?

Also, if I were to distribute Python bytecode (i.e. the .pyc files) are they easy to decompile?

So that begs the question-- does anyone use Python for commercial development?

---

### Post by crdlb on 2009-06-01
.pyc files are trivial to decompile, and that's what py2exe distributes. In the case of proprietary software (commercial software is not necessarily proprietary), you can simply not put it under an open source license. Compiling software is not a totally effective means of obfuscation anyway.

---

### Post by Volt9000 on 2009-06-01
No of course not, however if I wanted to distribute a Python app I've developed, I may not want to give out the original source. So other than giving the .pyc file, is there any way I can compile the source into a Linux binary?

---

### Post by crdlb on 2009-06-02
In that case, no, and as I mentioned above, you can't really on Windows either (py2exe is basically a python interpeter + the .pyc files bundled together). It should be possible to do something vaguely similar to py2exe for linux, but I'm not aware of anything.

---

### Post by sekinto on 2009-06-02
> **Volt9000 said:**
> I may not want to give out the original source.

Why does the source being visible or not visible even matter? Nobody can legally modify and redistribute it without your permission (because you are the copyright holder). That is, unless you license it, licenses modify the restrictions of copyright, some licenses like the GPL make it so that anyone can legally modify and redistribute your code as long as they give you attribution (and it also imposes the copyleft restriction, I don't think the LGPL does though). So if you license it just make sure you pick a license that works for you (or write your own).

---

### Post by Volt9000 on 2009-06-02
> **sekinto said:**
> Why does the source being visible or not visible even matter? Nobody can legally modify and redistribute it without your permission (because you are the copyright holder). That is, unless you license it, licenses modify the restrictions of copyright, some licenses like the GPL make it so that anyone can legally modify and redistribute your code as long as they give you attribution (and it also imposes the copyleft restriction, I don't think the LGPL does though). So if you license it just make sure you pick a license that works for you (or write your own).

Understood, but I'd still like to know if there is a way to at least pack my code along with the interpreter into a single, portable binary executable.

---

### Post by ssam on 2009-06-02
every modern linux system has python installed on it. just check that your ode works on versions 2.5 and 2.6 (maybe 2.4 if you want it to work on old systems).

including your own python into the package will make it bigger (maybe about 10MB bigger), slower (the system python will have already been loaded into ram by the time the computer boots, loading a second python is a waste of time and ram), and you need to update you package for things like security updates in python.

why don't you talk to the guys at CNR.com. they package software up for all the major distros.

also if someone wants to break, modify steal etc your software then they will find a way, even if it is all pre-compiled. if you start obfuscating your code, it will likely mean it does not work so well for legitimate users.

---

### Post by unutbu on 2009-06-02
For Linux, perhaps freeze.py is what you are looking for:
[http://mail.python.org/pipermail/tutor/2008-January/059909.html](http://mail.python.org/pipermail/tutor/2008-January/059909.html)
[http://wiki.python.org/moin/Freeze](http://wiki.python.org/moin/Freeze)

(PS. everyone here has given good reason for not using freeze... and I agree with them :))

---

### Post by Volt9000 on 2009-06-03
Ah yes, freeze is what I was looking for.

However based on all the comments that I see flying around, I shouldn't even bother with it.
Ok so my next question-- how can I distribute my Python program in a single package? I'm going to have several .py files floating around, I wonder if there's a way for me to merge them all into a single file?

---

### Post by CptPicard on 2009-06-03
Seriously, this is a FAQ that pops up every now and then and is based on the strange idea that Linux works like Windows does. The short answer is that if everyone distributed stuff the way you expect to, Linux systems would become awful messes with everyone shipping their own python and all that.

Linux distributions are built around dependency-managing package managers for a very good reason. There is absolutely no reason not to make use of them, and if your software doesn't play nice with them, I would not use whatever you have to offer. To answer the question on how you should go about this... see how to build .deb packages for Ubuntu/Debian (or RPMs for red hat or whatever..)

---

### Post by Volt9000 on 2009-06-03
> **CptPicard said:**
> Seriously, this is a FAQ that pops up every now and then and is based on the strange idea that Linux works like Windows does. The short answer is that if everyone distributed stuff the way you expect to, Linux systems would become awful messes with everyone shipping their own python and all that.

Linux distributions are built around dependency-managing package managers for a very good reason. There is absolutely no reason not to make use of them, and if your software doesn't play nice with them, I would not use whatever you have to offer. To answer the question on how you should go about this... see how to build .deb packages for Ubuntu/Debian (or RPMs for red hat or whatever..)

Ok, I understand. No need for a self-contained Python interpreter+program.

But what about my second question, about throwing all my files together? I think a .deb package would be a bit overkill in my case. I don't plan to distribute this package widely or anything, maybe give it to a few friends. But it just seems to me that handing out a .tar.gz file with a bunch of .py files in it, asking to extract to an empty directory, then executing a specific .py file seems a bit messy.

I understand the point that .deb packages automate this whole process the user doesn't see anything that happens in the background, but I still can't wrap my mind around that method. I guess this is what being with Windows development for too long does to me.

Is this how some packages are distributed, though? All wrapped in a .deb which just automatically decompresses itself and copies all files to its own dir?

---

### Post by CptPicard on 2009-06-03
Well, for a Linux user the .tar.gz method does not sound all that bad IMO if you insist on not creating a package...

And btw, package managers do not (necessarily/generally) put separate packages into their own directories, the Linux directory layout is a bit more complex -- for example, executables and data and libraries go under their own parts of the hierarchy... this is actually a reason why package managers are important, they keep track of what has been installed where.

---

### Post by EXCiD3 on 2009-06-04
[Pyinstaller ]("http://www.pyinstaller.org/")can create executables for Linux if you needed everything to be in one. This could be good if you intended to release it for any OS whether or not Python was installed. I will be using it for the next release of Keryx (a portable cross-platform application that runs from USB drives)

---

### Post by Volt9000 on 2009-06-04
Alright, thanks for your replies, everyone!

---

### Post by delfick on 2009-06-04
[http://peak.telecommunity.com/DevCenter/PythonEggs](http://peak.telecommunity.com/DevCenter/PythonEggs) :)

(I've never used them myself, but they appear to be what you want :))

---

