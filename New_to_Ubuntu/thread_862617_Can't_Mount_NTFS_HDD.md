---
title: "Can't Mount NTFS HDD"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by mikee55 on 2008-07-17
Cannot mount volume.

You are not privileged to mount the volume 'Storage'.

                                            OK

I can't access my harddrive called Storage because I'm not privileged. Who says?
Why? I've searched, but I'm not getting the answer. Can you help, please?

Mike:confused:

---

### Post by Horomancer on 2008-07-17
I'm not 100% sure, but i thought linux systems could not read or write to NTFS formated HDs. I think that's a windows only achitcture type.

---

### Post by mikee55 on 2008-07-17
Hi Horomancer, I have NTFS Config installed which worked in PCLinuxOS???

---

### Post by Joeb454 on 2008-07-17
Ntfs-Config works if you want to auto-mount the drive. I have a guide on this (link is in my sig).

And you need to make sure that you have cleanly unmounted the drive before mounting it in Linux.

Also, I'm curious here, did you try and mount it through the terminal?

---

### Post by Troll_the_Great on 2008-07-17
If your drive is already mounted, hit Alt+F2 and paste
```
gksu nautilus
```
Now navigate to the drive and you will have the permission to do anything.
If you want that your drive is mounted automatically at start up install ntfs-config:
```
sudo apt-get install ntfs-config
```
Have a look at this links too:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)
Hope this helps.
Cheers!

---

### Post by Troll_the_Great on 2008-07-17
> **Horomancer said:**
> I'm not 100% sure, but i thought linux systems could not read or write to NTFS formated HDs. I think that's a windows only achitcture type.

Linux CAN read and write NTFS now.And with ntfs-config will auto mount at start up NTFS partitions.

---

### Post by bodhi.zazen on 2008-07-17
> **mikee55 said:**
> Cannot mount volume.

You are not privileged to mount the volume 'Storage'.

                                            OK

I can't access my harddrive called Storage because I'm not privileged. Who says?
Why? I've searched, but I'm not getting the answer. Can you help, please?

Mike:confused:

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

[uhelp]community/RootSudo[/uhelp]

---

