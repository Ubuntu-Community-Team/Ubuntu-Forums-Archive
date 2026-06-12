---
title: "Windows Apps"
date: 2005-12-02
forum: Programming Talk
---

### Post by blanky on 2005-12-02
Hey guys, I didn't google it since I'm in a hurry, sorry, I always do but I cant right now. In Kdevelop they have the option of creating windows apps, and I'd like to create some as well, however, not using kdevelop (eclipse or just normal gedit). Are there any things I have to pass to G++ to make it make a windows app? I have wine installed by the way, thanks guys, very much appreciated.

---

### Post by toojays on 2005-12-02
I don't use kdevelop, but at my work I create windows apps on my Ubuntu machine, so I have some idea of what's involved. You don't use the regular gcc, you need a version which is setup to build windows apps. You can get this by installing the mingw* packages from universe.

---

### Post by blanky on 2005-12-02
Thanks, and then after, what command would I run to compile 'file.c/pp'?  Thanks again.

---

### Post by toojays on 2005-12-03
After you install the mingw packages, you basically have the full GNU compiler toolchain at your disposal. All the mingw tools are prefixed with something like i586-mingw-msvc- (it's something like that anyway, use tab completion), so you just compile your app with i586-mingw-msvc-gcc.

---

