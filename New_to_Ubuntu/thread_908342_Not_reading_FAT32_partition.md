---
title: "Not reading FAT32 partition"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by Zorgoth on 2008-09-02
I recently dual booted my Gateway M-6881 Windows Vista machine with Ubuntu 8.04 (64-bit) and noticed that ubuntu is not seeing the FAT32 partition I set up, while Windows is.  Is there a way to fix this?

---

### Post by aloshbennett on 2008-09-02
Are you able to mount the partition?

> mkdir /media/disk
sudo mount /dev/hda1 /media/disk

replace /dev/hda1 with the correct partition.

---

### Post by lapubell on 2008-09-02
it should be in your places menu.  also could be in the "Computer" option.

---

### Post by abhishek.malhotra35 on 2008-09-02
Your fat partition should come in Places. If not coming or some error is coming, then try to manually mount the partition. If it still not able to mount, try to forcibly mount it.

---

### Post by Zorgoth on 2008-09-02
I got it mounted now, thanks everyone.

---

