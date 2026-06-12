---
title: "gcc not picking up correct cpu"
date: 2014-06-24
forum: Packaging and Compiling Programs
---

### Post by kazik2002 on 2014-06-24
Hi all,

I hoping that someone can give me a quick reply about an issue where gcc is not picking up the right cpu for optimizations from local_cpu_detect.

I am using gcc 4.8 and the output of gcc -c -Q -march=native --help=target returns "pentium-m" as the -march and -msse3 as "disabled.

However the cpu I have is a T2300 which has SSE3 and therefore "prescott" would be a better match.
Also it returns -mfpmath=387 where -mfpmath=sse would be preferable.

How can I best change the defaults in gcc on a permanent basis to reflect these options?

And what are the options avaiable to achieve this?

Kind Regards,

Kaz

---

### Post by kazik2002 on 2014-06-25
OK from reading a bit more on it what I would specifically like to do is use a spec file derived from the original specs to instead of the local_cpu_detect setting march=native I would like to force march=native to be prescott as per replacing this line:

*cc1_cpu:
%{march=native:%>march=native %:local_cpu_detect(arch)   %{!mtune=*:%>mtune=native %:local_cpu_detect(tune)}} %{mtune=native:%>mtune=native %:local_cpu_detect(tune)}

However I am unsure of the syntax to be used.
I would still also like mfpmath=sse to be set also via the spec file.
I dont compile for any other arch so having these set permanently is fine.

---

