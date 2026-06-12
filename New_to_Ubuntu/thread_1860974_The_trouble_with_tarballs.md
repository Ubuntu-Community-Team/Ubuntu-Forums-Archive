---
title: "The trouble with tarballs"
date: 2011-10-15
forum: New to Ubuntu
---

### Post by JazzPotato on 2011-10-15
Hi there!
 Ive been using linux for quite a while now, and have stuck with ubuntu since my dear friend maverick meerkat. Unfortunately, i've never quite managed to figure out what to do with .tar.bz, .tar.bz2, and the other swathes of tarball files. I have attempted to install drivers and software and the like with compile, make, make install, install, and havn't had much luck. Every time i seem to encounter an error.
 Im hoping a more experienced linux user can clarify things for me,
Regards, and thanks in advance.

---

### Post by haqking on 2011-10-15
> **JazzPotato said:**
> Hi there!
 Ive been using linux for quite a while now, and have stuck with ubuntu since my dear friend maverick meerkat. Unfortunately, i've never quite managed to figure out what to do with .tar.bz, .tar.bz2, and the other swathes of tarball files. I have attempted to install drivers and software and the like with compile, make, make install, install, and havn't had much luck. Every time i seem to encounter an error.
 Im hoping a more experienced linux user can clarify things for me,
Regards, and thanks in advance.


Depends on the error and the contents of the tar to help you specifically.

**First of all always search in the Software Centre or Synaptic to see if software is already in the repos for easy install or from the developers website where a .deb might be available again for easy install (like a .exe in windows)**

If you have to download it as a package it will often come down in a package/archive format such as xxxxx.tar or xxxx.tar.gz etc.

These are analogous to windows .zip files but with varying compression denoted by the .xx after the .tar such as .tar.gz where .gz is the compression. A .tar file means Tape Archive which is legacy from UNIX when things were backed up to tape drives. The 2 or 3 letters after the .tar refer to the type of compression used to pack down the archive.

See here for dealing with these files [https://help.ubuntu.com/community/FileCompression](https://help.ubuntu.com/community/FileCompression)

It is often just a simple case of right clicking in your GUI on the file and choosing extract then it will be unpackaged to a directory.

The contents might simply be a .deb file as i said for easy installation see here:
[http://linux.about.com/od/ubuntu_doc/a/ubudg21t2.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg21t2.htm)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

If the contents is source code then you need to compile this, this is where people often get stumped and is dependant on the developer and the documentation provided, once unpackaged there is often a README text file or a INSTALL file which you should read as it will often contain clear and concise instructions on what to do.

If not then you need to figure it out, see here for information on compiling from source:

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

then you should be set ;-)


Have fun

Regards

haqking

---

### Post by JazzPotato on 2011-10-15
Thank you!
 Finally i should be able to use these!

And thanks for the quick reply :-)

---

### Post by haqking on 2011-10-15
> **JazzPotato said:**
> Thank you!
 Finally i should be able to use these!

And thanks for the quick reply :-)

no worries you are welcome

---

