---
title: "How can I find IDE for c++"
date: 2006-10-03
forum: Programming Talk
---

### Post by fyz on 2006-10-03
I used Microsoft VC++ under Windows XP.
I want to learn to programming under Ubuntu linux. Where can I find any IDE for C++?
Thank you very much!

---

### Post by gborzi on 2006-10-03
AFAIK, the two major IDE for C/C++ are the kde-based kdevelop and the gnome-based anjuta. Both are available in the repositories. However, I have never investigated on this matter, because I use gvim + gcc + makefile + ddd to write/compile/debug the code I develop.

---

### Post by Jussi Kukkonen on 2006-10-03
I'd estimate that most people don't use an IDE on linux, but there is at least anjuta in the repositories (it's for C/C++ and Gtk+)...

---

### Post by Ayman on 2006-10-04
Anjuta is nice, and there is also eclipse with the C/C++ plugin CDT:
[http://www.eclipse.org/cdt/](http://www.eclipse.org/cdt/)

It's available in the repositories as eclipse-cdt.

---

### Post by skymt on 2006-10-04
A lot of people like [Code::Blocks](http://www.codeblocks.org/) for C++.

---

### Post by lnostdal on 2006-10-04
> **fyz said:**
> I used Microsoft VC++ under Windows XP.
I want to learn to programming under Ubuntu linux. Where can I find any IDE for C++?
Thank you very much!


* Emacs (it's not an IDE; it's an Operating System)
* Scons
* GDB
* ..and DDD

Anything else is in my way and is to be assimilated or removed at once. :)

---

### Post by johnnymac on 2006-10-04
Just to bounce it around...

The company I work with mostly uses anjuta with shared projects via CVS.  The remainder use vi/vim with cscope.

---

### Post by public_void on 2006-10-05
Like most have said, Emacs, gcc, make, etc to write programs.

---

### Post by amo-ej1 on 2006-10-05
> **skymt said:**
> A lot of people like [Code::Blocks](http://www.codeblocks.org/) for C++.


Code::Blocks really look like it has a lot of potential, however it still needs a lot of work, it isn't in the (dapper) repository so you'll have to compile (at least if you want a more recent version with more freatures) it yourself which takes _forever_ ;).

Altough the first IDE with emacs keybindings and doxygen/stl comment aware code completion wins.

---

### Post by monktbd on 2006-10-05
> **amo-ej1 said:**
> Code::Blocks really look like it has a lot of potential, however it still needs a lot of work, it isn't in the (dapper) repository so you'll have to compile (at least if you want a more recent version with more freatures) it yourself which takes _forever_ ;).


you can download nightly builds from the forum there.
they work well.

so no need to compile when it is already a nightly build.

---

### Post by amo-ej1 on 2006-10-05
*argl* must 've missed that when I checked it out ](*,)

---

### Post by JapanFred on 2006-10-05
Eclipse or VIM, depends what im doing.

Something small, maybe only a function or two big i'll use VIM, whereas for an actual project i'll use Eclipse.

I'm a developer for a software dev house in London, we use Visual Studio (.NET Is very powerful) and in my eyes it is the best IDE ever, but it's only on windows, so Eclipse comes second.

:)

---

### Post by cstudent on 2006-10-05
You can also download nightly Ubuntu builds of Code::Blocks from here:
[http://developer.berlios.de/project/showfiles.php?group_id=5358&release_id=9217](http://developer.berlios.de/project/showfiles.php?group_id=5358&release_id=9217)

---

