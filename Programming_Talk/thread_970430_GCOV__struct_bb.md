---
title: "GCOV : struct bb"
date: 2008-11-04
forum: Programming Talk
---

### Post by forum_user on 2008-11-04
Hi,

I am working on gcov . There is one structure called "struct bb". I  just want to know how bb struture members are getting assigned values. I am not sure how is happening this.

Thanks in advance

---

### Post by Zugzwang on 2008-11-04
Dear OP, please always make sure to explain uncommon abbreviations (What's GCOV?).

You can use a debugger and tell it to stop the execution whenever some variable value changes. Perhaps you can do that here as well?

---

### Post by forum_user on 2008-11-04
sorry for the inconvience caused...GCOV is nothing but a code coverage tool for linux. And it is provided as a patch to the kernel. I dont think we can use debugger and all. Correct me if I am wrong.

---

### Post by Zugzwang on 2008-11-04
> **forum_user said:**
> sorry for the inconvience caused...GCOV is nothing but a code coverage tool for linux. And it is provided as a patch to the kernel. I dont think we can use debugger and all. Correct me if I am wrong.

If you have two machines, you can run the kernel on the one machine and debug it on the other one.

Apart from that, you are unlikely to get help on that here - Your question is rather advanced and special to the tool you are using. You might want to try their mailing list, if they have any.

---

