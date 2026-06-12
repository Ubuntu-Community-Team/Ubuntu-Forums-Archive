---
title: "DSDT(ACPI) Fix incorporating into the Kernel"
date: 2008-06-18
forum: Packaging and Compiling Programs
---

### Post by VMC on 2008-06-18
I have a buggy DSDT and I think I may have it fixed. The problem now is how to incorporated into the Kernel. Apparently there are three ways depending on the kernel. If you look here: [http://gentoo-wiki.com/index.php?title=HOWTO_Fix_Common_ACPI_Problems&action=edit&section=9](http://gentoo-wiki.com/index.php?title=HOWTO_Fix_Common_ACPI_Problems&action=edit&section=9)

They show 3 options. Since we have later Kernels, it appears I use options #3
"3. Build-in Options for Kernel 2.6.9 and Later ". I have copied the fixed DSDT over to /usr/src, but have no idea what to do next. They show some dialogues but how do I get there> Something with Kernel Config. I googled around, and it doesn't look easy. I wasn't under the impression that I had to recompile the whole kernel.

Has anyone included a custom DSDT into the kernel before?

Thanks for any help.

Edit: I found this thread, but now I'm more confused. The last post someone wanted to do what I'm trying to do, but that's the end of it. Also another poster mentioned to move config* file to /usr/src/linux. There is no just linux directory.

---

