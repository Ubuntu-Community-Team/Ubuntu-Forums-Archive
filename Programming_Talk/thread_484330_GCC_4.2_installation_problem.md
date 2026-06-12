---
title: "GCC 4.2 installation problem"
date: 2007-06-25
forum: Programming Talk
---

### Post by gizmoarena on 2007-06-25
can anybody tell me how to install gcc 4.2.0?

when i try to "make" the insaller, it says ...
> 
...
...
/home/gizmo/gcc-4.2.0/host-i686-pc-linux-gnu/gcc/../.././gcc/config/i386/i386.c:18987: undefined reference to `tree_contains_struct_check_failed'
libbackend.a(i386.o): In function `ix86_mangle_fundamental_type':
/home/gizmo/gcc-4.2.0/host-i686-pc-linux-gnu/gcc/../.././gcc/config/i386/i386.c:19107: undefined reference to `tree_class_check_failed'
libbackend.a(graph.o): In function `VEC_basic_block_base_index':
/home/gizmo/gcc-4.2.0/host-i686-pc-linux-gnu/gcc/../.././gcc/basic-block.h:285: undefined reference to `vec_assert_fail'
libbackend.a(graph.o): In function `VEC_edge_base_index':
/home/gizmo/gcc-4.2.0/host-i686-pc-linux-gnu/gcc/../.././gcc/basic-block.h:147: undefined reference to `vec_assert_fail'
collect2: ld returned 1 exit status
make[3]: *** [cc1-dummy] Error 1
make[3]: Leaving directory `/home/gizmo/gcc-4.2.0/host-i686-pc-linux-gnu/gcc'
make[2]: *** [all-stage1-gcc] Error 2
make[2]: Leaving directory `/home/gizmo/gcc-4.2.0'
make[1]: *** [stage1-bubble] Error 2
make[1]: Leaving directory `/home/gizmo/gcc-4.2.0'
make: *** [all] Error 2


what possibly could be wrong?

---

### Post by geraldm on 2007-06-27
#!/bin/bash
# Put this script in a directory called gcc-build/
# The gcc source, relative to this directory is in ../gcc-4.2.0
# These are the options I used this time to configure gcc.
# Then execute this script (changing the options to your
# needs)
../gcc-4.2.0/configure --prefix=/home/pkgs/gcc/4.2.0 \
  --enable-shared --enable-threads=posix \
  --enable-clocale=gnu \
  --disable-nls \
  --enable-languages=c 

# After running this, then do make in this directory.
# If your build fails and you want to start over, you can just
# remove this entire directory.
# In more recent gcc builds, there are a few kinks to be 
# expected.  There are tokens being pasted into header files
# that may not paste properly.  You may have to change "-" to "_"
# on occasion.  I had 2 based on my present headers.  And there
# was a directory that was not found.  I had to create a link
# in the i686 setup, and you may have to also. 
#   I have no idea what happened in your last compile.  I suggest
# you NOT build within the gcc source directory.  It may take
# a few builds to succeed. 

regards,
Gerald

---

### Post by praxis22 on 2007-06-28
[http://ubuntuforums.org/showthread.php?p=2931398#post2931398](http://ubuntuforums.org/showthread.php?p=2931398#post2931398)

So far so good :)

---

