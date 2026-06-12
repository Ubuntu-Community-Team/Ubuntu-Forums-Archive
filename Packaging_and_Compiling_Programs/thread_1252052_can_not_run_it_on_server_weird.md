---
title: "can not run it on server? weird?"
date: 2009-08-28
forum: Packaging and Compiling Programs
---

### Post by fayue1015 on 2009-08-28
I want to run imput2 which is exeutable program
then it prompt me that 
./impute2: error while loading shared libraries: libz.so.1: cannot open shared object file: No such file or directory

actually I have this lib in the system?

how should I do?

[wangyue@compbio ModelBasedImputation]$ ./impute2 
./impute2: error while loading shared libraries: libz.so.1: cannot open shared object file: No such file or directory
[wangyue@compbio ModelBasedImputation]$ ldd /bin/rpm
	linux-vdso.so.1 =>  (0x00007fff386f2000)
	librpm-4.4.so => /usr/lib64/librpm-4.4.so (0x0000003585200000)
	librpmdb-4.4.so => /usr/lib64/librpmdb-4.4.so (0x0000003584e00000)
	libselinux.so.1 => /lib64/libselinux.so.1 (0x0000003274e00000)
	librpmio-4.4.so => /usr/lib64/librpmio-4.4.so (0x00000036c1400000)
	libsqlite3.so.0 => /usr/lib64/libsqlite3.so.0 (0x0000003803c00000)
	libelf.so.1 => /usr/lib64/libelf.so.1 (0x0000003584a00000)
	libm.so.6 => /lib64/libm.so.6 (0x0000003274600000)
	libpopt.so.0 => /lib64/libpopt.so.0 (0x0000003282e00000)
**	libz.so.1 => /lib64/libz.so.1 (0x0000003275200000)**
	libnss3.so => /lib64/libnss3.so (0x00000036c0c00000)
	libnssutil3.so => /lib64/libnssutil3.so (0x00000036c1000000)
	libplds4.so => /lib64/libplds4.so (0x0000003276e00000)
	libplc4.so => /lib64/libplc4.so (0x0000003275600000)
	libnspr4.so => /lib64/libnspr4.so (0x0000003277600000)
	libdl.so.2 => /lib64/libdl.so.2 (0x0000003274200000)
	librt.so.1 => /lib64/librt.so.1 (0x0000003fb3c00000)
	libpthread.so.0 => /lib64/libpthread.so.0 (0x0000003fb3400000)
	libbz2.so.1 => /lib64/libbz2.so.1 (0x000000328a200000)
	libc.so.6 => /lib64/libc.so.6 (0x0000003273e00000)
	/lib64/ld-linux-x86-64.so.2 (0x0000003273a00000)
	libgcc_s.so.1 => /lib64/libgcc_s.so.1 (0x0000003280e00000)

---

### Post by fayue1015 on 2009-08-30
is there any help?

---

