---
title: "Many errors while installing gcc 3.4.6"
date: 2013-07-02
forum: New to Ubuntu
---

### Post by Eredanne on 2013-07-02
Hello all, I'm trying to install gcc 3.4.6 for days, I checked nearly every document I could find about it and still no luck.

I asked on askubuntu.com with no luck ([link]("http://askubuntu.com/questions/315125/i-cant-install-gcc-3-4-6-on-ubuntu-11-10"))

I tried these documents;

[LIST]
[*][http://www.lnf.infn.it/esperimenti/finuda/online/doc/GCC_CINT_OBSOLETE/GCC_CINT_Installation.html](http://www.lnf.infn.it/esperimenti/finuda/online/doc/GCC_CINT_OBSOLETE/GCC_CINT_Installation.html) 
[*][http://linux-buddy.blogspot.com/2011/02/install-gcc-34-on-ubuntu-1010.html](http://linux-buddy.blogspot.com/2011/02/install-gcc-34-on-ubuntu-1010.html) 
[*][http://ubuntuforums.org/archive/index.php/t-1530465.html](http://ubuntuforums.org/archive/index.php/t-1530465.html) 
[/LIST]


I'm always getting an error after I use ```
./configure&
``` then ```
make <anything> (eg. bootstrap, install)
```

This is the last error I got. I'm getting similar errors to these.

```

make[2]: *** [crtbegin.o] Error 1
make[2]: Leaving directory `/root/ObjectDir/gcc' 
make[1]: *** [stage1_build] Error 2 
make[1]: Leaving directory `/root/ObjectDir/gcc' 
make: *** [bootstrap] Error 2

```

I'm absolute beginner in linux, and I need help with this, can anyone help me installing gcc-3.4.6? I'm using 11.10 because my service only supports that one.

---

### Post by DeathByDenim on 2013-07-02
I still had a 11.10 install lying around, so I gave it a go as well. The amount of errors it generates is impressive. I'm not even sure how you would go about on fixing that.
Is there any particular reason you need such an old compiler though? Ubuntu 11.10 comes with gcc-4.6.1, right?

---

### Post by Eredanne on 2013-07-02
> **DeathByDenim said:**
> I still had a 11.10 install lying around, so I gave it a go as well. The amount of errors it generates is impressive. I'm not even sure how you would go about on fixing that.
Is there any particular reason you need such an old compiler though? Ubuntu 11.10 comes with gcc-4.6.1, right?

Yep, I have to compile this code and no other version can compile it without errors...

I only need it to compile this code. My hosting service doesn't support any other ubuntu versions but, it supports some other ones. Should I go for it?

---

### Post by Eredanne on 2013-07-02
> **Eredanne said:**
> Yep, I have to compile this code and no other version can compile it without errors...

I only need it to compile this code. My hosting service doesn't support any other ubuntu versions but, it supports some other ones. Should I go for it?

Also tried centos, no luck.  This time I didn't get an error.
```
I downloaded gcc-3.4.6.tar then I extracted it, and then
cd gcc-3.4.6
./configure&
```
output: many lines and codes and stuff
Creating makefile
```
make
```
Last lines;
```
creating rmiregistry
make[2]: Leaving directory '/home/gcc/gcc-3.4.6/i686-pc-linux-gnu/libjava'
make[1]: Leaving directory '/home/gcc/gcc-3.4.6/i686-pc-linux-gnu/libjava'
[1]+ Done                                  ./configure

```

Then I tried gcc -v, gcc-3.4 -v, gcc34 -v none of those worked except gcc -v and it said;
```
Using built-in specs.
Target: i386-redhat-linux
Configured with: ../configure --prefix=/usr --mandir=/usr/share/man --infodir=/usr/share/info --enable-shared --enable-threads=posix --enable-checking=release --with-system-zlib --enable-__cxa_atexit --disable-libunwind-exceptions --enable-libgcj-multifile --enable-languages=c,c++,objc,obj-c++,java,fortran,ada --enable-java-awt=gtk --disable-dssi --disable-plugin --with-java-home=/usr/lib/jvm/java-1.4.2-gcj-1.4.2.0/jre --with-cpu=generic --host=i386-redhat-linux
Thread model: posix
gcc version 4.1.2 20080704 (Red Hat 4.1.2-54)
```

But when I try g++ -v
```
Reading specs from /usr/local/lib/gcc/i686-pc-linux-gnu/3.4.6/specs
Configured with: ./configure
Thread model: posix
gcc version 3.4.6
```

---

### Post by DeathByDenim on 2013-07-02
That's rather strange. Is there a different path when you type these commands:
```
which gcc
which g++
```

By the way, you don't need to put the & after the configure command, doing so will make it run in the background and there's not really any reason to do that.

---

### Post by mc4man on 2013-07-02
You can likely use the hardy gcc-3.4 packages to install 3.4.6 
You'll need the 11.10 version of libstdc++6 **installed before installing the 3.4.6 packages**, it should be but check first
(sudo apt-get install libstdc++6 should return "libstdc++6 is already the newest version." or install it.  If not then you'll need to get it from the old-release repo before doing below

**Assuming libstdc++6 is installed** 
then go here for a 32 bit 11.10 install - 
[https://launchpad.net/ubuntu/+source/gcc-3.4/3.4.6-6ubuntu5/+build/601913](https://launchpad.net/ubuntu/+source/gcc-3.4/3.4.6-6ubuntu5/+build/601913)

Or if on a 64 bit install go here - 
[https://launchpad.net/ubuntu/+source/gcc-3.4/3.4.6-6ubuntu5/+build/601911](https://launchpad.net/ubuntu/+source/gcc-3.4/3.4.6-6ubuntu5/+build/601911)

(make sure you know if you're on a  32 or 64 bit install before procedding

Then scroll down to "Built Files", download these to an empty folder you create to hold them for install 
32 bit - 
> cpp-3.4_3.4.6-6ubuntu5_i386.deb  
g++-3.4_3.4.6-6ubuntu5_i386.deb 
gcc-3.4_3.4.6-6ubuntu5_i386.deb  
gcc-3.4-base_3.4.6-6ubuntu5_i386.deb     
libstdc++6-dev_3.4.6-6ubuntu5_i386.deb

64bit - 
> cpp-3.4_3.4.6-6ubuntu5_amd64.deb 
g++-3.4_3.4.6-6ubuntu5_amd64.deb  
gcc-3.4_3.4.6-6ubuntu5_amd64.deb       
gcc-3.4-base_3.4.6-6ubuntu5_amd64.deb
libstdc++6-dev_3.4.6-6ubuntu5_amd64.deb

Once all 5 are in the folder cd to the folder in a terminal & run 
```
sudo dpkg -i *.deb
```

Ex. here on 13.04 (amd64 install 
> :~/Desktop/gcc-3.4$ sudo dpkg -i *.deb
[sudo] password for doug: 
Selecting previously unselected package cpp-3.4.
(Reading database ... 284430 files and directories currently installed.)
Unpacking cpp-3.4 (from cpp-3.4_3.4.6-6ubuntu5_amd64.deb) ...
Selecting previously unselected package g++-3.4.
Unpacking g++-3.4 (from g++-3.4_3.4.6-6ubuntu5_amd64.deb) ...
Selecting previously unselected package gcc-3.4.
Unpacking gcc-3.4 (from gcc-3.4_3.4.6-6ubuntu5_amd64.deb) ...
Selecting previously unselected package gcc-3.4-base.
Unpacking gcc-3.4-base (from gcc-3.4-base_3.4.6-6ubuntu5_amd64.deb) ...
Selecting previously unselected package libstdc++6-dev.
Unpacking libstdc++6-dev (from libstdc++6-dev_3.4.6-6ubuntu5_amd64.deb) ...
Setting up gcc-3.4-base (3.4.6-6ubuntu5) ...
Setting up cpp-3.4 (3.4.6-6ubuntu5) ...
Processing triggers for man-db ...
Setting up gcc-3.4 (3.4.6-6ubuntu5) ...
Setting up g++-3.4 (3.4.6-6ubuntu5) ...
Setting up libstdc++6-dev (3.4.6-6ubuntu5) ...
doug@doug-XPS-M1330:~/Desktop/gcc-3.4$

> $ /usr/bin/gcc-3.4 -v
Reading specs from /usr/lib/gcc/x86_64-linux-gnu/3.4.6/specs
Configured with: ../src/configure -v --enable-languages=c,c++,f77,pascal --prefix=/usr --libexecdir=/usr/lib --with-gxx-include-dir=/usr/include/c++/3.4 --enable-shared --with-system-zlib --enable-nls --without-included-gettext --program-suffix=-3.4 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug x86_64-linux-gnu
Thread model: posix
gcc version 3.4.6 (Ubuntu 3.4.6-6ubuntu5)


---

### Post by Eredanne on 2013-07-02
> **mc4man said:**
> You can likely use the hardy gcc-3.4 packages to install 3.4.6 
You'll need the 11.10 version of libstdc++6 **installed before installing the 3.4.6 packages**, it should be but check first
(sudo apt-get install libstdc++6 should return "libstdc++6 is already the newest version." or install it.  If not then you'll need to get it from the old-release repo before doing below

**Assuming libstdc++6 is installed** 
then go here for a 32 bit 11.10 install - 
[https://launchpad.net/ubuntu/+source/gcc-3.4/3.4.6-6ubuntu5/+build/601913](https://launchpad.net/ubuntu/+source/gcc-3.4/3.4.6-6ubuntu5/+build/601913)

Or if on a 64 bit install go here - 
[https://launchpad.net/ubuntu/+source/gcc-3.4/3.4.6-6ubuntu5/+build/601911](https://launchpad.net/ubuntu/+source/gcc-3.4/3.4.6-6ubuntu5/+build/601911)

(make sure you know if you're on a  32 or 64 bit install before procedding

Then scroll down to "Built Files", download these to an empty folder you create to hold them for install 
32 bit - 


64bit - 


Once all 5 are in the folder cd to the folder in a terminal & run 
```
sudo dpkg -i *.deb
```

Ex. here on 13.04 (amd64 install


This actually did work! THANKS!

---

### Post by Eredanne on 2013-07-02
Turns out it didn't work...

```

root@sturm-VirtualBox:/home/sturm/gcc346# sudo dpkg -i *.deb
Selecting previously deselected package cpp-3.4:i386.
(Reading database ... 124726 files and directories currently installed.)
Unpacking cpp-3.4:i386 (from cpp-3.4_3.4.6-6ubuntu5_i386.deb) ...
Selecting previously deselected package g++-3.4:i386.
Unpacking g++-3.4:i386 (from g++-3.4_3.4.6-6ubuntu5_i386.deb) ...
Selecting previously deselected package gcc-3.4:i386.
Unpacking gcc-3.4:i386 (from gcc-3.4_3.4.6-6ubuntu5_i386.deb) ...
Selecting previously deselected package gcc-3.4-base:i386.
Unpacking gcc-3.4-base:i386 (from gcc-3.4-base_3.4.6-6ubuntu5_i386.deb) ...
Selecting previously deselected package libstdc++6-dev:i386.
Unpacking libstdc++6-dev:i386 (from libstdc++6-dev_3.4.6-6ubuntu5_i386.deb) ...
dpkg: dependency problems prevent configuration of cpp-3.4:i386:
 cpp-3.4:i386 depends on libc6 (>= 2.3).
dpkg: error processing cpp-3.4:i386 (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of g++-3.4:i386:
 g++-3.4:i386 depends on libc6 (>= 2.3).
 g++-3.4:i386 depends on libstdc++6 (>= 4.0.2-4).
dpkg: error processing g++-3.4:i386 (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gcc-3.4:i386:
 gcc-3.4:i386 depends on binutils (>= 2.16.1-3).
 gcc-3.4:i386 depends on cpp-3.4 (= 3.4.6-6ubuntu5); however:
  Package cpp-3.4:i386 is not configured yet.
 gcc-3.4:i386 depends on libc6 (>= 2.3); however:
 gcc-3.4:i386 depends on libgcc1 (>= 1:3.4.6-6ubuntu5); however:
dpkg: error processing gcc-3.4:i386 (--install):
 dependency problems - leaving unconfigured
Setting up gcc-3.4-base:i386 (3.4.6-6ubuntu5) ...
dpkg: dependency problems prevent configuration of libstdc++6-dev:i386:
 libstdc++6-dev:i386 depends on g++-3.4 (= 3.4.6-6ubuntu5); however:
  Package g++-3.4:i386 is not configured yet.
 libstdc++6-dev:i386 depends on libc6-dev (>= 2.3.5-10); however:
 libstdc++6-dev:i386 depends on libstdc++6 (>= 3.4.6-6ubuntu5); however:
dpkg: error processing libstdc++6-dev:i386 (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 cpp-3.4:i386
 g++-3.4:i386
 gcc-3.4:i386
 libstdc++6-dev:i386
root@sturm-VirtualBox:/home/sturm/gcc346# gcc -v
Using built-in specs.
COLLECT_GCC=gcc
COLLECT_LTO_WRAPPER=/usr/lib/gcc/x86_64-linux-gnu/4.6.1/lto-wrapper
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.6.1-9ubuntu3' --with-bugurl=file:///usr/share/doc/gcc-4.6/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++,go --prefix=/usr --program-suffix=-4.6 --enable-shared --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.6 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-plugin --enable-objc-gc --disable-werror --with-arch-32=i686 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) 


```

---

### Post by DeathByDenim on 2013-07-02
It says
```
 g++-3.4:i386 depends on libstdc++6 (>= 4.0.2-4).
```
Did you try
```
sudo apt-get install libstdc++6
```
as mc4man suggested?

I take it, you are on a 32-bit system then?

---

### Post by Eredanne on 2013-07-02
> **DeathByDenim said:**
> It says
```
 g++-3.4:i386 depends on libstdc++6 (>= 4.0.2-4).
```
Did you try
```
sudo apt-get install libstdc++6
```
as mc4man suggested?

I take it, you are on a 32-bit system then?

Yes, I tried and it said its already updated to the newest version.

I tried both i386 and amd64.
I tried i386 first, then I formatted and tried amd64. Still no luck.

---

### Post by mc4man on 2013-07-02
Not sure what your issue is but - 
seems you're running  a virtual 11.10 with no 11.10 repo support. 
(11.10 is EOL, you need to switch your sources to the 'old-release' repo

The way it's showing the attempted install is a bit odd "Unpacking cpp-3.4[COLOR="#FF0000"]:i386 [/COLOR]" , ect. , don't usually see that though i've not used 11.10 for some time

cpp is failing on libc6, seems odd there, & there are more fails other than libstdc++6,  -  libgcc1, maybe others

So the main question is,  Do you have the old-release repos enabled for oneiric?  

The earliest I have is 12.04 32 bit - as you can see no issue with the 3.4 gcc packages (
> doug@doug-XPS-M1330:/media/0a803857-8b6f-4332-82b4-85ebf8283805/home/doug/Desktop/gcc-3.4-32bit$ sudo dpkg -i *.deb
[sudo] password for doug: 
Selecting previously unselected package cpp-3.4.
(Reading database ... 291996 files and directories currently installed.)
Unpacking cpp-3.4 (from cpp-3.4_3.4.6-6ubuntu5_i386.deb) ...
Selecting previously unselected package g++-3.4.
Unpacking g++-3.4 (from g++-3.4_3.4.6-6ubuntu5_i386.deb) ...
Selecting previously unselected package gcc-3.4.
Unpacking gcc-3.4 (from gcc-3.4_3.4.6-6ubuntu5_i386.deb) ...
Selecting previously unselected package gcc-3.4-base.
Unpacking gcc-3.4-base (from gcc-3.4-base_3.4.6-6ubuntu5_i386.deb) ...
Selecting previously unselected package libstdc++6-dev.
Unpacking libstdc++6-dev (from libstdc++6-dev_3.4.6-6ubuntu5_i386.deb) ...
Setting up gcc-3.4-base (3.4.6-6ubuntu5) ...
Setting up cpp-3.4 (3.4.6-6ubuntu5) ...
Processing triggers for man-db ...
Setting up gcc-3.4 (3.4.6-6ubuntu5) ...
Setting up g++-3.4 (3.4.6-6ubuntu5) ...
Setting up libstdc++6-dev (3.4.6-6ubuntu5) ...
doug@doug-XPS-M1330:/media/0a803857-8b6f-4332-82b4-85ebf8283805/home/doug/Desktop/gcc-3.4-32bit$ 

---

### Post by naga2raja on 2013-07-03
You can just try the following.

$ sudo apt-cache search gcc

In the output list, if you find gcc-3.4.6 then you can straight away install using 
$ sudo apt-get install gcc-3.4.6

I think that your trying to install multiple versions of gcc. You need to set different prefix while installing a new version.
[http://gcc.gnu.org/faq.html#multiple](http://gcc.gnu.org/faq.html#multiple)

---

### Post by Eredanne on 2013-07-03
> **mc4man said:**
> Not sure what your issue is but - 
seems you're running  a virtual 11.10 with no 11.10 repo support. 
(11.10 is EOL, you need to switch your sources to the 'old-release' repo

The way it's showing the attempted install is a bit odd "Unpacking cpp-3.4[COLOR=#FF0000]:i386 [/COLOR]" , ect. , don't usually see that though i've not used 11.10 for some time

cpp is failing on libc6, seems odd there, & there are more fails other than libstdc++6,  -  libgcc1, maybe others

So the main question is,  Do you have the old-release repos enabled for oneiric?  

The earliest I have is 12.04 32 bit - as you can see no issue with the 3.4 gcc packages (

[http://old-releases.ubuntu.com/ubuntu/dists/hardy/](http://old-releases.ubuntu.com/ubuntu/dists/hardy/)

I should add this to the sources.list, right?

---

### Post by steeldriver on 2013-07-03
> **Eredanne said:**
> Yep, I have to compile **this code** and no other version can compile it without errors...

I only need it to compile this code. My hosting service doesn't support any other ubuntu versions but, it supports some other ones. Should I go for it?

What exactly is "this code" and what kind of errors? Have you considered putting your effort into fixing the code so that it builds in your current environment - you may find it's a lot easier than getting a working gcc-3.4.6 based toolchain installed

Just a thought

---

### Post by Eredanne on 2013-07-03
> **steeldriver said:**
> What exactly is "this code" and what kind of errors? Have you considered putting your effort into fixing the code so that it builds in your current environment - you may find it's a lot easier than getting a working gcc-3.4.6 based toolchain installed

Just a thought

It's a Anatolia MUD codebase. I tried many versions of GCC in the past and gcc-3.4.6 is the most stable for this one every other one doesn't compile at all or give errors. It would take me days to fix it I assume.

---

### Post by mc4man on 2013-07-03
> **Eredanne said:**
> [http://old-releases.ubuntu.com/ubuntu/dists/hardy/](http://old-releases.ubuntu.com/ubuntu/dists/hardy/)

I should add this to the sources.list, right?

No, you need to add the repo for the EOL release you are using which is 11.10, oneiric. 
The only packages you need or want from hardy you already have (the 5 prev. mentioned

How you properly add it i've never had reason to know, ask

---

### Post by deadflowr on 2013-07-03
> **mc4man said:**
> No, you need to add the repo for the EOL release you are using which is 11.10, oneiric. 
The only packages you need or want from hardy you already have (the 5 prev. mentioned

How you properly add it i've never had reason to know, ask

This works, somewhat
```
sudo sed -i -e 's/archive.ubuntu.com\|security.ubuntu.com/old-releases.ubuntu.com/g' /etc/apt/sources.list
```

Make sure that each line says old-release, and not us.old-release, or gb.old-release, or whatever the mirror is.
Then run apt-get update and inevitably comment out the lines which come up with errors.

---

### Post by mc4man on 2013-07-03
Not sure what you're doing wrong, works fine on 11.10
(the command above from deadflower is good though for this you should have all needed already installed. I'd still do that so you can get any build related packages that aren;t default installed

Ex. - on a live cd of 11.10 amd64
> ubuntu@ubuntu:/media/0a803857-8b6f-4332-82b4-85ebf8283805/home/doug/Desktop/gcc-3.4$ sudo dpkg -i *.deb
Selecting previously deselected package cpp-3.4.
(Reading database ... 130325 files and directories currently installed.)
Unpacking cpp-3.4 (from cpp-3.4_3.4.6-6ubuntu5_amd64.deb) ...
Selecting previously deselected package g++-3.4.
Unpacking g++-3.4 (from g++-3.4_3.4.6-6ubuntu5_amd64.deb) ...
Selecting previously deselected package gcc-3.4.
Unpacking gcc-3.4 (from gcc-3.4_3.4.6-6ubuntu5_amd64.deb) ...
Selecting previously deselected package gcc-3.4-base.
Unpacking gcc-3.4-base (from gcc-3.4-base_3.4.6-6ubuntu5_amd64.deb) ...
Selecting previously deselected package libstdc++6-dev.
Unpacking libstdc++6-dev (from libstdc++6-dev_3.4.6-6ubuntu5_amd64.deb) ...
Setting up gcc-3.4-base (3.4.6-6ubuntu5) ...
Setting up cpp-3.4 (3.4.6-6ubuntu5) ...
Processing triggers for man-db ...
Setting up gcc-3.4 (3.4.6-6ubuntu5) ...
Setting up g++-3.4 (3.4.6-6ubuntu5) ...
Setting up libstdc++6-dev (3.4.6-6ubuntu5) ...
> 
ubuntu@ubuntu:/media/0a803857-8b6f-4332-82b4-85ebf8283805/home/doug/Desktop/gcc-3.4$ /usr/bin/gcc-3.4 -v
Reading specs from /usr/lib/gcc/x86_64-linux-gnu/3.4.6/specs
Configured with: ../src/configure -v --enable-languages=c,c++,f77,pascal --prefix=/usr --libexecdir=/usr/lib --with-gxx-include-dir=/usr/include/c++/3.4 --enable-shared --with-system-zlib --enable-nls --without-included-gettext --program-suffix=-3.4 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug x86_64-linux-gnu
Thread model: posix
gcc version 3.4.6 (Ubuntu 3.4.6-6ubuntu5)

Note: after running deadflowers command  & updating sources

>  sudo apt-get update
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) oneiric InRelease
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) oneiric-security InRelease
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) oneiric-updates InRelease
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) oneiric Release.gpg
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) oneiric-security Release.gpg
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) oneiric-updates Release.gpg
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) oneiric Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) oneiric-security Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) oneiric-updates Release
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) oneiric/main amd64 Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) oneiric/restricted amd64 Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) oneiric/main i386 Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) oneiric/restricted i386 Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) oneiric/main TranslationIndex
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) oneiric/restricted TranslationIndex
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) oneiric-security/main amd64 Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) oneiric-security/restricted amd64 Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) oneiric-security/main i386 Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) oneiric-security/restricted i386 Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) oneiric-security/main TranslationIndex
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) oneiric-security/restricted TranslationIndex
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) oneiric/main Translation-en
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) oneiric-updates/main amd64 Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) oneiric-updates/restricted amd64 Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) oneiric-updates/main i386 Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) oneiric-updates/restricted i386 Packages
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) oneiric-updates/main TranslationIndex
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) oneiric-updates/restricted TranslationIndex
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) oneiric/restricted Translation-en
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) oneiric-security/main Translation-en
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) oneiric-security/restricted Translation-en
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) oneiric-updates/main Translation-en
Hit [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) oneiric-updates/restricted Translation-en
Reading package lists... Done

Add. 
> ubuntu@ubuntu:~$ apt-cache policy gcc
gcc:
  Installed: 4:4.6.1-2ubuntu5
  Candidate: 4:4.6.1-2ubuntu5
  Version table:
 *** 4:4.6.1-2ubuntu5 0
        500 [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) oneiric/main amd64 Packages
        100 /var/lib/dpkg/status
ubuntu@ubuntu:~$ apt-cache policy gcc-3.4
gcc-3.4:
  Installed: 3.4.6-6ubuntu5
  Candidate: 3.4.6-6ubuntu5
  Version table:
 *** 3.4.6-6ubuntu5 0
        100 /var/lib/dpkg/status
ubuntu@ubuntu:~$ 

---

