---
title: "Compiling for the First Time [GalaXQL]"
date: 2014-02-06
forum: New to Ubuntu
---

### Post by dogstoevski on 2014-02-06
Hello. I am new Ubuntu (13.10) and Linux, and I need assistance compiling/installing a program called [Galaxql]("http://sourceforge.net/projects/galaxql/"). I am trying to use this to learn SQL.
I couldn't find this program using apt-get, and the README file mentions it can be compiled in Ubuntu, so I went to Ubuntu's [compiling tutorial ]("https://help.ubuntu.com/community/CompilingEasyHowTo")for instructions.

The following are the steps I took. I am guessing these can be ignored:
I extracted the tar file into /usr/local/src then tried typing in "./configure" in the terminal, but nothing happened because there is no such file or directory.
Then I proceeded to run "make".
When I ran "make" for the first time, the terminal mentioned a file named wxprec.h was missing. I used apt-file search then installed wx2.8-headers.
I ran "make" again then it gave me an error about a "wx-config" command. I installed libwxgtk2.8-dev among the list apt-file gave me.
Next time, I got an error message about GL/gl.h missing. I apt-file searched it and got a list of several packages that contained the file. I chose to install mesa-common-dev and libglu1-mesa-dev for some reason. (I tried installing several minGW packages which did not resolve the GL/gl.h error message.)

Finally, here is where I am stuck. I ran "make" again, and now, I get an error message that I don't really understand.
```
g++ -o galaxql RegenerationDialog.o galaxql.o sqlqueryctrl.o sqlite3.o -L/usr/lib/x86_64-linux-gnu -pthread -Wl,-Bsymbolic-functions -Wl,-z,relro  -L/usr/lib/x86_64-linux-gnu   -lwx_gtk2u_core-2.8 -lwx_baseu-2.8 -lwx_gtk2u_gl-2.8 -lwx_gtk2u_html-2.8 -lwx_gtk2u_stc-2.8  -lGLU
/usr/bin/ld: sqlite3.o: undefined reference to symbol 'dlclose@@GLIBC_2.2.5'
/lib/x86_64-linux-gnu/libdl.so.2: error adding symbols: DSO missing from command line
collect2: error: ld returned 1 exit status
make: *** [galaxql] Error 1
```

First of all, am I doing this right? I have no idea what I've been installing. Is there a better/easier way to compile/install this program?
Up to this point, the error messages would tell me what file was missing and I could search for packages containing the file, but now, I'm stuck. I do now know what are GalaXQL's dependencies.

Any help would be appreciated. Thank you.

---

### Post by spjackson on 2014-02-06
It looks to me as though you are missing -ldl from the end of that command that links the executable. Having taken a quick look at the [makefile]("http://sourceforge.net/p/galaxql/code/ci/master/tree/makefile") I would suggest adding -ldl to line 23, i.e.
```

PLATFORM_LDFLAGS = -lGLU -ldl
```

---

### Post by SeijiSensei on 2014-02-06
And here I thought Galaxql was the database used by Ninomiya Rui to build the GALAX network in [Gatchaman Crowds]("http://www.crunchyroll.com/gatchaman-crowds")!

---

### Post by dogstoevski on 2014-02-06
Thank you for the tip. Adding -ldl gave this message: 
```
g++ -o galaxql RegenerationDialog.o galaxql.o sqlqueryctrl.o sqlite3.o -L/usr/lib/x86_64-linux-gnu -pthread -Wl,-Bsymbolic-functions -Wl,-z,relro  -L/usr/lib/x86_64-linux-gnu   -lwx_gtk2u_core-2.8 -lwx_baseu-2.8 -lwx_gtk2u_gl-2.8 -lwx_gtk2u_html-2.8 -lwx_gtk2u_stc-2.8  -lGLU -ldl
/usr/bin/ld: galaxql.o: undefined reference to symbol 'glDepthFunc'
/usr/lib/x86_64-linux-gnu/mesa/libGL.so.1: error adding symbols: DSO missing from command line
collect2: error: ld returned 1 exit status
make: *** [galaxql] Error 1
```
After some Googling, I added '-lGL' after '-ldl', and that seems to have done the trick. make ran without error messages.

Now I tried 'sudo checkinstall' and 'sudo checkinstall --fstrans=0' without making any changes and got this following error:
```
This package will be built according to these values: 

0 -  Maintainer: [ root@namehere ]
1 -  Summary: [ galaxql ]
2 -  Name:    [ galaxql-src ]
3 -  Version: [ 2.1 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ amd64 ]
8 -  Source location: [ galaxql-src-2.1 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]
11 - Provides: [ galaxql-src ]
12 - Conflicts: [  ]
13 - Replaces: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
make: *** No rule to make target `install'.  Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.
```
I do not know why the installation failed..

---

