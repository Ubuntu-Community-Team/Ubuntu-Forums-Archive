---
title: "Ogre3D and CodeBlocks"
date: 2010-04-23
forum: Programming Talk
---

### Post by Axel-P on 2010-04-23
Hi all!

I'm programming C++ in a school project. We are programming a game and we use Ogre3D 1.6.1 with CodeBlocks. Ogre 1.6.1 is in the repos and after installation codeblocks recognizes it, but I cant compile any project. Seems like it can't find its headers. The error message says it can find the headers in the includes. I downloaded the source for ogre and tried to add the headers manually but if I do so I get the following message:

```
Can't create output directory /bin/Debug/
```

And if I manually create a "Debug" folder and give it the right permissions I get:

```

-------------- Build: Debug in test1 ---------------

Compiling: main.cpp
cc1plus: error: unrecognized command line option "-mthreads"
Process terminated with status 1 (0 minutes, 5 seconds)
0 errors, 0 warnings
 

```

I'm looking for help about this but cant find much, I prefer not to compile from source since I have another set of problems if I try to do so xD

Thanks in advance
Axel

---

### Post by azagaros on 2010-04-24
You need to compile the libs with a multi thread option on the compiler.

Usually its one of the options in the codeblock compiler option lists.  You also may look for the lib options in the read me files with the lib.

When compiling code the lib and the program must match.

Most of the time these are default but can get skewed if not paying attention to the compilers/linker groans, which your post is talking about.

---

### Post by vek on 2010-04-24
Not sure if any of the following advice is useful but I just got the latest ogre working... here's how I did it:

The way I got this working (about 3 days ago) was to download the ogre sources directly from the ogre site, and then the build dependencies from the standard Ubuntu apt repository, as described in the doc thats part of the ogre tar.gz.  I also used aptitude to get the nvidia CG stuff, which you have to get and then additionally run "nvidia-cg-toolkit-installer" since the one in the repository isn't the actual files, just an installer for them.

I just unpacked the ogre sources in a folder on my desktop, made another empty folder elsewhere and used cmake-gui to tell it to create the makefiles in this new empty folder (i.e. the empty folder was my build folder).

Used make to prepare and build it, no problems... but after that I diverged from the docs and used "sudo checkinstall -D --strip=no make install" to make and install it as a package (so I could uninstall later) instead of 'make install' as the docs suggested.

Once this was done, I removed everything (the original sources and the build folder, leaving just the package installed).

You have to run "sudo ldconfig" after doing so, so that the libraries are registered with the system.

After that code blocks 'just worked'.  It has an ogre project wizard, which works for me...  I had to change it to use the "OgreMain" lib instead of the debug ("OgreMain_d") in the project settings in the projects it made becuase I did not build those, I just built ogre release... and by default Code::Blocks attempts to use those, but had no other issues.

Other than that, smooth sailing... hope this post helps some!

---

### Post by Axel-P on 2010-04-27
Still doesn't works.

if I try ./boostrap:
```
libtoolize: putting auxiliary files in `.'.
libtoolize: copying file `./ltmain.sh'
libtoolize: putting macros in `Scripts/m4'.
libtoolize: copying file `Scripts/m4/libtool.m4'
libtoolize: copying file `Scripts/m4/ltoptions.m4'
libtoolize: copying file `Scripts/m4/ltsugar.m4'
libtoolize: copying file `Scripts/m4/ltversion.m4'
libtoolize: copying file `Scripts/m4/lt~obsolete.m4'
libtoolize: Consider adding `AC_CONFIG_MACRO_DIR([m4])' to configure.in and
libtoolize: rerunning libtoolize, to keep the correct libtool macros in-tree.
configure.in:34: warning: AC_CACHE_VAL(ogre_prog_compiler_supports_visibility, ...): suspicious cache-id, must contain _cv_ to be cached
../../lib/autoconf/general.m4:2018: AC_CACHE_VAL is expanded from...
../../lib/autoconf/general.m4:2039: AC_CACHE_CHECK is expanded from...
Scripts/m4/libtool.m4:1402: _LT_COMPILER_OPTION is expanded from...
Scripts/m4/libtool.m4:1444: AC_LIBTOOL_COMPILER_OPTION is expanded from...
configure.in:34: the top level
configure.in:34: warning: AC_CACHE_VAL(ogre_prog_compiler_supports_visibility, ...): suspicious cache-id, must contain _cv_ to be cached
../../lib/autoconf/general.m4:2018: AC_CACHE_VAL is expanded from...
../../lib/autoconf/general.m4:2039: AC_CACHE_CHECK is expanded from...
Scripts/m4/libtool.m4:1402: _LT_COMPILER_OPTION is expanded from...
Scripts/m4/libtool.m4:1444: AC_LIBTOOL_COMPILER_OPTION is expanded from...
configure.in:34: the top level
configure.in:34: warning: AC_CACHE_VAL(ogre_prog_compiler_supports_visibility, ...): suspicious cache-id, must contain _cv_ to be cached
../../lib/autoconf/general.m4:2018: AC_CACHE_VAL is expanded from...
../../lib/autoconf/general.m4:2039: AC_CACHE_CHECK is expanded from...
Scripts/m4/libtool.m4:1402: _LT_COMPILER_OPTION is expanded from...
Scripts/m4/libtool.m4:1444: AC_LIBTOOL_COMPILER_OPTION is expanded from...
configure.in:34: the top level
configure.in:34: warning: AC_CACHE_VAL(ogre_prog_compiler_supports_visibility, ...): suspicious cache-id, must contain _cv_ to be cached
../../lib/autoconf/general.m4:2018: AC_CACHE_VAL is expanded from...
../../lib/autoconf/general.m4:2039: AC_CACHE_CHECK is expanded from...
Scripts/m4/libtool.m4:1402: _LT_COMPILER_OPTION is expanded from...
Scripts/m4/libtool.m4:1444: AC_LIBTOOL_COMPILER_OPTION is expanded from...
configure.in:34: the top level
configure:16145: error: possibly undefined macro: AC_MSG_ERROR
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.

```

I would want to run cmake-gui, but theres no Cmakelist.txt!

Also do I need the nvidia CG stuff? I don't have a nvidia graphic card.

Thanks!

---

### Post by Axel-P on 2010-04-28
I finally did it!

So I did MANY things. So here's a hint:

[This is the official tutorial]("http://ubuntuforums.org/showthread.php?t=1144592"), it didn't work for me.

[This]("http://www.cegui.org.uk/phpBB2/viewtopic.php?f=10&t=4499&start=0") is for a CEGUI related issue

[This]("http://www.ogre3d.org/forums/viewtopic.php?f=2&t=40991&start=25") is troubleshooting for a error: &#8216;RAND_MAX&#8217; was not declared in this scope      when trying to build CEGUI

[This]("http://www.cse.unr.edu/~lagoon/index.php/SGE") is for a ILvoid related issue.

[This]("http://www.ogre3d.org/wiki/index.php/BuildingFromSource_Shoggoth#Ubuntu_.2F_Kubuntu") is a tutorial that actually helped me.

[This]("http://www.ogre3d.org/forums/viewtopic.php?f=2&t=47860") is for an undefined reference while compiling a project

Right now I don't have "good" projects. In other words, I have all referenced headers in the project's main folder instead of only having them in the corresponding include folder. I'll try to fix that, when I get a nice fix I'll post it, in the mean time, any suggestions are welcomed!

Hope it helps.


Note: I DO google stuff, a LOT :D

---

