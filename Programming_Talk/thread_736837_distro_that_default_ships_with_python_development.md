---
title: "distro that default ships with python development"
date: 2008-03-27
forum: Programming Talk
---

### Post by miesnerd on 2008-03-27
Hi-
Im looking to set up a computer that doesnt have internet access to be a standalone workstation to learn python on and to hopefully develop a cool idea I have for a program to help researchers. In the end I want to have a program that can be run graphically on any linux machine. Is there a distro that comes with all the tools I need by default, or will i have to download the individual packages and install them onto the computer after the base install?

Thanks
Miesnerd

---

### Post by mssever on 2008-03-27
> **miesnerd said:**
> Hi-
Im looking to set up a computer that doesnt have internet access to be a standalone workstation to learn python on and to hopefully develop a cool idea I have for a program to help researchers. In the end I want to have a program that can be run graphically on any linux machine. Is there a distro that comes with all the tools I need by default, or will i have to download the individual packages and install them onto the computer after the base install?

Thanks
Miesnerd

That depends on what tools you need. If you stick to the Python stdlib, then pretty much any modern distro should do. Ubuntu includes by default a number of Python libs in addition to the stdlib; probably other distros do, too. Of course, unless you specify what libs you need, it's impossible to give a very specific answer.

---

### Post by uberlube on 2008-03-27
Why not use any distro you please. Python takes all of 30 seconds to install.

---

### Post by miesnerd on 2008-03-27
here's the thing:
I am learning python, so i dont know exactly what all I'd need to download after installing the base distro to then transfer over and install. I was hoping to have something like glade and IDLE installed by defualt in a larger distro (maybe suse or sabayon?) and not have to go through trying to collect all the dependencies to get a working system that will only be used for development. I plan on writing a program in python that will have a GUI in the end. if all it takes is installing a few packages after an initial install, that's no prob-- I just dont know.

---

### Post by pmasiar on 2008-03-27
No way you will be happy with default install in any distro. There is a way how to add external memory (CD, USB) as additional repository, learn that trick and it will solve many problems you will inevitably have on such disconnected linux. Linux expects to be connected :-)

---

### Post by miesnerd on 2008-03-27
I know how to add a cd as a repo-- its not hard, afterall.
What I dont know, is if I want a full enviornment for development that wont have acess to the internet, what all packages I need to get, if any. That's kinda why I mentioned SuSe and Saabayon because they ship large, as opposed to Ubuntu whch seems to only ship what's needed for a regular desktop user.

---

### Post by Wybiral on 2008-03-27
> **miesnerd said:**
> I know how to add a cd as a repo-- its not hard, afterall.
What I dont know, is if I want a full enviornment for development that wont have acess to the internet, what all packages I need to get, if any. That's kinda why I mentioned SuSe and Saabayon because they ship large, as opposed to Ubuntu whch seems to only ship what's needed for a regular desktop user.

It depends what you're doing. You don't need something like BioPython if you're going to be writing games... Likewise, you don't need PyGame if you're going to be studying molecular biology. What kind of stuff do you plan to develop?

---

### Post by miesnerd on 2008-03-27
thanks for getting back to me. First thing first is going to be a stand alone program that is searching the internet (i know, its ironic that the computer I want to use it for doesnt have internet access) and collect publication information for researchers. It will work with google scholar and a few other things like EBSCOhost, etc, but will collect information and store a log of it (citations and all) on your local machine.
Also, I'd love it (later, not a priority now) if it could work with Referencer.

---

### Post by Wybiral on 2008-03-27
You'll probably only need a database (such as SQLite) and an HTML parser (like BeautifulSoup) to do that.

---

### Post by htor on 2008-03-28
> **Wybiral said:**
> You'll probably only need a database (such as SQLite) and an HTML parser (like BeautifulSoup) to do that.
and some algorithm that will decide what information is more important (when dealing with multiple sources).

---

