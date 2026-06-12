---
title: "Migrating Wubi to a separate installation."
date: 2012-06-18
forum: New to Ubuntu
---

### Post by sparko0317 on 2012-06-18
I have installed Ubuntu 12.04 on my computer alongside with windows 7 using wubi installer , and after a months of using ubuntu i've decided to say goodbye to windows . How to remove windows 7 completely while keeping my current Ubuntu installs , settings, and all those softwares that i downloaded from ubuntu site ?

---

### Post by na5h on 2012-06-18
This should help:
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

Remeber to ALWAYS do a backup of your important files before installing/upgrading/migrating!

---

### Post by Curtis6767 on 2012-06-18
> **sparko0317 said:**
> [FONT=Trebuchet MS][SIZE=3][SIZE=4]I have installed Ubuntu 12.04 on my computer alongside with windows 7 using wubi installer , and after a months of using ubuntu i've decided to say goodbye to windows . How to remove windows 7 completely while keeping my current Ubuntu installs , settings, and all those softwares that i downloaded from ubuntu site ?[/SIZE][/SIZE][/FONT]

Think about a dual boot with Win7. Unless you happen to have a legitimate Win7 disk, then if you wipe out Win7 but decide in the future that you need it, then you'll end up having to buy it. Win7 will be supported for several more years, 

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

GL

---

### Post by vazduxosbra4kania on 2012-06-18
> **sparko0317 said:**
> [FONT="Trebuchet MS"][SIZE="3"][SIZE="4"]I have installed Ubuntu 12.04 on my computer alongside with windows 7 using wubi installer , and after a months of using ubuntu i've decided to say goodbye to windows . How to remove windows 7 completely while keeping my current Ubuntu installs , settings, and all those softwares that i downloaded from ubuntu site ?[/SIZE][/SIZE][/FONT]

Just dont do that. I dont see any problem for you to keep both systems keeping in mind that you are new (like me) and there are many things you will find difficult to do. Its better to have system that you are familiar with until you become ultimate "only ubuntu" user...;)

---

### Post by na5h on 2012-06-18
> **Curtis6767 said:**
> Think about a dual boot with Win7. Unless you happen to have a legitimate Win7 disk, then if you wipe out Win7 but decide in the future that you need it, then you'll end up having to buy it. Win7 will be supported for several more years, 

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

GL

True. It doesn't hurt to keep it around...it may always come in handy. If this would be about keeping Vista, however...:D

---

### Post by afixane on 2012-06-18
Don't do that! Windows's CHKDSK is very useful for repairing NTFS drive (because fsck never make my NTFS drive repaired)

---

### Post by sparko0317 on 2012-06-19
Thanks for all your responses 

I wanted to remove windows because i heard Ubuntu OS installed alongside with windows7 using wubi is kinda slower than Ubuntu without any alongside OS's is it true ?

---

### Post by Nanur on 2012-06-19
> **sparko0317 said:**
> Thanks for all your responses 

I wanted to remove windows because i heard Ubuntu OS installed alongside with windows7 using wubi is kinda slower than Ubuntu without any alongside OS's is it true ?


First: I would keep Windows.
This is true, but you can install Ubuntu fully onto a partition on your hard drive, along side of Windows.
You need to make a live-CD or live-DVD, here are some good guides you can follow:

for live-USB on Ubuntu: [http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu)

for live-CD on Ubuntu: [http://www.ubuntu.com/download/help/burn-a-cd-on-ubuntu](http://www.ubuntu.com/download/help/burn-a-cd-on-ubuntu)

for a live-USB on Windows: [http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)

for a live-CD on Windows: [http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)

For any of these, though, you need to first download the .iso file.
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

Once you've got that made, plug/put it in, then go to the option menu and press "enter" on run Ubuntu. once booted, double click the icon that says install Ubuntu, then follow the steps.
Here is a guide you can use after you've created your live-CD or live-USB:
[http://www.ubuntu.com/download/help/install-ubuntu-desktop](http://www.ubuntu.com/download/help/install-ubuntu-desktop)

Also, out of curiosity, how large is your hard drive you are using?

-Nanur

---

### Post by blackflame2996 on 2012-06-20
> **sparko0317 said:**
> 
I wanted to remove windows because i heard Ubuntu OS installed alongside with windows7 using wubi is kinda slower than Ubuntu without any alongside OS's is it true ?

No, It's not any slower. I dual boot, and it is plenty fast. I would (and did) keep windows, for the occasional piece of software that requires windows (namely NXT-G and LabVIEW, which I need for FIRST).

---

### Post by Nanur on 2012-06-20
> **blackflame2996 said:**
> No, It's not any slower. I dual boot, and it is plenty fast. I would (and did) keep windows, for the occasional piece of software that requires windows (namely NXT-G and LabVIEW, which I need for FIRST).

Did you use a WUBI install? cause that makes it slower, but if you do the full install, it isn't slower.

---

### Post by na5h on 2012-06-20
Using Wubi is slower than a "real" installation since Wubi doesn't install Ubuntu on a separate partition. Basically: if Windows fails, so will Ubuntu.

Installing Ubuntu alongside Windows using the LiveCD is no problem at all. Ubuntu and Windows will be installed on separate partitions, so they will not affect one another directly.

---

### Post by carl4926 on 2012-06-20
why keep windows?
I held on to it for 5 years and never used it.
I've completely removed windows now.

Probably a VM install of win7 would be sufficient for most people that have reached this stage of Linux use.

---

### Post by na5h on 2012-06-20
> **carl4926 said:**
> why keep windows?
I held on to it for 5 years and never used it.
I've completely removed windows now.

Probably a VM install of win7 would be sufficient for most people that have reached this stage of Linux use.

I totally understand you! :) However, since most people have usually paid for their copy of Windows 7, it doesn't hurt to have it around...especially if you're still a bit new to Ubuntu. That's why I often tell people not to be to quick about removing Windows completely.

---

### Post by carl4926 on 2012-06-20
> **na5h said:**
> I totally understand you! :) However, since most people have usually paid for their copy of Windows 7, it doesn't hurt to have it around...especially if you're still a bit new to Ubuntu. That's why I often tell people not to be to quick about removing Windows completely.
Yes

Actually, most pre-installed  windows are just a pile of 'smelly brown stuff'. The only advantage they offer is all the drivers are in place. Otherwise they are just bloated with all kinds of cr(a)p.

YMMV  of course.

---

### Post by na5h on 2012-06-20
> **carl4926 said:**
> Yes

Actually, most pre-installed  windows are just a pile of 'smelly brown stuff'. The only advantage they offer is all the drivers are in place. Otherwise they are just bloated with all kinds of cr(a)p.

YMMV  of course.

lol. I remember trying to help a friend of mine change his wallpaper on a netbook that came with the "starter" edition of Windows 7...took me quite a while to realize that it couldn't be done!

---

### Post by sparko0317 on 2012-06-21
Thanks for reply Nanur

My C drive that has windows have 151GB free of 210GB
and my D drive that i store my files is 250GB free of 488GB

---

