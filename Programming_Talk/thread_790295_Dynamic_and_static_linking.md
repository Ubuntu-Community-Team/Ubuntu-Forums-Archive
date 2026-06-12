---
title: "Dynamic and static linking"
date: 2008-05-11
forum: Programming Talk
---

### Post by me_himanshu on 2008-05-11
Hi all,
        I didn't know where to post this query,hope i am at the right place....

Can any body tell me or give me some links where i can study about intricacies of static and  dynamic linking of libraries in details..**.please note that i want the intricacies of both the types of linking in details ** as i know the basics about them....i want all the material in concern with gcc compiler.

Thanks in advance
Himanshu

---

### Post by LaRoza on 2008-05-11
> **me_himanshu said:**
> Hi all,
        I didn't know where to post this query,hope i am at the right place....

Can any body tell me or give me some links where i can study about intricacies of static and  dynamic linking of libraries in details..**.please note that i want the intricacies of both the types of linking in details ** as i know the basics about them....i want all the material in concern with gcc compiler.

Thanks in advance
Himanshu

I know of some guides, but they aren't in that much detail. I could google for more documentation and I would probably find it though.

This may be a good start: [http://www.faqs.org/docs/Linux-HOWTO/GCC-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/GCC-HOWTO.html)

[http://gcc.gnu.org/onlinedocs/](http://gcc.gnu.org/onlinedocs/)

---

### Post by bite on 2008-05-11
If you have doc-linux-text installed, you should find /usr/share/doc/HOWTO/en-txt/Program-Library-HOWTO.gz 
Don't know the level of intricacy you are looking for, but there you will learn how to make a static or a dynamic library.

---

### Post by me_himanshu on 2008-05-13
Thanx for your replies....I have a new question now....Reading on static and shared libraries on internet i found this piece:

=================================================================
 List Dependencies:

The shared library dependencies of the executable can be listed with the command: ldd name-of-executable

    Example: ldd prog

  libctest.so.1 => /opt/lib/libctest.so.1 (0x00002aaaaaaac000)
  libc.so.6 => /lib64/tls/libc.so.6 (0x0000003aa4e00000)
  /lib64/ld-linux-x86-64.so.2 (0x0000003aa4c00000)
        
=================================================================

what are these: (0x00002aaaaaaac000),(0x0000003aa4e00000),(0x0000003aa4c00000)????

---

### Post by LaRoza on 2008-05-13
> **me_himanshu said:**
> 
what are these: (0x00002aaaaaaac000),(0x0000003aa4e00000),(0x0000003aa4c00000)????

They look like memory addresses.

---

### Post by aks44 on 2008-05-13
> **me_himanshu said:**
>   libctest.so.1 => /opt/lib/libctest.so.1 (0x00002aaaaaaac000)
  libc.so.6 => /lib64/tls/libc.so.6 (0x0000003aa4e00000)
  /lib64/ld-linux-x86-64.so.2 (0x0000003aa4c00000)
        
=================================================================

what are these: (0x00002aaaaaaac000),(0x0000003aa4e00000),(0x0000003aa4c00000)????

Looks like the addresses at which each of the shared libraries will be loaded in memory.

WRT to dynamic linking, you may also want to document yourself on the ELF file format.

---

