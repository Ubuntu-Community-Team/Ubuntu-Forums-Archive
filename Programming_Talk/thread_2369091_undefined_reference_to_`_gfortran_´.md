---
title: "undefined reference to `_gfortran_´"
date: 2017-08-18
forum: Programming Talk
---

### Post by user1503 on 2017-08-18
Hi all, 

I have problems to compile a c++ program that was running without problems on a different laptop. 

$ g++ -std=c++11 -Wall -DVERSION=\"d1ffe1\"   -O2 -g  -Iinclude -Ilibabm/include  src/main.cpp -DAlpha -o build/main_DAlpha -L/usr/lib/gcc/x86_64-linux-gnu/5.4.0 -lhdf5 -lpthread -lprotobuf -labc -lboost_system -lboost_filesystem -lboost_program_options -lgfortran

I get the following error: 

/home/libraries/libabc/libl_bfgs_b3.so: undefined reference to `_gfortran_transfer_integer_write'
/libraries/libabc/libl_bfgs_b3.so: undefined reference to `_gfortran_st_open'
/home/libraries/libabc/libl_bfgs_b3.so: undefined reference to `_gfortran_transfer_character_write'
/home/libraries/libabc/libl_bfgs_b3.so: undefined reference to `_gfortran_compare_string'
/home/libraries/libabc/libl_bfgs_b3.so: undefined reference to `_gfortran_cpu_time_4'
/home/libraries/libabc/libl_bfgs_b3.so: undefined reference to `_gfortran_st_write_done'
/home/libraries/libabc/libl_bfgs_b3.so: undefined reference to `_gfortran_transfer_real_write'
/home/libraries/libabc/libl_bfgs_b3.so: undefined reference to `_gfortran_st_write'
collect2: error: ld returned 1 exit status

I only have the compiled version of libabc. The file libgfortran.so is in the folder /usr/lib/gcc/x86_64-linux-gnu/5.4.0. I also tried to specify the path with LIBRARY_PATH and LD_LIBRARY_PATH, but I got the same error. Do you have any idea why this error occurs and how I can solve it?

---

