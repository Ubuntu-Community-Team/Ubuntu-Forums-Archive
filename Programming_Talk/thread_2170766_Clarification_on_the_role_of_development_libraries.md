---
title: "Clarification on the role of development libraries and runtime binaries."
date: 2013-08-27
forum: Programming Talk
---

### Post by VforVincent on 2013-08-27
Hi,

I'm dabbling with a project that requires a library that is either pre-installed or that is shipped. Specifically, PySDL2 and SDL2. I'd like to ship the SDL2 library rather than assuming that it is installed. Which got me thinking: how do these things tie in with one another? You've got your source code, which you can configure-make-install, you've got your runtime binaries and you've got your development libraries. How do you from source code to either? Why is it that runtime libraries don't need everything that's in development libraries to run? I understand why libraries exist, but I can't really find anything on the distinction, even though it appears to be an important one.

Thanks,

V.

---

### Post by tgalati4 on 2013-08-27
Development libraries have headers, configuration files, and any support files that the library needs for compilation.  In some cases it may be source code, but usually source code is in a separate package.  Once a library is compiled to binary, it is just a blob with no need for support (or source) files.  As long as the binary blob is on your system, and the correct version, your package will find it and use it.

You can statically compile your code to include all libraries that it needs.  This reduces the need to rely on shared libraries on the target system, but makes your binary blob much bigger than it needs to be.  Because hard disks are so large today, the advantage of saving binary space by sharing libraries is less of an advantage.

---

### Post by VforVincent on 2013-08-27
That's enlightening. Am I getting this correctly if I take your answer to mean that development libraries are primarily useful in the following scenarios?

- you want to statically compile select portions of the library into your own project, rather than including the entire blob
- you want your project to build on different types of machines without having to provide separate binary blobs for, say, x86 and x64

Also, I take it you just set up one way to build the development library in your build file and another for the runtime blob?

---

### Post by tgalati4 on 2013-08-27
Yes to the first use case.  No for the second.  Different architectures require different compilations (switches) and therefore separate binary blobs for each architecture.

You need a specific package and set of libraries to answer your 3rd question.  There are just too many scenarios to make a generalization.  And I don't know anything about your project to make any comment on how to best set up your development environment.

---

