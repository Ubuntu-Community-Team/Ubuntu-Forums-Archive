---
title: "where can i get kernel source code which uses O(1) scheduler ?"
date: 2010-05-26
forum: Packaging and Compiling Programs
---

### Post by atulchavan on 2010-05-26
i am doing comparison between O(1) and cfs scheduler. current linux kernel using cfs scheduler. i think on kernel.org site whatever kernel versions are there, they are using cfs scheduler. where can i get kernel source code which uses O(1) scheduler.

---

### Post by SevenMachines on 2010-05-28
I think the fair group scheduler was merged in 2.6.23 or 4, something around then, so kernels before that i imagine. I'm not sure how you'd go about doing a comparison of the two though, but good luck!

[EDIT] I think there was a point around then when you could optionally config cfs which would then be the replacement, it seen a lot of improvements since then though obviously. I honestly have no idea if this is still possible in newer kernels though, hopefully theres some knowledgeable kernel person about :)

---

