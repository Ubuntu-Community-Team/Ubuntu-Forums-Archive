---
title: "Help compiling Molscript"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by evilkastel on 2008-10-23
hello, i need someone to please help me to compile MolScript, because i need to render chemical estructures in 3d. I'm in ubuntu 64 hardy, but i don't know how to. And the manpage for the program is for way more advanced users. thanx already.

---

### Post by rockerphil on 2008-10-23
first and foremost make sure you've got the package "build-essential" installed. without it you won't be able to compile any programs from source. this can be installed either through Synaptic or via the command line with:

```
sudo apt-get install build-essential
```

then of course you'll need to download the tarball (tar archive file) containing the source code for the program and decompress the tarball using file-roller. typically you'll find some type of "readme" file inside the unarchived file. hope this info helps,

Phil

---

### Post by evilkastel on 2008-10-23
Thanx phil, I do have build-essential and the tarball decompressed. Also, since this program is for UNIX, it has no GNU/Linux or Ubuntu native instructions on line, and has no readme. So that's why I need help.

---

### Post by Sarmacid on 2008-10-23
Usually to compile something you have to go to the directory where you decompressed it and run

```
./configure
make
sudo make install
```

---

### Post by rockerphil on 2008-10-23
> **Sarmacid said:**
> Usually to compile something you have to go to the directory where you decompressed it and run

```
./configure
make
sudo make install
```

yup, that's the basics. but just in case i've also seen:

```
./configure
make
make clean install
```

it really just depends on the program you're compiling, hope this helps,

Phil

---

