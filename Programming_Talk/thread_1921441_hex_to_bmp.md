---
title: "hex to bmp?"
date: 2012-02-06
forum: Programming Talk
---

### Post by conradin on 2012-02-06
Hi all,
I want to take raw hex and dump that to a bitmap in c programming.
How might I do that? additionaly, I would like to write strings to the bmp.

---

### Post by conradin on 2012-02-06
Here's something which works 

```
xxd -r 0hxd fooBar.bmp
```

where 0hxd is a file with:
```
0000000: 424d 4600 0000 0000 0000 3600 0000 2800
0000010: 0000 0200 0000 0200 0000 0100 1800 0000
0000020: 0000 1000 0000 130b 0000 130b 0000 0000
0000030: 0000 0000 0000 ff06 00ff ffff 0000 0000
0000040: 4c   4f   56   45   20   4d   45
```
That is a 2x2 pixel bitmap with "LOVE ME" tucked in on the end.
Its not C, but i could write a script and call it in C.

---

