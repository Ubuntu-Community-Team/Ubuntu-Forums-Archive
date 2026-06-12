---
title: "Linking to GTK, Poco under Eclipse CDT?"
date: 2008-01-01
forum: Packaging and Compiling Programs
---

### Post by Ansible on 2008-01-01
I'm pretty close to getting a program to build and run under eclipse CDT - its a GTK program I wrote on windows, now I'm trying to get it to compile on linux.  

At this point I've got it to compile, I've found all the correct include dirs and etc.  But it fails on the link step.  I get a lot of errors like this:

/home/bburdette/eclipse_workspace/TimeKeeper/Debug/../TimeKeeper.cpp:170: undefined reference to `Poco::Timespan::Timespan(long long)'

And this:

/home/bburdette/eclipse_workspace/TimeKeeper/Debug/../main.cpp:663: undefined reference to `gtk_file_selection_new'

So obviously poco and gtk libs aren't being linked in.  How do I specify which libraries to use?  It looks like the poco libs are in /usr/lib, for instance this is there:

/usr/lib/libPocoFoundation.so

But it doesn't work to specify /usr/lib as the lib search path and libPocoFoundation.so under 'libraries' (on the GCC Linker options for the project).  It just says file not found and stops the link.  I'm sure the gtk libs would work similarly.

---

### Post by plugwash on 2008-01-02
I suspect when specifying the library name you need to leave off the lib at the start and the .so at the end.

---

### Post by Ansible on 2008-01-02
Cool, that fixed it!

---

