---
title: "How do I get new c++ libraries working?"
date: 2009-01-17
forum: Programming Talk
---

### Post by pederka66 on 2009-01-17
How do I get new c++ libraries working in linux? To make this question a bit less general, my current problem is getting the linear algebra package lapack++ to work.

I have followed the instructions on how to install the package, but now I sit here with a folder full of header-files, how do I "add" them to the rest of the lib's so I can #include them regardless of their path on my computer?

---

### Post by stroyan on 2009-01-17
There is no config file for g++ include paths.  You could install the libpack++ header files in /usr/include or you could use one of the -I or -i* options to g++ to add the directory where you put the header files.

---

### Post by JupiterV2 on 2009-01-17
I am not specifically familiar with the package you are using but generally there a few things you may need to do, depending how you installed the new libraries.

If you installed them from source manually you may need to run ldconfig to refresh the linker's config so it can find the new libraries. 

As for the headers, or if you installed from repos. or a deb package, you may need to use pkg-config or the -I flag to gcc to locate the headers/libraries. I recommend looking at the documentation for the library to see how they recommend linking their libraries and accessing their headers at compile time.

---

