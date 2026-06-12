---
title: "Difficulty in compiling C++ codes using Makefile"
date: 2013-09-15
forum: New to Ubuntu
---

### Post by SUMAN003 on 2013-09-15
Hi,

I am facing the following problem while trying to run a C++ code in Makefile. Please suggest a solution to rectify this:[B]

$ make[/B]

ccache g++ -ggdb -fPIC  -I/opt/Xilinx/Vivado_HLS/2013.2/Linux_x86_64/tools/systemc/include -I.  -I/opt/Xilinx/Vivado_HLS/2013.2/include -mcmodel=medium  -lm -llog4cxx  -c quadratic_equation_test.cc
In file included from quadratic_equation_test.cc:7:0:
types.h:4:22: fatal error: ap_fixed.h: No such file or directory
compilation terminated.

---

### Post by codemaniac on 2013-09-15
Please do not start multiple threads for the same issue. This thread is closed now, please continue the discussion on the other thread  started by you.

[http://ubuntuforums.org/showthread.php?t=2174632](http://ubuntuforums.org/showthread.php?t=2174632)

---

