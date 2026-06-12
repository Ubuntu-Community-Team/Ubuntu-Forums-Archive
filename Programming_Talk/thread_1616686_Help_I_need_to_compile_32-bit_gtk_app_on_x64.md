---
title: "Help I need to compile 32-bit gtk app on x64"
date: 2010-11-08
forum: Programming Talk
---

### Post by nolag on 2010-11-08
I currently am doing this with a chroot.  The solution is not ideal (as it takes a lot of space and constantly requires me to chroot) I would much rather just do -m32 (right now it won't find the gtkmm headers stuff).  I would like to be able to install the gtk 32-bit librarries in the lib32 folder with apt-get like I did for the 64-bit.  Is this possible?  Any help is greatly appreciated :D.

---

### Post by johnl on 2010-11-08
Hi,

As far as I can tell the gtk+2 libs are part of the ia32-libs package.  You can test this by doing **dpkg -S /usr/lib32/libgtk-x11-2.0.so.0** with ia32-libs installed.

You will also need to have the '-dev' package installed (which includes the header files), but this is platform agnostic.

I compiled the following code with "-m32" on my amd64 box and had no problems running the result:

```

#include <stdlib.h>
#include <stdio.h>
#include <gtk/gtk.h>

int main(int argc, char* argv[]) 
{
    gtk_init(&argc, &argv);


    gtk_main();
    
    return 0;
}

```

compiled with:

```
gcc -m32 `pkg-config --cflags --libs gtk+-2.0` -Wall gtktest_main.c -o gtktest
'file' output:
./gtktest: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs),
for GNU/Linux 2.6.15, not stripped

'ldd' output:
ldd ./gtktest
	linux-gate.so.1 =>  (0xf7704000)
	libgtk-x11-2.0.so.0 => /usr/lib32/libgtk-x11-2.0.so.0 (0xf7312000)
	libgdk-x11-2.0.so.0 => /usr/lib32/libgdk-x11-2.0.so.0 (0xf727a000)
	libatk-1.0.so.0 => /usr/lib32/libatk-1.0.so.0 (0xf725f000)
	libgio-2.0.so.0 => /usr/lib32/libgio-2.0.so.0 (0xf7173000)
	libpangoft2-1.0.so.0 => /usr/lib32/libpangoft2-1.0.so.0 (0xf714d000)
	libpangocairo-1.0.so.0 => /usr/lib32/libpangocairo-1.0.so.0 (0xf7141000)
	libgdk_pixbuf-2.0.so.0 => /usr/lib32/libgdk_pixbuf-2.0.so.0 (0xf7128000)
	libm.so.6 => /lib32/libm.so.6 (0xf7101000)
	libcairo.so.2 => /usr/lib32/libcairo.so.2 (0xf704e000)
	libpng12.so.0 => /lib32/libpng12.so.0 (0xf7029000)
	libpango-1.0.so.0 => /usr/lib32/libpango-1.0.so.0 (0xf6fe7000)
	libfreetype.so.6 => /usr/lib32/libfreetype.so.6 (0xf6f70000)
	libfontconfig.so.1 => /usr/lib32/libfontconfig.so.1 (0xf6f3f000)
	libgobject-2.0.so.0 => /usr/lib32/libgobject-2.0.so.0 (0xf6efd000)
	libgmodule-2.0.so.0 => /usr/lib32/libgmodule-2.0.so.0 (0xf6ef9000)
	libgthread-2.0.so.0 => /usr/lib32/libgthread-2.0.so.0 (0xf6ef4000)
	librt.so.1 => /lib32/librt.so.1 (0xf6eeb000)
	libglib-2.0.so.0 => /lib32/libglib-2.0.so.0 (0xf6e1b000)
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf6e02000)
	libc.so.6 => /lib32/libc.so.6 (0xf6ca8000)
	libXext.so.6 => /usr/lib32/libXext.so.6 (0xf6c98000)
	libXrender.so.1 => /usr/lib32/libXrender.so.1 (0xf6c8e000)
	libXinerama.so.1 => /usr/lib32/libXinerama.so.1 (0xf6c89000)
	libXi.so.6 => /usr/lib32/libXi.so.6 (0xf6c7b000)
	libXrandr.so.2 => /usr/lib32/libXrandr.so.2 (0xf6c73000)
	libXcursor.so.1 => /usr/lib32/libXcursor.so.1 (0xf6c69000)
	libX11.so.6 => /usr/lib32/libX11.so.6 (0xf6b4c000)
	libXcomposite.so.1 => /usr/lib32/libXcomposite.so.1 (0xf6b48000)
	libXdamage.so.1 => /usr/lib32/libXdamage.so.1 (0xf6b43000)
	libXfixes.so.3 => /usr/lib32/libXfixes.so.3 (0xf6b3d000)
	libz.so.1 => /usr/lib32/libz.so.1 (0xf6b28000)
	libdl.so.2 => /lib32/libdl.so.2 (0xf6b24000)
	libpcre.so.3 => /lib32/libpcre.so.3 (0xf6aef000)
	libresolv.so.2 => /lib32/libresolv.so.2 (0xf6ada000)
	libselinux.so.1 => /lib32/libselinux.so.1 (0xf6abe000)
	/lib/ld-linux.so.2 (0xf7705000)
	libpixman-1.so.0 => /usr/lib32/libpixman-1.so.0 (0xf6a5e000)
	libxcb-shm.so.0 => /usr/lib32/libxcb-shm.so.0 (0xf6a5a000)
	libxcb-render.so.0 => /usr/lib32/libxcb-render.so.0 (0xf6a52000)
	libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf6a37000)
	libexpat.so.1 => /lib32/libexpat.so.1 (0xf6a10000)
	libXau.so.6 => /usr/lib32/libXau.so.6 (0xf6a0c000)
	libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf6a06000)

```

---

### Post by nolag on 2010-11-18
Great, thanks.  I am wondering though can you do this for gtkmm?  I have a school app I would like to cross compile.

---

