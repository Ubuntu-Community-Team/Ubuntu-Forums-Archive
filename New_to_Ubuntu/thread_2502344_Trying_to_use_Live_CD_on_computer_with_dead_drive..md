---
title: "Trying to use Live CD on computer with dead drive."
date: 2024-11-10
forum: New to Ubuntu
---

### Post by meh12111 on 2024-11-10
Hello. I'm trying to boot Ubuntu 20.04.6 LTS from a Toshiba Satellite using Ventoy. When I try to boot, it keeps popping up about ACPI errors and won't stop until I have to turn off the laptop. I saw some things online about turning off ACPI so I booted using grub2 and editted the boot options but it still kept erroring with some similar errors (not about ACPI tho). I'm not trying to recover or use the hard drive but I just want to see if I can boot into Ubuntu Live CD to do a few things.

---

### Post by yancek on 2024-11-11
If you are booting Ubuntu as an iso on a flash drive using Ventoy, it is a live system and can't be changed.  You might make note of whatever errors you see and post them as your current comments are too vague.  Also, some information about the computer hardware might help.

---

### Post by ActionParsnip on 2024-11-11
Try the boot option:
```

noacpi

```

---

