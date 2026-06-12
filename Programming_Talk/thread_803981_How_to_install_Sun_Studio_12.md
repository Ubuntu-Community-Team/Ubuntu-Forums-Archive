---
title: "How to install Sun Studio 12"
date: 2008-05-22
forum: Programming Talk
---

### Post by fb2007 on 2008-05-22
Can anybody post how to install Sun studio 12 on hardy?


thanks

---

### Post by xlinuks on 2008-05-22
Here's what the download page says:
```

There are two downloads on this page:

    * Sun Studio 12 Tarfile: This file contains an installed image of the Sun Studio 12 software (except for the Sun Performance Library[tm]), which you can extract into your directory of choice. This installation does not require root privileges.

    * System Preparation Tool: This file contains a tool that lets you check your system for the prerequisite software and OS patches, and if you have root privileges, install the missing prerequisites. The file also contains the prerequisite software.

```
If you choose the tar file, after unzipping it you'll find the directory /sunstudio12/bin, there's a file called "sunstudio" - double-clicking it will launch the sunstudio.

---

### Post by drtomc on 2008-05-26
I have an x86_64 box on my desk (core2 duo) running heron and installed from the tar package. When I try to run collect, I get a segfault. Has anyone successfully used collect on a similar platform?

Tom.

---

