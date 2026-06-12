---
title: "Eclipse 3.3 content assist misbehaving"
date: 2007-10-10
forum: Programming Talk
---

### Post by framebuffer on 2007-10-10
Hello!,

I just installed and tested Eclipse 3.3 with CDT 4. Here are the precise info:

CDT
Version: 4.0.1.200709241202
Build id: 200709241202

Eclipse SDK
Version: 3.3.0.v20070607-7M7J-BIolz-OcxWxvWAPSfLPqevO
Build id: I20070625-1500

I successfully compiled a "hello world!" program.

Content assist is not working though. I tried restarting the IDE but it didn't solve the problem. I can get it to work from the right click menu, but it does not work otherwise.

I am using Ubuntu 7.04, updated.

Other shortcuts are working though, for example, ctrl+shift+f for formatting and ctrl+/ for commenting. The only thing that is not working is ctrl+space.

Ironically, when i type std::{ctrl+space} it works!

Also, If I declare a class and access its members, it works.

If on the other hand I declare a variable and try to complete its name it does not work.

For example:

class Test
{
public:

int Number;
};

If I type Te{It wont work}
but

Test foo;
foo.{works}

Please help.

---

### Post by aitorcalero on 2007-10-11
Are you using sun java sdk package or gcj instead? Just type ```
java -version
``` in a terminal to know. If it is the second case you will find a lot of problems, so I recommend you to install sun java sdk package:
```
sudo aptitude install sun-java5-jdk
``` for java5

---

### Post by framebuffer on 2007-10-12
I am using sun java 6 package and i have also set linux to use this. Also, if it helps, I have not installed eclipse in the 'bin' directory. Its in my home.

---

### Post by xangor on 2011-04-29
Did yo solve the problem, as I have the same issue. 

Eclipse IDE for C/C++ Linux Developers

Version: Helios Service Release 2
Build id: 20110218-0911


java version "1.6.0_20"
OpenJDK Runtime Environment (IcedTea6 1.9.7) (6b20-1.9.7-0ubuntu1)
OpenJDK Server VM (build 19.0-b09, mixed mode)


The content assist works for :: . -> 
but when I press CTRL+space finishing variable / function name the Eclipse freezes.

Xangor

Hmm I also have today installed Firefox 4 with its libxul.so (I do not have package xulrunner installed) and I have still the same issue.

---

