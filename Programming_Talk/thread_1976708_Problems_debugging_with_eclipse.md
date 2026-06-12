---
title: "Problems debugging with eclipse"
date: 2012-05-09
forum: Programming Talk
---

### Post by debutant10 on 2012-05-09
Hello,
 I am trying to use eclipse with ubuntu 12.04 to debug a c++ program.
 Things that were working fine with ubuntu 10.04 now give me problems.

 From eclipse I built a c++ "Makefile project".
 I set it up as I did before.
 It runs fine.
 But when I want to debug, I get:
```

My_Exe [C/C++ Application]    
  gdb/mi (09/05/12 10:06) (Suspended)    
    Thread [1] (Suspended)    
      4 <symbol is not available> 0xb7fe0cb2    
      3 <symbol is not available> 0xb7ff2977    
      2 <symbol is not available> 0xb7fe2eeb    
      1 <symbol is not available> 0xb7fdf1d7    
    gdb (09/05/12 10:06)    
    /My_Path/My_Exec (09/05/12 10:06)    
    
```If I click in "step over" anyway, here is the message I get in 
the Console window:
```

.gdbinit: No file or folder of this kind    ("Aucun fichier ou dossier de ce type" in French).
Reading symbols from /My_Path/My_Exec...done.
Single stepping until exit from function _dl_debug_state,
which has no line number information.

``` I don't know where to start here to fix this problem.
 Is the problem due to the gdb compiler ? to eclipse ?
 Thanks for any help.

---

### Post by dwhitney67 on 2012-05-09
Specify the -g option as one of your compiler options, and then you should be ok.

The -g option tells GCC to include symbolic information in the executable so that it can be debugged.

---

### Post by debutant10 on 2012-05-09
I am compiling with the -g option:

gcc-4.6 -x c++ -std=c++0x -g ...

thanks!

---

