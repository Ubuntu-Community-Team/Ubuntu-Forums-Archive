---
title: "Help compiling a scilab 3.1.1 deb"
date: 2005-12-17
forum: Packaging and Compiling Programs
---

### Post by NeTo on 2005-12-17
I was attemping to compile deb files for scilab 3.1.1 using as a base the diff file from breezy. After some tweaking I got to the point where everything compiles and the deb files are successfully created.

Sadly, after installing them, I noticed scilab refused to run. The following is displayed:```
        -------------------------------------------
                         scilab-3.1.1

                  Copyright (c) 1989-2005
              Consortium Scilab (INRIA, ENPC)
        -------------------------------------------


Startup execution:
  loading initial environment

```And then, it simply exits with no error messages or warnings.

But, if I use the -ns option, scilab runs correctly. Maybe there is something wrong with the startup script?

Can someone give me a hand? 

You can find all files I have been playing with (.debs, the tweaked diff, sources, etc.) [here](http://netosoft.no-ip.org/Ubuntu%20-%20Breezy/scilab/).

---

### Post by NeTo on 2005-12-17
I will answer this one myself :KS

It seems scilab doesn't compile well with gcc4. I mean, it compiles, but nothing else. Modifying the debian/rules file to use gcc3.4 solved the problem :p

If you want to test the scilab 3.1.1 package (with the gtk2 interface) you can download the deb files from the link above. It seems to be working fine so far.

I will post a howto on this hopefully tomorrow. It's 4am, so I really need some sleep now.

---

