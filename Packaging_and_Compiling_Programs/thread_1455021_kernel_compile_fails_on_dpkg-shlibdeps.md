---
title: "kernel compile fails on dpkg-shlibdeps"
date: 2010-04-15
forum: Packaging and Compiling Programs
---

### Post by surferX on 2010-04-15
I am compiling the stock ubuntu kernel linux-image-2.6.31-20-generic the code is unchanged, however I have changed a couple of things to be complied as modules that were part of the kernel proper that causes problem with my old t41.

The deb for the kernel-image is created fine  the linux-headers is fails on this error:

dh_shlibdeps -plinux-headers-2.6.31-20-generic
dpkg-shlibdeps: error: no dependency information found for /lib/libc.so.6 (used by debian/linux-headers-2.6.31-20-generic/usr/src/linux-headers-2.6.31-20-generic/scripts/kallsyms).
dh_shlibdeps: dpkg-shlibdeps returned exit code 2
make[1]: *** [binary-generic] Error 1
make: *** [binary-generic] Error 2

is there a simple fix, or a way to run the stock script so it does not create the kernel-headers?

---

### Post by gmargo on 2010-04-15
The **dpkg-shlibdeps** man page says it looks for a "symbols" or "shlibs" file, in this case **/var/lib/dpkg/info/libc6.symbols** and **/var/lib/dpkg/info/libc6.shlibs**.  Do you have those files?

---

### Post by surferX on 2010-04-15
thanks that gave me a clue, I had the files but i suspected some corruption on var so i resinstall libc6

#aptitude reinstall libc6

and that fixed it thanks

---

### Post by jamil.farooq@hotmail.com on 2011-10-28
i am having a similar issue when trying installing ati-driver for radeon 5800. i hav tried reinstalling libc6 but it didn't work. i have recently upgraded to 11.10 and since then i m not able to install that driver from the downloaded script from ati site.


would appreciate your help
thanx

---

### Post by jamil.farooq@hotmail.com on 2011-10-28
this is the output log of my driver script


> 
objdump: debian/fglrx/usr/lib/pxpress/alt_ld.so.conf: File truncated
objdump: debian/fglrx/usr/lib/pxpress/ld.so.conf: File format not recognized
objdump: debian/fglrx/usr/lib/fglrx/alt_ld.so.conf: File truncated
objdump: debian/fglrx/usr/lib/fglrx/ld.so.conf: File format not recognized
   debian/rules override_dh_shlibdeps
make[1]: Entering directory `/tmp/fglrx.Nki86X'
dh_shlibdeps -l/tmp/fglrx.Nki86X/debian/fglrx/usr/lib/fglrx
dpkg-shlibdeps: error: no dependency information found for /lib/libc.so.6 (used by debian/fglrx/usr/lib/fglrx/libatiadlxx.so).
dh_shlibdeps: dpkg-shlibdeps -Tdebian/fglrx.substvars debian/fglrx/usr/lib/fglrx/libXvBAW.so.1.0 debian/fglrx/usr/lib/fglrx/libatiuki.so.1.0 debian/fglrx/usr/lib/fglrx/libaticalrt.so debian/fglrx/usr/lib/fglrx/libfglrx_dm.so.1.0 debian/fglrx/usr/lib/fglrx/xorg/modules/linux/libfglrxdrm.so debian/fglrx/usr/lib/fglrx/xorg/modules/glesx.so debian/fglrx/usr/lib/fglrx/xorg/modules/extensions/libglx.so debian/fglrx/usr/lib/fglrx/xorg/modules/drivers/fglrx_drv.so debian/fglrx/usr/lib/fglrx/xorg/modules/amdxmm.so debian/fglrx/usr/lib/fglrx/libGL.so.1.2 debian/fglrx/usr/lib/fglrx/dri/fglrx_dri.so debian/fglrx/usr/lib/fglrx/libaticaldd.so debian/fglrx/usr/lib/fglrx/bin/atiodcli debian/fglrx/usr/lib/fglrx/bin/aticonfig debian/fglrx/usr/lib/fglrx/bin/atiode debian/fglrx/usr/lib/fglrx/bin/atieventsd debian/fglrx/usr/lib/fglrx/bin/amdnotifyui debian/fglrx/usr/lib/fglrx/bin/fgl_glxgears debian/fglrx/usr/lib/fglrx/bin/fglrxinfo debian/fglrx/usr/lib/fglrx/libaticalcl.so debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 debian/fglrx/usr/lib/fglrx/libatiadlxx.so returned exit code 2
make[1]: *** [override_dh_shlibdeps] Error 2
make[1]: Leaving directory `/tmp/fglrx.Nki86X'
make: *** [binary-arch] Error 2
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.5Cut3s





---

