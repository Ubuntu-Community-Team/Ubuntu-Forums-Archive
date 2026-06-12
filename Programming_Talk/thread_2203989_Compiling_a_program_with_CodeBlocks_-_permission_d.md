---
title: "Compiling a program with Code::Blocks - permission denied"
date: 2014-02-06
forum: Programming Talk
---

### Post by Attila_Toth on 2014-02-06
Hello!
Yesterday I've decided to switch from Windows to Ubuntu, and I wanted to start programming with Code::Blocks (on Windows I used Code::Blocks), but everytime I want to compile my program it drops **Permission denied**. I've looked for the solution, I tried with *chmod*, *chown* and stuff, but none of these worked. Please help me, I want to start programming on Ubuntu :-|. 
Thanks in advance, Attila.

---

### Post by Joeb454 on 2014-02-06
Is there any other error displayed other than permission denied?

Also the code you're trying to compile (and the folder the compilation will output to), where are they located on your system? E.g. /home/your_user, or /code

---

### Post by TheFu on 2014-02-06
I don't know anything about Code::Blocks.

The basics of programming are the same. Assuming you use TDD
* write test cases
* write code
* compile code
* run code
* run test cases to see what isn't working
* debug until all test cases work
* Repeat

UNIX programming (Linux is like UNIX in 95% of everything), uses directories and files. Most of the programming will be performed in a subdirectory under your HOME, therefore YOUR userid will be the owner and have full writes - read, write, execute and YOUR userid will have control over the permissions.

Using any IDE is dangerous at this point, because you don't yet understand the OS and environment.  IDEs are a productivity tool, but they don't replace knowledge of the system.

Let's skip the testing parts now and get something to compile.  C or C++?
For c programs, the compiler is invoked by:
```
gcc -c main.c
```
If you want to link AND compile at the same time, use:
```
gcc -o main -c main.c
```

Of course, any libraries referenced will need to be added to the compile (headers) and link (.a or .so) lines.  Most people start out typing it all in, then quickly move to using a shell script and finally switch to using Makefiles.

I guess you'd probably prefer someone with code-blocks experience to tell you exactly what you did wrong. That isn't me.  I can only recommend that you check the directories where the output is written - it needs to be under your HOME somewhere.
I can also point to a simple file permissions link: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) to get started on a better understand of those things.  Since almost everything on UNIX is a file, these permissions are critical to understanding everything - mouse, keyboard, GPU, monitor, network cards - these are all just special files with UNIX-style permissions.

---

### Post by Attila_Toth on 2014-02-06
Thanks for the response guys. @Joeb454 There isn't any other error than Permission denied, my code is located in: /media/Local Disk/Programs/Ubuntu/C++, @TheFu and I program in C++...

---

### Post by howefield on 2014-02-06
Thread moved to the "*Programming Talk*" forum.

---

### Post by TheFu on 2014-02-06
> **Attila_Toth said:**
> Thanks for the response guys. @Joeb454 There isn't any other error than Permission denied, my code is located in: /media/Local Disk/Programs/Ubuntu/C++, @TheFu and I program in C++...

**Copy the code and all related files to be under your HOME directory.** It should work from there. I suspect that external disk is NOT using a UNIX file system - you cannot easily build programs that way. FAT32 and NTFS cannot be used.

For C++, filenames and/or case matters.
These are acceptable extensions for C++ ( .cc, .C, .cpp, .CC) Notice the case sensitive aspect? UNIX file systems are case sensitive.
And the C++ compiler is "g++" - besides that, try the same commands.

---

### Post by Attila_Toth on 2014-02-06
Thanks @TheFu, from HOME directory it works fine! **THANK YOU!**

---

