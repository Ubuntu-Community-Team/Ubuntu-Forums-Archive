---
title: "[SOLVED] Problem with exports"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by vale1286 on 2008-05-12
Hi all. I have the need to run a program for my thesys but I've encountered a little problem...

In the program's installation guide it says I should type these commands to configure the program ("root" is the program name, and <path> is the path where I extracted the program)

```
export ROOTSYS=<path>/root

```

```
 ./configure --help
        ./configure [<arch>]      [set arch appropriately if not default]
        (g)make                   [or, make -j2 for dual CPU machines]

```

```
 setenv PATH ${ROOTSYS}/bin:${PATH}
        setenv LD_LIBRARY_PATH ${ROOTSYS}/lib:${LD_LIBRARY_PATH}

```

First of all I get an error while typing the second list of commands. Second thing: if I run the program it all works, but if I close and reopen the terminal and try to run the program again it doesn't work and I have to retype all the commands above in order to get it to work, how can I avoid to retype those commands every time?

Thank you all

---

### Post by vale1286 on 2008-05-12
bump

---

### Post by SunnyRabbiera on 2008-05-12
well if you are trying to install this into your core, you need to enter into sudo mode to get root/administrative access.

---

### Post by Monicker on 2008-05-12
> **vale1286 said:**
> Hi all. I have the need to run a program for my thesys but I've encountered a little problem...

In the program's installation guide it says I should type these commands to configure the program ("root" is the program name, and <path> is the path where I extracted the program)

```
export ROOTSYS=<path>/root

```

```
 ./configure --help
        ./configure [<arch>]      [set arch appropriately if not default]
        (g)make                   [or, make -j2 for dual CPU machines]

```

```
 setenv PATH ${ROOTSYS}/bin:${PATH}
        setenv LD_LIBRARY_PATH ${ROOTSYS}/lib:${LD_LIBRARY_PATH}

```

First of all I get an error while typing the second list of commands. Second thing: if I run the program it all works, but if I close and reopen the terminal and try to run the program again it doesn't work and I have to retype all the commands above in order to get it to work, how can I avoid to retype those commands every time?

Thank you all

You could put the export in /etc/profile, or do it at the user level by putting it in /home/username/.bash_profie (you may have to create this file).

---

