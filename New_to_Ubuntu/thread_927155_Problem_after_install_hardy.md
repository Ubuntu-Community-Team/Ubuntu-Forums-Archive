---
title: "Problem after install hardy"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by iwan.gondrong14 on 2008-09-22
guys, i'm newbie in linux, i have problem after install hardy
1. missing windows boot
2. can't connect internet
3. my partition (fat32) didn't recognize

plz help, tq

---

### Post by JC Cheloven on 2008-09-22
please, post the output of this: 
```
sudo fdisk -l
```

and your /etc/fstab file

---

### Post by debiant on 2008-09-22
Hi there and "welcome to Ubuntu" !!!
:lolflag:

Seriously, once you're up and running you'll love it and it is satisfying to run your own machine and escape the evil empire..

Look-need more details! The FAT32-is that Windows? XP? (I know Vista is NTFS only) is it not seen/not recognised and that's why it wont boot? You know the GRUB loader-if it can see a drive but doesn't offer it as a choice to boot to that's easy to fix.

Also-you're internet, modem or router?

I'm a newbie myself but I can probably help with some of this and I'll be around for a couple of hours. :)

---

### Post by debiant on 2008-09-22
Hi there and "welcome to Ubuntu" !!!
:lolflag:

Seriously, once you're up and running you'll love it and it is satisfying to run your own machine and escape the evil empire..

Look-need more details! The FAT32-is that Windows? XP? (I know Vista is NTFS only) is it not seen/not recognised and that's why it wont boot? You know the GRUB loader-if it can see a drive but doesn't offer it as a choice to boot to that's easy to fix.

Also-you're internet, modem or router?

I'm a newbie myself but I can probably help with some of this and I'll be around for a couple of hours. :)

---

### Post by JC Cheloven on 2008-09-22
> **debiant said:**
> 

I'm a newbie myself but I can probably help with some of this and I'll be around for a couple of hours. :)

No way :-D Perhaps the original poster doesn't expect such a quick reply from the community, and is gone to have some beer :-) I'll come back tomorrow, myself :-({|=

---

### Post by mikewhatever on 2008-09-22
> **JC Cheloven said:**
> No way :-D Perhaps the original poster doesn't expect such a quick reply from the community, and is gone to have some beer :-) I'll come back tomorrow, myself :-({|=

Do you seriously expect the OP to know how to get the info you asked for?

> **iwan.gondrong14 said:**
> guys, i'm newbie in linux, i have problem after install hardy
1. missing windows boot
2. can't connect internet
3. my partition (fat32) didn't recognize

plz help, tq

Iwan, can you navigate to Applications->Accessories->Terminal and post the output of the following command:
> sudo fdisk -l
Don't re-type it, just copy/paste, you'll be asked for the password, type it in and hit Enter, copy the output and post here.

---

### Post by jemate18 on 2008-09-22
> **iwan.gondrong14 said:**
> guys, i'm newbie in linux, i have problem after install hardy
1. missing windows boot
2. can't connect internet
3. my partition (fat32) didn't recognize

plz help, tq

> 1. missing windows boot
Did you install ubuntu after windows?

> 2. can't connect internet
Please type this to the terminal
```
ifconfig -a
```
if you found any eth0 entry and numbers like 192.168.1.1 or something...
then type
```
sudo /etc/init.d/networking restart
```

> my partition (fat32) didn't recognize
please type
```
lsmod | grep -i "*fat*"
```
If there is an entry, then it should work.

---

