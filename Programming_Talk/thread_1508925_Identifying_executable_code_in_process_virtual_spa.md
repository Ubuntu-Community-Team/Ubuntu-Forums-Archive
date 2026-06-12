---
title: "Identifying executable code in process virtual space"
date: 2010-06-13
forum: Programming Talk
---

### Post by DBQ on 2010-06-13
I have a question, how can I identify (programmatically) the part of the process's virtual address space which contains the executable code. I seen many diagrams of process virtual address space, but how can I actually tell which part is where in the virtual memory of an actual process? For example, from the bellow (output from /proc/pid/maps) I know the address containing the binary are the ones with /bin/sleep next to them. Are there any other ways? 


0086d000-00888000 r-xp 00000000 08:06 5431341 /lib/ld-2.11.1.so 
00888000-00889000 r--p 0001a000 08:06 5431341 /lib/ld-2.11.1.so 
00889000-0088a000 rw-p 0001b000 08:06 5431341 /lib/ld-2.11.1.so 
009b6000-009b7000 r-xp 00000000 00:00 0 [vdso] 
00e0b000-00f5e000 r-xp 00000000 08:06 5447887 /lib/tls/i686/cmov/libc-2.11.1.so 
00f5e000-00f5f000 ---p 00153000 08:06 5447887 /lib/tls/i686/cmov/libc-2.11.1.so 
00f5f000-00f61000 r--p 00153000 08:06 5447887 /lib/tls/i686/cmov/libc-2.11.1.so 
00f61000-00f62000 rw-p 00155000 08:06 5447887 /lib/tls/i686/cmov/libc-2.11.1.so 
00f62000-00f65000 rw-p 00000000 00:00 0 
08048000-0804f000 r-xp 00000000 08:06 6308021 /bin/sleep 
0804f000-08050000 r--p 00006000 08:06 6308021 /bin/sleep 
08050000-08051000 rw-p 00007000 08:06 6308021 /bin/sleep 
09c80000-09ca1000 rw-p 00000000 00:00 0 [heap] 
b75e6000-b7625000 r--p 00000000 08:06 647523 /usr/lib/locale/en_US.utf8/LC_CTYPE 
b7625000-b7743000 r--p 00000000 08:06 647651 /usr/lib/locale/en_US.utf8/LC_COLLATE 
b7743000-b7744000 rw-p 00000000 00:00 0 
b774b000-b774c000 r--p 00000000 08:06 647612 /usr/lib/locale/en_US.utf8/LC_NUMERIC 
b774c000-b774d000 r--p 00000000 08:06 6479916 /usr/lib/locale/en_US.utf8/LC_TIME 
b774d000-b774e000 r--p 00000000 08:06 6479918 /usr/lib/locale/en_US.utf8/LC_MONETARY 
b774e000-b774f000 r--p 00000000 08:06 6504641 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES 
b774f000-b7750000 r--p 00000000 08:06 647618 /usr/lib/locale/en_US.utf8/LC_PAPER 
b7750000-b7751000 r--p 00000000 08:06 647619 /usr/lib/locale/en_US.utf8/LC_NAME 
b7751000-b7752000 r--p 00000000 08:06 6479919 /usr/lib/locale/en_US.utf8/LC_ADDRESS 
b7752000-b7753000 r--p 00000000 08:06 6479920 /usr/lib/locale/en_US.utf8/LC_TELEPHONE 
b7753000-b7754000 r--p 00000000 08:06 647622 /usr/lib/locale/en_US.utf8/LC_MEASUREMENT 
b7754000-b775b000 r--s 00000000 08:06 5070903 /usr/lib/gconv/gconv-modules.cache 
b775b000-b775c000 r--p 00000000 08:06 6479921 /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION 
b775c000-b775e000 rw-p 00000000 00:00 0 
bfd1f000-bfd34000 rw-p 00000000 00:00 0 [stack]

---

### Post by rnerwein on 2010-06-14
hi
i think what you want is --> man size of the programm
have a look at the command: [COLOR=Red]size[/COLOR] /path_to_any_program/xyz
ciao

---

### Post by soltanis on 2010-06-14
It would be those sections of code where the x flag is set. x means "executable"; since Intel-compatible processors have the NX flag (no execute, for protecting against buffer overflow attacks) capability, sections of the memory space will be specifically marked for execution. And yes, the part marked /bin/sleep with r-xp would appear to be the actual executable code of the process.

---

### Post by rnerwein on 2010-06-15
> **soltanis said:**
> It would be those sections of code where the x flag is set. x means "executable"; since Intel-compatible processors have the NX flag (no execute, for protecting against buffer overflow attacks) capability, sections of the memory space will be specifically marked for execution. And yes, the part marked /bin/sleep with r-xp would appear to be the actual executable code of the process.

hi 
soltanis tells the true.
stack overflow was ( and it is in MS ) former time. 
like in other systems ( like solaris etc ..... ) the administrator have to set up the kernel parameters they must
know what they do ( this works in linux too )  !!
just think about java ( put your thread into the stack ---> LOSER ). i  saw this a couple if timies.
may be a long time ago, but for other people to get this hint.
ciao

---

### Post by Zugzwang on 2010-06-15
Dear rnerwein,

please consider organizing your posts in a more understandable way and make sure that you actually understand the questions raised in a thread before posting. This is not meant to be rude, but rather I want to give you the opportunity to reflect on your previous post to help you in increasing the quality of your future answers.

Ok, let's start.

> **rnerwein said:**
> stack overflow was ( and it is in MS ) former time. The only connection 


For most readers of this thread, it is non-obvious how this relates to what was written before. The only connection that I see are the "buffer overflows" mentioned by soltanis. In his/her post, he/she just mentions it to give an impression on why the information is actually stored by the kernel or why it is named this way. Starting your post with the sentence quoted above gives the "new" reader of this thread the impression that this is actually an important point - which it isn't. Also of course the sentence as written is not entirely correct. Of course there can still occur stack overflows in our "modern times" - It's just that Linux does not distinguish between these and "segmentation faults" in terms of error messages.

> **rnerwein said:**
> 
like in other systems ( like solaris etc ..... ) the administrator have to set up the kernel parameters they must
know what they do ( this works in linux too )  !!


Here you continue to deviate from the topic.

> **rnerwein said:**
> 
just think about java ( put your thread into the stack ---> LOSER ). i  saw this a couple if timies.

This is hardly understandable. It is again non-obvious what the meaning behind the phrase "put your thread into the stack" could be, as a thread is no piece of information stored in memory. And who is meant to be the loser in this context? Also, the concept of "memory protection" in Java is totally incomparable to natively running programs, so this leaves most people puzzled here.

I hope that this "example analysis" of your post helps you in understanding how you can improve your future posts.

---

