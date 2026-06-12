---
title: "Compiling Kernel"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by Maccabee on 2008-07-09
I ve some basic questions

1. Can i compile a linux kernel 2.6.9 in a 2.6.24 Ubuntu hardy??
2..If possible ,Can i boot with that kernel into my current OS
3.If 1 not possible then wat is the most appropriate solution without changing my current OS??

I need to use a kernel 2.6.9 since the package rtlinux has only patches upto tat version

---

### Post by LowSky on 2008-07-09
RTlinux wont work in the newer kernel? I would think it should...
I don't think it is possible to downgrade to a different kernel,  as most of your system is based on the newer kernel. Too many of ther programs would break.

---

### Post by Cypher on 2008-07-09
You can compile ANY Kernel you want, but you'll have to spend some time configuring the Kernel with the necessary options to allow your system to work.

The amount of configuration that you have to do has no significance on the Kernel version itself. So don't be surprised if your newly compiled Kernel doesn't boot up right away or has issues..

---

### Post by nowshining on 2008-07-10
[color=#009900]rtlinux has patches up to 2.6.24.7 - the last time I checked,  & i had problems with the rt so  i re-compiled without it awhile back and now use grsec in my kernel, etc..[/color]

---

### Post by sharks on 2008-07-10
And i think compiling kernel is not a absolute beginner thing. so this must be posted somewhere in the forum.

---

### Post by nowshining on 2008-07-10
[color=#993300]lolz i started compiling early in my linux years. :)[/color]

---

### Post by sharks on 2008-07-10
i have also compiled a kernel in Ubuntu 8.04. i think it linux-2.6.25 or something. the first time its so tough for me.

---

### Post by sharks on 2008-07-10
Master Kernel Thread

[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

---

### Post by nowshining on 2008-07-10
for me it was easy

> i have also compiled a kernel in Ubuntu 8.04. i think it linux-2.6.25 or something. the first time its so tough for me.

&

look in the system monitor or terminal ```
uname -r or uname -a. :)
```

---

