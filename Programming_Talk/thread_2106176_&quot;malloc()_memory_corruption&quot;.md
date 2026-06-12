---
title: "&quot;malloc(): memory corruption:&quot;"
date: 2013-01-18
forum: Programming Talk
---

### Post by PoMaIIIka on 2013-01-18
In spite of an expirience of programming to fortran 90, I face with this error for the very first time...
In a big program I ask to allocate memory for an array in the following way:

...

integer,dimension( : ),pointer :: test_array

...

allocate(test_array(1:5))
 
And exactly in this moment my computer writes to me:

*** glibc detected *** ./main_simple: malloc(): memory corruption: 0x0000000000d99b00 ***
 
It seems that I have enough memory and I have no idea (unfortunately) what is this error about...

So, I hope that someone has already faced with this error and knows how to solve it


Thanks a lot!!

---

### Post by MG&amp;TL on 2013-01-18
What language are you using? Post code.

---

### Post by PoMaIIIka on 2013-01-18
I'm using FORTRAN 90.

```

module interface_construction_module

use element_module
use edge_module
use main_types_module
use maillage_module

contains

    subroutine creation_triangles(number_of_partitions, list_of_meshes, list_of_interface_triangles, list_of_edges)
    implicit none

    !!! input data
    integer :: number_of_partitions
    type(maillage),dimension(:),pointer :: list_of_meshes
    integer,dimension(:,:),pointer :: list_of_interface_triangles
    type(edge),dimension(:),pointer :: list_of_edges

    !!! we need that
    integer :: i,j,k
    integer :: l
    integer :: number_of_triangles_here
    integer :: number_of_triangles        ! number of INTERFACE triangles
    integer :: local_edge

    !!! for test
    integer,dimension(:),pointer :: test_array1

    print*,"Before error"
    allocate(test_array1(1:5))
    print*,"This message will never print!"

    !!!! here there is the rest of the code...

    end subroutine creation_triangles
end module interface_construction_module

```

---

### Post by MG&amp;TL on 2013-01-18
Oh! In which case, my apologies, I can't help. I assumed you meant you had experience with fortran but you were trying something else. Sorry. :(

---

### Post by PoMaIIIka on 2013-01-18
MG&TL, thanks a lot, anyway!:)

---

### Post by ofnuts on 2013-01-18
The code that executes before you allocate that array probably tramples some memory structure used by the memory management. Look for out-of-bounds array indexes in your code (especially negative ones), or for incorrect de-allocations.

---

### Post by MadCow108 on 2013-01-18
run the binary (compiled with debug info) through valgrind, that should give you some clues where you are messing up the memory

---

### Post by PoMaIIIka on 2013-01-18
ofnuts, MadCow108, Thank you very mutch!!!

I will definatelly try what you recommended me and I will tell you if it works!

---

### Post by PoMaIIIka on 2013-01-21
..

---

### Post by PoMaIIIka on 2013-01-21
In fact, my first problem is when I write something like that:
```

..
integer,dimension(:),pointer :: test_array3
..
allocate(test_array3(1:10))

test_array3(15) = 0
print*,"check1 = ",test_array3(15)

```and, after that
```

ifort -w -w95 -O3 **-fbounds-check** ../main_simple.f90

```He doesn't find this error...

And, when I'm running 
```

valgrind ./main_simple

```He finds big amount of errors like that
```

==8143== Conditional jump or move depends on uninitialised value(s)
==8143==    at 0x4C267D8: _intel_fast_memcpy (in /usr/lib64/valgrind/amd64-linux/vgpreload_memcheck.so)
==8143==    by 0x67F4AD: for__reopen_file (in /home/voznyuk/Im_dancing_inside_3D/CODE_IVAN/Version_seb/MAIN_DIRECT/main_simple)
==8143==    by 0x6480C5: for_open (in /home/voznyuk/Im_dancing_inside_3D/CODE_IVAN/Version_seb/MAIN_DIRECT/main_simple)
==8143==    by 0x405AE7: read_media_module_mp_read_media_ (in /home/voznyuk/Im_dancing_inside_3D/CODE_IVAN/Version_seb/MAIN_DIRECT/main_simple)
==8143==    by 0x4433A8: MAIN__ (in /home/voznyuk/Im_dancing_inside_3D/CODE_IVAN/Version_seb/MAIN_DIRECT/main_simple)
==8143==    by 0x404EBB: main (in /home/voznyuk/Im_dancing_inside_3D/CODE_IVAN/Version_seb/MAIN_DIRECT/main_simple)

```or, like this
```

==8143== Use of uninitialised value of size 8
==8143==    at 0x67F423: for__reopen_file (in /home/voznyuk/Im_dancing_inside_3D/CODE_IVAN/Version_seb/MAIN_DIRECT/main_simple)
==8143==    by 0x6480C5: for_open (in /home/voznyuk/Im_dancing_inside_3D/CODE_IVAN/Version_seb/MAIN_DIRECT/main_simple)
==8143==    by 0x405AE7: read_media_module_mp_read_media_ (in /home/voznyuk/Im_dancing_inside_3D/CODE_IVAN/Version_seb/MAIN_DIRECT/main_simple)
==8143==    by 0x4433A8: MAIN__ (in /home/voznyuk/Im_dancing_inside_3D/CODE_IVAN/Version_seb/MAIN_DIRECT/main_simple)
==8143==    by 0x404EBB: main (in /home/voznyuk/Im_dancing_inside_3D/CODE_IVAN/Version_seb/MAIN_DIRECT/main_simple)

``` He **allocates** memory for the test_array1 (from the test in my first message), so as the output we have:

```

Before error
This message will never print!

--8143-- VALGRIND INTERNAL ERROR: Valgrind received a signal 11 (SIGSEGV) - exiting
--8143-- si_code=1;  Faulting address: 0x602095282F2;  sp: 0x4028F2E50

valgrind: the 'impossible' happened:
   Killed by fatal signal
==8143==    at 0x380242BD: (within /usr/lib64/valgrind/amd64-linux/memcheck)
==8143==    by 0x38002A75: (within /usr/lib64/valgrind/amd64-linux/memcheck)
==8143==    by 0x38002D2E: (within /usr/lib64/valgrind/amd64-linux/memcheck)
==8143==    by 0x380383EF: (within /usr/lib64/valgrind/amd64-linux/memcheck)
==8143==    by 0x38049A70: (within /usr/lib64/valgrind/amd64-linux/memcheck)

sched status:
  running_tid=1

Thread 1: status = VgTs_Runnable
==8143==    at 0x4C232D0: memalign (in /usr/lib64/valgrind/amd64-linux/vgpreload_memcheck.so)
==8143==    by 0x4C2338A: posix_memalign (in /usr/lib64/valgrind/amd64-linux/vgpreload_memcheck.so)
==8143==    by 0x657567: for_allocate (in /home/voznyuk/Im_dancing_inside_3D/CODE_IVAN/Version_seb/MAIN_DIRECT/main_simple)
==8143==    by 0x43AC87: all_about_sb_module_mp_creation_matrix_dr_qr_into_sb_ (in /home/voznyuk/Im_dancing_inside_3D/CODE_IVAN/Version_seb/MAIN_DIRECT/main_simple)
==8143==    by 0x444966: MAIN__ (in /home/voznyuk/Im_dancing_inside_3D/CODE_IVAN/Version_seb/MAIN_DIRECT/main_simple)
==8143==    by 0x404EBB: main (in /home/voznyuk/Im_dancing_inside_3D/CODE_IVAN/Version_seb/MAIN_DIRECT/main_simple)


Note: see also the FAQ.txt in the source distribution.
It contains workarounds to several common problems.

If that doesn't help, please report this bug to: www.valgrind.org

In the bug report, send all the above text, the valgrind
version, and what Linux distro you are using.  Thanks.

```Something really strange is going on here...

So, maybe you guys know what can I do with this...

---

