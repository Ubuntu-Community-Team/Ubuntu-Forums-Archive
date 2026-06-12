---
title: "How to install 32 bit package in 12.04 64bit"
date: 2015-08-21
forum: New to Ubuntu
---

### Post by karthik24 on 2015-08-21
Hi friends,
I'm trying to install 32 bit architecture to install 32 bit softwares too in my Ubuntu 12.04.1 64bit. I tried [http://ftp.debian.org/debian/pool/main/i/ia32-libs/ia32-libs_20140630_amd64.deb](http://ftp.debian.org/debian/pool/main/i/ia32-libs/ia32-libs_20140630_amd64.deb) dependency not satisfiable and used the command sudo apt-get install ia32-libs, Got the error no packages found. 
Tried to force installation using sudo dpkg --force-architecture -i programname.deb, got the error as below:

dpkg: dependency problems prevent configuration of aabm:i386:
aabm:i386 depends on dkms.
dpkg: error processing aabm:i386 (-install):
dependency problems - leaving unconfigured
Errors were encountered while processing:
aabm:i386
Is there anyway to install 32 bit software in my 12.04 64 bit Ubuntu.
Please advice.

---

### Post by monkeybrain20122 on 2015-08-21
You have to install the i386 packages separately. Which 32 bit program you try to install?

---

### Post by grahammechanical on 2015-08-22
I think that I am correct in saying that since the release of 12.04 Ubuntu has multi-arch libraries and ia32-libs is no longer available because it has been replaced. No, I was wrong, the switch to multi-arch began with 11.10.

[https://help.ubuntu.com/community/MultiArch](https://help.ubuntu.com/community/MultiArch)


[http://askubuntu.com/questions/107230/what-happened-to-the-ia32-libs-package](http://askubuntu.com/questions/107230/what-happened-to-the-ia32-libs-package)

Regards.

---

### Post by karthik24 on 2015-08-23
I'm trying to install my office utility software.

---

### Post by karthik24 on 2015-08-31
I tried a lot, but nothing work out. Please let me the command or link to download i386 packages.

---

### Post by v3.xx on 2015-08-31
> **karthik24 said:**
> I'm trying to install my office utility software.
Name of software please.

---

### Post by karthik24 on 2015-08-31
> **monkeybrain20122 said:**
> You have to install the i386 packages separately. Which 32 bit program you try to install?

I tried a lot, but nothing work out. Please let me the command or link to download i386 packages.

---

### Post by karthik24 on 2015-08-31
> **v3.xx said:**
> Name of software please.

It is an internal software LAP made for mailing purpose to our clients made by internal company developers some years back. It is able to install on one of my friend's Ubuntu 12.04 64bit. Others are using on Windows computer. But I do not want to switch to Windows as Ubuntu is more secured.

---

### Post by sandyd on 2015-08-31
Hi, please run the following and post the output
```

dpkg -I *path/to/deb* |grep -i 'Depends\|Recommends\|Suggests\|Conflicts\|Breaks\|Replaces'
```

The '-I' is a capital i. Please replace *path/to/deb* with the path to the package. The command will show the necessary requirements of the package.

Thanks.

---

