---
title: "gcc cannot create executables"
date: 2005-10-16
forum: Programming Talk
---

### Post by tr333 on 2005-10-16
when i attempt to compile a program, i get the following error:
> checking whether the C compiler (gcc  ) works... no
configure: error: installation or configuration problem: C compiler cannot create executables.

i installed gcc via "sudo apt-get install gcc".

---

### Post by invalid on 2005-10-16
You are probably missing related packages.
Do the following:

sudo apt-get install build-essential

Cheers,
Cb

---

### Post by tr333 on 2005-10-16
thanks.

any other base packages that would be useful to install?

---

### Post by toojays on 2005-10-16
Depends what you want to do. The documentation for whatever libraries you are using is always good to have. Emacs is essential IMHO as well ;)

---

