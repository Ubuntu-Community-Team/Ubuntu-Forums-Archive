---
title: "adobe shockwave player"
date: 2012-12-27
forum: New to Ubuntu
---

### Post by twinkies on 2012-12-27
Hello! I wanted to play assult coarse on miniclip but i cant because i dont have Adobe Shockwave Player and it wont let me download it. Pls help!!!

---

### Post by iMac71 on 2012-12-27
There isn't a shockwave plugin for linux; you should install wine and then install in it shockwave for windows.
Alternatively, you should:
1) install VirtualBox,
2) create a virtual machine running Windows or Apple OS (*),
3) install in it the corresponding version of shockwave plugin.

(*)even if VirtualBox seems to require a server edition of Apple OS, you can install the client one without any problem.

---

### Post by twinkies on 2012-12-27
thx i will try that

---

### Post by twinkies on 2012-12-28
I tried installing shockwave player then puting it on wine, then it said it coudnt write it.

---

### Post by iMac71 on 2012-12-28
The following thread might be useful for your problem:
[http://ubuntuforums.org/showthread.php?t=1867345&highlight=shockwave](http://ubuntuforums.org/showthread.php?t=1867345&highlight=shockwave)

---

### Post by twinkies on 2012-12-28
> **iMac71 said:**
> The following thread might be useful for your problem:
[http://ubuntuforums.org/showthread.php?t=1867345&highlight=shockwave](http://ubuntuforums.org/showthread.php?t=1867345&highlight=shockwave)

I followed the link and did what it said, but whenever I tried to play it gets a blank white screen.

---

### Post by iMac71 on 2012-12-28
If wine doesn't solve at all your problem, you might try to install VirtualBox and create a virtual machine running Windows or Apple OS.

---

### Post by twinkies on 2012-12-28
> **iMac71 said:**
> If wine doesn't solve at all your problem, you might try to install VirtualBox and create a virtual machine running Windows or Apple OS.

I tried both but said that I had 16RAM for the video card and to change that, but there was no option to change the RAM for the video card.

---

### Post by iMac71 on 2012-12-29
You might then try playonlinux```
sudo apt-get install -y playonlinux
```

---

