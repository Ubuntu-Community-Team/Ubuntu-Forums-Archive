---
title: "errno in driver code"
date: 2011-12-21
forum: Programming Talk
---

### Post by auwerk on 2011-12-21
Hi! I'm developing driver for some I2C-based device.
i2c_smbus_write_word_data() returns error code, how can I get human-readable message? Can't find strerror() or perror() in kernel headers (I did a search with grep for that lexems in include dir inside kernel sources).
Thanks in advance.

Alex

---

### Post by gnometorule on 2011-12-21
I'm not sure that is possible without you writing an auxiliary routine. If you include linux/errno.h (usually referring back to a similar header in asm/ or asm-generic/ or such), you get the defines for kernel errors. But to printk those names, I think you'd need to create an array or such for the defines you see, and printk -(error number).

---

### Post by auwerk on 2011-12-25
Thanks for reply. I know about linux/errno.h and at the end I found this constant in asm-generic stuff. This has resolved my current problem, but it's no good, that there's no common solution for this in kernel sources, I think.

---

