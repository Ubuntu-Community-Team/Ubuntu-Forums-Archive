---
title: "Compiling Vim with Netbeans flag enabled"
date: 2009-05-04
forum: Programming Talk
---

### Post by melopsittacus on 2009-05-04
Hello!

I would need to achieve what is mentioned in the title in order to later install Vimpugin (a plugin for Eclipse which lets you use the key combinations like in Vim -- see here [http://vimplugin.org/](http://vimplugin.org/)).

In order to achieve this, a version of Vim compiled with Netbeans Integration is required, which the version available in the Ubuntu (Hardy) repository lacks.
Thus I have downloaded the original Vim source (version 7.2 from here: [ftp://ftp.vim.org/pub/vim/unix/vim-7.2.tar.bz2](ftp://ftp.vim.org/pub/vim/unix/vim-7.2.tar.bz2)) and compiled it ```
./configure && make
```
Vim manual states ([http://www.vim.org/htmldoc/netbeans.html#netbeans-configure](http://www.vim.org/htmldoc/netbeans.html#netbeans-configure)) that Netbeans is enabled by default, and it must be explicitly disabled if you do not need it.

However, after compilation, I have checked if that feature is enabled using 
```
./vim --version # make sure to run the just compiled editor not the one installed on the system
```
and as part of the output I still see
```
-netbeans_intg
```
meaning that Netbeans feature has not been enabled after all.

I also checked the configure log (auto/config.log), and the relevant lines seemed all right:

```
configure:5816: checking --disable-netbeans argument
configure:5826: result: no
configure:5978: checking whether compiling netbeans integration is possible
configure:6024: gcc -o conftest -g -O2   -L/usr/local/lib conftest.c -lnsl       >&5
configure:6031: $? = 0
configure:6039: result: yes

```

The generated auto/config.h also seems to be right:

```
/* Define if you want to include NetBeans integration. */
/* #undef FEAT_NETBEANS_INTG */

```

So I really do not know where the compilation can have gone wrong. If anyone has experience with this feature, I would really be glad for some help.

Thanks,

melopsittacus

---

