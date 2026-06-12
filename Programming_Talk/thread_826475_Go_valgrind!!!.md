---
title: "Go valgrind!!!"
date: 2008-06-11
forum: Programming Talk
---

### Post by raul_ on 2008-06-11
Ok so I was debugging this program, and valgrind kept giving me errors. I went to the point of commenting ALL of my code, and I was still getting errors.

So I went desperate and did this "program":

```

int main(){
	return 0;
}

```

Seriously. No includes, no nothing.

```

[kde4@horus ~]$ g++ proj.cpp

```

yey, so far so good!

```

[kde4@horus ~]$ valgrind ./a.out 
==20073== Memcheck, a memory error detector.                                       
==20073== Copyright (C) 2002-2007, and GNU GPL'd, by Julian Seward et al.          
==20073== Using LibVEX rev 1804, a library for dynamic binary translation.         
==20073== Copyright (C) 2004-2007, and GNU GPL'd, by OpenWorks LLP.                
==20073== Using valgrind-3.3.0, a dynamic binary instrumentation framework.        
==20073== Copyright (C) 2000-2007, and GNU GPL'd, by Julian Seward et al.          
==20073== For more details, rerun with: -v                                         
==20073==                                                                          
==20073== Conditional jump or move depends on uninitialised value(s)               
==20073==    at 0x400AC2B: _dl_relocate_object (in /lib/ld-2.8.so)                 
==20073==    by 0x4003788: dl_main (in /lib/ld-2.8.so)                             
==20073==    by 0x4014460: _dl_sysdep_start (in /lib/ld-2.8.so)                    
==20073==    by 0x4001187: _dl_start (in /lib/ld-2.8.so)                           
==20073==    by 0x40007F6: (within /lib/ld-2.8.so)                                 
==20073==                                                                          
==20073== Conditional jump or move depends on uninitialised value(s)               
==20073==    at 0x400AC33: _dl_relocate_object (in /lib/ld-2.8.so)                 
==20073==    by 0x4003788: dl_main (in /lib/ld-2.8.so)                             
==20073==    by 0x4014460: _dl_sysdep_start (in /lib/ld-2.8.so)                    
==20073==    by 0x4001187: _dl_start (in /lib/ld-2.8.so)                           
==20073==    by 0x40007F6: (within /lib/ld-2.8.so)                                 
==20073==                                                                          
==20073== Conditional jump or move depends on uninitialised value(s)               
==20073==    at 0x400BB61: _dl_relocate_object (in /lib/ld-2.8.so)                 
==20073==    by 0x4003788: dl_main (in /lib/ld-2.8.so)                             
==20073==    by 0x4014460: _dl_sysdep_start (in /lib/ld-2.8.so)                    
==20073==    by 0x4001187: _dl_start (in /lib/ld-2.8.so)                           
==20073==    by 0x40007F6: (within /lib/ld-2.8.so)                                 
==20073==                                                                          
==20073== Conditional jump or move depends on uninitialised value(s)               
==20073==    at 0x400ADE0: _dl_relocate_object (in /lib/ld-2.8.so)                 
==20073==    by 0x4003788: dl_main (in /lib/ld-2.8.so)                             
==20073==    by 0x4014460: _dl_sysdep_start (in /lib/ld-2.8.so)                    
==20073==    by 0x4001187: _dl_start (in /lib/ld-2.8.so)                           
==20073==    by 0x40007F6: (within /lib/ld-2.8.so)                                 
==20073==                                                                          
==20073== Conditional jump or move depends on uninitialised value(s)               
==20073==    at 0x400BC74: _dl_relocate_object (in /lib/ld-2.8.so)                 
==20073==    by 0x4003788: dl_main (in /lib/ld-2.8.so)                             
==20073==    by 0x4014460: _dl_sysdep_start (in /lib/ld-2.8.so)                    
==20073==    by 0x4001187: _dl_start (in /lib/ld-2.8.so)                           
==20073==    by 0x40007F6: (within /lib/ld-2.8.so)                                 
==20073==                                                                          
==20073== Conditional jump or move depends on uninitialised value(s)               
==20073==    at 0x400AC2B: _dl_relocate_object (in /lib/ld-2.8.so)                 
==20073==    by 0x40038B3: dl_main (in /lib/ld-2.8.so)                             
==20073==    by 0x4014460: _dl_sysdep_start (in /lib/ld-2.8.so)                    
==20073==    by 0x4001187: _dl_start (in /lib/ld-2.8.so)                           
==20073==    by 0x40007F6: (within /lib/ld-2.8.so)                                 
==20073==
==20073== Conditional jump or move depends on uninitialised value(s)
==20073==    at 0x400AC33: _dl_relocate_object (in /lib/ld-2.8.so)
==20073==    by 0x40038B3: dl_main (in /lib/ld-2.8.so)
==20073==    by 0x4014460: _dl_sysdep_start (in /lib/ld-2.8.so)
==20073==    by 0x4001187: _dl_start (in /lib/ld-2.8.so)
==20073==    by 0x40007F6: (within /lib/ld-2.8.so)
==20073==
==20073== Conditional jump or move depends on uninitialised value(s)
==20073==    at 0x400ADE0: _dl_relocate_object (in /lib/ld-2.8.so)
==20073==    by 0x40038B3: dl_main (in /lib/ld-2.8.so)
==20073==    by 0x4014460: _dl_sysdep_start (in /lib/ld-2.8.so)
==20073==    by 0x4001187: _dl_start (in /lib/ld-2.8.so)
==20073==    by 0x40007F6: (within /lib/ld-2.8.so)
==20073==
==20073== ERROR SUMMARY: 19 errors from 8 contexts (suppressed: 0 from 0)
==20073== malloc/free: in use at exit: 0 bytes in 0 blocks.
==20073== malloc/free: 0 allocs, 0 frees, 0 bytes allocated.
==20073== For counts of detected errors, rerun with: -v
==20073== All heap blocks were freed -- no leaks are possible.
[kde4@horus ~]$

```

I mean WTF!!!!!!!!!!!!!

I swear I'm not running another program. It gives me the exact amount of errors everytime, the same number as the other program.

:guitar: Sometimes I just wanna throw computers in the garbage

---

### Post by JudgeFudge on 2008-06-11
Weird. I owe valgrind, it has saved me more than once, so I tried it out:

(copying and pasting your program)

james@panda:~/src/c$ gedit val.c &
[1] 28020
james@panda:~/src/c$ g++ val.c
[1]+  Done                    gedit val.c
```

james@panda:~/src/c$ valgrind ./a.out 
==28055== Memcheck, a memory error detector.
==28055== Copyright (C) 2002-2007, and GNU GPL'd, by Julian Seward et al.
==28055== Using LibVEX rev 1804, a library for dynamic binary translation.
==28055== Copyright (C) 2004-2007, and GNU GPL'd, by OpenWorks LLP.
==28055== Using valgrind-3.3.0-Debian, a dynamic binary instrumentation framework.
==28055== Copyright (C) 2000-2007, and GNU GPL'd, by Julian Seward et al.
==28055== For more details, rerun with: -v
==28055== 
==28055== 
==28055== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 17 from 1)
==28055== malloc/free: in use at exit: 0 bytes in 0 blocks.
==28055== malloc/free: 0 allocs, 0 frees, 0 bytes allocated.
==28055== For counts of detected errors, rerun with: -v
==28055== All heap blocks were freed -- no leaks are possible.
james@panda:~/src/c$ 

james@panda:~/src/c$ valgrind --version
valgrind-3.3.0-Debian

```

Works for me so, as I say, weird.

---

### Post by raul_ on 2008-06-11
Yeah, I already tested it in another machine through ssh and it works fine. I already rebooted and it keeps giving me errors. I always used valgrind, I don't know why it went berserk :(

---

### Post by raul_ on 2008-06-11
Check this out (cool part in bold)

```

[kde4@horus ~]$ **g++** proj.c
[kde4@horus ~]$ valgrind ./a.out 
==3656== Memcheck, a memory error detector.
==3656== Copyright (C) 2002-2007, and GNU GPL'd, by Julian Seward et al.
==3656== Using LibVEX rev 1804, a library for dynamic binary translation.
==3656== Copyright (C) 2004-2007, and GNU GPL'd, by OpenWorks LLP.       
==3656== Using valgrind-3.3.0, a dynamic binary instrumentation framework.
==3656== Copyright (C) 2000-2007, and GNU GPL'd, by Julian Seward et al.  
==3656== For more details, rerun with: -v                                 
==3656==                                                                  
==3656== Conditional jump or move depends on uninitialised value(s)       
==3656==    at 0x400AC2B: _dl_relocate_object (in /lib/ld-2.8.so)         
==3656==    by 0x4003788: dl_main (in /lib/ld-2.8.so)                     
==3656==    by 0x4014460: _dl_sysdep_start (in /lib/ld-2.8.so)            
==3656==    by 0x4001187: _dl_start (in /lib/ld-2.8.so)                   
==3656==    by 0x40007F6: (within /lib/ld-2.8.so)                         
==3656==                                                                  
==3656== Conditional jump or move depends on uninitialised value(s)       
==3656==    at 0x400AC33: _dl_relocate_object (in /lib/ld-2.8.so)         
==3656==    by 0x4003788: dl_main (in /lib/ld-2.8.so)                     
==3656==    by 0x4014460: _dl_sysdep_start (in /lib/ld-2.8.so)            
==3656==    by 0x4001187: _dl_start (in /lib/ld-2.8.so)                   
==3656==    by 0x40007F6: (within /lib/ld-2.8.so)                         
==3656==                                                                  
==3656== Conditional jump or move depends on uninitialised value(s)       
==3656==    at 0x400BB61: _dl_relocate_object (in /lib/ld-2.8.so)         
==3656==    by 0x4003788: dl_main (in /lib/ld-2.8.so)                     
==3656==    by 0x4014460: _dl_sysdep_start (in /lib/ld-2.8.so)            
==3656==    by 0x4001187: _dl_start (in /lib/ld-2.8.so)                   
==3656==    by 0x40007F6: (within /lib/ld-2.8.so)                         
==3656==                                                                  
==3656== Conditional jump or move depends on uninitialised value(s)       
==3656==    at 0x400ADE0: _dl_relocate_object (in /lib/ld-2.8.so)         
==3656==    by 0x4003788: dl_main (in /lib/ld-2.8.so)                     
==3656==    by 0x4014460: _dl_sysdep_start (in /lib/ld-2.8.so)            
==3656==    by 0x4001187: _dl_start (in /lib/ld-2.8.so)                   
==3656==    by 0x40007F6: (within /lib/ld-2.8.so)                         
==3656==                                                                  
==3656== Conditional jump or move depends on uninitialised value(s)       
==3656==    at 0x400BC74: _dl_relocate_object (in /lib/ld-2.8.so)         
==3656==    by 0x4003788: dl_main (in /lib/ld-2.8.so)                     
==3656==    by 0x4014460: _dl_sysdep_start (in /lib/ld-2.8.so)            
==3656==    by 0x4001187: _dl_start (in /lib/ld-2.8.so)                   
==3656==    by 0x40007F6: (within /lib/ld-2.8.so)                         
==3656==                                                                  
==3656== Conditional jump or move depends on uninitialised value(s)       
==3656==    at 0x400AC2B: _dl_relocate_object (in /lib/ld-2.8.so)         
==3656==    by 0x40038B3: dl_main (in /lib/ld-2.8.so)                     
==3656==    by 0x4014460: _dl_sysdep_start (in /lib/ld-2.8.so)            
==3656==    by 0x4001187: _dl_start (in /lib/ld-2.8.so)
==3656==    by 0x40007F6: (within /lib/ld-2.8.so)
==3656==
==3656== Conditional jump or move depends on uninitialised value(s)
==3656==    at 0x400AC33: _dl_relocate_object (in /lib/ld-2.8.so)
==3656==    by 0x40038B3: dl_main (in /lib/ld-2.8.so)
==3656==    by 0x4014460: _dl_sysdep_start (in /lib/ld-2.8.so)
==3656==    by 0x4001187: _dl_start (in /lib/ld-2.8.so)
==3656==    by 0x40007F6: (within /lib/ld-2.8.so)
==3656==
==3656== Conditional jump or move depends on uninitialised value(s)
==3656==    at 0x400ADE0: _dl_relocate_object (in /lib/ld-2.8.so)
==3656==    by 0x40038B3: dl_main (in /lib/ld-2.8.so)
==3656==    by 0x4014460: _dl_sysdep_start (in /lib/ld-2.8.so)
==3656==    by 0x4001187: _dl_start (in /lib/ld-2.8.so)
==3656==    by 0x40007F6: (within /lib/ld-2.8.so)
==3656==
==3656==** ERROR SUMMARY: 19 errors from 8 contexts** (suppressed: 0 from 0)
==3656== malloc/free: in use at exit: 0 bytes in 0 blocks.
==3656== malloc/free: 0 allocs, 0 frees, 0 bytes allocated.
==3656== For counts of detected errors, rerun with: -v
==3656== All heap blocks were freed -- no leaks are possible.
[kde4@horus ~]$


[kde4@horus ~]$ **gcc** proj.c
[kde4@horus ~]$ valgrind ./a.out 
==3644== Memcheck, a memory error detector.
==3644== Copyright (C) 2002-2007, and GNU GPL'd, by Julian Seward et al.
==3644== Using LibVEX rev 1804, a library for dynamic binary translation.
==3644== Copyright (C) 2004-2007, and GNU GPL'd, by OpenWorks LLP.       
==3644== Using valgrind-3.3.0, a dynamic binary instrumentation framework.
==3644== Copyright (C) 2000-2007, and GNU GPL'd, by Julian Seward et al.  
==3644== For more details, rerun with: -v                                 
==3644==                                                                  
==3644== Conditional jump or move depends on uninitialised value(s)       
==3644==    at 0x400AC2B: _dl_relocate_object (in /lib/ld-2.8.so)         
==3644==    by 0x4003788: dl_main (in /lib/ld-2.8.so)                     
==3644==    by 0x4014460: _dl_sysdep_start (in /lib/ld-2.8.so)            
==3644==    by 0x4001187: _dl_start (in /lib/ld-2.8.so)                   
==3644==    by 0x40007F6: (within /lib/ld-2.8.so)                         
==3644==                                                                  
==3644== Conditional jump or move depends on uninitialised value(s)       
==3644==    at 0x400AC33: _dl_relocate_object (in /lib/ld-2.8.so)         
==3644==    by 0x4003788: dl_main (in /lib/ld-2.8.so)                     
==3644==    by 0x4014460: _dl_sysdep_start (in /lib/ld-2.8.so)            
==3644==    by 0x4001187: _dl_start (in /lib/ld-2.8.so)                   
==3644==    by 0x40007F6: (within /lib/ld-2.8.so)                         
==3644==                                                                  
==3644== Conditional jump or move depends on uninitialised value(s)       
==3644==    at 0x400BB61: _dl_relocate_object (in /lib/ld-2.8.so)         
==3644==    by 0x4003788: dl_main (in /lib/ld-2.8.so)                     
==3644==    by 0x4014460: _dl_sysdep_start (in /lib/ld-2.8.so)            
==3644==    by 0x4001187: _dl_start (in /lib/ld-2.8.so)                   
==3644==    by 0x40007F6: (within /lib/ld-2.8.so)                         
==3644==                                                                  
==3644== Conditional jump or move depends on uninitialised value(s)       
==3644==    at 0x400ADE0: _dl_relocate_object (in /lib/ld-2.8.so)         
==3644==    by 0x4003788: dl_main (in /lib/ld-2.8.so)                     
==3644==    by 0x4014460: _dl_sysdep_start (in /lib/ld-2.8.so)            
==3644==    by 0x4001187: _dl_start (in /lib/ld-2.8.so)                   
==3644==    by 0x40007F6: (within /lib/ld-2.8.so)                         
==3644==                                                                  
==3644== Conditional jump or move depends on uninitialised value(s)       
==3644==    at 0x400BC74: _dl_relocate_object (in /lib/ld-2.8.so)         
==3644==    by 0x4003788: dl_main (in /lib/ld-2.8.so)                     
==3644==    by 0x4014460: _dl_sysdep_start (in /lib/ld-2.8.so)            
==3644==    by 0x4001187: _dl_start (in /lib/ld-2.8.so)                   
==3644==    by 0x40007F6: (within /lib/ld-2.8.so)                         
==3644==                                                                  
==3644== Conditional jump or move depends on uninitialised value(s)       
==3644==    at 0x400AC2B: _dl_relocate_object (in /lib/ld-2.8.so)         
==3644==    by 0x40038B3: dl_main (in /lib/ld-2.8.so)                     
==3644==    by 0x4014460: _dl_sysdep_start (in /lib/ld-2.8.so)            
==3644==    by 0x4001187: _dl_start (in /lib/ld-2.8.so)                   
==3644==    by 0x40007F6: (within /lib/ld-2.8.so)                         
==3644==                                                                  
==3644== Conditional jump or move depends on uninitialised value(s)       
==3644==    at 0x400AC33: _dl_relocate_object (in /lib/ld-2.8.so)         
==3644==    by 0x40038B3: dl_main (in /lib/ld-2.8.so)                     
==3644==    by 0x4014460: _dl_sysdep_start (in /lib/ld-2.8.so)            
==3644==    by 0x4001187: _dl_start (in /lib/ld-2.8.so)                   
==3644==    by 0x40007F6: (within /lib/ld-2.8.so)                         
==3644==                                                                  
==3644== Conditional jump or move depends on uninitialised value(s)       
==3644==    at 0x400ADE0: _dl_relocate_object (in /lib/ld-2.8.so)         
==3644==    by 0x40038B3: dl_main (in /lib/ld-2.8.so)                     
==3644==    by 0x4014460: _dl_sysdep_start (in /lib/ld-2.8.so)            
==3644==    by 0x4001187: _dl_start (in /lib/ld-2.8.so)                   
==3644==    by 0x40007F6: (within /lib/ld-2.8.so)                         
==3644==                                                                  
==3644== **ERROR SUMMARY: 13 errors from 8 contexts (suppressed: 0 from 0)  **
==3644== malloc/free: in use at exit: 0 bytes in 0 blocks.                
==3644== malloc/free: 0 allocs, 0 frees, 0 bytes allocated.               
==3644== For counts of detected errors, rerun with: -v                    
==3644== All heap blocks were freed -- no leaks are possible.  

```

---

### Post by geirha on 2008-06-12
That's really weird. If you build that simple program on your machine and another machine using the same version of the compiler, do the binaries become identical? ```
md5sum a.out
```

If they are the same, could you also pop in your ubuntu CD in the machine where this weirdness is happening, boot it up, install build-essential and valgrind in the live-session, and compile the program the same way. Does it exhibit the same problem?

If the latter produces the same result, I would start to think you have some faulty hardware.

---

### Post by moma on 2008-06-12
<deleted>
because he runs Arch Linux.

The answer was not relevant to Arch.

---

### Post by raul_ on 2008-06-12
As stated in my sig I use Arch Linux :)

Anyway, I submited a bug report, and seems that the version of valgrind(3.3.0) wasn't compatible with the latest glibc (2.8 ) but they already released 3.3.1 so things should be fine.

glibc was released since I last programmed in C, so it was working fine at that point

I was starting to pull my hairs out

---

### Post by Jessehk on 2008-06-12
[http://bbs.archlinux.org/viewtopic.php?id=36309](http://bbs.archlinux.org/viewtopic.php?id=36309)

Since you're an Arch user, one would think you would be posting on the Arch linux forum
(or at least searching it). :rolleyes:

---

### Post by raul_ on 2008-06-12
Ah a fellow archer :) Well actually I didn't look for a fix, this was more like an amusing post. I went straight to the valgrind bug reports, and went to sleep.

We'll just wait for the next valgrind binary. Been using Arch for all this time now, I suspect that in the next few days there will be an update (after all they do use valgrind...don't they??)

EDIT: I noticed you were still using glibc6 back then. I guess this will be a recurrent problem when glibc releases an update. I guess I'll add it to my HOLDPKG list, until valgrind gets updated too

---

