---
title: "Recompile kernel error"
date: 2005-12-02
forum: Outdated Tutorials &amp; Tips
---

### Post by test006 on 2005-12-02
Hi,
i am trying to recompile kernel on 5.10 to enable sctp support in the kernel for my own testing.
I followed all the steps as per the Howto but during the last step i get the following error:
i.e when i type make-kpkg --initrd --append-to-version=-sctp kernel_image kernel_headers
It goes through and than after a while it gives me the following error:

Inconsistent kallsyms data
Try setting CONFIG_KALLSYMS_EXTRA_PASS
make[1]: *** [vmlinux] Error 1
make[1]: Leaving directory `/usr/src/linux-source-2.6.12'
make: *** [stamp-build] Error 2

Can some help.....

thanks in advance....

---

### Post by jgreasley on 2006-05-04
I have the same error. Does anyone know why this happens?

tia

J

---

### Post by thasheep on 2006-05-04
Did you do 'make-kpkg clean' first?

---

