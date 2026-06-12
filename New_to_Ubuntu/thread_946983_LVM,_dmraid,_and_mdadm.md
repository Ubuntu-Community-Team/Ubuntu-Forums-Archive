---
title: "LVM, dmraid, and mdadm?"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by momonari on 2008-10-13
Hi,
I didn't get any replies in one of the other forums, so I'm trying here.

I have decided to migrate from M$ Windows to Ubuntu. I currently have a RAID5 set up using the Intel ICH8R/ICH9R SATA RAID controller on my motherboard. From the reading I've been doing, I understand that this is a fakeRAID.

What I would like to know is, what is the difference between LVM, dmraid, and mdadm? And are any of these going to help me mount my RAID5 in Ubuntu?

If not, I have two new HDDs and I was going to copy all the data onto one of them and then build a RAID1 in Ubuntu (without wiping all the data, of course). Which tool should I use to do that?

Thank you.

Momonari

---

### Post by sazan on 2008-10-17
> **momonari said:**
> Hi,
I didn't get any replies in one of the other forums, so I'm trying here.

I have decided to migrate from M$ Windows to Ubuntu. I currently have a RAID5 set up using the Intel ICH8R/ICH9R SATA RAID controller on my motherboard. From the reading I've been doing, I understand that this is a fakeRAID.

What I would like to know is, what is the difference between LVM, dmraid, and mdadm? And are any of these going to help me mount my RAID5 in Ubuntu?

If not, I have two new HDDs and I was going to copy all the data onto one of them and then build a RAID1 in Ubuntu (without wiping all the data, of course). Which tool should I use to do that?

Thank you.

Momonari




for LVM...[http://www.redhat.com/magazine/009jul05/features/lvm2/](http://www.redhat.com/magazine/009jul05/features/lvm2/)
for dmraid.....[http://www.linuxmanpages.com/man8/dmraid.8.php](http://www.linuxmanpages.com/man8/dmraid.8.php)
for mdadm...[http://www.linuxmanpages.com/man8/mdadm.8.php](http://www.linuxmanpages.com/man8/mdadm.8.php)

u can use mdadm for configuring RAID.. u can choose levels and type etc.. and u can use LVM above it for managing raids and other drives if available... 

go through the links i have given.. they will help you.. 

cheers

---

### Post by _sAm_ on 2008-10-17
> And are any of these going to help me mount my RAID5 in Ubuntu?
Read this; [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by momonari on 2008-10-17
OK, so the way I understand it is, mdadm is a software RAID tool. Once I've created a RAID with it, I use LVM to manage partitions on the RAID?
And dmraid is just for discovering fakeRAIDs?

And since RAID5 support in dmraid is still only in its early stages, I'm pretty much going to have to rebuild my RAID5 using mdadm?

---

### Post by sazan on 2008-10-20
> **momonari said:**
> OK, so the way I understand it is, mdadm is a software RAID tool. Once I've created a RAID with it, I use LVM to manage partitions on the RAID?
And dmraid is just for discovering fakeRAIDs?

And since RAID5 support in dmraid is still only in its early stages, I'm pretty much going to have to rebuild my RAID5 using mdadm?




you hav understood that well enough..

---

### Post by jerome1232 on 2008-10-20
I just wanted to throw in LVM can do striping/mirroring. (I'm sure mdadm is better at this stuff though, I just use lvm to do striping across pata disks)

---

### Post by sazan on 2008-10-20
> **jerome1232 said:**
> I just wanted to throw in LVM can do striping/mirroring. (I'm sure mdadm is better at this stuff though, I just use lvm to do striping across pata disks)

is there a way to find out which is better for striping/mirroring ...LVM or mdadm...

---

### Post by momonari on 2008-10-20
> **jerome1232 said:**
> I just wanted to throw in LVM can do striping/mirroring. (I'm sure mdadm is better at this stuff though, I just use lvm to do striping across pata disks)

Is there a reason you use it to stripe PATA disks and not SATA disks?

---

### Post by sazan on 2008-10-20
> **momonari said:**
> Is there a reason you use it to stripe PATA disks and not SATA disks?


u can use it to stripe any of them.. not a problem ...
_SAM_ just added that u can use LVM to stripe the hard disks too.. using lvm commands similar to mdadm.. but mdadm is better in performance ..

---

### Post by momonari on 2008-10-20
> **sazan said:**
> u can use it to stripe any of them.. not a problem ...
_SAM_ just added that u can use LVM to stripe the hard disks too.. using lvm commands similar to mdadm.. but mdadm is better in performance ..

Oh, I realise that. I was just wondering why he said he uses it specifically for his PATA disks.

---

### Post by sazan on 2008-10-20
exactly .......

---

### Post by jerome1232 on 2008-10-20
Does mdadm work in that scenario? Well I've never used mdadm, come to think of it they are on the same ribbon so I doubt it's even a performance gain :)

And becuase I have pata disks on this old computer, why else would one be using them ;)

---

### Post by sazan on 2008-10-20
> **jerome1232 said:**
> Does mdadm work in that scenario? Well I've never used mdadm, come to think of it they are on the same ribbon so I doubt it's even a performance gain :)

And becuase I have pata disks on this old computer, why else would one be using them ;)

mdadm is a tool to handle raid .. it is a simple to use tool n used in companies who work on storage domain..

---

### Post by jerome1232 on 2008-10-20
Yeah I know, hence sata only club. 
I didn't ask what mdadm is... I was asked why I would use lvm to strip across pata disks and not sata, raid is a sata only thing....

---

### Post by momonari on 2008-10-20
> **jerome1232 said:**
> Yeah I know, hence sata only club. 
I didn't ask what mdadm is... I was asked why I would use lvm to strip across pata disks and not sata, raid is a sata only thing....

Err...since when was RAID for SATA only?

PATA RAID controllers: [http://www.highpoint-tech.com/USA/series_ataraid_ataraid.htm](http://www.highpoint-tech.com/USA/series_ataraid_ataraid.htm)

---

### Post by damvcoool on 2009-10-15
Because SATA is much more suitable than PATA for RAID. 1 Channel 1 Disk.
Altho SAS i even Better but not for regular Desktops. Unless you have a very expesive MoBo, or but you own controller.

---

