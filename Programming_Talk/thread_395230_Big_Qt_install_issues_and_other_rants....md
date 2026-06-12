---
title: "Big Qt install issues and other rants..."
date: 2007-03-27
forum: Programming Talk
---

### Post by msikka on 2007-03-27
Hi all, I was all happy the first time I installed Ubuntu a few days back. But all that initial euphoria has washed off after my first dabble with Linux. I think I am an accomplished programmer and have been programming in c, c++ for the last 7 years in the Windows environment, and then before that for a couple of years on Irix. I have been trying to install some C++ IDEs on my Linux, and having such a crappy time doing it. I just don't get why Linux is so hyped up when even basic installs are such a pain! I got KDevelop using Synaptic, but can never get even the basic HelloWorld program to compile, I thought maybe I'll try a more mature product with some proper documentation, and tried Qt, and can't even finish the damned convoluted installation process. The "make" finishes with tons of errors, and so does the "make install" part. Then I can't append the new path variable line to the "environment" file (bash: environment: Permission denied, I even tried it with the sudo prefix) which the Qt doc conveniently forgot should be the one to replace for Ubuntu shells instead of the .profile. 

So, I'm left with all this semi-installed crap on my system trying to figure out whether to just re-install Ubuntu, or get a degree in uninstalling crap from Linux. At least Windows gives you what you expect. 

In the end, I'm left with a desire to really figure out, what drives people who love Linux so much? And why? Apart from the fact that it's free, and has a few installed things that run OK, to me, it's the equivalent of every man carrying their own bridge and assembling it every-time they need to cross a river. With windows it's civilized - the state collects taxes and builds the bridge for you.

Thanks

---

### Post by lnostdal on 2007-03-28
*sigh* .. I'm tired of saying this: Why on earth are you installing stuff from source? Do .. not .. do .. that!

For QT development:

```

sudo aptitude install libqt4-dev

```

To install the GCC compiler (C and C++), libraries and headers do:

```

sudo aptitude install build-essential

```

..if you have problems with "Hello World" in KDevelop I'd like some more information.. (Project -> New Project -> C/C++ -> Simple hello world ..etc.)

You also use the wrong terms. KDevelop is not the same "product-type" as QT. QT is (well, mostly) a software library, while KDevelop is an application (an IDE). 

I'd say learn how to use the simple basics of the system properly before you try to do development on it: [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware) ...etc.

edit: 
Oh, and the ranting isn't needed. If you have a problem, simply describe it and focus on solving it. That is; if that is what your goal is.

There are plenty of other people on this forum who have no interest in actually solving any problem they might be having. Feel free to join them - you'll find plenty of threads leading no-where. If you do so I'll try to ignore you and them and keep myself busy developing using the best tools and environment ... ever -- while instead helping those who actually want help.

---

### Post by msikka on 2007-03-28
Thanks Inostdal. :o)

I guess that's why people like Linux - the community.

I'm going to try this tonight, but thanks so much for taking the time to write.

So, Qt is just libraries? Hmm, had no idea. Well, no wonder I couldn't find anything to run even after it seemed to have put some stuff in the /usr/local/Trolltech dir. Now, how can I uninstall this to follow your intall techniques? In their install file Qt says to type some uninstall command from the "build" directory - what is the build directory?

As far is KDevelop is concerned, I remember the errors were 'make' related, but again, I'll let you know tonight when I get back home. 

I installed CodeBlocks, and that runs fine, but I still want KDevelop to work. I like it's interface.

I'm sorry if I hurt anyones feelings, I was just a bit upset. I agree I should take the time to understand things first, and I like the tinkerability of Linux also.

Thanks again Inostdal.

---

### Post by msikka on 2007-03-28
Hi Inostdal, so here's the error messages I get when I try to build the HelloWorld in KDevelop:

cd '/home/msikka/programming/first_kdev' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -f Makefile.cvs && mkdir '/home/msikka/programming/first_kdev/debug' && cd '/home/msikka/programming/first_kdev/debug' && CFLAGS="-O0 -g3 " "/home/msikka/programming/first_kdev/configure" --enable-debug=full && cd '/home/msikka/programming/first_kdev/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -k 
aclocal
make: aclocal: Command not found
make: *** [all] Error 127
*** Exited with status: 2 ***


Thanks

---

### Post by msikka on 2007-03-29
Hi again Inostdal, I was successfully able to install the Qt libraries and compiled and ran a basic Qt window program. It all works.

Thanks so much. Could you see my output from the kDevelop program? It has some make related issues, but I can't figure it out.

---

### Post by lnostdal on 2007-03-29
I'm not entirely sure why you get that message. Maybe automake is missing?

---

### Post by justin whitaker on 2007-03-29
> **msikka said:**
> Hi Inostdal, so here's the error messages I get when I try to build the HelloWorld in KDevelop:

cd '/home/msikka/programming/first_kdev' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -f Makefile.cvs && mkdir '/home/msikka/programming/first_kdev/debug' && cd '/home/msikka/programming/first_kdev/debug' && CFLAGS="-O0 -g3 " "/home/msikka/programming/first_kdev/configure" --enable-debug=full && cd '/home/msikka/programming/first_kdev/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -k 
aclocal
make: aclocal: Command not found
make: *** [all] Error 127
*** Exited with status: 2 ***


Thanks

I think automake is missing. It is in the repository though, so you can fire up Synaptic...(or Adept...or aptitude....or apt....) and install it.

---

### Post by wkulecz on 2007-03-29
Is your rant really claiming that getting development tools working on Ubuntu is harder than installing Visual C/C++ on windows?

I think either your windows box was setup for you, or you've forgotten the pain and rebooting involved in getting Visual C/C++ working.

For C programming, command line and make with the text editor of your choice is probably the best way to go.  But for C++ you are severely handicapped without some class browser tools, so finding an IDE you can tolerate is essential.  Kdevelop is OK once you get used to it and the documentation files are installed right.   Eclipse seemed overkill for my needs but is probably worth learning if you are going to be doing cross-platform stuff.

I found this Kdevelop tutorial useful when first starting out:

[http://developer.kde.org/~larrosa/visualtutorial/index.html](http://developer.kde.org/~larrosa/visualtutorial/index.html)


--wally.

---

### Post by msikka on 2007-03-29
Yes, automake was the issue, and it's crossed that bridge, but stuck elsewhere now. Same program, here's the new error:

aclocal
aclocal:configure.in:8: warning: macro `AM_PROG_LIBTOOL' not found in library
autoheader
automake
autoconf
configure.in:8: error: possibly undefined macro: AM_PROG_LIBTOOL If this token and others are legitimate, please use m4_pattern_allow. See the Autoconf documentation.
make: *** [all] Error 1
*** Exited with status: 2 ***


Hi Wally, well, you're right about Visual Studio being installed for me. The Pro version was , at work, but a few weeks back I installed the Visual Studio C++ 2005 Express Edition at home, and it worked out of the box without a hitch. BTW, the Express Edition is made available free by Microsoft.

I have re-discovered the pleasure of programming using just a text editor and command-line compiling :o 

But still, I would love to have a RAD development tool that just works with minimal tweaking.

Thanks for your help guys.

---

### Post by wkulecz on 2007-03-30
Here is an IDE that looks a lot lighter weight if all you need is C/C++

[http://www.codeblocks.org/](http://www.codeblocks.org/)

I just learned about it,  I like the idea of having the same IDE on Linux and Windows, but doubt I'll switch tool chains any time soon unless a real reason develops.  Once a certain level of familiarity and functionality with the tools are attained, risk/benefit of change ends up being mostly risk.

--wally.

---

