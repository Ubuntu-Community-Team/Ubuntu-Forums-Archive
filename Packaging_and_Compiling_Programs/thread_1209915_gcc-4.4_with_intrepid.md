---
title: "gcc-4.4 with intrepid?"
date: 2009-07-10
forum: Packaging and Compiling Programs
---

### Post by quackeroni_pizza on 2009-07-10
I couldn't even find PPAs with gcc-4.4 for intrepid... Are there any plans to provide that version of gcc with intrepid?.. or has someone already created an Interpid .deb for it?

---

### Post by wojox on 2009-07-10
Here you go: [http://neo-technical.wikispaces.com/gcc-4.4](http://neo-technical.wikispaces.com/gcc-4.4)

---

### Post by quackeroni_pizza on 2009-07-16
Hmm, thanks.. I had to switch from gcc-4.1 to gcc-4.3 to get it to recognize some command-line switches... But I still get this error-

> gcc -c  -g -fkeep-inline-functions -DIN_GCC   -W -Wall -Wwrite-strings -Wstrict-prototypes -Wmissing-prototypes -Wcast-qual -Wold-style-definition -Wc++-compat -Wmissing-format-attribute -pedantic -Wno-long-long -Wno-variadic-macros -Wno-overlength-strings -fno-common  -DHAVE_CONFIG_H -I. -I. -I../.././gcc -I../.././gcc/. -I../.././gcc/../include -I../.././gcc/../libcpp/include  -I../.././gcc/../libdecnumber -I../.././gcc/../libdecnumber/bid -I../libdecnumber -I/include  -I/include -DCLOOG_PPL_BACKEND   ../.././gcc/c-lang.c -o c-lang.o
In file included from ../.././gcc/input.h:25,
                 from ../.././gcc/tree.h:27,
                 from ../.././gcc/c-lang.c:27:
../.././gcc/../libcpp/include/line-map.h:66: error: ‘CHAR_BIT’ undeclared here (not in a function)
../.././gcc/../libcpp/include/line-map.h:66: error: bit-field ‘reason’ width not an integer constant
../.././gcc/../libcpp/include/line-map.h:66: warning: ‘reason’ is narrower than values of its type
In file included from ../.././gcc/c-common.h:26,
                 from ../.././gcc/c-tree.h:25,
                 from ../.././gcc/c-lang.c:28:
../.././gcc/../libcpp/include/cpplib.h:198: error: bit-field ‘type’ width not an integer constant
../.././gcc/../libcpp/include/cpplib.h:198: warning: ‘type’ is narrower than values of its type
In file included from ../.././gcc/c-common.h:26,
                 from ../.././gcc/c-tree.h:25,
                 from ../.././gcc/c-lang.c:28:
../.././gcc/../libcpp/include/cpplib.h:241:3: error: #error "Cannot find a least-32-bit signed integer type"
../.././gcc/../libcpp/include/cpplib.h:243: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘cppchar_t’
../.././gcc/../libcpp/include/cpplib.h:244: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘cppchar_signed_t’
../.././gcc/../libcpp/include/cpplib.h:732: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘cpp_interpret_charconst’
../.././gcc/../libcpp/include/cpplib.h:743: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘cpp_host_to_exec_charset’
../.././gcc/../libcpp/include/cpplib.h:870: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘cpp_parse_escape’
In file included from ../.././gcc/c-tree.h:26,
                 from ../.././gcc/c-lang.c:28:
../.././gcc/toplev.h: In function ‘floor_log2’:
../.././gcc/toplev.h:193: warning: control reaches end of non-void function


---

