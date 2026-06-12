---
title: "C++ or Pascal compiler"
date: 2005-10-30
forum: Programming Talk
---

### Post by dave164 on 2005-10-30
Is there a C++ and / or pascal compiler for breezy? If so what is the repository address / link

Cheers,
Dave164

---

### Post by oldmanstan on 2005-10-30
g++ is a C++ compiler (part of gcc, gnu compiler collection, formerly gnu c compiler)

sudo apt-get install build-essential

or

use synaptic to install the build-essential package

this package includes all the stuff you need

gpc is the gnu pascal compiler, use synaptic and search for it

---

### Post by wmcbrine on 2005-10-31
For Pascal, there's also Free Pascal ( [http://www.freepascal.org/](http://www.freepascal.org/) ) -- very useful if you want to port old Borland/Turbo Pascal code.

---

### Post by wmcbrine on 2005-10-31
please delete

---

### Post by dave164 on 2005-10-31
Hey, thanks ive installed them in synaptic, but how do i then run them :(

Sorry

Also when i try to install FreePascal i install the rtl then the gtk and the gtk says that the rtl is not installed...

---

### Post by oldmanstan on 2005-10-31
i've never used either of the pascal compilers mentioned but they should work the same as gcc / g++

you can use g++ from the command line, open up a terminal window in gnome or whatever you use and type ```
g++ --help
```

that will give you a basic overview of what you need to compile a simple program, you can also get anjuta (search synaptic) which is an IDE and works a little more like what you're probably used to in windows, see the help files for how to use anjuta

---

### Post by dave164 on 2005-10-31
re there any visible compilers like turbo pascal were you can see it all happening, or am i just silly :P

---

### Post by mostwanted on 2005-10-31
You mean like an IDE? try Anjuta or Kdevelop.

---

### Post by oldmanstan on 2005-10-31
[QUOTE=dave164]re there any visible compilers like turbo pascal were you can see it all happening, or am i just silly :P[/QUOTE]
using a compiler from the command line still allows you to see error messages, etc.  not really sure what you mean by "visual" but probably an IDE (integrated development environment) get anjuta (or kdevelop, good call on that one) then just use the help files to figure out what exactly to do (in anjuta F9 and F11 are compile and build and F3 runs your app)

---

### Post by LorenzoD on 2005-10-31
[QUOTE=dave164]re there any visible compilers like turbo pascal were you can see it all happening, or am i just silly :P[/QUOTE]

For Pascal/Object Pascal there's lazarus ([http://lazarus.freepascal.org](http://lazarus.freepascal.org)) which is a bit similar to delphi/kylix. It's not in the repositories yet, and honestly it was a bit unstable last time I tried it. If you're feeling a bit adventurous you could give it a try.

---

