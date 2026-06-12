---
title: "Shutting Down Ubuntu 18.04 LTS Guest in VMWare Workstation 14 removes shared folder"
date: 2018-07-11
forum: New to Ubuntu
---

### Post by stardawg on 2018-07-11
I am using open-vm-tools coming with Ubuntu 18.04 LTS
Firstly I didnt have a hgfs folder so i created one in /mnt directory. Then I did
```
/usr/bin/vmhgfs-fuse .host:/ /mnt/hgfs/shares -o subtype=vmhgfs-fuse,allow_other 
```

and it works fine. I also ran the command again and mounted it in another location on the file system

```
/usr/bin/vmhgfs-fuse .host:/ /home/user1/shares -o subtype=vmhgfs-fuse,allow_other 
```

This works fine If I suspend the guest, it reloads the shared folders from host. The problem is when I shut down the guest, it doesnt remember the shared folders.
If I try vmhgfs-client in terminal it shows the shared folder so why can't I see it?
I presume this isn't really a big deal at the moment. Can someone offer some help?
Thank you.

---

### Post by wildmanne39 on 2018-07-11
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by yancek on 2018-07-12
If you booted the Ubuntu iso in VMWare and then proceeded to install it and subsequently have these errors (not retaining a mount) you may simply need an entry in fstab for it.  Not sure I'm reading the problem correctly.

---

### Post by stardawg on 2018-07-14
Found a fix for this [https://gist.github.com/darrenpmeyer/b69242a45197901f17bfe06e78f4dee3](https://gist.github.com/darrenpmeyer/b69242a45197901f17bfe06e78f4dee3) and you may need [https://forums.fedoraforum.org/archive/index.php/t-144176.html](https://forums.fedoraforum.org/archive/index.php/t-144176.html)

You need to use auto instead of noauto and the rc local file step is not needed. So far its good for me i can now shut down guest and i will see the shared folder from host. Thank you yancek.

---

