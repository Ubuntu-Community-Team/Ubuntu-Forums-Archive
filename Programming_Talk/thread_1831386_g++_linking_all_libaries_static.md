---
title: "g++ linking all libaries static"
date: 2011-08-23
forum: Programming Talk
---

### Post by zivilist4 on 2011-08-23
Hi, 

I wrote a Fortran program for my thesis. I use the ifort compiler (for some reasons I do not want to use gfortran).
These compiled files are linked in by the g++ compiler.
The Makefile looks like 

FC      = ifort
FCLIBS  = -I /local/peter/tt/masters/PSI/qd/lib/qd 

CC      = /usr/bin/g++
CFLAGS  = -L/local/peter/tt/masters/PSI/qd/lib/  -L/usr/local/intel_fce_80/lib/ -L/local/peter/tt/masters/PSI/Fortran-0.001-0.45/ -L/local/peter/tt/masters/PSI/ODE/quadrupole/
CLIBS   = -lqd_f_main -lqdmod -lqd  -lifcore  -lifport  -ljac2lm128 -ljac2lx128  -lode128

ggtt2l: ggtt2l.o
        $(CC) -o ggtt2l ggtt2l.o $(CFLAGS) $(CLIBS) 

ggtt2l.o: ggtt2l.f libjac2lm128.a libjac2lx128.a libode128.a
        $(FC) $(FCLIBS) -fpp -c ggtt2l.f


On the machines at the university it works fine. Now ...

My laptop can not execute my ggtt2l file  due to an error while loading shared libaries.
(I do not have the ifort compiler on my Laptop)

I guess, this is because of some dynamic linked libaries.
ldd ggtt2l gives me:
        linux-vdso.so.1 =>  (0x00007fff63dff000)
[B]        libifcore.so.5 => /usr/local/intel_fce_80/lib/libifcore.so.5 (0x00007f20bdf89000)
        libifport.so.5 => /usr/local/intel_fce_80/lib/libifport.so.5 (0x00007f20bde0a000)[/B]
        libstdc++.so.6 => /usr/lib64/libstdc++.so.6 (0x00007f20bdab4000)
        libm.so.6 => /lib64/libm.so.6 (0x00007f20bd85e000)
        libgcc_s.so.1 => /lib64/libgcc_s.so.1 (0x00007f20bd646000)
        libc.so.6 => /lib64/libc.so.6 (0x00007f20bd2ed000)
        libimf.so => /usr/local/intel_cce_80/lib/libimf.so (0x00007f20bd09d000)
        libirc.so => /usr/local/intel_cce_80/lib/libirc.so (0x00007f20bcf77000)
        /lib64/ld-linux-x86-64.so.2 (0x00007f20bdf41000)

Do you have any idea how to compile it in such a way that all necessary libaries are linked statically?
If I tried to use the option g++ -static, but I get an huge amount of undefined reference to `_intel_fast_....'
errors.

---

### Post by gnometorule on 2011-08-23
I have not yet written makefiles, but I believe they fall back on gcc (...might be very wrong here). If yes, the gcc option to statically link in is simply '-static'. Maybe try adding this wherever you pull in libs.

---

### Post by zivilist4 on 2011-08-23
Perhaps I should have written it on a earlz state of the text

> **zivilist4 said:**
> 
If I tried to use the option g++ -static, but I get an huge amount of undefined reference to `_intel_fast_....'
errors.

Like
./src/libfor/cvt_cvtas.c.text+0x154f): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c.text+0x15ba): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c.text+0x15ce): undefined reference to `_intel_fast_memset'

I tried to link against the static libaries
**libifcore.a and libifport.a  **but somehow I get the same errors.

---

### Post by Bachstelze on 2011-08-23
Do you have a static version of those libraries? Because if you don't, you obviously can't link them statically.

---

### Post by zivilist4 on 2011-08-23
Thanks for your answers

libifcore.a and libifport.a are available at the same directory like the dynamically linked ones libifcore.so and libifport.so.  

I do not know if libifcore.a and libifport.a  need some library which are only available
dynamically. (But this should not be since they are already static libraries)

Peter

---

### Post by Bachstelze on 2011-08-23
There might be another problem, then. Please paste the entire output of make.

---

### Post by zivilist4 on 2011-08-23
```

 /usr/bin/g++ -static -o ggtt2l ggtt2l.o -L. -L/local/peter/tt/masters/PSI/qd/lib/  -L/usr/local/intel_fce_80/lib/ -L/local/peter/tt/masters/PSI/Fortran-0.001-0.45/ -L/local/peter/tt/masters/PSI/ODE/quadrupole/ -lqd_f_main -lqdmod -lqd  -lifcore  -lifport  -ljac2lm128 -ljac2lx128  -lode128 
./libifcore.a(for_open_proc.o): In function `for__compute_filename':
./src/libfor/for_open_proc.c:(.text+0x3dec): warning: Using 'getpwnam' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
./src/libfor/for_open_proc.c:(.text+0x3f0a): warning: Using 'getpwuid' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
./libifcore.a(for_close_proc.o): In function `for__close_proc':
./src/libfor/for_close_proc.c:(.text+0x3dc): undefined reference to `_intel_fast_memset'
./libifcore.a(for_diags_intel.o): In function `for__io_return':
./src/libfor/for_diags_intel.c:(.text+0x6d0): undefined reference to `_intel_fast_memset'
./libifcore.a(for_diags_intel.o): In function `for_emit_diagnostic':
./src/libfor/for_diags_intel.c:(.text+0x996): undefined reference to `_intel_fast_memset'
./libifcore.a(for_diags_intel.o): In function `for_gerror_':
./src/libfor/for_diags_intel.c:(.text+0xafe): undefined reference to `_intel_fast_memset'
./libifcore.a(for_diags_intel.o): In function `tracebackqq_':
./src/libfor/for_diags_intel.c:(.text+0x117f): undefined reference to `_intel_fast_memset'
./src/libfor/for_diags_intel.c:(.text+0x1193): undefined reference to `_intel_fast_memcpy'
./libifcore.a(for_io_util.o): In function `for__adjust_buffer':
./src/libfor/for_io_util.c:(.text+0x4c4): undefined reference to `_intel_fast_memset'
./libifcore.a(for_io_util.o): In function `for__cvt_foreign_write':
./src/libfor/for_io_util.c:(.text+0x8f5): undefined reference to `_intel_fast_memcpy'
./libifcore.a(for_lub_mgt.o): In function `create_lub':
./src/libfor/for_lub_mgt.c:(.text+0x44): undefined reference to `_intel_fast_memset'
./libifcore.a(for_open.o): In function `for_open':
./src/libfor/for_open.c:(.text+0x76c): undefined reference to `_intel_fast_memset'
./libifcore.a(for_open.o): In function `for__open_default':
./src/libfor/for_open.c:(.text+0xcba): undefined reference to `_intel_fast_memset'
./libifcore.a(for_open_proc.o): In function `for__compute_filename':
./src/libfor/for_open_proc.c:(.text+0x3357): undefined reference to `_intel_fast_memcpy'
./src/libfor/for_open_proc.c:(.text+0x3580): undefined reference to `_intel_fast_memcpy'
./src/libfor/for_open_proc.c:(.text+0x35f9): undefined reference to `_intel_fast_memcpy'
./src/libfor/for_open_proc.c:(.text+0x374d): undefined reference to `_intel_fast_memcpy'
./src/libfor/for_open_proc.c:(.text+0x3785): undefined reference to `_intel_fast_memcpy'
./libifcore.a(for_open_proc.o):./src/libfor/for_open_proc.c:(.text+0x3b81): more undefined references to `_intel_fast_memcpy' follow
./libifcore.a(for_open_proc.o): In function `for__prompt_user':
./src/libfor/for_open_proc.c:(.text+0x4882): undefined reference to `_intel_fast_memset'
./src/libfor/for_open_proc.c:(.text+0x4895): undefined reference to `_intel_fast_memset'
./src/libfor/for_open_proc.c:(.text+0x48a8): undefined reference to `_intel_fast_memset'
./src/libfor/for_open_proc.c:(.text+0x4ed8): undefined reference to `_intel_fast_memcpy'
./src/libfor/for_open_proc.c:(.text+0x4f43): undefined reference to `_intel_fast_memcpy'
./libifcore.a(for_put.o): In function `for__put_su':
./src/libfor/for_put.c:(.text+0x68e): undefined reference to `_intel_fast_memset'
./libifcore.a(for_put.o): In function `for__put_sf':
./src/libfor/for_put.c:(.text+0x1d39): undefined reference to `_intel_fast_memset'
./libifcore.a(for_put.o): In function `for__put_d':
./src/libfor/for_put.c:(.text+0x1efa): undefined reference to `_intel_fast_memset'
./src/libfor/for_put.c:(.text+0x1f03): undefined reference to `_intel_fast_memset'
./libifcore.a(for_rseq_fmt.o): In function `for_read_seq_fmt_xmit':
./src/libfor/for_rseq_fmt.c:(.text+0xdd6): undefined reference to `_intel_fast_memcpy'
./src/libfor/for_rseq_fmt.c:(.text+0xe03): undefined reference to `_intel_fast_memset'
./libifcore.a(for_rseq_lis.o): In function `for_read_seq_lis_xmit':
./src/libfor/for_rseq_lis.c:(.text+0xa6b): undefined reference to `_intel_fast_memset'
./libifcore.a(for_rseq_lis.o): In function `rs_cvt_2step':
./src/libfor/for_rseq_lis.c:(.text+0x2086): undefined reference to `__qtod'
./src/libfor/for_rseq_lis.c:(.text+0x20f1): undefined reference to `__qtod'
./libifcore.a(for_wseq.o): In function `for_write_seq_xmit':
./src/libfor/for_wseq.c:(.text+0x1265): undefined reference to `_intel_fast_memcpy'
./src/libfor/for_wseq.c:(.text+0x1313): undefined reference to `_intel_fast_memcpy'
./src/libfor/for_wseq.c:(.text+0x157b): undefined reference to `_intel_fast_memcpy'
./src/libfor/for_wseq.c:(.text+0x1bb0): undefined reference to `_intel_fast_memcpy'
./libifcore.a(for_wseq.o): In function `for__finish_direct_write':
./src/libfor/for_wseq.c:(.text+0x330e): undefined reference to `_intel_fast_memset'
./libifcore.a(for_wseq.o): In function `for__write_from_user_buffer':
./src/libfor/for_wseq.c:(.text+0x3875): undefined reference to `_intel_fast_memset'
./libifcore.a(for_wseq_fmt.o): In function `for_write_seq_fmt':
./src/libfor/for_wseq_fmt.c:(.text+0x687): undefined reference to `_intel_fast_memset'
./libifcore.a(for_wseq_fmt.o): In function `for_write_seq_fmt_xmit':
./src/libfor/for_wseq_fmt.c:(.text+0x1063): undefined reference to `_intel_fast_memset'
./src/libfor/for_wseq_fmt.c:(.text+0x1da0): undefined reference to `_intel_fast_memset'
./libifcore.a(for_wseq_fmt.o):./src/libfor/for_wseq_fmt.c:(.text+0x2297): more undefined references to `_intel_fast_memset' follow
./libifcore.a(for_wseq_lis.o): In function `for_write_seq_lis_xmit':
./src/libfor/for_wseq_lis.c:(.text+0x1086): undefined reference to `_intel_fast_memcpy'
./src/libfor/for_wseq_lis.c:(.text+0x1383): undefined reference to `_intel_fast_memcpy'
./src/libfor/for_wseq_lis.c:(.text+0x169e): undefined reference to `_intel_fast_memcpy'
./src/libfor/for_wseq_lis.c:(.text+0x19b1): undefined reference to `_intel_fast_memcpy'
./libifcore.a(for_wseq_lis.o): In function `wseq_complex':
./src/libfor/for_wseq_lis.c:(.text+0x37f1): undefined reference to `_intel_fast_memset'
./libifcore.a(for_f90str.o): In function `for_cpystr':
./src/libfor/for_f90str.c:(.text+0x72): undefined reference to `_intel_fast_memset'
./libifcore.a(for_f90str.o): In function `for_cpstr':
./src/libfor/for_f90str.c:(.text+0xe1a): undefined reference to `_intel_fast_memcmp'
./libifcore.a(for_f90str.o): In function `for_concat':
./src/libfor/for_f90str.c:(.text+0x1168): undefined reference to `_intel_fast_memcpy'
./src/libfor/for_f90str.c:(.text+0x1198): undefined reference to `_intel_fast_memcpy'
./libifcore.a(tbk_traceback.o): In function `tbk_stack_trace':
./src/libfor/tbk_traceback.c:(.text+0xae): undefined reference to `tbk_string_stack_signal'
./libifcore.a(for_fmt_val.o): In function `for__format_value':
./src/libfor/for_fmt_val.c:(.text+0xda6): undefined reference to `_intel_fast_memcpy'
./libifcore.a(for_fmt_val.o): In function `for__cvt_value':
./src/libfor/for_fmt_val.c:(.text+0x186d): undefined reference to `_intel_fast_memcpy'
./src/libfor/for_fmt_val.c:(.text+0x1880): undefined reference to `_intel_fast_memcpy'
./libifcore.a(for_get.o): In function `for__get_su':
./src/libfor/for_get.c:(.text+0x35d): undefined reference to `_intel_fast_memcpy'
./src/libfor/for_get.c:(.text+0x433): undefined reference to `_intel_fast_memcpy'
./libifcore.a(for_get.o):./src/libfor/for_get.c:(.text+0x770): more undefined references to `_intel_fast_memcpy' follow
./libifcore.a(cvt_cvtas_s.o): In function `cvt_ieee_s_to_text_ex':
./src/libfor/cvt_cvtas.c:(.text+0x357): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x488): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x547): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x5bf): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x5d8): undefined reference to `_intel_fast_memset'
./libifcore.a(cvt_cvtas_s.o):./src/libfor/cvt_cvtas.c:(.text+0x74d): more undefined references to `_intel_fast_memset' follow
./libifcore.a(cvt_cvtas_s.o): In function `cvt_ieee_s_to_text_ex':
./src/libfor/cvt_cvtas.c:(.text+0xa36): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0xabf): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0xb4f): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xc7f): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xcd6): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xd09): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xd50): undefined reference to `_intel_fast_memset'
./libifcore.a(cvt_cvtas_s.o):./src/libfor/cvt_cvtas.c:(.text+0xd69): more undefined references to `_intel_fast_memset' follow
./libifcore.a(cvt_cvtas_s.o): In function `cvt_ieee_s_to_text_ex':
./src/libfor/cvt_cvtas.c:(.text+0xe62): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0xef9): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0xf6d): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xfb3): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x1069): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x10cc): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x10f8): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x1138): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x11e1): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x11f5): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x125c): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x1270): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x13d9): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x13ed): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x1458): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x146c): undefined reference to `_intel_fast_memset'
./libifcore.a(cvt_cvtas_t.o): In function `cvt_ieee_t_to_text_ex':
./src/libfor/cvt_cvtas.c:(.text+0x371): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x4a2): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x561): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x5d9): undefined reference to `_intel_fast_memset'
./libifcore.a(cvt_cvtas_t.o):./src/libfor/cvt_cvtas.c:(.text+0x5f2): more undefined references to `_intel_fast_memset' follow
./libifcore.a(cvt_cvtas_t.o): In function `cvt_ieee_t_to_text_ex':
./src/libfor/cvt_cvtas.c:(.text+0xa50): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0xad9): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0xb69): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xc9a): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xcf1): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xd24): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xd6b): undefined reference to `_intel_fast_memset'
./libifcore.a(cvt_cvtas_t.o):./src/libfor/cvt_cvtas.c:(.text+0xd84): more undefined references to `_intel_fast_memset' follow
./libifcore.a(cvt_cvtas_t.o): In function `cvt_ieee_t_to_text_ex':
./src/libfor/cvt_cvtas.c:(.text+0xe7d): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0xf14): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0xf88): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xfce): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x10ee): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x1151): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x117d): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x11bd): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x1266): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x127a): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x12e1): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x12f5): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x145e): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x1472): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x14dd): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x14f1): undefined reference to `_intel_fast_memset'
./libifcore.a(cvt_cvtas_x.o): In function `cvt_ieee_x_to_text_ex':
./src/libfor/cvt_cvtas.c:(.text+0x420): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x559): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x62e): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x6a7): undefined reference to `_intel_fast_memset'
./libifcore.a(cvt_cvtas_x.o):./src/libfor/cvt_cvtas.c:(.text+0x6c0): more undefined references to `_intel_fast_memset' follow
./libifcore.a(cvt_cvtas_x.o): In function `cvt_ieee_x_to_text_ex':
./src/libfor/cvt_cvtas.c:(.text+0xb19): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0xb9f): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0xc31): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xcc7): undefined reference to `a_mulq'
./src/libfor/cvt_cvtas.c:(.text+0xd6e): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xdc5): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xdf8): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xe41): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xe5a): undefined reference to `_intel_fast_memset'
./libifcore.a(cvt_cvtas_x.o):./src/libfor/cvt_cvtas.c:(.text+0xee0): more undefined references to `_intel_fast_memset' follow
./libifcore.a(cvt_cvtas_x.o): In function `cvt_ieee_x_to_text_ex':
./src/libfor/cvt_cvtas.c:(.text+0xf58): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0xff1): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x1065): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x10ab): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x1231): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x1294): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x12be): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x12fe): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x13a7): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x13bb): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x1422): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x1436): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x1494): undefined reference to `a_divq'
./src/libfor/cvt_cvtas.c:(.text+0x153b): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x154f): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x15ba): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x15ce): undefined reference to `_intel_fast_memset'
./libifcore.a(cvt_text_to_data.o): In function `cvt_text_to_data':
./src/libfor/cvt_text_to_data.c:(.text+0x4b): undefined reference to `_intel_fast_memset'
collect2: ld returned 1 exit status



```

---

### Post by Bachstelze on 2011-08-23
If you are using Natty (11.04), the linker is much more sensitive to wrong flag ordering. Try modifying your makefile like this:

```
FC = ifort
FCLIBS = -I /local/peter/tt/masters/PSI/qd/lib/qd

LD = /usr/bin/ld
LDFLAGS = -L/local/peter/tt/masters/PSI/qd/lib/ -L/usr/local/intel_fce_80/lib/ -L/local/peter/tt/masters/PSI/Fortran-0.001-0.45/ -L/local/peter/tt/masters/PSI/ODE/quadrupole/
LIBS = -lqd_f_main -lqdmod -lqd -lifcore -lifport -ljac2lm128 -ljac2lx128 -lode128

ggtt2l: ggtt2l.o
$(LD) $(LDFLAGS) -o ggtt2l ggtt2l.o $(LIBS)
```

If that still doesn't work, try putting -lifcore and -lifport at the beginning of LIBS.

ggtt2l.o: ggtt2l.f libjac2lm128.a libjac2lx128.a libode128.a
$(FC) $(FCLIBS) -fpp -c ggtt2l.f
[/code]

---

### Post by MadCow108 on 2011-08-23
> **Bachstelze said:**
> If you are using Natty (11.04), the linker is much more sensitive to wrong flag ordering.

its not just ubuntu, its a general problem when static linking as, compared to dynamic linking, no undefined references are allowed.
objects needing symbols must be placed before the objects providing them.
in case of circular dependencies, try adding the libraries multiple times.
e.g.
```
# liba needs symbols from libb *and* libb needs symbols from liba
gcc obj.o -o output liba.a libb.a liba.a
```

you can also use -Wl,--start-group -Wl,--end-group to let the linker do this, but it can be very slow while it brute forces the symbol resolution.

---

### Post by zivilist4 on 2011-08-24
Hi,

thanks for the correction of the Makefile. Unfourtunately there are still problems.
The command is now

```

/usr/bin/gcc -static -static-libgcc -L/local/peter/tt/masters/PSI/qd/lib/  -L/usr/local/intel_fce_80/lib/ -L/local/peter/tt/masters/PSI/Fortran-0.001-0.45/ -L/local/peter/tt/masters/PSI/ODE/quadrupole/ -o ggtt2l ggtt2l.o -lifcore -lifport -lqd_f_main -lqdmod -lqd  -ljac2lm128 -ljac2lx128 -lode128

```and the error

```

/usr/local/intel_fce_80/lib//libifcore.a(for_open_proc.o): In function `for__compute_filename':
./src/libfor/for_open_proc.c:(.text+0x3dec): warning: Using 'getpwnam' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
./src/libfor/for_open_proc.c:(.text+0x3f0a): warning: Using 'getpwuid' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
/usr/local/intel_fce_80/lib//libifcore.a(for_close_proc.o): In function `for__close_proc':
./src/libfor/for_close_proc.c:(.text+0x3dc): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(for_diags_intel.o): In function `for__io_return':
./src/libfor/for_diags_intel.c:(.text+0x6d0): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(for_diags_intel.o): In function `for_emit_diagnostic':
./src/libfor/for_diags_intel.c:(.text+0x996): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(for_diags_intel.o): In function `for_gerror_':
./src/libfor/for_diags_intel.c:(.text+0xafe): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(for_diags_intel.o): In function `tracebackqq_':
./src/libfor/for_diags_intel.c:(.text+0x117f): undefined reference to `_intel_fast_memset'
./src/libfor/for_diags_intel.c:(.text+0x1193): undefined reference to `_intel_fast_memcpy'
/usr/local/intel_fce_80/lib//libifcore.a(for_io_util.o): In function `for__adjust_buffer':
./src/libfor/for_io_util.c:(.text+0x4c4): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(for_io_util.o): In function `for__cvt_foreign_write':
./src/libfor/for_io_util.c:(.text+0x8f5): undefined reference to `_intel_fast_memcpy'
/usr/local/intel_fce_80/lib//libifcore.a(for_lub_mgt.o): In function `create_lub':
./src/libfor/for_lub_mgt.c:(.text+0x44): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(for_main.o): In function `main':
./src/libfor/for_main.c:(.text+0x24): undefined reference to `MAIN__'
/usr/local/intel_fce_80/lib//libifcore.a(for_open.o): In function `for_open':
./src/libfor/for_open.c:(.text+0x76c): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(for_open.o): In function `for__open_default':
./src/libfor/for_open.c:(.text+0xcba): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(for_open_proc.o): In function `for__compute_filename':
./src/libfor/for_open_proc.c:(.text+0x3357): undefined reference to `_intel_fast_memcpy'
./src/libfor/for_open_proc.c:(.text+0x3580): undefined reference to `_intel_fast_memcpy'
./src/libfor/for_open_proc.c:(.text+0x35f9): undefined reference to `_intel_fast_memcpy'
./src/libfor/for_open_proc.c:(.text+0x374d): undefined reference to `_intel_fast_memcpy'
./src/libfor/for_open_proc.c:(.text+0x3785): undefined reference to `_intel_fast_memcpy'
/usr/local/intel_fce_80/lib//libifcore.a(for_open_proc.o):./src/libfor/for_open_proc.c:(.text+0x3b81): more undefined references to `_intel_fast_memcpy' follow
/usr/local/intel_fce_80/lib//libifcore.a(for_open_proc.o): In function `for__prompt_user':
./src/libfor/for_open_proc.c:(.text+0x4882): undefined reference to `_intel_fast_memset'
./src/libfor/for_open_proc.c:(.text+0x4895): undefined reference to `_intel_fast_memset'
./src/libfor/for_open_proc.c:(.text+0x48a8): undefined reference to `_intel_fast_memset'
./src/libfor/for_open_proc.c:(.text+0x4ed8): undefined reference to `_intel_fast_memcpy'
./src/libfor/for_open_proc.c:(.text+0x4f43): undefined reference to `_intel_fast_memcpy'
/usr/local/intel_fce_80/lib//libifcore.a(for_put.o): In function `for__put_su':
./src/libfor/for_put.c:(.text+0x68e): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(for_put.o): In function `for__put_sf':
./src/libfor/for_put.c:(.text+0x1d39): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(for_put.o): In function `for__put_d':
./src/libfor/for_put.c:(.text+0x1efa): undefined reference to `_intel_fast_memset'
./src/libfor/for_put.c:(.text+0x1f03): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(for_rseq_lis.o): In function `for_read_seq_lis_xmit':
./src/libfor/for_rseq_lis.c:(.text+0xa6b): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(for_rseq_lis.o): In function `rs_cvt_2step':
./src/libfor/for_rseq_lis.c:(.text+0x2086): undefined reference to `__qtod'
./src/libfor/for_rseq_lis.c:(.text+0x20f1): undefined reference to `__qtod'
/usr/local/intel_fce_80/lib//libifcore.a(for_wseq.o): In function `for_write_seq_xmit':
./src/libfor/for_wseq.c:(.text+0x1265): undefined reference to `_intel_fast_memcpy'
./src/libfor/for_wseq.c:(.text+0x1313): undefined reference to `_intel_fast_memcpy'
./src/libfor/for_wseq.c:(.text+0x157b): undefined reference to `_intel_fast_memcpy'
./src/libfor/for_wseq.c:(.text+0x1bb0): undefined reference to `_intel_fast_memcpy'
/usr/local/intel_fce_80/lib//libifcore.a(for_wseq.o): In function `for__finish_direct_write':
./src/libfor/for_wseq.c:(.text+0x330e): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(for_wseq.o): In function `for__write_from_user_buffer':
./src/libfor/for_wseq.c:(.text+0x3875): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(for_wseq_fmt.o): In function `for_write_seq_fmt':
./src/libfor/for_wseq_fmt.c:(.text+0x687): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(for_wseq_fmt.o): In function `for_write_seq_fmt_xmit':
./src/libfor/for_wseq_fmt.c:(.text+0x1063): undefined reference to `_intel_fast_memset'
./src/libfor/for_wseq_fmt.c:(.text+0x1da0): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(for_wseq_fmt.o):./src/libfor/for_wseq_fmt.c:(.text+0x2297): more undefined references to `_intel_fast_memset' follow
/usr/local/intel_fce_80/lib//libifcore.a(for_wseq_lis.o): In function `for_write_seq_lis_xmit':
./src/libfor/for_wseq_lis.c:(.text+0x1086): undefined reference to `_intel_fast_memcpy'
./src/libfor/for_wseq_lis.c:(.text+0x1383): undefined reference to `_intel_fast_memcpy'
./src/libfor/for_wseq_lis.c:(.text+0x169e): undefined reference to `_intel_fast_memcpy'
./src/libfor/for_wseq_lis.c:(.text+0x19b1): undefined reference to `_intel_fast_memcpy'
/usr/local/intel_fce_80/lib//libifcore.a(for_wseq_lis.o): In function `wseq_complex':
./src/libfor/for_wseq_lis.c:(.text+0x37f1): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(tbk_traceback.o): In function `tbk_stack_trace':
./src/libfor/tbk_traceback.c:(.text+0xae): undefined reference to `tbk_string_stack_signal'
/usr/local/intel_fce_80/lib//libifcore.a(for_fmt_val.o): In function `for__format_value':
./src/libfor/for_fmt_val.c:(.text+0xda6): undefined reference to `_intel_fast_memcpy'
/usr/local/intel_fce_80/lib//libifcore.a(for_fmt_val.o): In function `for__cvt_value':
./src/libfor/for_fmt_val.c:(.text+0x186d): undefined reference to `_intel_fast_memcpy'
./src/libfor/for_fmt_val.c:(.text+0x1880): undefined reference to `_intel_fast_memcpy'
/usr/local/intel_fce_80/lib//libifcore.a(for_get.o): In function `for__get_su':
./src/libfor/for_get.c:(.text+0x35d): undefined reference to `_intel_fast_memcpy'
./src/libfor/for_get.c:(.text+0x433): undefined reference to `_intel_fast_memcpy'
/usr/local/intel_fce_80/lib//libifcore.a(for_get.o):./src/libfor/for_get.c:(.text+0x770): more undefined references to `_intel_fast_memcpy' follow
/usr/local/intel_fce_80/lib//libifcore.a(cvt_cvtas_s.o): In function `cvt_ieee_s_to_text_ex':
./src/libfor/cvt_cvtas.c:(.text+0x357): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x488): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x547): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x5bf): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x5d8): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(cvt_cvtas_s.o):./src/libfor/cvt_cvtas.c:(.text+0x74d): more undefined references to `_intel_fast_memset' follow
/usr/local/intel_fce_80/lib//libifcore.a(cvt_cvtas_s.o): In function `cvt_ieee_s_to_text_ex':
./src/libfor/cvt_cvtas.c:(.text+0xa36): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0xabf): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0xb4f): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xc7f): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xcd6): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xd09): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xd50): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(cvt_cvtas_s.o):./src/libfor/cvt_cvtas.c:(.text+0xd69): more undefined references to `_intel_fast_memset' follow
/usr/local/intel_fce_80/lib//libifcore.a(cvt_cvtas_s.o): In function `cvt_ieee_s_to_text_ex':
./src/libfor/cvt_cvtas.c:(.text+0xe62): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0xef9): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0xf6d): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xfb3): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x1069): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x10cc): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x10f8): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x1138): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x11e1): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x11f5): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x125c): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x1270): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x13d9): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x13ed): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x1458): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x146c): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(cvt_cvtas_t.o): In function `cvt_ieee_t_to_text_ex':
./src/libfor/cvt_cvtas.c:(.text+0x371): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x4a2): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x561): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x5d9): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(cvt_cvtas_t.o):./src/libfor/cvt_cvtas.c:(.text+0x5f2): more undefined references to `_intel_fast_memset' follow
/usr/local/intel_fce_80/lib//libifcore.a(cvt_cvtas_t.o): In function `cvt_ieee_t_to_text_ex':
./src/libfor/cvt_cvtas.c:(.text+0xa50): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0xad9): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0xb69): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xc9a): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xcf1): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xd24): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xd6b): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(cvt_cvtas_t.o):./src/libfor/cvt_cvtas.c:(.text+0xd84): more undefined references to `_intel_fast_memset' follow
/usr/local/intel_fce_80/lib//libifcore.a(cvt_cvtas_t.o): In function `cvt_ieee_t_to_text_ex':
./src/libfor/cvt_cvtas.c:(.text+0xe7d): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0xf14): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0xf88): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xfce): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x10ee): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x1151): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x117d): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x11bd): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x1266): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x127a): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x12e1): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x12f5): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x145e): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x1472): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x14dd): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x14f1): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(cvt_cvtas_x.o): In function `cvt_ieee_x_to_text_ex':
./src/libfor/cvt_cvtas.c:(.text+0x420): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x559): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x62e): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x6a7): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(cvt_cvtas_x.o):./src/libfor/cvt_cvtas.c:(.text+0x6c0): more undefined references to `_intel_fast_memset' follow
/usr/local/intel_fce_80/lib//libifcore.a(cvt_cvtas_x.o): In function `cvt_ieee_x_to_text_ex':
./src/libfor/cvt_cvtas.c:(.text+0xb19): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0xb9f): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0xc31): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xcc7): undefined reference to `a_mulq'
./src/libfor/cvt_cvtas.c:(.text+0xd6e): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xdc5): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xdf8): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xe41): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xe5a): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(cvt_cvtas_x.o):./src/libfor/cvt_cvtas.c:(.text+0xee0): more undefined references to `_intel_fast_memset' follow
/usr/local/intel_fce_80/lib//libifcore.a(cvt_cvtas_x.o): In function `cvt_ieee_x_to_text_ex':
./src/libfor/cvt_cvtas.c:(.text+0xf58): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0xff1): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x1065): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x10ab): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x1231): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x1294): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x12be): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x12fe): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x13a7): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x13bb): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x1422): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x1436): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x1494): undefined reference to `a_divq'
./src/libfor/cvt_cvtas.c:(.text+0x153b): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x154f): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x15ba): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x15ce): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(cvt_text_to_data.o): In function `cvt_text_to_data':
./src/libfor/cvt_text_to_data.c:(.text+0x4b): undefined reference to `_intel_fast_memset'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(qdmod.o): In function `qdmodule_mp_assign_qd_str_':
qdmod.f:(.text+0x1f): undefined reference to `for_cpystr'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(qdmod.o): In function `qdmodule_mp_to_qd_str_':
qdmod.f:(.text+0x313): undefined reference to `for_cpystr'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(qdmod.o): In function `qdmodule_mp_qdinp_':
qdmod.f:(.text+0x4363): undefined reference to `for_read_seq_fmt'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(qdmod.o): In function `qdmodule_mp_qdinpc_':
qdmod.f:(.text+0x4460): undefined reference to `for_cpstr'
qdmod.f:(.text+0x454f): undefined reference to `for_cpstr'
qdmod.f:(.text+0x45c3): undefined reference to `for_cpystr'
qdmod.f:(.text+0x467e): undefined reference to `for_f90_index'
qdmod.f:(.text+0x46a8): undefined reference to `for_f90_index'
qdmod.f:(.text+0x47c7): undefined reference to `for_cpystr'
qdmod.f:(.text+0x4817): undefined reference to `for_cpystr'
qdmod.f:(.text+0x4894): undefined reference to `for_f90_index'
qdmod.f:(.text+0x48eb): undefined reference to `for_cpystr'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_qd.o): In function `f_qd_pi_':
f_qd.cpp:(.text+0x2c3): undefined reference to `qd_real::_pi'
f_qd.cpp:(.text+0x2cd): undefined reference to `qd_real::_pi'
f_qd.cpp:(.text+0x2d8): undefined reference to `qd_real::_pi'
f_qd.cpp:(.text+0x2e3): undefined reference to `qd_real::_pi'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_qd.o): In function `f_qd_nan_':
f_qd.cpp:(.text+0x2f3): undefined reference to `qd_real::_nan'
f_qd.cpp:(.text+0x2fd): undefined reference to `qd_real::_nan'
f_qd.cpp:(.text+0x308): undefined reference to `qd_real::_nan'
f_qd.cpp:(.text+0x313): undefined reference to `qd_real::_nan'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_qd.o): In function `global constructors keyed to f_qd_add_':
f_qd.cpp:(.text+0x32a): undefined reference to `std::ios_base::Init::Init()'
f_qd.cpp:(.text+0x339): undefined reference to `std::ios_base::Init::~Init()'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_qd.o): In function `f_qd_rand_':
f_qd.cpp:(.text+0x37c): undefined reference to `qdrand()'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_qd.o): In function `f_qd_swrite_':
f_qd.cpp:(.text+0x3cf): undefined reference to `qd_real::_ndigits'
f_qd.cpp:(.text+0x41f): undefined reference to `qd_real::to_string(int, int, std::_Ios_Fmtflags, bool, bool, char) const'
f_qd.cpp:(.text+0x481): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::_Rep::_S_empty_rep_storage'
f_qd.cpp:(.text+0x49a): undefined reference to `qd_real::_ndigits'
f_qd.cpp:(.text+0x4da): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::_Rep::_M_destroy(std::allocator<char> const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_qd.o): In function `f_qd_sincosh_':
f_qd.cpp:(.text+0x557): undefined reference to `sincosh(qd_real const&, qd_real&, qd_real&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_qd.o): In function `f_qd_sincos_':
f_qd.cpp:(.text+0x617): undefined reference to `sincos(qd_real const&, qd_real&, qd_real&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_qd.o): In function `f_qd_atanh_':
f_qd.cpp:(.text+0x6a3): undefined reference to `atanh(qd_real const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_qd.o): In function `f_qd_acosh_':
f_qd.cpp:(.text+0x703): undefined reference to `acosh(qd_real const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_qd.o): In function `f_qd_asinh_':
f_qd.cpp:(.text+0x763): undefined reference to `asinh(qd_real const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_qd.o): In function `f_qd_tanh_':
f_qd.cpp:(.text+0x7c3): undefined reference to `tanh(qd_real const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_qd.o): In function `f_qd_cosh_':
f_qd.cpp:(.text+0x823): undefined reference to `cosh(qd_real const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_qd.o): In function `f_qd_sinh_':
f_qd.cpp:(.text+0x883): undefined reference to `sinh(qd_real const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_qd.o): In function `f_qd_atan2_':
f_qd.cpp:(.text+0x90b): undefined reference to `atan2(qd_real const&, qd_real const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_qd.o): In function `f_qd_atan_':
f_qd.cpp:(.text+0x973): undefined reference to `atan(qd_real const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_qd.o): In function `f_qd_acos_':
f_qd.cpp:(.text+0x9d3): undefined reference to `acos(qd_real const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_qd.o): In function `f_qd_asin_':
f_qd.cpp:(.text+0xa33): undefined reference to `asin(qd_real const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_qd.o): In function `f_qd_tan_':
f_qd.cpp:(.text+0xa93): undefined reference to `tan(qd_real const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_qd.o): In function `f_qd_cos_':
f_qd.cpp:(.text+0xaf3): undefined reference to `cos(qd_real const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_qd.o): In function `f_qd_sin_':
f_qd.cpp:(.text+0xb53): undefined reference to `sin(qd_real const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_qd.o): In function `f_qd_exp_':
f_qd.cpp:(.text+0xbb3): undefined reference to `exp(qd_real const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_qd.o): In function `f_qd_log10_':
f_qd.cpp:(.text+0xc13): undefined reference to `log10(qd_real const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_qd.o): In function `f_qd_log_':
f_qd.cpp:(.text+0xc73): undefined reference to `log(qd_real const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_qd.o): In function `f_qd_ceil_':
f_qd.cpp:(.text+0xcd3): undefined reference to `ceil(qd_real const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_qd.o): In function `f_qd_floor_':
f_qd.cpp:(.text+0xd33): undefined reference to `floor(qd_real const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_qd.o): In function `f_qd_aint_':
f_qd.cpp:(.text+0xda0): undefined reference to `floor(qd_real const&)'
f_qd.cpp:(.text+0xdd9): undefined reference to `ceil(qd_real const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_qd.o): In function `f_qd_nint_':
f_qd.cpp:(.text+0xe13): undefined reference to `nint(qd_real const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_qd.o): In function `f_qd_nroot_':
f_qd.cpp:(.text+0xe75): undefined reference to `nroot(qd_real const&, int)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_qd.o): In function `f_qd_npwr_':
f_qd.cpp:(.text+0xee5): undefined reference to `npwr(qd_real const&, int)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_qd.o): In function `f_qd_sqrt_':
f_qd.cpp:(.text+0xf53): undefined reference to `sqrt(qd_real const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_qd.o): In function `f_qd_selfdiv_d':
f_qd.cpp:(.text+0xfb8): undefined reference to `operator/(qd_real const&, double)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_qd.o): In function `f_qd_div_qd_d_':
f_qd.cpp:(.text+0x1047): undefined reference to `operator/(qd_real const&, double)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_qd.o): In function `f_qd_selfdiv_dd':
f_qd.cpp:(.text+0x10ca): undefined reference to `qd_real::sloppy_div(qd_real const&, dd_real const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_qd.o): In function `f_qd_div_qd_dd_':
f_qd.cpp:(.text+0x116a): undefined reference to `qd_real::sloppy_div(qd_real const&, dd_real const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_qd.o): In function `f_qd_selfdiv':
f_qd.cpp:(.text+0x11fc): undefined reference to `qd_real::sloppy_div(qd_real const&, qd_real const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_qd.o): In function `f_qd_div_d_qd_':
f_qd.cpp:(.text+0x12a1): undefined reference to `qd_real::sloppy_div(qd_real const&, qd_real const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_qd.o): In function `f_qd_div_dd_qd_':
f_qd.cpp:(.text+0x1325): undefined reference to `qd_real::sloppy_div(qd_real const&, qd_real const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_qd.o): In function `f_qd_div_':
f_qd.cpp:(.text+0x13bc): undefined reference to `qd_real::sloppy_div(qd_real const&, qd_real const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_qd.o): In function `f_qd_write_':
f_qd.cpp:(.text+0x142d): undefined reference to `std::cout'
f_qd.cpp:(.text+0x143a): undefined reference to `operator<<(std::basic_ostream<char, std::char_traits<char> >&, qd_real const&)'
f_qd.cpp:(.text+0x14c7): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::put(char)'
f_qd.cpp:(.text+0x14cf): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::flush()'
f_qd.cpp:(.text+0x14f9): undefined reference to `std::__throw_bad_cast()'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_qd.o):(.eh_frame+0x12): undefined reference to `__gxx_personality_v0'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(ddmod.o): In function `ddmodule_mp_assign_dd_str_':
ddmod.f:(.text+0x1f): undefined reference to `for_cpystr'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(ddmod.o): In function `ddmodule_mp_to_dd_str_':
ddmod.f:(.text+0x1d1): undefined reference to `for_cpystr'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(ddmod.o): In function `ddmodule_mp_ddinp_':
ddmod.f:(.text+0x412d): undefined reference to `for_read_seq_fmt'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(ddmod.o): In function `ddmodule_mp_ddinpc_':
ddmod.f:(.text+0x421e): undefined reference to `for_cpstr'
ddmod.f:(.text+0x430d): undefined reference to `for_cpstr'
ddmod.f:(.text+0x4381): undefined reference to `for_cpystr'
ddmod.f:(.text+0x443c): undefined reference to `for_f90_index'
ddmod.f:(.text+0x4466): undefined reference to `for_f90_index'
ddmod.f:(.text+0x455b): undefined reference to `for_cpystr'
ddmod.f:(.text+0x45ab): undefined reference to `for_cpystr'
ddmod.f:(.text+0x4628): undefined reference to `for_f90_index'
ddmod.f:(.text+0x467f): undefined reference to `for_cpystr'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(ddmod.o): In function `ddmodule_mp_dddigin_':
ddmod.f:(.text+0x4904): undefined reference to `for_f90_index'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(ddmod.o): In function `ddmodule_mp_dddigout_':
ddmod.f:(.text+0x49e5): undefined reference to `for_cpystr'
ddmod.f:(.text+0x4a76): undefined reference to `d_int_val'
ddmod.f:(.text+0x4b0a): undefined reference to `for_cpystr'
ddmod.f:(.text+0x4bd4): undefined reference to `for_cpystr'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_dd.o): In function `f_dd_pi_':
f_dd.cpp:(.text+0x623): undefined reference to `dd_real::_pi'
f_dd.cpp:(.text+0x62d): undefined reference to `dd_real::_pi'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_dd.o): In function `f_dd_nan_':
f_dd.cpp:(.text+0x643): undefined reference to `dd_real::_nan'
f_dd.cpp:(.text+0x64d): undefined reference to `dd_real::_nan'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_dd.o): In function `global constructors keyed to f_dd_add_':
f_dd.cpp:(.text+0x66a): undefined reference to `std::ios_base::Init::Init()'
f_dd.cpp:(.text+0x679): undefined reference to `std::ios_base::Init::~Init()'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_dd.o): In function `f_dd_rand_':
f_dd.cpp:(.text+0x6b9): undefined reference to `ddrand()'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_dd.o): In function `f_dd_swrite_':
f_dd.cpp:(.text+0x71f): undefined reference to `dd_real::_ndigits'
f_dd.cpp:(.text+0x75d): undefined reference to `dd_real::to_string(int, int, std::_Ios_Fmtflags, bool, bool, char) const'
f_dd.cpp:(.text+0x7c1): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::_Rep::_S_empty_rep_storage'
f_dd.cpp:(.text+0x7da): undefined reference to `dd_real::_ndigits'
f_dd.cpp:(.text+0x81a): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::_Rep::_M_destroy(std::allocator<char> const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_dd.o): In function `f_dd_sincosh_':
f_dd.cpp:(.text+0x871): undefined reference to `sincosh(dd_real const&, dd_real&, dd_real&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_dd.o): In function `f_dd_sincos_':
f_dd.cpp:(.text+0x8f1): undefined reference to `sincos(dd_real const&, dd_real&, dd_real&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_dd.o): In function `f_dd_atanh_':
f_dd.cpp:(.text+0x94f): undefined reference to `atanh(dd_real const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_dd.o): In function `f_dd_acosh_':
f_dd.cpp:(.text+0x9af): undefined reference to `acosh(dd_real const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_dd.o): In function `f_dd_asinh_':
f_dd.cpp:(.text+0xa0f): undefined reference to `asinh(dd_real const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_dd.o): In function `f_dd_tanh_':
f_dd.cpp:(.text+0xa6f): undefined reference to `tanh(dd_real const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_dd.o): In function `f_dd_cosh_':
f_dd.cpp:(.text+0xacf): undefined reference to `cosh(dd_real const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_dd.o): In function `f_dd_sinh_':
f_dd.cpp:(.text+0xb2f): undefined reference to `sinh(dd_real const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_dd.o): In function `f_dd_atan2_':
f_dd.cpp:(.text+0xba5): undefined reference to `atan2(dd_real const&, dd_real const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_dd.o): In function `f_dd_atan_':
f_dd.cpp:(.text+0xbff): undefined reference to `atan(dd_real const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_dd.o): In function `f_dd_acos_':
f_dd.cpp:(.text+0xc5f): undefined reference to `acos(dd_real const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_dd.o): In function `f_dd_asin_':
f_dd.cpp:(.text+0xcbf): undefined reference to `asin(dd_real const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_dd.o): In function `f_dd_tan_':
f_dd.cpp:(.text+0xd1f): undefined reference to `tan(dd_real const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_dd.o): In function `f_dd_cos_':
f_dd.cpp:(.text+0xd7f): undefined reference to `cos(dd_real const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_dd.o): In function `f_dd_sin_':
f_dd.cpp:(.text+0xddf): undefined reference to `sin(dd_real const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_dd.o): In function `f_dd_exp_':
f_dd.cpp:(.text+0xe3f): undefined reference to `exp(dd_real const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_dd.o): In function `f_dd_log10_':
f_dd.cpp:(.text+0xe9f): undefined reference to `log10(dd_real const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_dd.o): In function `f_dd_log_':
f_dd.cpp:(.text+0xeff): undefined reference to `log(dd_real const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_dd.o): In function `f_dd_aint_':
f_dd.cpp:(.text+0xf6b): undefined reference to `floor'
f_dd.cpp:(.text+0xfa7): undefined reference to `floor'
f_dd.cpp:(.text+0xfe2): undefined reference to `ceil'
f_dd.cpp:(.text+0x100c): undefined reference to `ceil'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_dd.o): In function `f_dd_nroot_':
f_dd.cpp:(.text+0x1041): undefined reference to `nroot(dd_real const&, int)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_dd.o): In function `f_dd_npwr_':
f_dd.cpp:(.text+0x10a1): undefined reference to `npwr(dd_real const&, int)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_dd.o): In function `f_dd_sqrt_':
f_dd.cpp:(.text+0x10ff): undefined reference to `sqrt(dd_real const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_dd.o): In function `f_dd_nint_':
f_dd.cpp:(.text+0x1162): undefined reference to `floor'
f_dd.cpp:(.text+0x120d): undefined reference to `floor'
f_dd.cpp:(.text+0x1237): undefined reference to `floor'
f_dd.cpp:(.text+0x128d): undefined reference to `floor'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_dd.o): In function `f_dd_floor_':
f_dd.cpp:(.text+0x12be): undefined reference to `floor'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_dd.o):f_dd.cpp:(.text+0x12fc): more undefined references to `floor' follow
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_dd.o): In function `f_dd_ceil_':
f_dd.cpp:(.text+0x134e): undefined reference to `ceil'
f_dd.cpp:(.text+0x138c): undefined reference to `ceil'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_dd.o): In function `f_dd_write_':
f_dd.cpp:(.text+0x13d4): undefined reference to `std::cout'
f_dd.cpp:(.text+0x13de): undefined reference to `operator<<(std::basic_ostream<char, std::char_traits<char> >&, dd_real const&)'
f_dd.cpp:(.text+0x13f5): undefined reference to `std::basic_ios<char, std::char_traits<char> >::widen(char) const'
f_dd.cpp:(.text+0x1400): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::put(char)'
f_dd.cpp:(.text+0x1408): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::flush()'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_dd.o):(.eh_frame+0x12): undefined reference to `__gxx_personality_v0'
/local/peter/tt/masters/PSI/Fortran-0.001-0.45//libode128.a(zvode.o): In function `zvode_':
zvode.f:(.text+0x1cb): undefined reference to `for_cpystr'
zvode.f:(.text+0x26f): undefined reference to `for_cpystr'
zvode.f:(.text+0x30c): undefined reference to `for_cpystr'
zvode.f:(.text+0x3a0): undefined reference to `for_cpystr'
zvode.f:(.text+0x45f): undefined reference to `for_cpystr'
/local/peter/tt/masters/PSI/Fortran-0.001-0.45//libode128.a(zvode.o):zvode.f:(.text+0x4f4): more undefined references to `for_cpystr' follow
collect2: ld returned 1 exit status
pbaernreuther@wthp098:/local/peter/tt/masters/Gluons/Fortran/Paket> /usr/bin/gcc -static -static-libgcc -L/local/peter/tt/masters/PSI/qd/lib/  -L/usr/local/intel_fce_80/lib/ -L/local/peter/tt/masters/PSI/Fortran-0.001-0.45/ -L/local/peter/tt/masters/PSI/ODE/quadrupole/ -o ggtt2l ggtt2l.o -lifport -lifcore -lifport -lqd -lqd_f_main -lqdmod -ljac2lm128 -ljac2lx128 -lode128
pbaernreuther@wthp098:/local/peter/tt/masters/Gluons/Fortran/Paket> less Makefile 
pbaernreuther@wthp098:/local/peter/tt/masters/Gluons/Fortran/Paket> /usr/bin/gcc -static -static-libgcc -L/local/peter/tt/masters/PSI/qd/lib/  -L/usr/local/intel_fce_80/lib/ -L/local/peter/tt/masters/PSI/Fortran-0.001-0.45/ -L/local/peter/tt/masters/PSI/ODE/quadrupole/ -o ggtt2l ggtt2l.o -lifport -lifcore -lifport -lqd -lqd_f_main -lqdmod -lqd  -ljac2lm128 -ljac2lx128 -lode128
pbaernreuther@wthp098:/local/peter/tt/masters/Gluons/Fortran/Paket> less Makefile 
pbaernreuther@wthp098:/local/peter/tt/masters/Gluons/Fortran/Paket> /usr/bin/gcc -static -static-libgcc -L/local/peter/tt/masters/PSI/qd/lib/  -L/usr/local/intel_fce_80/lib/ -L/local/peter/tt/masters/PSI/Fortran-0.001-0.45/ -L/local/peter/tt/masters/PSI/ODE/quadrupole/ -o ggtt2l ggtt2l.o -lifcore -lifport -lqd_f_main -lqdmod -lqd  -ljac2lm128 -ljac2lx128 -lode128
/usr/local/intel_fce_80/lib//libifcore.a(for_open_proc.o): In function `for__compute_filename':
./src/libfor/for_open_proc.c:(.text+0x3dec): warning: Using 'getpwnam' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
./src/libfor/for_open_proc.c:(.text+0x3f0a): warning: Using 'getpwuid' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking
/usr/local/intel_fce_80/lib//libifcore.a(for_close_proc.o): In function `for__close_proc':
./src/libfor/for_close_proc.c:(.text+0x3dc): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(for_diags_intel.o): In function `for__io_return':
./src/libfor/for_diags_intel.c:(.text+0x6d0): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(for_diags_intel.o): In function `for_emit_diagnostic':
./src/libfor/for_diags_intel.c:(.text+0x996): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(for_diags_intel.o): In function `for_gerror_':
./src/libfor/for_diags_intel.c:(.text+0xafe): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(for_diags_intel.o): In function `tracebackqq_':
./src/libfor/for_diags_intel.c:(.text+0x117f): undefined reference to `_intel_fast_memset'
./src/libfor/for_diags_intel.c:(.text+0x1193): undefined reference to `_intel_fast_memcpy'
/usr/local/intel_fce_80/lib//libifcore.a(for_io_util.o): In function `for__adjust_buffer':
./src/libfor/for_io_util.c:(.text+0x4c4): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(for_io_util.o): In function `for__cvt_foreign_write':
./src/libfor/for_io_util.c:(.text+0x8f5): undefined reference to `_intel_fast_memcpy'
/usr/local/intel_fce_80/lib//libifcore.a(for_lub_mgt.o): In function `create_lub':
./src/libfor/for_lub_mgt.c:(.text+0x44): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(for_main.o): In function `main':
./src/libfor/for_main.c:(.text+0x24): undefined reference to `MAIN__'
/usr/local/intel_fce_80/lib//libifcore.a(for_open.o): In function `for_open':
./src/libfor/for_open.c:(.text+0x76c): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(for_open.o): In function `for__open_default':
./src/libfor/for_open.c:(.text+0xcba): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(for_open_proc.o): In function `for__compute_filename':
./src/libfor/for_open_proc.c:(.text+0x3357): undefined reference to `_intel_fast_memcpy'
./src/libfor/for_open_proc.c:(.text+0x3580): undefined reference to `_intel_fast_memcpy'
./src/libfor/for_open_proc.c:(.text+0x35f9): undefined reference to `_intel_fast_memcpy'
./src/libfor/for_open_proc.c:(.text+0x374d): undefined reference to `_intel_fast_memcpy'
./src/libfor/for_open_proc.c:(.text+0x3785): undefined reference to `_intel_fast_memcpy'
/usr/local/intel_fce_80/lib//libifcore.a(for_open_proc.o):./src/libfor/for_open_proc.c:(.text+0x3b81): more undefined references to `_intel_fast_memcpy' follow
/usr/local/intel_fce_80/lib//libifcore.a(for_open_proc.o): In function `for__prompt_user':
./src/libfor/for_open_proc.c:(.text+0x4882): undefined reference to `_intel_fast_memset'
./src/libfor/for_open_proc.c:(.text+0x4895): undefined reference to `_intel_fast_memset'
./src/libfor/for_open_proc.c:(.text+0x48a8): undefined reference to `_intel_fast_memset'
./src/libfor/for_open_proc.c:(.text+0x4ed8): undefined reference to `_intel_fast_memcpy'
./src/libfor/for_open_proc.c:(.text+0x4f43): undefined reference to `_intel_fast_memcpy'
/usr/local/intel_fce_80/lib//libifcore.a(for_put.o): In function `for__put_su':
./src/libfor/for_put.c:(.text+0x68e): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(for_put.o): In function `for__put_sf':
./src/libfor/for_put.c:(.text+0x1d39): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(for_put.o): In function `for__put_d':
./src/libfor/for_put.c:(.text+0x1efa): undefined reference to `_intel_fast_memset'
./src/libfor/for_put.c:(.text+0x1f03): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(for_rseq_lis.o): In function `for_read_seq_lis_xmit':
./src/libfor/for_rseq_lis.c:(.text+0xa6b): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(for_rseq_lis.o): In function `rs_cvt_2step':
./src/libfor/for_rseq_lis.c:(.text+0x2086): undefined reference to `__qtod'
./src/libfor/for_rseq_lis.c:(.text+0x20f1): undefined reference to `__qtod'
/usr/local/intel_fce_80/lib//libifcore.a(for_wseq.o): In function `for_write_seq_xmit':
./src/libfor/for_wseq.c:(.text+0x1265): undefined reference to `_intel_fast_memcpy'
./src/libfor/for_wseq.c:(.text+0x1313): undefined reference to `_intel_fast_memcpy'
./src/libfor/for_wseq.c:(.text+0x157b): undefined reference to `_intel_fast_memcpy'
./src/libfor/for_wseq.c:(.text+0x1bb0): undefined reference to `_intel_fast_memcpy'
/usr/local/intel_fce_80/lib//libifcore.a(for_wseq.o): In function `for__finish_direct_write':
./src/libfor/for_wseq.c:(.text+0x330e): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(for_wseq.o): In function `for__write_from_user_buffer':
./src/libfor/for_wseq.c:(.text+0x3875): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(for_wseq_fmt.o): In function `for_write_seq_fmt':
./src/libfor/for_wseq_fmt.c:(.text+0x687): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(for_wseq_fmt.o): In function `for_write_seq_fmt_xmit':
./src/libfor/for_wseq_fmt.c:(.text+0x1063): undefined reference to `_intel_fast_memset'
./src/libfor/for_wseq_fmt.c:(.text+0x1da0): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(for_wseq_fmt.o):./src/libfor/for_wseq_fmt.c:(.text+0x2297): more undefined references to `_intel_fast_memset' follow
/usr/local/intel_fce_80/lib//libifcore.a(for_wseq_lis.o): In function `for_write_seq_lis_xmit':
./src/libfor/for_wseq_lis.c:(.text+0x1086): undefined reference to `_intel_fast_memcpy'
./src/libfor/for_wseq_lis.c:(.text+0x1383): undefined reference to `_intel_fast_memcpy'
./src/libfor/for_wseq_lis.c:(.text+0x169e): undefined reference to `_intel_fast_memcpy'
./src/libfor/for_wseq_lis.c:(.text+0x19b1): undefined reference to `_intel_fast_memcpy'
/usr/local/intel_fce_80/lib//libifcore.a(for_wseq_lis.o): In function `wseq_complex':
./src/libfor/for_wseq_lis.c:(.text+0x37f1): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(tbk_traceback.o): In function `tbk_stack_trace':
./src/libfor/tbk_traceback.c:(.text+0xae): undefined reference to `tbk_string_stack_signal'
/usr/local/intel_fce_80/lib//libifcore.a(for_fmt_val.o): In function `for__format_value':
./src/libfor/for_fmt_val.c:(.text+0xda6): undefined reference to `_intel_fast_memcpy'
/usr/local/intel_fce_80/lib//libifcore.a(for_fmt_val.o): In function `for__cvt_value':
./src/libfor/for_fmt_val.c:(.text+0x186d): undefined reference to `_intel_fast_memcpy'
./src/libfor/for_fmt_val.c:(.text+0x1880): undefined reference to `_intel_fast_memcpy'
/usr/local/intel_fce_80/lib//libifcore.a(for_get.o): In function `for__get_su':
./src/libfor/for_get.c:(.text+0x35d): undefined reference to `_intel_fast_memcpy'
./src/libfor/for_get.c:(.text+0x433): undefined reference to `_intel_fast_memcpy'
/usr/local/intel_fce_80/lib//libifcore.a(for_get.o):./src/libfor/for_get.c:(.text+0x770): more undefined references to `_intel_fast_memcpy' follow
/usr/local/intel_fce_80/lib//libifcore.a(cvt_cvtas_s.o): In function `cvt_ieee_s_to_text_ex':
./src/libfor/cvt_cvtas.c:(.text+0x357): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x488): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x547): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x5bf): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x5d8): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(cvt_cvtas_s.o):./src/libfor/cvt_cvtas.c:(.text+0x74d): more undefined references to `_intel_fast_memset' follow
/usr/local/intel_fce_80/lib//libifcore.a(cvt_cvtas_s.o): In function `cvt_ieee_s_to_text_ex':
./src/libfor/cvt_cvtas.c:(.text+0xa36): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0xabf): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0xb4f): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xc7f): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xcd6): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xd09): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xd50): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(cvt_cvtas_s.o):./src/libfor/cvt_cvtas.c:(.text+0xd69): more undefined references to `_intel_fast_memset' follow
/usr/local/intel_fce_80/lib//libifcore.a(cvt_cvtas_s.o): In function `cvt_ieee_s_to_text_ex':
./src/libfor/cvt_cvtas.c:(.text+0xe62): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0xef9): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0xf6d): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xfb3): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x1069): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x10cc): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x10f8): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x1138): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x11e1): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x11f5): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x125c): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x1270): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x13d9): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x13ed): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x1458): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x146c): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(cvt_cvtas_t.o): In function `cvt_ieee_t_to_text_ex':
./src/libfor/cvt_cvtas.c:(.text+0x371): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x4a2): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x561): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x5d9): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(cvt_cvtas_t.o):./src/libfor/cvt_cvtas.c:(.text+0x5f2): more undefined references to `_intel_fast_memset' follow
/usr/local/intel_fce_80/lib//libifcore.a(cvt_cvtas_t.o): In function `cvt_ieee_t_to_text_ex':
./src/libfor/cvt_cvtas.c:(.text+0xa50): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0xad9): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0xb69): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xc9a): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xcf1): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xd24): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xd6b): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(cvt_cvtas_t.o):./src/libfor/cvt_cvtas.c:(.text+0xd84): more undefined references to `_intel_fast_memset' follow
/usr/local/intel_fce_80/lib//libifcore.a(cvt_cvtas_t.o): In function `cvt_ieee_t_to_text_ex':
./src/libfor/cvt_cvtas.c:(.text+0xe7d): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0xf14): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0xf88): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xfce): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x10ee): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x1151): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x117d): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x11bd): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x1266): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x127a): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x12e1): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x12f5): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x145e): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x1472): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x14dd): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x14f1): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(cvt_cvtas_x.o): In function `cvt_ieee_x_to_text_ex':
./src/libfor/cvt_cvtas.c:(.text+0x420): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x559): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x62e): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x6a7): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(cvt_cvtas_x.o):./src/libfor/cvt_cvtas.c:(.text+0x6c0): more undefined references to `_intel_fast_memset' follow
/usr/local/intel_fce_80/lib//libifcore.a(cvt_cvtas_x.o): In function `cvt_ieee_x_to_text_ex':
./src/libfor/cvt_cvtas.c:(.text+0xb19): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0xb9f): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0xc31): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xcc7): undefined reference to `a_mulq'
./src/libfor/cvt_cvtas.c:(.text+0xd6e): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xdc5): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xdf8): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xe41): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0xe5a): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(cvt_cvtas_x.o):./src/libfor/cvt_cvtas.c:(.text+0xee0): more undefined references to `_intel_fast_memset' follow
/usr/local/intel_fce_80/lib//libifcore.a(cvt_cvtas_x.o): In function `cvt_ieee_x_to_text_ex':
./src/libfor/cvt_cvtas.c:(.text+0xf58): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0xff1): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x1065): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x10ab): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x1231): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x1294): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x12be): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x12fe): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x13a7): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x13bb): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x1422): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x1436): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x1494): undefined reference to `a_divq'
./src/libfor/cvt_cvtas.c:(.text+0x153b): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x154f): undefined reference to `_intel_fast_memset'
./src/libfor/cvt_cvtas.c:(.text+0x15ba): undefined reference to `_intel_fast_memcpy'
./src/libfor/cvt_cvtas.c:(.text+0x15ce): undefined reference to `_intel_fast_memset'
/usr/local/intel_fce_80/lib//libifcore.a(cvt_text_to_data.o): In function `cvt_text_to_data':
./src/libfor/cvt_text_to_data.c:(.text+0x4b): undefined reference to `_intel_fast_memset'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(qdmod.o): In function `qdmodule_mp_assign_qd_str_':
qdmod.f:(.text+0x1f): undefined reference to `for_cpystr'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(qdmod.o): In function `qdmodule_mp_to_qd_str_':
qdmod.f:(.text+0x313): undefined reference to `for_cpystr'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(qdmod.o): In function `qdmodule_mp_qdinp_':
qdmod.f:(.text+0x4363): undefined reference to `for_read_seq_fmt'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(qdmod.o): In function `qdmodule_mp_qdinpc_':
qdmod.f:(.text+0x4460): undefined reference to `for_cpstr'
qdmod.f:(.text+0x454f): undefined reference to `for_cpstr'
qdmod.f:(.text+0x45c3): undefined reference to `for_cpystr'
qdmod.f:(.text+0x467e): undefined reference to `for_f90_index'
qdmod.f:(.text+0x46a8): undefined reference to `for_f90_index'
qdmod.f:(.text+0x47c7): undefined reference to `for_cpystr'
qdmod.f:(.text+0x4817): undefined reference to `for_cpystr'
qdmod.f:(.text+0x4894): undefined reference to `for_f90_index'
qdmod.f:(.text+0x48eb): undefined reference to `for_cpystr'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_qd.o): In function `global constructors keyed to f_qd_add_':
f_qd.cpp:(.text+0x32a): undefined reference to `std::ios_base::Init::Init()'
f_qd.cpp:(.text+0x339): undefined reference to `std::ios_base::Init::~Init()'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_qd.o): In function `f_qd_swrite_':
f_qd.cpp:(.text+0x481): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::_Rep::_S_empty_rep_storage'
f_qd.cpp:(.text+0x4da): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::_Rep::_M_destroy(std::allocator<char> const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_qd.o): In function `f_qd_write_':
f_qd.cpp:(.text+0x142d): undefined reference to `std::cout'
f_qd.cpp:(.text+0x14c7): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::put(char)'
f_qd.cpp:(.text+0x14cf): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::flush()'
f_qd.cpp:(.text+0x14f9): undefined reference to `std::__throw_bad_cast()'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_qd.o):(.eh_frame+0x12): undefined reference to `__gxx_personality_v0'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(ddmod.o): In function `ddmodule_mp_assign_dd_str_':
ddmod.f:(.text+0x1f): undefined reference to `for_cpystr'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(ddmod.o): In function `ddmodule_mp_to_dd_str_':
ddmod.f:(.text+0x1d1): undefined reference to `for_cpystr'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(ddmod.o): In function `ddmodule_mp_ddinp_':
ddmod.f:(.text+0x412d): undefined reference to `for_read_seq_fmt'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(ddmod.o): In function `ddmodule_mp_ddinpc_':
ddmod.f:(.text+0x421e): undefined reference to `for_cpstr'
ddmod.f:(.text+0x430d): undefined reference to `for_cpstr'
ddmod.f:(.text+0x4381): undefined reference to `for_cpystr'
ddmod.f:(.text+0x443c): undefined reference to `for_f90_index'
ddmod.f:(.text+0x4466): undefined reference to `for_f90_index'
ddmod.f:(.text+0x455b): undefined reference to `for_cpystr'
ddmod.f:(.text+0x45ab): undefined reference to `for_cpystr'
ddmod.f:(.text+0x4628): undefined reference to `for_f90_index'
ddmod.f:(.text+0x467f): undefined reference to `for_cpystr'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(ddmod.o): In function `ddmodule_mp_dddigin_':
ddmod.f:(.text+0x4904): undefined reference to `for_f90_index'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(ddmod.o): In function `ddmodule_mp_dddigout_':
ddmod.f:(.text+0x49e5): undefined reference to `for_cpystr'
ddmod.f:(.text+0x4a76): undefined reference to `d_int_val'
ddmod.f:(.text+0x4b0a): undefined reference to `for_cpystr'
ddmod.f:(.text+0x4bd4): undefined reference to `for_cpystr'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_dd.o): In function `global constructors keyed to f_dd_add_':
f_dd.cpp:(.text+0x66a): undefined reference to `std::ios_base::Init::Init()'
f_dd.cpp:(.text+0x679): undefined reference to `std::ios_base::Init::~Init()'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_dd.o): In function `f_dd_swrite_':
f_dd.cpp:(.text+0x7c1): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::_Rep::_S_empty_rep_storage'
f_dd.cpp:(.text+0x81a): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::_Rep::_M_destroy(std::allocator<char> const&)'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_dd.o): In function `f_dd_aint_':
f_dd.cpp:(.text+0xf6b): undefined reference to `floor'
f_dd.cpp:(.text+0xfa7): undefined reference to `floor'
f_dd.cpp:(.text+0xfe2): undefined reference to `ceil'
f_dd.cpp:(.text+0x100c): undefined reference to `ceil'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_dd.o): In function `f_dd_nint_':
f_dd.cpp:(.text+0x1162): undefined reference to `floor'
f_dd.cpp:(.text+0x120d): undefined reference to `floor'
f_dd.cpp:(.text+0x1237): undefined reference to `floor'
f_dd.cpp:(.text+0x128d): undefined reference to `floor'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_dd.o): In function `f_dd_floor_':
f_dd.cpp:(.text+0x12be): undefined reference to `floor'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_dd.o):f_dd.cpp:(.text+0x12fc): more undefined references to `floor' follow
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_dd.o): In function `f_dd_ceil_':
f_dd.cpp:(.text+0x134e): undefined reference to `ceil'
f_dd.cpp:(.text+0x138c): undefined reference to `ceil'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_dd.o): In function `f_dd_write_':
f_dd.cpp:(.text+0x13d4): undefined reference to `std::cout'
f_dd.cpp:(.text+0x13f5): undefined reference to `std::basic_ios<char, std::char_traits<char> >::widen(char) const'
f_dd.cpp:(.text+0x1400): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::put(char)'
f_dd.cpp:(.text+0x1408): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::flush()'
/local/peter/tt/masters/PSI/qd/lib//libqdmod.a(f_dd.o):(.eh_frame+0x12): undefined reference to `__gxx_personality_v0'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(dd_real.o): In function `global constructors keyed to _ZN7dd_real5errorEPKc':
dd_real.cpp:(.text+0xa): undefined reference to `std::ios_base::Init::Init()'
dd_real.cpp:(.text+0x19): undefined reference to `std::ios_base::Init::~Init()'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(dd_real.o): In function `dd_real::dump_bits(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::basic_ostream<char, std::char_traits<char> >&) const':
dd_real.cpp:(.text+0x7eb): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::__ostream_insert<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*, long)'
dd_real.cpp:(.text+0x88b): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::put(char)'
dd_real.cpp:(.text+0x893): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::flush()'
dd_real.cpp:(.text+0x8c8): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::__ostream_insert<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*, long)'
dd_real.cpp:(.text+0x8ed): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::__ostream_insert<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*, long)'
dd_real.cpp:(.text+0x977): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::put(char)'
dd_real.cpp:(.text+0x97f): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::flush()'
dd_real.cpp:(.text+0x9cd): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::__ostream_insert<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*, long)'
dd_real.cpp:(.text+0x9df): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::__ostream_insert<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*, long)'
dd_real.cpp:(.text+0x9e9): undefined reference to `std::__throw_bad_cast()'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(dd_real.o): In function `dd_real::error(char const*)':
dd_real.cpp:(.text+0xa12): undefined reference to `std::cerr'
dd_real.cpp:(.text+0xa17): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::__ostream_insert<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*, long)'
dd_real.cpp:(.text+0xa2a): undefined reference to `std::cerr'
dd_real.cpp:(.text+0xa2f): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::__ostream_insert<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*, long)'
dd_real.cpp:(.text+0xa36): undefined reference to `std::cerr'
dd_real.cpp:(.text+0xa41): undefined reference to `std::cerr'
dd_real.cpp:(.text+0xab8): undefined reference to `std::cerr'
dd_real.cpp:(.text+0xac0): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::put(char)'
dd_real.cpp:(.text+0xac8): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::flush()'
dd_real.cpp:(.text+0xae1): undefined reference to `std::__throw_bad_cast()'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(dd_real.o): In function `operator>>(std::basic_istream<char, std::char_traits<char> >&, dd_real&)':
dd_real.cpp:(.text+0x1470): undefined reference to `std::basic_istream<char, std::char_traits<char> >& std::operator>><char, std::char_traits<char> >(std::basic_istream<char, std::char_traits<char> >&, char*)'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(dd_real.o): In function `sqrt(dd_real const&)':
dd_real.cpp:(.text+0x1695): undefined reference to `sqrt'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(dd_real.o): In function `dd_real::dump(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::basic_ostream<char, std::char_traits<char> >&) const':
dd_real.cpp:(.text+0x1773): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::__ostream_insert<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*, long)'
dd_real.cpp:(.text+0x1785): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::__ostream_insert<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*, long)'
dd_real.cpp:(.text+0x17ad): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::__ostream_insert<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*, long)'
dd_real.cpp:(.text+0x17cc): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::basic_ostream<char, std::char_traits<char> >::_M_insert<double>(double)'
dd_real.cpp:(.text+0x17e1): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::__ostream_insert<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*, long)'
dd_real.cpp:(.text+0x17ff): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::basic_ostream<char, std::char_traits<char> >::_M_insert<double>(double)'
dd_real.cpp:(.text+0x1814): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::__ostream_insert<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*, long)'
dd_real.cpp:(.text+0x18a0): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::put(char)'
dd_real.cpp:(.text+0x18a8): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::flush()'
dd_real.cpp:(.text+0x18e9): undefined reference to `std::__throw_bad_cast()'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(dd_real.o): In function `polyroot(dd_real const*, int, dd_real const&, int, double)':
dd_real.cpp:(.text+0x1931): undefined reference to `operator new[](unsigned long)'
dd_real.cpp:(.text+0x1c2a): undefined reference to `operator delete[](void*)'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(dd_real.o): In function `fmod(dd_real const&, dd_real const&)':
dd_real.cpp:(.text+0x2cf3): undefined reference to `floor'
dd_real.cpp:(.text+0x2fbf): undefined reference to `floor'
dd_real.cpp:(.text+0x300f): undefined reference to `ceil'
dd_real.cpp:(.text+0x305b): undefined reference to `ceil'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(dd_real.o): In function `exp(dd_real const&)':
dd_real.cpp:(.text+0x3108): undefined reference to `floor'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(dd_real.o): In function `log(dd_real const&)':
dd_real.cpp:(.text+0x4664): undefined reference to `log'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(dd_real.o): In function `cos(dd_real const&)':
dd_real.cpp:(.text+0x5707): undefined reference to `floor'
dd_real.cpp:(.text+0x58ec): undefined reference to `floor'
dd_real.cpp:(.text+0x5a61): undefined reference to `floor'
dd_real.cpp:(.text+0x5de0): undefined reference to `floor'
dd_real.cpp:(.text+0x5e33): undefined reference to `floor'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(dd_real.o):dd_real.cpp:(.text+0x62cb): more undefined references to `floor' follow
/local/peter/tt/masters/PSI/qd/lib//libqd.a(dd_real.o): In function `atan2(dd_real const&, dd_real const&)':
dd_real.cpp:(.text+0x8ecc): undefined reference to `atan2'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(dd_real.o): In function `nroot(dd_real const&, int)':
dd_real.cpp:(.text+0x9f37): undefined reference to `log'
dd_real.cpp:(.text+0x9f52): undefined reference to `exp'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(dd_real.o): In function `dd_real::to_digits(char*, int&, int) const':
dd_real.cpp:(.text+0xa85d): undefined reference to `log10'
dd_real.cpp:(.text+0xa862): undefined reference to `floor'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(dd_real.o): In function `dd_real::to_string(int, int, std::_Ios_Fmtflags, bool, bool, char) const':
dd_real.cpp:(.text+0xb33d): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::_Rep::_S_empty_rep_storage'
dd_real.cpp:(.text+0xb3e0): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::append(char const*, unsigned long)'
dd_real.cpp:(.text+0xb430): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::_M_replace_aux(unsigned long, unsigned long, unsigned long, char)'
dd_real.cpp:(.text+0xb45c): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::_M_replace_aux(unsigned long, unsigned long, unsigned long, char)'
dd_real.cpp:(.text+0xb4ad): undefined reference to `operator new[](unsigned long)'
dd_real.cpp:(.text+0xb505): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::reserve(unsigned long)'
dd_real.cpp:(.text+0xb547): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::push_back(char)'
dd_real.cpp:(.text+0xb57f): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::reserve(unsigned long)'
dd_real.cpp:(.text+0xb5bc): undefined reference to `operator delete[](void*)'
dd_real.cpp:(.text+0xb614): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::reserve(unsigned long)'
dd_real.cpp:(.text+0xb675): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::reserve(unsigned long)'
dd_real.cpp:(.text+0xb6dc): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::append(unsigned long, char)'
dd_real.cpp:(.text+0xb717): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::push_back(char)'
dd_real.cpp:(.text+0xb730): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::push_back(char)'
dd_real.cpp:(.text+0xb742): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::append(unsigned long, char)'
dd_real.cpp:(.text+0xb7a0): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::reserve(unsigned long)'
dd_real.cpp:(.text+0xb805): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::assign(char const*, unsigned long)'
dd_real.cpp:(.text+0xb8ba): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::push_back(char)'
dd_real.cpp:(.text+0xb8d8): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::push_back(char)'
dd_real.cpp:(.text+0xb8f1): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::push_back(char)'
dd_real.cpp:(.text+0xb926): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::reserve(unsigned long)'
dd_real.cpp:(.text+0xb988): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::append(char const*)'
dd_real.cpp:(.text+0xb9cf): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::reserve(unsigned long)'
dd_real.cpp:(.text+0xba10): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::append(unsigned long, char)'
dd_real.cpp:(.text+0xba1f): undefined reference to `std::__throw_out_of_range(char const*)'
dd_real.cpp:(.text+0xba2a): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string()'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(dd_real.o): In function `dd_real::write(char*, int, int, bool, bool) const':
dd_real.cpp:(.text+0xbaae): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::_Rep::_S_empty_rep_storage'
dd_real.cpp:(.text+0xbae8): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::_Rep::_M_destroy(std::allocator<char> const&)'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(dd_real.o): In function `operator<<(std::basic_ostream<char, std::char_traits<char> >&, dd_real const&)':
dd_real.cpp:(.text+0xbb4e): undefined reference to `std::basic_ios<char, std::char_traits<char> >::widen(char) const'
dd_real.cpp:(.text+0xbbb3): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::__ostream_insert<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*, long)'
dd_real.cpp:(.text+0xbbc6): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::_Rep::_S_empty_rep_storage'
dd_real.cpp:(.text+0xbc12): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::_Rep::_M_destroy(std::allocator<char> const&)'
dd_real.cpp:(.text+0xbc2a): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string()'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(dd_real.o): In function `floor(dd_real const&)':
dd_real.cpp:(.text._Z5floorRK7dd_real[floor(dd_real const&)]+0xd): undefined reference to `floor'
dd_real.cpp:(.text._Z5floorRK7dd_real[floor(dd_real const&)]+0x43): undefined reference to `floor'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(dd_real.o):(.eh_frame+0x13): undefined reference to `__gxx_personality_v0'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(dd_const.o): In function `global constructors keyed to _ZN7dd_real4_2piE':
dd_const.cpp:(.text+0xa): undefined reference to `std::ios_base::Init::Init()'
dd_const.cpp:(.text+0x19): undefined reference to `std::ios_base::Init::~Init()'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(dd_const.o):(.eh_frame+0x12): undefined reference to `__gxx_personality_v0'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(qd_real.o): In function `global constructors keyed to _ZN7qd_real5errorEPKc':
qd_real.cpp:(.text+0xa): undefined reference to `std::ios_base::Init::Init()'
qd_real.cpp:(.text+0x19): undefined reference to `std::ios_base::Init::~Init()'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(qd_real.o): In function `ceil(qd_real const&)':
qd_real.cpp:(.text+0x8ca1): undefined reference to `ceil'
qd_real.cpp:(.text+0x8cde): undefined reference to `ceil'
qd_real.cpp:(.text+0x8df1): undefined reference to `ceil'
qd_real.cpp:(.text+0x8ec7): undefined reference to `ceil'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(qd_real.o): In function `nint(qd_real const&)':
qd_real.cpp:(.text+0x8f0b): undefined reference to `floor'
qd_real.cpp:(.text+0x907d): undefined reference to `floor'
qd_real.cpp:(.text+0x90b1): undefined reference to `floor'
qd_real.cpp:(.text+0x91e5): undefined reference to `floor'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(qd_real.o): In function `qd_real::dump_bits(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::basic_ostream<char, std::char_traits<char> >&) const':
qd_real.cpp:(.text+0x9315): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::__ostream_insert<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*, long)'
qd_real.cpp:(.text+0x935d): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::__ostream_insert<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*, long)'
qd_real.cpp:(.text+0x9395): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::__ostream_insert<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*, long)'
qd_real.cpp:(.text+0x9425): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::put(char)'
qd_real.cpp:(.text+0x942d): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::flush()'
qd_real.cpp:(.text+0x94df): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::put(char)'
qd_real.cpp:(.text+0x94e7): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::flush()'
qd_real.cpp:(.text+0x9520): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::__ostream_insert<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*, long)'
qd_real.cpp:(.text+0x9532): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::__ostream_insert<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*, long)'
qd_real.cpp:(.text+0x953c): undefined reference to `std::__throw_bad_cast()'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(qd_real.o): In function `qd_real::error(char const*)':
qd_real.cpp:(.text+0x9562): undefined reference to `std::cerr'
qd_real.cpp:(.text+0x9567): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::__ostream_insert<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*, long)'
qd_real.cpp:(.text+0x957a): undefined reference to `std::cerr'
qd_real.cpp:(.text+0x957f): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::__ostream_insert<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*, long)'
qd_real.cpp:(.text+0x9586): undefined reference to `std::cerr'
qd_real.cpp:(.text+0x9591): undefined reference to `std::cerr'
qd_real.cpp:(.text+0x9608): undefined reference to `std::cerr'
qd_real.cpp:(.text+0x9610): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::put(char)'
qd_real.cpp:(.text+0x9618): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::flush()'
qd_real.cpp:(.text+0x9631): undefined reference to `std::__throw_bad_cast()'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(qd_real.o): In function `floor(qd_real const&)':
qd_real.cpp:(.text+0x9651): undefined reference to `floor'
qd_real.cpp:(.text+0x968e): undefined reference to `floor'
qd_real.cpp:(.text+0x97a1): undefined reference to `floor'
qd_real.cpp:(.text+0x9877): undefined reference to `floor'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(qd_real.o): In function `qd_real::dump(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::basic_ostream<char, std::char_traits<char> >&) const':
qd_real.cpp:(.text+0x9907): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::__ostream_insert<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*, long)'
qd_real.cpp:(.text+0x9934): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::basic_ostream<char, std::char_traits<char> >::_M_insert<double>(double)'
qd_real.cpp:(.text+0x9949): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::__ostream_insert<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*, long)'
qd_real.cpp:(.text+0x9967): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::basic_ostream<char, std::char_traits<char> >::_M_insert<double>(double)'
qd_real.cpp:(.text+0x997c): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::__ostream_insert<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*, long)'
qd_real.cpp:(.text+0x9a0b): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::put(char)'
qd_real.cpp:(.text+0x9a13): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::flush()'
qd_real.cpp:(.text+0x9a48): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::__ostream_insert<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*, long)'
qd_real.cpp:(.text+0x9a7b): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::basic_ostream<char, std::char_traits<char> >::_M_insert<double>(double)'
qd_real.cpp:(.text+0x9a90): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::__ostream_insert<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*, long)'
qd_real.cpp:(.text+0x9aae): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::basic_ostream<char, std::char_traits<char> >::_M_insert<double>(double)'
qd_real.cpp:(.text+0x9ac3): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::__ostream_insert<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*, long)'
qd_real.cpp:(.text+0x9b4f): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::put(char)'
qd_real.cpp:(.text+0x9b57): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::flush()'
qd_real.cpp:(.text+0x9bbd): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::__ostream_insert<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*, long)'
qd_real.cpp:(.text+0x9bcf): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::__ostream_insert<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*, long)'
qd_real.cpp:(.text+0x9bd9): undefined reference to `std::__throw_bad_cast()'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(qd_real.o): In function `polyroot(qd_real const*, int, qd_real const&, int, double)':
qd_real.cpp:(.text+0xbc40): undefined reference to `operator new[](unsigned long)'
qd_real.cpp:(.text+0xbdf4): undefined reference to `operator delete[](void*)'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(qd_real.o): In function `operator>>(std::basic_istream<char, std::char_traits<char> >&, qd_real&)':
qd_real.cpp:(.text+0xca60): undefined reference to `std::basic_istream<char, std::char_traits<char> >& std::operator>><char, std::char_traits<char> >(std::basic_istream<char, std::char_traits<char> >&, char*)'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(qd_real.o): In function `qd_real::to_digits(char*, int&, int) const':
qd_real.cpp:(.text+0xcbcd): undefined reference to `log10'
qd_real.cpp:(.text+0xcbd2): undefined reference to `floor'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(qd_real.o): In function `exp(qd_real const&)':
qd_real.cpp:(.text+0xd5b3): undefined reference to `floor'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(qd_real.o): In function `log(qd_real const&)':
qd_real.cpp:(.text+0x10019): undefined reference to `log'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(qd_real.o): In function `qd_real::to_string(int, int, std::_Ios_Fmtflags, bool, bool, char) const':
qd_real.cpp:(.text+0x10db9): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::_Rep::_S_empty_rep_storage'
qd_real.cpp:(.text+0x10e16): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::reserve(unsigned long)'
qd_real.cpp:(.text+0x10f0a): undefined reference to `operator new[](unsigned long)'
qd_real.cpp:(.text+0x10f65): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::reserve(unsigned long)'
qd_real.cpp:(.text+0x10fa7): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::push_back(char)'
qd_real.cpp:(.text+0x10fdf): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::reserve(unsigned long)'
qd_real.cpp:(.text+0x11018): undefined reference to `operator delete[](void*)'
qd_real.cpp:(.text+0x11054): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::reserve(unsigned long)'
qd_real.cpp:(.text+0x110c2): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::append(char const*, unsigned long)'
qd_real.cpp:(.text+0x11107): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::_M_replace_aux(unsigned long, unsigned long, unsigned long, char)'
qd_real.cpp:(.text+0x11128): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::_M_replace_aux(unsigned long, unsigned long, unsigned long, char)'
qd_real.cpp:(.text+0x11154): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::append(unsigned long, char)'
qd_real.cpp:(.text+0x11177): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::push_back(char)'
qd_real.cpp:(.text+0x111c5): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::assign(char const*, unsigned long)'
qd_real.cpp:(.text+0x111f8): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::reserve(unsigned long)'
qd_real.cpp:(.text+0x1129a): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::push_back(char)'
qd_real.cpp:(.text+0x112b3): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::push_back(char)'
qd_real.cpp:(.text+0x112c5): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::append(unsigned long, char)'
qd_real.cpp:(.text+0x112d9): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::push_back(char)'
qd_real.cpp:(.text+0x1130f): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::push_back(char)'
qd_real.cpp:(.text+0x11328): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::push_back(char)'
qd_real.cpp:(.text+0x1133a): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::append(unsigned long, char)'
qd_real.cpp:(.text+0x11350): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::push_back(char)'
qd_real.cpp:(.text+0x11369): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::push_back(char)'
qd_real.cpp:(.text+0x11396): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::reserve(unsigned long)'
qd_real.cpp:(.text+0x1141d): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::append(char const*)'
qd_real.cpp:(.text+0x11467): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::reserve(unsigned long)'
qd_real.cpp:(.text+0x114a8): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::append(unsigned long, char)'
qd_real.cpp:(.text+0x114b7): undefined reference to `std::__throw_out_of_range(char const*)'
qd_real.cpp:(.text+0x114c2): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string()'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(qd_real.o): In function `qd_real::write(char*, int, int, bool, bool) const':
qd_real.cpp:(.text+0x1153e): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::_Rep::_S_empty_rep_storage'
qd_real.cpp:(.text+0x11578): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::_Rep::_M_destroy(std::allocator<char> const&)'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(qd_real.o): In function `operator<<(std::basic_ostream<char, std::char_traits<char> >&, qd_real const&)':
qd_real.cpp:(.text+0x115de): undefined reference to `std::basic_ios<char, std::char_traits<char> >::widen(char) const'
qd_real.cpp:(.text+0x11643): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::__ostream_insert<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*, long)'
qd_real.cpp:(.text+0x11656): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::_Rep::_S_empty_rep_storage'
qd_real.cpp:(.text+0x116a2): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::_Rep::_M_destroy(std::allocator<char> const&)'
qd_real.cpp:(.text+0x116ba): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string()'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(qd_real.o): In function `sqrt(qd_real const&)':
qd_real.cpp:(.text+0x120a5): undefined reference to `sqrt'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(qd_real.o): In function `nroot(qd_real const&, int)':
qd_real.cpp:(.text+0x13233): undefined reference to `pow'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(qd_real.o): In function `sincos(qd_real const&, qd_real&, qd_real&)':
qd_real.cpp:(.text+0x14a24): undefined reference to `floor'
qd_real.cpp:(.text+0x14b05): undefined reference to `floor'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(qd_real.o): In function `atan2(qd_real const&, qd_real const&)':
qd_real.cpp:(.text+0x15bc8): undefined reference to `atan2'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(qd_real.o): In function `cos(qd_real const&)':
qd_real.cpp:(.text+0x166c1): undefined reference to `floor'
qd_real.cpp:(.text+0x1676c): undefined reference to `floor'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(qd_real.o): In function `sin(qd_real const&)':
qd_real.cpp:(.text+0x16fa9): undefined reference to `floor'
qd_real.cpp:(.text+0x17053): undefined reference to `floor'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(qd_real.o): In function `qd::nint(double)':
qd_real.cpp:(.text._ZN2qd4nintEd[qd::nint(double)]+0xa): undefined reference to `floor'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(qd_real.o):qd_real.cpp:(.text._ZN2qd4nintEd[qd::nint(double)]+0x3a): more undefined references to `floor' follow
/local/peter/tt/masters/PSI/qd/lib//libqd.a(qd_real.o):(.eh_frame+0x13): undefined reference to `__gxx_personality_v0'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(qd_const.o): In function `global constructors keyed to _ZN7qd_real4_2piE':
qd_const.cpp:(.text+0xa): undefined reference to `std::ios_base::Init::Init()'
qd_const.cpp:(.text+0x19): undefined reference to `std::ios_base::Init::~Init()'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(qd_const.o):(.eh_frame+0x12): undefined reference to `__gxx_personality_v0'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(util.o): In function `append_expn(std::basic_string<char, std::char_traits<char>, std::allocator<char> >&, int)':
util.cpp:(.text+0x52): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::reserve(unsigned long)'
util.cpp:(.text+0xbb): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::reserve(unsigned long)'
util.cpp:(.text+0xfc): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::reserve(unsigned long)'
util.cpp:(.text+0x175): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::reserve(unsigned long)'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(util.o):(.eh_frame+0x12): undefined reference to `__gxx_personality_v0'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(bits.o): In function `global constructors keyed to _Z15get_double_expnd':
bits.cpp:(.text+0xa): undefined reference to `std::ios_base::Init::Init()'
bits.cpp:(.text+0x19): undefined reference to `std::ios_base::Init::~Init()'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(bits.o): In function `print_double_info(std::basic_ostream<char, std::char_traits<char> >&, double)':
bits.cpp:(.text+0x151): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::basic_ostream<char, std::char_traits<char> >::_M_insert<double>(double)'
bits.cpp:(.text+0x166): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::__ostream_insert<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*, long)'
bits.cpp:(.text+0x19a): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::__ostream_insert<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*, long)'
bits.cpp:(.text+0x217): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(int)'
bits.cpp:(.text+0x229): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::__ostream_insert<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*, long)'
bits.cpp:(.text+0x256): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::__ostream_insert<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*, long)'
bits.cpp:(.text+0x295): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::__ostream_insert<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*, long)'
bits.cpp:(.text+0x2c4): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::__ostream_insert<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*, long)'
/local/peter/tt/masters/PSI/qd/lib//libqd.a(bits.o):(.eh_frame+0x12): undefined reference to `__gxx_personality_v0'
/local/peter/tt/masters/PSI/Fortran-0.001-0.45//libode128.a(zvode.o): In function `zvode_':
zvode.f:(.text+0x1cb): undefined reference to `for_cpystr'
zvode.f:(.text+0x26f): undefined reference to `for_cpystr'
zvode.f:(.text+0x30c): undefined reference to `for_cpystr'
zvode.f:(.text+0x3a0): undefined reference to `for_cpystr'
zvode.f:(.text+0x45f): undefined reference to `for_cpystr'
/local/peter/tt/masters/PSI/Fortran-0.001-0.45//libode128.a(zvode.o):zvode.f:(.text+0x4f4): more undefined references to `for_cpystr' follow
collect2: ld returned 1 exit status

```


I shuffled the order of the libraries in different ways, without success.

---

### Post by Bachstelze on 2011-08-24
I was wrong, read what MadCow said above. You need to put the libraries at the end, not the beginning.

---

