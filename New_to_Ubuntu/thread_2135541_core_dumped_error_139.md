---
title: "core dumped error 139"
date: 2013-04-14
forum: New to Ubuntu
---

### Post by annik on 2013-04-14
hii
 i am running some program on my pc (OS ubuntu-12.10 32 bit) most of programs are giving error mentioned below,i have tried ulimit -s and etc but it is not working  also backtrace by gdb says for example (gdb) frame 14: no registers or no stack ,i am not able to solve the problem ,how can i short it out this problem please tell me

Thanks in advance

Program received signal SIGSEGV: Segmentation fault - invalid memory reference.
 
Backtrace for this error:

#0  0xB6B91C8B

#1  0xB6B922DC

#2  0xB77CB3FF

#3  0xB6DC9106

#4  0xB6C96A3B

#5  0xB6C9984B

#6  0xB6C99DB2

#7  0xB6C9984B

#8  0xB6D3BE45

#9  0x81D14F8 in __fft_scalar_MOD_cfft3d at fft_scalar.f90:1353

#10  0x81CEE8F in invfft_x_ at fft_interfaces.f90:154

#11  0x8101105 in atomic_rho_ at atomic_rho.f90:150

#12  0x809258F in potinit_ at potinit.f90:123

#13  0x8060145 in init_run_ at init_run.f90:99

#14  0x804AE54 in pwscf at pwscf.f90:139

Segmentation fault (core dumped)

Error condition encountered during test: exit status = 139

Aborting

---

### Post by sanderj on 2013-04-15
Most programs do that? Then I would run memtest86+ from the GRUB menu and let it run for a few hours. If it gives errors, it means the problem is in your memory and/or mobo.

HTH

---

### Post by annik on 2013-04-16
i did as u told,but there is no error in memory and the problem is still same:(

---

