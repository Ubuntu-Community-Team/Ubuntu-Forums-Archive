---
title: "Generate an optimized config for kernel"
date: 2012-08-16
forum: Packaging and Compiling Programs
---

### Post by tempore on 2012-08-16
Is there a good way of generating a config file for compiling an optimized kernel? I want to remove as much as I can without breaking anything. I don't need Amateur Radio support, wireless, bluetooth, etc... Manually going through menuconfig is very time consuming. I know I should only disable a few things at a time and recompile but it would take forever. A script that could strip off the bulk then I could fine tune would be ideal.

As for why? I just like to tinker.

---

### Post by Bachstelze on 2012-08-17
Have you looked at the output of [font=monospace]make help[/font]?

---

