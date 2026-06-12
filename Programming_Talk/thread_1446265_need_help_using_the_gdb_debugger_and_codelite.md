---
title: "need help using the gdb debugger and codelite"
date: 2010-04-03
forum: Programming Talk
---

### Post by Jonas thomas on 2010-04-03
I'm trying to use the gdb debugger on a single file cpp and I'm getting some error messages that have me perplexed.  I've set a break point F9 and engaged the debugger via F5 and I get this message in the the terminal session.
```

&"warning:  GDB: Failed to set controlling terminal: Operation not permitted\n"
```

and this message in the IDE debugger:
```
Debug session started successfully!
Debuggee process ID: 7608
GNU gdb (GDB) 7.0-ubuntu
Copyright (C) 2009 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i486-linux-gnu".
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>...
Reading symbols from /home/jonas/.codelite/CppClass/hw_lab_7/Debug/hw_lab_7...
done.
set unwindonsignal on
set breakpoint pending on
set width 0
set height 0
Found the breakpoint ID!
Storing debugger breakpoint Id=1
Successfully set breakpoint 1 at: address 0
Found the breakpoint ID!
Storing debugger breakpoint Id=2
Successfully set breakpoint 2 at: address 0
ERROR: failed to place breakpoint: "^error,msg="No source file named /home/jonas/.codelite/CppClass/HW_project2/HW_Project.cpp.""
No source file named /home/jonas/.codelite/CppClass/HW_project2/HW_Project.cpp.
Found the breakpoint ID!
Storing debugger breakpoint Id=3
Successfully set breakpoint 3 at: /home/jonas/.codelite/CppClass/hw_lab_7/hw_lab_7.cpp:18
=thread-group-created,id="7608"
=thread-created,id="1",group-id="7608"
Continuing...
*running,thread-id="all"
=library-loaded,id="/lib/ld-linux.so.2",target-name="/lib/ld-linux.so.2",host-name="/lib/ld-linux.so.2",symbols-loaded="0"
Warning:\nCannot insert breakpoint 1.\nError accessing memory address 0x0: Input/output error.
```

At this point, I would like to use the debugger to finish my homework but at this point, I'm spending a heck of lot more time researching the debugger than working on the homework.. :(

I'm currently rtfm'ng [http://codelite.org/LiteEditor/Debugging]("http://codelite.org/LiteEditor/Debugging") hopefully this will make sense, but so far not...

Apparently, I'm not alone in this issue
[http://sourceforge.net/users/dymaxionuk]("http://sourceforge.net/users/dymaxionuk")

---

### Post by gnometorule on 2010-04-03
I run gdb directly with gcc/g++, so don't know your ide. However, a cursory look shows that breakpoints seem to be set properly in one file, and fail to be set in another file. At the top, you write that you try to debug a 'single file.' Something here seems fishy. Have a look at that.

---

### Post by Jonas thomas on 2010-04-03
> **gnometorule said:**
> I run gdb directly with gcc/g++, so don't know your ide. However, a cursory look shows that breakpoints seem to be set properly in one file, and fail to be set in another file. At the top, you write that you try to debug a 'single file.' Something here seems fishy. Have a look at that.

Thanks for the quick reply. I was using the version of codelite that was in synaptic.  On a whim, I downloaded the latest version of codelite from [http://sourceforge.net/projects/codelite/]("http://sourceforge.net/projects/codelite/") and debug seems to work perfectly now.  (In hind-site I wish I did that first. Although the last time I downloaded  codelite from sourceforge the package was broken and wound up going back to the version from synaptic.)..

---

### Post by ArCorvus on 2010-08-18
Hi, Jonas!


 You must compile your project with the debuging data. Add compiler switch -g for g++ compiler.
Don’t forget fully recompile your project.
 Good luck!

---

