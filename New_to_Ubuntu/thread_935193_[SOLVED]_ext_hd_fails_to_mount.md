---
title: "[SOLVED] ext hd fails to mount"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by satipera on 2008-10-01
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/hd-ntfs -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/hd-ntfs ntfs-3g force 0 0


help I have tried all this:confused:

---

### Post by Paqman on 2008-10-01
> **satipera said:**
> 
help I have tried all this:confused:

The problem is that the drive wasn't cleanly shut down at some point, so it has a flag set on it that prevents it from mounting.

Do you have Windows? If so, just try booting it up and then shutting it down. You should then be able to mount your drive in Ubuntu.

---

### Post by satipera on 2008-10-03
thanks paqman I was dual booting but got rid of xp all together, I changed the ownership of the disc and all is fine now.

---

