---
title: "Kernel Compilation/Make Errors"
date: 2006-11-12
forum: Programming Talk
---

### Post by Brando569 on 2006-11-12
hey everyone, i (like alot of you also) like to compile my own kernel and have been successful about 75% of the time. Sometimes I'll get an arbitrary error that stops me in my tracks and i'll just do a make clean and recompile it, sometimes it works and other times it doesnt. 

i wrote a script that works fine and does everything for me except choose the specific options in xconfig (which is how i want it) but sometimes i get an error after its been compiling for about 10-15 minutes and i dont know what it means. ill usually get one of these two (if not both): 

```
make[1]: *** [.tmp_vmlinux1] Error 1
make[1]: Leaving directory `/usr/src/linux-2.6.17'
make: *** [debian/stamp-build-kernel] Error 2

```

where is the actual error? is it before the error is thrown? this is some of the ouput before the errors were thrown:

```
LD      .tmp_vmlinux1
init/built-in.o: In function `try_name':
do_mounts.c:(.text+0x5e3): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `name_to_dev_t':
(.text+0x8eb): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `change_floppy':
(.init.text+0xa71): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `mount_block_root':
(.init.text+0xd07): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `do_header':
initramfs.c:(.init.text+0x44b3): undefined reference to `__stack_chk_fail'
arch/i386/kernel/built-in.o:(.text+0x51f1): more undefined references to `__stack_chk_fail' follow
make[1]: *** [.tmp_vmlinux1] Error 1
make[1]: Leaving directory `/usr/src/linux-2.6.17'
make: *** [debian/stamp-build-kernel] Error 2
```

i know a decent amount about linux but not enough to sift through all of this and figure out what the problem is. now if it was a c++ program i wrote myself that would be no problem.

any help would be appriciated :-D

---

### Post by 23meg on 2006-11-12
For a start, check the links given [here]("http://www.mail-archive.com/ubuntu-in@lists.ubuntu.com/msg00291.html"). It seems to be the exact error you're getting.

---

### Post by Brando569 on 2006-11-12
thanks for the links.i see whats causing the errors but i still dont understand how to fix it. at first i thought it might be a problem with beyond4 but then i saw people were getting the same errors using 2.6.18 w/o beyond4. another odd thing is i just compiled 2.6.18 using autokernel and it worked fine, yet when i tried to compile my custom kernel with beyond4 it threw those errors then i tried it with beyond4 but didnt tweak the kernel any and it still threw the errors.

im royally confused now...

---

