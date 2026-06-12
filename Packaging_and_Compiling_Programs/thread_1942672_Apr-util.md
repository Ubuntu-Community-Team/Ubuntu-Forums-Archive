---
title: "Apr-util"
date: 2012-03-18
forum: Packaging and Compiling Programs
---

### Post by AADAS on 2012-03-18
Why I cant install APR-util.
```
root@ubuntu:/apr-util-1.4.1# ./configure --prefix=/usr/local/apr-util --with-apr=/usr/local/apr/
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for working mkdir -p... yes
APR-util Version: 1.4.1
checking for chosen layout... apr-util
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
Applying apr-util hints file rules for i686-pc-linux-gnu
checking for APR... yes
  setting CPP to "gcc -E"
  adding "-Wall" to CFLAGS
  adding "-pg" to CFLAGS
  adding "-pthread" to CFLAGS
  setting CPPFLAGS to " -D_REENTRANT -D_GNU_SOURCE -D_LARGEFILE64_SOURCE"
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking for ldap support...
checking for default DBM... sdbm (default)
checking for pg_config... no
checking libpq-fe.h usability... no
checking libpq-fe.h presence... no
checking for libpq-fe.h... no
checking postgresql/libpq-fe.h usability... no
checking postgresql/libpq-fe.h presence... no
checking for postgresql/libpq-fe.h... no
checking sqlite3.h usability... no
checking sqlite3.h presence... no
checking for sqlite3.h... no
checking sqlite.h usability... no
checking sqlite.h presence... no
checking for sqlite.h... no
checking sybdb.h usability... no
checking sybdb.h presence... no
checking for sybdb.h... no
checking freetds/sybdb.h usability... no
checking freetds/sybdb.h presence... no
checking for freetds/sybdb.h... no
checking for odbc_config... no
checking sql.h usability... no
checking sql.h presence... no
checking for sql.h... no
checking odbc/sql.h usability... no
checking odbc/sql.h presence... no
checking for odbc/sql.h... no
checking Expat 1.95.x... no
checking old Debian-packaged expat... no
checking old FreeBSD-packaged expat... no
checking Expat 1.0/1.1... no
  setting LDFLAGS to "-L/usr/local/lib"
  adding "-I/usr/local/include" to CPPFLAGS
checking Expat 1.95.x in /usr/local... no
  nulling LDFLAGS
  removed "-I/usr/local/include" from CPPFLAGS
configuring package in xml/expat now
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking how to run the C preprocessor... gcc -E
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
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking for ANSI C header files... (cached) yes
checking whether byte ordering is bigendian... no
checking for an ANSI C-conforming const... yes
checking for size_t... yes
checking for memmove... yes
checking for bcopy... yes
checking check.h usability... no
checking check.h presence... no
checking for check.h... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating expat_config.h
config.status: expat_config.h is unchanged
config.status: executing libtool commands
xml/expat configured properly
  setting APRUTIL_INCLUDES to "-I/apr-util-1.4.1/xml/expat/lib"
  setting LDFLAGS to "-L/apr-util-1.4.1/xml/expat/lib"
  setting APRUTIL_EXPORT_LIBS to "/apr-util-1.4.1/xml/expat/libexpat.la"
  setting APRUTIL_LIBS to "/apr-util-1.4.1/xml/expat/libexpat.la"
checking iconv.h usability... yes
checking iconv.h presence... yes
checking for iconv.h... yes
checking for type of inbuf parameter to iconv... char **
checking for iconv.h... (cached) yes
checking langinfo.h usability... yes
checking langinfo.h presence... yes
checking for langinfo.h... yes
checking for nl_langinfo... yes
checking for CODESET in langinfo.h... yes
checking whether APR has DSO support... yes
checking for library containing crypt... -lcrypt
checking if system crypt() function is threadsafe... no
checking for crypt_r... yes
checking style of crypt_r... struct_crypt_data
  adding "/usr/local/apr/lib/libapr-1.la" to APRUTIL_LIBS
  adding "-lrt" to APRUTIL_LIBS
  adding "-lcrypt" to APRUTIL_LIBS
  adding "-lpthread" to APRUTIL_LIBS
  adding "-ldl" to APRUTIL_LIBS
configure: creating ./config.status
config.status: creating Makefile
config.status: creating export_vars.sh
config.status: creating build/pkg/pkginfo
config.status: creating apr-util.pc
config.status: creating apu-1-config
config.status: creating include/private/apu_select_dbm.h
config.status: creating include/apr_ldap.h
config.status: creating include/apu.h
config.status: creating include/apu_want.h
config.status: creating test/Makefile
config.status: creating include/private/apu_config.h
config.status: include/private/apu_config.h is unchanged
config.status: executing default commandsroot@ubuntu:/apr-util-1.4.1# make
Making all in xml/expat
make[1]: Entering directory `/apr-util-1.4.1/xml/expat'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/apr-util-1.4.1/xml/expat'
make[1]: Entering directory `/apr-util-1.4.1'
sed 's,^\(location=\).*$,\1installed,' < apu-1-config > apu-config.out
make[1]: Leaving directory `/apr-util-1.4.1'
root@ubuntu:/apr-util-1.4.1# make install
Making all in xml/expat
make[1]: Entering directory `/apr-util-1.4.1/xml/expat'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/apr-util-1.4.1/xml/expat'
make[1]: Entering directory `/apr-util-1.4.1'
make[1]: Nothing to be done for `local-all'.
make[1]: Leaving directory `/apr-util-1.4.1'
/usr/local/apr/build-1/mkdir.sh /usr/local/apr-util/include/apr-1 /usr/local/apr-util/lib/pkgconfig \
             /usr/local/apr-util/lib /usr/local/apr-util/bin
for f in /apr-util-1.4.1/include/*.h /apr-util-1.4.1/include/*.h; do \
        /usr/bin/install -c -m 644 ${f} /usr/local/apr-util/include/apr-1; \
    done
/usr/bin/install -c -m 644 apr-util.pc /usr/local/apr-util/lib/pkgconfig/apr-util-1.pc
list='xml/expat'; for i in $list; do \
        ( cd $i ; make DESTDIR= install ); \
    done
make[1]: Entering directory `/apr-util-1.4.1/xml/expat'
/bin/bash ./conftools/mkinstalldirs /usr/local/apr-util/lib /usr/local/apr-util/include/apr-1
/bin/bash ./libtool  --mode=install /usr/bin/install -c libexpat.la /usr/local/apr-util/lib/libexpat.la
libtool: install: /usr/bin/install -c .libs/libexpat.so.0.5.0 /usr/local/apr-util/lib/libexpat.so.0.5.0
libtool: install: (cd /usr/local/apr-util/lib && { ln -s -f libexpat.so.0.5.0 libexpat.so.0 || { rm -f libexpat.so.0 && ln -s libexpat.so.0.5.0 libexpat.so.0; }; })
libtool: install: (cd /usr/local/apr-util/lib && { ln -s -f libexpat.so.0.5.0 libexpat.so || { rm -f libexpat.so && ln -s libexpat.so.0.5.0 libexpat.so; }; })
libtool: install: /usr/bin/install -c .libs/libexpat.lai /usr/local/apr-util/lib/libexpat.la
libtool: install: /usr/bin/install -c .libs/libexpat.a /usr/local/apr-util/lib/libexpat.a
libtool: install: chmod 644 /usr/local/apr-util/lib/libexpat.a
libtool: install: ranlib /usr/local/apr-util/lib/libexpat.a
libtool: finish: PATH="/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/sbin" ldconfig -n /usr/local/apr-util/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/apr-util/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
/usr/bin/install -c -m 644 ./lib/expat.h /usr/local/apr-util/include/apr-1
make[1]: Leaving directory `/apr-util-1.4.1/xml/expat'
/bin/bash /usr/local/apr/build-1/libtool --mode=install /usr/bin/install -c -m 755 libaprutil-1.la /usr/local/apr-util/lib
libtool: install: warning: relinking `libaprutil-1.la'
libtool: install: (cd /apr-util-1.4.1; /bin/bash /usr/local/apr/build-1/libtool  --silent --mode=relink gcc -O2 -Wall -pg -pthread -DHAVE_CONFIG_H -D_REENTRANT -D_GNU_SOURCE -D_LARGEFILE64_SOURCE -I/apr-util-1.4.1/include -I/apr-util-1.4.1/include/private -I/usr/local/apr/include/apr-1 -I/apr-util-1.4.1/xml/expat/lib -version-info 4:1:4 -o libaprutil-1.la -rpath /usr/local/apr-util/lib buckets/apr_brigade.lo buckets/apr_buckets.lo buckets/apr_buckets_alloc.lo buckets/apr_buckets_eos.lo buckets/apr_buckets_file.lo buckets/apr_buckets_flush.lo buckets/apr_buckets_heap.lo buckets/apr_buckets_mmap.lo buckets/apr_buckets_pipe.lo buckets/apr_buckets_pool.lo buckets/apr_buckets_refcount.lo buckets/apr_buckets_simple.lo buckets/apr_buckets_socket.lo crypto/apr_crypto.lo crypto/apr_md4.lo crypto/apr_md5.lo crypto/apr_sha1.lo crypto/getuuid.lo crypto/uuid.lo dbd/apr_dbd.lo dbm/apr_dbm.lo dbm/apr_dbm_sdbm.lo dbm/sdbm/sdbm.lo dbm/sdbm/sdbm_hash.lo dbm/sdbm/sdbm_lock.lo dbm/sdbm/sdbm_pair.lo encoding/apr_base64.lo hooks/apr_hooks.lo ldap/apr_ldap_stub.lo ldap/apr_ldap_url.lo memcache/apr_memcache.lo misc/apr_date.lo misc/apr_queue.lo misc/apr_reslist.lo misc/apr_rmm.lo misc/apr_thread_pool.lo misc/apu_dso.lo misc/apu_version.lo strmatch/apr_strmatch.lo uri/apr_uri.lo xlate/xlate.lo xml/apr_xml.lo -lrt -lcrypt -lpthread -ldl /apr-util-1.4.1/xml/expat/libexpat.la /usr/local/apr/lib/libapr-1.la -lrt -lcrypt -lpthread -ldl )
libtool: install: /usr/bin/install -c -m 755 .libs/libaprutil-1.so.0.4.1T /usr/local/apr-util/lib/libaprutil-1.so.0.4.1
libtool: install: (cd /usr/local/apr-util/lib && { ln -s -f libaprutil-1.so.0.4.1 libaprutil-1.so.0 || { rm -f libaprutil-1.so.0 && ln -s libaprutil-1.so.0.4.1 libaprutil-1.so.0; }; })
libtool: install: (cd /usr/local/apr-util/lib && { ln -s -f libaprutil-1.so.0.4.1 libaprutil-1.so || { rm -f libaprutil-1.so && ln -s libaprutil-1.so.0.4.1 libaprutil-1.so; }; })
libtool: install: /usr/bin/install -c -m 755 .libs/libaprutil-1.lai /usr/local/apr-util/lib/libaprutil-1.la
libtool: install: /usr/bin/install -c -m 755 .libs/libaprutil-1.a /usr/local/apr-util/lib/libaprutil-1.a
libtool: install: chmod 644 /usr/local/apr-util/lib/libaprutil-1.a
libtool: install: ranlib /usr/local/apr-util/lib/libaprutil-1.a
libtool: finish: PATH="/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/sbin" ldconfig -n /usr/local/apr-util/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/apr-util/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
/usr/bin/install -c -m 644 aprutil.exp /usr/local/apr-util/lib
/usr/bin/install -c -m 755 apu-config.out /usr/local/apr-util/bin/apu-1-config
```

---

### Post by oldos2er on 2012-03-18
Moved to Packaging and Compiling Programs.

---

### Post by SevenMachines on 2012-03-19
> **AADAS said:**
> Why I cant install APR-util
I'm not sure I understand, is it actually installed in /usr/local/apr-util/lib or not? Look like it is, there doesnt look like theres been a problem with the installation at all. You'd need to explain further

---

