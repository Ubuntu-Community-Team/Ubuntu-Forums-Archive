---
title: "undefined reference when compiling sim-profile.c in Simplescalar tool"
date: 2009-09-02
forum: Programming Talk
---

### Post by green86 on 2009-09-02
Hi.. I installed SimpleScalar simulator as per **http://www.kth.se/student/program-kurser/kurshemsidor/kurser-ict/ecs/IS2202/VT09-1/2.7064?l=en_UK"** installation instructions in my Ubuntu 8.04 machine. Everything went fine but the sim-profile.c program which is the profiling simulator program doesn't compile! 

When I do the following :

root@surya-laptop:/home/surya/simplescalar/simplesim-3.0# **../bin/sslittle-na-sstrix-gcc sim-profile.c**

I get the following errors!

/tmp/ccTr2F8a1.o: In function `sim_reg_options':
sim-profile.c:106: undefined reference to `opt_reg_header'
sim-profile.c:106: undefined reference to `opt_reg_uint'
sim-profile.c:106: undefined reference to `opt_reg_flag'
sim-profile.c:106: undefined reference to `opt_reg_flag'
sim-profile.c:106: undefined reference to `opt_reg_flag'
sim-profile.c:106: undefined reference to `opt_reg_flag'
sim-profile.c:106: undefined reference to `opt_reg_flag'
/tmp/ccTr2F8a1.o:sim-profile.c:106: more undefined references to `opt_reg_flag' follow
/tmp/ccTr2F8a1.o: In function `sim_reg_options':
sim-profile.c:106: undefined reference to `opt_reg_string_list'
/tmp/ccTr2F8a1.o: In function `bind_to_seg':
sim-profile.c:255: undefined reference to `ld_data_base'
sim-profile.c:255: relocation truncated to fit: GPREL ld_data_base
sim-profile.c:255: undefined reference to `ld_data_base'
sim-profile.c:255: relocation truncated to fit: GPREL ld_data_base
sim-profile.c:255: undefined reference to `ld_data_size'
sim-profile.c:255: relocation truncated to fit: GPREL ld_data_size
sim-profile.c:255: undefined reference to `ld_data_base'
sim-profile.c:255: relocation truncated to fit: GPREL ld_data_base
sim-profile.c:255: undefined reference to `ld_data_size'
sim-profile.c:255: relocation truncated to fit: GPREL ld_data_size
sim-profile.c:255: undefined reference to `ld_brk_point'
sim-profile.c:255: relocation truncated to fit: GPREL ld_brk_point
sim-profile.c:255: undefined reference to `ld_stack_base'
sim-profile.c:255: relocation truncated to fit: GPREL ld_stack_base
sim-profile.c:255: undefined reference to `ld_stack_base'
sim-profile.c:255: relocation truncated to fit: GPREL ld_stack_base
sim-profile.c:255: undefined reference to `ld_text_base'
sim-profile.c:255: relocation truncated to fit: GPREL ld_text_base
sim-profile.c:255: undefined reference to `ld_text_base'
sim-profile.c:255: relocation truncated to fit: GPREL ld_text_base
sim-profile.c:255: undefined reference to `ld_text_size'
sim-profile.c:255: relocation truncated to fit: GPREL ld_text_size
sim-profile.c:255: undefined reference to `_panic'
/tmp/ccTr2F8a1.o: In function `sim_reg_stats':
sim-profile.c:298: undefined reference to `sim_num_insn'
sim-profile.c:298: relocation truncated to fit: GPREL sim_num_insn
sim-profile.c:298: undefined reference to `sim_num_insn'
sim-profile.c:298: relocation truncated to fit: GPREL sim_num_insn
sim-profile.c:298: undefined reference to `stat_reg_sqword'
sim-profile.c:298: undefined reference to `stat_reg_sqword'
sim-profile.c:298: undefined reference to `sim_elapsed_time'
sim-profile.c:298: relocation truncated to fit: GPREL sim_elapsed_time
sim-profile.c:298: undefined reference to `stat_reg_int'
sim-profile.c:298: undefined reference to `stat_reg_formula'
sim-profile.c:298: undefined reference to `stat_reg_dist'
sim-profile.c:298: undefined reference to `md_op2name'
sim-profile.c:298: undefined reference to `md_op2name'
sim-profile.c:298: undefined reference to `md_op2format'
sim-profile.c:298: undefined reference to `md_op2format'
sim-profile.c:298: undefined reference to `mystrdup'
sim-profile.c:298: undefined reference to `stat_reg_dist'
sim-profile.c:298: undefined reference to `stat_reg_dist'
sim-profile.c:298: undefined reference to `md_amode_str'
sim-profile.c:298: undefined reference to `md_amode_str'
sim-profile.c:298: undefined reference to `stat_reg_dist'
sim-profile.c:298: undefined reference to `stat_reg_dist'
sim-profile.c:298: undefined reference to `sym_ntextsyms'
sim-profile.c:298: relocation truncated to fit: GPREL sym_ntextsyms
sim-profile.c:298: undefined reference to `ld_prog_fname'
sim-profile.c:298: relocation truncated to fit: GPREL ld_prog_fname
sim-profile.c:298: undefined reference to `sym_loadsyms'
sim-profile.c:298: undefined reference to `sym_ntextsyms'
sim-profile.c:298: relocation truncated to fit: GPREL sym_ntextsyms
sim-profile.c:298: undefined reference to `sym_ntextsyms'
sim-profile.c:298: relocation truncated to fit: GPREL sym_ntextsyms
sim-profile.c:298: undefined reference to `sym_textsyms'
sim-profile.c:298: relocation truncated to fit: GPREL sym_textsyms
sim-profile.c:298: undefined reference to `sym_ntextsyms'
sim-profile.c:298: relocation truncated to fit: GPREL sym_ntextsyms
sim-profile.c:298: undefined reference to `stat_reg_dist'
sim-profile.c:298: undefined reference to `sym_ndatasyms'
sim-profile.c:298: relocation truncated to fit: GPREL sym_ndatasyms
sim-profile.c:298: undefined reference to `ld_prog_fname'
sim-profile.c:298: relocation truncated to fit: GPREL ld_prog_fname
sim-profile.c:298: undefined reference to `sym_loadsyms'
sim-profile.c:298: undefined reference to `sym_ndatasyms'
sim-profile.c:298: relocation truncated to fit: GPREL sym_ndatasyms
sim-profile.c:298: undefined reference to `sym_ndatasyms'
sim-profile.c:298: relocation truncated to fit: GPREL sym_ndatasyms
sim-profile.c:298: undefined reference to `sym_datasyms'
sim-profile.c:298: relocation truncated to fit: GPREL sym_datasyms
sim-profile.c:298: undefined reference to `sym_ndatasyms'
sim-profile.c:298: relocation truncated to fit: GPREL sym_ndatasyms
sim-profile.c:298: undefined reference to `stat_reg_dist'
sim-profile.c:298: undefined reference to `stat_reg_sdist'
sim-profile.c:298: undefined reference to `stat_find_stat'
sim-profile.c:298: undefined reference to `_fatal'
sim-profile.c:298: undefined reference to `_fatal'
sim-profile.c:298: undefined reference to `_panic'
sim-profile.c:298: undefined reference to `stat_reg_sdist'
sim-profile.c:298: undefined reference to `ld_reg_stats'
sim-profile.c:298: undefined reference to `mem_reg_stats'
/tmp/ccTr2F8a1.o: In function `sim_init':
sim-profile.c:495: undefined reference to `regs_init'
sim-profile.c:495: undefined reference to `mem_create'
sim-profile.c:495: undefined reference to `mem_init'
/tmp/ccTr2F8a1.o: In function `profile_mstate_obj':
sim-profile.c:512: undefined reference to `sim_print_stats'
/tmp/ccTr2F8a1.o: In function `sim_load_prog':
sim-profile.c:525: undefined reference to `ld_load_prog'
sim-profile.c:525: undefined reference to `md_reg_obj'
sim-profile.c:525: undefined reference to `md_reg_obj'
sim-profile.c:525: undefined reference to `dlite_mem_obj'
sim-profile.c:525: undefined reference to `dlite_mem_obj'
sim-profile.c:525: undefined reference to `dlite_init'
/tmp/ccTr2F8a1.o: In function `sim_main':
sim-profile.c:642: undefined reference to `dlite_check'
sim-profile.c:642: relocation truncated to fit: GPREL dlite_check
sim-profile.c:642: undefined reference to `dlite_active'
sim-profile.c:642: relocation truncated to fit: GPREL dlite_active
sim-profile.c:642: undefined reference to `__check_break'
sim-profile.c:642: undefined reference to `sim_num_insn'
sim-profile.c:642: relocation truncated to fit: GPREL sim_num_insn
sim-profile.c:642: undefined reference to `dlite_main'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `verbose'
sim-profile.c:642: relocation truncated to fit: GPREL verbose
sim-profile.c:642: undefined reference to `sim_num_insn'
sim-profile.c:642: relocation truncated to fit: GPREL sim_num_insn
sim-profile.c:642: undefined reference to `myfprintf'
sim-profile.c:642: undefined reference to `md_print_insn'
sim-profile.c:642: undefined reference to `sim_num_insn'
sim-profile.c:642: relocation truncated to fit: GPREL sim_num_insn
sim-profile.c:642: undefined reference to `sim_num_insn'
sim-profile.c:642: relocation truncated to fit: GPREL sim_num_insn
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
/tmp/ccTr2F8a1.o:sim-profile.c:642: more undefined references to `mem_translate' follow
/tmp/ccTr2F8a1.o: In function `sim_main':
sim-profile.c:642: undefined reference to `md_lr_masks'
sim-profile.c:642: undefined reference to `md_lr_masks'
sim-profile.c:642: undefined reference to `md_lr_masks'
sim-profile.c:642: undefined reference to `md_lr_masks'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `md_lr_masks'
sim-profile.c:642: undefined reference to `md_lr_masks'
sim-profile.c:642: undefined reference to `md_lr_masks'
sim-profile.c:642: undefined reference to `md_lr_masks'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `md_lr_masks'
sim-profile.c:642: undefined reference to `md_lr_masks'
sim-profile.c:642: undefined reference to `md_lr_masks'
sim-profile.c:642: undefined reference to `md_lr_masks'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `md_lr_masks'
sim-profile.c:642: undefined reference to `md_lr_masks'
sim-profile.c:642: undefined reference to `md_lr_masks'
sim-profile.c:642: undefined reference to `md_lr_masks'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
/tmp/ccTr2F8a1.o:sim-profile.c:642: more undefined references to `mem_translate' follow
/tmp/ccTr2F8a1.o: In function `sim_main':
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `extractl'
sim-profile.c:642: undefined reference to `extractl'
sim-profile.c:642: undefined reference to `extractl'
sim-profile.c:642: undefined reference to `extractl'
sim-profile.c:642: undefined reference to `mem_access'
sim-profile.c:642: undefined reference to `mem_access'
sim-profile.c:642: undefined reference to `sys_syscall'
sim-profile.c:642: undefined reference to `_panic'
sim-profile.c:642: undefined reference to `md_op2flags'
sim-profile.c:642: undefined reference to `md_op2flags'
sim-profile.c:642: undefined reference to `md_op2flags'
sim-profile.c:642: undefined reference to `md_op2flags'
sim-profile.c:642: undefined reference to `md_op2flags'
/tmp/ccTr2F8a1.o:sim-profile.c:642: more undefined references to `md_op2flags' follow
/tmp/ccTr2F8a1.o: In function `sim_main':
sim-profile.c:642: undefined reference to `_panic'
sim-profile.c:642: undefined reference to `stat_add_sample'
sim-profile.c:642: undefined reference to `stat_add_sample'
sim-profile.c:642: undefined reference to `_panic'
sim-profile.c:642: undefined reference to `stat_add_sample'
sim-profile.c:642: undefined reference to `md_op2flags'
sim-profile.c:642: undefined reference to `md_op2flags'
sim-profile.c:642: undefined reference to `md_op2flags'
sim-profile.c:642: undefined reference to `md_op2flags'
sim-profile.c:642: undefined reference to `_panic'
sim-profile.c:642: undefined reference to `stat_add_sample'
sim-profile.c:642: undefined reference to `stat_add_sample'
sim-profile.c:642: undefined reference to `sym_bind_addr'
sim-profile.c:642: undefined reference to `sym_ntextsyms'
sim-profile.c:642: relocation truncated to fit: GPREL sym_ntextsyms
sim-profile.c:642: undefined reference to `_panic'
sim-profile.c:642: undefined reference to `stat_add_sample'
sim-profile.c:642: undefined reference to `sym_bind_addr'
sim-profile.c:642: undefined reference to `sym_ndatasyms'
sim-profile.c:642: relocation truncated to fit: GPREL sym_ndatasyms
sim-profile.c:642: undefined reference to `_panic'
sim-profile.c:642: undefined reference to `stat_add_sample'
sim-profile.c:642: undefined reference to `stat_add_sample'
sim-profile.c:642: undefined reference to `_panic'
sim-profile.c:642: undefined reference to `stat_add_samples'
sim-profile.c:642: undefined reference to `dlite_check'
sim-profile.c:642: relocation truncated to fit: GPREL dlite_check
sim-profile.c:642: undefined reference to `dlite_active'
sim-profile.c:642: relocation truncated to fit: GPREL dlite_active
sim-profile.c:642: undefined reference to `sim_num_insn'
sim-profile.c:642: relocation truncated to fit: GPREL sim_num_insn
sim-profile.c:642: undefined reference to `sim_num_insn'
sim-profile.c:642: relocation truncated to fit: GPREL sim_num_insn
sim-profile.c:642: undefined reference to `__check_break'
sim-profile.c:642: undefined reference to `sim_num_insn'
sim-profile.c:642: relocation truncated to fit: GPREL sim_num_insn
sim-profile.c:642: undefined reference to `dlite_main'
sim-profile.c:642: undefined reference to `sim_num_insn'
sim-profile.c:642: relocation truncated to fit: GPREL sim_num_insn
sim-profile.c:642: undefined reference to `sim_num_insn'
sim-profile.c:642: relocation truncated to fit: GPREL sim_num_insn
sim-profile.c:642: undefined reference to `sim_num_insn'
sim-profile.c:642: relocation truncated to fit: GPREL sim_num_insn
sim-profile.c:642: undefined reference to `sim_num_insn'
sim-profile.c:642: relocation truncated to fit: GPREL sim_num_insn
/home/surya/simplescalar/sslittle-na-sstrix/lib/libc.a(fmain.o): In function `main':
fmain.c:118: undefined reference to `MAIN__'

It clearly cannot link to the header files included in the program. But I don't know how to rectify this!! Please help me.. 

The **Makefile** has the following:

CC = gcc
OFLAGS = -O -g -Wall
MFLAGS = `./sysprobe -flags`
MLIBS  = `./sysprobe -libs` -lm
ENDIAN = `./sysprobe -s`
MAKE = make
AR = ar qcv
AROPT =
RANLIB = ranlib
RM = rm -f
RMDIR = rm -f
LN = ln -s
LNDIR = ln -s
DIFF = diff
OEXT = o
LEXT = a
EEXT =
CS = ;
X=/

If I run the command 

**./sysprobe -libs**

I get a **space** as output! Is that got to do something with the problem??
Kindly share your thoughts....

---

### Post by Arndt on 2009-09-02
> **green86 said:**
> Hi.. I installed SimpleScalar simulator as per **http://www.kth.se/student/program-kurser/kurshemsidor/kurser-ict/ecs/IS2202/VT09-1/2.7064?l=en_UK"** installation instructions in my Ubuntu 8.04 machine. Everything went fine but the sim-profile.c program which is the profiling simulator program doesn't compile! 

When I do the following :

root@surya-laptop:/home/surya/simplescalar/simplesim-3.0# **../bin/sslittle-na-sstrix-gcc sim-profile.c**

I get the following errors!

/tmp/ccTr2F8a1.o: In function `sim_reg_options':
sim-profile.c:106: undefined reference to `opt_reg_header'
sim-profile.c:106: undefined reference to `opt_reg_uint'
sim-profile.c:106: undefined reference to `opt_reg_flag'
sim-profile.c:106: undefined reference to `opt_reg_flag'
sim-profile.c:106: undefined reference to `opt_reg_flag'
sim-profile.c:106: undefined reference to `opt_reg_flag'
sim-profile.c:106: undefined reference to `opt_reg_flag'
/tmp/ccTr2F8a1.o:sim-profile.c:106: more undefined references to `opt_reg_flag' follow
/tmp/ccTr2F8a1.o: In function `sim_reg_options':
sim-profile.c:106: undefined reference to `opt_reg_string_list'
/tmp/ccTr2F8a1.o: In function `bind_to_seg':
sim-profile.c:255: undefined reference to `ld_data_base'
sim-profile.c:255: relocation truncated to fit: GPREL ld_data_base
sim-profile.c:255: undefined reference to `ld_data_base'
sim-profile.c:255: relocation truncated to fit: GPREL ld_data_base
sim-profile.c:255: undefined reference to `ld_data_size'
sim-profile.c:255: relocation truncated to fit: GPREL ld_data_size
sim-profile.c:255: undefined reference to `ld_data_base'
sim-profile.c:255: relocation truncated to fit: GPREL ld_data_base
sim-profile.c:255: undefined reference to `ld_data_size'
sim-profile.c:255: relocation truncated to fit: GPREL ld_data_size
sim-profile.c:255: undefined reference to `ld_brk_point'
sim-profile.c:255: relocation truncated to fit: GPREL ld_brk_point
sim-profile.c:255: undefined reference to `ld_stack_base'
sim-profile.c:255: relocation truncated to fit: GPREL ld_stack_base
sim-profile.c:255: undefined reference to `ld_stack_base'
sim-profile.c:255: relocation truncated to fit: GPREL ld_stack_base
sim-profile.c:255: undefined reference to `ld_text_base'
sim-profile.c:255: relocation truncated to fit: GPREL ld_text_base
sim-profile.c:255: undefined reference to `ld_text_base'
sim-profile.c:255: relocation truncated to fit: GPREL ld_text_base
sim-profile.c:255: undefined reference to `ld_text_size'
sim-profile.c:255: relocation truncated to fit: GPREL ld_text_size
sim-profile.c:255: undefined reference to `_panic'
/tmp/ccTr2F8a1.o: In function `sim_reg_stats':
sim-profile.c:298: undefined reference to `sim_num_insn'
sim-profile.c:298: relocation truncated to fit: GPREL sim_num_insn
sim-profile.c:298: undefined reference to `sim_num_insn'
sim-profile.c:298: relocation truncated to fit: GPREL sim_num_insn
sim-profile.c:298: undefined reference to `stat_reg_sqword'
sim-profile.c:298: undefined reference to `stat_reg_sqword'
sim-profile.c:298: undefined reference to `sim_elapsed_time'
sim-profile.c:298: relocation truncated to fit: GPREL sim_elapsed_time
sim-profile.c:298: undefined reference to `stat_reg_int'
sim-profile.c:298: undefined reference to `stat_reg_formula'
sim-profile.c:298: undefined reference to `stat_reg_dist'
sim-profile.c:298: undefined reference to `md_op2name'
sim-profile.c:298: undefined reference to `md_op2name'
sim-profile.c:298: undefined reference to `md_op2format'
sim-profile.c:298: undefined reference to `md_op2format'
sim-profile.c:298: undefined reference to `mystrdup'
sim-profile.c:298: undefined reference to `stat_reg_dist'
sim-profile.c:298: undefined reference to `stat_reg_dist'
sim-profile.c:298: undefined reference to `md_amode_str'
sim-profile.c:298: undefined reference to `md_amode_str'
sim-profile.c:298: undefined reference to `stat_reg_dist'
sim-profile.c:298: undefined reference to `stat_reg_dist'
sim-profile.c:298: undefined reference to `sym_ntextsyms'
sim-profile.c:298: relocation truncated to fit: GPREL sym_ntextsyms
sim-profile.c:298: undefined reference to `ld_prog_fname'
sim-profile.c:298: relocation truncated to fit: GPREL ld_prog_fname
sim-profile.c:298: undefined reference to `sym_loadsyms'
sim-profile.c:298: undefined reference to `sym_ntextsyms'
sim-profile.c:298: relocation truncated to fit: GPREL sym_ntextsyms
sim-profile.c:298: undefined reference to `sym_ntextsyms'
sim-profile.c:298: relocation truncated to fit: GPREL sym_ntextsyms
sim-profile.c:298: undefined reference to `sym_textsyms'
sim-profile.c:298: relocation truncated to fit: GPREL sym_textsyms
sim-profile.c:298: undefined reference to `sym_ntextsyms'
sim-profile.c:298: relocation truncated to fit: GPREL sym_ntextsyms
sim-profile.c:298: undefined reference to `stat_reg_dist'
sim-profile.c:298: undefined reference to `sym_ndatasyms'
sim-profile.c:298: relocation truncated to fit: GPREL sym_ndatasyms
sim-profile.c:298: undefined reference to `ld_prog_fname'
sim-profile.c:298: relocation truncated to fit: GPREL ld_prog_fname
sim-profile.c:298: undefined reference to `sym_loadsyms'
sim-profile.c:298: undefined reference to `sym_ndatasyms'
sim-profile.c:298: relocation truncated to fit: GPREL sym_ndatasyms
sim-profile.c:298: undefined reference to `sym_ndatasyms'
sim-profile.c:298: relocation truncated to fit: GPREL sym_ndatasyms
sim-profile.c:298: undefined reference to `sym_datasyms'
sim-profile.c:298: relocation truncated to fit: GPREL sym_datasyms
sim-profile.c:298: undefined reference to `sym_ndatasyms'
sim-profile.c:298: relocation truncated to fit: GPREL sym_ndatasyms
sim-profile.c:298: undefined reference to `stat_reg_dist'
sim-profile.c:298: undefined reference to `stat_reg_sdist'
sim-profile.c:298: undefined reference to `stat_find_stat'
sim-profile.c:298: undefined reference to `_fatal'
sim-profile.c:298: undefined reference to `_fatal'
sim-profile.c:298: undefined reference to `_panic'
sim-profile.c:298: undefined reference to `stat_reg_sdist'
sim-profile.c:298: undefined reference to `ld_reg_stats'
sim-profile.c:298: undefined reference to `mem_reg_stats'
/tmp/ccTr2F8a1.o: In function `sim_init':
sim-profile.c:495: undefined reference to `regs_init'
sim-profile.c:495: undefined reference to `mem_create'
sim-profile.c:495: undefined reference to `mem_init'
/tmp/ccTr2F8a1.o: In function `profile_mstate_obj':
sim-profile.c:512: undefined reference to `sim_print_stats'
/tmp/ccTr2F8a1.o: In function `sim_load_prog':
sim-profile.c:525: undefined reference to `ld_load_prog'
sim-profile.c:525: undefined reference to `md_reg_obj'
sim-profile.c:525: undefined reference to `md_reg_obj'
sim-profile.c:525: undefined reference to `dlite_mem_obj'
sim-profile.c:525: undefined reference to `dlite_mem_obj'
sim-profile.c:525: undefined reference to `dlite_init'
/tmp/ccTr2F8a1.o: In function `sim_main':
sim-profile.c:642: undefined reference to `dlite_check'
sim-profile.c:642: relocation truncated to fit: GPREL dlite_check
sim-profile.c:642: undefined reference to `dlite_active'
sim-profile.c:642: relocation truncated to fit: GPREL dlite_active
sim-profile.c:642: undefined reference to `__check_break'
sim-profile.c:642: undefined reference to `sim_num_insn'
sim-profile.c:642: relocation truncated to fit: GPREL sim_num_insn
sim-profile.c:642: undefined reference to `dlite_main'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `verbose'
sim-profile.c:642: relocation truncated to fit: GPREL verbose
sim-profile.c:642: undefined reference to `sim_num_insn'
sim-profile.c:642: relocation truncated to fit: GPREL sim_num_insn
sim-profile.c:642: undefined reference to `myfprintf'
sim-profile.c:642: undefined reference to `md_print_insn'
sim-profile.c:642: undefined reference to `sim_num_insn'
sim-profile.c:642: relocation truncated to fit: GPREL sim_num_insn
sim-profile.c:642: undefined reference to `sim_num_insn'
sim-profile.c:642: relocation truncated to fit: GPREL sim_num_insn
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
/tmp/ccTr2F8a1.o:sim-profile.c:642: more undefined references to `mem_translate' follow
/tmp/ccTr2F8a1.o: In function `sim_main':
sim-profile.c:642: undefined reference to `md_lr_masks'
sim-profile.c:642: undefined reference to `md_lr_masks'
sim-profile.c:642: undefined reference to `md_lr_masks'
sim-profile.c:642: undefined reference to `md_lr_masks'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `md_lr_masks'
sim-profile.c:642: undefined reference to `md_lr_masks'
sim-profile.c:642: undefined reference to `md_lr_masks'
sim-profile.c:642: undefined reference to `md_lr_masks'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `md_lr_masks'
sim-profile.c:642: undefined reference to `md_lr_masks'
sim-profile.c:642: undefined reference to `md_lr_masks'
sim-profile.c:642: undefined reference to `md_lr_masks'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `md_lr_masks'
sim-profile.c:642: undefined reference to `md_lr_masks'
sim-profile.c:642: undefined reference to `md_lr_masks'
sim-profile.c:642: undefined reference to `md_lr_masks'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
/tmp/ccTr2F8a1.o:sim-profile.c:642: more undefined references to `mem_translate' follow
/tmp/ccTr2F8a1.o: In function `sim_main':
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `mem_newpage'
sim-profile.c:642: undefined reference to `mem_translate'
sim-profile.c:642: undefined reference to `extractl'
sim-profile.c:642: undefined reference to `extractl'
sim-profile.c:642: undefined reference to `extractl'
sim-profile.c:642: undefined reference to `extractl'
sim-profile.c:642: undefined reference to `mem_access'
sim-profile.c:642: undefined reference to `mem_access'
sim-profile.c:642: undefined reference to `sys_syscall'
sim-profile.c:642: undefined reference to `_panic'
sim-profile.c:642: undefined reference to `md_op2flags'
sim-profile.c:642: undefined reference to `md_op2flags'
sim-profile.c:642: undefined reference to `md_op2flags'
sim-profile.c:642: undefined reference to `md_op2flags'
sim-profile.c:642: undefined reference to `md_op2flags'
/tmp/ccTr2F8a1.o:sim-profile.c:642: more undefined references to `md_op2flags' follow
/tmp/ccTr2F8a1.o: In function `sim_main':
sim-profile.c:642: undefined reference to `_panic'
sim-profile.c:642: undefined reference to `stat_add_sample'
sim-profile.c:642: undefined reference to `stat_add_sample'
sim-profile.c:642: undefined reference to `_panic'
sim-profile.c:642: undefined reference to `stat_add_sample'
sim-profile.c:642: undefined reference to `md_op2flags'
sim-profile.c:642: undefined reference to `md_op2flags'
sim-profile.c:642: undefined reference to `md_op2flags'
sim-profile.c:642: undefined reference to `md_op2flags'
sim-profile.c:642: undefined reference to `_panic'
sim-profile.c:642: undefined reference to `stat_add_sample'
sim-profile.c:642: undefined reference to `stat_add_sample'
sim-profile.c:642: undefined reference to `sym_bind_addr'
sim-profile.c:642: undefined reference to `sym_ntextsyms'
sim-profile.c:642: relocation truncated to fit: GPREL sym_ntextsyms
sim-profile.c:642: undefined reference to `_panic'
sim-profile.c:642: undefined reference to `stat_add_sample'
sim-profile.c:642: undefined reference to `sym_bind_addr'
sim-profile.c:642: undefined reference to `sym_ndatasyms'
sim-profile.c:642: relocation truncated to fit: GPREL sym_ndatasyms
sim-profile.c:642: undefined reference to `_panic'
sim-profile.c:642: undefined reference to `stat_add_sample'
sim-profile.c:642: undefined reference to `stat_add_sample'
sim-profile.c:642: undefined reference to `_panic'
sim-profile.c:642: undefined reference to `stat_add_samples'
sim-profile.c:642: undefined reference to `dlite_check'
sim-profile.c:642: relocation truncated to fit: GPREL dlite_check
sim-profile.c:642: undefined reference to `dlite_active'
sim-profile.c:642: relocation truncated to fit: GPREL dlite_active
sim-profile.c:642: undefined reference to `sim_num_insn'
sim-profile.c:642: relocation truncated to fit: GPREL sim_num_insn
sim-profile.c:642: undefined reference to `sim_num_insn'
sim-profile.c:642: relocation truncated to fit: GPREL sim_num_insn
sim-profile.c:642: undefined reference to `__check_break'
sim-profile.c:642: undefined reference to `sim_num_insn'
sim-profile.c:642: relocation truncated to fit: GPREL sim_num_insn
sim-profile.c:642: undefined reference to `dlite_main'
sim-profile.c:642: undefined reference to `sim_num_insn'
sim-profile.c:642: relocation truncated to fit: GPREL sim_num_insn
sim-profile.c:642: undefined reference to `sim_num_insn'
sim-profile.c:642: relocation truncated to fit: GPREL sim_num_insn
sim-profile.c:642: undefined reference to `sim_num_insn'
sim-profile.c:642: relocation truncated to fit: GPREL sim_num_insn
sim-profile.c:642: undefined reference to `sim_num_insn'
sim-profile.c:642: relocation truncated to fit: GPREL sim_num_insn
/home/surya/simplescalar/sslittle-na-sstrix/lib/libc.a(fmain.o): In function `main':
fmain.c:118: undefined reference to `MAIN__'

It clearly cannot link to the header files included in the program. But I don't know how to rectify this!! Please help me.. 

The **Makefile** has the following:

CC = gcc
OFLAGS = -O -g -Wall
MFLAGS = `./sysprobe -flags`
MLIBS  = `./sysprobe -libs` -lm
ENDIAN = `./sysprobe -s`
MAKE = make
AR = ar qcv
AROPT =
RANLIB = ranlib
RM = rm -f
RMDIR = rm -f
LN = ln -s
LNDIR = ln -s
DIFF = diff
OEXT = o
LEXT = a
EEXT =
CS = ;
X=/

If I run the command 

**./sysprobe -libs**

I get a **space** as output! Is that got to do something with the problem??
Kindly share your thoughts....

As you say, there's probably a header file which the compiler doesn't find (not "link to" - linking is something else - so ./sysprobe -libs returning an empty result is probbaly not the cause of this problem). Do you know what that header file is called? Is it actually in place? What is the actual compiler command being run?

Besides, it seems you build while still being root (the prompt is #). That's not a good idea; you may inadvertently change the system in ways you didn't intend. Only be root to do things you need to be root for.

---

### Post by green86 on 2009-09-02
Hi Arndt, Thank you for replying.. I quit being the root unnecessarily!

There are several folders like bin, gcc-2.7.2.3, sslittle-na-sstrix, simplesim-3.0 etc., under the simplescalar directory. The program **/home/surya/simplescalar/simplesim-3.0/sim-profile.c** includes headers like regs.h,options.h,misc.h and many more which are found in /home/surya/simplescalar/simplesim-3.0 (The same directory in which the program is located)
I compile the program using the command [B]
/home/surya/simplescalar/bin/sslittle-na-sstrix-gcc [/B]sim-profile.c
which is the way it is compiled in simplescalar.
I tried the following without knowing if it will work.. But none worked!

1) I tried adding **#include "/home/surya/simplescalar/simplesim-3.0/regs.h"** and so on to the header files.
The same error messages..

2) I tried compiling using the command
**/home/surya/simplescalar/bin/sslittle-na-sstrix-gcc -lregs sim-profile.c** 
after adding the header files in /usr/local  and glibc!
and also tried the command
**/home/surya/simplescalar/bin/sslittle-na-sstrix-gcc -L /home/surya/simplescalar/simplesim-3.0/ -lregs sim-profile.c** 
-lregs not found was the output in both cases..
What am I missing!??

---

### Post by Arndt on 2009-09-03
> **green86 said:**
> Hi Arndt, Thank you for replying.. I quit being the root unnecessarily!

There are several folders like bin, gcc-2.7.2.3, sslittle-na-sstrix, simplesim-3.0 etc., under the simplescalar directory. The program **/home/surya/simplescalar/simplesim-3.0/sim-profile.c** includes headers like regs.h,options.h,misc.h and many more which are found in /home/surya/simplescalar/simplesim-3.0 (The same directory in which the program is located)
I compile the program using the command [B]
/home/surya/simplescalar/bin/sslittle-na-sstrix-gcc [/B]sim-profile.c
which is the way it is compiled in simplescalar.
I tried the following without knowing if it will work.. But none worked!

1) I tried adding **#include "/home/surya/simplescalar/simplesim-3.0/regs.h"** and so on to the header files.
The same error messages..

2) I tried compiling using the command
**/home/surya/simplescalar/bin/sslittle-na-sstrix-gcc -lregs sim-profile.c** 
after adding the header files in /usr/local  and glibc!
and also tried the command
**/home/surya/simplescalar/bin/sslittle-na-sstrix-gcc -L /home/surya/simplescalar/simplesim-3.0/ -lregs sim-profile.c** 
-lregs not found was the output in both cases..
What am I missing!??

Maybe it's not actually a missing header file. If you look for one of the symbols that are missing, for example opt_reg_header, where is it defined?

---

### Post by green86 on 2009-09-04
> **Arndt said:**
> Maybe it's not actually a missing header file. If you look for one of the symbols that are missing, for example opt_reg_header, where is it defined?

It's defined in options.h which is included in sim-profile.c
The program and the header files are in /home/surya/simplescalar/simplesim-3.0/

---

### Post by Arndt on 2009-09-04
> **green86 said:**
> It's defined in options.h which is included in sim-profile.c
The program and the header files are in /home/surya/simplescalar/simplesim-3.0/

Does the compilation find options.h? If it does, try to find out why opt_reg_header isn't expanded. (If this thing were smaller, I'd download it and try it myself, but it looks like a lot of work.)

---

### Post by Arndt on 2009-09-04
> **green86 said:**
> It's defined in options.h which is included in sim-profile.c
The program and the header files are in /home/surya/simplescalar/simplesim-3.0/

What's -lregs, by the way? Is it supposed to be -Iregs, by any chance?

---

### Post by dwhitney67 on 2009-09-04
An "undefined reference" error is generated by the linker; not the compiler.

So the compiler is satisfied with finding all of the header files (those ending with a .h).

What is missing from the OP's 'gcc' statement are the -L and -l (lowercase ell) options.

---

### Post by Arndt on 2009-09-04
> **dwhitney67 said:**
> An "undefined reference" error is generated by the linker; not the compiler.

So the compiler is satisfied with finding all of the header files (those ending with a .h).



Yes, of course. I confused myself by taking the word "defined" (which I introduced myself) at face value. The header file doesn't define the symbol in this case - it likely declares it. But it's obvious from the output that it's the linking which fails, yes, since it mentions an object file. Sorry for the confusion.

---

### Post by dwhitney67 on 2009-09-04
It appears the OP is using a cross-compiler, not the typical GCC.

Full-path names should be avoided when including header files.  If a path is required to specify where the header file resides, then this is when/where the -I (uppercase eye) option should be used.  Similar when specifying where to find the library files.

So really, what the OP needs to do is provide specific information as to where his header file(s) AND his library(-ies) are located.

Ultimately, the Makefile should at a minimum have something like:
```

APP       = SimProfile

SRCS      = sim_profile.c
OBJS      = $(SRCS:.c=.o)

CROSS_DIR = /home/surya/simplescalar

CC        = $(CROSS_DIR)/bin/sslittle-na-sstrix-gcc

INCLUDES  = -I$(CROSS_DIR)/include
CFLAGS    = -Wall $(INCLUDES)

LDPATH    = -L$(CROSS_DIR)/lib
LIBS      = -lsslittle_lib

...

$(APP) : $(OBJS)
        $(CC) $^ $(LDPATH) $(LIBS) -o $@

.c.o :
        $(CC) -c $(CFLAGS) $<

```

@ the OP:  Replace LIBS with your actual library name(s).  Also, verify the location of your header file(s) AND your libraries.

---

### Post by green86 on 2009-09-05
Hi.. One of my friends gave this piece of info.. I found it useful in solving this prob:

[I]Okay, a few basics about compilation.

The steps for compiling a C language project are these:

1. Compile the C source code (.c files) into relocatable object binary files (.o files).
2. Link these relocatable object binary files together to give an executable.

You can sometimes do both steps in one just by running gcc on the source file. However, this only works if the source file contains the entire codebase for the project (which is not true in this case).

The other important concept is the makefile.[/I]     ***Make is a program to automate the compilation process, by checking files that have changed and recompiling/linking as appropriate.** It uses an instruction file called the 'makefile'.*

I concluded that I should make every time I do changes to the program and it works!!
Thanks a lot for your help too....

---

### Post by dwhitney67 on 2009-09-05
> **green86 said:**
> Hi.. One of my friends gave this piece of info.. I found it useful in solving this prob:

[I]Okay, a few basics about compilation.

The steps for compiling a C language project are these:

1. Compile the C source code (.c files) into relocatable object binary files (.o files).
2. Link these relocatable object binary files together to give an executable.

You can sometimes do both steps in one just by running gcc on the source file. However, this only works if the source file contains the entire codebase for the project (which is not true in this case).

The other important concept is the makefile.[/I]     ***Make is a program to automate the compilation process, by checking files that have changed and recompiling/linking as appropriate.** It uses an instruction file called the 'makefile'.*

I concluded that I should make every time I do changes to the program and it works!!
Thanks a lot for your help too....

You went from having linking issues to a state of enlightenment with respect to Makefiles, and magically your problem was solved?

It would have been nice if you had posted your solution (ie. Makefile), so by chance should someone else have a similar problem, your solution may be able to help them.

---

### Post by green86 on 2009-09-05
hey.. the makefile is created while installing the toolset.. I haven't done any changes.. With gcc linking didn't work but with make it worked!

---

