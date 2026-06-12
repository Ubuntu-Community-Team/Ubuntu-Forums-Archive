---
title: "unclean filesystem forcing busybox"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by yoma819 on 2008-08-06
i have just done a new install on my toshiba portiage m200 tablet.
i activated the nvidia drivers in the restricted drivers page and restarted
on restart it goes straight into busybox
so i went into recovery mode and it says
mount: mounting /dev/disk/by-uuid/7ee2d0f9e4d0b51d. on /root failed: sucess
could not mount the partition /dev/disk/by-uuid/7ee2d0f9e4d0b51d. this could also happen if the filesystem is not clean because of an operating system crash, an interupted boot process, an improper shutdown or unplugging of a removable device without first unmounting or ejecting it. to fix this simply boot into windows, let it fully start, log in, run chkdsk /r then gracefully shutdown and reeboot back into windows. after this you should be able to reboot again and resume the installation. (filesystem = ntfs, error code =15)
i have tried this but windows says it cannot access the partition "cannot open the volume for direct writing!"
i have only access to windows and busybox
and i cannot really do a full install as my laptop has no cd drive so i am having to start the installation from a pendrive in windows!
many thanks
--yoma

---

