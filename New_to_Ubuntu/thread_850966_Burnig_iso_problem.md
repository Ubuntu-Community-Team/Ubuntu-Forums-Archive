---
title: "Burnig iso problem"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by rf-pt on 2008-07-06
Hello

I want to use Ubuntu with a laptot LGE500, so here i come...

I have downloded the iso from here...

Download URL: [http://releases.ubuntu.com/hardy/ubuntu-8.04.1-desktop-i386.iso](http://releases.ubuntu.com/hardy/ubuntu-8.04.1-desktop-i386.iso)
Ubuntu Edition: Ubuntu 8.04.1 desktop
Computer Platform: i386
Download Location: [http://releases.ubuntu.com/](http://releases.ubuntu.com/)

I try to burn the image, in 3 cd's, all of them with 80m and 700Mb Intenso, i used nero and other burning tools... 
But no luck i always get an error :(, can't close cd...
i try to verify hash with instruction from here:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

the hash do not match :(.

I have made another download from here:

Download URL: [ftp://glua.ua.pt/ubuntu/hardy/ubuntu-8.04.1-desktop-i386.iso](ftp://glua.ua.pt/ubuntu/hardy/ubuntu-8.04.1-desktop-i386.iso)
Ubuntu Edition: Ubuntu 8.04.1 desktop
Computer Platform: i386
Download Location: [ftp://glua.ua.pt/ubuntu/](ftp://glua.ua.pt/ubuntu/)

Still the hash do not match :(

the same problem... 

Please can someone help me what am i doing wrong?!! do i need a 800Mb cd to burn image?

I'm doing all of this ins the same laptop with windows XP home with Srp 3

Best Regards
RF-PT

---

### Post by sayakb on 2008-07-06
First of all, Welcome to Ubuntu Forums!
I had a similar problem like you. Maybe this post would help:
[http://ubuntuforums.org/showpost.php?p=5023630&postcount=13](http://ubuntuforums.org/showpost.php?p=5023630&postcount=13)

EDIT: Lol.. ugm6hr changed his sig.. I'll post the links shortly :)

EDIT: [http://releases.ubuntu.com/8.04/](http://releases.ubuntu.com/8.04/) <-- You already may have looked here.
Look below and download a .torrent file. Use a bittorrent client like uTorrent or Flashget. Copy the iso to the bittorrent client's download folder and start the torrent download. The client would download only specific bytes and correct the ISO.

---

### Post by drs305 on 2008-07-06
Here are the current hashes/md5sums, taken from [this site]("http://releases.ubuntu.com/8.04.1/MD5SUMS").  Some of the MD5SUM pages didn't have the 8.04.1 info updated when it was initially released.


```
38e3f4d0774a143bd24f1f2e42e80d63 *ubuntu-8.04.1-alternate-amd64.iso
bbd21ded02c06b41c59485266833937a *ubuntu-8.04.1-alternate-i386.iso
b78ef719e3361e726b89bab78c526ad0 *ubuntu-8.04.1-desktop-amd64.iso
c69e34e92d5402d1b87e6babc739f774 *ubuntu-8.04.1-desktop-i386.iso
e7351d79903588699a383ae77854f734 *ubuntu-8.04.1-server-amd64.iso
7232c6004ba438890cd09aded162dc8e *ubuntu-8.04.1-server-i386.iso
```

This is an excellent reference for burning the iso:
[ Downloading and burning an ISO of Ubuntu]("http://www.psychocats.net/ubuntu/iso")

This link has lots of other good info for installing and setting up ubuntu.

---

### Post by rf-pt on 2008-07-06
Hi :)

I manage to do do iso...

thanks for your help...

Best regards

rf-pt

---

