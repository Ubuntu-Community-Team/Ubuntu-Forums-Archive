---
title: "Cannot find -lperl"
date: 2008-09-04
forum: Packaging and Compiling Programs
---

### Post by tom66 on 2008-09-04
I am trying to compile Golly, the Game of Life simulator. make install throws the following message.

```

/usr/bin/ld: cannot find -lperl
collect2: ld returned 1 exit status
make: *** [golly] Error 1

```

Any help appreciated, thanks!

---

### Post by whelanh on 2008-09-05
My response is probably off the mark since I have not tried to compile Golly....but...it seems to be telling you that you do not have the perl library installed, or it cannot find it.

What happens when you run "locate libperl" from the command line?  When I do that, I get:

/usr/lib/libperl.so.5.8
/usr/lib/libperl.so.5.8.8
/usr/lib/libperld.a
/usr/lib/debug/usr/lib/libperl.so.5.8.8
/usr/share/defoma/libperl-file.pl
/usr/share/defoma/libperl-hint.pl
/usr/share/doc/libperl-critic-perl
/usr/share/doc/libperl5.8
/usr/share/doc/libperl-critic-perl/KomodoIntegration.pod
/usr/share/doc/libperl-critic-perl/TODO.pod.gz
/usr/share/doc/libperl-critic-perl/changelog.Debian.gz
/usr/share/doc/libperl-critic-perl/changelog.gz
/usr/share/doc/libperl-critic-perl/copyright
/usr/share/doc/libperl-critic-perl/examples
/usr/share/doc/libperl-critic-perl/perlcritic.el.gz
/usr/share/doc/libperl-critic-perl/examples/generatestats.gz
/usr/share/doc/libperl-critic-perl/examples/loadanalysisdb.gz
/usr/share/doc/libperl-critic-perl/examples/perlcriticrc-conway.gz
/usr/share/doc/libperl-critic-perl/examples/perlcriticrc.gz
/var/lib/dpkg/info/libperl-critic-perl.list
/var/lib/dpkg/info/libperl-critic-perl.md5sums
/var/lib/dpkg/info/libperl5.8.list
/var/lib/dpkg/info/libperl5.8.md5sums
/var/lib/dpkg/info/libperl5.8.postinst

The library is in /usr/lib which is generally in the default search path for most compilers.

Hope that helps.
Best,
Hugh

---

### Post by tonybaqain on 2008-09-23
hello,

simply ```
ln -sf /usr/lib/libperl.so.5.8 /usr/lib/libperl.so
```
and then
```
sudo ldconfig
```

then have fun :)

---

### Post by Lee Pan on 2009-02-17
Hi All,

I still have this problem with ld: cannot find -lperl, even I have install libperl-dev.
locate libperl:
appfs/net-snmp$ locate libperl 
/usr/lib/perl5/5.00503/ppc_8xx-linux/CORE/libperl.a 
/usr/lib/libperl.a 
/usr/lib/libperl.so 
/usr/lib/libperl.so.5.8 
/usr/lib/libperl.so.5.8.8 
/usr/share/defoma/libperl-file.pl 
/usr/share/defoma/libperl-hint.pl 
/usr/share/doc/libperl-dev 
/usr/share/doc/libperl5.8 
/var/cache/apt/archives/libperl-dev_5.8.8-12ubuntu0.4_i386.deb 
/var/cache/apt/archives/libperl5.8_5.8.8-12ubuntu0.4_i386.deb 
/var/lib/dpkg/info/libperl-dev.list 
/var/lib/dpkg/info/libperl-dev.md5sums 
/var/lib/dpkg/info/libperl5.8.list 
/var/lib/dpkg/info/libperl5.8.md5sums 
/var/lib/dpkg/info/libperl5.8.postinst 
/var/lib/dpkg/info/libperl5.8.shlibs 

Do I short some lib files?

The compiling error:
/usr/lib/perl/5.8.8/auto/DynaLoader/DynaLoader.a -L/usr/lib/perl/5.8.8/CORE -lperl -ldl -lm -lpthread -lc -lcrypt  
/opt/hardhat/devkit/ppc/8xx/powerpc-hardhat-linux/bin/ld: cannot find -lperl 
collect2: ld returned 1 exit status 
make[1]: *** [snmpd] Error 1 

Thanks

Lee

---

