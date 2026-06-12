---
title: "Large Drives"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by chowwi on 2008-10-14
Hello,

I have 2 1tb drives in my pc, I plan on using half of one for winblows and the other 1.5tb for linux. It's a ton of space and I am looking for ideas on how i should partition it. Maybe instal system on other half of drive a and use all of b for /home...i'm not sure......any advice would be great.

---

### Post by aeiah on 2008-10-14
you could set up a raid array if you have the right hardware / do it in software. otherwise you'll get better performance if /root is on one and /home is on the other i guess. id do it like this (if not doing raid):

HDD1:
linux root
backup partition

HDD2:
swap
/home
windows

---- or ----

HDD1:
linux root
backup partition

HDD2:
swap
/home
windows
a large partition that's shared between windows and linux, for your music, films, downloads, documents etc in NTFS (if you use a lot of windows) or EXT2 or EXT3 (if you're prepared to install the ext drivers for windows)


if you keep windows and linux on seperate drives, you can still use your pc if one breaks. also, you can reinstall windows without messing up grub

---

### Post by hyper_ch on 2008-10-14
do you need all that space on there? If not then I'd make:

hdd1:
500 GB Windows (if you need that much)
x GB Swap
500-x GB / (root)

hdd2:
500 GB windows backup
500 GB linux backup

---

### Post by manicman on 2008-10-14
I Also have two 1 Terabyte drives mine are set out as such

HD1
root (raid 0) (50gb) 
/home (raid 1) (947gb)
swap (2GB)
/boot (1gb)

HD2
root (raid 0) (50gb)
/home (raid 1) (947gb)
swap (2gb)

It works great you could do something similar but with a windows partition.

---

### Post by hyper_ch on 2008-10-14
don't forget: you should always have backups somewhere ;)

---

