---
title: "Syscall hooking 2.6.28"
date: 2009-11-09
forum: Programming Talk
---

### Post by chorlick on 2009-11-09
Hi all. Im trying kernel hacking for the fist time and only a few lines into the module im running into issues. Im trying to hook into a sys call to the kernel but i can seem to actually get it right. Bascially ive found the sys_call_table and i have the right offset for the particular call i want(__NR_open) but i cant seem to actually update the pointer to my function. Basically whenever i try to write the syscall table the module crashes. I know the pointers are correct but my current thinking is that the page file is locked ro by the kernel however ive set it wb and called set_memory_rw from the module yet its a no go. Anyone have any ideas as to why? Im thinking maybe ubuntu does something weird in their patches to lock anyone out. I dunno. Any help appreciated. 

Linux chorlick-laptop 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009 i686 GNU/Linux

Thanks
chorlick

---

