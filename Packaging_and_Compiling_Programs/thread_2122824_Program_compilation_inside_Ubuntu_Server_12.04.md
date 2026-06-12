---
title: "Program compilation inside Ubuntu Server 12.04"
date: 2013-03-06
forum: Packaging and Compiling Programs
---

### Post by tomzie on 2013-03-06
I have c programs running inside SCO 5.0.5 Openserver and have copied it inside Ubuntu Server 12.04 OS. Now, I am faced with library issues. I have copied the newlib folder that the c programs are using. However, when I compile it, I am getting /newlib/libio5.a: could not read symbols: File format not recognized error message. Then I went to the newlib folder and try to re-compile the libraries. When I compile it by executing make, then I get error saying the sys/locking.h: No such file or directory compilation terminated. I don't want to just copy all the files in the sys folder in SCO because this was for the SCO system. I wanted to use what Ubuntu has. In the Ubuntu server, I see that the locking.h file is inside /usr/src/linux-header-3.2.0-38-generic-pae/include/config/file/ and *-pae/include/config/ncpfs/ioctl/ folders. However, both locking.h files are empty. So I don't think this is the correct file to point my programs to. Please help. Thanks.

---

