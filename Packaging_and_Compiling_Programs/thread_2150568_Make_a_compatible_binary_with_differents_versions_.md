---
title: "Make a compatible binary with differents versions of Ubuntu"
date: 2013-06-01
forum: Packaging and Compiling Programs
---

### Post by shingosan on 2013-06-01
Hi, I'm a beginner developer but also a beginner in the Linux environment. I'm working on ArchLinux which allows me to have the latest versions of software and the latest versions of libraries. I am currently developing a game for Linux and a beta version is available. I tested the binary on the latest version of Ubuntu, it works very well. However, it does not run on the old version that has glibc 2.15. Less than compile this version of Ubuntu, I do not know how to make my game supports

I tried to dynamically linker to glibc 2.15 when compiling. It worked once for the i386 version, and since I am unable to make the game compatible with Ubuntu 12. In contrast, the amd64 version starts without any error. I spent a whole day on this problem, and I'd ask on the forum to see if there is not an easy way to make it compatible with my game the old version of Ubuntu.

I would think that users will update their systems to Ubuntu 13, but from what I understand, the updates are not simple. So some users are reluctant to update and therefore prefer to keep Ubuntu 12.

Could you tell me the right path to take? thank you

---

### Post by ronnyroll on 2013-06-08
> **shingosan said:**
> I tried to dynamically linker to glibc 2.15 when compiling. It worked once for the i386 version, and since I am unable to make the game compatible with Ubuntu 12.

I would think that users will update their systems to Ubuntu 13, but from what I understand, the updates are not simple. So some users are reluctant to update and therefore prefer to keep Ubuntu 12.
updating to ubuntu 13 would be best to do.

---

### Post by T.J. on 2013-06-09
Please forgive me if I am mistaken, but I'm taking a leap and making an assumption here from the text. It sounds like you are trying to run a newer binary, compiled on a more recent GLIBC, using an older version of GLIBC - on an older Ubuntu.  

While program binaries are typically backwards compatible (meaning that compiled on an older GLIBC they will probably work on a newer version) they are never forwards compatible (compiled against a newer version to run on an older GLIBC).  The library you compile the code against becomes the minimum version that you need to have.  This applies to all operating systems and languages, not just Linux or C/C++.  You can't compile something against  Microsoft C++ 2008 and expect it to run with a 2005 library, for example.   The same goes for interpreted or byte compiled languages such as C#, Perl, Python, or Java (in varying degrees).

You're best fit for compatibility would be: 

1. Release the code under a copyleft license - but that doesn't work for everyone.  
This may not work if you are working with proprietary materials, or be desireable in every instance, but it does have the advantage of getting others to help you fix problems.

2. compile packages against each major version of Linux that you intend to ship for.   
Making an individual package for each Linux is timeconsuming, but you guarantee ease of install.

3. Compile the code against the oldest version you intend to support and then test that binary on each version released after.  So if you were going to support 12.04 and up - compile it on 12.04 and then test the binaries against 12.10 and 13.04.
This is probably the practical option, but if you are using Debian style packaging you may want to test it very carefully for version conflicts in the package installer.  If you make a deb file for 12.04, you want to test it on each Ubuntu as well. 

If I can help or clarify anthing more, just let me know, I'd be happy to assist you.

Hope that helps and best wishes!:D

---

