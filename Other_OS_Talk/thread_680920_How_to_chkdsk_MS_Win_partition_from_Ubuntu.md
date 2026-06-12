---
title: "How to chkdsk MS Win partition from Ubuntu?"
date: 2008-01-28
forum: Other OS Talk
---

### Post by pointyblue on 2008-01-28
My sister's Win 2k pc crashed and I've installed Ubuntu 7.10 in stead. (And it actually runs much faster even though it's a pretty old computer!! \\:D/ ) 

It's a dual boot system with the Win 2k not working. The reason I haven't deleted Win 2k yet is that I hope to make it work so I can gain access to the old emails + address book from Outlook Express and I also need to gain access to some contacts she stored in Outlook.

When I try to boot Win 2k from Grub it blue screens and tells me that I have to chkdisk /F the hard disk to fix a problem. As I have no windows system disk or installation CD that seems to be impossible.

Do any of you know if I can somehow chkdsk /F the drive from inside Ubuntu? I believe there's a fsck command or something but don't know how to use it...

---

### Post by lswest on 2008-01-28
chkdsk is not the same as fsck, i wouldn't run fsck on an ntfs windows partition...only possible option is to use a windows install disk and repair the partition...

---

### Post by pointyblue on 2008-01-28
Yeah well ... the only problem is I haven't got a windows install disk... :confused:

Anyone else..?

---

### Post by lswest on 2008-01-28
[this]("http://forum.doom9.org/archive/index.php/t-77799.html") might help

or, supposedly,
```
fsck -t ntfs /dev/hda
``` might work, but i can promise anything, might make it worse. -be sure to unmount the drive before you run fsck on it-

seems like i was wrong about fsck :P guess it's come a ways since i tried to recover an ntfs partition with it a couple of years back.

---

### Post by terminal on 2008-01-28
sudo apt-get install ntfstools

then u can do ntfschk /dev/sdaX
I wont bank on it to fix all problems though .

---

