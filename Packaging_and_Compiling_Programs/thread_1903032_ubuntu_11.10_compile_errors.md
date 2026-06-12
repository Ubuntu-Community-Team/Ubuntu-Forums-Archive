---
title: "ubuntu 11.10 compile errors"
date: 2012-01-01
forum: Packaging and Compiling Programs
---

### Post by csstu on 2012-01-01
I downloaded the Ubuntu 11.10 source and tried to compile it with the following commands:
> git clone git://kernel.ubuntu.com/ubuntu/ubuntu-oneiric.git oneiric
> cd oneiric
> make defconfig ARCH=um
> make menuconfig ARCH=um
> make ARCH=um

I received the following errors, then the compilation stopped.
fs/binfmt_elf.c: In function &#8216;load_elf_binary&#8217;:
fs/binfmt_elf.c:720:62: error: &#8216;__supported_pte_mask&#8217; undeclared (first use in this function)
fs/binfmt_elf.c:720:62: note: each undeclared identifier is reported only once for each function it appears in
fs/binfmt_elf.c:720:85: error: &#8216;_PAGE_NX&#8217; undeclared (first use in this function)
fs/binfmt_elf.c:721:3: error: implicit declaration of function &#8216;arch_add_exec_range&#8217; [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors
 
make[1]: *** [fs/binfmt_elf.o] Error 1
make: *** [fs] Error 2

It looks to me that __supported_pte_mask and _PAGE_NX have not been defined.  What should their default values be?  Where should they be defined?

---

### Post by oldos2er on 2012-01-01
Moved to Packaging and Compiling Programs

---

### Post by Bachstelze on 2012-01-01
Whatever you want to do, this is probably not the right way to do it. So what do you want to do?

---

