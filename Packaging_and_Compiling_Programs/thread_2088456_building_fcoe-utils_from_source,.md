---
title: "building fcoe-utils from source,"
date: 2012-11-26
forum: Packaging and Compiling Programs
---

### Post by freisei on 2012-11-26
High, 

because fcping does not exist in ubuntu 12.10x64 server ([https://bugs.launchpad.net/ubuntu/+source/fcoe-utils/+bug/770838](https://bugs.launchpad.net/ubuntu/+source/fcoe-utils/+bug/770838)) i tried to compile it.

Here is my commandlist: 

```

mkdir -p ~*/fcoe/* 
cd ~*/fcoe/* 
wget  [http://www.open-fcoe.org/open-fcoe/downloads/open-fcoe-3.5.tar.gz/at_download/file](http://www.open-fcoe.org/open-fcoe/downloads/open-fcoe-3.5.tar.gz/at_download/file) 
mv file open-fcoe-3.5.tar.gz 
tar xfvz open-fcoe-3.5.tar.gz 

wget  [http://downloads.sourceforge.net/project/hbaapi/hbaapi-src/2.2%20August%202002/hbaapi_src_2.2.tgz?r=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fhbaapi%2Ffiles%2Fhbaapi-src%2F2.2%2520August%25202002%2F](http://downloads.sourceforge.net/project/hbaapi/hbaapi-src/2.2%20August%202002/hbaapi_src_2.2.tgz?r=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fhbaapi%2Ffiles%2Fhbaapi-src%2F2.2%2520August%25202002%2F) 
mv  hbaapi_src_2.2.tgz\?r\=http\:%2F%2Fsourceforge.net%2Fprojects%2Fhbaapi%2Ffiles%2Fhbaapi-src%2F2.2%20August%202002%2F  hbaapi_src_2.2.tgz 
tar xfvz hbaapi_src_2.2.tgz 
mv hbaapi_src_2.2/* hbaapi_build/ 
rmdir hbaapi_src_2.2 
cd hbaapi_build/ 

./bootstrap.sh 
PKG_CONFIG_PATH=*/usr/lib64/pkgconfig/* 
export PKG_CONFIG_PATH 
rpm --eval "%configure" | sh 
make 
make install 
echo /usr/lib64 > /etc/ld.so.conf.d/fcoe.conf 

cd ..*/libhbalinux/* 
./bootstrap.sh 
rpm --eval "%configure" | sh 

make 
make install 

cd ..*/fcoe-utils/* 
./bootstrap.sh 
rpm --eval "%configure" | sh 
make 

```Everything is fine until make of fcoe-utils (fcoeadm) stops with this  errors: 
```

[...] 
gcc -Wall  -O2 -g  -L/usr/lib64 -lHBAAPI -ldl    -o fcoeadm  fcoeadm-fcoeadm.o fcoeadm-fcoeadm_display.o lib/libutil.a 
fcoeadm-fcoeadm_display.o: In function `hba_table_list_init': 
/root/fcoe/fcoe-utils/fcoeadm_display.c:1145: undefined reference to  `HBA_GetNumberOfAdapters' 
[...] 

```I think "GetNumberOfAdapters" is in the HBAAPI, and the libHBAAPI-files  are in /usr/lib64. 

don't know what to do to geht this error way. Would be nice if someone  could help me! 

Sincerly Freisei 



---- complete build log --- 
```

root@permain3:~# mkdir -p ~*/fcoe/* 
root@permain3:~# cd ~*/fcoe/* 
root@permain3:~/fcoe# wget  [http://www.open-fcoe.org/open-fcoe/downloads/open-fcoe-3.5.tar.gz/at_download/file](http://www.open-fcoe.org/open-fcoe/downloads/open-fcoe-3.5.tar.gz/at_download/file) 
--2012-11-26 12:38:48--  [http://www.open-fcoe.org/open-fcoe/downloads/open-fcoe-3.5.tar.gz/at_download/file](http://www.open-fcoe.org/open-fcoe/downloads/open-fcoe-3.5.tar.gz/at_download/file) 
Auflösen des Hostnamen »[www.open-fcoe.org]("http://www.open-fcoe.org") ([www.open-fcoe.org]("http://www.open-fcoe.org"))«... mv  file open-fcoe-3.5.tar.gz 
tar xfvz open-fcoe-3.5.tar.gz 

wget  [http://downloads.sourceforge.net/project/hbaapi/hbaapi-src/2.2%20August%202002/hbaapi_src_2.2.tgz?r=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fhbaapi%2Ffiles%2Fhbaapi-src%2F2.2%2520August%25202002%2F](http://downloads.sourceforge.net/project/hbaapi/hbaapi-src/2.2%20August%202002/hbaapi_src_2.2.tgz?r=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fhbaapi%2Ffiles%2Fhbaapi-src%2F2.2%2520August%25202002%2F) 
mv  hbaapi_src_2.2.tgz\?r\=http\:%2F%2Fsourceforge.net%2Fprojects%2Fhbaapi%2Ffiles%2Fhbaapi-src%2F2.2%20August%202002%2F  hbaapi_src_2.2.tgz 
tar xfvz hbaapi_src_2.2.tgz 
mv hbaapi_src_2.2/* hbaapi_build/ 
rmdir hbaapi_src_2.2 
cd hbaapi_build/198.175.85.252 
Verbindungsaufbau zu [www.open-fcoe.org]("http://www.open-fcoe.org")  ([www.open-fcoe.org]("http://www.open-fcoe.org"))|198.175.85.252|:80... verbunden. 
HTTP-Anforderung gesendet, warte auf Antwort... 200 OK 
Länge: 190793 (186K) [application/x-tar] 
In »»file«« speichern. 

100%[======================================>] 190.793      147K/s   in 1,3s 

2012-11-26 12:38:50 (147 KB/s) - »»file«« gespeichert [190793/190793] 

root@permain3:~/fcoe# mv file open-fcoe-3.5.tar.gz 
root@permain3:~/fcoe# tar xfvz open-fcoe-3.5.tar.gz 
fcoe-utils/ 
fcoe-utils/fcrls.c 
fcoe-utils/fcnsq.c 
fcoe-utils/etc/ 
fcoe-utils/etc/cfg-ethx 
fcoe-utils/etc/initd/ 
fcoe-utils/etc/initd/initd.fedora 
fcoe-utils/etc/initd/initd.suse 
fcoe-utils/etc/config 
fcoe-utils/QUICKSTART 
fcoe-utils/configure.ac 
fcoe-utils/Makefile.am 
fcoe-utils/include/ 
fcoe-utils/include/scsi_netlink_fc.h 
fcoe-utils/include/fcoemon_utils.h 
fcoe-utils/include/fc_els.h 
fcoe-utils/include/scsi_bsg_fc.h 
fcoe-utils/include/scsi_netlink.h 
fcoe-utils/include/fc_ns.h 
fcoe-utils/include/fcoe_utils_version.h.in 
fcoe-utils/include/rtnetlink.h 
fcoe-utils/include/net_types.h 
fcoe-utils/include/fip.h 
fcoe-utils/include/fc_types.h 
fcoe-utils/include/fcoe_utils.h 
fcoe-utils/include/fc_gs.h 
fcoe-utils/include/fc_scsi.h 
fcoe-utils/include/linux/ 
fcoe-utils/include/linux/dcbnl.h 
fcoe-utils/include/linux/rtnetlink.h 
fcoe-utils/include/strarr.h 
fcoe-utils/fipvlan.c 
fcoe-utils/fcoeadm_display.h 
fcoe-utils/README 
fcoe-utils/COPYING 
fcoe-utils/build.sh 
fcoe-utils/CONFIGURE 
fcoe-utils/fcoe-utils.spec.in 
fcoe-utils/contrib/ 
fcoe-utils/contrib/fcoe_edd.sh 
fcoe-utils/contrib/bash_completion/ 
fcoe-utils/contrib/bash_completion/fcoemon 
fcoe-utils/contrib/bash_completion/fcoeadm 
fcoe-utils/contrib/fcc.sh 
fcoe-utils/contrib/fcoe-setup.sh 
fcoe-utils/fcoeadm_display.c 
fcoe-utils/fcoe_clif.h 
fcoe-utils/fcoeadm.c 
fcoe-utils/bootstrap.sh 
fcoe-utils/INSTALL 
fcoe-utils/fcoemon.h 
fcoe-utils/doc/ 
fcoe-utils/doc/fcrls.txt 
fcoe-utils/doc/fipvlan.8 
fcoe-utils/doc/fcnsq.txt 
fcoe-utils/doc/fcoemon.8 
fcoe-utils/doc/fcping.txt 
fcoe-utils/doc/fcping.8 
fcoe-utils/doc/fcoeadm.8 
fcoe-utils/doc/fcoemon.txt 
fcoe-utils/doc/Makefile 
fcoe-utils/doc/fcrls.8 
fcoe-utils/doc/fipvlan.txt 
fcoe-utils/doc/fcoeadm.txt 
fcoe-utils/doc/fcnsq.8 
fcoe-utils/fcoemon.c 
fcoe-utils/lib/ 
fcoe-utils/lib/fip.c 
fcoe-utils/lib/sa_log.c 
fcoe-utils/lib/fcoe_utils.c 
fcoe-utils/lib/sa_other.c 
fcoe-utils/lib/sa_timer.c 
fcoe-utils/lib/sa_select.c 
fcoe-utils/lib/rtnetlink.c 
fcoe-utils/debug/ 
fcoe-utils/debug/fcoedump.sh 
fcoe-utils/debug/dcbcheck.sh 
fcoe-utils/fcping.c 
libhbalinux/ 
libhbalinux/pci.c 
libhbalinux/scsi.c 
libhbalinux/utils.c 
libhbalinux/utils.h 
libhbalinux/configure.ac 
libhbalinux/Makefile.am 
libhbalinux/api_lib.h 
libhbalinux/sg.c 
libhbalinux/adapt.c 
libhbalinux/bind_impl.h 
libhbalinux/rport.c 
libhbalinux/libhbalinux.pc.in 
libhbalinux/README 
libhbalinux/COPYING 
libhbalinux/build.sh 
libhbalinux/CONFIGURE 
libhbalinux/net_types.h 
libhbalinux/fc_types.h 
libhbalinux/bootstrap.sh 
libhbalinux/adapt_impl.h 
libhbalinux/INSTALL 
libhbalinux/fc_scsi.h 
libhbalinux/bind.c 
libhbalinux/libhbalinux.spec.in 
libhbalinux/lport.c 
libhbalinux/lib.c 
hbaapi_build/ 
hbaapi_build/configure.ac 
hbaapi_build/Makefile.am 
hbaapi_build/libHBAAPI.spec 
hbaapi_build/COPYING 
hbaapi_build/hbaapi2.2.patch 
hbaapi_build/build.sh 
hbaapi_build/HBAAPI.pc.in 
hbaapi_build/bootstrap.sh 
hbaapi_build/INSTALL 
root@permain3:~/fcoe# 
root@permain3:~/fcoe# wget  [http://downloads.sourceforge.net/project/hbaapi/hbaapi-src/2.2%20August%202002/hbaapi_src_2.2.tgz?r=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fhbaapi%2Ffiles%2Fhbaapi-src%2F2.2%2520August%25202002%2F](http://downloads.sourceforge.net/project/hbaapi/hbaapi-src/2.2%20August%202002/hbaapi_src_2.2.tgz?r=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fhbaapi%2Ffiles%2Fhbaapi-src%2F2.2%2520August%25202002%2F) 
--2012-11-26 12:38:50--  [http://downloads.sourceforge.net/project/hbaapi/hbaapi-src/2.2%20August%202002/hbaapi_src_2.2.tgz?r=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fhbaapi%2Ffiles%2Fhbaapi-src%2F2.2%2520August%25202002%2F](http://downloads.sourceforge.net/project/hbaapi/hbaapi-src/2.2%20August%202002/hbaapi_src_2.2.tgz?r=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fhbaapi%2Ffiles%2Fhbaapi-src%2F2.2%2520August%25202002%2F) 
Auflösen des Hostnamen »downloads.sourceforge.net  (downloads.sourceforge.net)«... 216.34.181.59 
Verbindungsaufbau zu downloads.sourceforge.net  (downloads.sourceforge.net)|216.34.181.59|:80... verbunden. 
HTTP-Anforderung gesendet, warte auf Antwort... 302 Found 
Platz:  [http://switch.dl.sourceforge.net/project/hbaapi/hbaapi-src/2.2%20August%202002/hbaapi_src_2.2.tgz](http://switch.dl.sourceforge.net/project/hbaapi/hbaapi-src/2.2%20August%202002/hbaapi_src_2.2.tgz)  [folge] 
--2012-11-26 12:38:51--  [http://switch.dl.sourceforge.net/project/hbaapi/hbaapi-src/2.2%20August%202002/hbaapi_src_2.2.tgz](http://switch.dl.sourceforge.net/project/hbaapi/hbaapi-src/2.2%20August%202002/hbaapi_src_2.2.tgz) 
Auflösen des Hostnamen »switch.dl.sourceforge.net  (switch.dl.sourceforge.net)«... 130.59.138.21, 2001:620:0:1b::21 
Verbindungsaufbau zu switch.dl.sourceforge.net  (switch.dl.sourceforge.net)|130.59.138.21|:80... verbunden. 
HTTP-Anforderung gesendet, warte auf Antwort... 200 OK 
Länge: 30232 (30K) [application/x-gzip] 
In  »»hbaapi_src_2.2.tgz?r=[http:%2F%2Fsourceforge.net%2Fprojects%2Fhbaapi%2Ffiles%2Fhbaapi-src%2F2.2%20August%202002%2F««]("http:%2F%2Fsourceforge.net%2Fprojects%2Fhbaapi%2Ffiles%2Fhbaapi-src%2F2.2%20August%202002%2F%C2%AB%C2%AB")  speichern. 

100%[======================================>] 30.232       119K/s   in 0,2s 

2012-11-26 12:38:51 (119 KB/s) -  »»hbaapi_src_2.2.tgz?r=[http:%2F%2Fsourceforge.net%2Fprojects%2Fhbaapi%2Ffiles%2Fhbaapi-src%2F2.2%20August%202002%2F««]("http:%2F%2Fsourceforge.net%2Fprojects%2Fhbaapi%2Ffiles%2Fhbaapi-src%2F2.2%20August%202002%2F%C2%AB%C2%AB")  gespeichert [30232/30232] 

root@permain3:~/fcoe# mv  hbaapi_src_2.2.tgz\?r\=http\:%2F%2Fsourceforge.net%2Fprojects%2Fhbaapi%2Ffiles%2Fhbaapi-src%2F2.2%20August%202002%2F  hbaapi_src_2.2.tgz 
root@permain3:~/fcoe# tar xfvz hbaapi_src_2.2.tgz 
hbaapi_src_2.2/ 
hbaapi_src_2.2/hba.conf 
hbaapi_src_2.2/hba.reg 
hbaapi_src_2.2/hbaapi.h 
hbaapi_src_2.2/vendorhbaapi.h 
hbaapi_src_2.2/HBAAPILIB.c 
hbaapi_src_2.2/hbaapitest.c 
hbaapi_src_2.2/hbasample.c 
hbaapi_src_2.2/hbasample.h 
hbaapi_src_2.2/makefile.nt 
hbaapi_src_2.2/makefile.unix 
hbaapi_src_2.2/readme.txt 
root@permain3:~*/fcoe# mv hbaapi_src_2.2/* hbaapi_build/* 
root@permain3:~/fcoe# rmdir hbaapi_src_2.2 
root@permain3:~*/fcoe# cd hbaapi_build/* 
root@permain3:~/fcoe/hbaapi_build# 
root@permain3:~/fcoe/hbaapi_build# ./bootstrap.sh 
libtoolize: putting auxiliary files in `.'. 
libtoolize: copying file `./config.guess' 
libtoolize: copying file `./config.sub' 
libtoolize: copying file `./install-sh' 
libtoolize: copying file `./ltmain.sh' 
libtoolize: Consider adding `AC_CONFIG_MACRO_DIR([m4])' to configure.ac and 
libtoolize: rerunning libtoolize, to keep the correct libtool macros  in-tree. 
libtoolize: Consider adding `-I m4' to ACLOCAL_AMFLAGS in Makefile.am. 
configure.ac:2: installing `./missing' 
Makefile.am: installing `./depcomp' 
root@permain3:~*/fcoe/hbaapi_build# PKG_CONFIG_PATH=/usr/lib64/pkgconfig/* 
root@permain3:~/fcoe/hbaapi_build# export PKG_CONFIG_PATH 
root@permain3:~/fcoe/hbaapi_build# rpm --eval "%configure" | sh 
checking for a BSD-compatible install... /usr/bin/install -c 
checking whether build environment is sane... yes 
checking for a thread-safe mkdir -p... /bin/mkdir -p 
checking for gawk... no 
checking for mawk... mawk 
checking whether make sets $(MAKE)... yes 
checking for x86_64-pc-linux-gnu-gcc... no 
checking for gcc... gcc 
checking whether the C compiler works... yes 
checking for C compiler default output file name... a.out 
checking for suffix of executables... 
checking whether we are cross compiling... no 
checking for suffix of object files... o 
checking whether we are using the GNU C compiler... yes 
checking whether gcc accepts -g... yes 
checking for gcc option to accept ISO C89... none needed 
checking for style of include used by make... GNU 
checking dependency style of gcc... none 
checking build system type... x86_64-pc-linux-gnu 
checking host system type... x86_64-pc-linux-gnu 
checking how to print strings... printf 
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
checking how to convert x86_64-pc-linux-gnu file names to  x86_64-pc-linux-gnu format... func_convert_file_noop 
checking how to convert x86_64-pc-linux-gnu file names to toolchain  format... func_convert_file_noop 
checking for /usr/bin/ld option to reload object files... -r 
checking for x86_64-pc-linux-gnu-objdump... no 
checking for objdump... objdump 
checking how to recognize dependent libraries... pass_all 
checking for x86_64-pc-linux-gnu-dlltool... no 
checking for dlltool... no 
checking how to associate runtime and link libraries... printf %s\n 
checking for x86_64-pc-linux-gnu-ar... no 
checking for ar... ar 
checking for archiver @FILE support... @ 
checking for x86_64-pc-linux-gnu-strip... no 
checking for strip... strip 
checking for x86_64-pc-linux-gnu-ranlib... no 
checking for ranlib... ranlib 
checking command to parse /usr/bin/nm -B output from gcc object... ok 
checking for sysroot... no 
checking for x86_64-pc-linux-gnu-mt... no 
checking for mt... mt 
checking if mt is a manifest tool... no 
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
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports  shared libraries... yes 
checking whether -lc should be explicitly linked in... no 
checking dynamic linker characteristics... GNU/Linux ld.so 
checking how to hardcode library paths into programs... immediate 
checking whether stripping libraries is possible... yes 
checking if libtool supports shared libraries... yes 
checking whether to build shared libraries... yes 
checking whether to build static libraries... yes 
configure: creating ./config.status 
config.status: creating Makefile 
config.status: creating HBAAPI.pc 
config.status: executing depfiles commands 
config.status: executing libtool commands 
root@permain3:~/fcoe/hbaapi_build# make 
patch < hbaapi2.2.patch 
patching file HBAAPILIB.c 
patching file hbaapi.h 
cp ./HBAAPILIB.c hbaapilib.c 
/bin/bash ./libtool --tag=CC   --mode=compile gcc  -DPACKAGE_NAME=\"libHBAAPI\" -DPACKAGE_TARNAME=\"libhbaapi\"  -DPACKAGE_VERSION=\"2.2.5\" -DPACKAGE_STRING=\"libHBAAPI\ 2.2.5\"  -DPACKAGE_BUGREPORT=\"\" -DPACKAGE_URL=\"\" -DPACKAGE=\"libhbaapi\"  -DVERSION=\"2.2.5\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1  -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1  -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1  -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1  -DLT_OBJDIR=\".libs/\" -I.     -O2 -g -c -o hbaapilib.lo hbaapilib.c 
libtool: compile:  gcc -DPACKAGE_NAME=\"libHBAAPI\"  -DPACKAGE_TARNAME=\"libhbaapi\" -DPACKAGE_VERSION=\"2.2.5\"  "-DPACKAGE_STRING=\"libHBAAPI 2.2.5\"" -DPACKAGE_BUGREPORT=\"\"  -DPACKAGE_URL=\"\" -DPACKAGE=\"libhbaapi\" -DVERSION=\"2.2.5\"  -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1  -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1  -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1  -DLT_OBJDIR=\".libs/\" -I. -O2 -g -c hbaapilib.c  -fPIC -DPIC -o  .libs/hbaapilib.o 
libtool: compile:  gcc -DPACKAGE_NAME=\"libHBAAPI\"  -DPACKAGE_TARNAME=\"libhbaapi\" -DPACKAGE_VERSION=\"2.2.5\"  "-DPACKAGE_STRING=\"libHBAAPI 2.2.5\"" -DPACKAGE_BUGREPORT=\"\"  -DPACKAGE_URL=\"\" -DPACKAGE=\"libhbaapi\" -DVERSION=\"2.2.5\"  -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1  -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1  -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1  -DLT_OBJDIR=\".libs/\" -I. -O2 -g -c hbaapilib.c -o hbaapilib.o  >/dev/null 2>&1 
/bin/bash ./libtool --tag=CC   --mode=link gcc  -O2 -g -version-info  2:2:0  -o libHBAAPI.la -rpath /usr/lib64  hbaapilib.lo 
libtool: link: gcc -shared  -fPIC -DPIC  .libs/hbaapilib.o    -O2  -Wl,-soname -Wl,libHBAAPI.so.2 -o .libs/libHBAAPI.so.2.0.2 
libtool: link: (cd ".libs" && rm -f "libHBAAPI.so.2" && ln -s  "libHBAAPI.so.2.0.2" "libHBAAPI.so.2") 
libtool: link: (cd ".libs" && rm -f "libHBAAPI.so" && ln -s  "libHBAAPI.so.2.0.2" "libHBAAPI.so") 
libtool: link: ar cru .libs/libHBAAPI.a  hbaapilib.o 
libtool: link: ranlib .libs/libHBAAPI.a 
libtool: link: ( cd ".libs" && rm -f "libHBAAPI.la" && ln -s  "../libHBAAPI.la" "libHBAAPI.la" ) 
grep "^#\|^[[:space:]]*$" ./hba.conf > hba.conf.tmp 
mv hba.conf.tmp hba.conf 
root@permain3:~/fcoe/hbaapi_build# make install 
grep "^#\|^[[:space:]]*$" ./hba.conf > hba.conf.tmp 
mv hba.conf.tmp hba.conf 
make[1]: Betrete Verzeichnis '/root/fcoe/hbaapi_build' 
grep "^#\|^[[:space:]]*$" ./hba.conf > hba.conf.tmp 
mv hba.conf.tmp hba.conf 
 /bin/mkdir -p '/etc' 
 /usr/bin/install -c -m 644 hba.conf '/etc' 
 /bin/mkdir -p '/usr/lib64' 
 /bin/bash ./libtool   --mode=install /usr/bin/install -c  libHBAAPI.la '/usr/lib64' 
libtool: install: /usr/bin/install -c .libs/libHBAAPI.so.2.0.2  /usr/lib64/libHBAAPI.so.2.0.2 
libtool: install: (cd /usr/lib64 && { ln -s -f libHBAAPI.so.2.0.2  libHBAAPI.so.2 || { rm -f libHBAAPI.so.2 && ln -s libHBAAPI.so.2.0.2  libHBAAPI.so.2; }; }) 
libtool: install: (cd /usr/lib64 && { ln -s -f libHBAAPI.so.2.0.2  libHBAAPI.so || { rm -f libHBAAPI.so && ln -s libHBAAPI.so.2.0.2  libHBAAPI.so; }; }) 
libtool: install: /usr/bin/install -c .libs/libHBAAPI.lai  /usr/lib64/libHBAAPI.la 
libtool: install: /usr/bin/install -c .libs/libHBAAPI.a  /usr/lib64/libHBAAPI.a 
libtool: install: chmod 644 /usr/lib64/libHBAAPI.a 
libtool: install: ranlib /usr/lib64/libHBAAPI.a 
libtool: finish:  PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/sbin"  ldconfig -n /usr/lib64 
---------------------------------------------------------------------- 
Libraries have been installed in: 
   /usr/lib64 

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
 /bin/mkdir -p '/usr/include' 
 */usr/bin/install -c -m 644  hbaapi.h vendorhbaapi.h '/usr/include/*.' 
 /bin/mkdir -p '/usr/lib64/pkgconfig' 
 /usr/bin/install -c -m 644 HBAAPI.pc '/usr/lib64/pkgconfig' 
make[1]: Verlasse Verzeichnis '/root/fcoe/hbaapi_build' 
root@permain3:~/fcoe/hbaapi_build# echo /usr/lib64 >  /etc/ld.so.conf.d/fcoe.confroot@permain3:~/fcoe/hbaapi_build# 
root@permain3:~*/fcoe/hbaapi_build# cd ../libhbalinux/* 
root@permain3:~/fcoe/libhbalinux# ./bootstrap.sh 

libtoolize: putting auxiliary files in `.'. 
libtoolize: linking file `./config.guess' 
libtoolize: linking file `./config.sub' 
libtoolize: linking file `./install-sh' 
libtoolize: linking file `./ltmain.sh' 
libtoolize: Consider adding `AC_CONFIG_MACRO_DIR([m4])' to configure.ac and 
libtoolize: rerunning libtoolize, to keep the correct libtool macros  in-tree. 
libtoolize: Consider adding `-I m4' to ACLOCAL_AMFLAGS in Makefile.am. 
configure.ac:2: installing `./missing' 
Makefile.am: installing `./depcomp' 
root@permain3:~/fcoe/libhbalinux# rpm --eval "%configure" | sh 
checking for a BSD-compatible install... /usr/bin/install -c 
checking whether build environment is sane... yes 
checking for a thread-safe mkdir -p... /bin/mkdir -p 
checking for gawk... no 
checking for mawk... mawk 
checking whether make sets $(MAKE)... yes 
checking build system type... x86_64-pc-linux-gnu 
checking host system type... x86_64-pc-linux-gnu 
checking how to print strings... printf 
checking for style of include used by make... GNU 
checking for x86_64-pc-linux-gnu-gcc... no 
checking for gcc... gcc 
checking whether the C compiler works... yes 
checking for C compiler default output file name... a.out 
checking for suffix of executables... 
checking whether we are cross compiling... no 
checking for suffix of object files... o 
checking whether we are using the GNU C compiler... yes 
checking whether gcc accepts -g... yes 
checking for gcc option to accept ISO C89... none needed 
checking dependency style of gcc... none 
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
checking how to convert x86_64-pc-linux-gnu file names to  x86_64-pc-linux-gnu format... func_convert_file_noop 
checking how to convert x86_64-pc-linux-gnu file names to toolchain  format... func_convert_file_noop 
checking for /usr/bin/ld option to reload object files... -r 
checking for x86_64-pc-linux-gnu-objdump... no 
checking for objdump... objdump 
checking how to recognize dependent libraries... pass_all 
checking for x86_64-pc-linux-gnu-dlltool... no 
checking for dlltool... no 
checking how to associate runtime and link libraries... printf %s\n 
checking for x86_64-pc-linux-gnu-ar... no 
checking for ar... ar 
checking for archiver @FILE support... @ 
checking for x86_64-pc-linux-gnu-strip... no 
checking for strip... strip 
checking for x86_64-pc-linux-gnu-ranlib... no 
checking for ranlib... ranlib 
checking command to parse /usr/bin/nm -B output from gcc object... ok 
checking for sysroot... no 
checking for x86_64-pc-linux-gnu-mt... no 
checking for mt... mt 
checking if mt is a manifest tool... no 
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
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports  shared libraries... yes 
checking whether -lc should be explicitly linked in... no 
checking dynamic linker characteristics... GNU/Linux ld.so 
checking how to hardcode library paths into programs... immediate 
checking whether stripping libraries is possible... yes 
checking if libtool supports shared libraries... yes 
checking whether to build shared libraries... yes 
checking whether to build static libraries... yes 
checking for x86_64-pc-linux-gnu-gcc... gcc 
checking whether we are using the GNU C compiler... (cached) yes 
checking whether gcc accepts -g... (cached) yes 
checking for gcc option to accept ISO C89... (cached) none needed 
checking dependency style of gcc... (cached) none 
checking for x86_64-pc-linux-gnu-pkg-config... no 
checking for pkg-config... /usr/bin/pkg-config 
checking pkg-config is at least version 0.9.0... yes 
checking for PCIACCESS... yes 
checking for HBAAPI... yes 
configure: creating ./config.status 
config.status: creating Makefile 
config.status: creating libhbalinux.spec 
config.status: creating libhbalinux.pc 
config.status: executing depfiles commands 
config.status: executing libtool commands 
root@permain3:~/fcoe/libhbalinux# 
root@permain3:~/fcoe/libhbalinux# make 
/bin/bash ./libtool --tag=CC   --mode=compile gcc  -DPACKAGE_NAME=\"libhbalinux\" -DPACKAGE_TARNAME=\"libhbalinux\"  -DPACKAGE_VERSION=\"1.0.14\" -DPACKAGE_STRING=\"libhbalinux\ 1.0.14\"  -DPACKAGE_BUGREPORT=\"devel@open-fcoe.org\" -DPACKAGE_URL=\"\"  -DPACKAGE=\"libhbalinux\" -DVERSION=\"1.0.14\" -DSTDC_HEADERS=1  -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1  -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1  -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1  -DLT_OBJDIR=\".libs/\" -I.      -O2 -g -c -o adapt.lo adapt.c 
libtool: compile:  gcc -DPACKAGE_NAME=\"libhbalinux\"  -DPACKAGE_TARNAME=\"libhbalinux\" -DPACKAGE_VERSION=\"1.0.14\"  "-DPACKAGE_STRING=\"libhbalinux 1.0.14\""  -DPACKAGE_BUGREPORT=\"devel@open-fcoe.org\" -DPACKAGE_URL=\"\"  -DPACKAGE=\"libhbalinux\" -DVERSION=\"1.0.14\" -DSTDC_HEADERS=1  -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1  -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1  -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1  -DLT_OBJDIR=\".libs/\" -I. -O2 -g -c adapt.c  -fPIC -DPIC -o .libs/adapt.o 
libtool: compile:  gcc -DPACKAGE_NAME=\"libhbalinux\"  -DPACKAGE_TARNAME=\"libhbalinux\" -DPACKAGE_VERSION=\"1.0.14\"  "-DPACKAGE_STRING=\"libhbalinux 1.0.14\""  -DPACKAGE_BUGREPORT=\"devel@open-fcoe.org\" -DPACKAGE_URL=\"\"  -DPACKAGE=\"libhbalinux\" -DVERSION=\"1.0.14\" -DSTDC_HEADERS=1  -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1  -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1  -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1  -DLT_OBJDIR=\".libs/\" -I. -O2 -g -c adapt.c -o adapt.o >/dev/null 2>&1 
/bin/bash ./libtool --tag=CC   --mode=compile gcc  -DPACKAGE_NAME=\"libhbalinux\" -DPACKAGE_TARNAME=\"libhbalinux\"  -DPACKAGE_VERSION=\"1.0.14\" -DPACKAGE_STRING=\"libhbalinux\ 1.0.14\"  -DPACKAGE_BUGREPORT=\"devel@open-fcoe.org\" -DPACKAGE_URL=\"\"  -DPACKAGE=\"libhbalinux\" -DVERSION=\"1.0.14\" -DSTDC_HEADERS=1  -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1  -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1  -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1  -DLT_OBJDIR=\".libs/\" -I.      -O2 -g -c -o bind.lo bind.c 
libtool: compile:  gcc -DPACKAGE_NAME=\"libhbalinux\"  -DPACKAGE_TARNAME=\"libhbalinux\" -DPACKAGE_VERSION=\"1.0.14\"  "-DPACKAGE_STRING=\"libhbalinux 1.0.14\""  -DPACKAGE_BUGREPORT=\"devel@open-fcoe.org\" -DPACKAGE_URL=\"\"  -DPACKAGE=\"libhbalinux\" -DVERSION=\"1.0.14\" -DSTDC_HEADERS=1  -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1  -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1  -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1  -DLT_OBJDIR=\".libs/\" -I. -O2 -g -c bind.c  -fPIC -DPIC -o .libs/bind.o 
libtool: compile:  gcc -DPACKAGE_NAME=\"libhbalinux\"  -DPACKAGE_TARNAME=\"libhbalinux\" -DPACKAGE_VERSION=\"1.0.14\"  "-DPACKAGE_STRING=\"libhbalinux 1.0.14\""  -DPACKAGE_BUGREPORT=\"devel@open-fcoe.org\" -DPACKAGE_URL=\"\"  -DPACKAGE=\"libhbalinux\" -DVERSION=\"1.0.14\" -DSTDC_HEADERS=1  -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1  -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1  -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1  -DLT_OBJDIR=\".libs/\" -I. -O2 -g -c bind.c -o bind.o >/dev/null 2>&1 
/bin/bash ./libtool --tag=CC   --mode=compile gcc  -DPACKAGE_NAME=\"libhbalinux\" -DPACKAGE_TARNAME=\"libhbalinux\"  -DPACKAGE_VERSION=\"1.0.14\" -DPACKAGE_STRING=\"libhbalinux\ 1.0.14\"  -DPACKAGE_BUGREPORT=\"devel@open-fcoe.org\" -DPACKAGE_URL=\"\"  -DPACKAGE=\"libhbalinux\" -DVERSION=\"1.0.14\" -DSTDC_HEADERS=1  -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1  -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1  -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1  -DLT_OBJDIR=\".libs/\" -I.      -O2 -g -c -o lib.lo lib.c 
libtool: compile:  gcc -DPACKAGE_NAME=\"libhbalinux\"  -DPACKAGE_TARNAME=\"libhbalinux\" -DPACKAGE_VERSION=\"1.0.14\"  "-DPACKAGE_STRING=\"libhbalinux 1.0.14\""  -DPACKAGE_BUGREPORT=\"devel@open-fcoe.org\" -DPACKAGE_URL=\"\"  -DPACKAGE=\"libhbalinux\" -DVERSION=\"1.0.14\" -DSTDC_HEADERS=1  -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1  -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1  -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1  -DLT_OBJDIR=\".libs/\" -I. -O2 -g -c lib.c  -fPIC -DPIC -o .libs/lib.o 
libtool: compile:  gcc -DPACKAGE_NAME=\"libhbalinux\"  -DPACKAGE_TARNAME=\"libhbalinux\" -DPACKAGE_VERSION=\"1.0.14\"  "-DPACKAGE_STRING=\"libhbalinux 1.0.14\""  -DPACKAGE_BUGREPORT=\"devel@open-fcoe.org\" -DPACKAGE_URL=\"\"  -DPACKAGE=\"libhbalinux\" -DVERSION=\"1.0.14\" -DSTDC_HEADERS=1  -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1  -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1  -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1  -DLT_OBJDIR=\".libs/\" -I. -O2 -g -c lib.c -o lib.o >/dev/null 2>&1 
/bin/bash ./libtool --tag=CC   --mode=compile gcc  -DPACKAGE_NAME=\"libhbalinux\" -DPACKAGE_TARNAME=\"libhbalinux\"  -DPACKAGE_VERSION=\"1.0.14\" -DPACKAGE_STRING=\"libhbalinux\ 1.0.14\"  -DPACKAGE_BUGREPORT=\"devel@open-fcoe.org\" -DPACKAGE_URL=\"\"  -DPACKAGE=\"libhbalinux\" -DVERSION=\"1.0.14\" -DSTDC_HEADERS=1  -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1  -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1  -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1  -DLT_OBJDIR=\".libs/\" -I.      -O2 -g -c -o lport.lo lport.c 
libtool: compile:  gcc -DPACKAGE_NAME=\"libhbalinux\"  -DPACKAGE_TARNAME=\"libhbalinux\" -DPACKAGE_VERSION=\"1.0.14\"  "-DPACKAGE_STRING=\"libhbalinux 1.0.14\""  -DPACKAGE_BUGREPORT=\"devel@open-fcoe.org\" -DPACKAGE_URL=\"\"  -DPACKAGE=\"libhbalinux\" -DVERSION=\"1.0.14\" -DSTDC_HEADERS=1  -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1  -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1  -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1  -DLT_OBJDIR=\".libs/\" -I. -O2 -g -c lport.c  -fPIC -DPIC -o .libs/lport.o 
libtool: compile:  gcc -DPACKAGE_NAME=\"libhbalinux\"  -DPACKAGE_TARNAME=\"libhbalinux\" -DPACKAGE_VERSION=\"1.0.14\"  "-DPACKAGE_STRING=\"libhbalinux 1.0.14\""  -DPACKAGE_BUGREPORT=\"devel@open-fcoe.org\" -DPACKAGE_URL=\"\"  -DPACKAGE=\"libhbalinux\" -DVERSION=\"1.0.14\" -DSTDC_HEADERS=1  -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1  -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1  -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1  -DLT_OBJDIR=\".libs/\" -I. -O2 -g -c lport.c -o lport.o >/dev/null 2>&1 
/bin/bash ./libtool --tag=CC   --mode=compile gcc  -DPACKAGE_NAME=\"libhbalinux\" -DPACKAGE_TARNAME=\"libhbalinux\"  -DPACKAGE_VERSION=\"1.0.14\" -DPACKAGE_STRING=\"libhbalinux\ 1.0.14\"  -DPACKAGE_BUGREPORT=\"devel@open-fcoe.org\" -DPACKAGE_URL=\"\"  -DPACKAGE=\"libhbalinux\" -DVERSION=\"1.0.14\" -DSTDC_HEADERS=1  -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1  -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1  -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1  -DLT_OBJDIR=\".libs/\" -I.      -O2 -g -c -o pci.lo pci.c 
libtool: compile:  gcc -DPACKAGE_NAME=\"libhbalinux\"  -DPACKAGE_TARNAME=\"libhbalinux\" -DPACKAGE_VERSION=\"1.0.14\"  "-DPACKAGE_STRING=\"libhbalinux 1.0.14\""  -DPACKAGE_BUGREPORT=\"devel@open-fcoe.org\" -DPACKAGE_URL=\"\"  -DPACKAGE=\"libhbalinux\" -DVERSION=\"1.0.14\" -DSTDC_HEADERS=1  -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1  -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1  -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1  -DLT_OBJDIR=\".libs/\" -I. -O2 -g -c pci.c  -fPIC -DPIC -o .libs/pci.o 
libtool: compile:  gcc -DPACKAGE_NAME=\"libhbalinux\"  -DPACKAGE_TARNAME=\"libhbalinux\" -DPACKAGE_VERSION=\"1.0.14\"  "-DPACKAGE_STRING=\"libhbalinux 1.0.14\""  -DPACKAGE_BUGREPORT=\"devel@open-fcoe.org\" -DPACKAGE_URL=\"\"  -DPACKAGE=\"libhbalinux\" -DVERSION=\"1.0.14\" -DSTDC_HEADERS=1  -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1  -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1  -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1  -DLT_OBJDIR=\".libs/\" -I. -O2 -g -c pci.c -o pci.o >/dev/null 2>&1 
/bin/bash ./libtool --tag=CC   --mode=compile gcc  -DPACKAGE_NAME=\"libhbalinux\" -DPACKAGE_TARNAME=\"libhbalinux\"  -DPACKAGE_VERSION=\"1.0.14\" -DPACKAGE_STRING=\"libhbalinux\ 1.0.14\"  -DPACKAGE_BUGREPORT=\"devel@open-fcoe.org\" -DPACKAGE_URL=\"\"  -DPACKAGE=\"libhbalinux\" -DVERSION=\"1.0.14\" -DSTDC_HEADERS=1  -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1  -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1  -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1  -DLT_OBJDIR=\".libs/\" -I.      -O2 -g -c -o rport.lo rport.c 
libtool: compile:  gcc -DPACKAGE_NAME=\"libhbalinux\"  -DPACKAGE_TARNAME=\"libhbalinux\" -DPACKAGE_VERSION=\"1.0.14\"  "-DPACKAGE_STRING=\"libhbalinux 1.0.14\""  -DPACKAGE_BUGREPORT=\"devel@open-fcoe.org\" -DPACKAGE_URL=\"\"  -DPACKAGE=\"libhbalinux\" -DVERSION=\"1.0.14\" -DSTDC_HEADERS=1  -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1  -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1  -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1  -DLT_OBJDIR=\".libs/\" -I. -O2 -g -c rport.c  -fPIC -DPIC -o .libs/rport.o 
libtool: compile:  gcc -DPACKAGE_NAME=\"libhbalinux\"  -DPACKAGE_TARNAME=\"libhbalinux\" -DPACKAGE_VERSION=\"1.0.14\"  "-DPACKAGE_STRING=\"libhbalinux 1.0.14\""  -DPACKAGE_BUGREPORT=\"devel@open-fcoe.org\" -DPACKAGE_URL=\"\"  -DPACKAGE=\"libhbalinux\" -DVERSION=\"1.0.14\" -DSTDC_HEADERS=1  -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1  -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1  -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1  -DLT_OBJDIR=\".libs/\" -I. -O2 -g -c rport.c -o rport.o >/dev/null 2>&1 
/bin/bash ./libtool --tag=CC   --mode=compile gcc  -DPACKAGE_NAME=\"libhbalinux\" -DPACKAGE_TARNAME=\"libhbalinux\"  -DPACKAGE_VERSION=\"1.0.14\" -DPACKAGE_STRING=\"libhbalinux\ 1.0.14\"  -DPACKAGE_BUGREPORT=\"devel@open-fcoe.org\" -DPACKAGE_URL=\"\"  -DPACKAGE=\"libhbalinux\" -DVERSION=\"1.0.14\" -DSTDC_HEADERS=1  -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1  -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1  -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1  -DLT_OBJDIR=\".libs/\" -I.      -O2 -g -c -o scsi.lo scsi.c 
libtool: compile:  gcc -DPACKAGE_NAME=\"libhbalinux\"  -DPACKAGE_TARNAME=\"libhbalinux\" -DPACKAGE_VERSION=\"1.0.14\"  "-DPACKAGE_STRING=\"libhbalinux 1.0.14\""  -DPACKAGE_BUGREPORT=\"devel@open-fcoe.org\" -DPACKAGE_URL=\"\"  -DPACKAGE=\"libhbalinux\" -DVERSION=\"1.0.14\" -DSTDC_HEADERS=1  -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1  -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1  -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1  -DLT_OBJDIR=\".libs/\" -I. -O2 -g -c scsi.c  -fPIC -DPIC -o .libs/scsi.o 
libtool: compile:  gcc -DPACKAGE_NAME=\"libhbalinux\"  -DPACKAGE_TARNAME=\"libhbalinux\" -DPACKAGE_VERSION=\"1.0.14\"  "-DPACKAGE_STRING=\"libhbalinux 1.0.14\""  -DPACKAGE_BUGREPORT=\"devel@open-fcoe.org\" -DPACKAGE_URL=\"\"  -DPACKAGE=\"libhbalinux\" -DVERSION=\"1.0.14\" -DSTDC_HEADERS=1  -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1  -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1  -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1  -DLT_OBJDIR=\".libs/\" -I. -O2 -g -c scsi.c -o scsi.o >/dev/null 2>&1 
/bin/bash ./libtool --tag=CC   --mode=compile gcc  -DPACKAGE_NAME=\"libhbalinux\" -DPACKAGE_TARNAME=\"libhbalinux\"  -DPACKAGE_VERSION=\"1.0.14\" -DPACKAGE_STRING=\"libhbalinux\ 1.0.14\"  -DPACKAGE_BUGREPORT=\"devel@open-fcoe.org\" -DPACKAGE_URL=\"\"  -DPACKAGE=\"libhbalinux\" -DVERSION=\"1.0.14\" -DSTDC_HEADERS=1  -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1  -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1  -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1  -DLT_OBJDIR=\".libs/\" -I.      -O2 -g -c -o sg.lo sg.c 
libtool: compile:  gcc -DPACKAGE_NAME=\"libhbalinux\"  -DPACKAGE_TARNAME=\"libhbalinux\" -DPACKAGE_VERSION=\"1.0.14\"  "-DPACKAGE_STRING=\"libhbalinux 1.0.14\""  -DPACKAGE_BUGREPORT=\"devel@open-fcoe.org\" -DPACKAGE_URL=\"\"  -DPACKAGE=\"libhbalinux\" -DVERSION=\"1.0.14\" -DSTDC_HEADERS=1  -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1  -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1  -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1  -DLT_OBJDIR=\".libs/\" -I. -O2 -g -c sg.c  -fPIC -DPIC -o .libs/sg.o 
libtool: compile:  gcc -DPACKAGE_NAME=\"libhbalinux\"  -DPACKAGE_TARNAME=\"libhbalinux\" -DPACKAGE_VERSION=\"1.0.14\"  "-DPACKAGE_STRING=\"libhbalinux 1.0.14\""  -DPACKAGE_BUGREPORT=\"devel@open-fcoe.org\" -DPACKAGE_URL=\"\"  -DPACKAGE=\"libhbalinux\" -DVERSION=\"1.0.14\" -DSTDC_HEADERS=1  -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1  -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1  -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1  -DLT_OBJDIR=\".libs/\" -I. -O2 -g -c sg.c -o sg.o >/dev/null 2>&1 
/bin/bash ./libtool --tag=CC   --mode=compile gcc  -DPACKAGE_NAME=\"libhbalinux\" -DPACKAGE_TARNAME=\"libhbalinux\"  -DPACKAGE_VERSION=\"1.0.14\" -DPACKAGE_STRING=\"libhbalinux\ 1.0.14\"  -DPACKAGE_BUGREPORT=\"devel@open-fcoe.org\" -DPACKAGE_URL=\"\"  -DPACKAGE=\"libhbalinux\" -DVERSION=\"1.0.14\" -DSTDC_HEADERS=1  -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1  -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1  -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1  -DLT_OBJDIR=\".libs/\" -I.      -O2 -g -c -o utils.lo utils.c 
libtool: compile:  gcc -DPACKAGE_NAME=\"libhbalinux\"  -DPACKAGE_TARNAME=\"libhbalinux\" -DPACKAGE_VERSION=\"1.0.14\"  "-DPACKAGE_STRING=\"libhbalinux 1.0.14\""  -DPACKAGE_BUGREPORT=\"devel@open-fcoe.org\" -DPACKAGE_URL=\"\"  -DPACKAGE=\"libhbalinux\" -DVERSION=\"1.0.14\" -DSTDC_HEADERS=1  -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1  -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1  -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1  -DLT_OBJDIR=\".libs/\" -I. -O2 -g -c utils.c  -fPIC -DPIC -o .libs/utils.o 
libtool: compile:  gcc -DPACKAGE_NAME=\"libhbalinux\"  -DPACKAGE_TARNAME=\"libhbalinux\" -DPACKAGE_VERSION=\"1.0.14\"  "-DPACKAGE_STRING=\"libhbalinux 1.0.14\""  -DPACKAGE_BUGREPORT=\"devel@open-fcoe.org\" -DPACKAGE_URL=\"\"  -DPACKAGE=\"libhbalinux\" -DVERSION=\"1.0.14\" -DSTDC_HEADERS=1  -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1  -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1  -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1  -DLT_OBJDIR=\".libs/\" -I. -O2 -g -c utils.c -o utils.o >/dev/null 2>&1 
/bin/bash ./libtool --tag=CC   --mode=link gcc   -O2 -g -version-info  2:2:0  -o libhbalinux.la -rpath /usr/lib64 adapt.lo bind.lo lib.lo  lport.lo pci.lo rport.lo scsi.lo sg.lo utils.lo -lpciaccess 
libtool: link: gcc -shared  -fPIC -DPIC  .libs/adapt.o .libs/bind.o  .libs/lib.o .libs/lport.o .libs/pci.o .libs/rport.o .libs/scsi.o  .libs/sg.o .libs/utils.o   -lpciaccess  -O2   -Wl,-soname  -Wl,libhbalinux.so.2 -o .libs/libhbalinux.so.2.0.2 
libtool: link: (cd ".libs" && rm -f "libhbalinux.so.2" && ln -s  "libhbalinux.so.2.0.2" "libhbalinux.so.2") 
libtool: link: (cd ".libs" && rm -f "libhbalinux.so" && ln -s  "libhbalinux.so.2.0.2" "libhbalinux.so") 
libtool: link: ar cru .libs/libhbalinux.a  adapt.o bind.o lib.o lport.o  pci.o rport.o scsi.o sg.o utils.o 
libtool: link: ranlib .libs/libhbalinux.a 
libtool: link: ( cd ".libs" && rm -f "libhbalinux.la" && ln -s  "../libhbalinux.la" "libhbalinux.la" ) 
root@permain3:~/fcoe/libhbalinux# make install 
make[1]: Betrete Verzeichnis '/root/fcoe/libhbalinux' 
 /bin/mkdir -p '/usr/lib64' 
 /bin/bash ./libtool   --mode=install /usr/bin/install -c  libhbalinux.la '/usr/lib64' 
libtool: install: /usr/bin/install -c .libs/libhbalinux.so.2.0.2  /usr/lib64/libhbalinux.so.2.0.2 
libtool: install: (cd /usr/lib64 && { ln -s -f libhbalinux.so.2.0.2  libhbalinux.so.2 || { rm -f libhbalinux.so.2 && ln -s  libhbalinux.so.2.0.2 libhbalinux.so.2; }; }) 
libtool: install: (cd /usr/lib64 && { ln -s -f libhbalinux.so.2.0.2  libhbalinux.so || { rm -f libhbalinux.so && ln -s libhbalinux.so.2.0.2  libhbalinux.so; }; }) 
libtool: install: /usr/bin/install -c .libs/libhbalinux.lai  /usr/lib64/libhbalinux.la 
libtool: install: /usr/bin/install -c .libs/libhbalinux.a  /usr/lib64/libhbalinux.a 
libtool: install: chmod 644 /usr/lib64/libhbalinux.a 
libtool: install: ranlib /usr/lib64/libhbalinux.a 
libtool: finish:  PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/sbin"  ldconfig -n /usr/lib64 
---------------------------------------------------------------------- 
Libraries have been installed in: 
   /usr/lib64 

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
 /bin/mkdir -p '/usr/lib64/pkgconfig' 
 /usr/bin/install -c -m 644 libhbalinux.pc '/usr/lib64/pkgconfig' 
make  install-data-hook 
make[2]: Betrete Verzeichnis '/root/fcoe/libhbalinux' 
. ${PWD}/libhbalinux.la; \ 
        ORG=org.open-fcoe.libhbalinux; \ 
        LIB=/usr/lib64/${dlname}; \ 
        STR="$ORG       $LIB"; \ 
        CONF=/etc/hba.conf; \ 
        if test -f $CONF; then \ 
                grep -E -q ^[[:space:]]*$ORG[[:space:]]+$LIB $CONF; \ 
                if test $? -ne 0; then \ 
                        echo $STR >> $CONF; \ 
                else \ 
                        echo "** $CONF already configured"; \ 
                        echo "** system configuration not updated"; \ 
                fi; \ 
        else \ 
                echo "** WARNING: $CONF does not exist"; \ 
                echo "** system configuration not updated"; \ 
        fi 
make[2]: Verlasse Verzeichnis '/root/fcoe/libhbalinux' 
make[1]: Verlasse Verzeichnis '/root/fcoe/libhbalinux' 
root@permain3:~/fcoe/libhbalinux# 
root@permain3:~*/fcoe/libhbalinux# cd ../fcoe-utils/* 
root@permain3:~/fcoe/fcoe-utils# ./bootstrap.sh 
configure.ac:5: installing `./compile' 
configure.ac:2: installing `./install-sh' 
configure.ac:2: installing `./missing' 
Makefile.am: installing `./depcomp' 
root@permain3:~/fcoe/fcoe-utils# rpm --eval "%configure" | sh 
checking for a BSD-compatible install... /usr/bin/install -c 
checking whether build environment is sane... yes 
checking for a thread-safe mkdir -p... /bin/mkdir -p 
checking for gawk... no 
checking for mawk... mawk 
checking whether make sets $(MAKE)... yes 
checking for x86_64-pc-linux-gnu-gcc... no 
checking for gcc... gcc 
checking whether the C compiler works... yes 
checking for C compiler default output file name... a.out 
checking for suffix of executables... 
checking whether we are cross compiling... no 
checking for suffix of object files... o 
checking whether we are using the GNU C compiler... yes 
checking whether gcc accepts -g... yes 
checking for gcc option to accept ISO C89... none needed 
checking for style of include used by make... GNU 
checking dependency style of gcc... none 
checking whether gcc and cc understand -c and -o together... yes 
checking for x86_64-pc-linux-gnu-ranlib... no 
checking for ranlib... ranlib 
checking for x86_64-pc-linux-gnu-pkg-config... no 
checking for pkg-config... /usr/bin/pkg-config 
checking pkg-config is at least version 0.9.0... yes 
checking for HBAAPI... yes 
checking for LLDPAD... yes 
checking for LIBHBALINUX... yes 
configure: creating ./config.status 
config.status: creating Makefile 
config.status: creating fcoe-utils.spec 
config.status: creating include/fcoe_utils_version.h 
config.status: executing depfiles commands 
root@permain3:~/fcoe/fcoe-utils# 
root@permain3:~*/fcoe/fcoe-utils# cd ../fcoe-utils/* 
root@permain3:~/fcoe/fcoe-utils# ./bootstrap.sh 
root@permain3:~/fcoe/fcoe-utils# rpm --eval "%configure" | sh^C 
root@permain3:~/fcoe/fcoe-utils# make 
gcc -DPACKAGE_NAME=\"fcoe-utils\" -DPACKAGE_TARNAME=\"fcoe-utils\"  -DPACKAGE_VERSION=\"1.0.24\" -DPACKAGE_STRING=\"fcoe-utils\ 1.0.24\"  -DPACKAGE_BUGREPORT=\"devel@open-fcoe.org\" -DPACKAGE_URL=\"\"  -DPACKAGE=\"fcoe-utils\" -DVERSION=\"1.0.24\" -I.  -I./include  -I./include -DSYSCONFDIR="\"/etc\""  -Wall -O2 -g -c -o lib/fcoe_utils.o  lib/fcoe_utils.c 
gcc -DPACKAGE_NAME=\"fcoe-utils\" -DPACKAGE_TARNAME=\"fcoe-utils\"  -DPACKAGE_VERSION=\"1.0.24\" -DPACKAGE_STRING=\"fcoe-utils\ 1.0.24\"  -DPACKAGE_BUGREPORT=\"devel@open-fcoe.org\" -DPACKAGE_URL=\"\"  -DPACKAGE=\"fcoe-utils\" -DVERSION=\"1.0.24\" -I.  -I./include  -I./include -DSYSCONFDIR="\"/etc\""  -Wall -O2 -g -c -o lib/sa_log.o  lib/sa_log.c 
gcc -DPACKAGE_NAME=\"fcoe-utils\" -DPACKAGE_TARNAME=\"fcoe-utils\"  -DPACKAGE_VERSION=\"1.0.24\" -DPACKAGE_STRING=\"fcoe-utils\ 1.0.24\"  -DPACKAGE_BUGREPORT=\"devel@open-fcoe.org\" -DPACKAGE_URL=\"\"  -DPACKAGE=\"fcoe-utils\" -DVERSION=\"1.0.24\" -I.  -I./include  -I./include -DSYSCONFDIR="\"/etc\""  -Wall -O2 -g -c -o lib/sa_select.o  lib/sa_select.c 
gcc -DPACKAGE_NAME=\"fcoe-utils\" -DPACKAGE_TARNAME=\"fcoe-utils\"  -DPACKAGE_VERSION=\"1.0.24\" -DPACKAGE_STRING=\"fcoe-utils\ 1.0.24\"  -DPACKAGE_BUGREPORT=\"devel@open-fcoe.org\" -DPACKAGE_URL=\"\"  -DPACKAGE=\"fcoe-utils\" -DVERSION=\"1.0.24\" -I.  -I./include  -I./include -DSYSCONFDIR="\"/etc\""  -Wall -O2 -g -c -o lib/sa_timer.o  lib/sa_timer.c 
gcc -DPACKAGE_NAME=\"fcoe-utils\" -DPACKAGE_TARNAME=\"fcoe-utils\"  -DPACKAGE_VERSION=\"1.0.24\" -DPACKAGE_STRING=\"fcoe-utils\ 1.0.24\"  -DPACKAGE_BUGREPORT=\"devel@open-fcoe.org\" -DPACKAGE_URL=\"\"  -DPACKAGE=\"fcoe-utils\" -DVERSION=\"1.0.24\" -I.  -I./include  -I./include -DSYSCONFDIR="\"/etc\""  -Wall -O2 -g -c -o lib/sa_other.o  lib/sa_other.c 
gcc -DPACKAGE_NAME=\"fcoe-utils\" -DPACKAGE_TARNAME=\"fcoe-utils\"  -DPACKAGE_VERSION=\"1.0.24\" -DPACKAGE_STRING=\"fcoe-utils\ 1.0.24\"  -DPACKAGE_BUGREPORT=\"devel@open-fcoe.org\" -DPACKAGE_URL=\"\"  -DPACKAGE=\"fcoe-utils\" -DVERSION=\"1.0.24\" -I.  -I./include  -I./include -DSYSCONFDIR="\"/etc\""  -Wall -O2 -g -c -o lib/fip.o lib/fip.c 
gcc -DPACKAGE_NAME=\"fcoe-utils\" -DPACKAGE_TARNAME=\"fcoe-utils\"  -DPACKAGE_VERSION=\"1.0.24\" -DPACKAGE_STRING=\"fcoe-utils\ 1.0.24\"  -DPACKAGE_BUGREPORT=\"devel@open-fcoe.org\" -DPACKAGE_URL=\"\"  -DPACKAGE=\"fcoe-utils\" -DVERSION=\"1.0.24\" -I.  -I./include  -I./include -DSYSCONFDIR="\"/etc\""  -Wall -O2 -g -c -o lib/rtnetlink.o  lib/rtnetlink.c 
lib/rtnetlink.c: In Funktion »rtnl_getlinkname_handler«: 
lib/rtnetlink.c:374:20: Warnung: Variable »ifm« gesetzt, aber nicht  verwendet [-Wunused-but-set-variable] 
lib/rtnetlink.c: In Funktion »rtnl_find_vlan_handler«: 
lib/rtnetlink.c:416:20: Warnung: Variable »ifm« gesetzt, aber nicht  verwendet [-Wunused-but-set-variable] 
rm -f lib/libutil.a 
ar cru lib/libutil.a lib/fcoe_utils.o lib/sa_log.o lib/sa_select.o  lib/sa_timer.o lib/sa_other.o lib/fip.o lib/rtnetlink.o 
ranlib lib/libutil.a 
gcc -DPACKAGE_NAME=\"fcoe-utils\" -DPACKAGE_TARNAME=\"fcoe-utils\"  -DPACKAGE_VERSION=\"1.0.24\" -DPACKAGE_STRING=\"fcoe-utils\ 1.0.24\"  -DPACKAGE_BUGREPORT=\"devel@open-fcoe.org\" -DPACKAGE_URL=\"\"  -DPACKAGE=\"fcoe-utils\" -DVERSION=\"1.0.24\" -I.  -I./include  -I./include -DSYSCONFDIR="\"/etc\""  -Wall  -O2 -g -c -o  fcoeadm-fcoeadm.o `test -f 'fcoeadm.c' || echo './'`fcoeadm.c 
gcc -DPACKAGE_NAME=\"fcoe-utils\" -DPACKAGE_TARNAME=\"fcoe-utils\"  -DPACKAGE_VERSION=\"1.0.24\" -DPACKAGE_STRING=\"fcoe-utils\ 1.0.24\"  -DPACKAGE_BUGREPORT=\"devel@open-fcoe.org\" -DPACKAGE_URL=\"\"  -DPACKAGE=\"fcoe-utils\" -DVERSION=\"1.0.24\" -I.  -I./include  -I./include -DSYSCONFDIR="\"/etc\""  -Wall  -O2 -g -c -o  fcoeadm-fcoeadm_display.o `test -f 'fcoeadm_display.c' || echo  './'`fcoeadm_display.c 
fcoeadm_display.c: In Funktion »show_target_info«: 
fcoeadm_display.c:352:6: Warnung: Variable »rc« gesetzt, aber nicht  verwendet [-Wunused-but-set-variable] 
fcoeadm_display.c: In Funktion »display_adapter_info«: 
fcoeadm_display.c:1335:13: Warnung: Variable »hba_handle« gesetzt, aber  nicht verwendet [-Wunused-but-set-variable] 
gcc -Wall  -O2 -g  -L/usr/lib64 -lHBAAPI -ldl    -o fcoeadm  fcoeadm-fcoeadm.o fcoeadm-fcoeadm_display.o lib/libutil.a 
fcoeadm-fcoeadm_display.o: In function `hba_table_list_init': 
/root/fcoe/fcoe-utils/fcoeadm_display.c:1145: undefined reference to  `HBA_GetNumberOfAdapters' 
/root/fcoe/fcoe-utils/fcoeadm_display.c:1167: undefined reference to  `HBA_GetAdapterName' 
/root/fcoe/fcoe-utils/fcoeadm_display.c:1175: undefined reference to  `HBA_OpenAdapter' 
/root/fcoe/fcoe-utils/fcoeadm_display.c:1183: undefined reference to  `HBA_GetAdapterAttributes' 
/root/fcoe/fcoe-utils/fcoeadm_display.c:1186: undefined reference to  `HBA_CloseAdapter' 
/root/fcoe/fcoe-utils/fcoeadm_display.c:1195: undefined reference to  `HBA_GetAdapterPortAttributes' 
/root/fcoe/fcoe-utils/fcoeadm_display.c:1199: undefined reference to  `HBA_CloseAdapter' 
fcoeadm-fcoeadm_display.o: In function `hba_table_list_destroy': 
/root/fcoe/fcoe-utils/fcoeadm_display.c:1119: undefined reference to  `HBA_CloseAdapter' 
fcoeadm-fcoeadm_display.o: In function `get_device_capacity_v2': 
/root/fcoe/fcoe-utils/fcoeadm_display.c:535: undefined reference to  `HBA_ScsiReadCapacityV2' 
fcoeadm-fcoeadm_display.o: In function `fcoeadm_loadhba': 
/root/fcoe/fcoe-utils/fcoeadm_display.c:1127: undefined reference to  `HBA_LoadLibrary' 
fcoeadm-fcoeadm_display.o: In function `display_port_stats': 
/root/fcoe/fcoe-utils/fcoeadm_display.c:1277: undefined reference to  `HBA_GetPortStatistics' 
/root/fcoe/fcoe-utils/fcoeadm_display.c:1296: undefined reference to  `HBA_GetFC4Statistics' 
/root/fcoe/fcoe-utils/fcoeadm_display.c:1326: undefined reference to  `HBA_FreeLibrary' 
/root/fcoe/fcoe-utils/fcoeadm_display.c:1266: undefined reference to  `HBA_FreeLibrary' 
fcoeadm-fcoeadm_display.o: In function `fcoeadm_loadhba': 
/root/fcoe/fcoe-utils/fcoeadm_display.c:1127: undefined reference to  `HBA_LoadLibrary' 
fcoeadm-fcoeadm_display.o: In function `display_adapter_info': 
/root/fcoe/fcoe-utils/fcoeadm_display.c:1412: undefined reference to  `HBA_FreeLibrary' 
fcoeadm-fcoeadm_display.o: In function `fcoeadm_loadhba': 
/root/fcoe/fcoe-utils/fcoeadm_display.c:1127: undefined reference to  `HBA_LoadLibrary' 
fcoeadm-fcoeadm_display.o: In function `display_target_info': 
/root/fcoe/fcoe-utils/fcoeadm_display.c:1512: undefined reference to  `HBA_FreeLibrary' 
/root/fcoe/fcoe-utils/fcoeadm_display.c:1471: undefined reference to  `HBA_GetDiscoveredPortAttributes' 
fcoeadm-fcoeadm_display.o: In function `get_device_map': 
/root/fcoe/fcoe-utils/fcoeadm_display.c:917: undefined reference to  `HBA_GetFcpTargetMappingV2' 
fcoeadm-fcoeadm_display.o: In function `get_inquiry_data_v2': 
/root/fcoe/fcoe-utils/fcoeadm_display.c:451: undefined reference to  `HBA_ScsiInquiryV2' 
collect2: Fehler: ld gab 1 als Ende-Status zurück 
make: *** [fcoeadm] Fehler 1 


root@permain3:~/fcoe/fcoe-utils# lsb_release -a 
No LSB modules are available. 
Distributor ID: Ubuntu 
Description:    Ubuntu 12.10 
Release:        12.10 
Codename:       quantal 
root@permain3:~/fcoe/fcoe-utils# uname -a 
Linux permain3 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC  2012 x86_64 x86_64 x86_64 GNU/Linux 

root@permain3:~/fcoe/fcoe-utils# ls -la /usr/lib64/ 
insgesamt 856 
drwxr-xr-x  3 root root   4096 Nov 26 12:39 . 
drwxr-xr-x 11 root root   4096 Nov 24 21:19 .. 
-rw-r--r--  1 root root 184064 Nov 26 12:39 libHBAAPI.a 
-rwxr-xr-x  1 root root    949 Nov 26 12:39 libHBAAPI.la 
lrwxrwxrwx  1 root root     18 Nov 26 12:39 libHBAAPI.so ->  libHBAAPI.so.2.0.2 
lrwxrwxrwx  1 root root     18 Nov 26 12:39 libHBAAPI.so.2 ->  libHBAAPI.so.2.0.2 
-rwxr-xr-x  1 root root 132926 Nov 26 12:39 libHBAAPI.so.2.0.2 
-rw-r--r--  1 root root 329842 Nov 26 12:39 libhbalinux.a 
-rwxr-xr-x  1 root root    975 Nov 26 12:39 libhbalinux.la 
lrwxrwxrwx  1 root root     20 Nov 26 12:39 libhbalinux.so ->  libhbalinux.so.2.0.2 
lrwxrwxrwx  1 root root     20 Nov 26 12:39 libhbalinux.so.2 ->  libhbalinux.so.2.0.2 
-rwxr-xr-x  1 root root 200709 Nov 26 12:39 libhbalinux.so.2.0.2 
drwxr-xr-x  2 root root   4096 Nov 26 12:39 pkgconfig 

```

---

