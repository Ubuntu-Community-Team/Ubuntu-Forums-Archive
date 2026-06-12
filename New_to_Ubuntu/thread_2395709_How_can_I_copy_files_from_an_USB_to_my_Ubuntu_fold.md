---
title: "How can I copy files from an USB to my Ubuntu folders"
date: 2018-07-05
forum: New to Ubuntu
---

### Post by 81giamsu on 2018-07-05
Hi everyone, 
I am new to Ubuntu. I have an issue with using Ubuntu supported by Mircosoft Apps Store. I have many files that I want to copy to the Ubuntu. Does anyone help me to load these files to the Ubuntu? I tried with Nautilus but it doesn't work with my Ubuntu. 
Thank you in advanced
Gia Nguyen

---

### Post by Holger_Gehrke on 2018-07-05
What you're running isn't actually Ubuntu, it's a partial Ubuntu userland on top of the Windows Subsystem for Linux, a kind of kernel-level translation system that answers the requests programs make of the Linux Kernel by translating them into calls to the Windows Kernel, similar to the way wine makes it possible to run Windows programs on Linux systems. Since WSL is rather new, there's still a lot of stuff that doesn't work quite right.  Accessing USB and network drives only works in builds of WSL newer than 16176 from April of this year. Details in a [blog-post at msdn]("https://blogs.msdn.microsoft.com/wsl/2017/04/18/file-system-improvements-to-the-windows-subsystem-for-linux/").

Holger

---

### Post by 81giamsu on 2018-07-06
Thank so much! It works!

---

