---
title: "install tar.gz file format"
date: 2011-10-07
forum: New to Ubuntu
---

### Post by pmohankumar on 2011-10-07
Hi friends,

Iam using ubuntu 9.10.

How to install software file with extension tar.gz

---

### Post by cherva on 2011-10-07
You have to extract it first with:
```
tar -zxvf <FILE_NAME>
```
And the program probably came as a source code so read this:
[http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html]("http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html")

---

### Post by garvinrick4 on 2011-10-07
# 1: Uncompress tarball

To uncompress them, execute the following command(s) depending on the extension:
$ tar zxf file.tar.gz
$ tar zxf file.tgz
$ tar jxf file.tar.bz2
$ tar jxf file.tbz2

Now change directory
$ ls
$ cd path-to-software/

# 2: Build and install software

Generally you need to type 3 commands as follows for building and compiling software:
# ./configure
# make
# make install

Where,

    ./configure will configure the software to ensure your system has the necessary functionality and libraries to successfully compile the package
    make will compile all the source files into executable binaries.
    Finally, make install will install the binaries and any supporting files into the appropriate locations.

# 3: Read INSTALL / README file

Each tarball comes with installation and build instructions. Open INSTALL or README file for more information:

---

### Post by amjjawad on 2011-10-07
> **pmohankumar said:**
> Iam using ubuntu 9.10.

Why not go for newer version?
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

If your machine is old and has less than 1GB RAM, then go for [Lubuntu]("http://lubuntu.net/").

Sorry if this has nothing to do with what you are looking for :)

---

### Post by ClientAlive on 2011-10-07
For documentation on these utilites you can type the following commands into your terminal:

```

man gzip

```

And

```

man tar

```


Press the letter "q" to exit

---

