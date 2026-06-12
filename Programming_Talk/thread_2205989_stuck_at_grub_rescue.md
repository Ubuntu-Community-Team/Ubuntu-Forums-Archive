---
title: "stuck at grub rescue"
date: 2014-02-16
forum: Programming Talk
---

### Post by IAMTubby on 2014-02-16
Hello,
 I need to rescue my grub. When I do an 'ls' on the grub rescue prompt, it gives me a lot of (hd0,msdosX). But when I do ls on each of these, all I get is one of the following.
```

1.error: unknown filesystem
2.error: bad filename

```
I was intending to do the following, but I'm unfortunately stuck at the very first step :(
```

[COLOR=#333333][FONT=UbuntuRegular]When you hit the right one, you'll get a line mentioning "lost+found" an so on.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Assuming (hd0,msdos5) is the right partition:[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]*set prefix=(hd0,5)/boot/grub*[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]*set root=(hd0,5)*[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]*insmod normal*[/FONT][/COLOR]
*normal*
```

Is is possible to restore my grub ?

---

### Post by IAMTubby on 2014-02-16
Okayy.. I got it done using boot-repair-disk utility. But still would be great to know if it can be done from command line, for a later time.

---

