---
title: "User Mode Vs Kernel Mode"
date: 2008-10-30
forum: Programming Talk
---

### Post by thunderfox933 on 2008-10-30
Does Code run better In Kernel mode since it has full access to everything?

---

### Post by hessiess on 2008-10-30
Yes if your developing device drivers or the kernal. running anything that the user interacts with directly in kernal mode would provide a big scurity problem.

---

### Post by Joeb454 on 2008-10-30
+1

User Mode is probably best for anything other than device drivers and things that need to interact directly with the kernel.

---

### Post by jespdj on 2008-10-31
> **thunderfox933 said:**
> Does Code run better In Kernel mode since it has full access to everything?
What do you mean with "run better"?

There should be as little code run in kernel mode as possible, because if there's a bug while running in kernel mode, it will most likely lock up the computer hard. Always prefer user mode above kernel mode; only run stuff in kernel mode if really necessary.

Note that there are certain restrictions to kernel mode code. It cannot, for example, use floating-point instructions (so in C you would not be able to use the float and double data types).

---

