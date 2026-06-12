---
title: "Vim regular expression weirdness"
date: 2009-08-31
forum: Programming Talk
---

### Post by Okuryo on 2009-08-31
Hello,

I'm trying to write a regular expression for numbers/bitstreams, to be used in a syntax highlighting file.
The numbers are just [FONT="Courier New"]**\d+**[/FONT], but bitstreams can start with [FONT="Courier New"]**0x**[/FONT] for hexadecimal bitstreams, or start with [FONT="Courier New"]**0b**[/FONT] for binary bitstreams.
Both bitstream types can include the [FONT="Courier New"]**x**[/FONT] (or [FONT="Courier New"]**X**[/FONT]) character for 'dont care', and a hexadecimal bitstream can include some binary digits surrounded by [FONT="Courier New"]**[**[/FONT] and [FONT="Courier New"]**]**[/FONT] for specific binary digits inside the hexadecimal number.
For example, valid bitstreams are:
```
0x5467FB
0x78X5X1
0bx10x00
0x123[01]
0xFF[1xx0]
0xF[1xx0]A
```

Now, the regular expression I wrote for this number/bitstream token is (it's case-insensitive):
```
\<\(\d\+\|0x\([0-9a-f_x]\|\[[01_x]\+\]\)\+\|0b[01_x]\+\)\>
```
The weird thing is, it sometimes doesn't match what should match.
For example, [FONT="Courier New"]**0xFF[1x0]**[/FONT] doesn't match, but if I add an [FONT="Courier New"]**A**[/FONT] to get [FONT="Courier New"]**0xFF[1x0]A**[/FONT], it does match.

What could be the reason for this, and how can I fix the regular expression?

Thanks a lot,
Daniel


EDIT: well, the problem seems to be the **\<** and **\>**. The brackets count as word-boundary characters, so the expression terminates at them. Removing the **\<** and **\>** solves this problem, but might introduce the problem of highlighting parts of things like **win32** or **web2.0x11** as numbers. Oh, well.

---

