---
title: "/usr/bin/ld: cannot find -lCg"
date: 2008-10-15
forum: Packaging and Compiling Programs
---

### Post by linhdkl on 2008-10-15
Hi 

I've on ready install OGRE [[COLOR="Red"]here[/COLOR]]("http://www.ogre3d.org/wiki/index.php/Building_From_Source#Ubuntu_.2F_Kubuntu")

when i set up for cg from Cg-2.0_May2008_x86.tgz 
it's ok but when i type 
```
gcc -lCg
```
it's error 
```
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.3/../../../../lib/libCg.so when searching for -lCg
/usr/bin/ld: skipping incompatible /usr/lib/../lib/libCg.so when searching for -lCg
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.3/../../../libCg.so when searching for -lCg
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libCg.so when searching for -lCg
/usr/bin/ld: skipping incompatible /usr/lib64/libCg.so when searching for -lCg
/usr/bin/ld: skipping incompatible /usr/lib/libCg.so when searching for -lCg
/usr/bin/ld: cannot find -lCg
collect2: ld returned 1 exit status
```

it's cause for when i type 
```
./configure
```
it's show message this 
```
checking for cgCreateProgram in -lCg... no
configure: error:
	****************************************************************
	* You do not have the nVidia Cg libraries installed.           *
	* Go to http://developer.nvidia.com/object/cg_toolkit.html     *
	* (Click on Cg_Linux.tar.gz).                                  *
	* You can disable the building of Cg support by providing      *
	* --disable-cg to this configure script but this is highly     *
	* discouraged as this breaks many of the examples.             *
	****************************************************************

```

some one have any idea for my problem ... ?
thanks so much !

---

