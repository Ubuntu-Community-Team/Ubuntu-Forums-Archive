---
title: "install cant find IDE HDD"
date: 2012-05-07
forum: New to Ubuntu
---

### Post by fate6 on 2012-05-07
I have tried Ubuntu before but I never really made the switch and only used it very little
(like a day)
ok so I am trying to install Ubuntu 10.04 from a USB on a WD Caviar EIDE 120 GB but the installer cant find it
now the odd thing is that Gparted can see it just fine 


I have installed it before on a older HDD on the same computer using the same USB and everything when just fine >___<


I know im not describing things very well but frankly I have no idea what im talking about :)
(probably should mention I have been running windows the hole time right ?)
(oh and if you have a idea for a better tittle for the thread please let me know)



EDIT: I would also like to add that when running Ubuntu from USB it can see the HDD and I have access to it
(its just that damn installer that wont find it)

---

### Post by oldfred on 2012-05-07
Welcome to the forum.

Post this and a screenshot from gparted:

sudo fdisk -lu

---

### Post by fate6 on 2012-05-08
is there anything else you need ?

EDIT: here is a better pic

---

### Post by oldfred on 2012-05-08
You only have one NTFS partition. I have had gparted/installer not see my entire drive when chkdsk was needed on my NTFS XP partition. XP still booted so I did not know it then. I ran chkdsk, XP booted a bit faster & then gparted saw the NTFS drive.

I might try chkdsk from your Windows install CD/DVD or Windows repairCD or USB.

You should be able to just shrink the NTFS partition with gparted. Then Ubuntu should install to the unallocated.

I have several drives and have always partitioned in advance as I want control over where & partition sizes. But with 12.04 I thought I would just see what auto install does. It just took off,  found I had a 40GB unallocated space on sdc (no choices ether) and installed without any issues (other than nomodeset which I always have to use).

---

