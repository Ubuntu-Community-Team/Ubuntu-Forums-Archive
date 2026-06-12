---
title: "cant open external HDD (cant mount volume)"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by sven_wien on 2008-11-11
Hi all,

i tryed to open my external HDD even tryed to force it but it didnt work.
I can see the icon under places but then i always get the msg "cant mount volume".
Any quick ideas, i do not have a windows mashine.

thanks

---

### Post by vigya on 2008-11-11
hi. not sure. try dis and let me knw too.
try the mount command at terminal
goes lyk
mount -t <filesystem> <something> <somewhere>
need to be a root user to do it, so add sudo to the beginning of the command.
u can use fdisk to know where ur drive really  is and wat its file system is.
might work with 
fdisk -ls
ur drive shud be sumwhere in /dev/hda/'ur drive'
use fdisk to find d drive name and mount it wherever u want.

---

### Post by sven_wien on 2008-11-11
wow thats a little to much can u ease that a little down , somewhere somehow, im new to this.

---

### Post by vigya on 2008-11-11
ohh.
<something> <somewhere> means <source> <destination>
i.e. where ur disk oes presently, and where u want to mount it.
so u just need to know where ur present disk actually is, and what its name is.thaat comes in <source>
for destination, if u want to mount it at the desktop, just give that path, like /Desktop

---

### Post by fenian on 2008-11-11
Open a terminal and Run this command...

> sudo blkid

Post the results and I can help you edit your fstab so the drive will mount.

---

### Post by DieHards77 on 2008-11-11
> **fenian said:**
> Open a terminal and Run this command...



Post the results and I can help you edit your fstab so the drive will mount.

hey, if you dont mind i have a very similiar problem, i posted my results from that command in terminal in my thread ( [http://ubuntuforums.org/showthread.php?p=6149890#post6149890](http://ubuntuforums.org/showthread.php?p=6149890#post6149890) ) 

also theyre 
> /dev/sda1: UUID="a3a40d3c-b4b3-46d0-8a0c-ffc9e5823754" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="311be9a7-6f1d-4da3-8599-25ff97b85924" 
/dev/sdb1: UUID="D27431CF7431B6D7" LABEL="Iomega HDD" TYPE="ntfs" 


do you have any ideas why this might be happening to me?  thanks a lot if you can i would really appreciate it

---

