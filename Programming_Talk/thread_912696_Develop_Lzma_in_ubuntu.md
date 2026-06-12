---
title: "Develop Lzma in ubuntu"
date: 2008-09-07
forum: Programming Talk
---

### Post by rustybar on 2008-09-07
Hi

I know this might be a wrong place to post this question. But I hope someone can help.

I'm trying to develop a simple compression program using LZMA algorithm.

LZMA is the default compression/decompression alogrithm used in 7-Zip. Even though it is open source, it lacked in documentations and their forums doesn't seem to help much.

What I'm trying to do is integrate LZMA compression/decompression into a simple program so that it can run in an embedded application using linux. However, even though they have the source code written in c in the latest version of LZMA SDK 4.60 beta, but some files contain windows.h as their header. As such during compilation, a lot of errors were generated for certain files.

Does anyone have experience in dealing with open source file which used windows.h. Is there any way to overcome it?

Please advise.

Thanks!

---

### Post by mssever on 2008-09-07
I've never messed with windows.h, but I think you're making this too difficult. A Linux LZMA program already exists.
```
sudo aptitude install lzma
```

---

### Post by rustybar on 2008-09-07
Thanks for the reply. 

The reason why I have to compile the source files is because I need to integrate the compression/decompression with another program. Thus, I may need to call the function in LZMA in the other program. If by just installling the program, I will have to make a script file to manipulate the program. However, I like to interact with LZMA through its functions instead. 

I downloaded the LZMA SDK 4.60 beta, but unable to compile under ubuntu. Does anyone know how to compile their source files? 

Thanks.

---

### Post by samjh on 2008-09-07
Keep in mind that 7-zip is a Windows program.

p7zip is an implementation for Unix-based systems, including Linux.  It is FOSS, of course. ;)

See here: [http://p7zip.sourceforge.net/](http://p7zip.sourceforge.net/)

---

### Post by Quikee on 2008-09-07
> **rustybar said:**
> Thanks for the reply. 

The reason why I have to compile the source files is because I need to integrate the compression/decompression with another program. Thus, I may need to call the function in LZMA in the other program. If by just installling the program, I will have to make a script file to manipulate the program. However, I like to interact with LZMA through its functions instead. 

I downloaded the LZMA SDK 4.60 beta, but unable to compile under ubuntu. Does anyone know how to compile their source files? 

Thanks.

Then get the source of lzma in ubuntu. You can get the source for every package in Ubuntu by "apt-get source <input-package-name>"

Also in the repository you have lzma-dev which is meant exactly for the use in your own program.

---

### Post by mssever on 2008-09-07
> **Quikee said:**
> Then get the source of lzma in ubuntu. You can get the source for every package in Ubuntu by "apt-get source <input-package-name>"

Also in the repository you have lzma-dev which is meant exactly for the use in your own program.
Yes, that's what I was trying to say, but I didn't say it too clearly. You don't need to mess with a Windows program when a Linux one already exists.

---

