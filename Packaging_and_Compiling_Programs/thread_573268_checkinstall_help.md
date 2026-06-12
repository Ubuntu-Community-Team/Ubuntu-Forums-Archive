---
title: "checkinstall help"
date: 2007-10-11
forum: Packaging and Compiling Programs
---

### Post by fourthdimension on 2007-10-11
I'm at a loss for how to use checkinstall.  I have a single source file (C++) without a makefile.  I've tried all sorts of different tutorials, but all I get is ```
make: *** No rule to make target `install_packages'.  Stop.

****  Installation failed. Aborting package creation.

Cleaning up.../usr/bin/checkinstall: line 300: [: too many arguments
OK

Bye.

```

I've cd'd into the right directory, and I've compiled the package.  I've run ./configure also.  Then I type "checkinstall" and I get the above error.  Could anyone tell me how I'm supposed to use it?  Is a makefile necessary (if so, how would I make it from the source?)?

On a sort of side note, I downloaded the kobo deluxe source files from the repositories and edited them, but I don't know how to install them because there are two different makefiles.  ... well, maybe that problem will be answered in the process.

One last question - when I write my own programs, I only create a  single source file.  How do I create all the other files needed in order to convert the source into a deb?

Thanks.

---

