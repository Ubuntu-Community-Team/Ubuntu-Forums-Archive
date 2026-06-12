---
title: "self-compilation of procps on Ubuntu 64-bit"
date: 2013-07-16
forum: Packaging and Compiling Programs
---

### Post by unknown spirit on 2013-07-16
First of all I send greetings to all members of the forum, in particular to all readers of my thread.
I am currently dealing with a strange compilation issue on Kubuntu  12.04.02 64BE concerning the source code of procps, which is actually  written in C, but I suspect certain forum members to handle that language. 
Being part of procps, my KDE plasmoid uses top as a frontend, and as I  wish to enhance functionality I downloaded the latest release, changed  it in my favour and compiled it successfully on both processor  architectures. However, on the 64-bit edition, the original program as  well as the modified version do not behave as expected. Some variables  of the central struct called "proc_t" are corrupted. Weirdly enough, the  installed Ubuntu binaries work flawlessly, so I suppose there are two  possible scenarios: 

The ubuntu developers/packagers used a different source code (I couldn't  find the code in question, the code of packages.ubuntu.com is identical) or I don't get my compiler to work properly  (incorrect padding), although I considered the hints in the provided  README file. 

You can download and view the code here: [http://procps.sourceforge.net/](http://procps.sourceforge.net/)
I'd appreciate compiling tips or compilation attempts (extract, change  directory and type "make") on other 64-bit linux systems. Please note  that some hidden errors may only get visible after a change in standard  top settings.

Thanks for your help in advance,
unknown_spirit

---

### Post by steeldriver on 2013-07-16
How did you determine that "the code of packages.ubuntu.com is identical"? instead of using the tar.gz that you downloaded, have you tried enabling deb-src repositories and then just doing

```
apt-get source procps
```

- that should get you the exact source as used to build the version for your platform - it appears to apply quite a lot of patches relative to the original 3.2.8

---

### Post by unknown spirit on 2013-07-16
You are right, I only compared the original file, not the one containing the patches. I wonder how to integrate those in my program though, never done that before.
That'd mean I gotta recompile procps for every linux distribution available, right?
I hope I'll get it done somehow.

---

### Post by oldos2er on 2013-07-16
Moved to Packaging & Compiling Programs.

---

