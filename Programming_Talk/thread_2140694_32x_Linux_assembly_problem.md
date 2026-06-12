---
title: "32x Linux assembly problem"
date: 2013-04-30
forum: Programming Talk
---

### Post by silvercats on 2013-04-30
[COLOR=#333333][FONT=arial]I get an error when compiling this.[/FONT][/COLOR]



[COLOR=#333333][FONT=arial]section .data[/FONT][/COLOR]

[COLOR=#333333][FONT=arial]TestValue db 17h[/FONT][/COLOR]

[COLOR=#333333][FONT=arial]section .text[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]global	_start[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]_start:[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]nop[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]; Put your experiments between the two nops...[/FONT][/COLOR]

[COLOR=#333333][FONT=arial]mov eax,0FFFFFFFFh[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]ebx,02Dh[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]dec ebx	[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]inc eax[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]; Put your experiments between the two nops...[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]nop[/FONT][/COLOR]



[COLOR=#333333][FONT=arial]"label or instruction expected at start of line" is the error I get.[/FONT][/COLOR]

---

### Post by schragge on 2013-04-30
This ```
ebx,02Dh
``` probably should be ```
[COLOR=#ff0000]mov[/COLOR] ebx,02Dh
```

---

### Post by silvercats on 2013-04-30
Thanks! that was the problem.

---

