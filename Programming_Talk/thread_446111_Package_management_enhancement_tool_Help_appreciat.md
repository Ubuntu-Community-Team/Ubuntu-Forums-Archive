---
title: "Package management enhancement tool: Help appreciated"
date: 2007-05-16
forum: Programming Talk
---

### Post by Warbo on 2007-05-16
NOTE: Sorry for the complicated explanation to follow, please bear with me :)

Hi, I'm pretty new to programming, and unfortunately know a lot more Java than I do anything else (it is what my University teaches). I have had an idea knocking around for a while and now that I might be able to make it (in Java at least) I have started attempting to do just that, but I think a bit of help wouldn't hurt.

The program I am trying to make is a small tool to make powerful package management easier by the use of what I call "service packs". I have made a spec on the Wiki here: [https://wiki.ubuntu.com/TransparentServicePackMaker](https://wiki.ubuntu.com/TransparentServicePackMaker) . It doesn't (necessarily) involve any changes to the current APT system as a service pack is just a small APT repository containing all of the dependencies needed by the packages specified through the tool to be included (for example, telling the tool to include the package "gimp" would put a package of the GIMP into the generated service pack's repository along with all of its dependencies, and their dependencies, etc.). As well as specifying exact packages by name the tool should also be able to include all of the packages currently installed. Service packs are then just self-contained application packages which can be moved around to non-networked computers, or distributed over the Internet to get all dependencies in one go (APT would still use newer versions of included packages if they exist, so there is no conflict).

To make these repositories a little less massive they can assume that certain packages are already installed via dependencies on other service packs. This is handled by giving each service pack a meta-package which depends on all of its specified packages. These meta-packages can then depend on each other to make sure only relevant packages are stored inside the packs. This also lets meta-packages like ubuntu-desktop be treated as already-installed service packs, since depending on ubuntu-desktop allows service packs to only include changes from a default install (VERY useful in the include-all-installed-packages scenario, since it would then become an offline update tool).

The "transparent" comes from the fact that it uses the existing possibilities of APT, and all a user has to do to install the included applications is install the included meta-package (how the repository gets added to and removed from APT is still an issue, but dumping files around from inside package installation/removal scripts seems the most obvious answer).

Anyway, enough of the babble. Basically I am making a Java version (linked to from the spec page, stored on crappy free webspace) just to show how useful it could be (see use cases, especially useful if an LSB unified packaging API is made) but I would really like to see it made in a much more professional way, and in Python (probably) to be available in Ubuntu. So this is a call to Python programmers: If you are interested then could you please help me turn this into a useful tool?

Thanks for reading all of that :D

---

### Post by pmasiar on 2007-05-16
Even for half-competent Java programmer (this is generic statement, not about your skill level :-) ), learning Python is matter of a week, so don't be afraid. Second programming language is always easier than first.

---

### Post by Warbo on 2007-05-17
I do have a little Python knowledge, just under a year ago I tried to make a simple board-based game from scratch (file-wise and knowledge-wise) mainly relying on DiveIntoPython,. I made the basic logic for it in about a day, but couldn't get my head around GTK and stuff. Know that I know about OO programming I tried making it in Java and had it fully working in about an hour :)

I suppose all I really need to know is the syntax for Python classes, methods, etc. (my game logic was one big method :) ). I'll try and get this Java one working properly first, so I have all of my algorithms right, then make a start on Python. I was just thinking that if I can make a good start on it then it would be trivial for an experienced programmer to get it running in a minute.

---

