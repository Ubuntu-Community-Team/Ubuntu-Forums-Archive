---
title: "Getting the Kernel Version from the image"
date: 2006-05-18
forum: Programming Talk
---

### Post by dave on 2006-05-18
I am doing some work on comparing filesystem images, and have a question about the kernel.

Kernels when compiled compile in the date/time, so the same .config file will have 2 different kernels (at least by hash) made.

I was wondering if there was a way to find out kernel information based on the file itself.

---

### Post by tomchuk on 2006-05-19
This should work:

```

head -n20 <kernel image> | strings | grep '^2'

```

---

