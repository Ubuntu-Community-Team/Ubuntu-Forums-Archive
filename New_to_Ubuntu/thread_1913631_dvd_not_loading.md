---
title: "dvd not loading"
date: 2012-01-22
forum: New to Ubuntu
---

### Post by cadmos on 2012-01-22
New to ubuntu  I tried to load a dvd into my laptop and it is not load. I have tried different dvd but still it does not work. It worked yesterday.

---

### Post by uRock on 2012-01-22
Hello and welcome to the forums.

Are you trying to use and ubuntu LiveDVD or are you trying to play a movie DVD?

If you are trying to play a movie DVD, then you will need to install a package for decrypting the DVD. To install the package you will need to copy and paste the proper command for the version of ubuntu you installed into a terminal.

**[COLOR="Red"]32bit[/COLOR]** ```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb && sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb
```

**[COLOR="Red"]64bit[/COLOR]** ```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb && sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_amd64.deb
```

---

### Post by cadmos on 2012-01-22
Trying to watch a movie. Thanks it worked. Just don't understand why it quick working. Watched a movie yesterday. But at least it is working again. Once again thank you

---

### Post by uRock on 2012-01-22
> **cadmos said:**
> Trying to watch a movie. Thanks it worked. Just don't understand why it quick working. Watched a movie yesterday. But at least it is working again. Once again thank you

Most, but not all, DVDs are encrypted. I am glad this worked for you.

Welcome and enjoy!:D

---

