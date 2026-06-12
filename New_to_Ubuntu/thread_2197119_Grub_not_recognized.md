---
title: "Grub not recognized"
date: 2014-01-02
forum: New to Ubuntu
---

### Post by klemzy2012 on 2014-01-02
Yesterday I installed Ubuntu 13.10 beside Windows 8.1, but my grub menu does not appear on it's own. I have to go in boot options and check disc boot manually to get grub menu.

Probably problem is, that I have two discs in my laptop. One is 120Gb ssd and the other is 750Gb HDD disc. Windows is installed on ssd and I chose partition from HDD disc to be ext4 for Ubuntu.
So I suspect that there is something wrong with this am I right? I already try to fix this using [Boot-repair]("https://help.ubuntu.com/community/Boot-Repair"), but without any success.

---

### Post by oldfred on 2014-01-02
Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by chkneater on 2014-01-02
Is Bios set to boot from Sata or IDE?

---

### Post by klemzy2012 on 2014-01-03
Ok damn it, I forgot to mention another thing..I plug second disc(750hdd) in the place where [dvd drive should be]("http://www.newmodeus.com/shop/index.php?main_page=page&id=7"). 
I suspect now, that this could be my problem am I right?

I am wondering now, if I can install grub on my ssd, so it will be recognized correctly?

Oldfred, I will paste you this report later this day ok?

thanks

---

### Post by oldfred on 2014-01-04
Some systems will see and use a hard drive mounted in the DVD slot, but will not boot from it for some reason.

---

### Post by klemzy2012 on 2014-01-05
> **oldfred said:**
> Some systems will see and use a hard drive mounted in the DVD slot, but will not boot from it for some reason.

Ok, so I will have to find another solution...any idea? :)

---

### Post by oldfred on 2014-01-05
I think one user posted that he was able to put  a /boot partition on main hard drive but then have / (root) on the convertible drive. You may be able to also have /boot on a flash drive on anything else that boots.
Its Windows that does not boot from external drives, so maybe they have a BIOS update that would let other system boot?

---

### Post by klemzy2012 on 2014-01-14
Ok, so if I understand this correctly I can put a /boot partition on ssd drive beside windows 8.1 and it should boot normally? Or I have to do something with this /boot partition. I know how to create it, but I didn't work with it yet...so I don't know if there is any special procedure for that.

About BIOS...I have the latest version.

---

### Post by klemzy2012 on 2014-01-14
> **oldfred said:**
> I think one user posted that he was able to put  a /boot partition on main hard drive but then have / (root) on the convertible drive. You may be able to also have /boot on a flash drive on anything else that boots.
Its Windows that does not boot from external drives, so maybe they have a BIOS update that would let other system boot?

Ok, so if I understand this correctly I can put a /boot partition on ssd drive beside windows 8.1 and it should boot normally? Or I have to do something with this /boot partition. I know how to create it, but I didn't work with it yet...so I don't know if there is any special procedure for that.

About BIOS...I have the latest version.

---

### Post by oldfred on 2014-01-14
When you install you have to use Something Else or manual install so you can specify more than the default / (root) and swap partitions.
Since UEFI, systems use one efi partition to boot from, so does system still boot from SSD with grub in efi partition on SSD?
I like to configure all drives with UEFI to have an efi partition first, even if that drive is not currently the boot drive. Later you may want to boot from that drive (even if only for repairs) and adding an efi partition may be difficult.

Did you review the two drive UEFI info in link in my thread. Plus several (now older) links to users who manually moved efi files from one drive to another or used Boot-Repair.

---

