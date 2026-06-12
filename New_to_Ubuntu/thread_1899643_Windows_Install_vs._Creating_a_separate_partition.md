---
title: "Windows Install vs. Creating a separate partition"
date: 2011-12-24
forum: New to Ubuntu
---

### Post by Justin534 on 2011-12-24
Whats the difference between doing a windows install and creating a separate partition for Ubuntu. If I create a separate partition would Ubuntu run faster?

[Edit]Ok, now I'm a bit confused. I was reading a bit about Wubi... is Ubuntu actually running on top of windows?

---

### Post by BC59 on 2011-12-24
Yes it's something like this:
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Normal against Wubi installation is far better.

---

### Post by mcduck on 2011-12-24
> **Justin534 said:**
> Whats the difference between doing a windows install and creating a separate partition for Ubuntu. If I create a separate partition would Ubuntu run faster?

[Edit]Ok, now I'm a bit confused. I was reading a bit about Wubi... is Ubuntu actually running on top of windows?

Wubi install doesn't run on top of Windows, it's just that it's filesystem is inside the Windows filesystem which means that all disk reads and writes are a bit more complicated. This results in slighlty lower performance than on a normal install, but it's hardly noticeable in most normal use cases.

However the big difference is the extra robustness you get from a normal install. If the windows filesystem has any problems, your Wubi install will fail together with it. A normal install on the other hand is completely separated from Windows, so it's much less likely to break (and you'll also have more options regards partitioning, upgrades etc.)

I wouldn't really recommend using Wubi as a permanent Ubuntu install, only for testing purposes if you aren't sure if you want Ubuntu or not and wish to test drive it without changing your partitions. In the long run it's better idea to make a proper install instead.

---

### Post by amjjawad on 2011-12-24
> **Justin534 said:**
> [Edit]Ok, now I'm a bit confused. I was reading a bit about Wubi... is Ubuntu actually running on top of windows?

Hi,

I prefer to avoid Wubi: [http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

However, some think it's a good way to start with Ubuntu but I'm not one of those :)

---

### Post by Justin534 on 2011-12-24
Thanks for the info. I think I actually like Ubuntu a lot better than Windows, but would like to keep Win 7 on my system for when I really need it for something I can't do in linux. Is there a way to move my current installation of Wubi to its own partition, while also preserving my windows partition?

---

### Post by Megaptera on 2011-12-24
> **Justin534 said:**
> Thanks for the info. I think I actually like Ubuntu a lot better than Windows, but would like to keep Win 7 on my system for when I really need it for something I can't do in linux. Is there a way to move my current installation of Wubi to its own partition, while also preserving my windows partition?

I think this is the guide you need: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by Justin534 on 2011-12-24
> **Megaptera said:**
> I think this is the guide you need: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

Thanks!

---

