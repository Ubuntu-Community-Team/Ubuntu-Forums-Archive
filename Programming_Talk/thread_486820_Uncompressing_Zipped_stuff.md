---
title: "Uncompressing Zipped stuff"
date: 2007-06-28
forum: Programming Talk
---

### Post by FlyingIsFun1217 on 2007-06-28
Hey!

I know that you can use the terminal to unzip files. How can I translate this into a C++ program? It would be nice if I didn't have to use a library to unzip files (.zip's, .tar's, .tar.gz's).

Is there a fast way of going around this?

Thanks!
FlyingIsFun1217

---

### Post by Ramses de Norre on 2007-06-28
I'm not a c programmer, but I think you can issue **system("command");** or something like that in c. It'll return an int, being zero if the command was successful and a non zero value if an error occurred.

---

### Post by Paul Miller on 2007-06-28
As the previous post said, you can use the system() function to call gzip or whatever, assuming that meets your requirements.  The other simple way to go about it is to link against zlib.  Google zlib and you should find all the info you need on how to use it.  It's quite widely available in most (if not all) current Linuxes.

---

### Post by FlyingIsFun1217 on 2007-06-28
Cool, system("<command>") executes <command as if it were in a terminal?

If so, what should I link against for this?

Thanks!
FlyingIsFun1217

---

### Post by FlyingIsFun1217 on 2007-06-28
Seems that [this]("http://www.phim.unibe.ch/comp_doc/c_manual/C/FUNCTIONS/system.html") site explains it some more.

I'll post here again if need be.

Thanks so much!
FlyingIsFun1217

---

### Post by avik on 2007-06-28
> **FlyingIsFun1217 said:**
> Cool, system("<command>") executes <command as if it were in a terminal?

If so, what should I link against for this?

You don't have to link anything, as system is part of stdlib.

---

