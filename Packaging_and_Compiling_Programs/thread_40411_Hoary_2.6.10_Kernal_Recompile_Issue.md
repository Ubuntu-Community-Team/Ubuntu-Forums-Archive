---
title: "Hoary 2.6.10 Kernal Recompile Issue?"
date: 2005-06-09
forum: Packaging and Compiling Programs
---

### Post by brainwave64 on 2005-06-09
I'm working on recompiling my Hoary 2.6.10 kernel in order to add support for my ITE 8212 RAID controller. However, even when doing a clean compile with no driver modifications according to the wiki instructions at [KernelBuildPackageDetailedHowTo](http://www.ubuntulinux.org/wiki/KernelBuildpackageDetailedHowto),  I've still run into issues. The actual errors are included below. [COLOR=Red]I know the errors are the result of setting the flavour to only compile for k7 (step 4), and I've finally found workarounds (steps 5 and 6) so that it will still compile with the flavour set to k7, but I'm wondering if this is a problem with the way Hoary's source is set up or with the Wiki directions not being applicable to Hoary?[/COLOR] Should the Wiki instructions be updated?

Thanks in advance for any input you can provide!

--------------------------------------------------

**Here is what I did:**

Started in my home directory /home/austin.

$ sudo apt-get update
$ sudo apt-get build-dep linux-source-2.6.8.1
$ sudo apt-get install fakeroot
$ sudo apt-get install devscripts

$ apt-get source linux-source-2.6.10
$ cd linux-source-2.6.10-2.6.10/

1. Added a new version (2.6.10-34.1mod) to debian/changelog using the dch -i command.
2. Renamed the folder debian/abi/2.6.10-34 to "2.6.10-34.1" (should match the 2nd newest version listed in changelog).
3. Made a copy of the file debian/patches/00list-34.1, kept it in the same directory and renamed it to "00list-34.1mod".

[COLOR=Red]4. Added the following setting at line 122 of debian/rules (so it only compiles for the k7 i386 flavour):
   flavours := k7
5. Modified debian/d-i/i386/kernel-versions by replacing "386" with "k7" (it must match one of the flavours being compiled).
6. Removed all i386 entries other than k7 from debian/control and debian/control.stub.[/COLOR]

$ dpkg-buildpackage -rfakeroot -us -uc -b

--------------------------------------------------
[B]
The error I get when I don't first do step 5 (I know this is due to lines 400-403 of the debian/rules file):[/B]
dpkg-deb: building package `linux-image-2.6.10-5-k7' in `../linux-image-2.6.10-5-k7_2.6.10-34.1_i386.deb'.
rm -f -r debian/tmp-image
echo done >  stamp-image
make[2]: Leaving directory `/home/austin/linux-source-2.6.10-2.6.10/debian/build/install-k7'
make[1]: Leaving directory `/home/austin/linux-source-2.6.10-2.6.10/debian/build/install-k7'
dh_testdir
dh_testroot
# unpack the kernels into a temporary directory
mkdir -p debian/d-i-i386
# XXX: this stuff finds the kernels that need upacking according to
# kernel-versions and unpack them into the temp dir.
imagelist=$(cat kernel-versions | grep ^i386 | awk '{print $4}') && \
for i in $imagelist; do \
  dpkg -x $(ls debian/build/linux-image-$i\_*i386.deb) debian/d-i-i386; \
done
[COLOR=Red]ls: debian/build/linux-image-2.6.10-5-386_*i386.deb: No such file or directory[/COLOR]
dpkg-deb: --extract needs a target directory.
Perhaps you should be using dpkg --install ?
make: *** [binary-udebs] Error 2

--------------------------------------------------

**The relavent section from the debian/rules file:**
binary-udebs: binary-debs
[INDENT]dh_testdir
	dh_testroot

	# unpack the kernels into a temporary directory
	mkdir -p debian/d-i-${arch}

	# XXX: this stuff finds the kernels that need upacking according to
	# kernel-versions and unpack them into the temp dir.

	imagelist=$$(cat [COLOR=Red]kernel-versions[/COLOR] | grep ^${arch} | awk '{print $$4}') && \
	for i in $$imagelist; do \
	  dpkg -x $$(ls debian/build/linux-image-$$i\_*${arch}.deb) debian/d-i-${arch}; \
	done

	kernel-wedge make-links[/INDENT]
--------------------------------------------------

[B]The error I get right before the end of compiling when I don't first do step 6:
   (all I know is that the problem is related to the contents of the debian/files file, which is generated during compile)[/B]
for i in $dilist; do \
  dh_builddeb -p$i; \
done
warning, `debian/kernel-image-2.6.10-5-k7-di/DEBIAN/control' contains user-defined field `kernel-version'
dpkg-deb: building package `kernel-image-2.6.10-5-k7-di' in `../kernel-image-2.6.10-5-k7-di_2.6.10-34.1_i386.udeb'.
dpkg-deb: ignoring 1 warnings about the control file(s)
...(lots of similiar lines appear here)
warning, `debian/nfs-modules-2.6.10-5-k7-di/DEBIAN/control' contains user-defined field `kernel-version'
dpkg-deb: building package `nfs-modules-2.6.10-5-k7-di' in `../nfs-modules-2.6.10-5-k7-di_2.6.10-34.1_i386.udeb'.
dpkg-deb: ignoring 1 warnings about the control file(s)
dh_testdir
dh_testroot
chmod u+x debian/make-kernel-patch-pkgs
debian/make-kernel-patch-pkgs linux
dpkg-deb: building package `linux-patch-ubuntu-2.6.10' in `../linux-patch-ubuntu-2.6.10_2.6.10-34.1_i386.deb'.
mv debian/build/*.deb ..
cat debian/build/linux-source-2.6.10/debian/files >> debian/files
rm debian/build/linux-source-2.6.10/debian/files
 dpkg-genchanges -b
dpkg-genchanges: warning: duplicate files list entry for package linux-headers-2.6.10-5 (line 60)
dpkg-genchanges: warning: duplicate files list entry for file linux-headers-2.6.10-5_2.6.10-34.1_i386.deb (line 60)
dpkg-genchanges: warning: unknown information field  in input data in package's section of control info file
dpkg-genchanges: warning: unknown information field  in input data in package's section of control info file
...(lots of similiar lines appear here)
dpkg-genchanges: warning: unknown information field  in input data in package's section of control info file
dpkg-genchanges: warning: unknown information field  in input data in package's section of control info file
dpkg-genchanges: binary-only upload - not including any source code
[COLOR=Red]dpkg-genchanges: failure: cannot open upload file ../linux-headers-2.6.10-5-386_2.6.10-34.1_i386.deb for reading: No such file or directory[/COLOR]

**How the compile is supposed to end (correctly):**
dpkg-genchanges: warning: unknown information field  in input data in package's section of control info file
dpkg-genchanges: warning: unknown information field  in input data in package's section of control info file
dpkg-genchanges: binary-only upload - not including any source code
[COLOR=Red]dpkg-buildpackage: binary only upload (no source included)[/COLOR]

--------------------------------------------------

**The contents of the debian/files file:**
linux-tree-2.6.10_2.6.10-34.1_all.deb devel optional
linux-source-2.6.10_2.6.10-34.1_all.deb devel optional
linux-doc-2.6.10_2.6.10-34.1_all.deb doc optional
linux-headers-2.6.10-5_2.6.10-34.1_i386.deb devel optional
[COLOR=Red]linux-headers-2.6.10-5-386_2.6.10-34.1_i386.deb devel optional
linux-image-2.6.10-5-386_2.6.10-34.1_i386.deb base optional
linux-headers-2.6.10-5-686_2.6.10-34.1_i386.deb devel optional
linux-image-2.6.10-5-686_2.6.10-34.1_i386.deb base optional
linux-headers-2.6.10-5-686-smp_2.6.10-34.1_i386.deb devel optional
linux-image-2.6.10-5-686-smp_2.6.10-34.1_i386.deb base optional[/COLOR]
linux-headers-2.6.10-5-k7_2.6.10-34.1_i386.deb devel optional
linux-image-2.6.10-5-k7_2.6.10-34.1_i386.deb base optional
[COLOR=Red]linux-headers-2.6.10-5-k7-smp_2.6.10-34.1_i386.deb devel optional
linux-image-2.6.10-5-k7-smp_2.6.10-34.1_i386.deb base optional[/COLOR]
kernel-image-2.6.10-5-k7-di_2.6.10-34.1_i386.udeb debian-installer extra
...(all the other *.udeb files apear here)
nfs-modules-2.6.10-5-k7-di_2.6.10-34.1_i386.udeb debian-installer extra
linux-patch-ubuntu-2.6.10_2.6.10-34.1_i386.deb devel optional
linux-headers-2.6.10-5_2.6.10-34.1_i386.deb devel optional

--------------------------------------------------

---

### Post by blind0wl on 2005-06-21
Really simple question...are you logged into your terminal as root?  Just looking at the first output 
```
ls: debian/build/linux-image-2.6.10-5-386_*i386.deb: No such file or directory
dpkg-deb: --extract needs a target directory.
Perhaps you should be using dpkg --install ?
make: *** [binary-udebs] Error 2
```

It just seems when dpkg tries to create the directory for the extract but it cannot find it, so it leads me to believe that the directory isnt even created....

---

### Post by brainwave64 on 2005-06-25
No, actually, I am not logged in as root. However, I am running the whole compile in my home directory, so permission issues shouldn't be a problem.

You are right, though, that the error is occurring because the directory isn't even created. It doesn't exist because I set "flavours" = k7 in my debian/rules file (as the Wiki directed), so *386* files and folders are never created. However, on lines 400-403 of that file (I included them in my post) it reads the contents of the debian/d-i/i386/kernel-versions file, which only lists the 386 flavour. That is what is causing dpkg to look there.

The Wiki I followed was based off of 4.10, and this must not have been an issue in that release.

Thanks for your question.

---

### Post by naumanis on 2005-08-03
Thank you very much for your update, brainwave64. 

I was experiencing exactly the same issues by compiling 686 kernel and I am also believe, that Wiki Kernel Build Howto (*dpkg-buildpackage*) must be rewritten or a comment must be added that these instructions will just not work on Hoary.

I guess everybody else are using *make-kpkg* to build ubuntu 2.6.10 kernel or just put their kernel config in config/i386/386 file.

---

### Post by cowdinosaur on 2005-09-01
I concur. Following brainwave64's modification to kernel-version will work around the problems of building that the wiki did not foresee.

---

