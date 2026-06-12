---
title: "Cannot access my encrypted home folder using Live USB"
date: 2016-01-25
forum: New to Ubuntu
---

### Post by Kallipygian on 2016-01-25
I have messed up my laptop to the point where I cannot boot into grub. I  have been struggling since past two days to get it right but to no  success. I had an excrpted drive with encrypted home folder. Now I just  want to recover data from my /home drive and go ahead with fresh  install. It seems even this not an easy option which is evident from the  steps below.

Step 1: Mount the /dev/sda3 on /mnt
```

cryptsetup luksOpen /dev/sda3 linux
Enter passphrase for /dev/sda3: 

```  

```
          
mint ~ # sudo mount /dev/mint-vg/root /mnt
mint ~ # sudo mount -o bind /dev /mnt/dev
mint ~ # sudo mount -o bind /dev/shm/ /mnt/dev/shm
mint ~ # sudo mount -o bind /proc /mnt/proc
mint ~ # sudo mount -o bind /sys /mnt/sys 

```

Step 2: Chroot to my broken / folder

 ```
          
mint ~ # sudo chroot /mnt /bin/bash
mint / # su - kalli
open: Permission denied
Error locking counter 

``` 

Step 3: Mount /home folder using ecryptfs-mount-private utility
```

kalli ~ $ ecryptfs-mount-private
Enter your login passphrase:
Inserted auth tok with sig [] into the user session keyring
open: Permission denied
Error locking counter 

```
I am pretty sure that my passphrases are alright but I do not seem to  understand what is causing this problem. Please help me find recover my  data.

---

### Post by sandyd on 2016-01-25
Hi,

Seems to be the same issue as [https://bugs.launchpad.net/ecryptfs/+bug/573518](https://bugs.launchpad.net/ecryptfs/+bug/573518)

Maybe try ecryptfs-recover-private?

Exit the chroot and run
```

ecryptfs-recover-private /mnt/home/.ecryptfs/*username*/.Private/
```

Replace *username* with your username

---

