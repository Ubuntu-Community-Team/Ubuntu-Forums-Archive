---
title: "I'm pulling my hair out!"
date: 2007-12-29
forum: Other OS Talk
---

### Post by HappyFeet on 2007-12-29
i have spent many hours researching how to mount/read-write a ntfs partition/drive in debian. i'm beginning to think it's impossible. i've tried so many things that my head hurts. is there a ***definitive***  method that will work?

can someone give me a step by step how to achieve this? and maybe what my /etc/fstab should look like? 

like i said, ive tried  many web tutorials to get this done. i'm at my wits end.

---

### Post by sstusick on 2007-12-29
Install the ntfs-3g driver.

I'm not familiar with Debian, but it's in the repo's in Ubuntu.

---

### Post by HappyFeet on 2007-12-29
ok, ive installed ntfs-3g, fuse-utils, etc. i did mkdir /mnt/media, then mount /dev/sda1 /mnt/media

the drive opens up and says i dont have permission. how do i change that?

---

### Post by tbroderick on 2007-12-30
> **HappyFeet said:**
> ok, ive installed ntfs-3g, fuse-utils, etc. i did mkdir /mnt/media, then mount /dev/sda1 /mnt/media

the drive opens up and says i dont have permission. how do i change that?

Change the ownership or /mnt/media. Open a terminal as root or use sudo:

chown username:username /mnt/media

Or

sudo chown username:username /mnt/media

---

### Post by pelle.k on 2007-12-30
mount with gid=1000 (or is it 100 in debian?) and uid=1000, or with umask=000 (which is 666 permissions on all files and folders).
or use uid=1000 and umask=022 together to prevent other users to write to that file system.

---

### Post by HappyFeet on 2007-12-30
i tried   chown username:username /mnt/media   but it still says i dont have permission. what next?

---

### Post by pelle.k on 2007-12-31
Eh, i just gave you the answer?

---

