---
title: "standalone linux app problems"
date: 2013-06-01
forum: Programming Talk
---

### Post by thedardanius on 2013-06-01
hey, I created a C openGL glx application. I need to link to libx11. so and other standard libs. Im little worried about the linker: I typed ./libcustom to link to custom lib in working directory. -l libX11 to link to x11, but I tested the app on another Ubuntu. It failed to open shared object libx11.so.6??? I thought libx was standard for Linux? So I really don't know how to robustly link with standalone applications on Linux. I do not want the user to install the libs (I don't even know how to code an installer). I know, my machine is x86, the other Ubuntu was x86_64, so a 32bit app linking to a 64 bit lib. Shouldn't be a problem? Do I need to provide 2 different executable, one for 32 bit and one for 64 bit, with the dependancies provided by me? I want to keep the distribution package as small as possible.

---

### Post by Bachstelze on 2013-06-01
You need to install specific packages if you want to run 32-bit executables on 64-bit systems. The standard practice is to provide two executables (one for 32-bit and one for 64-bit).

---

### Post by nvteighen on 2013-06-01
Not sure on how Ubuntu manages multiarch, but in Debian we are able to mix 64-bits and 32-bits by adding an architecture to dpkg:

```

# dpkg --add-architecture i386
# apt-get update

```

You may have to install the Ubuntu-equivalent of the Debian ia32-libs package, and then the relevant 32-bits versions of the libraries you need.

---

### Post by thedardanius on 2013-06-02
so I need to create 32bit and 64 bit of app? But I run a 32 bit OS. How do I compile for 64 bit? And I though 32 bit could run on 64bit without problems?

---

### Post by Bachstelze on 2013-06-02
> **thedardanius said:**
> so I need to create 32bit and 64 bit of app? But I run a 32 bit OS. How do I compile for 64 bit?

You could cross-compile, but it's a pain. You really can't get your hands on a 64-bit machine?

> And I though 32 bit could run on 64bit without problems?

It can, once you have installed the necessary packages.

---

### Post by thedardanius on 2013-06-04
So for 32 bit and 64 bit you have separate libs? Uhm, should I provide themselves in my package I distribute?

---

