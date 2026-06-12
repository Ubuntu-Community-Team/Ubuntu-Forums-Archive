---
title: "g++ makefile problem"
date: 2007-02-27
forum: Programming Talk
---

### Post by 2many2count on 2007-02-27
I'm learning to create makefiles for my g++ code and I could use some help with an error I'm getting.  I have the compile section of the makefile working ok, but I can't get my "clean" section to work.  When I enter the command,  "make clean" from the command prompt, I get the following error:

make : *** No rule to make target 'clean'. Stop.

Here is my make file:
==================================

# Compile-Assemble-Link project:
rc: rc.cpp io.o io.h
        g++ rc.cpp io.o -o rc
#
# Compile and Assemble components:
io.o: io.cpp io.h
        g++ -c io.cpp
#
# File cleanup:
clean:
        -rm -f *.o core

Can anyone tell me what the problem is with the makefile?  Note: Even though the message doesn't show it, there are correct tabs on each build line as expected.

Thanks.

---

### Post by lnostdal on 2007-02-27
ok, this doesn't really answer your question but i'm going to suggest that you should use another build-tool when you have this opportunity

examples are
* scons ( sudo aptitude install scons )
* cmake

..i know scons well and can help you get started with it; it is a major improvement over plain make (which has many flaws) ..

 a SConstruct-file that does the same thing as your Makefile looks like:

```

# Construction environments
###########################

dbg = Environment(CCFLAGS = '-g -Wall -std=c99',
                  CXXFLAGS = '-g -Wall')

rel = Environment(CCFLAGS = '-O2 -Wall -std=c99',
                  CXXFLAGS = '-O2 -Wall')


# Current set environment
#########################
env = dbg


env.Program('rc', ['rc.cpp', 'io.cpp'])

```

and..that's it! .. type scons -u to build, and scons -c to clean .. and ask if you have any problems getting started

---

### Post by WW on 2007-02-27
I cut-and-pasted your example into a file, added tabs in front of the g++ and -rm lines, and saved it as Makefile.  Then the command "make clean" worked fine for me.  Did you run the command in the correct directory?  Is your file named "Makefile" or "makefile"? (To use any other name, you will have to use the -f option with the make command.)  You will get the error "make: *** No rule to make target `clean'.  Stop." if the make command doesn't find "Makefile" or "makefile" (or if there is no "clean" target in the file).

If you do have the Makefile in the directory where you ran "make clean", how about attaching it to a post here, so we can see *exactly* what is in the file.

I agree with Inostdal that using something like scons or cmake would be better in the long term, but it is definitely worthwhile to learn how to create and use a basic Makefile.

---

### Post by 2many2count on 2007-02-27
WW,
Thank you for your reply and for running the makefile.  That helps knowing the syntax for the file is correct.  The name of the file is Makefile.  I run the command line command "make clean" from the the directory where the makefile is located and where the .cpp source files are located.    So I'm not sure what is causing the error.  Any suggestions where to go from here?

On the question of another make tool.  I have learned over the years to use the tools you have at hand first, then explore other alternatives.  Changing because you can't get it to work sometimes causes more problems in the long run.  Having come from using Visual Studio for quite a while, the g++ compiler with Gedit and make is rather refreshing.  I've gotten rather tired of complicated, bloated tools.  Simplicity has it's place.  *grin*

Thanks guys for your help.

---

### Post by WW on 2007-02-27
There must be something wrong in your version of the Makefile.  I have attached my version of the file you posted earlier. (I had to gzip it in order to attach it here.)  Is it the same as yours?  Save it in a different directory (say, /tmp), and try "make clean" in that directory (you won't need the source code files just to test "make clean").

---

### Post by 2many2count on 2007-02-27
Well, you are right.  There must have been a format mistake somewhere.
Here is the results which is now correct with the makefile you sent me back.

> cd testing
> ls 
Makefile  Makefile.gz
> make clean
rm -f *.o core
> 

Maybe I had a space somewhere.  Well, thank you both for your help.  I love this
forum and Ubuntu(Linux)!  Take care.

---

### Post by lnostdal on 2007-02-27
> **2many2count said:**
> 
On the question of another make tool.  I have learned over the years to use the tools you have at hand first, then explore other alternatives.  Changing because you can't get it to work sometimes causes more problems in the long run.

this is true when you have a significant investment in tools you already know - it is not so true when this is not the case as i believe this to be here (edit: at the starting cross-roads)

i strongly suggest you to reconsider when you clearly have the opportunity of a better way with absolutely no significant "step back" for relearning

i'll even promise to help you so you'll have immediate equivalent and even _better_ results than what you already have or are able to do with `make' at all times

.. if you don't believe me i'll stop "bothering" you .. :)

> 
  Having come from using Visual Studio for quite a while, the g++ compiler with Gedit and make is rather refreshing.  I've gotten rather tired of complicated, bloated tools.  Simplicity has it's place.  *grin*


i agree completely, and that is why you should know that `make' does have _actual flaws_ that complicate things instead of simplify them  .. this is _not_ a matter of taste or personal opinion/preferences from my side .. this makes `make' _more_ complex and hard to use than for instance scons .. 

setting up Gedit to call "scons -u" instead of "make" is a trivial task and you will save time and be more productive in this way without losing _any_ simplicity (you gain it) or "to the bones" knowledge/control

---

### Post by 2many2count on 2007-02-28
lnostdal ,
I agree with that and you are not bothing me.  I still have a lot to learn about programming tools for Ubuntu/Linux.  Sometimes the number of applications/utilities available in Linux can be overwhelming trying to find solid reliable tools.  I will be installing scons tonight look forward to discussing it with you once I get it installed and played with it some.  Thanks for writing back and I hope we can discuss scons again soon.  Thank you for your help.  Take care.

---

### Post by 2many2count on 2007-02-28
Ok, I found the problem.  As WW said, it was a formatting issue.  I have two PCs, one running desktop and the other server.  I was using Gedit for my makefile editing on my desktop pc and the makefile worked fine.  I had to use nano on my server box.  Nano was inserting spaces for the tab.  Is there a way to configure nano to use a tab instead of spaces for a tab?  I used VI (yuck) and fixed the problem.

Now I can get on to exploring scons as lnostdal suggested.  Thanks again for the help.

---

### Post by lnostdal on 2007-02-28
> **2many2count said:**
> Ok, I found the problem.  As WW said, it was a formatting issue.  I have two PCs, one running desktop and the other server.  I was using Gedit for my makefile editing on my desktop pc and the makefile worked fine.  I had to use nano on my server box. 

sshfs is great for remote editing:

```

sshfs lars@nostdal.org:/ ~/mounts/nostdal.org
cd ~/mounts/nostdal.org/home/lars/public_html
gedit index.html

```

~/mounts/nostdal.org is just a directory i use as a mount-point in my home-folder as you see .. (i watch DVD movies from my server over the wireless network using this btw.)

you use *fusermount -u -z ~/mounts/nostdal.org* to unmount

you can also execute a command remotely, like this:

```

lars@ibmr52:~$ ssh lars@nostdal.org gcc --version
gcc (GCC) 4.1.2 20061028 (prerelease) (Debian 4.1.1-19)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

lars@ibmr52:~$ 

```

..so you can both edit and trigger compilation (execute scons -u) on a remote computer :)

> 
 Nano was inserting spaces for the tab.  Is there a way to configure nano to use a tab instead of spaces for a tab?  I used VI (yuck) and fixed the problem.

that's weird; i tried nano here just now (ubuntu feisty) and it inserts a tab-character (0x09) when i press tab .. the -E argument to nano converts tabs to spaces but that's probably not the problem

---

### Post by 2many2count on 2007-02-28
Sorry, but I need to ask one more question as an obvious new linux user.  When I enter the command below to connect to my server, it asks me for the server password and then  I get a 'permission denied' error back:

> sshfs myserve@192.168.1.60: /dev

Can you tell me what I need to do on the server to allow this command?  I assume I only need to have sshfs installed on my desktop client box.  By the way, I can remote the server fine running ssh through a terminal session on my client desktop pc, but sshfs gives me the 'permission denied' error.

Thanks

---

### Post by lnostdal on 2007-02-28
you are trying to mount a filesystem at /dev .. that doesn't make much sense; you shouldn't do that

instead you should create a directory in your home folder .. call it myserve for instance .. like this:

```

cd ~
mkdir myserve

```

you can now use this unused and empty directory as a *mount point* .. so do:

```

sshfs remoteusername@192.168.1.60:/ myserve

```

note that that will mount the remote root-folder (/) at ~/myserve .. you can mount any remote folder you like .. for instance:

```

sshfs remoteusername@192.168.1.60:/home/somefolder myserve

```

looking at the man-page (man 1 sshfs) you'll see:

```

sshfs [user@]host:[dir] mountpoint

```

---

### Post by 2many2count on 2007-02-28
Sorry Lars,
That wasn't a very smart directory name on my part.  Actually, I had created a directory called "dev" under my home directory.  /home/dev  I wasn't pointing to /dev.  Your explanation was great.  I t worked fine after your explanation.   Thanks.

---

