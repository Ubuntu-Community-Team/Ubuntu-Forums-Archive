---
title: "Generating Dependency List for an Application?"
date: 2007-05-05
forum: Programming Talk
---

### Post by Xangis on 2007-05-05
I'm trying to learn Debian packaging.  I'm working through some of the tutorials, but I have a problem that I need to solve:

I'm unsure what the dependencies of the application I'm building really are.

Is there a tool that I can run against a compiled executable to find out what libraries it requires?

---

### Post by zvacet on 2007-05-05
If you compile program in **read me** file you have list of dependencies you need to install.
If you just download deb file use

```
sudo aptitude install file_name
```

With aptitude you will install program and all dependencies.

---

### Post by winch on 2007-05-05
ldd prints shared library dependencies

```

ldd `which mousepad`
        libxfcegui4.so.4 => /usr/lib/libxfcegui4.so.4 (0x00002b6b6b00f000)
        libstartup-notification-1.so.0 => /usr/lib/libstartup-notification-1.so.0 (0x00002b6b6b265000)
        libSM.so.6 => /usr/lib/libSM.so.6 (0x00002b6b6b46e000)
        libICE.so.6 => /usr/lib/libICE.so.6 (0x00002b6b6b678000)
        libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0x00002b6b6b894000)
        libxfce4util.so.4 => /usr/lib/libxfce4util.so.4 (0x00002b6b6be2f000)
        libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0x00002b6b6c03e000)
        libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0x00002b6b6c2d8000)
        libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0x00002b6b6c4f9000)
        libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0x00002b6b6c711000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0x00002b6b6c91b000)
        libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0x00002b6b6cb2c000)
        libXi.so.6 => /usr/lib/libXi.so.6 (0x00002b6b6cc2e000)
        libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0x00002b6b6ce38000)
        libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0x00002b6b6d03f000)
        libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0x00002b6b6d249000)
        libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0x00002b6b6d44f000)
        libcairo.so.2 => /usr/lib/libcairo.so.2 (0x00002b6b6d694000)
        libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0x00002b6b6d90a000)
        libz.so.1 => /usr/lib/libz.so.1 (0x00002b6b6db84000)
        libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0x00002b6b6dd9a000)
        libpng12.so.0 => /usr/lib/libpng12.so.0 (0x00002b6b6dfce000)
        libXrender.so.1 => /usr/lib/libXrender.so.1 (0x00002b6b6e1f3000)
        libm.so.6 => /lib/libm.so.6 (0x00002b6b6e3fc000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0x00002b6b6e67e000)
        libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0x00002b6b6e98c000)
        libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0x00002b6b6ebce000)
        libdl.so.2 => /lib/libdl.so.2 (0x00002b6b6edd1000)
        libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0x00002b6b6efd6000)
        libc.so.6 => /lib/libc.so.6 (0x00002b6b6f277000)
        libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0x00002b6b6f5c9000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0x00002b6b6f7f7000)
        libexpat.so.1 => /usr/lib/libexpat.so.1 (0x00002b6b6f9fa000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00002b6b6fc1d000)
        /lib64/ld-linux-x86-64.so.2 (0x00002b6b6adf2000)
        libpthread.so.0 => /lib/libpthread.so.0 (0x00002b6b6fe23000)

```

I'm not sure if that is all you need. For instance if the app needs lib-a lib-b and lib-c yet lib-b and lib-c are dependencies of lib-a do you list all three libs as dependencies or just lib-a?

```

 apt-cache depends mousepad
mousepad
  Depends: libatk1.0-0
  Depends: libc6
  Depends: libcairo2
  Depends: libfontconfig1
  Depends: libfreetype6
  Depends: libglib2.0-0
  Depends: libgtk2.0-0
  Depends: libice6
  Depends: libpango1.0-0
  Depends: libpng12-0
  Depends: libsm6
  Depends: libstartup-notification0
  Depends: libx11-6
  Depends: libxcursor1
  Depends: libxext6
  Depends: libxfce4util4
  Depends: libxfcegui4-4
  Depends: libxfixes3
  Depends: libxi6
  Depends: libxinerama1
  Depends: libxrandr2
  Depends: libxrender1
  Depends: zlib1g
  Recommends: xfprint4

```

Quite different from the list above.

---

### Post by reacocard on 2007-05-05
I don't know of any tools, but here's a few tips:

1) Jot down any extra packages you need to compile it the first time. (-dev are build-depends, be sure to put the binary for each -dev in depends.)

2) Look in the documentation, odds are that the README or INSTALLING has at least a partial list of dependencies

3) Look at the imported modules manually. eg., if a python program has 'import pygtk' in it, that tells you a dependency right there. 'cat | grep' is really helpful here.

4) After you've built the deb, use pbuilder to recompile it from the .dsc. If there are any missing dependencies, pbuilder will fail, and the output should tell you what you're missing.

Dependency finding is probably the hardest part of packaging new applications (except for the occasional odd build system). I often spend two or more times as much time tracking down dependencies than I do for everything else when packaging.

---

### Post by Xangis on 2007-05-06
Thank you, that ldd trick is exactly what I was looking for.  Other good info too :)

---

