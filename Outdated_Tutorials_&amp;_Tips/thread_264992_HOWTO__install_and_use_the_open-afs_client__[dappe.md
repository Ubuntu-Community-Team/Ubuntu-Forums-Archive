---
title: "HOWTO : install and use the open-afs client  [dapper]"
date: 2006-09-25
forum: Outdated Tutorials &amp; Tips
---

### Post by terminatorkobold on 2006-09-25
Hello Everybody,

Tis howto is for the people who want to connect to an afs cell witt the open-afs client. It is not a guide to install an afs server.

For the client to run you must unfortunately compile a kernel module for the kernel that you are using. This means that you have to recompile the module each time tat you update your kernel. 
You need to have the linux-headers package and the kernel-package package installed for the kernel you are running. (you can use apt-get or synaptic)

    ```
 sudo apt-get install linux-headers-x.x.x kernel-package 
```

Where x.x.x is the version of the kernel that you are using.

Then you have to get the openafs-modules-source package and untar the tarball it gives you:

    ```
 sudo apt-get install openafs-modules-source
 cd /usr/src
 sudo tar xzvf openafs.tar.gz 
```

Then you need to build the openafs kernel module. We will create a new .deb file in your /usr/src directory and then use dpkg to install it. A very big lot of text will defile during the process, it is normal.

    ```
cd /usr/src/linux-headers-x.x.x.
 sudo make-kpkg configure 
 (lots of stuff will fly by)
 sudo make-kpkg modules_image 
 (if it asks about the version number, don't abort)
```

Finally nstall the newly created openafs-modules package:

    ```
 sudo dpkg -i /usr/src/openafs-modules-x.x.x....deb 
```

This is the end of the part that you need to do every time that you update your kernel.

Now get the openafs-client and kerberos packages (if you need the kerberos 4 packages, also install the krb4 equivalents):

    ```
 sudo apt-get install openafs-client openafs-krb5 krb5-user krb5-config 
```

Configuration:
During the process you will be asked to give the name of the AFS cell, the size of the AFS cache and the default kerberos realm:
    
    ```
 default Kerberos version 5 realm: <blank>
 AFS cell: name of the cell you want to connect to. Ask the administrator.
 AFS cache: 50000 
```
    

If you wish for the AFS client to start at boot, edit /etc/openafs/afs.conf.client:

    change
    AFS_CLIENT=false
    to
    AFS_CLIENT=true

Load the newly made module (I don't know why, bu it is not automatically loaded at startup)

    ```
 sudo insmod /lib/modules/x.x.x/fs/openafs.ko 
```

Start the openafs client:

    ```
 sudo /etc/init.d/openafs-client start 
```

Get an AFS token using kerberos

    ```
 klog -principal your_username -cell the_name_of_the_AFS_server 
```

You can then access the afs server in the /afs/the_name_of_the_AFS_server
directory.


Yours

Christophe Schlicht

---

### Post by bollocks00 on 2006-10-13
I get down to the line:

```
sudo dpkg -i /usr/src/openafs-modules-2.6.17-10-386.deb
```

which gives

```
dpkg: error processing /usr/src/openafs-modules-2.6.17-10-386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /usr/src/openafs-modules-2.6.17-10-386.deb

```

Has the openafs-module been created for 2.6.17 yet?

---

### Post by terminatorkobold on 2006-10-14
> **bollocks00 said:**
> I get down to the line:

```
sudo dpkg -i /usr/src/openafs-modules-2.6.17-10-386.deb
```

which gives

```
dpkg: error processing /usr/src/openafs-modules-2.6.17-10-386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /usr/src/openafs-modules-2.6.17-10-386.deb

```

Has the openafs-module been created for 2.6.17 yet?



There should be no problem. The .deb file should have been created with the make-kpkg command. You con look in Nautilus if the file was created in another place like/usr/src/linux-headers-x.x.x/
If it is not the case, then you had a problem with the make-kpkg command. Did it give you an error?

yours

Christophe

---

### Post by bollocks00 on 2006-10-16
Christophe,

I believe the configure went fine, but the modules_image seems to have some errors:

```
lenny@IBM:/usr/src/linux-headers-2.6.17-10-386$ sudo make-kpkg modules_image
exec debian/rules  DEBIAN_REVISION=2.6.17-10-386-10.00.Custom  modules_image 
====== making .config because of Makefile ======

test -f .config || test ! -f .config.save || \
                            cp -pf .config.save .config
test -f .config || test ! -f .config || \
                            cp -pf .config .config
test -f .config || test ! -f ./debian/config || \
                            cp -pf ./debian/config  .config
test -f .config || (echo "*** Need a config file .config" && false)
for module in /usr/src/modules/openafs ; do                       \
          if test -d  $module; then                                \
            (cd $module;                                          \
              if ./debian/rules KVERS="2.6.17-10-386" KSRC="/usr/src/linux-headers-2.6.17-10-386" \
                             KMAINT="Unknown Kernel Package Maintainer" KEMAIL="unknown@unconfigured.in.etc.kernel-pkg.conf"      \
                             KPKG_DEST_DIR="/usr/src/linux-headers-2.6.17-10-386/.."       \
                             KPKG_MAINTAINER="Unknown Kernel Package Maintainer"        \
                             KPKG_EXTRAV_ARG=""        \
                             ARCH="i386"                  \
                             KDREV="2.6.17-10-386-10.00.Custom" kdist_image; then    \
                  echo "Module $module processed fine";            \
              else                                                  \
                   echo "Module $module failed.";                  \
                   if [ "X" != "X" ]; then      \
                      echo "Perhaps $module does not understand --rootcmd?";  \
                      echo "If you see messages that indicate that it is not"; \
                      echo "in fact being built as root, please file a bug ";  \
                      echo "against $module.";                     \
                   fi;                                              \
                   echo "Hit return to Continue";                   \
                 read ans;                                        \
              fi;                                                   \
             );                                                    \
          else                                                      \
               echo "Module $module does not exist";               \
               echo "Hit return to Continue?";                      \
          fi;                                                       \
        done
make[1]: Entering directory `/usr/src/modules/openafs'
make only_libafs
make[2]: Entering directory `/usr/src/modules/openafs'
make build TARGET=libafs
make[3]: Entering directory `/usr/src/modules/openafs'
make libafs DEST=/usr/src/modules/openafs/i386_linux26/dest COMPILE_PART2B=all DESTDIR=
make[4]: Entering directory `/usr/src/modules/openafs'
cd src && cd config && make all
make[5]: Entering directory `/usr/src/modules/openafs/src/config'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/usr/src/modules/openafs/src/config'
src/config/config src/libafs/MakefileProto.LINUX src/libafs/Makefile i386_linux26
Wrote new makefile 'src/libafs/Makefile'.
cd src && cd pinstall && make all
make[5]: Entering directory `/usr/src/modules/openafs/src/pinstall'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/usr/src/modules/openafs/src/pinstall'
cd src && cd lwp && make depinstall
make[5]: Entering directory `/usr/src/modules/openafs/src/lwp'
make[5]: Nothing to be done for `depinstall'.
make[5]: Leaving directory `/usr/src/modules/openafs/src/lwp'
cd src && cd rx && make depinstall
make[5]: Entering directory `/usr/src/modules/openafs/src/rx'
make[5]: Nothing to be done for `depinstall'.
make[5]: Leaving directory `/usr/src/modules/openafs/src/rx'
cd src && cd rxgen && make all
make[5]: Entering directory `/usr/src/modules/openafs/src/rxgen'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/usr/src/modules/openafs/src/rxgen'
cd src && cd procmgmt && make all
make[5]: Entering directory `/usr/src/modules/openafs/src/procmgmt'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/usr/src/modules/openafs/src/procmgmt'
cd src && cd des && make all 
make[5]: Entering directory `/usr/src/modules/openafs/src/des'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/usr/src/modules/openafs/src/des'
cd src && cd util && make all
make[5]: Entering directory `/usr/src/modules/openafs/src/util'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/usr/src/modules/openafs/src/util'
cd src && cd comerr && make all
make[5]: Entering directory `/usr/src/modules/openafs/src/comerr'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/usr/src/modules/openafs/src/comerr'
cd src && cd ubik && make depinstall
make[5]: Entering directory `/usr/src/modules/openafs/src/ubik'
Makefile:174: warning: overriding commands for target `/usr/src/modules/openafs/debian/tmp/bin/udebug'
Makefile:171: warning: ignoring old commands for target `/usr/src/modules/openafs/debian/tmp/bin/udebug'
make[5]: Nothing to be done for `depinstall'.
make[5]: Leaving directory `/usr/src/modules/openafs/src/ubik'
cd src && cd auth && make depinstall
make[5]: Entering directory `/usr/src/modules/openafs/src/auth'
make[5]: Nothing to be done for `depinstall'.
make[5]: Leaving directory `/usr/src/modules/openafs/src/auth'
cd src && cd vlserver && make depinstall
make[5]: Entering directory `/usr/src/modules/openafs/src/vlserver'
make[5]: Nothing to be done for `depinstall'.
make[5]: Leaving directory `/usr/src/modules/openafs/src/vlserver'
cd src && cd rxkad && make depinstall
make[5]: Entering directory `/usr/src/modules/openafs/src/rxkad'
make[5]: Nothing to be done for `depinstall'.
make[5]: Leaving directory `/usr/src/modules/openafs/src/rxkad'
cd src && cd fsint && make depinstall
make[5]: Entering directory `/usr/src/modules/openafs/src/fsint'
make[5]: Nothing to be done for `depinstall'.
make[5]: Leaving directory `/usr/src/modules/openafs/src/fsint'
cd src && cd libacl && make depinstall
make[5]: Entering directory `/usr/src/modules/openafs/src/libacl'
make[5]: Nothing to be done for `depinstall'.
make[5]: Leaving directory `/usr/src/modules/openafs/src/libacl'
cd src && cd afs && make depinstall
make[5]: Entering directory `/usr/src/modules/openafs/src/afs'
case i386_linux26 in \
                pmax_ul43 | pmax_ul43a) \
                        /usr/src/modules/openafs/src/pinstall/pinstall longc_procs.h /usr/src/modules/openafs/include/afs ;; \
        esac
make[5]: Leaving directory `/usr/src/modules/openafs/src/afs'
cd src && cd dir && make depinstall
make[5]: Entering directory `/usr/src/modules/openafs/src/dir'
make[5]: Nothing to be done for `depinstall'.
make[5]: Leaving directory `/usr/src/modules/openafs/src/dir'
cd src && cd rxstat && make depinstall
make[5]: Entering directory `/usr/src/modules/openafs/src/rxstat'
make[5]: Nothing to be done for `depinstall'.
make[5]: Leaving directory `/usr/src/modules/openafs/src/rxstat'
cd src && cd sys && make depinstall
make[5]: Entering directory `/usr/src/modules/openafs/src/sys'
make[5]: Leaving directory `/usr/src/modules/openafs/src/sys'
cd src && cd libafs && make all
make[5]: Entering directory `/usr/src/modules/openafs/src/libafs'
Makefile.common:50: warning: overriding commands for target `.c.o'
/usr/src/modules/openafs/src/config/Makefile.config:132: warning: ignoring old commands for target `.c.o'
Makefile:163: target `openafs.ko' given more than once in the same rule.
Makefile:168: warning: overriding commands for target `openafs.ko'
Makefile:164: warning: ignoring old commands for target `openafs.ko'
Makefile:200: warning: overriding commands for target `/usr/src/modules/openafs/debian/tmp/lib/openafs/openafs.ko'
Makefile:197: warning: ignoring old commands for target `/usr/src/modules/openafs/debian/tmp/lib/openafs/openafs.ko'
rm -f h net netinet sys rpc
ln -fs rx rpc
for m in SP ; do \
                KDIR=MODLOAD-2.6.17-10-386-$m; \
                mkdir -p ${KDIR}; \
                ln -fs ../Makefile ${KDIR}/Makefile.afs ; \
                ln -fs ../Makefile.common ${KDIR}/Makefile.common; \
                ln -fs ../config ${KDIR}/config; \
        done 
rm -f h 
rm -f sys
rm -f netinet 
if [ -d /usr/src/linux-headers-2.6.17-10-386/include2 ] ; then                  \
            ln -fs /usr/src/linux-headers-2.6.17-10-386/include2/asm/../linux h       ; \
            ln -fs /usr/src/linux-headers-2.6.17-10-386/include2/asm/../linux sys     ; \
            ln -fs /usr/src/linux-headers-2.6.17-10-386/include2/asm/../linux netinet ; \
        else                                                            \
            ln -fs /usr/src/linux-headers-2.6.17-10-386/include/linux h               ; \
            ln -fs /usr/src/linux-headers-2.6.17-10-386/include/linux sys             ; \
            ln -fs /usr/src/linux-headers-2.6.17-10-386/include/linux netinet         ; \
        fi
rm -f linux 
ln -fs /usr/src/linux-headers-2.6.17-10-386/include/linux linux 
rm -f net 
ln -fs /usr/src/linux-headers-2.6.17-10-386/include/net net 
rm -f asm-generic
ln -fs /usr/src/linux-headers-2.6.17-10-386/include/asm-generic asm-generic
rm -f asm
ln -fs /usr/src/linux-headers-2.6.17-10-386/include/asm-i386 asm
for m in SP ; do \
                KDIR=MODLOAD-2.6.17-10-386-$m ; \
                echo Building in directory: ${KDIR} ; \
                if [ "$m" = "MP" ] ; then \
                        SMP_DEF="-DAFS_SMP  " ; \
                        TARG="libafs.mp" ; \
                elif [ "$m" = "EP" ] ; then \
                        SMP_DEF="-DAFS_SMP  " ; \
                        TARG="libafs.ep" ; \
                elif [ "$m" = "BM" ] ; then \
                        SMP_DEF="-DAFS_SMP  " ; \
                        TARG="libafs.bm" ; \
                else  \
                        SMP_DEF=" " ; \
                        TARG=libafs ; \
                fi ; \
                cd ${KDIR} ; \
                make -f Makefile.afs SMP_DEF="${SMP_DEF}" linux_compdirs_${TARG} CLIENT=2.6.17-10-386 KDIR=${KDIR} || exit $?; \
                cd ../ ; \
        done
Building in directory: MODLOAD-2.6.17-10-386-SP
make[6]: Entering directory `/usr/src/modules/openafs/src/libafs/MODLOAD-2.6.17-10-386-SP'
Makefile.common:50: warning: overriding commands for target `.c.o'
/usr/src/modules/openafs/src/config/Makefile.config:132: warning: ignoring old commands for target `.c.o'
Makefile.afs:163: target `openafs.ko' given more than once in the same rule.
Makefile.afs:168: warning: overriding commands for target `openafs.ko'
Makefile.afs:164: warning: ignoring old commands for target `openafs.ko'
Makefile.afs:200: warning: overriding commands for target `/usr/src/modules/openafs/debian/tmp/lib/openafs/openafs.ko'
Makefile.afs:197: warning: ignoring old commands for target `/usr/src/modules/openafs/debian/tmp/lib/openafs/openafs.ko'
make[6]: Circular openafs.ko <- openafs.ko dependency dropped.
make[6]: Circular openafs.ko <- openafs.ko dependency dropped.
env EXTRA_CFLAGS="" /usr/src/modules/openafs/src/libafs/make_kbuild_makefile.pl MODLOAD-2.6.17-10-386-SP openafs.ko /usr/src/modules/openafs/src/config/Makefile.config Makefile.afs Makefile.common
env EXTRA_CFLAGS="" make -C /usr/src/linux-headers-2.6.17-10-386 M=/usr/src/modules/openafs/src/libafs/MODLOAD-2.6.17-10-386-SP modules
make[7]: Entering directory `/usr/src/linux-headers-2.6.17-10-386'
  CC [M]  /usr/src/modules/openafs/src/libafs/MODLOAD-2.6.17-10-386-SP/afs_analyze.o
In file included from /usr/src/modules/openafs/src/afs/afs_osi.h:443,
                 from /usr/src/modules/openafs/src/rx/rx_clock.h:88,
                 from /usr/src/modules/openafs/src/rx/rx.h:35,
                 from /usr/src/modules/openafs/src/afs/afsincludes.h:26,
                 from /usr/src/modules/openafs/src/libafs/MODLOAD-2.6.17-10-386-SP/afs_analyze.c:36:
/usr/src/modules/openafs/src/afs/LINUX/osi_machdep.h:55:2: error: #error Not sure what to do about rlim (should be in the Linux task struct somewhere....)
make[8]: *** [/usr/src/modules/openafs/src/libafs/MODLOAD-2.6.17-10-386-SP/afs_analyze.o] Error 1
make[7]: *** [_module_/usr/src/modules/openafs/src/libafs/MODLOAD-2.6.17-10-386-SP] Error 2
make[7]: Leaving directory `/usr/src/linux-headers-2.6.17-10-386'
make[6]: *** [openafs.ko] Error 2
make[6]: Leaving directory `/usr/src/modules/openafs/src/libafs/MODLOAD-2.6.17-10-386-SP'
make[5]: *** [linux_compdirs] Error 2
make[5]: Leaving directory `/usr/src/modules/openafs/src/libafs'
make[4]: *** [libafs] Error 2
make[4]: Leaving directory `/usr/src/modules/openafs'
make[3]: *** [build] Error 2
make[3]: Leaving directory `/usr/src/modules/openafs'
make[2]: *** [only_libafs] Error 2
make[2]: Leaving directory `/usr/src/modules/openafs'
make[1]: *** [build-modules-stamp] Error 2
make[1]: Leaving directory `/usr/src/modules/openafs'
Module /usr/src/modules/openafs failed.
Hit return to Continue

```

Do I need to download some other package before I try this command?
Thanks.

---

### Post by yangtj207 on 2006-10-22
Hello,
   This is what I got:
sudo dpkg -i /usr/src/openafs-modules-2.6.15-27-386_1.4.1-2+10.00.Custom_i386.deb
dpkg: status database area is locked by another proces

Does it matter? Thank you.

T.J.

---

### Post by terminatorkobold on 2006-10-24
> **bollocks00 said:**
> Christophe,

I believe the configure went fine, but the modules_image seems to have some errors:

Do I need to download some other package before I try this command?
Thanks.

Hello bollocks00,

I am sorry bu this goes beyond my knowledge of the system. I am by far not a linux guru, but perhaps somebody else can answer your question.

Yours

Christophe

---

### Post by terminatorkobold on 2006-10-24
> **yangtj207 said:**
> Hello,
   This is what I got:
sudo dpkg -i /usr/src/openafs-modules-2.6.15-27-386_1.4.1-2+10.00.Custom_i386.deb
dpkg: status database area is locked by another proces

Does it matter? Thank you.

T.J.

Hi,

If you have another package manager openned at that time (aptitude or synaptic) you have to close it before you can run the dpkg command.

Yours

Christophe

---

### Post by JDahl on 2006-10-26
Openafs currently doesn't work with kernel 2.6.17, which can be
quite a showstopper for Edgy if you rely on openafs (as I do):
[http://ubuntuforums.org/showthread.php?p=1665690#post1665690](http://ubuntuforums.org/showthread.php?p=1665690#post1665690)


There's has been a much easier of building openafs kernel modules 
for quite some time using module-assistant.

From /usr/share/doc/openafs-client/README.modules:

  First, install module-assistant and then prepare the kernel headers and
  install openafs-modules-source:

      apt-get install module-assistant
      module-assistant prepare openafs-modules

  (If you want to build modules for a different kernel than your currently
  running one, pass the -l flag to module-assistant.  See the man page.)
  module-assistant may be able to find the right packages itself or it may
  tell you to install particular packages.  Once you've finished with
  that, build the module with:

      module-assistant auto-build openafs-modules

---

### Post by Sethiano on 2006-10-31
Hi!

I've been trying to install open afs for quite some time now, and I can't get it to work.

Im on the 2.6.15-27-383 kernel, and I think there is something wrong with the header packages for this version.

When I'm trying to build with "kpgk-make modules_image" or with the "
module-assistant auto-build openafs-modules" I'll get this:
```

make[6]: Entering directory `/usr/src/linux-headers-2.6.15-27-386'         
 &#9474; Makefile:536: /usr/src/linux-headers-2.6.15-27-386/arch/i386/Makefile:     
 &#9474; No such file or directory                                                  
 &#9474; make[6]: *** No rule to make target                                        
 &#9474; `/usr/src/linux-headers-2.6.15-27-386/arch/i386/Makefile'.  Stop.       

```

If i look into the header kernel package in the /usr/src/ i see that the folder "arch" is a "broken link" along with many other folders.
I downloaded a header package for a previous version and it contained all the folders as folders and not as broken links.

Now, how will I solve this problem?

Thanks in advance!

---

### Post by emmanuelepig on 2006-11-01
hello,

I am not sure that it is a problem with kernel 2.6.17, maybe it is something related to Edgy, because I had afs working with Dapper (on an ibook g4) with kernel 2.6.17.0, then I upgraded to Edgy and I was not able to use afs anymore (by the way, I used the guide here,  plus module-assistant, as you describe...  thank you, I could not survive without it).
I tried installing afs again, but nothing; so I installed Dapper again with kernel 2.6.17.14 and I was able to install and use afs with no problems.
                                          emmanuele


> **JDahl said:**
> Openafs currently doesn't work with kernel 2.6.17, which can be
quite a showstopper for Edgy if you rely on openafs (as I do):
[http://ubuntuforums.org/showthread.php?p=1665690#post1665690](http://ubuntuforums.org/showthread.php?p=1665690#post1665690)


There's has been a much easier of building openafs kernel modules 
for quite some time using module-assistant.

From /usr/share/doc/openafs-client/README.modules:

  First, install module-assistant and then prepare the kernel headers and
  install openafs-modules-source:

      apt-get install module-assistant
      module-assistant prepare openafs-modules

  (If you want to build modules for a different kernel than your currently
  running one, pass the -l flag to module-assistant.  See the man page.)
  module-assistant may be able to find the right packages itself or it may
  tell you to install particular packages.  Once you've finished with
  that, build the module with:

      module-assistant auto-build openafs-modules

---

### Post by JDahl on 2006-11-01
Openafs 1.4.2 (included in Debian Unstable) works fine with never kernels.
To build a package from Debian's source-package do the following:

1)  Make a directory "openafs" and download the packages to it from:
$ mkdir openafs; cd openafs
$ wget [http://ftp.debian.org/debian/pool/main/o/openafs/openafs_1.4.2.orig.tar.gz](http://ftp.debian.org/debian/pool/main/o/openafs/openafs_1.4.2.orig.tar.gz)
$ wget [http://ftp.debian.org/debian/pool/main/o/openafs/openafs_1.4.2-2.diff.gz](http://ftp.debian.org/debian/pool/main/o/openafs/openafs_1.4.2-2.diff.gz)

2) Unpack and patch
$ tar xzvf openafs_1.4.2.orig.tar.gz
$ zcat openafs_1.4.2-2.diff.gz | patch -p0

3) Install necessary dependencies 
$ sudo apt-get build-dep openafs-client
$ sudo apt-get install build-essential fakeroot

4) Build the Debian packages (takes a long time)
$ cd openafs-1.4.2
$ chmod u+x debian/rules
$ dpkg-buildpackage -rfakeroot
Compilation may fail if you don't have all dependencies installed. Just install the missing packages and rebuild.

5) Install the packages
$ sudo dpkg -i ../openafs-modules-source_1.4.2-2_all.deb openafs-client_1.4.2-2_i386.deb

6) Build the kernel module
$ sudo apt-get install module-assistant
$ sudo module-assistant prepare openafs-modules
$ sudo module-assistant auto-build openafs-modules
$ sudo dpkg -i openafs-modules-2.6.17-10-386_1.4.2-2+2.6.17-10.33_i386.deb

7) Install the packages (and say [Y]es to overwriting /etc config scripts; there's a bug in the old ones)
$ sudo dpkg -i /usr/src/openafs-modules-2.6.17-10-386_1.4.2-2+2.6.17-10.33_i386.deb


That did if it for me, at least.

---

### Post by Sethiano on 2006-11-03
```
dpkg-deb: parse error, in file `debian/openafs-dbg/DEBIAN/control' near line 6 package `openafs-dbg':
 `Depends' field, reference to `openafs-fileserver': error in version: version string is empty

```

This is what i get when I try run the ```
dpkg-buildpackage -rfakeroot
``` command.

Any suggestions?

Thanks!

---

### Post by JDahl on 2006-11-03
I don't know where that error comes from.

This is line 6 from my version of
debian/openafs-dbg/DEBIAN/control

Depends: openafs-fileserver (= 1.4.2-2)

I don't see any reason why yours should be empty. Maybe you can just
manually insert the fileserver version number?

It probably wouldn't take the Ubuntu package maintainer long to update the 
openafs package, though, which would be the preferred solution to this problem.

---

### Post by Sethiano on 2006-11-06
> **JDahl said:**
> Openafs 1.4.2 (included in Debian Unstable) works fine with never kernels.
To build a package from Debian's source-package do the following:

1)  Make a directory "openafs" and download the packages to it from:
$ mkdir openafs; cd openafs
$ wget [http://ftp.debian.org/debian/pool/main/o/openafs/openafs_1.4.2.orig.tar.gz](http://ftp.debian.org/debian/pool/main/o/openafs/openafs_1.4.2.orig.tar.gz)
$ wget [http://ftp.debian.org/debian/pool/main/o/openafs/openafs_1.4.2-2.diff.gz](http://ftp.debian.org/debian/pool/main/o/openafs/openafs_1.4.2-2.diff.gz)

2) Unpack and patch
$ tar xzvf openafs_1.4.2.orig.tar.gz
$ zcat openafs_1.4.2-2.diff.gz | patch -p0

3) Install necessary dependencies 
$ sudo apt-get build-dep openafs-client
$ sudo apt-get install build-essential fakeroot

4) Build the Debian packages (takes a long time)
$ cd openafs-1.4.2
$ chmod u+x debian/rules
$ dpkg-buildpackage -rfakeroot
Compilation may fail if you don't have all dependencies installed. Just install the missing packages and rebuild.

5) Install the packages
$ sudo dpkg -i ../openafs-modules-source_1.4.2-2_all.deb openafs-client_1.4.2-2_i386.deb

6) Build the kernel module
$ sudo apt-get install module-assistant
$ sudo module-assistant prepare openafs-modules
$ sudo module-assistant auto-build openafs-modules
$ sudo dpkg -i openafs-modules-2.6.17-10-386_1.4.2-2+2.6.17-10.33_i386.deb

7) Install the packages (and say [Y]es to overwriting /etc config scripts; there's a bug in the old ones)
$ sudo dpkg -i /usr/src/openafs-modules-2.6.17-10-386_1.4.2-2+2.6.17-10.33_i386.deb


That did if it for me, at least.

So, I did a upgrade to Edgy Eft with kernel 2.6.17-10-386 and your guide workt perfectly!

Thanks for all the help!

P.S Now that we know this, **JDahl** and other users should be aware that there is possible to run AFS perfectly on Edgy Eft.

---

### Post by jamesotron on 2006-11-14
I managed to get openafs-modules to build on my Edgy ppc64 (G5 iMac) machine and all seems to be working except for a stack trace in aklog:

```

[16:31][jnt@bingo]~$ kinit jtys003
Password for jtys003@EC.AUCKLAND.AC.NZ: 
[16:32][jnt@bingo]~$ aklog
stackcheck = 0: stack = 0 
topstack = 0xf7fcb03c: stackptr = 0xf7f9b008: stacksize = 0x30000
Wed Nov 15 16:32:04 2006 LWP: stack overflow in process IO MANAGER!
Aborted (core dumped)

```

If anyone has any suggestions I'd be glad to hear them.

---

### Post by krugger on 2006-12-08
The current openAFS version in the universe repositories is still 1.4.1. Why is that? Debian packages for 1.4.2 which solve the rlim problem that is happening with the 2.6.17/18 kernel has been in debian testing for about a month now. Who do I have to mail to get openAFS to 1.4.2 in universe?

And version 1.5.12 of AFS lists only Windows and Mac support.

Besides suggesting that you report the stack overflow to the AFS people, I can't help much more.

EDIT: my noobiness made me forget to check if it had been released in feisty, lets see if I a backport is possible

---

### Post by bodhi.zazen on 2006-12-15
Nice How-to

This thread has been added to the UDSF wiki.

[Open-afs_client](http://doc.gwos.org/index.php/Open-afs_client)

---

### Post by JMoriarty on 2006-12-30
Backport openafs-1.4.2 from Feisty:

1. Edit /etc/apt/sources.list to add these lines:
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) feisty universe multiverse 
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) feisty universe multiverse 

This will add the feisty repositories.
2. Edit /etc/apt/preferences file to add:
Package: *
Pin: release a=feisty
Pin-Priority: 200

Package: openafs-modules-source
Pin: release a=feisty
Pin-Priority: 999

This will deactivate all feisty packages except the openafs-modules-sources package.

After that, proceed as usual with openafs installation.

---

### Post by Luggy on 2007-08-29
I've been following the original instructions and I'm encountering a strange problem. When I try and start afs I get the following error 
```

paul@paul-desktop:~$ sudo /etc/init.d/openafs-client start
Password:
Starting AFS services: afsd.
afsd: All AFS daemons started.
afsd: Can't mount AFS on /afs(22)

```

Any ideas?

---

### Post by lamnk on 2007-09-29
> **Luggy said:**
> I've been following the original instructions and I'm encountering a strange problem. When I try and start afs I get the following error 
```

afsd: Can't mount AFS on /afs(22)

```

I think it's very obvious from the output that afsd has no write access on /afs ...

---

### Post by free-martin on 2008-05-05
...warm up...

Hello, 

I have exactly the same problem as Luggy and lamnk.
After surfing around I found this thread and was quite lucky to be able to compile the module.
But this error 
```

afsd: Can't mount AFS on /afs(22)

```
doesn't disappear. The module openafs is loaded.

Ideas would be appreciated.

---

### Post by pjomega on 2008-06-14
This is an access error. It usually means that the openafs client doesn't have permission mount the afs root (usually the root.afs volume) on /afs. The client /afs DIRECTORY doesn't have to be writeable, or even readable really, since the afs module is mounting the filesystem on top of it with root privileges. Typically, the afs root ACL is set so that the system:anyuser has read/list privileges. You may get this error if 
1) afs root read/list privileges are restricted to certain principals which include you.
      Fix: You are not authenticated; log in with aklog before starting the client
2) afs root read/list privileges are restricted to certain principals which do not include you.
      Fix: The admin is lazy or just doesn't like you; go bug him/her for for proper access
3) no root volume has been set in the afs fileserver
      Fix: a)The admin is lazy; go bug him to finish setting up
           b)The admin has set a volume other than root.afs as the root of the filesystem; bug your admin for the correct volume name and manually add it to afsd's startup options. For consistency you should probably add a parameter in afs.conf.client and edit the startup script to look for it. The easiest (and more direct) way is probably simply to edit the startup script /etc/init.d/openafs-client to include the root volume specification. Look for the line:

start-stop-daemon --start --quiet --exec /sbin/afsd -- $AFSD_OPTIONS

Add "-rootvol <name of the root volume>" after $AFSD_OPTIONS, and you're in business.
4) (most commonly) a root volume has been setup but no acl has been set up for the afs root. This is easy to overlook, and will prevent anyone from accessing the root. 
      Fix: Again, bug the admin, and ask him/her to run the appropriate 'fs sa /afs...' command

Good luck

---

