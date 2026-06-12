---
title: "&quot;make&quot; successful, but wont &quot;install&quot;"
date: 2011-03-24
forum: Packaging and Compiling Programs
---

### Post by Irvine_himself on 2011-03-24
I use Blender and MakeHuman, which are both undergoing rapid development and as a result, the version updates need to be kept in sync. MakeHuman has a nightly build and Blender is updated using subversion. I got the Blender SVN installed and updating fine without any problems.

Now the real problem is that I have a dial up modem with a very low bandwidth of about 3kb/s and dislike having my internet connection being tied up for most of each day downloading the latest nightly builds, it would be preferable to use MakeHuman SVN since it only updates the bits that have been changed. Unfortunately, I cannot find a clear and concice guide on how to install MakeHuman SVN.
 
Anyway, not being faint-hearted, I noticed that there were various files such as Makefile.linux, Makefile.osx.... etc and after some experimentation, I copied the Makefile.linux, renamed it to Makefile and then ran "make" .... result, it worked and can now launch the MakeHuman SVN from inside the source directory. 
 
Now the problem is  that any combination of install gives errors,.for example I have tried many other combinations of  the following: 

```
~/makehuman-svn/makehuman-read-only/makehuman$   **install ~makehuman-svn/makehuman-build  **
[I]install: missing destination file operand after `~makehuman-svn/makehuman-build 
Try `install --help for more information. [/I]
 
~$   **install ~makehuman-svn/makehuman-read-only/makehuman ~makehuman-svn/makehuman-build ** 
*install: omitting directory `~makehuman-svn/makehuman-read-only/makehuman *
 
~/makehuman-svn/makehuman-read-only/makehuman$   **sudo make install ~makehuman-svn/makehuman-build  **
*make: *** No rule to make target `install. Stop. *
 
~/makehuman-svn/makehuman-read-only/makehuman$  ** sudo install ~makehuman-svn/makehuman-build  **
[I]install: missing destination file operand after `~makehuman-svn/makehuman-build 
Try `install --help for more information. [/I]
 
~/makehuman-svn/makehuman-read-only/makehuman$  ** install ~makehuman-svn/makehuman-read-only/makehuman -T ~makehuman-svn/makehuman-build ** 
*install: omitting directory `~makehuman-svn/makehuman-read-only/makehuman *
 
~/makehuman-svn/makehuman-read-only/makehuman$  ** install ~makehuman-svn/makehuman-read-only/makehuman ~makehuman-svn/makehuman-build**  
*install: omitting directory `~makehuman-svn/makehuman-read-only/makehuman *
 
~/makehuman-svn/makehuman-read-only/makehuman$  ** sudo make install **
*make: *** No rule to make target `install. Stop.*
```Could anybody please give me some guidance here, because I am lost
.

---

### Post by MadCow108 on 2011-03-24
this
> 
sudo make install 
make: *** No rule to make target `install. Stop. 
indicates that the makefile does not have a install target (or the makefile is buggy), so there might be nothing you can do about it (besides adding one yourself)

---

### Post by Irvine_himself on 2011-03-24
> **MadCow108 said:**
>  the makefile does not have a install target (or the makefile is buggy), so there might be nothing you can do about it **(besides adding one yourself)**

As you may have noticed, I am not an expert at this. In the past I have tried to edit Makefiles for obstreperous installations and have always found it to be be  an exercise in futility and delusion.

Would anyone care to hazard a guess at what is wrong with this Makefile and how I could add a rule to make a target?

Alternativly, after running "make" and before trying to "install", I have an executable file in the  makehuman folder which launches Makehuman.  So, failing to get it installed, is there any problem in just running  this un-installed version?

```
CSRCS = src/core.c src/glmodule.c src/arraybuffer.c src/main.c

DEPS = $(addsuffix .d,$(basename $(CSRCS) $(CCSRCS) ))
OBJS = $(addsuffix .o,$(basename $(CSRCS) $(CCSRCS) ))

CCOPTS = -Wall -O0 -g

PYTHONVER     = 2.6
EXTRAFMWKS    = -lX11 -lGL -lGLU -lSDL -lGLEW
EXTRALIBS     = -lpython$(PYTHONVER)
EXTRADEFINES  =
INCLUDEPATH   = -I/usr/include/SDL/ -I/usr/include/python$(PYTHONVER)/ -I/usr/X11R6/include -I./include

EXE = makehuman

    
%.o : %.c
    @echo "compiling C file $< to $@ ..."
    @gcc -c -MMD $(CCOPTS) $(INCLUDEPATH) $< -o $@

%.o : %.cpp
    @echo "compiling C file $< to $@ ..."
    @g++ -c -MMD $(CCOPTS) $(INCLUDEPATH) $< -o $@

%.o : %.m
    @echo "compiling ObjC file $< to $@ ..."
    @gcc -c -MMD $(CCOPTS) $(INCLUDEPATH) $< -o $@

%.o : %.mm
    @echo "compiling ObjC++ file $< to $@ ..."
    @g++ -c -MMD $(CCOPTS) $(INCLUDEPATH) $< -o $@

$(EXE) : $(OBJS)    
    @echo "linking as $@ ."
    @g++ $(EXTRALIBS) $(EXTRAFMWKS) $(OBJS) -o $@

# ---------------------------------------------------------------------
# Cleanup unused stuff
# ---------------------------------------------------------------------
clean:
    $(RM) $(OBJS) $(DEPS) *.obj *~ *.bak *%% *~ makehuman
    find apps -name "*.pyc" -exec "rm" "-f" {} ";"
    find utils -name "*.pyc" -exec "rm" "-f" {} ";"
    find core -name "*.pyc" -exec "rm" "-f" {} ";"

# ---------------------------------------------------------------------
# Include dependencies if exists
# ---------------------------------------------------------------------
-include $(DEPS)
```

Any help is gratefully appreciated
.

---

### Post by Bucky Ball on 2011-03-24
Just wondering why, if you have a version of each that work together, you would want to be downloading nightly builds? Do you have an overwhelming desire to have the absolute latest version or is there another reason why you would attempt to fix something that's not broke? ;)

---

### Post by Irvine_himself on 2011-03-24
> **Bucky Ball said:**
> Just wondering why, if you have a version of each that work together, you would want to be downloading nightly builds? Do you have an overwhelming desire to have the absolute latest version or is there another reason why you would attempt to fix something that's not broke? ;)

Whats broken is my Internet connection..... Although it is free, it is also very very slow and updating from the Makehuman-SVN liberates a significant amount of bandwidth. 

The rate of current development with regard to using MakeHuman and Blender in combination is such that it is worthwhile updating about once a week or so, but whereas I can update Blender-SVN in a matter of minutes, the MakeHuman nightly takes several hours. Using the MakeHuman-SVN I can update the whole thing in about 5 minutes, since I am only downloading what has been changed as oppose to a completed installation

.

---

### Post by MadCow108 on 2011-03-24
> **Irvine_himself said:**
> 
Alternativly, after running "make" and before trying to "install", I have an executable file in the  makehuman folder which launches Makehuman.  So, failing to get it installed, is there any problem in just running  this un-installed version?


you'll have to ask that the developers.
But as the makefile has no install target it is likely that the file alone is fine.

---

### Post by Irvine_himself on 2011-03-24
> **MadCow108 said:**
> But as the makefile has no install target it is likely that the file alone is fine.

Thanks, I feel you are correct, but have no expertise to base this on. The Makefile compiles and links the various source files without reporting any errors or warnings. The problems only start when I try to install and I was only doing that because all the generic guides to compiling from source have this as the final step.

Another example of strangeness is that there was no configure file so that the  generic recommended step prior "make", ["./configure",] did not work either.

---

### Post by MadCow108 on 2011-03-24
not all builds use the configure, make, (make check), make install method.
This is mostly the case for packages using autotools, other systems may be built differently.
some do not even use make.

but autotools based packages are currently the majority. Although newer software tends to use other systems (cmake, scons, distutils...)

---

### Post by Irvine_himself on 2011-03-24
I hope developers read and take note of this, (and the many similar posts by other people,) and realize the importance of including some guidance on how to install their packages. As I have said many times, you can write the best software in the world but if people can't install it, it is  just so much waisted effort. 

It does not have to be a deb installer, it just needs good documentation.
.

---

### Post by Irvine_himself on 2011-03-25
In case anyone else has this problem I have found the solution:

MakeHuman-SVN uses scons and hence running scons in the MakeHuman-SVN folder is all that is need to successfully compile the source.:P

References:

[This link]("http://makehuman.blogspot.com/2010/08/update-your-nightly-build-smart-way.html") gives an incomplete but easy way of updating MakeHuman-SVN

Whereas, buried deep in [this link]("http://sites.google.com/site/makehumandocs/developers-guide") is a fuller description
.

---

