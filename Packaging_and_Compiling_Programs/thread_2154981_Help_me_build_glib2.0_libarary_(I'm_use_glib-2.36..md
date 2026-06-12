---
title: "Help me build glib2.0 libarary (I'm use glib-2.36.3) for ARM use arm-linux-gcc !!!!"
date: 2013-06-16
forum: Packaging and Compiling Programs
---

### Post by kdich on 2013-06-16
Hi everybody !

I build glib2.0 for FriendlyARM but get erorr :

make[4]: Entering directory `/home/kdich/Downloads/glib-2.36.3/gobject'
  CC     libgobject_2_0_la-gatomicarray.lo
  CC     libgobject_2_0_la-gbinding.lo
  CC     libgobject_2_0_la-gboxed.lo
  CC     libgobject_2_0_la-gclosure.lo
gclosure.c:29:17: error: ffi.h: No such file or directory
gclosure.c:1128: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
gclosure.c: In function 'value_from_ffi_type':
gclosure.c:1217: error: 'ffi_arg' undeclared (first use in this function)
gclosure.c:1217: error: (Each undeclared identifier is reported only once
gclosure.c:1217: error: for each function it appears in.)
gclosure.c:1217: error: 'int_val' undeclared (first use in this function)
gclosure.c:1217: error: expected expression before ')' token
gclosure.c: At top level:
gclosure.c:1296: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
gclosure.c: In function 'g_cclosure_marshal_generic':
gclosure.c:1391: error: 'ffi_type' undeclared (first use in this function)
gclosure.c:1391: error: 'rtype' undeclared (first use in this function)
gclosure.c:1392: error: ISO C90 forbids mixed declarations and code
gclosure.c:1394: error: 'atypes' undeclared (first use in this function)
gclosure.c:1395: error: ISO C90 forbids mixed declarations and code
gclosure.c:1397: error: 'ffi_cif' undeclared (first use in this function)
gclosure.c:1397: error: expected ';' before 'cif'
gclosure.c:1398: error: ISO C90 forbids mixed declarations and code
gclosure.c:1405: error: implicit declaration of function 'value_to_ffi_type'
gclosure.c:1409: error: 'ffi_type_void' undeclared (first use in this function)
gclosure.c:1412: error: 'ffi_arg' undeclared (first use in this function)
gclosure.c:1415: error: expected expression before ')' token
gclosure.c:1427: error: 'ffi_type_pointer' undeclared (first use in this function)
gclosure.c:1451: error: implicit declaration of function 'ffi_prep_cif'
gclosure.c:1451: error: 'cif' undeclared (first use in this function)
gclosure.c:1451: error: 'FFI_DEFAULT_ABI' undeclared (first use in this function)
gclosure.c:1451: error: 'FFI_OK' undeclared (first use in this function)
gclosure.c:1454: error: implicit declaration of function 'ffi_call'
gclosure.c: In function 'g_cclosure_marshal_generic_va':
gclosure.c:1469: error: 'ffi_type' undeclared (first use in this function)
gclosure.c:1469: error: 'rtype' undeclared (first use in this function)
gclosure.c:1470: error: ISO C90 forbids mixed declarations and code
gclosure.c:1472: error: 'atypes' undeclared (first use in this function)
gclosure.c:1473: error: ISO C90 forbids mixed declarations and code
gclosure.c:1476: error: 'ffi_cif' undeclared (first use in this function)
gclosure.c:1476: error: expected ';' before 'cif'
gclosure.c:1477: error: ISO C90 forbids mixed declarations and code
gclosure.c:1489: error: 'ffi_type_void' undeclared (first use in this function)
gclosure.c:1492: error: 'ffi_arg' undeclared (first use in this function)
gclosure.c:1495: error: expected expression before ')' token
gclosure.c:1504: error: 'ffi_type_pointer' undeclared (first use in this function)
gclosure.c:1525: error: implicit declaration of function 'va_to_ffi_type'
gclosure.c:1547: error: 'cif' undeclared (first use in this function)
gclosure.c:1547: error: 'FFI_DEFAULT_ABI' undeclared (first use in this function)
gclosure.c:1547: error: 'FFI_OK' undeclared (first use in this function)
make[4]: *** [libgobject_2_0_la-gclosure.lo] Error 1
make[4]: Leaving directory `/home/kdich/Downloads/glib-2.36.3/gobject'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/kdich/Downloads/glib-2.36.3/gobject'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/kdich/Downloads/glib-2.36.3/gobject'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/kdich/Downloads/glib-2.36.3'
make: *** [all] Error 2

My setup for variable enviroment :
xport PREFIX=/opt/FriendlyARM/toolschain/4.4.3/arm-none-linux-gnueabi/sys-root
export CFLAGS="-O2 -I$PREFIX/include -I$PREFIX/usr/include"
export CPPFLAGS="-I$PREFIX/include -I$PREFIX/usr/include"
export LDFLAGS="-L$PREFIX/lib -L$PREFIX/usr/lib"

export CC=arm-linux-gcc
export CXX=arm-linux-g++
export LD=arm-linux-ld
export NM="arm-linux-nm -B"
export RANLIB=arm-linux-ranlib
export STRIP=arm-linux-strip
export OBJCOPY=arm-linux-objcopy


export LDFLAGS=-L$PREFIX/lib
export CFLAGS="-g -I$PREFIX/include"
export PKG_CONFIG_PATH=$PREFIX/lib/pkgconfig:$PKG_CONFIG_PATH

Everyone help me, please !

Thanks very much !

---

