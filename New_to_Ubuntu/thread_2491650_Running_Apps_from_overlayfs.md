---
title: "Running Apps from overlayfs"
date: 2023-10-16
forum: New to Ubuntu
---

### Post by syn0ptic on 2023-10-16
Hi there! I've just found a cool video (in Spanish but you can turn on English subtitles)

[https://youtu.be/0fBd1zDcMzg?si=BM9IkZrLNO4ATNSk](https://youtu.be/0fBd1zDcMzg?si=BM9IkZrLNO4ATNSk)

sudo mount -t overlay overlay -o lowerdir=/,upperdir=/tmp/p,workdir=/tmp/w /mnt
sudo chroot /mnt
sudo apt install htop

I do the same as it's shown in the video, but when I try to install the app I'm getting this ugly Error:

```
Ign:1 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 htop amd64 3.0.5-7build2
Ign:1 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 htop amd64 3.0.5-7build2
Ign:1 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 htop amd64 3.0.5-7build2
Err:1 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 htop amd64 3.0.5-7build2
  Temporary failure resolving 'us.archive.ubuntu.com'
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/h/htop/htop_3.0.5-7build2_amd64.deb  Temporary failure resolving 'us.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

What do I do wrong?
Thanks in advance!

Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.3 LTS
Release:    22.04
Codename:    jammy

---

### Post by TheFu on 2023-10-16
>  maybe run apt-get update 

Could be that your repo list doesn't exist after the chroot crap.    I won't pretend to understand the point of this exercise. There are enterprise proven solutions for merging multiple disks into a single file system. That's what LVM is for and it has been around and used inside enterprises for nearly 25 yrs now.

Generally, when setting up a chroot, a number of directories need to be included separately, but perhaps what you are attempting is pure genus.  I can't tell.

Regardless, you posted this in the new-to-ubuntu subforum and doing things like this really isn't for people new to Linux. I suspect the thread needs to be moved somewhere else.

---

