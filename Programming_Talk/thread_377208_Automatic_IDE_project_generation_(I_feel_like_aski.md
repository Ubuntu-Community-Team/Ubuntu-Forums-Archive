---
title: "Automatic IDE project generation? (I feel like asking a clueless question)"
date: 2007-03-05
forum: Programming Talk
---

### Post by Mr. Picklesworth on 2007-03-05
I have finally taken the plunge and started a mad frenzy of downloading Gnome development packages in the hopes of eventually totally rejigging Epiphany's bookmarks system to something more awesome.
All has gone well and I have Epiphany compiling, etc., but I have hit a spot where I wonder if it could be better...

What I have is Epiphany's source code, with the Makefile and all that fun stuff, but pretty much the only way I can edit it is opening up individual files in an IDE that has no real clue about their connection to a single cohesive project. This is a bit of a shame, because the IDEs (note: I am obsessed with IDEs) I've found have some cool features that are available for projects and I am simply too lazy (and stubborn) to simply set up a project file myself!

I know it's a long shot, but is there some kind of magical software that will read through Makefiles, Includes, Imports and the like to determine a sane and useful project file for an IDE? (Hopefully Anjuta, though anything will do as long as that IDE is not an unnecessarily slow and bloated one *chough*Ecli*cough*).

Edit:
Hrm... From the Anjuta FAQ:
> I already have a project tree. How do I use Anjuta ?

If your project is autoconf/automake based, simply run File->New->Project from existing sources to import your project.Trying shortly! (And they web site desperately needs an overhaul).

---

### Post by cronholio on 2007-03-06
If it fails (which may be the case in my experience - Anjuta has really deteriorated over the last few releases) you can always ask the Epiphany developers what they used and if they have a project file for you.

---

### Post by Pankrat on 2007-03-06
The only thing that worked for me (even it is far from perfect) ... you know ... was Eclipse/CDT. Create project from CVS and select Standard C/C++ Make project. Then run autogen.sh/bootstrap and configure (or whatever configuration type they use) from the command line.

Don't know if this is going to work with a GNOME project, though, as they have their own way of doing things. Anjuta might be better choice here, haven't used it for quite a while as I couldn't see a big difference to Eclipse when it comes to "bloatliness". Now I use vim most of the time ...

---

