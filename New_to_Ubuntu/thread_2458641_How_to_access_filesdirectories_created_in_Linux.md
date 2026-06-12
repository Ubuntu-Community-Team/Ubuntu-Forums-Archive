---
title: "How to access files/directories created in Linux"
date: 2021-03-01
forum: New to Ubuntu
---

### Post by andrei0408 on 2021-03-01
Newbie here, I use Ubuntu 20.04 LTS to write C programs. Where can I access these programs and directories on my Win 10 disks? If, for instance, I have an assignment that I have to send how can I find the program written in Linux to send it? Thank you in advance!

---

### Post by CelticWarrior on 2021-03-01
Welcome.

Windows does not "see" Linux partitions if you're talking about a dual-boot system. One or more shared NTFS formatted data partitions are used for sharing files between system. Or a simple USB stick. Or a cloud service.

---

### Post by mastablasta on 2021-03-01
you need to mount the partition in windows 10 first. 

WSL can do it. 

you can also use Ext2Read for example. 

or you can save your work into shared NTFS data partition for example.

make sure you unmount any mounted partition at/before re-boot.

for virtualbox system it's a bit different.

---

### Post by Impavidus on 2021-03-01
Or you can simply use Ubuntu to send those files. Why would you need Windows to send in your assignments?

---

### Post by ActionParsnip on 2021-03-01
Windows cannot natively access Ext4 because.....it can't access very many file systems at all. You can install 3rd party tools to read Ext4 but on it's own Windows generally isn't very good.

---

### Post by TheFu on 2021-03-01
> **andrei0408 said:**
> Newbie here, I use Ubuntu 20.04 LTS to write C programs. Where can I access these programs and directories on my Win 10 disks? If, for instance, I have an assignment that I have to send how can I find the program written in Linux to send it? Thank you in advance!

Where or how is Ubuntu installed.  Is it a virtual machine?  Is it on a different machine available on a network?  Something else?

Do you ssh from Windows into the Ubuntu machine to do your coding?  

Linux/Unix is crazy flexible.

---

