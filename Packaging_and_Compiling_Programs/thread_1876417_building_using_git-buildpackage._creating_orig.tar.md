---
title: "building using git-buildpackage. creating orig.tar.gz help"
date: 2011-11-06
forum: Packaging and Compiling Programs
---

### Post by deepclutch on 2011-11-06
Hi,
I am trying to build debian packages from git debian compiz source. 

[http://anonscm.debian.org/gitweb/?p=pkg-xorg/app/compiz.git](http://anonscm.debian.org/gitweb/?p=pkg-xorg/app/compiz.git)

I pulled the git sources and edited debian/control file to suit the dependencies and committed. but, when I run "git-buildpackage" it fails . saying *.orig.tar.gz is missing.

I tried reading the documentation and it is confusing as it says about setting a repository?
/usr/share/doc/git-buildpackage/manual-html/index.html

EDIT: Since I am using Gnome-2.30.2 on Debian Testing, I don't want "compiz-kde" package being built once compiled. Is there any way to prevent kde specific packages from being built? I removed kde dependencies and removed "compiz-kde" in debian/control file hoping it will work.
I need to know what I am missing. does it needs to edit debian/gbp.conf ? 

Thanks.

---

### Post by SevenMachines on 2011-11-06
Can you post the output? git-buildpackage should create an orig.tar.gz automatically

---

### Post by MadCow108 on 2011-11-06
this repository has no pristine-tar brranch
but you can download the orig.tar with uscan

---

### Post by SevenMachines on 2011-11-06
also,
$ cmake ../ -DCOMPIZ_DISABLE_PLUGIN_KDE=ON -DBUILD_KDE4=OFF

---

### Post by deepclutch on 2011-11-06
> **MadCow108 said:**
> this repository has no pristine-tar brranch
but you can download the orig.tar with uscan

Please brief or can You show Me a link on how to use uscan to create/download orig.tar.gz. this is very confusing for Me as to how to import the *.orig.tar.gz from git branch in this particular case.

Will a Snapshot from the current version works as a replacement for orig.tar.gz 
this: 
[http://anonscm.debian.org/gitweb/?p=pkg-xorg/app/compiz.git;a=snapshot;h=9f9188e26727ea648fb49015462ca9c61fcaf529;sf=tgz](http://anonscm.debian.org/gitweb/?p=pkg-xorg/app/compiz.git;a=snapshot;h=9f9188e26727ea648fb49015462ca9c61fcaf529;sf=tgz)

if I rename it to compiz_0.9.5.0.orig.tar.gz and place it a directory before the git source, will it work.

debian/gbp.conf file in the git source is this:
```
cat debian/gbp.conf 
[DEFAULT]
debian-branch = debian-unstable
debian-tag = compiz-%(version)s
upstream-branch = upstream-unstable
upstream-tag = compiz-%(version)s
[git-dch]
meta = 1

```> **SevenMachines said:**
> Can you post the output? git-buildpackage should create an orig.tar.gz automatically
since no compiz_0.9.5.0.orig.tar.gz lies in ../ directory, it fails to proceed.
```
git-buildpackage 
dh clean
   dh_testdir
   dh_auto_clean
   dh_clean
# upstream build leaves this around
rm -f po/compiz.pot
**gbp:info: compiz_0.9.5.0.orig.tar.gz does not exist, creating from 'compiz-0.9.5.0'**
fatal: Not a valid object name compiz-0.9.5.0

``````
         also,
$ cmake ../ -DCOMPIZ_DISABLE_PLUGIN_KDE=ON -DBUILD_KDE4=OFF     
```I need to add these lines in debian/rules and git commit ? is their something like "DEB_BUILD_OPTIONS=" line to prevent the kde packages from being built? 

Thanks 

---------
_**UPDATE:**_
I tried: 
> Will a Snapshot from the current version works as a replacement for orig.tar.gz 
this: 
[http://anonscm.debian.org/gitweb/?p=pkg-xorg/app/compiz.git;a=snapshot;h=9f9188e26727ea648fb49015462ca9c61fcaf529;sf=tgz](http://anonscm.debian.org/gitweb/?p=pkg-xorg/app/compiz.git;a=snapshot;h=9f9188e26727ea648fb49015462ca9c61fcaf529;sf=tgz)

if I rename it to compiz_0.9.5.0.orig.tar.gz and place it a directory before the git source, will it work.

first, this is the "git status" :
```
 git status
# On branch debian-unstable
# **Your branch is ahead of 'origin/debian-unstable' by 5 commits.**
#
nothing to commit (working directory clean 
```
I copied the snapshot tarball,renamed it 
and it built packages. but, shows LOT of warnings regarding dpkg-shlibs :(  I am doubting will these packages works well in the system or will be instable/segfault? lot of linking warnings! also look at the "your branch is ahead" warning from git-status makes any mismatch between versions downloaded?(I think tarball is for the last version and the same as git source downloaded)
Here: [http://paste.ubuntu.com/730143/](http://paste.ubuntu.com/730143/)
some of them:
```
dpkg-shlibdeps: warning: debian/compiz-plugins/usr/lib/compiz/librotate.so contains an unresolvable reference to symbol _ZN10CompScreen9grabExistEPKc: it's probably a plugin.
dpkg-shlibdeps: **warning: 129 other similar warnings** have been skipped (use -v to see them all).

``````
dpkg-shlibdeps: warning: dependency on libpangoft2-1.0.so.0 could be avoided if "debian/compiz-gtk/usr/bin/gtk-window-decorator" were not uselessly linked against it (they use none of its symbols).
dpkg-shlibdeps: warning: diversions involved - output may be incorrect
 diversion by glx-diversions from: /usr/lib/x86_64-linux-gnu/libGL.so.1
dpkg-shlibdeps: warning: diversions involved - output may be incorrect
 diversion by glx-diversions to: /usr/lib/mesa-diverted/x86_64-linux-gnu/libGL.so.1
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcompiztoolbox.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcompiztoolbox.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcompiztoolbox.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libopengl.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libopengl.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libopengl.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcomposite.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcomposite.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libcomposite.so'
dpkg-shlibdeps: warning: debian/compiz-plugins/usr/lib/compiz/libscreenshot.so contains an
```@SevenMachines: All compiz packages are built except compiz-kde. :) Thanks for the Tip. But, DEB_BUILD_OPTIONS will work or not :/
I added the line at:
```
override_dh_auto_configure:
        # currently, segfault if CMAKE_BUILD_TYPE=Release
        dh_auto_configure -- -DCOMPIZ_BUILD_WITH_RPATH=FALSE -DCOMPIZ_DEFAULT_PLUGINS=\"$(DEFAULT_PLUGINS)\" -DCMAKE_BUILD_TYPE=RelWithDebInfo -DCOMPIZ_PACKAGING_ENABLED=TRUE
**       cmake ../ -DCOMPIZ_DISABLE_PLUGIN_KDE=ON -DBUILD_KDE4=OFF**

```

---

### Post by MadCow108 on 2011-11-06
> **deepclutch said:**
> I copied the snapshot tarball,renamed it 
and it built packages. but, shows LOT of warnings regarding dpkg-shlibs :(  I am doubting will these packages works well in the system or will be instable/segfault? lot of linking warnings! also look at the "your branch is ahead" warning from git-status makes any mismatch between versions downloaded?(I think tarball is for the last version and the same as git source downloaded)

those should be fine, as the files mentioned are indeed plugins, so the symbols will always be resolved before they are loaded.
the ubuntu buildlogs also show these warnings.

---

### Post by deepclutch on 2011-11-06
@MadCow108: Would like to Know more about > download the orig.tar with uscan

---

### Post by SevenMachines on 2011-11-06
git-buildpackage looks for a branch corresponding to the changelog version to autobuild the tar.gz archive. e.g,

# Clone compiz git
```
$ git clone git://git.debian.org/git/pkg-xorg/app/compiz
Cloning into compiz...
remote: Counting objects: 29289, done.
remote: Compressing objects: 100% (6809/6809), done.
remote: Total 29289 (delta 22655), reused 28861 (delta 22320)
Receiving objects: 100% (29289/29289), 12.31 MiB | 1.21 MiB/s, done.
Resolving deltas: 100% (22655/22655), done.
$ cd compiz/
```# Looks for a branch based on the changelog version 0.9.5.0
```
$ git-buildpackage 
dh clean
   dh_testdir
   dh_auto_clean
   dh_clean
# upstream build leaves this around
rm -f po/compiz.pot
gbp:info: compiz_0.9.5.0.orig.tar.gz does not exist, creating from 'compiz-0.9.5.0'
fatal: Not a valid object name compiz-0.9.5.0
```# But there isnt one
```
$ git branch 
* debian-unstable
```# So make one
```
$ git branch compiz-0.9.5.0 debian-unstable
$ git branch
  compiz-0.9.5.0
* debian-unstable
```# This should work now
```
$ git-buildpackage 
dh clean
   dh_testdir
   dh_auto_clean
   dh_clean
# upstream build leaves this around
rm -f po/compiz.pot
gbp:info: compiz_0.9.5.0.orig.tar.gz does not exist, creating from 'compiz-0.9.5.0'
 dpkg-buildpackage -rfakeroot -D -us -uc -i -I7
.....
....
```Theres maybe a better way to specify the branch to use but I had no joy with --git-debian-branch=debian-unstable

uscan probably isnt generally what you want when building packages from git but might be more what you're looking for. It uses the debian/watch file to pattern match check for newer versions from a link so...

```
$ cat debian/watch 
version=3
http://releases.compiz.org/([\d\.]+)[\d]/ compiz-([\d\.]+)\.tar\.bz2
```# Get uscan to check the above link for new releases, if it finds one it downloads it to ../
```
$ uscan
compiz: Newer version (0.9.5.92.1) available on remote site:
  http://releases.compiz.org/0.9.5.92.1/compiz-0.9.5.92.1.tar.bz2
  (local version is 0.9.5.0)
compiz: Successfully downloaded updated package compiz-0.9.5.92.1.tar.bz2
    and symlinked compiz_0.9.5.92.1.orig.tar.bz2 to it

```

---

### Post by deepclutch on 2011-11-06
Thank You @SevenMachines. :) much helpful.
---
in the last try of compiling compiz and after installing the compiz packages:
"compiz --replace" showed:
compiz_0.9.5.0 failed to load due to errors like wall,theme,session etc not loading error. I built libcompizconfig0 to match the version. but to no avail. I was doubtful after seeing lot of warning messages(ABI incompatibility included) in the earlier compiling.
Will Try tomorrow and will update this thread tomorrow.
Thanks Again.

---

### Post by deepclutch on 2011-11-07
I have compiled compiz and it compiles and builds packages. 
libcompizconfig0(>= 0.9) is a dependency for compiz and I am trying to compile it from git.

 , I branched to libcompizconfig-0.9.5.0 after debian-unstable.
```
:~$ git branch 
* debian-unstable
  libcompizconfig-0.9.5.0
 
```
but, when I run git-buildpackage, this error comes:
[COLOR=Red]fatal: Not a valid object name 0.9.5.0[/COLOR]

```
 $ git-buildpackage 
dh clean
   dh_testdir
   dh_auto_clean
   debian/rules override_dh_clean
make[1]: Entering directory `/home/meow/compiz-dev/LIBS/libcompizconfig'
dh_clean -X plugin/ccp/src/ccp.cpp~
rm -f src/compizconfig.pb.cc src/compizconfig.pb.h
make[1]: Leaving directory `/home/meow/compiz-dev/LIBS/libcompizconfig'
gbp:info: libcompizconfig_0.9.5.0.orig.tar.gz does not exist, creating from '0.9.5.0'
**fatal: Not a valid object name 0.9.5.0**
  
```
the auto completion shows this, when I tried "git branchTAB" :
```
0.5.2                                            libcompizconfig-0.7.6-1 
0.6.0                                            libcompizconfig-0.8.2-1 
0.7.2                                            libcompizconfig-0.8.2-1-bpo50+1 
0.7.4                                            libcompizconfig-0.8.2-2 
0.7.6                                            libcompizconfig-0.8.4-1 
0.7.8                                            libcompizconfig-0.8.4-2 
0.8.2                                            libcompizconfig-0.9.2.1+git20110226.78a7cc8c-1 
0.8.4                                            libcompizconfig-0.9.5.0 
0.9.0                                            origin/debian-lenny-backports 
debian-unstable                                  origin/debian-squeeze 
HEAD                                             origin/debian-unstable 
libcompizconfig-0.6.0                            origin/HEAD 
libcompizconfig-0.6.0-1                          origin/upstream-lenny-backports 
libcompizconfig-0.6.0-2                          origin/upstream-squeeze 
libcompizconfig-0.7.4-1                          origin/upstream-unstable 
libcompizconfig-0.7.4-2                   
```

but, for compiz, the above branching worked.

---

### Post by SevenMachines on 2011-11-07
```
fatal: Not a valid object name 0.9.5.0
```[COLOR=Red]
[/COLOR]Means it can't find a branch with that name. So you could again just create that branch.
```
$ git branch             
* debian-unstable
$ git branch 0.9.5.0 debian-unstable 
$ git branch 
  0.9.5.0
* debian-unstable
```
I'm not sure if theres better ways of doing this but seems a reasonable idea to have a branch that matches up to a package version in any case.

---

### Post by deepclutch on 2011-11-07
Thanks Again. Yes, it did the work and built the packages.

---

