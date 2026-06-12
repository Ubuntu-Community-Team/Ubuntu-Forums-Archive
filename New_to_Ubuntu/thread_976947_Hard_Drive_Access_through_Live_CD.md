---
title: "Hard Drive Access through Live CD"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by supermelon928 on 2008-11-09
So I made a booboo trying to get ubuntu onto a pen drive, and now GRUB won't boot my operating system (Error 21). I have some resources to fix it (and if I fail I can just reinstall), But first I really want to back up the documents on my hard drive.

I have access, seemingly, to the files I acquired when I had windows, but about 1/3 of my files cannot be read, copied, written, or deleted from the Live CD. 

I was wondering if anyone knew of a method I could use to access these files so I can copy them to my pen drive.

---

### Post by louieb on 2008-11-09
Believe the hard drive can be accessed through the places menu. Know if you have a  [Knoppix Linux]("http://www.knoppix.net/")  CD the hard drives partitions show up as icons on the desktop

---

### Post by supermelon928 on 2008-11-09
I can view the files themselves and open the folders on my hard drive, but I can't read of write any of the files.

---

### Post by louieb on 2008-11-09
Try this Press Alt+F2 to bring up the run dialog. and enter
```
gksudo nautilus
```

---

### Post by adult swim on 2008-11-09
if you are having problems writing from the ntfs drive check out post 2 here [http://ubuntuforums.org/showthread.php?t=542702](http://ubuntuforums.org/showthread.php?t=542702)

note you need to change /dev/sda1 to whatever your ntfs partition is, if youre unsure how to find that  post back.

---

