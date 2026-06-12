---
title: "C/C++ Development Tools"
date: 2006-04-20
forum: Programming Talk
---

### Post by larry on 2006-04-20
Dear All,
I am starting to programming in C/C++ (mainly scientific programming in order to to some number crunching).
I am a bit confused about which development tools I should use: Emacs, an IDE, etc...
For the codes I am using right now, I would need mainly a text editor with syntax highlighting and able to easily call the compiler.
Gedit would be ideal (for now) if I did not have to keep a separate terminal open.
Someone is radical and tells me to switch to KDE, which allegedly has more developing tools.
Kate could be close to what I need, but I do not know if there is already a Gnome application which is suitable for me.
I tried Anjuta as an IDE, but I did not fall in love with it (apt does not install all of the needed dependencies and I had to ask for help to get it working) and it is by far beyond what I need now.
BTW, I am running dapper beta.
Many thanks

Larry

---

### Post by toojays on 2006-04-20
It sounds like you just need to learn more about Emacs. Turn on syntax highlighting with "M-x global-font-lock", and use "M-x compile" to build your project.

---

### Post by larry on 2006-04-20
Thanks for the suggestion.
Is it difficult if you want to use under Emacs your own file with instructions about how to compile the source code, what libraries to link it to, etc...?

Larry

---

### Post by toojays on 2006-04-20
The standard way to do that is to use a Makefile. By default, "M-x compile" will run "make -k". You can then jump to the location of errors with "C-x `"

It's quite nice once you get the hang of it, because it's so versatile. For instance, I have a C++ project which uses Doxygen for documentation. With a single interface "M-x compile", I can build the binaries, or build the documentation, and jump to errors the same way. I have another project which uses the GNUPIC assembler. Again, "M-x compile", and "C-x `" to jump to errors. It takes a bit of time to learn, but once you get it, you can reuse it for just about anything. Very elegant.

---

### Post by MichaelZ on 2006-04-20
[quote=larry]
I am starting to programming in C/C++ (mainly scientific programming in order to to some number crunching).
I am a bit confused about which development tools I should use: Emacs, an IDE, etc...
For the codes I am using right now, I would need mainly a text editor with syntax highlighting and able to easily call the compiler.
Gedit would be ideal (for now) if I did not have to keep a separate terminal open.
[...]
I tried Anjuta as an IDE, but I did not fall in love with it (apt does not install all of the needed dependencies and I had to ask for help to get it working) and it is by far beyond what I need now.
[/quote] 
Hello,

May be you can give a try to [CodeBlocks]("http://www.codeblocks.org"). It is an open-source and cross-platform C/C++ IDE which supports different compilers. The easy way to give it a try is to download a pre-compiled .deb package (see my signature).

Best wishes,
Michael

---

### Post by Kimm on 2006-04-20
Even though I dont run KDE I have falled in love with KDevelop, I find it more stable than anjuta, and that it has more features. Just find a nice theme for it and it will blend in nicely.
Another nice IDE is monodevelop, I trust Dapper has a fairly new release in the repositories so why dont you give that a spin.

KDev in XFCE:
[[IMG]http://img215.imageshack.us/img215/6458/kdevxfce1mk.th.png[/IMG]](http://img215.imageshack.us/my.php?image=kdevxfce1mk.png)

Monodevelop:
[[IMG]http://img58.imageshack.us/img58/8551/monodevxfce8zx.th.png[/IMG]](http://img58.imageshack.us/my.php?image=monodevxfce8zx.png)

---

### Post by mostwanted on 2006-04-21
[QUOTE=Kimm]Even though I dont run KDE I have falled in love with KDevelop, I find it more stable than anjuta, and that it has more features. Just find a nice theme for it and it will blend in nicely.
Another nice IDE is monodevelop, I trust Dapper has a fairly new release in the repositories so why dont you give that a spin.

KDev in XFCE:
[[IMG]http://img215.imageshack.us/img215/6458/kdevxfce1mk.th.png[/IMG]](http://img215.imageshack.us/my.php?image=kdevxfce1mk.png)

Monodevelop:
[[IMG]http://img58.imageshack.us/img58/8551/monodevxfce8zx.th.png[/IMG]](http://img58.imageshack.us/my.php?image=monodevxfce8zx.png)[/QUOTE]

Monodevelop is for Mono languages (C#, Java, Boo, Nermerle), not C/C++.

---

### Post by Kimm on 2006-04-21
Mostwanted, Monodevelop works nicely for C/C++ developement (if you look at the screenshot you will see that it has a C++ Source File open).
If I remember correctly it will even allow you to start C++ projects in the project menu... but I'm not by my computer so I cant check.

Edit: I stand corrected. Monodevelop will edit C and C++ files with synthax highlighting but it will not compile the code.
but with a separe terminal and a script like this:

#!/bin/bash
g++ <nameoffile>.cc -o <nameoffile>

will simplify the build process somewhat.

---

### Post by cro.smiley on 2006-04-21
You could try Anjuta. ([http://www.anjuta.org]("www.anjuta.org"))

Sorry I didn't notice you already tried

---

