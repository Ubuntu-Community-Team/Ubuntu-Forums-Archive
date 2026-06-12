---
title: "Download a single file instead of the complete iso"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by asadi on 2008-09-01
I have downloaded ubuntu-8.04.1-desktop-i386. The md5 check sum isn't correct. I have a low speed internet connection and i don't want to downland ubuntu-8.04.1-desktop-i386 completely again. Is there a way to find the incorrect file and download just that file.

---

### Post by ~LoKe on 2008-09-01
No, I don't think it's possible to determine the bad file, and definitely not possible to download part of an iso (unless someone extracted it and uploaded it).

---

### Post by asadi on 2008-09-01
Thank you ~LoKe,
I can extract downloaded iso file with no errors. There is a file named md5sum.txt in the extracted folder and it has the md5 of all files in the iso. I can check the md5 of every single file, but how can i download that file if it is corrupted.

---

### Post by dRock1286 on 2008-09-01
You can always google it to see if it anyone else has had problems with it and see if it is uploaded somewhere...

---

### Post by fidamehran on 2008-09-02
You can order a CD from shipit.ubuntu.com which takes about 4 weeks to come. That's a sure way to get a good CD.
Moreover, you can download Wubi ([wubi-installer.org]("http://wubi-installer.org")) and use it to download and install the latest Ubuntu. That way you should not get corrupted download, despite slow internet connection.
Moreoverm you can use Torrent downloads to get a full proof errorless download.

---

### Post by Perfect Storm on 2008-09-02
I recommend using torrent next time, it's godsend when on low-connection and you won't end up with a bad file.

---

### Post by asadi on 2008-09-02
Thanks for your reply.
I checked installation files. The corrupted file was "./casper/filesystem.squashfs" and it is about 669 MB. It is not a good choice to download this file instead of ISO package!

---

### Post by gn2 on 2008-09-02
If you extract the contents of a downloaded .iso of a Linux distro you run the risk of corrupting the image.

Burn the .iso as an image using Imgburn or similar.
I only check the md5 if the burned CD doesn't work.

There are other methods of getting CD's if you don't want to download it, they are available cheap on Ebay, or you can get one free from [**Shipit**]("https://shipit.ubuntu.com/")

---

