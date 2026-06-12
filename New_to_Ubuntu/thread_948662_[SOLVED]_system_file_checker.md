---
title: "[SOLVED] system file checker"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by melrokz on 2008-10-15
May i know: What is the equivalent of windows system file checker```
sfc /scannow
```in Ubuntu 7.10?

---

### Post by bumanie on 2008-10-15
fsck is the linux filesystem checker. It is not so important (unless there is something obviously wrong) to routinely run it, as it checks your filesystem every thirty boots, which is a default setting. In terminal type > man fsck for more information on fsck, also google is a good resource to find out more.

---

### Post by Therion on 2008-10-15
There really isn't a directly corresponding application or command for Linux because Linux-based distros don't need one.  Linux is not self-imploding like Windows is.

By default the command ***fsck*** runs every 30th boot and checks for system integrity, but that's an entirely different sort of thing than running SFC (System File Check) under Windows. 

Linux is not Windows and is not built like Windows, hence many of the problems and issues that Windows has are not to be found in the Linux environment.

---

