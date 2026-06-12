---
title: "copying remotely - permission denied"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by ben22 on 2008-04-24
Hi,

with the following command I want to copy files from a MAC to Ubuntu PC using terminal:

```
$ scp -r folder_to_copy ben@192.168.0.142:/ben/backup
```

>> I get the error permission denied.

The passwords  etc are correct, since with the same credentials I can SSH the Ubuntu pc from the mac.

Do I need to access via root the Ubuntu PC to be allowed to copy?

thx,
Ben

---

### Post by swoll1980 on 2008-04-24
try putting sudo in front of the command sudo scp -r folder_to_copy ben@192.168.0.142:/ben/backup see if that helps

---

### Post by prshah on 2008-04-24
> **ben22 said:**
> Hi,
```
$ scp -r folder_to_copy ben@192.168.0.142:/ben/backup
```
>> I get the error permission denied.


Does your remote folder /ben/backup have permissions allowing user "ben" to write/access the folder? If the backup folder is in ben's home folder, then the correct path will be "/home/ben/backup" or just "~/backup".

---

### Post by ben22 on 2008-04-24
> **swoll1980 said:**
> try putting sudo in front of the command sudo scp -r folder_to_copy ben@192.168.0.142:/ben/backup see if that helps

Hi, I tried with sudo, but still get "permission denied" - sudo would also give root rights to the local user, but not to the user at the Ubuntu pc I would like to connect I guess?

---

### Post by ben22 on 2008-04-24
> **prshah said:**
> Does your remote folder /ben/backup have permissions allowing user "ben" to write/access the folder? If the backup folder is in ben's home folder, then the correct path will be "/home/ben/backup" or just "~/backup".

high thx, I forgot the ~ in the URL.

---

### Post by ben22 on 2008-04-24
Now I succeed in copying 1 file (the only one) that is in the folder, but not the complete folder itself. 

What is the correct command for copying the complete folder?

```
$ scp -r folder_to_copy ben@192.168.0.142:/ben/backup
```

---

