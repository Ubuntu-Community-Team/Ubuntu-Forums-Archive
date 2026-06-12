---
title: "Can't get PDO_IBM"
date: 2007-11-20
forum: Programming Talk
---

### Post by Archasm on 2007-11-20
I am running 7.10, Apache2 and PHP5 which comes with the PDO enabled for MySQL only. 

I apt-getted php-pear and have tried to install PDO_IBM using pecl install PDO_IBM but it comes back with

pear/PDO_IBM requires package "pear/PDO"

I have tried installing PDO using pecl install which worked, but still it throws this message. I can't work out, if PDO is meant to be enabled in PHP5, why they have not given an easy way to get hold of the drivers!!!

Cheers

---

### Post by cookie@zeno.pl on 2009-07-22
I have the same problem. I tried install pdo_ibm extension and I obtained the error:

pear/PDO_IBM requires package "pear/PDO"

I don't understand why pecl throws me this error, because I have already installed PDO using command:

pecl install pdo

and command *pecl list* shows me:

PDO     1.0.3   stable

Does anybody know what I should do to install properly this ext?

// I forgot: I'm running on ubuntu 9.04, apache 2.2, php5.2.6

---

### Post by Regbuntu on 2010-02-09
This worked for me:
1. Download the latest PDO IBM driver file from [http://pecl.php.net/package/PDO_IBM](http://pecl.php.net/package/PDO_IBM) 
    EX: PDO_IBM-1.3.1.tgz
2. Untar the file: tar -xvf PDO_IBM-1.3.1.tgz
3. Go to the main directory (directory that contains the config.m4 file)
4. Execute 'phpize' and that creates several files. Note: must have php5-dev installed ( sudo apt-get install php5-dev )for phpize to run.
5. There is a bug in the configure script. It can't find necessary header files, so you have to put them in the correct directory.
    - Create the following folder structure: php/ext/pdo/ in the PDO_IBM-1.3.1/include/ directory
    - Copy all the *.h files from /usr/include/php5/ext/pdo to the new pdo directory you just created above
6. Execute './configure --with-pdo-ibm=/home/db2inst1/sqllib'
7. Execute 'make'
8. Execute 'sudo make install'
9. Modify the /etc/apache2/php.ini file in order to activate the pdo_ibm.so extension.
    extension=pdo_ibm.so
10. Restart Apache.

---

### Post by kdford on 2010-08-03
Hi,

I am trying to install PDO_IBM extension for PHP in my Ubuntu 10.4 machine.  I seem to have PDO configured for mysql (by what phpinfo tells me), but when I try to do
```
sudo pecl install pdo_ibm
```it tells me I need to have PDO installed.

So I run
```
sudo pecl install pdo
```and it comes back with a bunch of output, with some erros at the end that I don't understand.  Output below...  Any help would be appreciated.  I have, by the way, already installed and successfully tested the ibm_db2 driver with my php/apache setup.

```
downloading PDO-1.0.3.tgz ...
Starting to download PDO-1.0.3.tgz (52,613 bytes)
.............done: 52,613 bytes
12 source files, building
running: phpize
Configuring for:
PHP Api Version:         20090626
Zend Module Api No:      20090626
Zend Extension Api No:   220090626
building in /var/tmp/pear-build-root/PDO-1.0.3
running: /tmp/pear/temp/PDO/configure
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for a sed that does not truncate output... /bin/sed
checking for cc... cc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables...
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether cc accepts -g... yes
checking for cc option to accept ISO C89... none needed
checking how to run the C preprocessor... cc -E
checking for icc... no
checking for suncc... no
checking whether cc understands -c and -o together... yes
checking for system library directory... lib
checking if compiler supports -R... no
checking if compiler supports -Wl,-rpath,... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for PHP prefix... /usr
checking for PHP includes... -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
checking for PHP extension directory... /usr/lib/php5/20090626+lfs
checking for PHP installed headers prefix... /usr/include/php5
checking if debug is enabled... no
checking if zts is enabled... no
checking for re2c... no
configure: WARNING: You will need re2c 0.13.4 or later if you want to regenerate PHP parsers.
checking for gawk... no
checking for nawk... nawk
checking if nawk is broken... no
checking whether to enable PDO support... yes, shared
checking for a sed that does not truncate output... (cached) /bin/sed
checking for fgrep... /bin/grep -F
checking for ld used by cc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from cc object... ok
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for dlfcn.h... yes
checking for objdir... .libs
checking if cc supports -fno-rtti -fno-exceptions... no
checking for cc option to produce PIC... -fPIC -DPIC
checking if cc PIC flag -fPIC -DPIC works... yes
checking if cc static flag -static works... yes
checking if cc supports -c -o file.o... yes
checking if cc supports -c -o file.o... (cached) yes
checking whether the cc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating ./config.status
config.status: creating config.h
config.status: executing libtool commands
running: make
/bin/bash /var/tmp/pear-build-root/PDO-1.0.3/libtool --mode=compile cc  -I. -I/tmp/pear/temp/PDO -DPHP_ATOM_INC -I/var/tmp/pear-build-root/PDO-1.0.3/include -I/var/tmp/pear-build-root/PDO-1.0.3/main -I/tmp/pear/temp/PDO -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -DHAVE_CONFIG_H  -g -O2   -c /tmp/pear/temp/PDO/pdo.c -o pdo.lo
libtool: compile:  cc -I. -I/tmp/pear/temp/PDO -DPHP_ATOM_INC -I/var/tmp/pear-build-root/PDO-1.0.3/include -I/var/tmp/pear-build-root/PDO-1.0.3/main -I/tmp/pear/temp/PDO -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -DHAVE_CONFIG_H -g -O2 -c /tmp/pear/temp/PDO/pdo.c  -fPIC -DPIC -o .libs/pdo.o
/bin/bash /var/tmp/pear-build-root/PDO-1.0.3/libtool --mode=compile cc  -I. -I/tmp/pear/temp/PDO -DPHP_ATOM_INC -I/var/tmp/pear-build-root/PDO-1.0.3/include -I/var/tmp/pear-build-root/PDO-1.0.3/main -I/tmp/pear/temp/PDO -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -DHAVE_CONFIG_H  -g -O2   -c /tmp/pear/temp/PDO/pdo_dbh.c -o pdo_dbh.lo
libtool: compile:  cc -I. -I/tmp/pear/temp/PDO -DPHP_ATOM_INC -I/var/tmp/pear-build-root/PDO-1.0.3/include -I/var/tmp/pear-build-root/PDO-1.0.3/main -I/tmp/pear/temp/PDO -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -DHAVE_CONFIG_H -g -O2 -c /tmp/pear/temp/PDO/pdo_dbh.c  -fPIC -DPIC -o .libs/pdo_dbh.o
/tmp/pear/temp/PDO/pdo_dbh.c: In function ‘pdo_stmt_instantiate’:
/tmp/pear/temp/PDO/pdo_dbh.c:410: error: ‘zval’ has no member named ‘refcount’
/tmp/pear/temp/PDO/pdo_dbh.c:411: error: ‘zval’ has no member named ‘is_ref’
/tmp/pear/temp/PDO/pdo_dbh.c: In function ‘pdo_stmt_construct’:
/tmp/pear/temp/PDO/pdo_dbh.c:435: error: ‘zend_fcall_info’ has no member named ‘object_pp’
/tmp/pear/temp/PDO/pdo_dbh.c:458: error: ‘zend_fcall_info_cache’ has no member named ‘object_pp’
/tmp/pear/temp/PDO/pdo_dbh.c: In function ‘zim_PDO_setAttribute’:
/tmp/pear/temp/PDO/pdo_dbh.c:752: error: ‘zval’ has no member named ‘refcount’
/tmp/pear/temp/PDO/pdo_dbh.c: In function ‘zim_PDO_getAttribute’:
/tmp/pear/temp/PDO/pdo_dbh.c:818: error: ‘zval’ has no member named ‘refcount’
/tmp/pear/temp/PDO/pdo_dbh.c: In function ‘pdo_hash_methods’:
/tmp/pear/temp/PDO/pdo_dbh.c:1122: warning: assignment discards qualifiers from pointer target type
/tmp/pear/temp/PDO/pdo_dbh.c:1126: warning: assignment discards qualifiers from pointer target type
make: *** [pdo_dbh.lo] Error 1
ERROR: `make' failed
```

---

