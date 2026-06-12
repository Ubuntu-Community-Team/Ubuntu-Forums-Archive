---
title: "Why are so many programs written in C?"
date: 2010-08-08
forum: Programming Talk
---

### Post by SpinningAround on 2010-08-08
I looked around at a few programs (totem, gedit, pidgin, empathy, gnome) and notice that many of them are written in C and not C++, is there a explanation for this?

---

### Post by DrMelon on 2010-08-08
C is very extensible, and also has a lot of support on varied platforms - for example, embedded devices.

---

### Post by dv3500ea on 2010-08-08
C is used mainly for it's compiled speed. You will find lots of programs that have their libraries in C, for speed, and their interfaces in dynamic languages such as python for their speed of development (they are generally easier to work with and have a more elegant design).

---

### Post by lisati on 2010-08-08
Have a look [here]("http://en.wikipedia.org/wiki/C_%28programming_language%29"), it's interesting reading.

---

### Post by Bachstelze on 2010-08-08
> **SpinningAround said:**
> I looked around at a few programs (totem, gedit, pidgin, empathy, gnome) and notice that many of them are written in C and not C++, is there a explanation for this?

Because a lot of people hate C++.  Perhaps not as much as [Linus]("http://article.gmane.org/gmane.comp.version-control.git/57918"), but close.

---

### Post by nvteighen on 2010-08-08
Mainly because you cited GNOME applications... KDE applications tend to be C++ because Qt is written in that language. GTK+ is a C library... ok, it has C++ bindings, but well...

Bah, there's also the fact that Linux being written in C forces you to use that language in order to interface with the kernel. That's why most system utilities are also written in C... (also, because you wouldn't need 90% of C++'s features).

---

### Post by worseisworser on 2010-08-08
> **SpinningAround said:**
> I looked around at a few programs (totem, gedit, pidgin, empathy, gnome) and notice that many of them are written in C and not C++, is there a explanation for this?

[http://yosefk.com/c++fqa/](http://yosefk.com/c++fqa/)

Some think C++ has more C than ++ in it for it to be safe/sane/nice to use. The amount of abstraction provided isn't backed up by enough power in the run-time and tool department; it is delivering promises with regards to benefits and convenience it cannot keep or maintain in the long run.

I.e., it isn't worth the effort; it's still C, but with stuff added on top without enough bottom/mid-level support making things brittle as a whole. This lack of support makes debugging, introspection and use (and development) of tools in general significantly harder, and ultimately it isn't worth it as a whole; considering the entire picture.

People sometimes skip past C++ and jump straight to a HLL with a run-time/VM backing it. They want a language and/or an environment with support for advanced debugging and introspection, and safety; GC and freedom from [memory corruption]("http://en.wikipedia.org/wiki/Memory_corruption"), so it is possible to examine the state of a program when something goes wrong without having the very foundational hallways of their creation themselves completely warped in an unrecognizable time/space (or something) random noise/garbage type fashion making navigation and finding the original or real problem impossible.

---

### Post by trent.josephsen on 2010-08-08
@worseisworser:  Nice assessment.

@OP:  Your question is rather like asking, "I see a lot of programs are written in Java and not Perl; is there a reason for that?"  C and C++ are different languages; C++ is not really a successor to C, despite their occasional superficial similarities.  People write in C because they know C and like C; if you know and like C++, there's no reason you shouldn't use it for an appropriate application.

---

### Post by SpinningAround on 2010-08-08
Thanks for all the answers, it make a little more sense now :)

---

