---
title: "Compiling Old Kernel Modules Into a Newer Kernel"
date: 2010-10-30
forum: Programming Talk
---

### Post by TeamXlink on 2010-10-30
I'm unsure if this is in the right section or not.

I thought it might have belonged here:

[http://ubuntuforums.org/forumdisplay.php?f=41](http://ubuntuforums.org/forumdisplay.php?f=41)

But after reading this:

> 
**Before You Post**
This forum is for the installation, configuration, and usage of software supported by Ubuntu. That is, all the software in the main and restricted repositories.

Please only post relevant topics here.



Thanks,

Ubuntu Forums Team


I realized it doesn't belong there because old kernel modules are not in the main and restricted repositories anymore, I *think*.

Now onto, my question.

I'm trying to compile an old kernel module, specifically:

```

ppp_generic kernel

```

From this kernel:

```

2.6.18

```

The reason being, I was having problems with the kernel that I'm using:

```

2.6.24-21

```

After reading about this online, they said that the ppp_generic module from Hardy Heron has a few bugs, that to my knowledge weren't fixed in later kernel releases.

I want to replace my existing ppp_generic kernel module with the one from the older kernel.

How would I go about doing this?

Thank you.

---

