---
title: "how can I add specific librarys to linker?"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by clapton on 2008-09-16
Hello people,
I've got to compile LSD, I need to add to linker some library, how can I add?
THe instructions files says that I install like this:
```
make -f makefile.ln
```

I type
```
ldd /usr/bin/wish
```

returns
```

       linux-vdso.so.1 =>  (0x00007fff3e5fe000)
	libtk8.4.so.0 => /usr/lib/libtk8.4.so.0 (0x00007f2835fe1000)
	libtcl8.4.so.0 => /usr/lib/libtcl8.4.so.0 (0x00007f2835d19000)
	libpthread.so.0 => /lib/libpthread.so.0 (0x00007f2835afd000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0x00007f28357fa000)
	libdl.so.2 => /lib/libdl.so.2 (0x00007f28355f6000)
	libm.so.6 => /lib/libm.so.6 (0x00007f2835375000)
	libc.so.6 => /lib/libc.so.6 (0x00007f2835013000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f28362dd000)
	libxcb-xlib.so.0 => /usr/lib/libxcb-xlib.so.0 (0x00007f2834e12000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0x00007f2834bf7000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0x00007f28349f5000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00007f28347f0000)

```

How can I add to linker this libs?

THank you for answers!

---

