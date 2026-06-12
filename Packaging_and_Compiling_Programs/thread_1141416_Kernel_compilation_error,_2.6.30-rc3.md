---
title: "Kernel compilation error, 2.6.30-rc3"
date: 2009-04-28
forum: Packaging and Compiling Programs
---

### Post by Zorael on 2009-04-28
I'm trying to compile myown 2.6.30-rc3 kernel to shave off stuff I don't need, make it preemptible and 1000hz (just for the heck of it), and enable intel kernel mode-setting by default. Upon compiling, however, I get the following error and the process stops.
```
drivers/built-in.o: In function `intel_opregion_init':
(.text+0xaefaa): undefined reference to `**acpi_video_register**'
make[1]: *** [.tmp_vmlinux1] Error 1
make[1]: Leaving directory `/usr/src/linux-2.6.29'
make: *** [debian/stamp/build/kernel] Error 2
```

acpi_video_register is defined in **drivers/acpi/video.c**, and somehow (?) it's not being included. There's also a "stub" of it in **include/acpi/video.h**, which only returns 0. Neither seems to be read?

Obviously I disabled something in the .config file I shouldn't have, but how do I tell what it is?

---

### Post by bodhi.zazen on 2011-12-07
This is an old thread, but it comes up in google searches.

You enabled something (do not know what) , and built it into your kernel (rather than a module). This driver needs acpi_video, but you are building the apci_video as a module.

Try changing

CONFIG_ACPI_VIDEO=m

to

CONFIG_ACPI_VIDEO=y

to make that change you may need to compile a number of additional drivers (into the kernel) as well.

If that does not resolve the error, then it would be something to (bug) report to kernel.org

---

