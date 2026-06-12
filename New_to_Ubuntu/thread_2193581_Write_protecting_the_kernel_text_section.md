---
title: "Write protecting the kernel text section"
date: 2013-12-13
forum: New to Ubuntu
---

### Post by hel.souz on 2013-12-13
hi all :)

i have linaro (lubuntu) installed on my cubieboard2, and after some usage, i ALWAYS get those errors:

```
[COLOR=#000000][FONT=dejavu sans mono]Write protecting the kernel text section c0008000 - c07e4000
[/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]ureadahead main process (485) terminated with status 5 ...[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]plymouth main process (53) killed by segv signal.

[/FONT][/COLOR]
```After some research i was able to eliminate the last two, remaining with this one:

```
[COLOR=#000000][FONT=dejavu sans mono]Write protecting the kernel text section c0008000 - c[/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]07e4000[/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]

[/FONT][/COLOR]
```I have no clue on what to do from here. I hope you can help me in some way. 

I am using an SD card with debian to mount linaro and access as root.

---

