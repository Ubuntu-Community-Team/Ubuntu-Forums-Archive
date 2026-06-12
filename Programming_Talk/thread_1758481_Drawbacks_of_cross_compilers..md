---
title: "Drawbacks of cross compilers."
date: 2011-05-14
forum: Programming Talk
---

### Post by cgroza on 2011-05-14
Hello, I may need in the future to compile my C++ project for Windows and Linux.

What would be the drawbacks of this practice?

I am talking about generated code efficiency, library support, distribution.

Any oppinions?

---

### Post by JupiterV2 on 2011-05-14
Well I've had to "cross-compile" my C program for distribution across multiple platforms. By that I mean, for Linux and Windows. The application was written, I thought, with portability in mind but that portability only really extended to the Linux/Unix universe. Considerations I had to take:

1. Portable Code: If your program uses "non-pure C++", that is, POSIX extensions or other non-specification conforming code, you're going to run into issues. Using a cross-platform library like Glib will help but you'll still probably need to write some OS specific code for each platform.

2. Portable Libraries: I used GTK+ and SQLite libraries which are "portable." That is to say, their sources are portable but distributing their libraries may be more problematic. You will need to, in the case of GTK+, either require your users to download and install the runtime libraries separately, bundle the runtime installer with your own installer, or create (as I did, based on how pidgin IM does it) your own custom GTK+ package to distribute with your installers. In the case of SQLite, I had to build the DLL myself and distribute it with my binary. Make sure you obey all the rules dictated by the GPL/LGPL when using open source technology!

3. Installers: You'll need to create separate ones for each platform. 99.9% of Windows users will NOT know how to compile from source, unless that's not your target audience. =)

4. Testing: If you don't have access to a computer with the target OS you're looking for, you're either going to need to rely on users providing you feedback on why something doesn't work as intended or, if you're developing on Linux and cross-compiling for Windows, you'll need something like WINE installed.

To answer your question, more directly I mean, you will need to bare in mind that you will need a COMPLETE set of cross-compilation tools for building non-host specific binaries. You'll either need to build a complete cross-compile toolchain or use mingw (my recommendation). Additionally, you'll have to cross-compile any libraries you need to build against too. I found it much easier, and straight-forward, to simply use a Windows box and install msys/mingw. I refer you back to point 4 for additional issues where having access to the target platform comes in handy.

Does this answer your question?

Oh, and using the GNU autotools is almost a requirement IMO. There are some tricks to work out there too when cross-compiling.

If you want a WORA (Write Once, Run Anywhere) situation, use Java. Or Python maybe, if you don't mind your users having to manually install the Python platform themselves, if they don't already have it.

---

### Post by cgroza on 2011-05-15
> **JupiterV2 said:**
> Well I've had to "cross-compile" my C program for distribution across multiple platforms. By that I mean, for Linux and Windows. The application was written, I thought, with portability in mind but that portability only really extended to the Linux/Unix universe. Considerations I had to take:

1. Portable Code: If your program uses "non-pure C++", that is, POSIX extensions or other non-specification conforming code, you're going to run into issues. Using a cross-platform library like Glib will help but you'll still probably need to write some OS specific code for each platform.

2. Portable Libraries: I used GTK+ and SQLite libraries which are "portable." That is to say, their sources are portable but distributing their libraries may be more problematic. You will need to, in the case of GTK+, either require your users to download and install the runtime libraries separately, bundle the runtime installer with your own installer, or create (as I did, based on how pidgin IM does it) your own custom GTK+ package to distribute with your installers. In the case of SQLite, I had to build the DLL myself and distribute it with my binary. Make sure you obey all the rules dictated by the GPL/LGPL when using open source technology!

3. Installers: You'll need to create separate ones for each platform. 99.9% of Windows users will NOT know how to compile from source, unless that's not your target audience. =)

4. Testing: If you don't have access to a computer with the target OS you're looking for, you're either going to need to rely on users providing you feedback on why something doesn't work as intended or, if you're developing on Linux and cross-compiling for Windows, you'll need something like WINE installed.

To answer your question, more directly I mean, you will need to bare in mind that you will need a COMPLETE set of cross-compilation tools for building non-host specific binaries. You'll either need to build a complete cross-compile toolchain or use mingw (my recommendation). Additionally, you'll have to cross-compile any libraries you need to build against too. I found it much easier, and straight-forward, to simply use a Windows box and install msys/mingw. I refer you back to point 4 for additional issues where having access to the target platform comes in handy.

Does this answer your question?

Oh, and using the GNU autotools is almost a requirement IMO. There are some tricks to work out there too when cross-compiling.

If you want a WORA (Write Once, Run Anywhere) situation, use Java. Or Python maybe, if you don't mind your users having to manually install the Python platform themselves, if they don't already have it.

Ok, that was all I needed to know. Your post was very helpful. Thank you Jupiter.

---

