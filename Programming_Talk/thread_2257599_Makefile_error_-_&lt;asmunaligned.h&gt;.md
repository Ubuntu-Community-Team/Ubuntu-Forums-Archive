---
title: "Makefile error - &lt;asm/unaligned.h&gt;"
date: 2014-12-21
forum: Programming Talk
---

### Post by Ian.kz.ma on 2014-12-21
I'm following a set of instructions to put together a build and after typing 'make' I get an error:

In file included from libavformat/mov.c:41:0:
./libavformat/zlib.h:7:27: fatal error: asm/unaligned.h: No such file or directory
 #include <asm/unaligned.h>
                                      ^
I found asm.h and unaligned.h and copied both to libavformat directory but it does not solve the error. I've not seen a preprocessor directive in that format before.
I have searched everywhere for a fix but have not found one. I've been told "This make is building host binaries: you should use codesourcery not mipssde".
I'm not sure what this means....any help would be much appreciated. Thanks for your time~

Edit: formating

---

### Post by TheFu on 2014-12-21
What package are you trying to build? Normally the source package will include build instructions in either a README or INSTALL or BUILD text file.

It looks like the include path just isn't correct.  That would be the -I (capital eye) in the makefile, but there isn't anyway to be certain. It is usually (always?) a bad idea to move a header file.  That file is needed to build the library and that much happen first before building the program.  Then the makefile uses the .h and library to link the program - either static or shared libraries.

Seems like the "fix" may have come from someone either in a hurry or who doesn't speak English natively.

---

### Post by Ian.kz.ma on 2014-12-21
Thanks for the reply.

I'm not quite sure what package I'm building, I believe Its a type of media package since the directory I'm in is "Media". As for the headers I did not move them, I copied them, so there is no absence of the original file in it's original location.

Most google results stated it was a linux bug....but I find it hard to believe that. I also did a $find . -name "<asm/unaligned.h>" and found nothing. 

I also checked the configs and readmes, nothing in there except licensing stuff. I'm an intern and our team is extremely resource starved, so answers I receive are often un-detailed/poorly written. Our company in general has poor documentation.

What kind of header file has a "/" in it? Does the slash in asm/unaligned mean anything? Might help me debug

---

### Post by TheFu on 2014-12-21
If you aren't at a command line, this will be difficult.
You cannot build UnIX/Linux software easily on non-Linux formatted drives.
Also - searching for "<asm/unaligned.h>" will NEVER find anything.  You need to look for "unaligned.h" from / ... or install locate and use that tool instead - it is almost instantaneous.

The asm/something.h means the something.h file is in a relative directory below the included "include path" - based on the -I settings inside the Makefile.  Any UNIX C programmer should be able to solve this in 3-5 minutes.  Talk to the dev team.

---

### Post by ofnuts on 2014-12-21
Usually the "asm" directory in include files is hardware specific, and is usually a link to one of the "asm-architecture-or-bitness" directories found elsewhere ("asm_x86_32", "asm_x86_64", "power_64" or else).

---

### Post by Ian.kz.ma on 2014-12-21
> **TheFu said:**
> If you aren't at a command line, this will be difficult.
You cannot build UnIX/Linux software easily on non-Linux formatted drives.
Also - searching for "<asm/unaligned.h>" will NEVER find anything.  You need to look for "unaligned.h" from / ... or install locate and use that tool instead - it is almost instantaneous.

The asm/something.h means the something.h file is in a relative directory below the included "include path" - based on the -I .  Any UNIX C programmer should be able to solve this in 3-5 minutes.  Talk to the dev team.

I'm sorry I forgot to mention. My work PC is x32 windows but I installed VirtualBox and mounted ubuntu, so this is all done in my ubuntu environment with the command line. 

Thank you for your advice, I'll continue to try and debug until tomorrow.

---

### Post by TheFu on 2014-12-21
> **Ian.kz.ma said:**
> I'm sorry I forgot to mention. My work PC is x32 windows but I installed VirtualBox and mounted ubuntu, so this is all done in my ubuntu environment with the command line. 

Thank you for your advice, I'll continue to try and debug until tomorrow.

Did you mount the Ubuntu file system to Windows
or
are you running Ubuntu inside a virtual machine and using on the Linux file system for all this work?

The 1st won't work for building Linux C software. The 2nd will. If you've accessed Windows steroage from inside Ubuntu using the "shared folders" for virtualbox, that won't work either.

---

### Post by Ian.kz.ma on 2014-12-22
> **TheFu said:**
> Did you mount the Ubuntu file system to Windows
or
are you running Ubuntu inside a virtual machine and using on the Linux file system for all this work?

The 1st won't work for building Linux C software. The 2nd will. If you've accessed Windows steroage from inside Ubuntu using the "shared folders" for virtualbox, that won't work either.

I am running ubuntu inside a virtual machine and using the Linux file system for all this work.

Since my last post I've been trying to edit the -I in the makefile to include as many directories as possible within the project. Tomorrow I work, I'll see what I can get from the devs if anything.

edit: spelling

---

### Post by TheFu on 2014-12-22
> **Ian.kz.ma said:**
> I am running ubuntu inside a virtual machine and using the Linux file system for all this work.

Since my last post I've been trying to edit the -I in the makefile to include as many directories as possible within the project. Tomorrow I work, I'll see what I can get from the devs if anything.

edit: spelling

Good on doing everything inside a VM.

The order of includes matters. Be careful.  It is probably best to just ask the dev team. Also - whenever you do change that order, rebuild everything from scratch - usually there is a 'make cleanall' target which will clean up any files from prior attempts.

---

### Post by Ian.kz.ma on 2014-12-23
We traced the problem to codesourcery. After many hours we discovered during my codecourcery download, I failed to acquire a certain package because I did not have svn permission.

I got the missing package, did a make, and it has passed the directory where the problem occurred. Everything should be fine now.

Thanks for replying back to my posts~

---

