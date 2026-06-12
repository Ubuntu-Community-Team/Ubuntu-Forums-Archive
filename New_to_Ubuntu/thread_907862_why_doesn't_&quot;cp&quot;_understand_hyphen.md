---
title: "why doesn't &quot;cp&quot; understand hyphen"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by dalailama on 2008-09-01
~/Desktop> cp UnePourTous.mp3 -
~/Desktop> cp UnePourTous.mp3 /media/usb1

~/Desktop> cd /media/usb1
/media/usb1> cd -
/home/dalailama/Desktop
~/Desktop>

Notice that when you pass the hyphen to **cd**, it sends you back to the original directory. But cp doesn't work that work. It created a file "-" as a result of the first line.

Regards,

Dalai Lama

FREE TIBET

---

### Post by prshah on 2008-09-01
> **dalailama said:**
> ~/Desktop> cp UnePourTous.mp3 -
/media/usb1> cd -
/home/dalailama/Desktop
~/Desktop>
Notice that when you pass the hyphen to **cd**, it sends you back to the original directory. But cp doesn't work that work. It created a file "-" as a result of the first line.


Passing hyphen to cd has no meaning. Just "cd" by itself will also send you back to your home directory. 

If you want to copy a file to your home directory, instead of "[SIZE="6"]-[/SIZE]" (hyphen), use tilde "[SIZE="6"]~[/SIZE]" (Upper-right hand side, next to "1" in the US layout) 

Eg ```

cp somefile ~
```
will copy somefile to your home directory.

> **dalailama said:**
> Regards,
Dalai Lama

Pull the other one; it's got bells on it.

---

