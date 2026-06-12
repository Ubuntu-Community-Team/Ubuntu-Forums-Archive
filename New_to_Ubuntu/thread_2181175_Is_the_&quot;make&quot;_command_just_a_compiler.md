---
title: "Is the &quot;make&quot; command just a compiler"
date: 2013-10-16
forum: New to Ubuntu
---

### Post by adam20 on 2013-10-16
[HR][/HR]since it turns source code into objects?

---

### Post by hakermania on 2013-10-16
No. "make" is not a compiler. It calls compilers that build your code.

It is like you make a file named my_script.sh that calls gcc and compiles code. my_script.sh is not a compiler itself.

---

### Post by Impavidus on 2013-10-17
**make** is a program that reads a file called Makefile (where it can find rules and filenames), compares modification times of files (to know if the source code was modified after the last compilation) and runs specified commands (usually the compiler or linker). Projects using multiple source files (that is, anything non-trivial) usually use **make** to call a compiler and linker. Apart from programming, I sometimes use **make** in document typesetting.

---

### Post by tgalati4 on 2013-10-17
```
man make
```  will give you a detailed list of make's capabilities.

*Make* is just a small part of a much larger compilation process described here:  [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

