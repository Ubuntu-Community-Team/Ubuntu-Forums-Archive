---
title: "decompress vmlinuz"
date: 2011-10-19
forum: Programming Talk
---

### Post by raghulnt on 2011-10-19
Hello Experts,
I'm trying to uncompress the vmlinuz(located at /boot) to vmlinux for oprofile. Linux 2.6.24-26.generic is the version.

The below command does not output anything:

Od-A d-t x1 vmlinuz-`uname -r` | grep '1f 8b 08 00'

can you please tell me what am I missing?

Please help.

Thanks

---

### Post by Zugzwang on 2011-10-19
Perhaps you could explain what "Od-A d-t x1" is supposed to mean?

---

### Post by Bachstelze on 2011-10-19
Using my psychic powers I guess it means 'od -t x1'.

---

### Post by gmargo on 2011-10-19
What is the significance of '1f 8b 08 00'?

The reason you don't see it is because **od(1)** prints lines 16 bytes at a time by default.  Your particular pattern happens to be split over two lines.

```

$ od -t x1 vmlinuz-2.6.24-26-generic | grep "1f 8b 08 00"
(returns nothing)

$ od --width=32 -t x1 vmlinuz-2.6.24-26-generic | grep "1f 8b 08 00"
0026200 f0 ff 8d 83 f0 14 1d 00 ff e0 54 14 1d 00 [COLOR=Red]1f 8b 08 00[/COLOR] 81 62 15 4b 02 03 ec 3a 6d 74 54 45 96 d5

```

---

