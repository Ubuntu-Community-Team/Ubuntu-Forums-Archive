---
title: "How do make and use a new partition?"
date: 2012-05-05
forum: New to Ubuntu
---

### Post by KongKNoob on 2012-05-05
I've got an Ubuntu 10.11 system (64-bit) on a 1 TB disk. When I installed Ubuntu I made the rather silly decision to only use 500 GB of the disk. I thought I'd use the other half for other distros or something, and who really need all that space, right? Turns out, I do.

What I want is to partition the unused 500 GB, and move all my movies/music/photos there. Formatting and making a new partition is no problem, but how should I name it (which path)? How do I make it automount? How do i make it easily available to both users and Mediatomb (media server)?

---

### Post by datenhalde on 2012-05-05
You can mount it anywhere you want. You can just create a new empty directory somewhere, mount the new partition there and copy all the data to there. As soon as you're sure that everything's ok with it you can empty the old directory, umount the new partition and remount on the directory where your data had been before. 
To make it automount you have to create an entry in /etc/fstab. Have a look at the entries already in the file to learn about the syntax(plus "man fstab"). Should look something like that (fill in your values, of course): 

/dev/sda2    /home/user/videos4example    ext4    defaults    0    0

Be careful with that file, though, if you mess it up, your system won't boot cleanly. 
File permissions on the new partition: 
If you want two users to have access there, you could do something like that:
Assuming both users are members of group "users" you can do chown -R user1:users /path/to/new/partition && chmod -R g+rwX /path/to/new/partition

For mediatomb I can't give you any advice. If it wants to access your partition(s) with smb, you'd have to create a share in your /etc/samba/smb.conf, I guess.

---

### Post by KongKNoob on 2012-05-21
Thanks! I haven't found time to mess around with this yet, but hope do do so soon...

---

