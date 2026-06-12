---
title: "What are plugins with &quot;debug symbols&quot;"
date: 2012-01-15
forum: New to Ubuntu
---

### Post by BudworthTDog on 2012-01-15
"Debug symbols" is such a common phrase in Linux that I found it almost impossible to find an answer for such a simple question. If there are two seemingly identical plugins for a program what is the general difference or idea behind having a regular one and one with a debug package? I have seen them several times but in this case I am referring to integrating Skype and pidgin with pidgin-skype or pidgin-skype-dbg

General rule of thumb I go without the dbg since I don't know what they are but just for kicks I would like to know the difference.

---

### Post by JKyleOKC on 2012-01-15
Normally the "dbg" versions include additional files that a debugging utility can use to produce more meaningful output. Because of this, they require more disk space. Usually they do not offer any difference in operation.

However, it's possible that a developer might produce a debugging version of a program that writes explicit operation logs, and indicate that version using the same convention. In this case the package would be somewhat slower than the non-debug version, because of the additional work it's doing, and also would consume growing amounts of disk space over time as the logs continued to grow.

Your practice of not selecting the debug versions is the correct choice for most folk. Only those interesting in contributing to development of the package, and able to use the additional information included, have any need for the debug editions. The situation is similar for "dev" packages, although the details of how they differ isn't quite the same. The "dev" packages include header files that would be required to rebuild the application, and may contain source as well.

---

