---
title: "GCC ARM cross-compiling?"
date: 2009-11-01
forum: Programming Talk
---

### Post by apetresc on 2009-11-01
Is there an easy way to bring in GCC's ARM cross-compiling features that doesn't involve reconfiguring and recompiling GCC from source and using that instead?

Basically, in a properly-configured GCC you could, for example, add [FONT="Lucida Console"]-mcpu=arm920t -mapcs-32[/FONT] to the CFLAGS and you would get an ARM binary. The [FONT="Lucida Console"]gcc[/FONT] that comes with Ubuntu doesn't have this config option set, however. 

This seems like a big gap in Ubuntu's developer offering (ARM is the most widely-used architecture in the world), so if by chance this *isn't* a hidden feature somewhere, there really should be a roadmap item for adding virtual packages that add these options somewhere.

---

