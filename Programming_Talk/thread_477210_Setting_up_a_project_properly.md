---
title: "Setting up a project properly"
date: 2007-06-18
forum: Programming Talk
---

### Post by bsmith on 2007-06-18
I am starting to create a simple software 3d renderer, more for a learning experience than anything else, I have made one before, but as soon as it starts getting intricate it becomes a mess, with source files and headers all over the place. Anyway, I was looking at a few other open source apps and noticed how structured they all are,  and was wondering if there were any guidelines for setting up the folders and makefiles and stuff.

I'm using SDL, and gcc. Thanks in advance

---

### Post by KIAaze on 2007-06-18
I think the best way is to use an IDE and eventually an UML modeller like Umbrello for the classes.
Learning to use doxygen to automatically create user documentation can also help.

I currently use Anjuta for one of my projects and it automatically creates the autotools input files (configure.in, makefile.in/.am, etc) and places the files in the correct places:
src
include
doc
po
...

(right click in the left menu to add a file by specifying what kind of file it is and it will place it in the correct directory and create the directory if it doesn't exist yet (as well as modify the autotools files so that when you click "build distribution" it works correctly :) ))

For big object-oriented projects the UML (Unified Modelling Language) is extremely useful.
And Umbrello (available in the repositories) makes it easy to learn and use it.
It can import source code and generate the corresponding graph and also automatically generate source code for you fromn a graph. :)

Doxygen is a program which automatically generates documentation in several formats (latex, pdf, HTML, ...) and especially dependency graphs which can be quite helpful.

Note: Nothing prevents you from placing header files in the "src" folder instead of the "include" folder if you want to.
Personnally, I find it simpler to have both source and header files in the src folder, especially for classes.

---

### Post by bsmith on 2007-06-18
Thanks for the great info, so is this how everyone sets up there projects? I'll give Anjuta a go and see how it turns out this time, Thanks angin;)

---

### Post by KIAaze on 2007-06-18
I don't know if the pros do it like this, but that's how I currently do it. (for Anjuta and Doxygen at least. I know Umbrello, but I haven't used it in any real project yet.)
I'm still learning too. ;)

But we did indeed learn UML at my engineering school, so I think it's also something used in big projects. ^^

---

### Post by ankursethi on 2007-06-18
What about make, Subversion and Autotools? They don't exactly help you structure your project, but they ought to come in handy, no?

But I expect you already know that, since you seem quite experienced.

---

### Post by KIAaze on 2007-06-18
Yes, I should probably have mentioned Makefiles too. ^^'
But IDEs create them for you, which makes it easier.

Then there's also:
CVS, Trac, ...
Creating .deb packages, other packages...
Branch/tags system...
All the other IDEs: KDevelop, Eclipse, Code::Blocks...
Eventually GUI builders...

There's a lot too learn to work on open-source projects and not all is necessary. I'm still learning too and still don't know how to set up SVN and Trac instead of CVS on sourceforge for example. ^^

Personally I think that a good way to start having organized source code is using an IDE, altough it still requires a basic understanding of compiling, linking, makefiles and autotools to master the IDE completely even with the GUI. (so knowing the basics of gcc/g++ command-line options is necessary)

The first step to organizing source code is probably the Makefile.
But it's just easier to use an IDE once the project starts getting complex.
(altough the use of autotools (which IDEs also use) makes the Makefiles extremely complex to read. Manually written makefiles are usually clean and easy to understand in comparison.)

---

