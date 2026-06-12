---
title: "Grub Menu Kernel list recovery."
date: 2008-10-17
forum: New to Ubuntu
---

### Post by MarkBM on 2008-10-17
Hi
I upgraded to the latest kernel. Have a dual boot system with Ubuntu on second HDD. Went to modify menu.lst to make WinXP default.Attempted to do backup using sudo cp but accidently got source & destination reversed in the command & inadvertently restored an old backup which has all the kernels for 7.10. How can I restore the correct kernel list for 8.04LTS. I can still boot into the old kernel but end up in low resolution mode. 

Thanx.

---

### Post by iponeverything on 2008-10-17
from the prompt run:

```
sudo update-grub
```

It will regenerate your menu.lst

---

### Post by MarkBM on 2008-10-17
Cheers Thanx, I'll give it ago when I get home.

---

