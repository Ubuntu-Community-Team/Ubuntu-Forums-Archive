---
title: "grub rescue problem, need help"
date: 2013-07-10
forum: New to Ubuntu
---

### Post by Traxster on 2013-07-10
Hi guys,


I have a major issue here. I am getting a grub rescue message upon boot. 

I have loaded into my system with a live cd and downloaded and ran boot-repair which attempted to make a repair, however, I still have the same problem. In the process it created [this]("http://paste.ubuntu.com/5863210/") log file. Can someone please help, as I am locked out of my system. I need specific instructions if possible. 

Highly appreciated! 

Traxster

---

### Post by Traxster on 2013-07-10
Ok guys, 


I tried to back up my home directory so I can do a clean install, however, since my home directory was encrypted, and I did not write down my wrapped pass phrase then I was not successful at backing up my home directory. Remember I am getting into my system with a live cd. There are utilities that will allow you to recover your wrapped pass phrase for home directory, however, I think that you have to be logged in to that user account, which I cant do since I have the grub rescue error, so it seems like my only hope is to fix grub and try to be able to load into my system. Considering my circumstances, can anyone give me any help. I have a lot of bookmarks, and files, I don't want to loose.

Greatly appreciated



Traxster

---

### Post by fantab on 2013-07-11
You can re-install GRUB following this [Grub Wiki]("https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2"). In your case use a LiveCD/DVD method.

Good Luck.

---

### Post by dannyboy79 on 2013-07-11
was your /home/ directory on it's own partition OR was it just part of /?

---

### Post by Traxster on 2013-07-11
> **dannyboy79 said:**
> was your /home/ directory on it's own partition OR was it just part of /?


it was part of /

---

### Post by Traxster on 2013-07-11
ok, guys, here is what I ended up doing. I formatted my hd and I am  starting all over. I was able to recover MOST of my data from various  other places. since I am reinstalling, I decided to attempt to enhance  the security of my system, and in the process, learn more about the  Ubuntu installation process, and the file system itself.  

I am attempting to perform [this]("http://blog.markloiseau.com/2012/05/ubuntu-aes-xts-plain64/")  custom install using LVM2 and cryptsetup , since  Ubuntu DOES NOT (do  not understand the reason for this) support AES-XTS-256 bit encryption  from a live cd install. It has been very challenging, however, I have  made progress after reading a few blogs. One of the issues I am having  is updating initramfs after making changes to /etc/crypttab. I received a  message "update-initramfs is disabled since running on read-only  media". I have figured out why I am getting the message. I have to  chroot in to the real Ubuntu partition. found this out by reading [here]("http://ubuntuforums.org/showthread.php?t=1756694"), [here]("http://ubuntuforums.org/showthread.php?t=1756694") and [here]("http://karuppuswamy.com/wordpress/2010/06/02/how-to-chroot-to-ubuntu-using-live-cd-to-fix-grub-rescue-prompt/"),  while i made progress on this particular step, I am still getting some  errors.  Below is what I am doing at terminal to, first, chroot to the  real Ubuntu partition from the Live CD, and command  to update  initramfs.

ubuntu@ubuntu:~$ sudo chroot /media/ubuntu/dbcba8da-2d9f-4564-a2ee-ee52f4903e1c
root@ubuntu:/# update-initramfs -u

below is the responce from terminal

update-initramfs: Generating /boot/initrd.img-3.8.0-19-generic
/usr/sbin/mkinitramfs: 137: /usr/sbin/mkinitramfs: cannot create /dev/null: Permission denied
grep: /boot/config-3.8.0-19-generic: No such file or directory
/usr/sbin/mkinitramfs: 142: /usr/sbin/mkinitramfs: cannot create /dev/null: Permission denied
/usr/sbin/mkinitramfs: 142: /usr/sbin/mkinitramfs: cannot create /dev/null: Permission denied
/usr/sbin/mkinitramfs: 279: /usr/sbin/mkinitramfs: cannot create /dev/null: Permission denied
WARNING: no ldd around - install libc-bin
update-initramfs: failed for /boot/initrd.img-3.8.0-19-generic with 1.

 Can  soneone familiar with this particular install, give me an explanation  of the steps and command to update initramfs propertly? I will continue  to research on my own, however, any help would be greatly appreciated.

thanks again,


Traxster

---

