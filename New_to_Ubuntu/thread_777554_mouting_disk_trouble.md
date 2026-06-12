---
title: "mouting disk trouble"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by onus on 2008-05-01
how come it is that when either i slave a hard drive to one w/ an ubuntu OS or mount a partition... it is read only... how do you mount it so that you can write on it. would be greatly appreciative. thanxs

-onus

---

### Post by neurostu on 2008-05-01
how are you mounting it? Are you mounting with sudo?  What you need to do is give ownership of the drive to you

```

sudo chown <username> <directory>
sudo chown me /media/MountedDrive

```
try that then try
```

sudo chmod +w <directory>

```
then you should be able to write to the directory (mounted drive)

---

### Post by onus on 2008-05-02
onus@onus-desktop:~$ chown onus /media/disk
chown: changing ownership of `/media/disk': Operation not permitted
onus@onus-desktop:~$ sudo chown onus /media/disk
onus@onus-desktop:~$ su chown onus /media/disk
Unknown id: chown

even though it said not permitted... it worked. your awesome thank you so much!

---

### Post by neurostu on 2008-05-02
```

chown: changing ownership of `/media/disk': Operation not permitted

```
You must be root to do this, (You need to use sudo)

```

onus@onus-desktop:~$ su chown onus /media/disk
Unknown id: chown

```
su is the command to login as root, You only need to use sudo

---

### Post by neurostu on 2008-05-02
If you want you can publically thank people by clicking the little star on the bottom right corner of a post (just for future reference)

---

