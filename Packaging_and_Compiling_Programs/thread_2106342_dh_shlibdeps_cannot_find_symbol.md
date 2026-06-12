---
title: "dh_shlibdeps cannot find symbol"
date: 2013-01-18
forum: Packaging and Compiling Programs
---

### Post by jabernathy on 2013-01-18
Hello everyone,

While packaging some upstream software, dpkg-shlibdeps is emitting a large number of warnings during the build process.

An example is:

```
dpkg-shlibdeps: warning: symbol _ZN17asynNDArrayDriver14createFileNameEiPc used by debian/libadvsplugins/usr/lib/x86_64-linux-gnu/libNDPluginAttributes.so.2 found in none of the libraries.
```

The symbol should be provided by a library from another package named "libsynapps5" that I've created. The library is named libADBase.so.5.

This is an excerpt from the /var/lib/dpkg/info/libsynapps5:amd64.symbols file on my system:

```
libADBase.so.5 libsynapps5 #MINVER#
...
 _ZN17asynNDArrayDriver14createFileNameEiPc@Base 6
....
```

Here is confirmation that libNDPluginAttributes.so.2 is linked against libADBase.so.5:

```
ldd debian/libadvsplugins/usr/lib/x86_64-linux-gnu/libNDPluginAttributes.so.2
	linux-vdso.so.1 =>  (0x00007fff8f9ff000)
	libNDPlugin.so.5 => /usr/lib/x86_64-linux-gnu/libNDPlugin.so.5 (0x00007f6ebbe7d000)
	libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f6ebbc60000)
	libstdc++.so.6 => /usr/lib/x86_64-linux-gnu/libstdc++.so.6 (0x00007f6ebb95f000)
	libgcc_s.so.1 => /lib/x86_64-linux-gnu/libgcc_s.so.1 (0x00007f6ebb749000)
	libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f6ebb38a000)
	libADBase.so.5 => /usr/lib/x86_64-linux-gnu/libADBase.so.5 (0x00007f6ebb15b000)
	libnetCDF.so.5 => /usr/lib/x86_64-linux-gnu/libnetCDF.so.5 (0x00007f6ebae7d000)
....
```

The only thing I can notice is that the symbol name has the suffix @Base in the .symbols file.

Also, the installed libADBase.so.5 file doesn't have any symbols included. They were stripped out during the package building process.

Why can't dpkg-shlibdeps find the symbol in the .symbols file?

Thanks!

---

