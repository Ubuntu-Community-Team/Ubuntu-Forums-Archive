---
title: "Where are the samba shares mounted ?"
date: 2019-08-27
forum: New to Ubuntu
---

### Post by hk42 on 2019-08-27
Hi
Using the GUI I can easily mount and use the various samba shares of my network.
But in a text console using Midnight Commander as root I cannot find the mounting points.
Another solution would be to permanently mount those shares at boot for every body as 
I am the only user of my network.
What would be the correct way to do that ?

---

### Post by yancek on 2019-08-27
To permanently mount, you should have proper entries in the /etc/fstab file.  I don't use samba but I'm sure an online search for fstab samba example entries will provide some info.

---

### Post by Morbius1 on 2019-08-27
**/run/user/$UID/gvfs**

So in my case I connected to a server ( vin128 ) and a share ( shared ) in Nautilus so the mount point is:
```
/run/user/1000/gvfs/smb-share:server=vin128.local,share=shared
```

---

### Post by Holger_Gehrke on 2019-08-27
Shares mounted temporarily through a graphical file manager end up in subdirectories of /run/user/numerical_ID_of_mounting_user/gvfs/ (for example /run/user/1000/gvfs/ for the first normal user of the system). As you can tell by that path, gvfs is involved in accessing the shares which means the usual speed-penalties apply. For shares you use a lot, you should follow yancek's advice.

Holger

---

### Post by hk42 on 2019-08-27
Many thanks for the quick answers.
I had no idea gvfs existed.
I'll go the usual fstab way.
I plan to use shares a lot as my present successful (dual boot W10) installation is on a Beelink disk-less mini PC.

---

### Post by hk42 on 2019-08-27
Success :-)
The trick was I had to do: 
[COLOR=#242729][FONT=Consolas]sudo apt install cifs-utils
for my :
[/FONT][/COLOR]//192.168.1.68/SDA6  /mnt/Z  cifs  user=xxx,pass=xxxx,uid=1000,iocharset=utf8,vers=1.0  0 0
[COLOR=#242729][FONT=Consolas]/etc/fstab line to be accepted.
Z is the letter I use to mount the same share on a windows system.

[/FONT][/COLOR]

---

### Post by yetimon_64 on 2019-08-27
> **hk42 said:**
> Success :-) ...

That is good to see; please mark your thread as [SOLVED] from the drop down "Thread Tools" menu near the top of this page. The middle blue link in my signature is to a guide for how to do so, if needed.

Regards, yeti.

---

