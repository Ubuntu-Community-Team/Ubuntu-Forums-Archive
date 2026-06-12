---
title: "buld cross-toolchain in ubuntu"
date: 2007-04-17
forum: Programming Talk
---

### Post by tomane on 2007-04-17
Hello, I'm trying to build a cross-compiler for the microblaze target.
I got the source and scripts which were used to build the toolchain from source under cygwin.

I don't know the origin of the files, all I can tell is that there are a few tcsh scripts used to run the build process, here's the list:
```
-rwxr--r-- 1 to   to   1020 2007-04-16 14:07 build_gcc.csh
-rwxr--r-- 1 to   to    705 2007-04-16 14:07 build_gdb.csh
-rwxr--r-- 1 to   to    110 2007-04-16 14:07 common.csh
-rwxr--r-- 1 to   to   1040 2007-04-16 14:07 do_all_binutils.csh
-rwxr--r-- 1 to   to   3438 2007-04-16 14:07 do_all_gcc.csh
-rwxr--r-- 1 to   to   1113 2007-04-16 14:07 do_all_gdb.csh
-rwxr--r-- 1 to   to   7572 2007-04-16 14:07 do_all_newlib.csh
-rwxr--r-- 1 to   to   1932 2007-04-16 14:07 do_all_uclinux.csh
-rwxr--r-- 1 to   to    383 2007-04-17 09:55 do_everything.csh
-rwxr--r-- 1 to   to    362 2007-04-16 14:07 init_path.csh
drwxr-xr-x 3 to   to   4096 2007-04-16 14:13 release
drwxr-xr-x 8 to   to   4096 2007-04-16 14:14 srcs
```

I use `do_everything.csh` to fire up the build process. During the `configure` phase of binutils, it abort after some time with the following error:
```
*** ld does not support target microblaze
*** see ld/configure.tgt for supported targets
Configure in /home/to/files_local/software/fw_gcc_dev/fw_gcc_dev/build/linux/bld_binutils/ld failed, exiting.
```

I installed binutils-multiarch but it still doesn't solve the problem.
This is the first time I'm creating a cross-compiler and I don't know where to go next. Can someoe provide some hints/resources on how to build the toolchain?

cheers,
--to

---

### Post by izak on 2007-04-17
I built a cross-toolchain in ubuntu for an sh4 processor earlier this year. Head over to [http://buildroot.uclibc.org/buildroot.html](http://buildroot.uclibc.org/buildroot.html) . They have a collection of makefiles and scripts to help automate the process, but don't expect it to be easy:)

---

### Post by scorpio2002 on 2007-08-23
Did you manage to compile buildroot? I can't -.- And I can't compile crosstool... basically nothing useful to cross-compiling compiles on my ubuntu box -.-

---

### Post by tomane on 2007-08-23
I believe that I managed to solve my problem, but I didn't touch buildroot nor crosstool at all.
My problem was that the files were given to me in a zip archive which didn't preserve the original file permissions.
I tried to restore them but not all at first and it ended up that the script that translates architecture/platform names wasn't executable so the configure script would think that the architecture was unsupported.

Changing the permissions to the scripts solved the problem. Now I "repacked" them in a tarball as it should have been in the first place.

Cheers,
--to

---

