---
title: "[SOLVED] Resizing partition problem"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by Miguellint on 2008-06-30
Hi all...I have a 30 GB hard disk with the following partitions...

(hd0,0) 200MB /boot
(hd0,1) 15GB  free space (formerly XP)
(hd0,2) 14GB  / (root partition for Ubuntu)
(hd0,3) 800MB /swap

I want to resize my Ubuntu partition to make use of the free space brought about by deleting XP. 

I've run both Gparted and QTparted from my live Knoppix DVD but am unable to add the free space to Ubuntu. Is it because the free space precedes the Ubuntu partition. 

If I delete the swap partition I am able to add that without any problem. Just drag and resize. But there is no such option with the free space.

Any advice appreciated

Regards
Miguel

---

### Post by logos34 on 2008-06-30
> **Miguellint said:**
> 
I've run both Gparted and QTparted from my live Knoppix DVD but am unable to add the free space to Ubuntu. Is it because the free space precedes the Ubuntu partition. 


You're probably using an older version of gparted--0.3.3 or higher can handle resizing the left boundary.

Use Gparted on the gutsy or hardy live cd, or dl the latest Gparted live cd.

---

### Post by ChameleonDave on 2008-06-30
Be warned.  Resizing from the left seems to take hours sometimes.

---

### Post by Miguellint on 2008-07-04
Thanks all. Upgraded gparted and job done.

Regards
Miguel

---

### Post by logos34 on 2008-07-04
ok. Go to thread tools>mark as 'Solved'

enjoy

---

