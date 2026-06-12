---
title: "Release debugging"
date: 2006-07-29
forum: Programming Talk
---

### Post by vek on 2006-07-29
Hello there.  I'm still getting into linux dev here, got a few apps working cleanly now, but I have a few loose ends to tie up.  Perhaps some seasoned coders can help me here.

How do y'all debug your release applications?  For example, those that are in the public, and crashing.  Is there some standard way?

In the current windows environment, I have the app save a minidump out to file, and keep the program database (pdb file) for that particular release, and the source code.  Then if it crashes, I get ahold of the minidump, double click it, and through automagic, goes directly to the line number/source code where it crashed.  It even has the complete stack, with function names and everything.   Its multi-thread safe, even.

Is there a clean way to reproduce this same behavior in a linux environment?  Once my programs start to get more complex, I'm going to need to be able to accept some sort of crash dump (cores perhaps) and quickly get to the stack  / file source, without having to go through some crazy procedure of looking up source offsets in map files, etc... and it needs to be from release-compiled binaries that themselves have no debugging information embedded.  I'm sure there's a way to do this... windows can... but how?  Ideally it'd be just as clean - open the core file up in some sort of IDE, and have it show the stack / go directly to the C++ source where the error occured.  

It doesnt matter if I have to use a special library to do this, or code the program in a specific way - since I'm just starting out, I can establish those procedures right now, to save myself time and effort later.  So long as it doesnt take me ages, later on, to get to 'where it crashed'.

So... anyone got suggestions / help?

---

### Post by Harleen on 2006-07-29
So you want information about where your program crashed for a version without debugging symbols? I don't think this is possible. For a release version the compiler optimises your code, meaning it rearranges the statements in your code and may substitute function calls with the function's content. If your program crashed at these changed statements, where should the debugger set the pointer to? I also doubt, that MS Visual Studio can do this.
If you compile without optimisation, you may get some useful output. But you won't get more information than the function name of the crash, as line numbers and variable names are not contained in the binary. And I don't know of any way to get a debugging symbol table in a separate file, as it is dony by MS (with the pdb file).
For useful core dumps you need to compile with debugging symbols. Than your program will create a useful core dump on a crash.

To get a core dump, you have to allow applications to create those dumps. This is disabled on Ubuntu on default but can be enabled by calling "ulimit -c unlimited" which sets the maximum allowed disk space that can be occupied by a core dump to "unlimited" (only for applications started from the current shell!). After that, each crashing application will create a core dump, which then can be loaded into the debugger.

---

### Post by vek on 2006-07-30
MS visual studio can do this, its how we debug our release programs.  Basically, it generates a program database when it compiles.  This program database is very big, but contains a code map (its a giant binary file) which is able to associate each generated assembly instruction with the line in the source code that it comes from (and has much more info, too).  Its not 100% accurate but its pretty darn good.

Obviously, you don't ship the program database, you just ship the release compiled executable.  You also have to make sure that if the program crashes, the exception is handled by a mini-dumping handler, which can save the dump file somewhere useful.  Its a few short lines of code.

Then when the program crashes, even if it has no symbols, the mini-dump, the executable, and the program database can be loaded.  With all three of those, the entire stack becomes available and so does every line / function, in a very high degree of accuracy.

Now I'm sure there's a way to do something like this, in a ubuntu/linux environment, because, well, linux is always the programmer's OS... so ... how is it done?  What tools generate a nice program database, and what other tools read them.  Its probably just a matter of finding the correct packages...

Without a program database, its still possible to debug running code, because some compilers generate a code map (text .map file) which is similar, albeit less info, and rough ascii.  Given a .map file its also possible to locate whereabout in the code the program is.

NOte that, yes, optimizing compilers make it a little harder - it might be off by one or two lines, but VS2005 lets you view both the dissassembly and the source, intertwined with each other, so that you can reconstruct what happened.  Its been able to do this for years.  And when it comes to programming stuff like that, generally, linux leads the way.  So ... I'm just hoping someone out there knows what the linux equivalent is.  I know intel's VTUNE works for linux applications too - and that runs off the program database also.

---

