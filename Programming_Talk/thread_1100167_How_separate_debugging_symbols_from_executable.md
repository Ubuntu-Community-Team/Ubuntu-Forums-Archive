---
title: "How separate debugging symbols from executable?"
date: 2009-03-18
forum: Programming Talk
---

### Post by mhexyl on 2009-03-18
just like some dbg packages do?

---

### Post by lensman3 on 2009-03-19
What do you mean by separate?  Do you mean delete them?  To delete the debug symbols you the program "strip <filename.obj>.  You might run the executable through "nm <filename>" to see what libraries are needed.  I don't remember is strip will  strip the debug info from an executable.

The program "objdump" will list the assembler equivalent and if the debug has been added then it will list the external symbols too.  There are lots of flags for objdump.  

"ldd <executable>" will list the external ".so" dynamic libraries.

Hope this helps.

---

### Post by nvteighen on 2009-03-19
Strip does what you want. Look at strip's manpage and see the two possible methods described under the **--only-keep-debug** flag's description.

---

### Post by mhexyl on 2009-03-20
Thanks for reply!

May be flag -g and flag --strip-unneeded are what I need. I want to find out why some rule in default Valgrind suppression file are invalid without libglib2.0-0-dbg package. I built glib myself and use strip with flag -g, but these rule is still valid. After reading strip manual again, I think I have missed flag --strip-unneeded.

---

