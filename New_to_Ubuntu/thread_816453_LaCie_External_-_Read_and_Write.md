---
title: "LaCie External - Read and Write"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by thebarefootmarauder on 2008-06-02
I just bought a LaCie 320 GB external hard drive.  I can't get Ubuntu to let me write on the disk.

I think I may need to change the permissions or format it but I don't know how.

Help?

---

### Post by shifty_powers on 2008-06-02
have you got gparted installed?

---

### Post by meistercobbman on 2008-06-02
i have a similar issue. YES i have gparted installed, and i just used it to change my external hd from NTFS to ext2 filesystem. however now i can't write to it because i don't have permissions. i don't know how to change permissions on the drive. please help. thanks!

---

### Post by crossedout on 2008-06-02
You can change the mount point by doing this:

```
sudo chown -R LoginName:LoginName /MountPoint/LaCie
ls -la /MountPoint
```

'MountPoint' is generally /media, so it would be /media/LaCie.  You'll have to adjust it based on your mount point.

 
-Xout

---

### Post by meistercobbman on 2008-06-02
works like a dream thanks!

---

### Post by gingerana on 2010-01-08
Hello, I'm having a similar problem with my lacie drive. I am running MAC os 10.4.11 and have been using this drive for about 3 months. Recently it mysteriously changed from read/write to only read. With that change the partition has vanished. 
Any thoughts on how I can restore my drive?
I'm not computer savvy so please give me a step by step like you're talking to a 4 year old. 
Thanks.

---

