---
title: "Setting up WD My Book Live on Kubuntu"
date: 2013-02-16
forum: New to Ubuntu
---

### Post by NevidS on 2013-02-16
> **wallaroo said:**
> Hi Shadius,

The 'Compatibilty' list is just for the included software, which is written only for Windows or Mac (not needed for Linux). The OS on the box itself is Linux so if you wanted to connect the pure 'linux way' you could use SSH to bring up a terminal session on the MYBOOK, then set up NFS connections.

However you don't need to go to that level, a simple CIFS mount on your Ubuntu box is sufficient for general use.

The default share on the MYBOOK is named 'Public' and as the name suggests allows anyone to connect to the share. 

On your Ubuntu box..
- Create a mount point in /media
e.g. 
```
sudo mkdir /media/mybooklive
```- then mount it as a 'CIFS' mount
i.e. 
```
sudo mount -t cifs -o username=,rw,users,uid=1000 //mybookipaddress/Public /media/mybooklive
```(uid is your Ubuntu uid - usually 1000)
(mybookipaddress is the ip address of the MYBOOK device)
(You may need to install the 'cifs-utils' package first).

- to make it mount at boot, add the mount to the /etc/fstab file.
i.e.
```
//mybookipaddress/Public /media/mybooklive cifs rw,username=,uid=1000 0 0
```Note: I have found that when I need to transfer large or lots of files to the MYBOOK, it's best to use FTP because it's more stable. CIFS and NFS mounts are fragile and tend drop out or freeze at the worst possible times.

Hi!
I have the 1tb My Book Live and a Kubuntu.
If I try to do like report from Wallaroo, at the second command I receive this output:
```
nevids@hall9000:~$ sudo mount -t cifs -o username=,rw,users,uid=1000 //192.168.0.9/Public /media/mybooklive
username specified with no parameter

```
Where is my mistake?
Thanks!

---

### Post by oldos2er on 2013-02-16
Post moved to its own thread.

---

### Post by NevidS on 2013-02-18
No one can help me?

---

### Post by NevidS on 2013-02-23
Last try: anyone? :p

---

### Post by howefield on 2013-02-23
It isn't completely clear what it is that you want to accomplish.

Perhaps if you state your intended/expected outcome someone will be more likely to offer some help.

Certainly with the same drive, and adding the last command to fstab mounts my drive at boot.

---

### Post by NevidS on 2013-03-03
> **howefield said:**
> It isn't completely clear what it is that you want to accomplish.

Perhaps if you state your intended/expected outcome someone will be more likely to offer some help.

Certainly with the same drive, and adding the last command to fstab mounts my drive at boot.
Oh thank you for support!
So, the point is: I have a Western Digital Live book ([http://www.wdc.com/it/products/products.aspx?id=280]("http://www.wdc.com/it/products/products.aspx?id=280")) that have only and ethernet port. I'm trying to use, but Kubuntu seems that is not able to access. 
If I follow how reported in the first post (that is a thread that talk about the same problem) the output received in the second step (after the mkdir command) is:
```
nevids@hall9000:~$ sudo mount -t cifs -o username=,rw,users,uid=1000 //192.168.0.9/Public /media/mybooklive
username specified with no parameter
```
Why?:(

---

### Post by JGiordano999 on 2013-03-25
> **NevidS said:**
> Oh thank you for support!
So, the point is: I have a Western Digital Live book ([http://www.wdc.com/it/products/products.aspx?id=280](http://www.wdc.com/it/products/products.aspx?id=280)) that have only and ethernet port. I'm trying to use, but Kubuntu seems that is not able to access. 
If I follow how reported in the first post (that is a thread that talk about the same problem) the output received in the second step (after the mkdir command) is:
```
nevids@hall9000:~$ sudo mount -t cifs -o username=,rw,users,uid=1000 //192.168.0.9/Public /media/mybooklive
username specified with no parameter
```
Why?:(

You forgot to put your username there, after "username=", just like the error message said.

---

### Post by SimplymeRainer on 2013-04-30
Same problem as above except that it asks me for the password. where would i enter that so it mounts automatically at boot?

---

