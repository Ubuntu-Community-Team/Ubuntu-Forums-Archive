---
title: "_syscallX and ubuntu 6.10 (edgy)"
date: 2006-11-02
forum: Programming Talk
---

### Post by yargevad on 2006-11-02
I'm trying to compile a program on ubuntu 6.10 that makes use of the _syscall1 macro but it's not included with the usual```
#include <linux/unistd.h>
```What am I missing? This worked with Dapper. ](*,)

---

### Post by yargevad on 2006-11-02
So after digging through some manpages (including *[man 2 intro]("http://www.die.net/doc/linux/man/man2/intro.2.html")*), I added the missing macros myself and all seems to be well. I wonder why they were left/taken out to begin with? :-k 

```
--- linux/unistd.h.old  2006-11-02 16:45:36.000000000 -0700
+++ linux/unistd.h  2006-11-02 16:43:29.000000000 -0700
@@ -6,4 +6,41 @@
  * Include machine specific syscallX macros
  */
 #include <asm/unistd.h>
+
+#define _syscall1(type,name,type1,arg1) \
+type name(type1 arg1) \
+{\
+  return syscall(__NR_##name, arg1);\
+}
+
+#define _syscall2(type,name,type1,arg1,type2,arg2) \
+type name(type1 arg1, type2 arg2) \
+{\
+  return syscall(__NR_##name, arg1, arg2);\
+}
+
+#define _syscall3(type,name,type1,arg1,type2,arg2,type3,arg3) \
+type name(type1 arg1, type2 arg2, type3 arg3) \
+{\
+  return syscall(__NR_##name, arg1, arg2, arg3);\
+}
+
+#define _syscall4(type,name,type1,arg1,type2,arg2,type3,arg3,type4,arg4) \
+type name(type1 arg1, type2 arg2, type3 arg3, type4 arg4) \
+{\
+  return syscall(__NR_##name, arg1, arg2, arg3, arg4);\
+}
+
+#define _syscall5(type,name,type1,arg1,type2,arg2,type3,arg3,type4,arg4,type5,arg5) \
+type name(type1 arg1, type2 arg2, type3 arg3, type4 arg4, type5 arg5) \
+{\
+  return syscall(__NR_##name, arg1, arg2, arg3, arg4, arg5);\
+}
+
+#define _syscall6(type,name,type1,arg1,type2,arg2,type3,arg3,type4,arg4,type5,arg5,type6,arg6) \
+type name(type1 arg1, type2 arg2, type3 arg3, type4 arg4, type5 arg5, type6 arg6) \
+{\
+  return syscall(__NR_##name, arg1, arg2, arg3, arg4, arg5, arg6);\
+}
+
 #endif /* _LINUX_UNISTD_H_ */
```

---

