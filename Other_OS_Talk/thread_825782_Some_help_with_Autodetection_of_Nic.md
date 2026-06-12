---
title: "Some help with Autodetection of Nic?"
date: 2008-06-11
forum: Other OS Talk
---

### Post by pixeldotz on 2008-06-11
hello,

i'm having a bit of a problem here.
i created a boot disk for our machines @ work that have the following nic drivers on them

> display bootmsg.txt
default 1
prompt 1


label 1
	kernel memdisk
	append initrd=intel.img

label 2
	kernel memdisk
	append initrd=intel1b.img

label 3
	kernel memdisk
	append initrd=broadcom.img
label 4
	kernel memdisk
	append initrd=3com.ima

timeout 60000

my question is this - is there anyway to get a script somewhere in here that will autodetect the nic inside a pc and autoload the  corresponding .img?

as you probably guessed, all these .img files are windows bootdisks designed to load the driver it's named as.

luckily - all the computers we have in the district use one of these 4 drivers.

---

### Post by timcredible on 2008-06-11
are you running ubuntu?  if so, it runs a hardware autodetect at boot.

---

### Post by pixeldotz on 2008-06-11
not on this machine.

but what i'm looking for is some sort of function that will load with isolinux, detect the nic card, then load the .img that corresponds to that nic card.

none of these drivers are for a linux box.

every multinic autodetection utility i've found for windows has way to many options than what i need.

---

