---
title: "Help Packaging A Script Library For Installation"
date: 2009-11-19
forum: Packaging and Compiling Programs
---

### Post by Nuvious on 2009-11-19
I have a set of scripts I'd like to package for installation.  The only dependencies are loopaes, expect and bash; after that it's all scripts, config files and a few aliases in /etc/rc.*.   The scripts are listed below:

/usr/sbin/bb
/usr/sbin/bb_setup
/usr/sbin/bb_mount
/usr/sbin/basedirs (directory)
/usr/sbin/imgs (directory)
/etc/bb/example.config
/etc/init.d/bb_sys
/etc/rc.d(016)/K80bb_sys (alias of bb_sys)
/etc/rc.d(35)/S10bb_sys (alias of bb_sys)

I would like to release this as both a no-arc package and an ubuntu package but I have no idea how to build either.  I've tried using Automake but I'm getting the vibe that that's a bit of overkill; however if I could use it I would prefer it as it would make it easier to update the make/config files.  I need to check on the dependencies (expect and libaes) and then install the files listed above.  Any help is greatly appreciated as this is my first experience with making a package for distribution in linux.

---

### Post by SevenMachines on 2009-11-19
you should have a look at, in particular,
[https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete)
and perhaps
[http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/)
and see how you get on.
dependency resolution is done in debian/control. packaging can be quite simple if you use [cdbs]("https://wiki.ubuntu.com/PackagingGuide/Complete#Packaging%20with%20CDBS"), yes, your debian/rules file can happily install all files with only a couple of lines!
you could also
$apt-get source hello-debhelper
and have a look at how thats been packaged, it'll use more features of debian packaging than you'll probably need but it'll give you a good example of how things work

---

