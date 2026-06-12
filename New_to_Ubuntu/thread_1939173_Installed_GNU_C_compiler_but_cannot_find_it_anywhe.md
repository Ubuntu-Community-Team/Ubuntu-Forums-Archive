---
title: "Installed GNU C compiler but cannot find it anywhere"
date: 2012-03-11
forum: New to Ubuntu
---

### Post by kiedis on 2012-03-11
Hi.

I installed gcc-4.5 package via Synaptic Manager but I cannot find C compiler anywhere in my system. How should I launch C compiler?

Thanks

---

### Post by Cheesemill on 2012-03-11
It's a text-based tool, it doesn't have a graphical interface.

Open a terminal and type
```
man gcc
```
for more info.

---

### Post by MG&amp;TL on 2012-03-11
GCC & co. (g++, gfortran, etc.) are all command-line compilers. That is, they do not have an interface, you launch them from the command-line.

Open a terminal, then cd to the folder with your C files. Then run:

```
gcc -o <name> <files>
```

Where <name> is what you want to call your executable, and <files> is your files.

---

### Post by kiedis on 2012-03-11
thank you for your replies!

but I don't quite understand what should i type in the terminal in order to launch C compiler. I located "gcc" and "gcc-4.5" files under /user/bin but what's the use of it? I typed for example **$ cd usr/bin/ gcc -0** but got **bash: cd: usr/bin/: No such file or directory** error.

do i need to move those files to some other directory or smth?

---

### Post by Cheesemill on 2012-03-11
> **kiedis said:**
> do i need to move those files to some other directory or smth?

No. Just follow MG&TL's instructions above.

Change directory to where the C files are that you wish to compile and type:
```
gcc -o <name> <files>
```

---

