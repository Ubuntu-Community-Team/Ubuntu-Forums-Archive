---
title: "error: macro &quot;index&quot; requires 2 arguments, but only 1 given"
date: 2008-01-24
forum: Programming Talk
---

### Post by SandyKhan on 2008-01-24
Hi,
i'm cross-compiling for linux_arm as target platform. when i build my program, it stops unexpectedly and the following error messages are displayed at the end:


/home/user/mr2src/cldc/src/vm/share/runtime/BufferedFile.hpp:127:14: error: macro "index" requires 2 arguments, but only 1 given
/home/user/mr2src/cldc/src/vm/share/runtime/BufferedFile.hpp:152:42: error: macro "index" requires 2 arguments, but only 1 given
/home/user/mr2src/cldc/src/vm/share/runtime/BufferedFile.hpp:127: error: invalid member function declaration
/home/user/mr2src/cldc/src/vm/share/runtime/BufferedFile.hpp: In member function 'jint JVMBufferedFile::last_unread_file_pos()':
/home/user/mr2src/cldc/src/vm/share/runtime/BufferedFile.hpp:152: error: 'index' was not declared in this scope
make[1]: *** [FloatSupport_arm.o] Error 1
make[1]: Leaving directory `/home/user/mr2build/cldc/arm/linux_arm/target/debug'
make: *** [_debug] Error 2


is there any possibility that there might be something wrong with the code? or it is being caused by some other thing?

---

### Post by guruvadhiraj on 2009-03-02
Hi sandy,

Did the problem got solved. if yes what is the changes you made. Iam facing the same kind of error

Guru

---

