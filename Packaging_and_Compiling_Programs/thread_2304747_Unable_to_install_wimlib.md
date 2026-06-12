---
title: "Unable to install wimlib"
date: 2015-11-29
forum: Packaging and Compiling Programs
---

### Post by Hodevah on 2015-11-29
Using the latest build of this to build a Windows PE .
**wimtools** is deprecated. Therefore **wimlib**. 

```
git clone git://wimlib.net/wimlib
```
 
```
cd Download/wimlib
```
 Prepare to ./configure , make , and make-install
```
wimlib]$ ./configure
bash: ./configure: No such file or directory
```

Perhaps something is missing....

```
sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version
```

Nope. Everything is fine.

Having a look at the rwx listings inside the** /wimlib** folder

```
ls -l
total 208
drwxrwxr-x 2 frankenstein frankenstein  4096 Nov 29 12:54 archlinux
-rwxrwxr-x 1 frankenstein frankenstein    54 Nov 29 12:54 bootstrap
drwxrwxr-x 2 frankenstein frankenstein  4096 Nov 29 12:54 build-aux
-rw-rw-r-- 1 frankenstein frankenstein 10050 Nov 29 12:54 configure.ac
-rw-rw-r-- 1 frankenstein frankenstein    41 Nov 29 12:54 configure.windows
-rw-rw-r-- 1 frankenstein frankenstein   984 Nov 29 12:54 COPYING
-rw-rw-r-- 1 frankenstein frankenstein 35147 Nov 29 12:54 COPYING.GPLv3
-rw-rw-r-- 1 frankenstein frankenstein  7637 Nov 29 12:54 COPYING.LGPLv3
drwxrwxr-x 3 frankenstein frankenstein  4096 Nov 29 12:54 debian
drwxrwxr-x 3 frankenstein frankenstein  4096 Nov 29 12:54 doc
drwxrwxr-x 2 frankenstein frankenstein  4096 Nov 29 12:54 examples
drwxrwxr-x 3 frankenstein frankenstein  4096 Nov 29 12:54 include
-rw-rw-r-- 1 frankenstein frankenstein 15749 Nov 29 12:54 INSTALL
drwxrwxr-x 2 frankenstein frankenstein  4096 Nov 29 12:54 m4
-rw-rw-r-- 1 frankenstein frankenstein  8762 Nov 29 12:54 Makefile.am
-rw-rw-r-- 1 frankenstein frankenstein 36312 Nov 29 12:54 NEWS
drwxrwxr-x 2 frankenstein frankenstein  4096 Nov 29 12:54 programs
-rw-rw-r-- 1 frankenstein frankenstein 19580 Nov 29 12:54 README
drwxrwxr-x 2 frankenstein frankenstein  4096 Nov 29 12:54 rpm
drwxrwxr-x 2 frankenstein frankenstein  4096 Nov 29 12:54 src
drwxrwxr-x 4 frankenstein frankenstein  4096 Nov 29 12:54 tests
drwxrwxr-x 3 frankenstein frankenstein  4096 Nov 29 12:54 tools
-rw-rw-r-- 1 frankenstein frankenstein   360 Nov 29 12:54 wimlib.pc.in

```

Perhaps it is to be built using autoconf and automake?


```
autoconf
configure.ac:7: error: possibly undefined macro: AM_INIT_AUTOMAKE
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.ac:24: error: possibly undefined macro: AM_PROG_CC_C_O
configure.ac:57: error: possibly undefined macro: AM_CONDITIONAL
configure.ac:87: error: possibly undefined macro: AC_DEFINE
configure.ac:98: error: possibly undefined macro: AC_MSG_ERROR
configure.ac:105: error: possibly undefined macro: AM_ICONV
configure.ac:197: error: possibly undefined macro: AC_PROG_NASM
configure.ac:225: error: possibly undefined macro: AC_MSG_WARN


```
after some Googling, figured that I needed some extras. 
```
pkg-config, libtool, gfortran
```

Ok. Try again.


```
autoconf
```
No output. 
Hmmm. Try automake, now.

```
automake -a
configure.ac: error: no proper invocation of AM_INIT_AUTOMAKE was found.
configure.ac: You should verify that configure.ac invokes AM_INIT_AUTOMAKE,
configure.ac: that aclocal.m4 is present in the top-level directory,
configure.ac: and that aclocal.m4 was recently regenerated (using aclocal)
Makefile.am:155: error: WITH_NTFS_3G does not appear in AM_CONDITIONAL
Makefile.am:161: error: WINDOWS_NATIVE_BUILD does not appear in AM_CONDITIONAL
Makefile.am:195: error: ENABLE_SSSE3_SHA1 does not appear in AM_CONDITIONAL
Makefile.am:221: error: WINDOWS_NATIVE_BUILD does not appear in AM_CONDITIONAL
Makefile.am:310: error: WITH_FUSE does not appear in AM_CONDITIONAL
Makefile.am:314: error: WITH_NTFS_3G does not appear in AM_CONDITIONAL
Makefile.am:326: error: WINDOWS_NATIVE_BUILD does not appear in AM_CONDITIONAL
Makefile.am: error: required file './AUTHORS' not found
Makefile.am: error: required file './ChangeLog' not found
configure.ac:12: error: required file 'config.h.in' not found
Makefile.am:29: error: Libtool library used but 'LIBTOOL' is undefined
Makefile.am:29:   The usual way to define 'LIBTOOL' is to add 'LT_INIT'
Makefile.am:29:   to 'configure.ac' and run 'aclocal' and 'autoconf' again.
Makefile.am:29:   If 'LT_INIT' is in 'configure.ac', make sure
Makefile.am:29:   its definition is in aclocal's search path.
Makefile.am:36: warning: source file 'src/add_image.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
automake: warning: possible forward-incompatibility.
automake: At least a source file is in a subdirectory, but the 'subdir-objects'
automake: automake option hasn't been enabled.  For now, the corresponding output
automake: object file(s) will be placed in the top-level directory.  However,
automake: this behaviour will change in future Automake versions: they will
automake: unconditionally cause object files to be placed in the same subdirectory
automake: of the corresponding sources.
automake: You are advised to start using 'subdir-objects' option throughout your
automake: project, to avoid future incompatibilities.
Makefile.am:36: warning: source file 'src/avl_tree.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/blob_table.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/capture_common.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/compress.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/compress_common.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/compress_parallel.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/compress_serial.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/decompress.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/decompress_common.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/delete_image.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/dentry.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/divsufsort.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/encoding.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/error.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/export_image.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/extract.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/file_io.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/header.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/inode.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/inode_fixup.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/inode_table.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/integrity.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/iterate_dir.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/join.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/lcpit_matchfinder.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/lzms_common.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/lzms_compress.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/lzms_decompress.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/lzx_common.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/lzx_compress.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/lzx_decompress.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/metadata_resource.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/mount_image.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/pathlist.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/paths.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/pattern.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/progress.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/resource.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/reference.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/security.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/sha1.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/solid.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/split.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/reparse.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/tagged_items.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/template.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/textfile.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/timestamp.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/update_image.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/util.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/verify.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/wim.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/write.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/x86_cpu_features.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/xml.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/xpress_compress.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:36: warning: source file 'src/xpress_decompress.c' is in a subdirectory,
Makefile.am:36: but option 'subdir-objects' is disabled
Makefile.am:156: warning: source file 'src/ntfs-3g_apply.c' is in a subdirectory,
Makefile.am:156: but option 'subdir-objects' is disabled
Makefile.am:156: warning: source file 'src/ntfs-3g_capture.c' is in a subdirectory,
Makefile.am:156: but option 'subdir-objects' is disabled
Makefile.am:162: warning: source file 'src/win32_common.c' is in a subdirectory,
Makefile.am:162: but option 'subdir-objects' is disabled
Makefile.am:162: warning: source file 'src/win32_apply.c' is in a subdirectory,
Makefile.am:162: but option 'subdir-objects' is disabled
Makefile.am:162: warning: source file 'src/win32_capture.c' is in a subdirectory,
Makefile.am:162: but option 'subdir-objects' is disabled
Makefile.am:162: warning: source file 'src/win32_replacements.c' is in a subdirectory,
Makefile.am:162: but option 'subdir-objects' is disabled
Makefile.am:162: warning: source file 'src/wimboot.c' is in a subdirectory,
Makefile.am:162: but option 'subdir-objects' is disabled
Makefile.am:172: warning: source file 'src/unix_apply.c' is in a subdirectory,
Makefile.am:172: but option 'subdir-objects' is disabled
Makefile.am:172: warning: source file 'src/unix_capture.c' is in a subdirectory,
Makefile.am:172: but option 'subdir-objects' is disabled
Makefile.am:304: warning: source file 'tests/tree-cmp.c' is in a subdirectory,
Makefile.am:304: but option 'subdir-objects' is disabled
Makefile.am:216: warning: source file 'programs/imagex.c' is in a subdirectory,
Makefile.am:216: but option 'subdir-objects' is disabled
Makefile.am:222: warning: source file 'programs/imagex-win32.c' is in a subdirectory,
Makefile.am:222: but option 'subdir-objects' is disabled
Makefile.am:222: warning: source file 'programs/wgetopt.c' is in a subdirectory,
Makefile.am:222: but option 'subdir-objects' is disabled
/usr/share/automake-1.15/am/depend2.am: error: am__fastdepCC does not appear in AM_CONDITIONAL
/usr/share/automake-1.15/am/depend2.am:   The usual way to define 'am__fastdepCC' is to add 'AC_PROG_CC'
/usr/share/automake-1.15/am/depend2.am:   to 'configure.ac' and run 'aclocal' and 'autoconf' again
/usr/share/automake-1.15/am/depend2.am: error: AMDEP does not appear in AM_CONDITIONAL
/usr/share/automake-1.15/am/depend2.am:   The usual way to define 'AMDEP' is to add one of the compiler tests
/usr/share/automake-1.15/am/depend2.am:     AC_PROG_CC, AC_PROG_CXX, AC_PROG_OBJC, AC_PROG_OBJCXX,
/usr/share/automake-1.15/am/depend2.am:     AM_PROG_AS, AM_PROG_GCJ, AM_PROG_UPC
/usr/share/automake-1.15/am/depend2.am:   to 'configure.ac' and run 'aclocal' and 'autoconf' again
/usr/share/automake-1.15/am/check2.am: error: am__EXEEXT does not appear in AM_CONDITIONAL
```


Do not really understand the above error. 
But I will try again, using ./configure. Even though I suspicion that ./configure at point  is not the program to use. 

```
./configure
configure: error: cannot find install-sh, install.sh, or shtool in build-aux "."/build-aux


```
NOpe. 
Well, that is because the folder was not meant to carry any of the those. Hence my suspicion that it is to built using [B]autoconf

[/B]Looking for some assistance, please.
 
EDIT: I would like to point out that the /wimlib folder's README file does say to use ./configure, make, and make-install. Very strange.

---

