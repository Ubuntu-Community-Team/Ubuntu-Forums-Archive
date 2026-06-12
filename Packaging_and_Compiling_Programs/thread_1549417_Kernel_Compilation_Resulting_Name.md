---
title: "Kernel Compilation Resulting Name"
date: 2010-08-09
forum: Packaging and Compiling Programs
---

### Post by teqdruid on 2010-08-09
Hi all-

I'm compiling a custom kernel with make-kpkg.  It puts "+drm33.5" in my kernel name.  Yuck!  I've had programs fail (Eclipse, in particular) due to the ugly uname result.  How do I get rid of that?

Thanks

---

### Post by Milos_SD on 2010-08-09
Use this command:

make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers

Insted of **custom** use what ever you want to name your kernel. :)

For example, let's set **custom** to **teqdruid**

Your uname would be something like:
**2.6.35-teqdruid**

---

### Post by teqdruid on 2010-08-09
> **Milos_SD said:**
> Use this command:

make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers

Insted of **custom** use what ever you want to name your kernel. :)

For example, let's set **custom** to **teqdruid**

Your uname would be something like:
**2.6.35-teqdruid**

That's exactly the command I used, but instead I get:
linux-image-2.6.32.15+drm33.5-limit_1.1_amd64.deb

I've applied the Ubuntu patch set and I'm using 10.04.

---

### Post by teqdruid on 2010-08-09
> **teqdruid said:**
> That's exactly the command I used, but instead I get:
linux-image-2.6.32.15+drm33.5-limit_1.1_amd64.deb

I've applied the Ubuntu patch set and I'm using 10.04.

Please disregard all.  I've solved the problem.  Looks like the patch sets:
-EXTRAVERSION =
+EXTRAVERSION = .15+drm33.5

In the Makefile.  I can change that.

This behavior very annoying, actually.  The standard package certainly doesn't have that in the string.

---

