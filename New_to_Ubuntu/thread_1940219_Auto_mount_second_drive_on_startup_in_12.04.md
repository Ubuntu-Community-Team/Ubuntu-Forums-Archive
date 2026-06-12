---
title: "Auto mount second drive on startup in 12.04?"
date: 2012-03-13
forum: New to Ubuntu
---

### Post by kramer65 on 2012-03-13
Hello,


I installed Ubuntu 12.04 alpha2 and installed all updates (which makes it beta1 now I guess). So far everything works pretty smooth.

I now want to auto mount my second (internal) hard drive like I had it working in 10.04. To achieve this I found this wiki-page: [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

I followed the guide all up to where I found the UUID if ny sdb1. It then says that I have to add it to the start up applications. For this it says I need to "*paste in your command*", and this is where I am lost.

What command do I need to paste in here to have my disk mount automatically..?

---

### Post by kramer65 on 2012-03-13
Okay, nevermind again!

I found that I needed to paste the following there: /usr/bin/udisks --mount /dev/disk/by-uuid/1313-F422-etc-etc

---

### Post by Kay The Bantu on 2012-06-12
I know this is "solved" but i thought i'd throw in my two cents worth. And now my two cents worth [http://sourceforge.net/projects/arios/files/repo/arios-automount-1.0_all.deb/download]("http://sourceforge.net/projects/arios/files/repo/arios-automount-1.0_all.deb/download")

It does it automatically

---

