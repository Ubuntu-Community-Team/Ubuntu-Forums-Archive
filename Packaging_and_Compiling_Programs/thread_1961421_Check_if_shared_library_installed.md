---
title: "Check if shared library installed"
date: 2012-04-19
forum: Packaging and Compiling Programs
---

### Post by schander on 2012-04-19
Hi all,
We have several products in our range and they all rely on a common shared library. Therefore what we have done is generate driver debs for each product that have 2 shared libraries, a common one and one for the product.
The problem is that when a user tries to install drivers for more than one product an error in generated:
```
dpkg: error processing Driver2_1.0-1_i386.deb (--install):
trying to overwrite '/usr/lib/common-1.0.la', which is also in package Driver1 1.0-1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)

```

[LIST]
[*]Is there anyway to check if the common shared library is already available and not install it?
[*]Or should we just have a seperate deb package for the common shared library?
[LIST]
[*] Is there anyway that my driver deb package could install the seperate common deb package if it's in the current directory?
[/LIST]
[/LIST]

Thanks
Satpal

---

### Post by bregma on 2012-04-19
> **schander said:**
> Hi all,
We have several products in our range and they all rely on a common shared library. Therefore what we have done is generate driver debs for each product that have 2 shared libraries, a common one and one for the product.


Er, no.

You should have a package for each product, and a separate package for the common library.  In your *debian/control* file for each product package, list the separate library package in the [FONT="Courier New"]Depends:[/FONT] field.  **apt** will make sure the required dependencies are installed.

In fact, once you package the library and build your product packages against the library package, the standard packaging tools should normally detect that dependency automatically (that's what the dh_shlibdeps tool does).

---

