---
title: "[SOLVED] Error trying to 'make' libconfuse2.6"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by Maverick1712 on 2008-11-19
Hey all

I am currently trying to setup AwesomeWM usin this tutorial: [http://ubuntuforums.org/showthread.php?t=678902](http://ubuntuforums.org/showthread.php?t=678902)

The problem I am running in to is on the second step, downloading and making libconfuse2.6. These are the results when I try to run make:

```
adam@*****:~/confuse-2.6$ make
make  all-recursive
make[1]: Entering directory `/home/adam/confuse-2.6'
Making all in m4
make[2]: Entering directory `/home/adam/confuse-2.6/m4'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/adam/confuse-2.6/m4'
Making all in po
make[2]: Entering directory `/home/adam/confuse-2.6/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/adam/confuse-2.6/po'
Making all in src
make[2]: Entering directory `/home/adam/confuse-2.6/src'
if /bin/bash ../libtool --mode=compile gcc -DLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_CONFIG_H -I. -I. -I..    -Wall -Werror -g -O2 -MT lexer.lo -MD -MP -MF ".deps/lexer.Tpo" -c -o lexer.lo lexer.c; \
	then mv -f ".deps/lexer.Tpo" ".deps/lexer.Plo"; else rm -f ".deps/lexer.Tpo"; exit 1; fi
 gcc -DLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_CONFIG_H -I. -I. -I.. -Wall -Werror -g -O2 -MT lexer.lo -MD -MP -MF .deps/lexer.Tpo -c lexer.c -o lexer.o
cc1: warnings being treated as errors
lexer.c: In function 'cfg_yylex':
lexer.l:270: error: ignoring return value of 'fwrite', declared with attribute warn_unused_result
make[2]: *** [lexer.lo] Error 1
make[2]: Leaving directory `/home/adam/confuse-2.6/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/adam/confuse-2.6'
make: *** [all] Error 2
```

I have searched the forums and other internet sources and haven't been able to find a solution thus far. I checked out the Makefile, but wasn't able to make heads or tails of it (no pun intended). Any help is appreciated.

Cheers.

---

### Post by mc4man on 2008-11-19
I'm assuming your using intrepid because confuse builds fine on hardy.

If so, note that libconfuse0-2.6 is available in repo.
The main difference between what your doing/following is your 'how to' is installing to /usr/local/lib with a configure option of '--enable-static'

The repo will install to /usr/lib with a configure option of '--enable-shared'

Don't know if it matters

Intrepid seems to fail compiling because of it's default gcc version (4:4.3.1

I was able to build successfully by switching to earlier version (4:4.2.3

I did fool around a little to much so it's too late tonight to see if just installing some of the below packages would work with prefixing the configure to use the 4.2.3 version

Anyway this did work  (in synaptic

> Removed the following packages:
build-essential
dh-buildinfo
g++
g++-4.3
gcc
libstdc++6-4.3-dev


> Installed the following packages:
cpp-4.2 (4.2.4-3ubuntu4)
gcc-4.2 (4.2.4-3ubuntu4)

Installed the following packages:
g++-4.2 (4.2.4-3ubuntu4)
libstdc++6-4.2-dev (4.2.4-3ubuntu4)


And then from here downloaded and installed gcc (4:4.2.3-1ubuntu3)

[http://packages.ubuntu.com/hardy/gcc](http://packages.ubuntu.com/hardy/gcc)

checkinstall will probably fail, just use sudo make install
Keep your sources folder, cd'ing to it and running sudo make uninstall will remove confuse if needed.

If you want to try then cd to your confuse-2.6 folder and then run from the prompt
make clean
./configure
make
sudo make install

note; you could also **before doing any of the above** (including the remove and add) run this to make sure.
```
sudo apt-get build-dep confuse
```

---

### Post by ad_267 on 2008-11-19
This guide here worked perfectly for me:
[http://awesome.naquadah.org/wiki/index.php?title=Awesome-3-git-Ubuntu-Intrepid](http://awesome.naquadah.org/wiki/index.php?title=Awesome-3-git-Ubuntu-Intrepid)

I didn't need to build libconfuse.

---

### Post by mc4man on 2008-11-19
I would definitely try the previous post's link, your 'how to' is from 9 months ago, probably gutsy.

---

### Post by Maverick1712 on 2008-11-19
Hey guys. 

The other tutorial worked flawlessly. The only thing I changed was making Awesome a new GDM entry instead of linking it to Xsession (for now). Thanks!

---

### Post by ad_267 on 2008-11-20
> **Maverick1712 said:**
> Hey guys. 

The other tutorial worked flawlessly. The only thing I changed was making Awesome a new GDM entry instead of linking it to Xsession (for now). Thanks!

Yeah that's what I did too. I was also using Urukrama's guide at [http://urukrama.wordpress.com/2008/07/10/first-steps-with-awesome-window-manager/](http://urukrama.wordpress.com/2008/07/10/first-steps-with-awesome-window-manager/).

That's based on Awesome 2.3 and the configuration is completely different with version 3, but some of the information was still useful.

---

