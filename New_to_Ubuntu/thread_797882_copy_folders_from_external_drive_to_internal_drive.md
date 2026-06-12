---
title: "copy folders from external drive to internal drive"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by franky_88 on 2008-05-17
Hello everyone,


I have a folder on an networked hard disk drive that I want to copy on my internal Hard disk drive. hen I try to drag & drop the folder it gives me the error: permission denied. When I try to do it via the sudo nautilus --no-desktop command it gives me the error: Location is not mounted.

Any help would be greatly appreciated,

Frank

---

### Post by bodhi.zazen on 2008-05-17
What folder are you copying and to where ?

---

### Post by franky_88 on 2008-05-17
I am copying a folder from my external Hard drive to my internal hard drive. I have the permission to copy the folder from my external Hard drive, i just checked. I think this might be a problem with Ubuntu. 


Thank you,

Frank

---

### Post by bodhi.zazen on 2008-05-17
The problem is most likely with permissions of the destination directory.

Without additional information, hard to help.

---

### Post by franky_88 on 2008-05-18
How do I have total permission in ubuntu?? I am the one who installed ubuntu on my laptop. I tried the gksudo nautilus command but it gives me the error: cant copy because location not mounted. If you need additional information please tell me what you need and I will give it to you.


Thank you,


Frank

---

### Post by bodhi.zazen on 2008-05-18
where are you trying to copy the file to ?

---

### Post by Xiong Chiamiov on 2008-05-18
> **franky_88 said:**
> How do I have total permission in ubuntu?? I am the one who installed ubuntu on my laptop. I tried the gksudo nautilus command but it gives me the error: cant copy because location not mounted. If you need additional information please tell me what you need and I will give it to you.


Thank you,


Frank
Even though you are the only user on your system, there is actually a hidden user (root) who has special priviledges that you do not.  Because of the way Ubuntu works, instead of having separate user accounts (like an administrator and limited account in Windows), you only have one account - yours.  When you need to do something as root, however, is when you have to use the sudo command (or its cousins, gksudo and kdesudo).
Have you tried just
```

gksudo nautilus

```

---

### Post by franky_88 on 2008-05-18
I am trying to copy files from my external Hard Drive to my Hard Drive in my computer. I want to copy the entire folder containing the files in \home\francis\video. I have to mention that my external Hard Drive is on my home network. I recently checked, and I have total permission to copy the folder.




Thank you,



Frank

---

### Post by dislocated on 2008-07-11
This seems to be a known bug. I have the same problem, and here is my workaround:

I installed the file "Dolphin" file manipulation program, and it doesn't seem to have any problem moving external folders around. It must be a bug in Nautilus and not in Samba.

Hope this helps.

Reference: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/185729](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/185729)

---

### Post by dislocated on 2008-07-12
After having played with the problem a little more, I've discovered that if I modify the /etc/fstab file and permanently mount the external drive, then Nautilus doesn't seem to have any problem in copying the folders any more.

My NAS is located at //192.168.1.100/ and I wanted to mount it at /media/backup so this is what I added to fstab:

```
//192.168.1.100/Volume_1 /media/backup cifs guest,uid=1000	0	0
```

It works like a charm now!

---

