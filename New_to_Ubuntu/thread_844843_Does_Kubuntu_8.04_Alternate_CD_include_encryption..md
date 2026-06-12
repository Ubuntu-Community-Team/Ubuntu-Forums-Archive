---
title: "Does Kubuntu 8.04 Alternate CD include encryption... Y/N"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by Miguellint on 2008-06-30
Hi all...Have both googled and searched ubuntuforums but I can't find whether or not the Kubuntu Hardy Alternate CD has the "disk encryption at install" option. 

Specifically the "manual partitioning" option and the "physical volume for encryption" option (which in turn leads onto the LVM options)

Can anyone enlighten me with a definite yes or no.

Many thanks
Miguel

---

### Post by kool_kat_os on 2008-06-30
im just curious...but what are the LVM options for?

---

### Post by Miguellint on 2008-06-30
Hi kool_kat_os....This really clever guy explains it way more betterer than I ever could. 


[http://learninginlinux.wordpress.com/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/](http://learninginlinux.wordpress.com/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/)


Regards
Miguel

---

### Post by hyper_ch on 2008-06-30
alternate and server cd feature disk encryption upon installation.

LVM is a way to just add more harddisk as a "single partition". e.g. you have a 250 GB, a 500 GB and 1000 GB harddisk. With LVM you can combine them so that it appears to be a 1750 GB partition - however I think there are a few problems with LVM and disk encryption. Someone else had a problem here but I don't know if that's fixed meanwhile.

---

### Post by Miguellint on 2008-06-30
Thanks for the info hyper_ch. 

So I downloaded the alternate kubuntu CD and it's got the encryption options I want. 

The encryption install gave me a bit of a problem at "install the grub boot loader" because I'm dual booting. But it gave me enough info to manually edit the menu.lst file after reboot so all's well that ends well.

Regards
Miguel

---

