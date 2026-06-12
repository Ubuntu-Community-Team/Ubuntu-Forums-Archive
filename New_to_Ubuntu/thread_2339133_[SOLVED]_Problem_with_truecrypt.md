---
title: "[SOLVED] Problem with truecrypt"
date: 2016-10-05
forum: New to Ubuntu
---

### Post by johnstons on 2016-10-05
Hi,
I have a problem with truecrypt. Installation seemed to work, but when I try to mount my file it says: "Couldnt find dmsetup". Even if I create a new container on my Lubuntu same error message appears.
What does it mean? Any idea how to fix? Or an alternative to TC for Lubuntu? Just want to crypt my banking details, nothing special.

Thanks!

---

### Post by alvils on 2016-10-05
Open the terminal and type in this:
sudo apt-get install dmsetup

dmsetup is the Linux kernel device mapper userspace library. In simple words, it is required for TrueCrypt to be able to do exactly what you want - mount your .tc file.

---

### Post by johnstons on 2016-10-05
Haha - didnt even think about this option. Thank you very much! :)

---

