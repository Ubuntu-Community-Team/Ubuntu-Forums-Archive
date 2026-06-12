---
title: "makefile problem"
date: 2010-07-05
forum: Programming Talk
---

### Post by vksingh on 2010-07-05
Hi, I have problem related to makefile in c in linux(ubuntu).

What is the meaning of @prefix@

what this two @ symbols mean here?

Thanks,

Vivek

---

### Post by dwhitney67 on 2010-07-05
Could you post the entire Makefile, or will this be too difficult?

---

### Post by diesch on 2010-07-05
Are you sure that your file really is a makefile? Things like @prefix@ are usually used in autonf's makefile templates (usually called Makefile.in) that are used by the famous *./configure* to create a makefile

---

