---
title: "Getting software?"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by danny138 on 2008-11-21
Hello All, I'm a new person to Linux Ubuntu and think it is good for the most part. Someone told me to not worry about tar files, just use deb and search the repository for what you need. This works but I always come to a tar file and then I get stuck. I used Ubuntu briefly before but dropped it eventually due to this problem. I try to follow tutorials but have no success. I'm a MS user and it just doesn't make sense to me. All attempts to install give errors of no such file or directory. If anyone can help me to break this down to a workable solution it would be good. I know that I will stay with Ubuntu for life if I can overcome this, Thanks in advance.

---

### Post by taurus on 2008-11-21
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by pdwerryhouse on 2008-11-21
It would help to know what it is you're trying to install. Ubuntu's repository is quite big, so most popular free software can be installed from debs.

Typically, if you have to install a program with tar, then it contains the source code, and you'll need to compile it. If the developer has used autotools to build it, then the installation process might be as simple as unpacking, running configure, then make:

```
tar xzf programname-x.y.z.tar.gz
cd programname-x.y.z
./configure --prefix=/usr/local
make
sudo make install
```

No guarantee though, it might be written differently. Check the README or INSTALL file inside the tar archive. You also have to make sure that you have all the dependencies, so it really does pay to read the instructions that come with the program.

If the tar archive is a binary archive, then just unpack it wherever you want it installed:

```
cd /usr/local
sudo tar xf /path/to/binary-tarball.tar
```

---

