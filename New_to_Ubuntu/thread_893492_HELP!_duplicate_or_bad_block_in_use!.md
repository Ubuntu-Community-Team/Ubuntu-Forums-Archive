---
title: "HELP! duplicate or bad block in use!"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by DVD-R on 2008-08-18
Help!
The system will no longer boot.
It comes up to /dev/sda1/multiply-claimed blocks in inode xxxxxxx:xxxxxx

Automatic fsck failed, manual must be performed.

I have a ubuntu restore cd, but it doesn't seem to have anything on it that I can use to help.
If nothing more, I would like to copy out text or document files I was working on and start over.

Can I simply restore the root files without having to delete everything?

Big thanks!!
dw

---

### Post by ajgreeny on 2008-08-18
Not sure what you mean by a Ubuntu restore CD, but assuming it's a live Ubuntu CD boot into that and then in the terminal of that run  ```
sudo e2fsck /dev/sd??
```Make sure your hard disk partitions are not mounted and make sure you get the right partition of your install before doing this.  That will run the manual fsck asked for and may help.

---

### Post by DVD-R on 2008-08-18
Thank you Ajgreeny!!!!

Awesome!!
That worked sweet!!
I used the install cd instead of the rescue cd.

I wonder if there is a safe way for me to keep a snapshot of the system for a future restore is need be?

---

