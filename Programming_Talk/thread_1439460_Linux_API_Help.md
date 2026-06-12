---
title: "Linux API Help"
date: 2010-03-26
forum: Programming Talk
---

### Post by vikasmailsu on 2010-03-26
Dear Experts,
               As there are Window API for getting system information . Is there any API for the same in linux.

I would like to get the following information :-

System Information:-
OS_name, OS_version,Hard_drive_serial_number,system_name, manufacturer,model, cpu_type etc

Memory Information:-
 total_memory_space,free memory , total_hard_drive_space,total_swap_space,free_swap_space,total_virtual_memory,
free_virtual_memory,CPU usage etc

Other Information:-
Computer_domain,BIOS etc

I would like to develop a program in c/c++ using the API that can do the specifc task.

Kindly help me in this regard

Thanks & Regards
Vikas

---

### Post by Compyx on 2010-03-26
There isn't a single unified API that can provide all the information you're looking for, but the kernel exposes a lot of information through the proc virtual filesystem, such as '/proc/cpuinfo' which will give you a lot of information on the CPU('s) of the system.

I suggest looking into the POSIX extensions to the C standard library, a lot of information can obtained through functions such as sysconf(3).

An excellent book on systems programming for Linux/Unix is 'Advanced Programming in the UNIX Environment, Second Edition' by W. Richard Stevens and Stephen A. Rago.


Good luck.

---

### Post by lavinog on 2010-03-26
many of the things you are looking for could be parsed from /proc
I am not sure how to get the hd serial number, but you could look at the source for hdparm.

---

