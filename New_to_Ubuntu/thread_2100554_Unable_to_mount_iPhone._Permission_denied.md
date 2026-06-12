---
title: "Unable to mount iPhone. Permission denied"
date: 2013-01-02
forum: New to Ubuntu
---

### Post by gurrunaki on 2013-01-02
Hi all, I'm running Ubuntu 12.04 in a toshiba portege Z830, each time I tried connect my iPhone there is giving me the error Unable to mount iPhone, Permission denied. I checked in forums and the info that I got was about alternative software for the iphone in Ubuntu, but I can not reach this step if first I can not mount my iphone with the right permissions, any idea or command I should type in the terminal for mount the device?

Thanks in advance!!!

---

### Post by LiamOS on 2013-01-02
I'm not sure that this is generally the correct way, but you could try this.

```
sudo fdisk -l # Shows your partitions and disks, one of which should be your iPhone
sudo mount /dev/sdXn /mnt # X and n will be one of a,b,c 1,2,3 respectively, from the command above

```
Now your phone should be mounted to /mnt, so you can have a look around there. Don't expect this to interact well with any music players or whatever, though. I can't help on the automounting permissions as I don't use any software that does that.

---

### Post by gurrunaki on 2013-01-02
Thanks Liam for your answear but seems to much complicated for me and I don't want mess up. Searching in google I found the conecting the phone unlocked was working and yes, worked. I can see the pictures and music, I didn't try more yet, but if is nothing like itunes in linux, I think the best way is connect in a computer with windows :(

Thanks for your time, I really appreciate.

---

### Post by audiomick on 2013-01-02
> **gurrunaki said:**
> ..like itunes in linux,...

A search in the Internet turns up lost of articles about this. This one seems to sum up the alternatives quite nicely.

[http://www.ubuntuka.com/itunes-ubuntu-linux/]("http://www.ubuntuka.com/itunes-ubuntu-linux/")

---

