---
title: "trying to compile ktorrent"
date: 2007-05-19
forum: Packaging and Compiling Programs
---

### Post by Angelbeast on 2007-05-19
Hi... had reason to uninstall ktorrent   and now i'm trying to reinstall it by compiling it from the source code because i want to learn how to do it. Some other things i want to install are only available that way. Well it looked like i was having some success but then it just stopped with this error:

> checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
ron@ron-laptop:~/Desktop/ktorrent-2.1.4$ make
make: *** No targets specified and no makefile found.  Stop.
ron@ron-laptop:~/Desktop/ktorrent-2.1.4$ make install 

this is what i put in the terminal:

> tar -xvzf ktorrent-2.1.4.tar.gz
cd /home/ron/Desktop/ktorrent-2.1.4
./configure
make
make install 

Does anyone happen to know what i did wrong?

---

### Post by heimo on 2007-05-19
To make sure that you have all build dependencies installed, you could run:
```
sudo apt-get build-dep ktorrent
```

---

### Post by Angelbeast on 2007-05-19
> **heimo said:**
> To make sure that you have all build dependencies installed, you could run:
```
sudo apt-get build-dep ktorrent
```

it looks like it's going to install a good amount of extra stuff. Doing this will i be able to uninstall ktorrent and it's dependencies with having not installed it through the package manager ifi need to?

---

### Post by heimo on 2007-05-19
> **Angelbeast said:**
> it looks like it's going to install a good amount of extra stuff. Doing this will i be able to uninstall ktorrent and it's dependencies with having not installed it through the package manager ifi need to?

Yes and no. You can uninstall all those packages that apt-get build-dep will install, but there may not be easy way to select just one package for removal - you probably need to select all those - so you may want to put names of those packages to some list. There seems to be no aptitude build-dep equivalent (by default), but I did find this what at least claims to do that:
[http://p12n.org/hacks/aptitude-build-dep](http://p12n.org/hacks/aptitude-build-dep)

---

### Post by Angelbeast on 2007-05-19
> **heimo said:**
> Yes and no. You can uninstall all those packages that apt-get build-dep will install, but there may not be easy way to select just one package for removal - you probably need to select all those - so you may want to put names of those packages to some list. There seems to be no aptitude build-dep equivalent (by default), but I did find this what at least claims to do that:
[http://p12n.org/hacks/aptitude-build-dep](http://p12n.org/hacks/aptitude-build-dep)

sorry for sounding so ignorant now but what do i do with that?

---

### Post by heimo on 2007-05-19
> **Angelbeast said:**
> sorry for sounding so ignorant now but what do i do with that?

That particular piece of code is perl script, but you do not need it to install build dependencies for ktorrent. It's just an example that someone somewhere tried to make aptitude equivalent for apt-get build-dep functionality. You could just write down, or copy-paste names of the packages that will get installed by apt-get build-dep, if you're worried about being able to uninstall them later.

---

### Post by Angelbeast on 2007-05-19
> **heimo said:**
> That particular piece of code is perl script, but you do not need it to install build dependencies for ktorrent. It's just an example that someone somewhere tried to make aptitude equivalent for apt-get build-dep functionality. You could just write down, or copy-paste names of the packages that will get installed by apt-get build-dep, if you're worried about being able to uninstall them later.

i DON'T need to install the build dependencies? I thought that would have been why i got the error.  I'll have to come back to this tomorrow. It's 7:30 am and my mind is getting foggy *LOL* ... I'll look at this again after i get some sleep...Thanks for your help :-)

---

### Post by heimo on 2007-05-19
You do need build dependencies to build. You don't need build dependencies to run. After you've build binary, you only need its runtime dependencies installed. So you can remove what build-dep installs, you can't remove runtime dependencies for ktorrent.

---

### Post by Angelbeast on 2007-05-19
> **heimo said:**
> You do need build dependencies to build. You don't need build dependencies to run. After you've build binary, you only need its runtime dependencies installed. So you can remove what build-dep installs, you can't remove runtime dependencies for ktorrent.

okay so this build dependencies...are they for any time i'm going to compile from source, or just for one program?

---

### Post by Angelbeast on 2007-05-19
okay i went anddid everything and then when it was done i clicked on the deb pckage it made...and it's not for 64 bit...how do i make it for 64 bit?

---

