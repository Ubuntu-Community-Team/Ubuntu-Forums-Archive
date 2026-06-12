---
title: "How to make FM show file size in MB instead of MiB"
date: 2018-06-09
forum: New to Ubuntu
---

### Post by wrongusername2 on 2018-06-09
Hi,
            File manager in 18.04  is showing file size in MiB. Please tell me how can I make FM show size in MB.


It can lead to lot of misunderstanding. I got a shock seeing DNG file becoming 4.2MB instead of 45MB. I was about to read the camera manual thinking some camera setting has made all the images 4.2MB.



Thanks

---

### Post by mc4man on 2018-06-09
The diff is 4.2 to 4.5, not 45

---

### Post by Topsiho on 2018-06-10
That's right.
MB counts in millions of bytes, and MiB counts in 1024*1024 bytes
1 million is decimal, 10^6; 1024 is binary: 2^10.
Topsiho

---

### Post by The Cog on 2018-06-10
Thunar (the default file manager with Xubuntu) shows the correct file size in megabytes. If that helps at all. Thunar can be installed in Ubuntu (sudo apt install thunar): I use it in the Ubuntu systems at work.

---

### Post by mc4man on 2018-06-11
I guess if you return would be useful to mention FM used. Ubuntu uses nautilus which reports in MB, ect. as do thunar & nemo
Dolphin & pcmanfm use MiB, ect.

---

