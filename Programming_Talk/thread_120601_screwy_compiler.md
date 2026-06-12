---
title: "screwy compiler"
date: 2006-01-22
forum: Programming Talk
---

### Post by Syntax13 on 2006-01-22
i was compiling this program and others just fine all day yesterday, but for some reason after i rebooted my computer this morning, gcc sudenly started being screwy. here's what it tells me (and glfw.h and library are where they're supposed to be)

```

$ gcc -Wall -lglfw -lGL -lGLU -lX11 -lpthread -lm -o LearnGLFW02.exe LearnGLFW02.cpp
LearnGLFW02.cpp:125:2: warning: no newline at end of file
/tmp/cc1MjnL2.o: In function `KeyCheck()':
LearnGLFW02.cpp:(.text+0xf): undefined reference to `glfwGetKey'
LearnGLFW02.cpp:(.text+0x29): undefined reference to `glfwGetKey'
LearnGLFW02.cpp:(.text+0x43): undefined reference to `glfwGetKey'
LearnGLFW02.cpp:(.text+0x5d): undefined reference to `glfwGetKey'
/tmp/cc1MjnL2.o: In function `Draw()':
LearnGLFW02.cpp:(.text+0x103): undefined reference to `glfwGetTime'
LearnGLFW02.cpp:(.text+0x116): undefined reference to `glfwGetWindowSize'
/tmp/cc1MjnL2.o: In function `main':
LearnGLFW02.cpp:(.text+0x473): undefined reference to `glfwInit'
LearnGLFW02.cpp:(.text+0x496): undefined reference to `glfwOpenWindow'
LearnGLFW02.cpp:(.text+0x4a7): undefined reference to `glfwTerminate'
LearnGLFW02.cpp:(.text+0x4bd): undefined reference to `glfwSetWindowTitle'
LearnGLFW02.cpp:(.text+0x4cd): undefined reference to `glfwEnable'
LearnGLFW02.cpp:(.text+0x4e1): undefined reference to `glfwSwapBuffers'
LearnGLFW02.cpp:(.text+0x4ee): undefined reference to `glfwGetKey'
LearnGLFW02.cpp:(.text+0x502): undefined reference to `glfwGetWindowParam'
LearnGLFW02.cpp:(.text+0x524): undefined reference to `glfwTerminate'
collect2: ld returned 1 exit status

```

anyone have any suggestions of what's wrong?

---

### Post by rock freak on 2006-01-23
the error you are getting is to do with the include libaried everytime its happened with me, any chance of seeign the source code maybe able to give a better answer then :)

(sorry about spelling)

---

### Post by Viro on 2006-01-23
It's clearly a linker problem, as it seems to compile fine. Have you tried passing the path to the libraries? Use the flag -L/path/to/library and see if that works.

---

### Post by toojays on 2006-01-23
Try listing -lglfw last and see if that helps.

---

### Post by LordHunter317 on 2006-01-23
You should always list libraries to link last, after the code you wish to compile/link.  You should also always list them after search directives.

---

### Post by Syntax13 on 2006-01-23
thank you all for replying, but the problem has been resolved. for some reason i have to write the linking after the file....it's strange because it wask working perfectly fine the other way originally (i saved the exact line into a text file after i got it working on the first day...and after i rebooted, that exact same line didn't work anymore *shrugs*). again, thank you for your replies.

---

