---
title: "Question about dependencies"
date: 2007-02-01
forum: Packaging and Compiling Programs
---

### Post by david.rahrer on 2007-02-01
This may be incredibly basic, but when I compile a program using ./configure, make, make install, and during configure it asks for a dozen programs to be installed so it can compile, are those dependencies (programs) then needed if I install the program in the same machine?  Or are these just necessary on the machine I compile on so it will properly compile?  I was just wondering if I can get rid of a lot of extra stuff installed during these compiles.  Thanks.

---

### Post by lloyd_b on 2007-02-01
> This may be incredibly basic, but when I compile a program using ./configure, make, make install, and during configure it asks for a dozen programs to be installed so it can compile, are those dependencies (programs) then needed if I install the program in the same machine? Or are these just necessary on the machine I compile on so it will properly compile? I was just wondering if I can get rid of a lot of extra stuff installed during these compiles. Thanks.

I'm afraid the answer to that one is ... it depends (Sorry, couldn't resist).

Some of those requirements may be "build tools", i.e. things that are required for the compile processes, such as moc (meta-object compiler), which is needed to compile the program, but not to run it.  Others may be "development headers", i.e. ".h" files needed for different libraries that are required by the program that you're trying to compile, but which aren't needed once the program is compiled and installed.

On the other hand, it may be asking for shared libraries, i.e. ".so" files.  In this case, you most likely need those libraries to run the program, as well as compile it, so you'll have to install the libraries and leave them installed in order for the program to work.

Sorry, there's no straight answer to that question.  There are just too many possibilities...

Lloyd B.

---

### Post by raul_ on 2007-02-01
That is the so called "dependency hell". Very famous some years ago. Now the packaging tools like apt can solve that automatically

---

### Post by david.rahrer on 2007-02-01
Ah, yes I've heard that term :)  So if I really don't want a lot of extra garbage, I could have a separate Ubuntu install and use it just for compliling stuff?  I'm using checkinstall for the last part, so it will create a deb.  Would installing that automatically install the missing deps if I tried on a separate Ubuntu installation?

---

