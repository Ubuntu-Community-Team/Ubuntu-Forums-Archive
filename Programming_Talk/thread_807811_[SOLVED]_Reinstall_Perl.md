---
title: "[SOLVED] Reinstall Perl"
date: 2008-05-26
forum: Programming Talk
---

### Post by keenlearner on 2008-05-26
Hello, I have perl interpreter install using sypnatic package manager, now I want to reinstall perl from the source code with different configuration setting. Should I remove the perl first from the sypnatic package ? when I try to to so they are a lot of package that depend on perl, it seems unwise. So I just resinstall from source directly,

./Configure -doptimize='-g'
make
Making x2p stuff
make[1]: Entering directory `/home/william/p/perl-5.8.8/x2p'
You haven't done a "make depend" yet!
make[1]: *** [hash.o] Error 1
make[1]: Leaving directory `/home/william/p/perl-5.8.8/x2p'
make: *** [translators] Error 2

When I run
make depend

sh ./makedepend MAKE=make
./makedepend: Already running, exiting.
test -s perlmain.c && touch perlmain.c
cd x2p; make depend
make[1]: Entering directory `/home/william/p/perl-5.8.8/x2p'
sh ../makedepend MAKE=make
../makedepend: Already running, exiting.
make[1]: Leaving directory `/home/william/p/perl-5.8.8/x2p'


How to solve this ? Thanks

---

### Post by pdwerryhouse on 2008-05-26
No, don't remove the perl packages, and replace them with one you compiled yourself, as you will break your system badly.

Compile perl to install itself in a different location within the filesystem, for example, /usr/local/perl5.8.8/

You can do this by using the following to configure it:

./configure.gnu --prefix=/usr/local/perl5.8.8

(and then the usual make, make install, etc).

Then to use the new perl binary, put the following at the top of your scripts:

#!/usr/local/perl5.8.8/bin/perl

---

### Post by danbuter on 2008-05-26
Makes me wish Hardy had Perl 5.10, as I was thinking about doing the same thing.

---

### Post by keenlearner on 2008-05-26
Thanks pdwerryhouse for the solutions. 

But I got these error when using make,

After I ran, 
 ./Configure -Dusethreads -Dprefix=p/perl/ -Doptimize='-g' 

Then 
make 

        Making DynaLoader (static) 
make[1]: Entering directory `/home/william/p/perl-5.8.8/ext/ 
DynaLoader' 
Makefile out-of-date with respect to ../../lib/Config.pm ../../ 
config.h 
Cleaning current config before rebuilding Makefile... 
make -f Makefile.old clean > /dev/null 2>&1 
../../miniperl "-I../../lib" "-I../../lib" Makefile.PL 
"INSTALLDIRS=perl" "PERL_CORE=1" "LIBPERL_A=libperl.a" 
Processing hints file hints/linux.pl 
Writing Makefile for DynaLoader 
==> Your Makefile has been rebuilt. <== 
==> Please rerun the make command.  <== 
false 
make[1]: *** [Makefile] Error 1 
make[1]: Leaving directory `/home/william/p/perl-5.8.8/ext/DynaLoader' 

Extracting xsubpp (with variable substitutions) 
make[1]: Leaving directory `/home/william/p/perl-5.8.8/utils' 

        Making x2p stuff 
make[1]: Entering directory `/home/william/p/perl-5.8.8/x2p' 
You haven't done a "make depend" yet! 
make[1]: *** [hash.o] Error 1 
make[1]: Leaving directory `/home/william/p/perl-5.8.8/x2p' 
make: *** [translators] Error 2 

Above are the two portions of errors that I am having. Thanks

---

### Post by slavik on 2008-05-26
screw 5.10 ... I want 6!!!!!!!! :P

---

### Post by danbuter on 2008-05-26
I'll believe in 6 when I see it. And I'm not really sure I like where it's heading. Requiring Parrot to do anything? How will this effect CL one-liners? Or won't it? The whole Parrot thing is confusing.

---

### Post by unutbu on 2008-05-26
According to [http://ubuntuforums.org/showthread.php?t=291651](http://ubuntuforums.org/showthread.php?t=291651)
the build-essential package is a meta-package which installs other packages necessary for compiling programs. Do you have it installed?

---

### Post by slavik on 2008-05-26
> **danbuter said:**
> I'll believe in 6 when I see it. And I'm not really sure I like where it's heading. Requiring Parrot to do anything? How will this effect CL one-liners? Or won't it? The whole Parrot thing is confusing.
parrot is a VM, just like JVM is, just like the VM that perl 5 uses.

parrot is pretty much like the .NET VM where multiple languages compile to a single byte code.

there is also pugs, which is the leading implementation of Perl6 as Larry puts out the apocalypses. But the latest svn doesn't build and the older version requires ghc 6.6 (6.8 is in hardy). pugs is written in haskel.

---

### Post by keenlearner on 2008-05-26
> **unutbu said:**
> According to [http://ubuntuforums.org/showthread.php?t=291651](http://ubuntuforums.org/showthread.php?t=291651)
the build-essential package is a meta-package which installs other packages necessary for compiling programs. Do you have it installed?

I ran that but still the same problem. Thanks

---

### Post by unutbu on 2008-05-26
> **keenlearner said:**
> 
 ./Configure -Dusethreads -Dprefix=p/perl/ -Doptimize='-g' 

Did you run ./Configure with a capital C? Usually configure scripts start with a little c... 
If the configure command failed, then maybe it did not write your Makefile. (See below.)

> **keenlearner said:**
> 
Then 
make 

        Making DynaLoader (static) 
make[1]: Entering directory `/home/william/p/perl-5.8.8/ext/ 
DynaLoader' 
**Makefile out-of-date** with respect to ../../lib/Config.pm ../../ 


Perhaps something is wrong with your Makefile?

---

### Post by keenlearner on 2008-05-26
> **unutbu said:**
> Did you run ./Configure with a capital C? Usually configure scripts start with a little c... 
If the configure command failed, then maybe it did not write your Makefile. (See below.)



Perhaps something is wrong with your Makefile?

I have use the capital C of Configure as show by the exact command. Yeah there might be something wrong with the Makefile, even it's auto generated by Configure.

---

### Post by unutbu on 2008-05-26
keenlearner, I managed to compile perl 5.8.8 with

```
16:56:38 child@play:~/src% mkdir /home/child/opt
16:56:38 child@play:~/src% cd perl-5.8.8/
16:56:42 child@play:~/src/perl-5.8.8% ./Configure -Dusethreads -Dprefix=/home/child/opt -Doptimize='-g' 
17:04:23 child@play:~/src/perl-5.8.8% make
```

play is running Gutsy.

I just pressed return at all Configure questions, unless Configure forced me to do something different, like supply a path. Whenever I entered a path, I gave an absolute path. I see you used a relative path, p/perl, but I don't know if this makes any difference.


I found this in the INSTALL directions:

> If you have built perl before, you should clean out the build directory
with the command

	make distclean

Perhaps you should do a make distclean and just try again from the beginning.

---

### Post by keenlearner on 2008-05-27
> 
If you have built perl before, you should clean out the build directory
with the command

make distclean

I have done that the same error of configure that I always get is the 

> 
Run make depend now? [y]  
sh ./makedepend MAKE=make
./makedepend: Already running, exiting.
test -s perlmain.c && touch perlmain.c
cd x2p; make depend
make[1]: Entering directory `/home/william/p/perl-5.8.8/x2p'
sh ../makedepend MAKE=make
make[2]: Entering directory `/home/william/p/perl-5.8.8/x2p'
echo hash.c  str.c util.c walk.c | tr ' ' '\n' >.clist
make[2]: Leaving directory `/home/william/p/perl-5.8.8/x2p'
../makedepend: 1: Syntax error: Unterminated quoted string
make[1]: *** [depend] Error 2
make[1]: Leaving directory `/home/william/p/perl-5.8.8/x2p'
make: *** [depend] Error 2


You got the perl source code from  [http://www.cpan.org/src/README.html](http://www.cpan.org/src/README.html) ?
5.8	5.8.8	perl-5.8.8.tar.gz	maint	2 years, 3 months, 25 days

---

### Post by keenlearner on 2008-05-27
Thanks unutbu, it appear to be a bug of perl

[http://bugs.openembedded.org/show_bug.cgi?id=2035](http://bugs.openembedded.org/show_bug.cgi?id=2035)
[http://www.nntp.perl.org/group/perl.perl5.porters/2008/02/msg133863.html](http://www.nntp.perl.org/group/perl.perl5.porters/2008/02/msg133863.html)

---

### Post by unutbu on 2008-05-27
keenlearner, I'm glad you found the solution!

For anyone stuck in the same situation, the solution appears to be:
```
sudo ln -sf /bin/bash /bin/sh
```

---

