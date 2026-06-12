---
title: "md5 check?"
date: 2012-10-16
forum: New to Ubuntu
---

### Post by Yezinki on 2012-10-16
Is it possible to check md5 checksum of iso image on a drive or on a bootable media?

Thanks.

---

### Post by drmrgd on 2012-10-16
Sure.  If you can access the file, you can run md5sum on it.  Be aware, though, that it should be the .iso image and not bootable media made from the .iso image.

---

### Post by Lars Noodén on 2012-10-16
Yes, the utility k3b, if you have it, will to a checksum when opening the image beforey you start the burn.  Or you can do one manually with [md5sum](http://manpages.ubuntu.com/manpages/precise/en/man1/md5sum.1.html)

```

md5sum lubuntu-12.04-desktop-amd64.iso

```

---

### Post by Yezinki on 2012-10-16
> **drmrgd said:**
> Sure.  If you can access the file, you can run md5sum on it.  Be aware, though, that it should be the .iso image and not bootable media made from the .iso image.

Thanks drmrgd & Lars Noodén,

If I can't access the file can I run WinMD5 ([http://www.winmd5.com/](http://www.winmd5.com/))

on the .iso image on W7?

---

### Post by Yezinki on 2012-10-16
The reason for asking is that is that my OS i.e Ubuntu is running fine, just want to be sure that the downloaded file was correct since I accidently deleted it.

Now I have only the .iso image or the bootable media...

Thanks again.

---

### Post by Lars Noodén on 2012-10-16
Also, if you download using a torrent, the torrent client will automatically checksum the file for you.

---

### Post by Yezinki on 2012-10-16
What's the md5 for Ubuntu 12.04?

Thanks.

---

### Post by Lars Noodén on 2012-10-16
> **Yezinki said:**
> What's the md5 for Ubuntu 12.04?

Thanks.

Which variants of 12.04?

[http://ftp.funet.fi/pub/Linux/INSTALL/Ubuntu/dvd-releases/releases/12.04/release/MD5SUMS](http://ftp.funet.fi/pub/Linux/INSTALL/Ubuntu/dvd-releases/releases/12.04/release/MD5SUMS)

---

### Post by drmrgd on 2012-10-16
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Yezinki on 2012-10-16
Thanks, this one. 

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

Ubuntu 12.04.1 LTS 32 bit

[http://www.ubuntu.com/download/help/install-ubuntu-desktop](http://www.ubuntu.com/download/help/install-ubuntu-desktop)

---

### Post by Lars Noodén on 2012-10-16
> **Yezinki said:**
> Thanks, this one. 

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

Ubuntu 12.04.1 LTS 32 bit

[http://www.ubuntu.com/download/help/install-ubuntu-desktop](http://www.ubuntu.com/download/help/install-ubuntu-desktop)

It looks to be the one at the bottom of the list:
[http://ftp.funet.fi/pub/Linux/INSTALL/Ubuntu/dvd-releases/releases/12.04.1/release/MD5SUMS](http://ftp.funet.fi/pub/Linux/INSTALL/Ubuntu/dvd-releases/releases/12.04.1/release/MD5SUMS)

The md5 file was found here, at the top of the list:
[http://ftp.funet.fi/pub/Linux/INSTALL/Ubuntu/dvd-releases/releases/12.04.1/release/](http://ftp.funet.fi/pub/Linux/INSTALL/Ubuntu/dvd-releases/releases/12.04.1/release/)

---

