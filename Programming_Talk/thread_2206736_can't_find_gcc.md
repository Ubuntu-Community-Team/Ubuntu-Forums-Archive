---
title: "can't find gcc"
date: 2014-02-20
forum: Programming Talk
---

### Post by dapps2 on 2014-02-20
I am running Lubuntu 13.10 and have installed "gcc" via the command line but like a fool i can't find where it is located. Help anyone please.

---

### Post by Lars Noodén on 2014-02-20
You should be able to find it with 'which'

```

which gcc

```

If it is installed, then that should show where.  If it gives no answer, double check what you have.

```

apt-cache policy gcc

```

Check the output where it says 'Installed:' to see which version you have installed or if it is yet to be installed.

---

### Post by SeijiSensei on 2014-02-20
If you plan on compiling software to run on Linux, gcc alone is not sufficient.  I suggest you start by running "sudo apt-get install build-essential" to get the standard development environment.  I also recommend reading this: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

Like most executable binaries, gcc is stored in /usr/bin.  However on my 14.04 system, it is actually a symbolic link to gcc-4.8 which is the actual executable.

---

### Post by dapps2 on 2014-02-20
Finally, found it! which gcc = /usr/bin/gcc
Thanks for the help guys + the link

---

