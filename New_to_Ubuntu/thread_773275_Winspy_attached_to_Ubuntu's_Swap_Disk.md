---
title: "Winspy attached to Ubuntu's Swap Disk"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by Ionna on 2008-04-28
Hi all!

Complete newbie at Ubuntu here. I downloaded and installed Ubuntu yesterday (dual-boot), ran for a bit and then switched to Windows for my games and ran Avast! while I slept. I woke up this morning to find that Avast has tagged Win32:Winspy-CK [Trj] as a trojan to my ubuntu swap disk file. Is there any way for me to remove this without having to go into my registry or deleting the file? 

Thanks in advance!

*PS: I'm posting this before work, so I hope you guys understand if I don't reply asap.

---

### Post by Jive Turkey on 2008-04-28
IFAIK windows can't even read a linux swap file, I'm thinking its probably a false positive anyway.  Try telling Avast to ignore that partition.  if you are using the ext2 driver in windows there is no need to mount your linux swap file.  Is this in WUBI or something?

---

### Post by Ionna on 2008-04-28
I'm not using the ext2 driver yet, just downloaded it today. Thing is, the trojan that Avast tagged was a malicious one; a keyboard logger called "Winspy", which as you can see, worries and has gotten me on the verge of panic. Is it still safe to ignore? :S

---

### Post by randomnick on 2008-04-28
No win32 executable is going to be able to install itself on a swap partition, I would also tell avast to ignore the partition, or better yet have it attempt to move the file to "quarantine" then manually browse to the quarantine location (after disabling avast) and upload the supposed malware to an online submission based scan if it will ease your peace of mind. I wouldn't worry about it though.

---

### Post by PeterJS on 2008-04-28
Even with the Ext2 driver windows wouldn't be able to read a swap partition, which is formated linuxswap not ext2. It's entirely possible that you have a virus, it is however quite impossible that a windows program would have found it in a linux swap partition, because there is no way for windows to read a linuxswap partition.

---

### Post by Ionna on 2008-04-29
Now that makes a whole lot more sense. Thanks everyone!

---

