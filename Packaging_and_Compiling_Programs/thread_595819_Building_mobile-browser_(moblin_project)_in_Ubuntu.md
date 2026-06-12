---
title: "Building mobile-browser (moblin project) in Ubuntu 7.04 fails"
date: 2007-10-29
forum: Packaging and Compiling Programs
---

### Post by milind_iitg on 2007-10-29
DETAILS:--

I am building mozilla in chroot environment using commands pdebuild, pbuilder (package-building tools) with sudo & 

appropriate options. These package-builder tools use chroot intensively, so I cannot do away with chroot. I 

downloaded all modules from [http://www.moblin.org/repos/](http://www.moblin.org/repos/) for building mobile linux modules(there are 10-12 C/C++ 

modules, all I successfully built & installed), except mozilla, which fails at the starting phase itself. This is 

due to chroot being used. All other modules also use chroot, but they do not fail due to this. I am confused as to 

how only mozilla fails when there seems to be no difference at all in the way the building takes place.

The error captured is :--

dpkg-buildpackage: source package is mozilla
dpkg-buildpackage: source version is 19990716.M8-3
dpkg-buildpackage: source changed by Brent A. Fulgham <bfulgham@debian.org>
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 19990716.M8-3
 fakeroot debian/rules clean
dh_testdir
make: dh_testdir: Command not found
make: *** [clean] Error 127
Copying back the cached apt archive contents
 -> unmounting /home/persist/moblin filesystem
 -> unmounting dev/pts filesystem
 -> unmounting proc filesystem
 -> cleaning the build env
    -> removing directory /var/cache/pbuilder/build//5553 and its subdirectories
-------------------------------------------------------------------
I am not using ./configure & such commands, as it will take me lot of time to install packages manually. and also 

./configure fails due to gtk+-2.0 & other packages not present. 
  Please use sudo with all package-building commands, as well as for download & installs.

2) Steps to Reproduce:--

1. Download the package(takes quite some time).. the command is:-->
git clone [http://moblin.org/repos/projects/mobile-browser.git](http://moblin.org/repos/projects/mobile-browser.git)
you can also download other moblin ( C/C++ ) modules to see them succeeding in their respective builds. It downloads 

from the CVS repositories.
2. ln -s ./build/package/debian ./debian to create soft-link
3. sudo pdebuild --use-pdebuild-internal , it should do all the build process (i.e unpacking, installing packages, configure, running makefiles, etc) till creating the final executable (.exe, or .so)

3) Actual Result:--

fakeroot debian/rules clean
dh_testdir
make: dh_testdir: Command not found
make: *** [clean] Error 127
Copying back the cached apt archive contents
 -> unmounting /home/persist/moblin filesystem
 -> unmounting dev/pts filesystem
 -> unmounting proc filesystem
 -> cleaning the build env
    -> removing directory /var/cache/pbuilder/build//10107 and its
subdirectories

Expected Results:  
The build should go on, as with the other modules, and it should locate
dh_testdir command in chroot environments.

Please provide me a workaround or check if I am missing anything, as I tried
hard to find any hacks/workarounds, but I have to use chroot..

---

### Post by mlind on 2007-10-31
Package must build-depend on debhelper which provides the missing dh_testdir script.

---

### Post by milind_iitg on 2007-11-01
hello mlind,
  Thanks for the reply, though brief. Could you provide pointers to this..
Also, if you went through the whole detail, I stated that dh_testdir & other dh-related scripts are already there in /usr/sbin/ & even if in the Rules file, I specify the whole /ur/sbin/dh_testdir, it gives the same error..
/usr/sbin/dh_testdir
make: /usr/sbin/dh_testdir: Command not found
  This is happening due to chroot, and the environment is changing. I know theoretically about chroot. As I am new to building in Ubuntu. But my other modules did not fail in Ubuntu, though they also used chroot in the same way. Only mobile-browser failed.
  If you could try downloading just the mobile-browser module from [http://www.moblin.org/repos/](http://www.moblin.org/repos/), through the steps I suggested (how to download) in 2) Steps to Reproduce:-- (in earlier comm)..
then it would be great. If it succeeds, then it would also be surprising to me.
  If you can do it, please convey to me. Any other information would also be beneficial.

---

### Post by mlind on 2007-11-01
Your package must Build-Depends on debhelper so that package gets installed in the chroot environment. I suggest you to read the [New Maintainers Guide]("http://www.debian.org/doc/maint-guide/") for starters.

The source package doesn't look very good, you will probably have hard time to get it compile properly.

---

### Post by milind_iitg on 2007-11-20
Hello mlind,

The chroot problem went off with your suggestion. 
Later on., I got this error:--
configure: error: Library requirements (gtk+-2.0 >= 1.3.7) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

I installed gtk+-2.0 with this command:--
sudo apt-get install build-essential linux-headers-`uname -r` gcc-3.4 libgtk2.0-dev

After that, when I run the ./configure, gtk passes, but different dependency package error comes.

But gtk fails ( same above gtk error) comes, when I build with sudo pdebuild --use-pdebuild-internal, though it passes with configure. 
  Can you point it what is wrong, and how I can eliminate that by using pdebuild. 
  I also added this in Depends:
gtk+-2.0 >= 1.3.7

  What is going wrong. Is it in configure script or debian/control file. I know I have to add many things to debian/control.. Debian Maintainer's guide is not becoming much useful to me. I m a newbie in Ubuntu, so please give me pointers on this. Till then, I will use ./configure to resolve other package dependency errors.

---

### Post by dholbach on 2007-11-21
Try running ./configure by hand in the chroot and read config.log to find out what's missing.

---

