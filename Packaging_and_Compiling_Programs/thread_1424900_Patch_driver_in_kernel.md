---
title: "Patch driver in kernel"
date: 2010-03-08
forum: Packaging and Compiling Programs
---

### Post by babyhuey on 2010-03-08
I have a Synaptics Clickpad that is not well supported in the current kernel. However, there exists a patch to get a few things working in the interim. I originally planned to grab the latest kernel source and patch the synaptics driver with said patch. 

Is there a way that I can patch and recompile just the synaptics driver? I would think that it would only be possible if it is compiled as a module, which I don't think it is. Do I need to go ahead and recompile the entire kernel?

Thanks!

---

### Post by iponeverything on 2010-03-08
If it not a module, you are right in that you will have recompile the kernel.

---

### Post by babyhuey on 2010-03-09
Thanks for the quick reply!

---

