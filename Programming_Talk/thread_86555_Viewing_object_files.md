---
title: "Viewing object files"
date: 2005-11-05
forum: Programming Talk
---

### Post by perenshaw on 2005-11-05
I want to know how to view *.o (object files) in ubuntu, but don't know what program to use - tried scite and gedit

---

### Post by Remmelas on 2005-11-05
not sure why you would want to view compiler output, but they are binary files(compiler output), so i doubt you will find anything that views them in any human readable fashion.(maybe a decompiler), but, then, if you have object files, you likely have the source they were created from.

---

### Post by perenshaw on 2005-11-05
k, thanks, jus wondrin, i can be curious at times.:)

---

### Post by Remmelas on 2005-11-05
Tis how we learn, right?

---

### Post by stuporglue on 2005-11-05
If you're really desparate/curious, you'd probably use a hex editor. If you happen to use Vim, you can view it there.  To view it in Hex in Vim the commands are* "%!xxd" (to hex) and "%!xxd -r" (from hex). If you use Gvim (easier!) you can use the Tools menu. 

*If you don't know Vim, you'd have to learn it first as Vim has a steep learning curve. Once you learn it though, it's pretty handy.

---

### Post by toojays on 2005-11-05
The nm program will show you the symbols which are present in an object file, which can be very useful sometimes. Similarly, objdump will decompile the object to assembly, which also has its uses.

---

