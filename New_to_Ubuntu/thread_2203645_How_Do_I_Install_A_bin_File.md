---
title: "How Do I Install A bin File"
date: 2014-02-04
forum: New to Ubuntu
---

### Post by JerryC on 2014-02-04
I downloaded the file "install-crossover-13.0.1.bin".  How do I install it?  I am running 12.04 LTS.  Need any more info?

JC

---

### Post by sandyd on 2014-02-04
Where is the file located?

You can install it by browsing to the file path in the terminal and running
```

chmod u+x install-crossover-13.0.1.bin
bash ./install-crossover-13.0.1.bin
```

---

### Post by TheFu on 2014-02-04
Usually there wold be a README or INSTALL file included with any programs to be installed. The instructions would be inside there. If you downloaded from a website, then the website might have instructions to be followed too.

Lacking that, I'd try **sh ./install-crossover-13.0.1.bin** from a terminal with the CWD set correctly.

However, it is a bad idea to install programs from outside the package manager ecosystem. Doing so means breaking dependencies and accepting responsibility to keep the program patched manually - you know - like the way _other_ operating systems do it.

Prefer to use the version of any programs from the default package manager locations.
Next, prefer to use a PPA from a trusted source.
After that, if you will make money from the software, perhaps, getting it from a commercial vendor is the only choice.
If I don't make money with the software, I won't install using anything outside the package manager, but that is just me.  You'll need to make your own decisions about that.

---

