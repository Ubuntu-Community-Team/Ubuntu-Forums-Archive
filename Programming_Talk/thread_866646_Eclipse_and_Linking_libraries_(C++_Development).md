---
title: "Eclipse and Linking libraries (C++ Development)"
date: 2008-07-22
forum: Programming Talk
---

### Post by rba1988 on 2008-07-22
When compiling source code, I'm used to typing "g++ -g -o [program_name] *.cpp -l[library name]. I've recently tried out Eclipse IDE for C++ development and svn commiting system (for syncing code). Unfortunately I haven't been able to compile my C++ code because it requires to be linked to certain libraries. How do I tell Eclipse to link these certain libraries (the -l equivalent). Thanks in advance.

---

### Post by ceclauson on 2008-07-22
I'm sort of new to C++ in Eclipse myself, but I might be able to help.

Eclipse offers two project types, standard make and managed make.  If you're doing a standard make project, then you write you own makefile (called simply "Makefile") in the project folder.  You can put whatever compiler options in there that you need to build your project.

Of course, if you're not comfortable with Makefiles, this isn't much help.  In that case, you'd do a managed make project (I'm assume), and hopefully someone more knowledgable than I am can fill in how to add libraries to the build path this way.

If you're interested in trying the standard make option, though, and aren't comfortable with makefiles, here's the code from (a simple!) one of mine that should illustrate the idea:

```

.PHONY = all

all:
	g++ main.cpp -lmozjs

```

The fourth line is simply the command that's run to build the project.

---

### Post by hellz99 on 2009-02-04
I just went through this same thing.  Recently started a C project that uses a few linux libraries and had trouble linking them in eclipse.  In case anyone else needs the help, [here's a tutorial]("http://whatwouldnickdo.com/wordpress/328/eclipse-cdt-and-linux-libraries/").

---

