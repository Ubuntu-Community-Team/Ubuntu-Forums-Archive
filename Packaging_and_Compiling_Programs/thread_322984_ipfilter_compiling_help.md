---
title: "ipfilter compiling help"
date: 2006-12-21
forum: Packaging and Compiling Programs
---

### Post by enatiello on 2006-12-21
howdy,
     I have been working to get ipfilter working with ubuntu server, and I have been making some headway, however I need a little help. ](*,) 

Thanks,
Ernest


Here are my build notes:
1. install these things:
build-essential byacc fakeroot libc6 libc6-dev libc6-i686 libelfg0 libelfg0-dev linux-source-2.6.15

2. build kernel
apt-get install linux-source-2.6.15
cp /boot/config-2.6.15-26-server /usr/src/linux-source-2.6.15/.config
ln -s /usr/src/linux-source-2.6.15 /usr/src/linux
cd /usr/src/linux
make menuconfig
(load alternat config file =  .config)
(make changes, if necessary)
(exit and then save)
make-kpkg clean
fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers
cd /usr/src
dpkg -i kernel-image-2.6.15.7-ubuntu1-custom_10.00.Custom_i386.deb
dpkg -i kernel-headers-2.6.15.7-ubuntu1-custom_10.00.Custom_i386.deb
rm /usr/src/linux
ln -s /usr/src/kernel-headers-2.6.15.7-ubuntu1-custom /usr/src/linux

3. empty the file:
/usr/include/linux/config.h

4. IPFilter
wget [http://coombs.anu.edu.au/~avalon/ip_fil4.1.16.tar.gz](http://coombs.anu.edu.au/~avalon/ip_fil4.1.16.tar.gz)
tar -xzvf ip_fil4.1.16.tar.gz

5. Linux-ify IPFilter
edit the Makefile
67,68c67
< # LINUXKERNEL=/usr/src/linux
< LINUXKERNEL=/usr/src/kernel-headers-2.6.15.7-ubuntu1-custom
---
> LINUXKERNEL=/usr/src/linux
85c84
< STATETOP_INC=
---
> #STATETOP_INC=
87d85
< STATETOP_INC=-I/usr/include
91c89
< STATETOP_LIB=-lncurses
---
> #STATETOP_LIB=-lncurses
93d90
< STATETOP_LIB=-L/usr/lib -lncurses

7. Build IPFilter
make clean-linux
make linux
make install-linux


Here is the output of "make linux"
... truncated for length ...

if [ ! -f /usr/lib/libelf.so ] ; then \
                (cd /usr/lib; a=`echo libelf.so.*|head -n 1`; \
                 if [ "$a" != "" ] ; then ln -s $a libelf.so; fi) \
        fi
cc -I. -ILinux-2.6.15.7-ubuntu1-custom-i686 -g -I.. -D_BSD_SOURCE     -DIPFILTER_LOOKUP -DIPFILTER_SCAN -DIPFILTER_LOG -DLINUX=20615 Linux-2.6.15.7-ubuntu1-custom-i686/ipnat.o Linux-2.6.15.7-ubuntu1-custom-i686/ipnat_y.o Linux-2.6.15.7-ubuntu1-custom-i686/ipnat_l.o -o Linux-2.6.15.7-ubuntu1-custom-i686/ipnat -LLinux-2.6.15.7-ubuntu1-custom-i686 -lipf  -lelf
cc -I. -ILinux-2.6.15.7-ubuntu1-custom-i686 -g -I.. -D_BSD_SOURCE     -DIPFILTER_LOOKUP -DIPFILTER_SCAN -DIPFILTER_LOG -DLINUX=20615 -c ../tools/ippool.c -o Linux-2.6.15.7-ubuntu1-custom-i686/ippool.o
cc -I. -ILinux-2.6.15.7-ubuntu1-custom-i686 -g -I.. -D_BSD_SOURCE     -DIPFILTER_LOOKUP -DIPFILTER_SCAN -DIPFILTER_LOG -DLINUX=20615 Linux-2.6.15.7-ubuntu1-custom-i686/ippool_y.o Linux-2.6.15.7-ubuntu1-custom-i686/ippool_l.o Linux-2.6.15.7-ubuntu1-custom-i686/kmem.o Linux-2.6.15.7-ubuntu1-custom-i686/ippool.o -o Linux-2.6.15.7-ubuntu1-custom-i686/ippool -LLinux-2.6.15.7-ubuntu1-custom-i686 -lipf -lelf
sh -c 'for i in ipf ipftest ipmon ippool ipnat ipscan ipsyncm ipsyncs; do /bin/rm -f ../$i; ln -s `pwd`/Linux-2.6.15.7-ubuntu1-custom-i686/$i ..; done'
make[1]: warning:  Clock skew detected.  Your build may be incomplete.
make[1]: Leaving directory `/export/home/enatiello/IPF/ip_fil4.1.16/Linux'
(cd Linux; make ipflkm LINUX=`uname -r | awk -F. ' { printf"%d",$1;for(i=1;i<NF&&i<3;i++){printf("%02d",$(i+1));}}'` TOP=.. "DEBUG=-g" "CC=cc" 'CFLAGS=-I$(TOP) -D_BSD_SOURCE    ' "IPFLOG=-DIPFILTER_LOG" "LOGFAC=-DLOGFAC=LOG_LOCAL0" "POLICY=-DIPF_DEFAULT_PASS=FR_PASS" "SOLARIS2=" "DEBUG=-g" "DCPU=`uname -m`" "LIBBPF=" "CPUDIR=`uname -s|sed -e 's@/@@g'`-`uname -r`-`uname -m`" "IPFBPF=" 'STATETOP_CFLAGS=' "BPFILTER=" 'STATETOP_INC=' 'STATETOP_LIB=' "BITS=" "OBJ=." "LOOKUP=-DIPFILTER_LOOKUP -DIPFILTER_SCAN" "COMPIPF=" 'SYNC=' 'ALLOPTS=-DIPFILTER_LOG -DIPFILTER_LOOKUP -DIPFILTER_SCAN -DIPFILTER_SYNC -DIPFILTER_CKSUM' 'LIBBPF=' "IPFLKM=-DIPFILTER_LKM" OBJ=`uname -s|sed -e 's@/@@g'`-`uname -r`-`uname -m` LINUXKERNEL=/usr/src/linux WORKDIR=`pwd`; cd ..)
make[1]: Entering directory `/export/home/enatiello/IPF/ip_fil4.1.16/Linux'
if [ 20615 -lt 20499 ] ; then \
                make Linux-2.6.15.7-ubuntu1-custom-i686/ipfilter.o; \
        else \
                (cd Linux-2.6.15.7-ubuntu1-custom-i686; unset MAKEFLAGS; make -C "/lib/modules/2.6.15.7-ubuntu1-custom/build" SUBDIRS="`pwd`" TOP="`pwd`/../.."  CPUDIR="Linux-2.6.15.7-ubuntu1-custom-i686" EXTRA_CFLAGS="-DLINUX=20615 -I.. -I`pwd`/.. -I`pwd`/../..  -DIPFILTER_LOOKUP -DIPFILTER_SCAN -DIPFILTER_LOG -O2" OBJ= modules); \
        fi
make[2]: Entering directory `/usr/src/linux-source-2.6.15'
  CC [M]  /export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686//linuxm.o
In file included from include/linux/interrupt.h:11,
                 from include/linux/rcuref.h:36,
                 from include/linux/fs.h:12,
                 from include/linux/mm.h:15,
                 from include/linux/skbuff.h:26,
                 from include/linux/if_ether.h:109,
                 from include/linux/netdevice.h:29,
                 from /export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686/../ipf-linux.h:23,
                 from /export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686//linuxm.c:2:
include/linux/hardirq.h:35:27: warning: "NR_IRQS" is not defined
In file included from /export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686/../ipf-linux.h:158,
                 from /export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686//linuxm.c:2:
/export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686/../../ip_compat.h:37:5: warning: "SOLARIS2" is not defined
/export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686/../../ip_compat.h:1495:5: warning: "BSD" is not defined
/export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686/../../ip_compat.h:1531:7: warning: "BSD" is not defined
/export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686/../../ip_compat.h:1761:6: warning: "BSD" is not defined
In file included from /export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686/../ipf-linux.h:159,
                 from /export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686//linuxm.c:2:
/export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686/../../ip_fil.h:1330:9: warning: "_BSDI_VERSION" is not defined
/export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686/../../ip_fil.h:1330:38: warning: "__FreeBSD_version" is not defined
/export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686/../../ip_fil.h:1331:8: warning: "NetBSD" is not defined
/export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686/../../ip_fil.h:1376:8: warning: "BSD" is not defined
/export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686/../../ip_fil.h:1424:7: warning: "__FreeBSD_version" is not defined
In file included from /export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686/../ipf-linux.h:164,
                 from /export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686//linuxm.c:2:
/export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686/../../ip_frag.h:85:31: warning: "BSD" is not defined
In file included from /export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686/../../ip_pool.h:25,
                 from /export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686/../ipf-linux.h:167,
                 from /export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686//linuxm.c:2:
/export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686/../../radix_ipf.h:164:43: warning: "IRIX" is not defined
  CC [M]  /export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686//ip_film.o
In file included from include/linux/interrupt.h:11,
                 from include/linux/rcuref.h:36,
                 from include/linux/fs.h:12,
                 from include/linux/mm.h:15,
                 from include/linux/skbuff.h:26,
                 from include/linux/if_ether.h:109,
                 from include/linux/netdevice.h:29,
                 from include/net/sock.h:48,
                 from include/net/request_sock.h:22,
                 from include/linux/ip.h:84,
                 from include/net/ip.h:28,
                 from /export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686//ip_film.c:7:
include/linux/hardirq.h:35:27: warning: "NR_IRQS" is not defined
In file included from /export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686/../ipf-linux.h:158,
                 from /export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686//ip_film.c:9:
/export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686/../../ip_compat.h:37:5: warning: "SOLARIS2" is not defined
/export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686/../../ip_compat.h:1495:5: warning: "BSD" is not defined
/export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686/../../ip_compat.h:1531:7: warning: "BSD" is not defined
/export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686/../../ip_compat.h:1761:6: warning: "BSD" is not defined
In file included from /export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686/../ipf-linux.h:159,
                 from /export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686//ip_film.c:9:
/export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686/../../ip_fil.h:1330:9: warning: "_BSDI_VERSION" is not defined
/export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686/../../ip_fil.h:1330:38: warning: "__FreeBSD_version" is not defined
/export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686/../../ip_fil.h:1331:8: warning: "NetBSD" is not defined
/export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686/../../ip_fil.h:1376:8: warning: "BSD" is not defined
/export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686/../../ip_fil.h:1424:7: warning: "__FreeBSD_version" is not defined
In file included from /export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686/../ipf-linux.h:164,
                 from /export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686//ip_film.c:9:
/export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686/../../ip_frag.h:85:31: warning: "BSD" is not defined
In file included from /export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686/../../ip_pool.h:25,
                 from /export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686/../ipf-linux.h:167,
                 from /export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686//ip_film.c:9:
/export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686/../../radix_ipf.h:164:43: warning: "IRIX" is not defined
/export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686//ip_film.c: In function ‘ipfattach’:
/export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686//ip_film.c:141: warning: assignment from incompatible pointer type
/export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686//ip_film.c:142: warning: assignment makes integer from pointer without a cast
/export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686//ip_film.c: In function ‘fr_fastroute’:
/export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686//ip_film.c:646: error: ‘ip_finish_output’ undeclared (first use in this function)
/export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686//ip_film.c:646: error: (Each undeclared identifier is reported only once
/export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686//ip_film.c:646: error: for each function it appears in.)
/export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686//ip_film.c: In function ‘fr_ifpaddr’:
/export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686//ip_film.c:679: warning: implicit declaration of function ‘__in_dev_get’
/export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686//ip_film.c:679: warning: assignment makes pointer from integer without a cast
make[3]: *** [/export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686//ip_film.o] Error 1
make[2]: *** [_module_/export/home/enatiello/IPF/ip_fil4.1.16/Linux/Linux-2.6.15.7-ubuntu1-custom-i686] Error 2
make[2]: Leaving directory `/usr/src/linux-source-2.6.15'
make[1]: *** [ipflkm] Error 2
make[1]: Leaving directory `/export/home/enatiello/IPF/ip_fil4.1.16/Linux'

---

