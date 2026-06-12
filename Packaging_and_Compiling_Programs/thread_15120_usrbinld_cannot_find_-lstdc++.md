---
title: "/usr/bin/ld: cannot find -lstdc++"
date: 2005-02-12
forum: Packaging and Compiling Programs
---

### Post by ralph_ubuntu on 2005-02-12
Arghh,
I'm trying to compile simias to get ifolder to work.
The problem is, that I always end up with the following error message:

/usr/bin/ld CSPObjectIterator.o CSPropertyIterator.o CSPStore.o CSPStoreObject.o FlaimWrapper.o -oFlaimWrapper.so -L "../../../external/flaim/lxx86/gcc3/release" -lflm -lstdc++ -lpthread -shared
/usr/bin/ld: cannot find -lstdc++
make[3]: *** [FlaimWrapper.so] Fehler 1
make[3]: Verlasse Verzeichnis »/home/ralph/build/simias-1.0.20050209/src/FlaimProvider/FlaimWrapper«
make[2]: *** [all-recursive] Fehler 1
make[2]: Verlasse Verzeichnis »/home/ralph/build/simias-1.0.20050209/src/FlaimProvider«
make[1]: *** [all-recursive] Fehler 1
make[1]: Verlasse Verzeichnis »/home/ralph/build/simias-1.0.20050209/src«
make: *** [all-recursive] Fehler 1

The problem is that libstdc++ is installed and I can't figure out why ld isn't able to find it.

Any ideas?

---

### Post by mendicant on 2005-02-12
I find that I no longer need to add stdc++ in the latest versions of gcc.

---

### Post by ralph_ubuntu on 2005-02-13
[QUOTE=mendicant]I find that I no longer need to add stdc++ in the latest versions of gcc.[/QUOTE]
 My problem is that simias insists on adding this. However, I played around with the Makefile and got it to compile, only to find out that I also couldn't get ifolder to compile.

I think I'll simply wait till someone packages it for debian. ;-D

---

### Post by tturk on 2005-02-19
I've softlinked my libstdc.so file to the one ld is looking for and that did the trick:
*sudo ln -s /usr/lib/libstdc++.so.5.0.7 /usr/lib/libstdc++.so*
In my case I am using gcc 3.3.5, your file may vary (this is, I guess the official ubuntu compiler).
ifolder and simias compile fine from cvs, but I am still unable to get the SimpleServer work, anyone has managed to make it work?

---

### Post by ralph_ubuntu on 2005-02-19
Great. I'll give it a try and see if I can get ifolder to work now. :-D

---

### Post by mattisking on 2005-06-19
Well, I was able to get everything to compile using that trick and ran iFolder successfully... but of course I don't have a server to connect to and I can't seem to work out SimpleServer.

---

### Post by progressdll on 2005-08-02
use this howto

[http://forge.novell.com/modules/xfmod/cvs/cvsbrowse.php/*checkout*/ifolder/ifolder/HOWTOs/SimpleServer-Setup-HOWTO.txt](http://forge.novell.com/modules/xfmod/cvs/cvsbrowse.php/*checkout*/ifolder/ifolder/HOWTOs/SimpleServer-Setup-HOWTO.txt)

---

### Post by shankerj on 2005-09-17
On running the step: ./autogen.sh --prefix=/opt/simias, I get the error:

Running libtoolize...
./autogen.sh: line 109: libtoolize: command not found

..snip..

checking for ANSI C header files... (cached) yes
./configure: line 4960: AM_PROG_LIBTOOL: command not found
NDOC_CMD=
checking for pkg-config... (cached) /usr/bin/pkg-config
checking for xml2-config... (cached) /usr/bin/xml2-config
configure: creating ./config.status
config.status: error: cannot find input file: Makefile.in
====================

I have autoconf, automake, libxml2. Anything else I am missing?
--Shanker

---

### Post by shankerj on 2005-09-20
I got this to work after installing one-by-one the missing packages. So far, so good. Anyone has a startup script for ubuntu? The one provided in ubuntu.com needs an input argument that I'm not sure how to pass.

---

### Post by dandaman32 on 2006-04-11
I have Knoppix 4.0.2 and I'm not sure if Ubuntu has more than one version of GCC but I couldn't compile libmusicbrainz until I moved back to gcc 3.3:
```
su -c "rm -f /usr/bin/gcc; ln -s /usr/bin/gcc3.3 /usr/bin/gcc"
``` 
-dandaman32

---

### Post by despindola on 2010-02-17
The library libstdc++ are well but I solved this problem so:

sudo apt-get install libstdc++6-4.4-dev (In my case i.e. install the dev packages)

;)

---

### Post by ntlam on 2010-06-05
> **despindola said:**
> The library libstdc++ are well but I solved this problem so:

sudo apt-get install libstdc++6-4.4-dev (In my case i.e. install the dev packages)

;)

The same with me, libstdc++6-4.3-dev does not solve the problem but libstdc++6-4.4-dev does.

---

### Post by agenthex on 2010-10-29
I'm using Hardy 8.04 LTS, and there is no libstdc++6-4.4-dev package.  Does anyone else find it strange that this thread started, died for 5 years, and then got revived?

---

### Post by spezifanta on 2012-01-17
Cant say installing libstdc++6-4.4-dev helped :/

However this helped:
```
sudo ln -s /usr/lib32/libstdc++.so.6 /usr/lib32/libstdc++.so
```

Was trying to compile 32bit software with an 64bit environment.

---

### Post by goldencako on 2012-12-06
> **spezifanta said:**
> Cant say installing libstdc++6-4.4-dev helped :/

However this helped:
```
sudo ln -s /usr/lib32/libstdc++.so.6 /usr/lib32/libstdc++.so
```

Was trying to compile 32bit software with an 64bit environment.

Don't forget that if you are using gcc 4.6, you need libstdc++6-4.6-dev

---

