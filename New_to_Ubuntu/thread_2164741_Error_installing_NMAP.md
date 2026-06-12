---
title: "Error installing NMAP"
date: 2013-08-01
forum: New to Ubuntu
---

### Post by 8H3LnBH on 2013-08-01
Let me start off by saying I am as new is gets to Linux.  I have 12.04 running in a Hyper-V VM and everything seems to be working fine.  I am trying to install NMAP using the steps below but when I get to the "make" command...it terminates in the errors below.  Being new to Linux...I have no idea what is wrong:

Commands executed to install NMAP:
[INDENT]mkdir ~/Development
cd ~/Development
svn co [https://svn.nmap.org/nmap](https://svn.nmap.org/nmap)
cd nmap
./configure
make
sudo make install
make clean[/INDENT]

Errors generated:

[INDENT]gcc -o test/addrset -g -O2 -Wall -Wall  test/addrset.o ncat_core.o sys_wrap.o util.o ncat_posix.o ncat_lua.o -ldl -lssl -lcrypto -ldl  ../nsock/src/libnsock.a ../nbase/libnbase.a -lssl -lcrypto -lpcap ./../liblua/liblua.a -lm

/usr/bin/ld: ./../liblua/liblua.a(loadlib.o): undefined reference to symbol [EMAIL="'dlclose@@GLIBC_2.2.5'"]'dlclose@@GLIBC_2.2.5'[/EMAIL]

/usr/bin/ld: note: [EMAIL="'dlcose@@GLIBC_2.2.5'"]'dlcose@@GLIBC_2.2.5'[/EMAIL] is defined in DSO /usr/lib/gcc/x86_64-linux-gnu/4.6/../../../x86_64-linux-gnu/libdl.so so try adding it to the linker command line

/usr/lib/gcc/x86_64-linux-gnu/4.6/../../../x86_64-linux-gnu/libdl.so: could not read symbols: Invalid operation

collect2: Id returned 1 exit status

make[1]: *** [test/addrset] Error 1

make[1]: Leaving directory '/home/Phydeauxman/Development/nmap/ncat'

make[1]: *** [ncat_build] Error 2

[/INDENT]

---

### Post by steeldriver on 2013-08-01
Hello and welcome to the forum

Before we try to address the linker error specifically, is there any particular reason you are trying to install nmap from source? you can install the binary package from the standard repository, via a package manager tool or using apt-get

```
sudo apt-get install nmap
```

---

### Post by oldos2er on 2013-08-01
Moved to Absolute Beginners.

---

### Post by 8H3LnBH on 2013-08-02
> **steeldriver said:**
> Hello and welcome to the forum

Before we try to address the linker error specifically, is there any particular reason you are trying to install nmap from source? you can install the binary package from the standard repository, via a package manager tool or using apt-get

```
sudo apt-get install nmap
```

The reason is...is because I found that process online and was trying it.  I am about as new as possible to Linux, have never used Unix, have lived entire life in Windows and am engrained with the commands used in the PowerShell/Windows command shell.  I have to learn from scratch with Linux.  The command you provided me worked great...thanks for the quick reply and the help.

---

### Post by Lars Noodén on 2013-08-02
There is a graphical way of installing programs, too, using The Software Center or Synaptic.  Myself, I prefer apt-get.

About nmap, there is also a graphical front end for it called [zenmap](http://nmap.org/zenmap/).  It can be installed the same way as nmap was.

---

### Post by steeldriver on 2013-08-02
Well just in case someone stumbles across this thread and really does need to build from source, the problem seems to be limited to the sub-build of the ncat binary - so if you don't need that then just configure the build without it

```

./configure --without-ncat

```

For anyone who needs ncat, the actual issue seems to be library link order - although libdl.so gets linked twice, neither instance is in the right place to resolve the dependencies of liblua.a

```

gcc -o test/test-uri -g -O2 -Wall -Wall -L../libpcap  test/test-uri.o base64.o http.o ncat_core.o sys_wrap.o util.o ncat_posix.o ncat_lua.o \
 [COLOR=#ff0000]-ldl[/COLOR] -lssl -lcrypto [COLOR=#ff0000]-ldl[/COLOR]  ../nsock/src/libnsock.a ../nbase/libnbase.a -lssl -lcrypto -lpcap [COLOR=#ff0000]./../liblua/liblua.a[/COLOR] -lm
/usr/bin/ld: ./../liblua/liblua.a(loadlib.o): undefined reference to symbol 'dlopen@@GLIBC_2.1'

```

As a quick and dirty fix, adding an extra -ldl to the RHS of liblua.a allows it to resolve (you'd need to do that for each target in ncat - or fix the makefile to correct the library order)
```

$ gcc -o test/test-uri -g -O2 -Wall -Wall -L../libpcap  test/test-uri.o base64.o http.o ncat_core.o sys_wrap.o util.o ncat_posix.o ncat_lua.o \
-ldl -lssl -lcrypto -ldl  ../nsock/src/libnsock.a ../nbase/libnbase.a -lssl -lcrypto -lpcap ./../liblua/liblua.a [COLOR=#ff0000]-ldl[/COLOR] -lm

```

---

### Post by 8H3LnBH on 2013-08-02
> **Lars Noodén said:**
> There is a graphical way of installing programs, too, using The Software Center or Synaptic.  Myself, I prefer apt-get.

About nmap, there is also a graphical front end for it called [zenmap]("http://nmap.org/zenmap/").  It can be installed the same way as nmap was.

Thanks for taking time to provide the tip

---

### Post by moonoiuk on 2013-09-02
HI there, in need that ncat binary, and note that nmap doesnt work with scripts with the package install (apt-get) so need to compile from source. Please can you help clarify where in the make file i need to add the liblua.a -ldl, after doing a scan of the Makefile, and adding to the places i see fit it still will not make after a configure. Many thanks. I am using precise server, Ubuntu 12.04.3 LTS.

---

### Post by steeldriver on 2013-09-02
You can either edit the LUA_LIBS definition in the ncat/Makefile, or  just pass the modified def to 'make' from the command line

```

steeldriver@lap-t61p:~/src/nmap$ cd ncat
steeldriver@lap-t61p:~/src/nmap/ncat$ make "LUA_LIBS=../liblua/liblua.a -ldl -lm"

```

---

### Post by moonoiuk on 2013-09-03
Thank you so much! that worked out for me very well, but just for my own sanity please can you help me understand what the -ldl is; because running strace showed the command without the -ldl. And can you give me any thoughts on how i can keep this packet updated? Thanks.

for those they may want to know what my final path to success was in creating my own DEB install file from the download of source to install on 12.04 please see below...

[http://nmap.org/dist/?C=M&O=D](http://nmap.org/dist/?C=M&O=D)
[http://nmap.org/dist/nmap-6.40.tar.bz2](http://nmap.org/dist/nmap-6.40.tar.bz2)

code:
```

wget [http://nmap.org/dist/nmap-6.40.tar.bz2](http://nmap.org/dist/nmap-6.40.tar.bz2)
tar -jxvf nmap-6.40.tar.bz2
cd nmap-6.40
./configure
make "LUA_LIBS=../liblua/liblua.a -ldl -lm"
sudo checkinstall
sudo dpkg -i nmap_6.40-1_amd64.deb

```

---

