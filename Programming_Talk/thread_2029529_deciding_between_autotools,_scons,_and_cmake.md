---
title: "deciding between autotools, scons, and cmake"
date: 2012-07-19
forum: Programming Talk
---

### Post by PGScooter on 2012-07-19
I've searched and have found some threads on this topic but they are a few years old (I post them at the end of this message for reference).

I would like to eventually become a significant contributor to some open source C++ cross-platform projects. I guess in the end the answer will depend on whatever those projects use but 1) I'm not sure which projects I'm interested in and 2) Many projects use two (or even all three!) of those so I might have my choice.

I get the feeling that cmake is becoming more popular. Is that true? In 5 years, will most open source C++ cross-platform projects use scons, cmake, or autotools?

Below I paste previous threads from 2008 and 2009 on this topic:
[http://ubuntuforums.org/showthread.php?t=692692&highlight=cmake+autotools](http://ubuntuforums.org/showthread.php?t=692692&highlight=cmake+autotools)
[http://ubuntuforums.org/showthread.php?t=520015&highlight=cmake+autotools](http://ubuntuforums.org/showthread.php?t=520015&highlight=cmake+autotools)
[http://ubuntuforums.org/showthread.php?t=976922&highlight=cmake+autotools&page=2](http://ubuntuforums.org/showthread.php?t=976922&highlight=cmake+autotools&page=2)
[http://ubuntuforums.org/showthread.php?t=1190584&highlight=cmake+autotools](http://ubuntuforums.org/showthread.php?t=1190584&highlight=cmake+autotools)
[http://ubuntuforums.org/showthread.php?t=1112266&highlight=cmake+autotools](http://ubuntuforums.org/showthread.php?t=1112266&highlight=cmake+autotools)

---

### Post by PGScooter on 2012-07-21
bump.

---

### Post by PGScooter on 2012-07-27
bump

---

### Post by scu-ba-de-buntu on 2012-07-28
bump.

...

Check out autotools/GNU build system. This is fairly ubiquitous, even if its rather old. Note that this does not mean its the best. Just what I personally found useful to know. You could even help revive an old project that people wish was being updated. Afterwards, learn whatever your team is using - it might not be any one of those three (m4, custom scripts, etc). Of course you could also scan through a couple tutorials on each of them for the cost of a couple minutes.

---

### Post by PGScooter on 2012-07-30
scu-ba-de-buntu --

Thank you for your response. I understand that the answer will depend on the project. However, that's exactly the point is I don't know what project I'll be interested in 5 years from now so I'm wondering what the best chances are. I'm interested in a long-term investment.

---

### Post by GeneralZod on 2012-07-30
I've not had much experience with autotools (and none at all with scons), so I'll advocate for CMake.

CMake definitely seems to be gaining traction: I've lost count of the number of projects that have either switched to it or are seriously considering it (with the entirety of the KDE project being one of the more famous examples).  When you think of how much work it is to port an old, large project to a new build system, it says a lot that so many people thought it was worth the effort.

A brief anecdote, first: I'm currently working on a C++ + KDE project ("KListings") as a means to practice [Test-Driven Development](http://en.wikipedia.org/wiki/Test_driven_development), and along the way I've been working on a support library consisting of both C++ classes and a substantial amount of CMake packages and functions to enable unit testing of code and integrate nicely with Google Test and Google Mock.  Yesterday, I decided I'd try to take what I have and compile it using Visual Studio on Windows.

After booting up Windows and installing VS, CMake, Google Test + Mock, and the MSVC version of [KDE on Windows](http://windows.kde.org/), I used CMake to generate a Visual Studio project file from my project's CMakeLists.txt.

Everything worked (mostly) flawlessly, without a single change to my extensive collection of CMake scripts and libraries: The Visual Studio project correctly listed my support library as a dependency of KListings and built and linked it automatically; etc.  All of the flaws could be traced back to the packaging of KDE on Windows (missing debug version of Qt libraries; some hard-coded path names (["N:/"](http://old.nabble.com/automoc4-crash,-where-does-N:\lib-path-comes-from,-and-kdewind-for-msvc-td30970436.html)) that apparently come from the build server; etc).  I was pretty amazed by how well it worked, to be honest: I had made no effort to ensure that this would all work under any OS but Linux.

Anyway, here are some good features of CMake, from my point of view; I don't know if I can call them "advantages", as the other projects may have them, too :)

- Backed by an active and responsive commercial company ([Kitware](http://www.kitware.com/)) 
- Reasonably rich, built-in (and so nicely consistent, standardised and interoperable) libraries for performing such common takes as file querying/ manipulation, regex's etc
- Built-in, decently consistent and standardised set of packages for finding and utilising a broad range of common libraries (see the Find* packages, [here](http://cmake.org/gitweb?p=cmake.git;a=tree;f=Modules;h=e5e046d2325801885c63b91eac4805e643fb0352;hb=HEAD)).  In particular, has built in support for Qt and its automoc system.
- Generators for build systems other than GNU Make, which includes IDEs (note above how CMake generated me a nice Visual Studio project file!)
- Natively supports unit tests which it hands off to its companion app, CTest, which in turn integrates nicely with its other brother, the rather swanky [CDash](http://vps2.etotheipiplusone.com:30176/cdash/index.php?project=KListings&date=2012-07-28).
- Fully native on whatever platforms it runs on: in particular, I could build my KDE app and support libraries on Windows 32 using *no* UNIX-y ports (such as cygwin, MSYS, Mingw etc) whatsoever, which is apparently not the case with autotools.  In particular, the entire KDE Software Compilation can be built this way, which I was very impressed by! :)
- Relatedly: (mostly) transparent support for more compilers than just gcc/ mingw.
- *Reasonably* clean and expressive language syntax, though not without its weird quirks and limitations! Has native lists and list iterators, functions, packages/ modules, and at least rudimentary namespacing which is nice when writing large-ish CMake-based libraries.

On the whole, I'm very happy with it, and based on what I've read,  honestly can't think of a good reason to go with autotools. scons sounds good, though.

---

### Post by PGScooter on 2012-07-30
GeneralZod --

Thank you so much for your careful and detailed response. You gave a nice example and also made some nice general remarks. I think scons could have an advantage for me if I already knew Python, but I don't.

I think I will start studying cmake. This books seems like a good place to start:
[http://www.amazon.com/Mastering-CMake-Cross-Platform-Build-System/dp/1930934203/ref=sr_1_3?ie=UTF8&qid=1343675597&sr=8-3&keywords=cmake](http://www.amazon.com/Mastering-CMake-Cross-Platform-Build-System/dp/1930934203/ref=sr_1_3?ie=UTF8&qid=1343675597&sr=8-3&keywords=cmake)

Thanks again GeneralZod. I really appreciate the time you took to write a careful response (complete with links!).

---

### Post by GeneralZod on 2012-07-30
You're very welcome :) 

But, addendum: it turns out that, in my excitement, I didn't actually build all the automated tests and stuff (doh!), which has now exposed a couple of small flaws in my CMake stuff, and isn't automatically set up correctly in Visual Studio.  So not quite as flawless as I originally thought :)

Edit:

I learnt CMake from the online docs, so you might not want to splash out on a book.  Plus, it's a fast-moving target! :)

---

### Post by PGScooter on 2012-07-31
Interesting. Thanks for the update. I hope you get the VS stuff figured out without too much pain. I don't know why but I've always enjoyed learning from books. Makes no sense for computer topics but still it's what I like.

---

