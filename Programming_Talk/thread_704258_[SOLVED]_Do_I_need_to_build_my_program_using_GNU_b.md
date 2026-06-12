---
title: "[SOLVED] Do I need to build my program using GNU build system?"
date: 2008-02-22
forum: Programming Talk
---

### Post by fyplinux on 2008-02-22
"Although all of the Unix variants were fundamentally similar, there were various differences between them. They had slightly different sets of header files and slightly different lists of functions in the system libraries, as well as more significant differences in areas such as terminal handling and job control."([http://sourceware.org/autobook/autobook/autobook_7.html#SEC7](http://sourceware.org/autobook/autobook/autobook_7.html#SEC7))

I think the above quotation is the reason why the GNU build system([http://www.gnu.org/software/autoconf/manual/html_node/The-GNU-Build-System.html#The-GNU-Build-System](http://www.gnu.org/software/autoconf/manual/html_node/The-GNU-Build-System.html#The-GNU-Build-System)) could be used. but if I build my program using GCC and every target machine of my program is using GCC, Do I still need the build system?

---

### Post by Bachstelze on 2008-02-22
If gcc is the only thing your program needs, you obviously don't need Autoconf and friends. They're useful if your program needs a lot of external libraries, for example.

---

### Post by hod139 on 2008-02-22
The autoconf build system is really ugly and non-portable.  I suggest you look into using cmake or scons (I prefer cmake for what it's worth).  Both have much simpler syntax and are cross platform.

---

### Post by Vadi on 2008-02-22
Both look prettier when compiling too.

---

### Post by fyplinux on 2008-02-22
> **hod139 said:**
> The autoconf build system is really ugly and non-portable.  I suggest you look into using cmake or scons (I prefer cmake for what it's worth).  Both have much simpler syntax and are cross platform.

But it seems autoconf is widely used and there are vast of materials introducing autoconf and the related tools.

---

### Post by hod139 on 2008-02-22
> **fyplinux said:**
> But it seems autoconf is widely used and there are vast of materials introducing autoconf and the related tools.
Autoconf is widely used now because there have not been alternatives.  However, more and more projects are beginning to use these more modern build tools.  For a high profile example, KDE is now using cmake.

---

