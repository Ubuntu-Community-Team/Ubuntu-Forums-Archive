---
title: "Just a simple question about SAMBA"
date: 2012-07-05
forum: New to Ubuntu
---

### Post by Deniz343 on 2012-07-05
Can I change this in smb.conf > [share]
    comment = Ubuntu File Server Share
    path = **_/srv/samba/share_**
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0755
To
> [share]
    comment = Ubuntu File Server Share
    path = **_/dev/sdb2_**
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0755

---

### Post by Morbius1 on 2012-07-05
No.

/dev/sdb2 is a physical device. You can change the path to the directory it's mounted to though ( i.e., mount point ).

---

### Post by Deniz343 on 2012-07-05
> **Morbius1 said:**
> No.

/dev/sdb2 is a physical device. You can change the path to the directory it's mounted to though ( i.e., mount point ).

How can I path this mount point to samba ?

Best Regards

---

### Post by alexlpratt on 2012-07-05
This appears to be a pretty good guide for what you would like to do: [Forum Thread]("http://www.linuxquestions.org/questions/linux-newbie-8/how-to-create-new-mount-point-in-linux-906731/")

---

### Post by Morbius1 on 2012-07-05
> **Deniz343 said:**
> How can I path this mount point to samba ?

Best Regards
Your simple questions require much information:

[1] Is it currently mounted?

The output of this command will tell you if it is mounted and where it is mounted:
```
mount
```[2] If it's not mounted then more information is required: How is it formatted and what is it's UUID number:
```
sudo blkid -c /dev/null
```And where would you like it to be mounted?

---

### Post by Deniz343 on 2012-07-05
> fukawi1 ~ # sudo mkdir /media/usb_hdd
and then mount the filesystem to the mount point, using:
Code:
fukawi1 ~ # sudo mount /dev/sdc /media/usb_hdd
This is simple but is this command start on start up.

---

### Post by Deniz343 on 2012-07-05
> **Morbius1 said:**
> Your simple questions require much information:

[1] Is it currently mounted?

The output of this command will tell you if it is mounted and where it is mounted:
```
mount
```[2] If it's not mounted then more information is required: How is it formatted and what is it's UUID number:
```
sudo blkid -c /dev/null
```And where would you like it to be mounted?

1) Yes my disk is mounted. And I run the command and I see this /dev/sdb2 on /media/sdb2 should I need to path this > /media/sdb2

---

### Post by Morbius1 on 2012-07-05
You asked 2 questions in the last 2 posts:

[1] your current mount point is /media/sdb2 so your smb.conf share should look like this:
> [share]
    comment = Ubuntu File Server Share
    path = **_/media/sdb2_**
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0755                      [2] But the remaining question is how did it mount to /media/sdb2?

If there is an entry for sdb2 in /etc/fstab then it will always mount to that location. 

If it isn't in fstab then it will not. So post the output of the following commands:
```
cat /etc/fstab
``````
sudo blkid -c /dev/null
```
And we will have enough information to put it there.

---

### Post by Deniz343 on 2012-07-06
> **Morbius1 said:**
> You asked 2 questions in the last 2 posts:

[1] your current mount point is /media/sdb2 so your smb.conf share should look like this:
[2] But the remaining question is how did it mount to /media/sdb2?

If there is an entry for sdb2 in /etc/fstab then it will always mount to that location. 

If it isn't in fstab then it will not. So post the output of the following commands:
```
cat /etc/fstab
``````
sudo blkid -c /dev/null
```
And we will have enough information to put it there.

I'm using pySDM to mount my disk every startup automaticly.
And look out this screenshot from pySDM
[ATTACH]220749[/ATTACH]

---

