---
title: "Monodevelop 0.13.1 version control hates me!"
date: 2007-06-04
forum: Programming Talk
---

### Post by Mr. Picklesworth on 2007-06-04
Never mind, it's fixed. I had to add --enable-subversion as an argument to the configure script, then recompile it. SVN hates me, but it does work.


I have installed Monodevelop 0.13.1 from source. All has gone well: It opens and I have successfully progressed through developing my first reasonably adventurous program with Mono :)
Fantastic IDE, by the way!

Just now I was reminded of the cool looking Version Control add-in, so I started an SVN repo on Google and opened up Version Control -> Publish for my project.

But here comes a (hopefully simple) problem! Under Connect to Repository and Add Repository (anything to do with repositories), the Type combo box, which I assume holds the types of repositories I can connect to, holds nothing.

From the looks of it, the program's dependencies are satisfied. Monodevelop 0.12's dependencies, as well as those of monodevelop-versioncontrol 0.12 are definitely satisfied since I had that installed previously from the Feisty repos (and it configured fine, installing the add-in). Looking at the Add-In manager, it has its dependencies satisfied and should work.

I guess the problem is that the program is looking for special libraries, to connect to version control systems, that just aren't there, yet it is coded in such a way that it doesn't mind their nonexistence. (Even though the lack of /any/ of them renders the add-in useless).

Googling it isn't being helpful, so perhaps you have seen this before?

Thanks in advance!

---

