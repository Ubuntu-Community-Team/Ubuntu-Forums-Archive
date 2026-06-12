---
title: "What programming language does Linux mainly consist of?"
date: 2007-12-16
forum: Programming Talk
---

### Post by ameba on 2007-12-16
i

---

### Post by finer recliner on 2007-12-16
lots of C and python

---

### Post by ameba on 2007-12-16
T

---

### Post by samjh on 2007-12-16
The Linux kernel is mainly written in C, with some hard-ware specific code using Assembly.

The command-shell is usually Bourne Again Shell for most Linux distros (ie. bash).

The X11 windowing system, on which most graphical environments are written on, is written in C.

For desktop environments, the languages are almost always C or C++.  Gnome's core systems are written using C, with some projects using C++, and recently some C# and Python for miscellaneous projects.  KDE's core systems are written using C++, with some external projects using Python.  XCFE is still almost completely written in C++.

For Linux application software, there are many varied languages used across many projects.  According to statistics at Freshmeat and Sourceforge, most FOSS projects are written using C, C++, and Java.  Contrary to what some people might say, Python still only a minority language, but its popularity is increasing sharply.  C# is also making inroads thanks to some significant projects by Novell and the Mono project team.

---

### Post by ameba on 2007-12-16
Wow

---

### Post by pmasiar on 2007-12-16
As samjh explained, you need to distinguish between Linux the kernel (which is in C with small bits of ASM, IIUC), and linux-based distro like ubuntu, which adds thousands of packages running on top of kernel, and written in many different languages for different (partly historical, partly developers' preferences) reasons.

Recently, Python became more popular, and rather big part (I am not sure, but I guess still not all) of code traditionally written in C, like windows manager and desktop, was written in Python for Sugar/OLPC.

---

### Post by Wybiral on 2007-12-16
Tons of applications for ubuntu are written in python, while most of the libraries are written in C and C++ (such as gtk and qt).

---

### Post by Majorix on 2007-12-16
Kernel is written in C. Applications are mostly in Python.

---

### Post by LaRoza on 2007-12-16
> **Majorix said:**
> Kernel is written in C. Applications are mostly in Python.

Applications are mostly in C, and depending on the app, Python, Perl, Java, C# etc are used.

---

### Post by Majorix on 2007-12-16
Could you provide a link please?

---

### Post by Jessehk on 2007-12-16
> **Majorix said:**
> Could you provide a link please?

Maybe he will after you provide a link for your first claim.

---

### Post by CptPicard on 2007-12-16
> **Majorix said:**
> Could you provide a link please?

I suppose she *could* give you links to the sources for all the Ubuntu packages so you could go check out for yourself, but you're able to do that without. :) 

Really, Python isn't nearly as widely used as some people make it seem like... Ubuntu devs might favour Python for Ubuntu's internal development, but you have to realize that this is the distribution integration stuff, not application development.

Now, this once again does not support your thesis that Python is either an eternal beginner language or the be-all, end-all language, mind you...

---

### Post by pmasiar on 2007-12-16
For obvious reasons (fitness tor the task, personal preferences, history) Python is NOT most used language. It could be used for many more projects (not sure if for most - probably not), if all projects would be starting now from scratch, and all developers liked Python, but fat chance of that :-)

Python is main language used in Canonical and for internal ubuntu development, but most of 20K debian packages are in languages other than Python, and it is not going to change anytime soon (and there is good reason why not).

For extra credit, adventurous reader can parse debian package info, extract implementation language for each package, and run some stats on that. MOTUs will help you with parsing :-) If you do, post results promonently - it would be interesting factoid to know - even if 100% useless and meaningless.

BTW this could be good training project for an aspiring ubuntu developer.

---

### Post by LaRoza on 2007-12-16
> **Majorix said:**
> Could you provide a link please?

[http://www.gnu.org/prep/standards/standards.html](http://www.gnu.org/prep/standards/standards.html)

I imagine it is followed most of the time :)

Naturally, Java is found in some apps (OO), C# is others (FSpot?), and Perl in some (FrozenBubble) and Python in a few (Ubuntu installer), but C is the *nix language, and was in fact built for such programming.

---

### Post by samjh on 2007-12-16
While this is not a definitive measure of programming language popularity, it's a reasonably good indicator:
[http://freshmeat.net/browse/160/](http://freshmeat.net/browse/160/)

Also you can search projects by programming language at Sourceforge.
Projects incorporating:
Java = 29636
C++ = 24767
C = 21067
Python = 8066
C# = 7294

---

### Post by Majorix on 2007-12-16
> **LaRoza said:**
> [http://www.gnu.org/prep/standards/standards.html](http://www.gnu.org/prep/standards/standards.html)

I imagine it is followed most of the time :)

Naturally, Java is found in some apps (OO), C# is others (FSpot?), and Perl in some (FrozenBubble) and Python in a few (Ubuntu installer), but C is the *nix language, and was in fact built for such programming.

God knows how many pages that has haha! I was talking of a table-like page, if possible. I always liked stats and measurement :D

---

### Post by LaRoza on 2007-12-16
> **Majorix said:**
> God knows how many pages that has haha! I was talking of a table-like page, if possible. I always liked stats and measurement :D

Well, the page says that GNU software should be written in C, and gives what version to use, and what style to use.

If you like stats and measurement, I don't have them, but you could always look at the source of each OS app on Ubuntu (which is all of them, by default)

(C is not a requirement, just widespread. Developers can use any language they want)

---

### Post by pmasiar on 2007-12-16
Yes, GNU standard is C, but ubuntu distributes also even more non-GNU projects which are independent from GNU, and they can be in any language developers prefer.

---

### Post by jpkotta on 2007-12-17
I'd say it is overwhelmingly C.  Even if most applications/projects were not written in C, the core is.  Linux kernel, GCC and toolchain, glib, GTK, X, Bash, etc.  Not to mention the Python and Perl (and many other) interpreters.  If you write a little Python app, it is basically a wrapper around a huge base that is written in C.  

I'm not saying that any language is better than another, I'm just saying we should assign more weight to pieces of the core, and those are mostly written in C.

---

