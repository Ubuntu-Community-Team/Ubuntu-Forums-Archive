---
title: "Installing mingw"
date: 2006-02-27
forum: Programming Talk
---

### Post by drgreborn on 2006-02-27
Really sorry about this. But how do I install mingw into Ubuntu? I need to do some school work which are Windows based. Just a quick and dirty installation guide would do. Thank you very much.

---

### Post by toojays on 2006-02-27
Run the synaptic package manager, and search for packages with mingw in the name. There are three packages you need to install, all starting with mingw. You then have access to all the regular gnu tools, prefixed with 'i586-mingw32msvc-', e.g. your Windows GCC is called i586-mingw32msvc-gcc.

Is that quick and dirty enough for you?

---

### Post by drgreborn on 2006-02-28
Right thanks. Got it in, so how do I check ifthe gcc I'm using is the mingw one? I type gcc -v And it displays teh posix version. Or they using teh same?

---

### Post by toojays on 2006-02-28
No, they are not the same. Where you would normally run gcc, you now need to run i586-mingw32msvc-gcc.

If you want a way to easily switch from native gcc to the mingw gcc, you can use a makefile to control your build.

---

