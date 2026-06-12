---
title: "Mono C# In chroot"
date: 2012-08-04
forum: Programming Talk
---

### Post by Paris.K on 2012-08-04
Hello,

I 'd like to run some C# programs in a chroot. I copied the following inside my jail

[LIST]
[*]My program (program.exe)
[*]/bin/sh and libraries found by ldd
[*]/bin/bash and libraries found by ldd
[*]/usr/bin/mono
[*]/usr/lib/mono
[/LIST]

When I try to run my program like this: ```
sudo chroot jail ./program.exe
```, I get the error message that this program does not exist. Mono C# does not do Dynamic Linking, so I cannot find the libraries on which my program depends, by using ldd. Could you please help me with that?

Thanks

---

### Post by Sslaxx on 2012-08-04
A mono-created program relies upon the .NET framework being present. Also, by default Ubuntu won't know what to do with the program.exe file - you'd need to run it as "mono ./program.exe" - which, if you're running it from a chroot jail, might be tricky.

---

### Post by directhex on 2012-08-06
> **Paris.K said:**
> Hello,

I 'd like to run some C# programs in a chroot. I copied the following inside my jail

[LIST]
[*]My program (program.exe)
[*]/bin/sh and libraries found by ldd
[*]/bin/bash and libraries found by ldd
[*]/usr/bin/mono
[*]/usr/lib/mono
[/LIST]

When I try to run my program like this: ```
sudo chroot jail ./program.exe
```, I get the error message that this program does not exist. Mono C# does not do Dynamic Linking, so I cannot find the libraries on which my program depends, by using ldd. Could you please help me with that?

Thanks

running Mono executables directly, as "./program.exe" (rather than as "mono program.exe") requires that /proc be mounted, and that the binfmt_misc kernel module be loaded, and that binfmt_misc be mounted to /proc/sys/fs/binfmt_misc, and that ':CLR:M::MZ::/usr/bin/mono:' be echoed into /proc/sys/fs/binfmt_misc/register

It's automated by the binfmt-support package

And I'd certainly not consider doing it inside a chroot. The Mono app deployment guidelines strongly caution against using "./foo.exe" rather than "mono foo.exe" precisely because it causes this kind of problem.

---

### Post by Paris.K on 2012-08-07
I tried running the program in chroot like ```
mono Program.exe
``` and it still needed /proc to be mounted. I did mount it and the new errors showed u. I finally got bored and quit :P

---

