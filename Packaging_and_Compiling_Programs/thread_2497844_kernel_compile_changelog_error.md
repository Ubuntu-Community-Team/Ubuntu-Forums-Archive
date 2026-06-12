---
title: "kernel compile changelog error"
date: 2024-05-20
forum: Packaging and Compiling Programs
---

### Post by rolfbruge on 2024-05-20
After numerous previous kernel compiles without problems, ran into this recent error.  Anyone had this problem recently, and if so what does it mean?

```
sudo make bindeb-pkg -j2
  SYNC    include/config/auto.conf.cmd
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/kconfig/conf.o
  HOSTCC  scripts/kconfig/confdata.o
  HOSTCC  scripts/kconfig/expr.o
  LEX     scripts/kconfig/lexer.lex.c
  YACC    scripts/kconfig/parser.tab.[ch]
  HOSTCC  scripts/kconfig/menu.o
  HOSTCC  scripts/kconfig/preprocess.o
  HOSTCC  scripts/kconfig/symbol.o
  HOSTCC  scripts/kconfig/util.o
  HOSTCC  scripts/kconfig/lexer.lex.o
  HOSTCC  scripts/kconfig/parser.tab.o
  HOSTLD  scripts/kconfig/conf
  GEN     debian
dpkg-buildpackage --build=binary --no-pre-clean --unsigned-changes -R'make -f debian/rules' -j1 -a$(cat debian/arch)
dpkg-buildpackage: warning:     debian/changelog(l2): found end of file where expected first heading
dpkg-buildpackage: error: fatal error occurred while parsing debian/changelog
make[2]: *** [scripts/Makefile.package:121: bindeb-pkg] Error 255
make[1]: *** [/media/Ext2/kernel/linux-6.9.1/Makefile:1541: bindeb-pkg] Error 2
make: *** [Makefile:240: __sub-make] Error 2
```

changelog info:

```
linux-upstream (6.9.1-5) urgency=low

  * Custom built Linux kernel.

 -- root <root@user>  Sun, 19 May 2024 21:43:27 -0300
```

---

### Post by &amp;KyT$0P# on 2024-05-20
That changelog info is missing the distribution and following semicolon -
```
linux-upstream (6.9.1-5) [COLOR="#FF0000"]DISTRIBUTION;[/COLOR] urgency=low

  * Custom built Linux kernel.

 -- root <root@user>  Sun, 19 May 2024 21:43:27 -0300
```

In place of [COLOR="#FF0000"]DISTRIBUTION[/COLOR] put the output from running
```
lsb_release -cs
```

For more info see [Debian policy manual]("https://www.debian.org/doc/debian-policy/ch-source.html#debian-changelog-debian-changelog")

---

