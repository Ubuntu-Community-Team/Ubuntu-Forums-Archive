---
title: "Can't share media drive"
date: 2012-08-27
forum: New to Ubuntu
---

### Post by Mrs Twaddle on 2012-08-27
I just upgraded to 11.10, and I am having trouble with my second hard-drive.
I use it just to keep all the media on, which is then accessable by all users.

I have never had trouble with this before, so cannot understand why I cannot do it now.
Any kind of adjustment in the permissions won't stay as I want, even if i go in as root.

I don't want it to mount on start up, and it doesn't need to be shared on the network. 
Just mount when someone needs anything on that drive.
perviously you could click and it would mount, and pop open.
Now, I am the only user that can do that, and I can't adjust the permissions for the 2 other users on my pc to do that too.

Any help would be appreciated.

---

### Post by Gone fishing on 2012-08-27
Is it an ntfs partitioned drive? in which case it will need the permisions set in fstab you could hand edit or use MountManager in the software centre.

---

### Post by Mrs Twaddle on 2012-08-28
No, it's fat32.
I tried mountmanager, but must have done something wrong as it wouldn't boot properly after using it.
I got in, adjusted fstab and it now mounts the drive to mnt/sdb1 and is accessible by all users, at least to read. Not tested writable yet.

Now I need to make it easy to get to for all users. Best way would be a shortcut in the unity sidebar, or a link on the desktop.

---

### Post by Mrs Twaddle on 2012-08-28
No one has write permissions on that drive, not even me. LOL.
here is what is in my fstab
> UUID=11343475-e675-4d43-b680-1b18b57d9b55 / ext4 defaults 0 1
UUID=1bf7ba2f-30a5-48cf-8487-41d0d4d2afdf swap swap sw 0 0
UUID=8C68-E4AF /mnt/sdb1 vfat users 0 0

---

### Post by Gone fishing on 2012-08-28
I think what you need in your fstab is

UUID=8C68-E4AF /media/shared vfat defaults,user,exec,uid=1000,gid=100,umask=000 0 0

after you have made the directory /media/shared ```
sudo mkdir /media/shared
``` then it should be read write and on the side bar

---

### Post by Mrs Twaddle on 2012-08-29
cheers I'll give it a shot

---

