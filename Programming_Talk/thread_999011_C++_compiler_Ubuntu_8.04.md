---
title: "C++ compiler Ubuntu 8.04"
date: 2008-12-01
forum: Programming Talk
---

### Post by stmartin on 2008-12-01
Hello!
I got Geany and KDevelop C++ compilers from Add/Remove.

When I try to execute the program I get error Failed to execute the program on Geany.

When I press "Make All" I get: 
make: *** No rule to make target `all'.  Stop.

On KDevelop I got:
```
cd '/home/stefan/programiranje/asda' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" LC_MESSAGES="C" LC_CTYPE="C" make -f Makefile.cvs && mkdir '/home/stefan/programiranje/asda/debug' && cd '/home/stefan/programiranje/asda/debug' && CXXFLAGS="-O0 -g3" "/home/stefan/programiranje/asda/configure" --enable-debug=full && cd '/home/stefan/programiranje/asda/debug/src' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" LC_MESSAGES="C" LC_CTYPE="C" make -k asda.lo
aclocal
make: aclocal: Command not found
make: *** [all] Error 127
*** Exited with status: 2 ***

```

Can you please help me?

Thanks in advance.

---

### Post by Zugzwang on 2008-12-01
Please look at the so-called stickies (the threads that always appear at the top of the thread list), i.e. how to compile your first C/C++ program.

Note that neither Geany nor KDevelop are *compilers*, just Integrated Development environments that use the GCC compiler suite.

Apart from that, it is clearly stated that there's something missing. The following general advice helps you with dealing with such situations:
> 
You have ran into the problem that some files are missing on your system. This can be seen more or less directly from the error message. Since Ubuntu uses package management, it is worthwhile searching for a package containing that file. In order to do so, redirect your web browser to "http://packages.ubuntu.com", type in the name of the file you are missing (note that the error message may contain parts of paths special to your system, like your home path if it is searched for the missing file there - make sure to strip them beforehand) in the section "Search the contents of packages", select "packages that contain files whose names contain the keyword" and choose your distribution. Then hit search and have a look at the answers. You should get a list of packages containing a respective file. Examine the package names and remember the names of the packages that look promising. Then install them by entering "sudo apt-get install " plus a space-separated list of packages in the terminal. You will need "sudo"-rights for this. Afterwards, see if your problem has vanished. If not, come back reporting what you did (including what you actually searched for) and ask for further help.


---

### Post by stmartin on 2008-12-01
Thanks for the reply.

I managed to get working Greany. It works perfectly.

Can you please give me the link to the sticky thread?

I installed KDevelop through Add/Remove so I don't think that any package is missing. I got updated Ubuntu before 1 hours, so I think everything is fine.

---

### Post by Zugzwang on 2008-12-02
> **stmartin said:**
> Can you please give me the link to the sticky 
thread?

Actually, you cannot miss it. See the attached image. It shows the forum and where the sticky threads actually are. Read though all the threads and follow the links under the C/C++ sections. 

> **stmartin said:**
> 
I installed KDevelop through Add/Remove so I don't think that any package is missing. I got updated Ubuntu before 1 hours, so I think everything is fine.
It doesn't work that way. If everything you might ever need when programming is installed together with the IDE, you would have ~20GB (rough estimate) of unused development stuff on your harddisk. You will need to install the packages that *you* need manually.

The autotools are not installed automatically (at least I assume so) because when using only "Custom Makefiles" or "QMake projects" (Project types in KDevelop), you do not need them. Therefore, they are optional and not installed automatically.

---

### Post by stmartin on 2008-12-02
Thanks for the reply. I thought there is separate sticky thread for C/C++ compiling.

Anyway, Geany now works perfectly.

---

### Post by stmartin on 2008-12-06
But the problem is that I don't want to compiling manually. It is too much time spending. If I got errors in my code I will compiling 5 times, which is no good.

---

### Post by namegame on 2008-12-06
> **stmartin said:**
> But the problem is that I don't want to compiling manually. It is too much time spending. If I got errors in my code I will compiling 5 times, which is no good.

When beginning programming, expect to be compiling many times to sort out your errors. It's the nature of programming.

The appending your compilation command with -Wall will return many insightful warnings.

An example,

[php]g++ -Wall hello.cpp[/php]

---

