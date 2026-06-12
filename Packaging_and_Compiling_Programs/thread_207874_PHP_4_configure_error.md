---
title: "PHP 4 configure error"
date: 2006-07-02
forum: Packaging and Compiling Programs
---

### Post by mssever on 2006-07-02
I didn't know about this forum when I posted the following thread: [http://www.ubuntuforums.org/showthread.php?t=207590](http://www.ubuntuforums.org/showthread.php?t=207590)

Trying to compile PHP4:
```
./configure --prefix=/usr/local/php4 --with-mysql --with-apxs2=/opt/apache2/bin/apxs

<snip>

checking for gawk... no
checking for mawk... mawk
checking for bison... bison -y
checking bison version... configure: warning: You will need bison 1.28
2.1 (ok)
checking for flex... lex
checking for yywrap in -ll... no
checking lex output file root... ./configure: line 2540: lex: command not found
configure: error: cannot find output from lex; giving up
```
What package(s) am I missing?

---

### Post by maddog39 on 2006-11-25
I have the same exact problem compiling PHP 5.2.0
```

maddog39@maddog39-desktop:~$ cd '/home/maddog39/Desktop/php-5.2.0' ]
maddog39@maddog39-desktop:~/Desktop/php-5.2.0$ ./configure
creating cache ./config.cache
checking for Cygwin environment... no
checking for mingw32 environment... no
checking for egrep... grep -E
checking for a sed that does not truncate output... /bin/sed
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking whether gcc and cc understand -c and -o together... yes
checking how to run the C preprocessor... gcc -E
checking for AIX... no
checking whether ln -s works... yes
checking if compiler supports -R... no
checking if compiler supports -Wl,-rpath,... yes
checking for re2c... no
configure: warning: You will need re2c 0.9.11 or later if you want to regenerate PHP parsers.
checking for gawk... no
checking for nawk... nawk
checking if nawk is broken... no
checking for bison... no
checking for byacc... no
checking for bison version... invalid
configure: warning: bison versions supported for regeneration of the Zend/PHP parsers: 1.28 1.35 1.75 1.875 2.0 2.1 2.2 2.3 (found: none).
checking for flex... lex
checking for yywrap in -ll... no
checking lex output file root... ./configure: 1: lex: not found
configure: error: cannot find output from lex; giving up

```

---

### Post by mssever on 2006-11-25
> **maddog39 said:**
> I have the same exact problem compiling PHP 5.2.0
```

maddog39@maddog39-desktop:~$ cd '/home/maddog39/Desktop/php-5.2.0' ]
maddog39@maddog39-desktop:~/Desktop/php-5.2.0$ ./configure
creating cache ./config.cache
checking for Cygwin environment... no
checking for mingw32 environment... no
checking for egrep... grep -E
checking for a sed that does not truncate output... /bin/sed
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking whether gcc and cc understand -c and -o together... yes
checking how to run the C preprocessor... gcc -E
checking for AIX... no
checking whether ln -s works... yes
checking if compiler supports -R... no
checking if compiler supports -Wl,-rpath,... yes
checking for re2c... no
configure: warning: You will need re2c 0.9.11 or later if you want to regenerate PHP parsers.
checking for gawk... no
checking for nawk... nawk
checking if nawk is broken... no
checking for bison... no
checking for byacc... no
checking for bison version... invalid
configure: warning: bison versions supported for regeneration of the Zend/PHP parsers: 1.28 1.35 1.75 1.875 2.0 2.1 2.2 2.3 (found: none).
checking for flex... lex
checking for yywrap in -ll... no
checking lex output file root... ./configure: 1: lex: not found
configure: error: cannot find output from lex; giving up

```
You need to install flex for sure and likely bison as well.

---

