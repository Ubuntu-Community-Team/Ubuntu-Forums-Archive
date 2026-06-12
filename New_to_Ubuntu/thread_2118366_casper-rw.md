---
title: "casper-rw"
date: 2013-02-21
forum: New to Ubuntu
---

### Post by Lespoodurr on 2013-02-21
whenever i try to mount casper-rw it then tells me that it is unable to mount it

Adding read ACL for uid 999 to `/media/ubuntu' failed: Operation not supported



error message above

---

### Post by NikTh on 2013-02-21
Hi , 

please read this thread that might helps
[http://ubuntuforums.org/showthread.php?t=1028564](http://ubuntuforums.org/showthread.php?t=1028564)

Thank you

---

### Post by Lespoodurr on 2013-02-21
i've done that but it just tells me that the casper directory is already made

in fact, none of the drives can be mounted they all give me the above error message

---

### Post by NikTh on 2013-02-22
Hi,
this seems to me like a permissions problem. 
> **Lespoodurr said:**
> 
in fact, none of the drives can be mounted they all give me the above error message

Have a look here
[http://askubuntu.com/questions/202630/cant-mount-any-partitions-acl-error](http://askubuntu.com/questions/202630/cant-mount-any-partitions-acl-error)

Thanks

---

### Post by Lespoodurr on 2013-02-24
okay, now i can mount other drives but i can't mount casper
it now gives me this error message:

Device /dev/loop1 is already mounted at `/media/ubuntu/casper-rw'.

---

### Post by NikTh on 2013-02-26
Hi ,
have you tried to open the folder ? /media/ubuntu/casper-rw 

For clarification , you cannot mount the casper-rw when you are IN from the Live-Usb with the persistent space. 

Thanks

---

### Post by C.S.Cameron on 2013-02-26
You need to plug the Persistent flash drive into a computer running Linux in order to mount casper-rw.
You can not mount it if you are running from the Persistent drive.

---

