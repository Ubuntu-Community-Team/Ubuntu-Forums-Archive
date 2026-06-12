---
title: "Adding a directory to the sources lists"
date: 2005-02-23
forum: Repositories &amp; Backports
---

### Post by qa1433 on 2005-02-23
Hi all,
I am sure that this question has been asked before. However, I have searched the forum to no avail.

My question is how to add a file folder to the source list?
The file path in question is:
/home/qa1433/downloads

Is it possible to add a directory to the source file?

Thanks you in advance for your any help you provide,
paul

---

### Post by leviatan on 2005-02-24
Hi,

cd /home/qa1433
dpkg-scanpackages downloads | gzip > downloads/Packages.gz

Add the following line in /etc/apt/sources.list:
        deb file:/home/qa1433 downloads/

apt-get update

Look here for details:
              [http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-dpkg-scanpackages](http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-dpkg-scanpackages)

Regards,

leviatan

---

### Post by leviatan on 2005-02-24
Sorry, override file is mandatory:

dpkg-scanpackages downloads /dev/null | gzip > downloads/Packages.gz

Regrds,

leviatan

---

### Post by qa1433 on 2005-02-27
leviatan,
Thanks for the info and fix. 
paul

---

