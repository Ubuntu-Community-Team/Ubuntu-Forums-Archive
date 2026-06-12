---
title: "[C++/MinGW]  Trying to Debug"
date: 2010-05-21
forum: Programming Talk
---

### Post by dodle on 2010-05-21
I am cross-compiling to Win32 with MinGW/g++.  Compiling the program succeeds, but when I try to run the Win32 executable I get the following error:
```
wine: Unhandled page fault on write access to 0x00667ab0 at address 0x7bc48208 (thread 0009), starting debugger...
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x7bc48208
```

Is there a way to find, in the source code, where 0x00667ab0 and 0x7bc48208 are referenced?  I'm trying to use the MinGW debugger, but I don't have a lot of experience with debugging.

Also, if I compile the program for Ubuntu, it appears to work fine.

**Edit:** Something I forgot to mention; here is the output from when I try to run the debugger:
```
Reading symbols from H:\Programming\C++\ABC/abc.exe...done.
(gdb) Exception condition detected on fd 0
error detected on stdin
```

---

### Post by dwhitney67 on 2010-05-21
> **dodle said:**
> 
Also, if I compile the program for Ubuntu, it appears to work fine.


Did you run the program (under Ubuntu)?  Use valgrind to find places where you *may have* inadvertently overwritten a buffer, and thus corrupted the program's stack/heap.

---

### Post by mmix on 2010-05-21
not sure, but, sound like wine bug.

---

### Post by dodle on 2010-05-23
> **mmix said:**
> not sure, but, sound like wine bug.

I think you may be mostly right, although I did as dhwhitney said and ran valgrind which did return some errors.  So I know I've got some memory issues to deal with.  But, I compiled my program on my WinXP machine and it appears to work fine.  

I did end up changing some things around in the source, so I'll try re-compiling it again on Ubuntu later with the updated source and see if it works.

---

### Post by dodle on 2010-05-24
Yep, the same code that I compile on WinXP that runs fine, comes back with those errors when compiled on wine.  

Compiled on XP:
[list][*]runs on XP[*]runs on wine[/list]
Compiled on wine:
[list][*]does not run on XP[*]does not run on wine[/list]

I'm not sure which part of the code wine has trouble with.  I have compiled wx apps before that worked fine.

---

