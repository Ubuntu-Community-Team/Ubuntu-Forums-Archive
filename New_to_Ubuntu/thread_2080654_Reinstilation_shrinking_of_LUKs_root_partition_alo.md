---
title: "Reinstilation/ shrinking of LUKs root partition alongside Truecrypted win 7"
date: 2012-11-04
forum: New to Ubuntu
---

### Post by wintonian on 2012-11-04
After taking a look at win 8 and that horrible Metro carp a few months ago I jumped ship. I have briefly looked at Linux some years ago but never spent the time needed with it, so I'm just picking it up as I go along and find problems really.

I currently have the following:

sda1 - 100 M - win 7 (system partition) - boot flag
sda2 - 48.73 G - win 7 x64 (Truecrypt) 
sda3 - 203.95 M - /boot
sda4 --- extended part ---
 -sda5 99.98 G - crypt /root (Kubuntu 12.10 x64)

sdb1 1.36 T - NTFS - file storage

sdc1 ---extended part ---
-sdc5 - 1.86 G - unformatted (left over from previous setup)
-sdc6 - 0.91 T - crypt /home

Whilst I was fighting with the Kubuntu installer about keyfiles as well as arguing with GRUB I absent mindlessly told /root to take up the remaining space on the disk instead of just using 20 G.

I idely wanted to just shrink the partition but there seems to be no way way to do this and having got part way into and having trouble, I came to the conclusion that it might just be easier to reinstall /root.

If I have to reinstall windows as well then thats not too bad as there is noting on it and its only a baisc install with drivers and a couple of programs, so wouldn't take too tong.

So I'm hoping I can just reinstall /root, point to the existing encrypted (LUKs) /home and sling GRUB back on /sda3.

The question is I don't know if it will work like that and what needs to be done with Truecrypt and will I spend the evening swearing at GRUB again?

Unless there is a simple way to do a resize that I have missed?

To give some additional background for clarity I had to install Kubuntu from the 12.04 alt DVD and upgrade as 12.10 kept giving  me error about not being able to create keyfiles. Also I have not used a LVM.

Thanks in anticipation.

---

### Post by wintonian on 2012-11-05
I appreciate that people might not be able to help but if someone could suggest somewhere that might be able I would be grateful.

---

