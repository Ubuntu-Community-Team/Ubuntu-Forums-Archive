---
title: "Mounting error popup when mounting Windows drive"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by 45acp on 2008-11-19
When I mount my Window drive (separate hdd) I get this notice:

Unable to mount locstion
internal error: No mount object for mounted volume.

The drive mounts OK. I am wondering what is causing this.

---

### Post by Titan8990 on 2008-11-19
Try using ntfs-3g to mount. So if you NTFS drive is /dev/sda1:

instead of:

sudo mount /dev/sda1 /media/sda1

you would do:

sudo ntfs-3g /dev/sda1 /media/sda1

---

### Post by 45acp on 2008-11-19
Thanks for the reply. I found a bug report #256749 on this. I have not tried to mount it with cli. Just Nautilus. Its annoying but it still mounts

---

