---
title: "System call doubt"
date: 2008-12-14
forum: Programming Talk
---

### Post by shantanu.nalawade on 2008-12-14
Hello eveyone ,

I'm new to linux programming and wanted to know the system call that I can use for opening any application in Ubuntu.

Any help and guidance would be appreciated.

Thaank You.

---

### Post by kcode on 2008-12-14
You can use system() function to execute any program. Therefore, if you want to run the ls command from a C program, you can do so by doing system("ls") in your C program. Header file used will be stdio.h.

Hope this helped. :-)

---

### Post by mssever on 2008-12-14
If you mean you want to execute some command line, then the method will vary by language. kcode's answer applies to C. Python programs have several methods with their benefits and drawbacks.

If you want to open an arbitrary item like double-clicking its icon does, call xdg-open.

---

