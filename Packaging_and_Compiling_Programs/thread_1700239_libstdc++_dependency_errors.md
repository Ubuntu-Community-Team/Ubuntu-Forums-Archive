---
title: "libstdc++ dependency errors"
date: 2011-03-04
forum: Packaging and Compiling Programs
---

### Post by ltaverne07 on 2011-03-04
I am trying to learn GNU C++ using Tom Swan's GNU C++ for Linux. When trying to compile a program with the iostream.h included, G++ tells me it can't find the file. So I need to install libstdc++ using sudo apt-get install libstdc++. When I try this I get a whole nasty error:

> $ sudo apt-get install libstdc++
[sudo] password for luke: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libstdc++6' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.4-dev' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.4-dbg' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.5-dev' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.5-dbg' for regex 'libstdc+'
Note, selecting 'libstdc++-dev' for regex 'libstdc+'
Note, selecting 'libstdc++5-3.3-dbg' for regex 'libstdc+'
Note, selecting 'libstdc++5-dbg' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.0-dbg' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.1-dbg' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.2-dbg' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.3-dbg' for regex 'libstdc+'
Note, selecting 'libstdc++6-dbg' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.4-doc' for regex 'libstdc+'
Note, selecting 'libstdc++2.10-dev' for regex 'libstdc+'
Note, selecting 'libstdc++2.8-dev' for regex 'libstdc+'
Note, selecting 'libstdc++2.9-dev' for regex 'libstdc+'
Note, selecting 'libstdc++2.9-glibc2.1-dev' for regex 'libstdc+'
Note, selecting 'libstdc++3.0-dev' for regex 'libstdc+'
Note, selecting 'libstdc++5-3.3-doc' for regex 'libstdc+'
Note, selecting 'libstdc++5-doc' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.0-doc' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.1-doc' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.2-doc' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.3-doc' for regex 'libstdc+'
Note, selecting 'libstdc++6-doc' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.4-pic' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.5-doc' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.3-dev' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.4-dev-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.4-dbg-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.5-dev-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.5-dbg-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++5' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.3-pic' for regex 'libstdc+'
Note, selecting 'libstdc++6-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++5-3.3-dbg-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++5-dbg-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.0-dbg-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.1-dbg-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.2-dbg-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.3-dbg-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-dbg-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-dbg-armel-dcv1' for regex 'libstdc+'
Note, selecting 'libstdc++-dev-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++-dev-armel-dcv1' for regex 'libstdc+'
Note, selecting 'libstdc++6-dev-armel-dcv1' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.4-pic-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-pic-armel-dcv1' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.5-pic' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.5-pic-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-armel-dcv1' for regex 'libstdc+'
Note, selecting 'libstdc++6-armel-cross' instead of 'libstdc++6-armel-dcv1'
libstdc++6 is already the newest version.
libstdc++6-4.4-dev is already the newest version.
libstdc++6-4.4-dev set to manually installed.
libstdc++6-4.5-dbg is already the newest version.
libstdc++6-4.5-dev is already the newest version.
libstdc++6-4.5-dev set to manually installed.
libstdc++6-4.3-dev is already the newest version.
libstdc++6-4.3-dev set to manually installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libstdc++6-4.4-dbg : Conflicts: libstdc++6-4.3-dbg but 4.3.5-3ubuntu1 is to be installed
 libstdc++6-4.4-doc : Conflicts: libstdc++6-4.3-doc but 4.3.5-3ubuntu1 is to be installed
 libstdc++6-4.5-dbg : Conflicts: libstdc++6-4.3-dbg but 4.3.5-3ubuntu1 is to be installed
                      Conflicts: libstdc++6-4.4-dbg but 4.4.4-14ubuntu5 is to be installed
 libstdc++6-4.5-dbg-armel-cross : Conflicts: libstdc++6-4.4-dbg-armel-cross but 4.4.4-14ubuntu4 is to be installed
 libstdc++6-4.5-doc : Conflicts: libstdc++6-4.3-doc but 4.3.5-3ubuntu1 is to be installed
                      Conflicts: libstdc++6-4.4-doc but 4.4.4-14ubuntu5 is to be installed
E: Broken packages


Please help me resolve this, I want to keep reading this book, but since I can't compile any programs, it's useless to just read it.

---

### Post by ltaverne07 on 2011-03-04
After more research, I got it to compile, but I would still like help resolving these broken packages.

---

### Post by MadCow108 on 2011-03-04
the package manager, being confused by the ++ regex in the package name, got greedy and tried to install all packages of libstdc++ available.
there are multiple versions in the repository (3.3, 4.1, 4.2 , 4.3, 4.4 and 4.5 in your case).
but not all packages from all versions can be installed at the same time.
e.g. the -dbg and -doc packages are mutually exclusive. you must choose one.

so your request for all at once cannot be fulfilled.
the ++ in the package name is unfortunate

specify the version you need exactly, e.g.
sudo apt-get install libstdc++6-4.5-dev

(note that you already have more than you need installed, you can probably remove the older versions which are not mutually exclusive again, e.g. 4.3-dev and 4.4-dev )

---

### Post by ltaverne07 on 2011-03-04
Thank you! I didn't realize I wasn't being specific enough, the book I'm using said to find libstdc++.rpm, so I figured the Ubuntu version would be the same name.

Thanks again, thread solved. :KS

---

