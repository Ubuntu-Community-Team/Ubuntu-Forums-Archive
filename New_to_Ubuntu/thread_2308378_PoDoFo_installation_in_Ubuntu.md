---
title: "PoDoFo installation in Ubuntu"
date: 2016-01-02
forum: New to Ubuntu
---

### Post by Balbir_Kumar on 2016-01-02
[COLOR=#222426][FONT=Arial]I compile and installed PoDoFo in Ubuntu. But /usr/include and /usr/lib doesn't have any entry. I need it to work with my programs. Could you please let me know by default where the header file and lib files are installed? And how I can install them in /usr/include and /usr/lib?[/FONT][/COLOR]

---

### Post by oldos2er on 2016-01-03
I'm guessing they were installed to /usr/local/include/and /usr/local/lib/ which is where compiled apps usually go.

---

### Post by sandyd on 2016-01-03
> **Balbir_Kumar said:**
> [COLOR=#222426][FONT=Arial]I compile and installed PoDoFo in Ubuntu. But /usr/include and /usr/lib doesn't have any entry. I need it to work with my programs. Could you please let me know by default where the header file and lib files are installed? And how I can install them in /usr/include and /usr/lib?[/FONT][/COLOR]

When installing from source, most applications will use a "./configure" script to configure the build/install steps. When installing, applications/libraries/etc will use what is called the "prefix" to determine where to install an application. For example, if the library has to install libraries that go in the lib folder, it will install to <prefix>/lib unless an alternate directory has been specified. Alternate directories can be set for just the prefix, or specific sections of the installation such as libraries and manuals.

With configure, you can override the default prefix by adding "--prefix=/path/i/choose"

For example:
```

./configure --prefix=/opt/podofo
```
Will install podofo to /opt/podofo. There will be folders created for the lib/manual/etc.

Generally when installing compiled applications, it is best to set a alternate prefix which is not "/usr/", which is where most libraries and software are installed. This reduces the risk of filename conflicts/etc.

By default, most developers use "/usr/local", you can probably try searching /usr/local/lib for the library.

Note that the above only applies to applications installed using "./configure" and not cmake or other.

---

### Post by Balbir_Kumar on 2016-01-04
There is no entry for PoDoFo in /usr/local/include & /usr/local/lib. Also we used to install PoDoFo using cmake or ccmake.

---

