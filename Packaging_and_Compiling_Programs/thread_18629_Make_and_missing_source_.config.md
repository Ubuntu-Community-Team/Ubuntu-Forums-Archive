---
title: "Make and missing source .config"
date: 2005-03-07
forum: Packaging and Compiling Programs
---

### Post by Slavakion on 2005-03-07
I'm trying to install madwifi, and make wants to know where the source kernel is. So I download 2.6.11 and point make at that, but apparently .config is missing. Any idea of where I could find a standard kernel .config? And this is day one in linux, so I don't know about making my own. 8-[

---

### Post by Slavakion on 2005-03-07
Turns out that madwifi was auto-intalled by synaptic when I installed Ubuntu. But I *would* like to know more about the elusive .config in case I want to MAKE something.

---

### Post by toojays on 2005-03-08
Copies of the config files for your installed kernels will be in /boot, with a more descriptive name, e.g. /boot/config-2.6.10-4-powerpc.

---

### Post by az on 2005-03-08
...but unless you want to build your own custom kernel, just use the kernel headers.  The package is named linux-headers-2.6.(enter the version of your kernel here)

---

### Post by Slavakion on 2005-03-08
Thanks. I'll check that out next time I need to make something.

---

