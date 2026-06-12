---
title: "Replacing blueman in Xubuntu"
date: 2015-08-20
forum: New to Ubuntu
---

### Post by alan66 on 2015-08-20
I use bluetooth to send music to my hi-fi via a music receiver. Blueman can't handle bluetooth receivers (and bluetooth headphones) because of problems with the audio-sink. Ubuntu doesn't have that problem. I prefer to use Xubuntu so how can I put the Ubuntu bluetooth software in Xubuntu.

Thank you
Alan

---

### Post by TheFu on 2015-08-20
Run the program you want under ubuntu, determine the program name (I'd look in the process table) and search for the package which from which it comes (dpkg-query). Install that package and use it.

---

### Post by alan66 on 2015-08-20
Thank you I will do that
Cheers
Alan

---

