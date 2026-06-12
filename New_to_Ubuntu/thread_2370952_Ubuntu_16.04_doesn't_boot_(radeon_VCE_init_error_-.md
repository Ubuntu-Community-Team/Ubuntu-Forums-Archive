---
title: "Ubuntu 16.04 doesn't boot (radeon VCE init error -22)"
date: 2017-09-09
forum: New to Ubuntu
---

### Post by the+phoenix on 2017-09-09
[SIZE=2][FONT=arial]I recently started using a pre-installed Ubuntu 16.04 laptop. I upgraded Ubuntu to 16.04.3. However now my laptop isn't starting. It shows[/FONT] [COLOR=#333333][FONT=Consolas][FONT=arial black]radeon 0000:01:00.0: VCE init[/FONT] [FONT=arial black]error (-22)[/FONT] [FONT=arial]and screen remains &#8203;black with this error message forever. Kindly assist me[/FONT].[/FONT][/COLOR][/SIZE]

---

### Post by BenginM on 2017-09-09
Hiya, does the machine happens to have a dual graphics Intel/Radeon , as in the CPU has a built-in integrated Intel GPU, if so, then disable the AMD radeon in the BIOS and boot with Intel's graphic .. when it boots and reach the desktop, then consider reporting a kernel bug :

[https://wiki.ubuntu.com/Kernel/Bugs](https://wiki.ubuntu.com/Kernel/Bugs)

you might as well inform the kernel team about the bug on IRC , join #ubuntu-kernel on freenode using [this web-interface]("https://webchat.freenode.net/") .

---

### Post by Yellow Pasque on 2017-09-11
Try booting into the original 4.4.x kernel (assuming you didn't remove it).

---

### Post by the+phoenix on 2017-09-14
That way I won't be able to use the radeon graphics card.

---

### Post by the+phoenix on 2017-09-14
Tried. Didn't work.

---

