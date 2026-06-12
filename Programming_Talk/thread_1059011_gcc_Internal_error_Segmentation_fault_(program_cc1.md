---
title: "gcc: Internal error: Segmentation fault (program cc1)"
date: 2009-02-03
forum: Programming Talk
---

### Post by navneeth on 2009-02-03
That is the error message I get when I try to compile a C program using gcc. I have never had this happen to me before. 

I was actually learning how to create library files, so initially I used the -c option. But then, just to double-check, I wrote the Hello World program. I had the error message thrown back at me when I compiled it.

```
#include<stdio.h>

void main()
{
    printf("Hello, World!");
}

```

```
$ gcc hello.c
gcc: Internal error: Segmentation fault (program cc1)
Please submit a full bug report.
See <file:///usr/share/doc/gcc-4.3/README.Bugs> for instructions.

```

```
$ gcc --version
gcc (Ubuntu 4.3.2-1ubuntu12) 4.3.2
Copyright (C) 2008 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

I use Ubuntu 8.10.

I'd appreciate any help in solving this issue.

---

### Post by monkeyking on 2009-02-03
thats awkward, it works for me but I'm told that main should be of type int as returnvalue.

[PHP]
cat hello.c
#include<stdio.h>

void main()
{
    printf("Hello, World!");
}
[/PHP]


[PHP]
gcc -Wall -pedantic hello.c -ansi
hello.c:4: warning: return type of ‘main’ is not ‘int’
[/PHP]


have you installed build-essential?

---

### Post by johnl on 2009-02-03
You should never get the message you've described based on code input.  If there is a problem with your code, you should get an error or warning describing the issue.

It's more likely something is not installed or installed incorrectly.  I second the suggestion above -- check that the build-essential package is installed.

---

### Post by navneeth on 2009-02-04
Thanks for the replies. Build-essential is the newest version. And, as I said,(I have been using Ubunut since Dapper(!) and) I have never had this happen to me before. 



P.S.: I know the prescribed return value of main() is integer, but I was lazy to type the extra statement at the end. ;)

---

### Post by iharrold on 2009-02-04
what does "ldd gcc" show?

what does "catchsegv gcc" show?

---

### Post by navneeth on 2009-02-04
> **iharrold said:**
> what does "ldd gcc" show?
Executing that command from my home directory...

```
$ ldd gcc
ldd: ./gcc: No such file or directory

```

> what does "catchsegv gcc" show?

From the same location,

```
$ catchsegv gcc
gcc: no input files

```

---

### Post by monkeyking on 2009-02-04
Hmm your error is strange is strange.
First I would figure out what gcc actually symlinks to.

[PHP]
ls -lah gcc*
lrwxrwxrwx 1 root root    7 2008-06-12 16:01 gcc -> gcc-4.2
-rwxr-xr-x 1 root root  87K 2008-05-08 13:32 gcc-3.3
-rwxr-xr-x 1 root root  92K 2008-05-08 09:35 gcc-3.4
-rwxr-xr-x 1 root root 218K 2008-10-11 06:24 gcc-4.2
-rwxr-xr-x 1 root root  16K 2008-05-08 13:31 gccbug-3.3
-rwxr-xr-x 1 root root  16K 2008-05-08 09:34 gccbug-3.4
-rwxr-xr-x 1 root root 2,0K 2007-06-05 03:06 gccmakedep
[/PHP]
Then I would try to compile with one of the others.
If you want to run ldd you should do it like this.

[PHP]
ldd /usr/bin/gcc
        linux-vdso.so.1 =>  (0x00007fffd99fe000)
        libc.so.6 => /lib/libc.so.6 (0x00007f85d138b000)
        /lib64/ld-linux-x86-64.so.2 (0x00007f85d16ed000)

[/PHP]

---

### Post by navneeth on 2009-02-04
> **monkeyking said:**
> Hmm your error is strange is strange.

It isn't strange at all, in the sense that it has been reported many times in the past for previous versions. Apparently, it was taken care of in 4.2. (A Google search for the subject line of this thread should give you more info.)

> First I would figure out what gcc actually symlinks to.

```
/usr/bin$ ls -ahl gcc*
lrwxrwxrwx 1 root root    7 2008-11-01 16:03 gcc -> gcc-4.3
-rwxr-xr-x 1 root root 195K 2008-10-26 18:42 gcc-4.1
-rwxr-xr-x 1 root root 189K 2008-10-26 21:54 gcc-4.2
-rwxr-xr-x 1 root root 204K 2009-01-24 01:50 gcc-4.3
-rwxr-xr-x 1 root root  16K 2008-10-26 18:39 gccbug-4.1
-rwxr-xr-x 1 root root 2.0K 2008-08-05 06:14 gccmakedep

```

> Then I would try to compile with one of the others.
Could you please tell me how to do that?


> If you want to run ldd you should do it like this.

Thanks. Running it from the /usr/bin directory,

```
/usr/bin$ ldd gcc
	linux-gate.so.1 =>  (0xb8006000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7e78000)
	/lib/ld-linux.so.2 (0xb7fec000)

```

catchsegv still shows gcc: no input file. (Just to check, I supplied a C program's name as the argument, but that just showed me in the error from the first post.)


This is bugging me.(No pun intended.) I borrowed this nice, fat Linux programming book from the library, and I find my compiler won't do its thing. :(

---

### Post by snova on 2009-02-04
I don't see what running **ldd** on the gcc binary will do, since gcc is little more than a frontend. Try this instead:

```
ldd /usr/lib/gcc/i486-linux-gnu/4.3/cc1
```

Lets try getting a little more information from gcc's failure (from the directory your source code is in):

```
gcc -v hello.c
```

Then lets see if prior versions of gcc will work correctly. Try these (from the same place):

```
gcc-4.1 -v hello.c
```
```
gcc-4.2 -v hello.c
```

Just in case, post all output, not just failures.

---

### Post by monkeyking on 2009-02-04
you should simply try

[PHP]
gcc-4.1
[/PHP]
instead of gcc.
Or some of the other.

If I were you, I would try to remove the build-essential,
reboot.
and install it again.

Is your setup a dapper that you have upgraded all the way through the different versions?

If int doesn't help try posting your env
[PHP]env[/PHP]

---

### Post by navneeth on 2009-02-04
All of the following commands were executed from the home directory. 

> 
```
ldd /usr/lib/gcc/i486-linux-gnu/4.3/cc1
```


```
	statically linked
```


> ```
gcc -v programs/c/lib*/hello.c
```

```
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.3.2-1ubuntu12' --with-bugurl=file:///usr/share/doc/gcc-4.3/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.3 --program-suffix=-4.3 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu12) 
COLLECT_GCC_OPTIONS='-v' '-mtune=generic'
 /usr/lib/gcc/i486-linux-gnu/4.3.2/cc1 -quiet -v programs/c/lib_example/hello.c -D_FORTIFY_SOURCE=2 -quiet -dumpbase hello.c -mtune=generic -auxbase hello -version -fstack-protector -o /tmp/ccvQWFO7.s
gcc: Internal error: Segmentation fault (program cc1)
Please submit a full bug report.
See <file:///usr/share/doc/gcc-4.3/README.Bugs> for instructions.

```

> ```
gcc-4.1 -v programs/c/lib*/hello.c
```

```

Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++ --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.1.3 --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.3 20080623 (prerelease) (Ubuntu 4.1.2-23ubuntu3)
 /usr/lib/gcc/i486-linux-gnu/4.1.3/cc1 -quiet -v programs/c/lib_example/hello.c -quiet -dumpbase hello.c -mtune=generic -auxbase hello -version -fstack-protector -fstack-protector -o /tmp/ccgmlHX3.s
ignoring nonexistent directory "/usr/local/include/i486-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/i486-linux-gnu/4.1.3/../../../../i486-linux-gnu/include"
ignoring nonexistent directory "/usr/include/i486-linux-gnu"
#include "..." search starts here:
#include <...> search starts here:
 /usr/local/include
 /usr/lib/gcc/i486-linux-gnu/4.1.3/include
 /usr/include
End of search list.
GNU C version 4.1.3 20080623 (prerelease) (Ubuntu 4.1.2-23ubuntu3) (i486-linux-gnu)
	compiled by GNU C version 4.1.3 20080623 (prerelease) (Ubuntu 4.1.2-23ubuntu3).
GGC heuristics: --param ggc-min-expand=79 --param ggc-min-heapsize=92648
Compiler executable checksum: 701f49e7293d34991318670b7ec675ac
programs/c/lib_example/hello.c:1:19: error: stdio.h: No such file or directory
programs/c/lib_example/hello.c: In function ‘main’:
programs/c/lib_example/hello.c:5: warning: incompatible implicit declaration of built-in function ‘printf’

```



The error message is weird!


> ```
gcc-4.2 -v programs/c/lib*/hello.c
```

```
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.2 --program-suffix=-4.2 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.2.4 (Ubuntu 4.2.4-3ubuntu4)
 /usr/lib/gcc/i486-linux-gnu/4.2.4/cc1 -quiet -v programs/c/lib_example/hello.c -quiet -dumpbase hello.c -mtune=generic -auxbase hello -version -fstack-protector -fstack-protector -o /tmp/ccyoe9LG.s
ignoring nonexistent directory "/usr/local/include/i486-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/i486-linux-gnu/4.2.4/../../../../i486-linux-gnu/include"
ignoring nonexistent directory "/usr/include/i486-linux-gnu"
#include "..." search starts here:
#include <...> search starts here:
 /usr/local/include
 /usr/lib/gcc/i486-linux-gnu/4.2.4/include
 /usr/include
End of search list.
GNU C version 4.2.4 (Ubuntu 4.2.4-3ubuntu4) (i486-linux-gnu)
	compiled by GNU C version 4.2.4 (Ubuntu 4.2.4-3ubuntu4).
GGC heuristics: --param ggc-min-expand=79 --param ggc-min-heapsize=92648
Compiler executable checksum: 21e04fdda2d2a1bc2d3b4961d672332a
programs/c/lib_example/hello.c:1:19: error: stdio.h: No such file or directory
programs/c/lib_example/hello.c: In function ‘main’:
programs/c/lib_example/hello.c:5: warning: incompatible implicit declaration of built-in function ‘printf’

```

---

### Post by navneeth on 2009-02-04
> **monkeyking said:**
> you should simply try

[PHP]
gcc-4.1
[/PHP]
instead of gcc.
Or some of the other.

And it gives me rather weird errors, which you can see in my previous post. But at least we know they work.

> If I were you, I would try to remove the build-essential,
reboot.
and install it again.


I'd try it right now, but it's getting late here, and I'll be going to bed in the next few minutes. All the same, I really appreciate you and others helping me out. Thanks a lot. :)

> Is your setup a dapper that you have upgraded all the way through the different versions?


I didn't always upgrade. There were cases where I had to erase and re-install. But for the past two or three releases (maybe even four), the upgrades have been smooth.

> 
If int doesn't help try posting your env
[PHP]env[/PHP]

I'll post it, anyway... :)

```
ORBIT_SOCKETDIR=/tmp/orbit-navneeth
SSH_AGENT_PID=5251
GPG_AGENT_INFO=/tmp/seahorse-D6Xd1N/S.gpg-agent:5296:1
SHELL=/bin/bash
TERM=xterm
XDG_SESSION_COOKIE=0194efc135d1d53e12c5d900462c5b60-1233771183.982631-1677968814
GTK_RC_FILES=/etc/gtk/gtkrc:/home/navneeth/.gtkrc-1.2-gnome2
WINDOWID=31457339
USER=navneeth
LS_COLORS=no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.svgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:
SSH_AUTH_SOCK=/tmp/keyring-iCt4mf/ssh
GNOME_KEYRING_SOCKET=/tmp/keyring-iCt4mf/socket
SESSION_MANAGER=local/ubuntu:/tmp/.ICE-unix/5194
USERNAME=navneeth
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
DESKTOP_SESSION=default
GDM_XSERVER_LOCATION=local
PWD=/home/navneeth
LANG=en_IN
GNOME_KEYRING_PID=5314

GDM_LANG=en_IN
GDMSESSION=default
HISTCONTROL=ignoreboth
SHLVL=1
HOME=/home/navneeth
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
LOGNAME=navneeth
XDG_DATA_DIRS=/usr/local/share/:/usr/share/:/usr/share/gdm/
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-hVf7TI34o9,guid=3b66ce5c38b7c3ca389a7d044989dab2
LESSOPEN=| /usr/bin/lesspipe %s
WINDOWPATH=7
DISPLAY=:0.0
LESSCLOSE=/usr/bin/lesspipe %s %s
COLORTERM=gnome-terminal
XAUTHORITY=/home/navneeth/.Xauthority
_=/usr/bin/env
OLDPWD=/usr/lib

```

---

### Post by nvteighen on 2009-02-04
Just to be sure... are you using 64-bit? It's the only rational possibility I can think of. Otherwise, you may have something broken. (How were you creating the libraries? The correct ways, static and dynamic, are the two described here: [http://crasseux.com/books/ctutorial/Building-a-library.html](http://crasseux.com/books/ctutorial/Building-a-library.html) I doubt you could have broken gcc, but in such a weird case, you never know...)

I never encountered myself with gcc segfaulting... that's weird.

EDIT: An idea from [https://bugzilla.redhat.com/show_bug.cgi?id=445494](https://bugzilla.redhat.com/show_bug.cgi?id=445494)

Try doing:
```

ulimit -s unlimited

```

And then start gcc again...

---

### Post by navneeth on 2009-02-05
> **nvteighen said:**
> Just to be sure... are you using 64-bit? It's the only rational possibility I can think of. Otherwise, you may have something broken.
Nope. 32. I'm trying to remember if something I had done has resulted in this, but nothing pops up. There were some problems with the kernel updates a few days agp, but that had nothing to do with me. 

> (How were you creating the libraries? The correct ways, static and dynamic, are the two described here: [http://crasseux.com/books/ctutorial/Building-a-library.html](http://crasseux.com/books/ctutorial/Building-a-library.html) I doubt you could have broken gcc, but in such a weird case, you never know...)


As per the directions given in the first chapter of *Beginning Linux Programming* 3rd Ed., by Neil Matthew and Richard Stones. (Wiley/Wrox) Very simple stuff, actually. 



> EDIT: An idea from [https://bugzilla.redhat.com/show_bug.cgi?id=445494](https://bugzilla.redhat.com/show_bug.cgi?id=445494)

Try doing:
```

ulimit -s unlimited

```

And then start gcc again...

If by start you mean run the command again, then it doesn't work. 

I've yet to try removing and installing build-install. Will report on that shortly.

---

### Post by navneeth on 2009-02-05
Removing and re-installing build-essential doesn't work.

And what's even strange is that neither 4.1 nor 4.2 recognises the stdio header. :(


Could I possibly (and safely) remove 4.3 and re-install it?

---

### Post by navneeth on 2009-02-05
Just bumping this up.

---

### Post by navneeth on 2009-02-05
Okay, one more person with the same nonsense popping up. 

Someone help me, PLEASE! In fact, I don't even have a working C compiler. I found out that 4.3 doesn't work at all, so I started a thread, [here](http://ubuntuforums.org/showthread.php?p=6669603). But 4.1 and 4.2 tell me that stdio.h doesn't exist. 

build-essential and libc6-dev are installed and the latest versions. 

After updatedb

```
 locate stdio.h
/usr/include/c++/4.2/tr1/stdio.h
/usr/include/c++/4.3/tr1/stdio.h
/usr/lib/perl/5.10.0/CORE/nostdio.h

```

---

### Post by geirha on 2009-02-05
The libc6-dev package installs stdio.h as /usr/include/stdio.h. Can't imagine why it wouldn't be there. Try reinstalling the package
```
sudo aptitude reinstall libc6-dev
```

---

### Post by navneeth on 2009-02-05
> **geirha said:**
> The libc6-dev package installs stdio.h as /usr/include/stdio.h. Can't imagine why it wouldn't be there. Try reinstalling the package
```
sudo aptitude reinstall libc6-dev
```

AWESOME! 

Now I at least have a working version of C compiler. 


Thank you so much.

Do you also have, by any chance, a solution to the main problem that I posted in the other thread? :)

---

### Post by dmizer on 2009-02-05
Please keep support requests to one thread please. It is impossible for people to follow more than one thread which makes more work for both you and the people trying to help you.

If you need immediate support, you may be better off seeking help in the Ubuntu IRC channel: [http://www.ubuntu.com/support/community/chatirc](http://www.ubuntu.com/support/community/chatirc)

Thank you :)

---

### Post by geirha on 2009-02-06
I find it odd that gcc-4.3 would segfault. Try purging gcc-4.3, then install it again. Only thing I can think up is that one or more of the files installed along with gcc-4.3 are corrupt.

```
sudo aptitude purge gcc-4.3
sudo aptitude install gcc-4.3
```

---

### Post by navneeth on 2009-02-06
> **geirha said:**
> I find it odd that gcc-4.3 would segfault. Try purging gcc-4.3, then install it again. Only thing I can think up is that one or more of the files installed along with gcc-4.3 are corrupt.

```
sudo aptitude purge gcc-4.3
sudo aptitude install gcc-4.3
```

Hi, geirha, thanks for looking into this. 

Purging and re-installing didn't work, either. :( 

(For those who might be facing the problem and trying the above solution: you may need to install build-essential separately after the second step.)

---

### Post by Timon&amp;Pumba on 2009-02-09
I am on a 64-bit machine, and have the same problem.
Using gcc-4.3.2-2ubuntu1, compiling even a simple hello world program does not work.

```
Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.3.3-3ubuntu2' --with-bugurl=file:///usr/share/doc/gcc-4.3/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.3 --program-suffix=-4.3 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.3.3 (Ubuntu 4.3.3-3ubuntu2) 
COLLECT_GCC_OPTIONS='-v' '-mtune=generic'
 /usr/lib/gcc/x86_64-linux-gnu/4.3.3/cc1 -quiet -v test.c -D_FORTIFY_SOURCE=2 -quiet -dumpbase test.c -mtune=generic -auxbase test -version -fstack-protector -o /tmp/cc8ohXpo.s
gcc: Internal error: Segmentation fault (program cc1)
Please submit a full bug report.
See <file:///usr/share/doc/gcc-4.3/README.Bugs> for instructions.
```

---

### Post by monkeyking on 2009-02-09
This problem you are having is very weird.

can you try just to run the c preprocessor

[PHP]
cpp yourfile.cpp
[/PHP]

---

### Post by logari81 on 2009-03-07
```
$ dlocate -S /usr/lib/gcc/i486-linux-gnu/4.3/cc1
cpp-4.3: /usr/lib/gcc/i486-linux-gnu/4.3/cc1
g++-4.3: /usr/lib/gcc/i486-linux-gnu/4.3/cc1plus
```

for me the re-installation of cpp-4.3 and g++-4.3 fixed the problem

---

### Post by andrew222 on 2009-03-07
A simpler approach....

Try declaring the main function as:

```
main(){}
```

instead of

```
void main(){}
```

---

### Post by nutznboltz on 2010-01-06
> **navneeth said:**
> 
```
$ gcc hello.c
gcc: Internal error: Segmentation fault (program cc1)
Please submit a full bug report.
See <file:///usr/share/doc/gcc-4.3/README.Bugs> for instructions
```

```
$ gcc --version
gcc (Ubuntu 4.3.2-1ubuntu12) 4.3.2
Copyright (C) 2008 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```

I use Ubuntu 8.10.

I'd appreciate any help in solving this issue.

One of the Ubuntu 8.10 amd64 systems I admin had this very same issue.  I used strace to determine that /usr/lib/gcc/x86_64-linux-gnu/4.3.2/cc1 was the binary that got the SEGFAULT.

The MD5 signature for the cc1 that gets the SEGFAULT:
```

257957f8651047dfc8a13229f4ef70cf /usr/lib/gcc/x86_64-linux-gnu/4.3.2/cc1
```

I copied the cc1 from a working Ubuntu 8.10 (supposedly) identical system.  The MD5 signature for that one matches a few other systems:
```

e293a93ab58c0d62c9ed1168359cf733 /usr/lib/gcc/x86_64-linux-gnu/4.3.2/cc1
```

gcc works now but I have know idea how cc1 got to be different on the two systems.  No other files under /usr/lib/gcc/x86_64-linux-gnu/4.3.2/* on the two systems had different MD5 signatures.

Note that /usr/lib/gcc/x86_64-linux-gnu/4.3.2/cc1 is not in any package list, however the directory /usr/lib/gcc/x86_64-linux-gnu/4.3.2/ is in the gcc-4.3-base package.

```
$ dpkg -S /usr/lib/gcc/x86_64-linux-gnu/4.3.2/cc1
dpkg: /usr/lib/gcc/x86_64-linux-gnu/4.3.2/cc1 not found.

$ dpkg -S /usr/lib/gcc/x86_64-linux-gnu/4.3.2
gcc-4.3-base: /usr/lib/gcc/x86_64-linux-gnu/4.3.2
```

---

