---
title: "help with installing ubuntu on external usb hdd"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by Kcrim on 2008-11-22
OK so i have read almost if not all threads about this and im having some problems 
so i go throught the install like normal but when it gets to install the grub loader i click on advance and type in /dev/sdb or /dev/sdb1 and for some reason when i plug the usb hdd i get some error 17
dont remember what it said but something like cannot mount the partition or something like that like i said dont really remember.

so ive installed it twice now and I dont want to intall the boot loader on hd0 since if i dont have the usb hdd it give me and error (did that once) and i have to reinstall windows on my laptop.


any help is really apriciated please help me solve this really want linux on a usb hdd

---

### Post by shifty_powers on 2008-11-22
[http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml](http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml)

super grub allows you to choose the hard drive to boot from.....

i know it is not ideal, but you may also be able to use the tools on there to achieve your aims...

---

### Post by caljohnsmith on 2008-11-22
How about booting your Live CD, open a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'

```
That will determine where Grub in the MBR of your sdb drive is looking for its boot files, which should help us figure out your Grub error 17 problem.

---

### Post by Kcrim on 2008-11-23
Thanks alot for all your help but i ended up tacking out my internal hdd from my laptop now it works just fine... I have another question tho

If i use dvd::rip to rip a movie will i be able to use dvd shrink in windows to burn it to a dvd or do i need to do some special thing to it??

---

