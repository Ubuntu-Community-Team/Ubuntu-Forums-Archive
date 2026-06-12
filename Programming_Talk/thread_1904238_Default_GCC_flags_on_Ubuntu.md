---
title: "Default GCC flags on Ubuntu"
date: 2012-01-04
forum: Programming Talk
---

### Post by Jorenko on 2012-01-04
My company has a large code-base and a large variety of linux machines on which it is compiled. We use both -Wall and -Werror in order to ensure maximum code quality, but often Ubuntu's gcc seems to add warnings with -Wall that other distros' gccs do not, even at the exact same or newer gcc version. This means if another developer checks in code there's a good chance that the build will break for me, since I use Ubuntu. I've found [https://wiki.kubuntu.org/ToolChain/CompilerFlags?action=show&redirect=CompilerFlags](https://wiki.kubuntu.org/ToolChain/CompilerFlags?action=show&redirect=CompilerFlags) but even turning off all the options called out there doesn't fix all my problems. For instance, I'm seeing unused-but-set-variable show up often even with all of those accounted for. I'd like to know once and for all exactly where and why Ubuntu adds all these extra warnings, so that I can either explicitly disable them all for me or explicitly enable them all in the code-base.

---

### Post by dwhitney67 on 2012-01-04
If you don't want your compilation to abort, then remove the -Werror.  If that is not an option, then determine why your co-worker's compiler is not complaining enough.

Whether I'm on Ubuntu or RedHat, compiling with the -Wall option will spit out a warning about unused variables.

What platforms are your co-workers using?

---

### Post by Jorenko on 2012-01-04
Turning of -Werror is definitely not an option. Most of the co-workings are on Debian stable. One's actually on Ubuntu 11.04 still as well, which DOES use an older version of gcc, but I've definitely seen similar issues between identical gcc versions on debian and ubuntu.

Really, the only thing I want is a piece of documentation saying how ubuntu defines default compiler flags. I can't seem to find anything other than that kubuntu wiki article anywhere.

---

### Post by dwhitney67 on 2012-01-04
> **Jorenko said:**
> Turning of -Werror is definitely not an option. Most of the co-workings are on Debian stable. One's actually on Ubuntu 11.04 still as well, which DOES use an older version of gcc, but I've definitely seen similar issues between identical gcc versions on debian and ubuntu.

Really, the only thing I want is a piece of documentation saying how ubuntu defines default compiler flags. I can't seem to find anything other than that kubuntu wiki article anywhere.

Check your and your co-workers working environment; either echo CFLAGS (or CXXFLAGS for C++).  They hopefully shouldn't be set to anything.  If they are, then unset them.  Typically the compiler options are set within a Makefile.  Also check that they have not aliased gcc or g++ to something other than the generic version.

I typically alias gcc and g++ to the following:
```

alias gcc='gcc -Wall -pedantic -std=c99'
alias g++='g++ -Wall -pedantic'

``` 

I do not have access to a Debian system, so I cannot perform any testing to duplicate the anomaly you see.  All I have at my disposal is Ubuntu, Kubuntu, and RHEL (RedHat) 4, 5, and 6.  On each of these systems that I do have, the compiler behavior that you have described is normal.  Thus if there is an issue, it is with the Debian system or with the working environment.

---

### Post by Zugzwang on 2012-01-04
Perhaps you are building your project on a different optimization level than your colleagues? 

There are a few warnings that only appear if you let the compiler optimize your code, as only then, dataflow analysis is performed, which is needed to find some warnings.

See [http://www.network-theory.co.uk/docs/gccintro/gccintro_52.html](http://www.network-theory.co.uk/docs/gccintro/gccintro_52.html) for details.

---

### Post by MadCow108 on 2012-01-04
> **Jorenko said:**
> Turning of -Werror is definitely not an option. Most of the co-workings are on Debian stable. One's actually on Ubuntu 11.04 still as well, which DOES use an older version of gcc, but I've definitely seen similar issues between identical gcc versions on debian and ubuntu.

Really, the only thing I want is a piece of documentation saying how ubuntu defines default compiler flags. I can't seem to find anything other than that kubuntu wiki article anywhere.

compiler warnings change pretty much with every version. e.g. unused-but-set is a new one in 4.6.

ubuntus defaults also change all the time and are rarely documented.
I think with 12.04 ubuntu uses the gcc defaults (meaning no -D_FORTIFY_SOURCE and other hardning by default anymore)

best way to solve this issue and keeping Werror is using a buildbot which always has the newest compiler (be sure to include clang, that may have different warnings too) and rebuild every commit.

---

