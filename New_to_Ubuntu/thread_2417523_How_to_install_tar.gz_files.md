---
title: "How to install tar.gz files"
date: 2019-04-23
forum: New to Ubuntu
---

### Post by redus on 2019-04-23
Hey all I've been having a ton of trouble installing anything on Linux. I know I need to pick the tar.gz files, but beyond that I've no idea what to do. Where do I look in those folders to actually install things? I know I can install stuff through the terminal, but what am I looking for in the tar.gz folders that tells me what to type in the terminal? Thank you very much!!

---

### Post by Impavidus on 2019-04-24
Installing stuff from .tar.gz files (also known as tarballs) is considered a last resort in Linux. Only do it if there's really no other way. In order of preference (more or less):
1: From the official Ubuntu repositories;
2: From third-party repositories (PPAs);
3: Stand-alone packages, handled through the package manager (I think the new snap packages are better in this case than the traditional deb packages as they don't suffer from dependency hell);
4: Tarballs not requiring anything more than unpacking in a specific location (like pre-compiled executables, ready-to-use themes etc.);
5: Tarballs with source code.

There are no rules for tarballs. With a bit of luck, there's a readme file or an install file with instructions. If not and you're new to Ubuntu, don't try unless your computer is unusable otherwise. 98% of the software I use is from the official repositories.

What kind of stuff do you want to install? Programs, themes, drivers, libraries, extensions to already installed programs?

---

### Post by monkeybrain20122 on 2019-04-24
What software is that? A tar.gz file is an archive exactly like a .zip file, so it really depends on what is in the tarball. If it is a binary (already compiled) then basically you just click the executable to use it, no installation needed (e.g if you download Firefox for Linux from Mozilla) If it is source code then you need to first compile it, and is not recommended for beginners. Chances are you can find the software in the repo or a PPA (third party repo that you can add to your software sources)

---

### Post by him610 on 2019-04-25
Hey monkeybrain20122,

If you insist on ignoring perfectly good advice from a *buntu cognizant individual then review these....
```

man tar
man gzip
man gunzip

```
That should provide you with enough information to complete the task at hand with your chosen method.

---

### Post by SeijiSensei on 2019-04-25
90% or more of the software you would ever want is in the Ubuntu repositories.  I haven't installed a package from a tarball in years except for WordPress.  It's been even longer since I built a package by compiling from source code.  Use the Ubuntu Software Center that came with your copy of Ubuntu.

---

### Post by redus on 2019-04-25
> **Impavidus said:**
>  What kind of stuff do you want to install? Programs, themes, drivers, libraries, extensions to already installed programs?

So I'm trying to install TeX Live. I need it to run LaTeX. I've already got TeXMaker, just need TeX Live.

---

### Post by redus on 2019-04-25
> **SeijiSensei said:**
> Use the Ubuntu Software Center that came with your copy of Ubuntu.
 
Yeah I just did this and downloaded something slightly different. Hopefully it all works. Thank you!!

---

### Post by oldrocker99 on 2019-04-25
I have used, for about 7 years, the gapless music player Aqualung, to do a radio show.. It disappeared from the repos, the PPA was not updated, and the tar.gz was my only solution. I had to compile it, which took me longer the first time I did it, and shorter once I did it a second time.

Compilation is not all that hard to do, and you have a program customized for your machine. This is not the place for instructions on source code compilation, but here's a start:[http://webhotel4.ruc.dk/~keld/teaching/CAN_e14/Readings/How%20to%20Compile%20and%20Run%20a%20C%20Program%20on%20Ubuntu%20Linux.pdf](http://webhotel4.ruc.dk/~keld/teaching/CAN_e14/Readings/How%20to%20Compile%20and%20Run%20a%20C%20Program%20on%20Ubuntu%20Linux.pdf)

---

### Post by TheFu on 2019-04-25
> **redus said:**
> Hey all I've been having a ton of trouble installing anything on Linux. I know I need to pick the tar.gz files, but beyond that I've no idea what to do. Where do I look in those folders to actually install things? I know I can install stuff through the terminal, but what am I looking for in the tar.gz folders that tells me what to type in the terminal? Thank you very much!!

If you aren't aware, almost all Ubuntu software has been pre-packaged and is available for installation by a "package manager." You don't manually download anything. The package manager handles that, validates the package using cryptographic keys used to sign each package, installs it, adds the manual pages to your system and modifies the menus to include the new software.  Linux systems have been handling software installation in this way for well over 20 yrs. 

tgz or tar.gz files are normally used for alpha software that the team hasn't gotten approved to be included in a distro yet. Gunzip the file, then de-tar it. Inside the directory either at this level or 1 level deeper, there should be a README and/or INSTALL file which explains how to install the program.  There are thousands of different possible answers for how to build and install any of these tgz files. It completely depends on what the development team used in the project.  tgz is like ZIP. It can hold anything.

---

