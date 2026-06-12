---
title: "how to use ls command in kernel module code?"
date: 2014-03-31
forum: Programming Talk
---

### Post by Muhammad_Nouman on 2014-03-31
I want to use the ls command from my module. I want to make a file in the directory and read the contents of that file in a module. When I tried to do this by run this command ls >> input.txt on terminal it works fine. But I want to use this command inside my kernel module code? HOw can I do this?

---

### Post by Dave_L on 2014-03-31
According to this discussion, you're not supposed to do that:
[https://www.linuxquestions.org/questions/linux-kernel-70/shell-command-from-a-linux-kernel-module-911004/](https://www.linuxquestions.org/questions/linux-kernel-70/shell-command-from-a-linux-kernel-module-911004/)

---

### Post by Toz on 2014-03-31
*Moved to **Programming Talk***.

---

### Post by ofnuts on 2014-04-01
In an ***application*** one uses the opendir()/readdir() functions. For kernel modules look at [this]("http://stackoverflow.com/questions/8347553/how-do-i-open-a-directory-at-kernel-level-using-the-file-descriptor-for-that-dir").

(but not knowing about this and writing kernel modules?)

---

### Post by SeijiSensei on 2014-04-01
I suspect you probably want to read files that may not yet be available during boot.  At boot, the kernel relies on a tiny filesystem stored in [initrd]("http://en.wikipedia.org/wiki/Initrd") since during the boot process the main root filesystem is not yet mounted.  In addition, on any classical Unix system, some portions of the filesystem like /usr, /var, and /home need not be available until the system goes multi-user.  Most contemporary Linux distributions usually build a single filesystem, but that is not required.  I've built servers where /home and /var are on separate partitions, and one once with /usr on a separate partition as well.  Putting /tmp on a separate filesystem marked with noexec is also a common practice.

---

