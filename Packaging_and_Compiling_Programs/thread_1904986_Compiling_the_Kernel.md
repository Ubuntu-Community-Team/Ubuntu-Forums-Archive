---
title: "Compiling the Kernel"
date: 2012-01-05
forum: Packaging and Compiling Programs
---

### Post by sonnet on 2012-01-05
I'd like to understand few things about compiling the kernel:
uncompressed the folder is more than 400mb.

Now if i select only the driver and the modules that I intend to use, will the folder be greatly reduced in size once the kernel is recompiled?

---

### Post by Bachstelze on 2012-01-05
What you have extracted is the source code. The source is what the kernel is compiled from. The source doesn't change when you compile, but the size of the compiled kernel will be smaller if you compile less thigs in it.

---

### Post by sonnet on 2012-01-06
> **Bachstelze said:**
>  but the size of the compiled kernel will be smaller if you compile less thigs in it.
and what should i do to compile less things?

---

### Post by Bachstelze on 2012-01-07
With [font=monospace]make menuconfig[/font] or similar. Any guide on kernel compilation will explain that.

---

### Post by sonnet on 2012-01-07
> **Bachstelze said:**
> With [font=monospace]make menuconfig[/font] or similar. Any guide on kernel compilation will explain that.

Ah ok, that's what i wanted to know.
I'm using the more graphical xconfig (as things are explained in plain sight). So by deselecting completely modules the resulting compiled kernel should be much more smaller I guess.

---

### Post by Bachstelze on 2012-01-07
It will be smaller. How much smaller of course depdends on how big the module is.

---

