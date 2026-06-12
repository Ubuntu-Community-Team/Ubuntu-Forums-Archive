---
title: "install java6 in root"
date: 2007-10-23
forum: Programming Talk
---

### Post by yolloms on 2007-10-23
i downloaded the file "jdk-6u3-linux-i586.bin"

then did
         $ chmod +x jdk-6u3-linux-i586.bin
         $  ./jdk-6u3-linux-i586.bin

my problen is its not in the root directory so is not available on all levels.
I want to be able to use it when i use Eclipse n other IDE's

How do i move it to the root files

---

### Post by kaamos on 2007-10-23
Always install software from the repositories when possible. In this case the package you want is _sun-java6-jdk_. That installs the jdk to /usr/lib/jvm/java-6-sun and it is usable by all users and programs.

---

