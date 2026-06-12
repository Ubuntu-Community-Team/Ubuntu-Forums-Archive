---
title: "md5 hash not agreeing"
date: 2012-09-06
forum: New to Ubuntu
---

### Post by keheikev on 2012-09-06
I downloaded the latest releases today 12.04 LTS but both times I manually md5'd from terminal it returned hashes that are not on Ubunutu's list for amd64 bit.

kevin@kevin-desktop:~/Downloads$ md5sum ubuntu-12.04.1-desktop-amd64.iso
06472ddf11382c8da1f32e9487435c3d  ubuntu-12.04.1-desktop-amd64.iso


The official hash

128f0c16f4734c420b0185a492d92e52

ubuntu-12.04-desktop-amd64.iso

The first time I downloaded it I chalked it up to being two busy on the computer ...multiple things going on but now its kind of frustrating I did open one tab in chrome but that doesnt seem like its enough to foul it up.

:kihei

---

### Post by m_duck on 2012-09-06
Your generated MD5 is the correct one for that ISO. Note the version number, the update has been released, so you have downloaded 12.04.1, whereas that MD5 is for 12.04.

For up to date checksums, see [here]("http://releases.ubuntu.com/12.04.1/MD5SUMS").

---

### Post by vexorian on 2012-09-06
It seems you are comparing with the hash of 12.04 instead of 12.04.1.

A google took me here: [http://releases.ubuntu.com/12.04/MD5SUMS](http://releases.ubuntu.com/12.04/MD5SUMS)

spoiler: Your ISO is fine.

Edit: too late. Oh well.

---

### Post by keheikev on 2012-09-06
Thanks for the information I guess they hadn't updated the page. Always helps to look a little closer at the version.
:kihei

---

