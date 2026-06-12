---
title: "error: file not found. grub rescue&gt;"
date: 2014-10-01
forum: New to Ubuntu
---

### Post by akross6966 on 2014-10-01
Hello all!  I had to restart my server tonight and am now receiving the message "error: file not found. grub rescue>" when it tries to boot off the drive.  I am running Ubuntu 12.04 LTS x64 server.  Everything has been working great.  Not sure what could have happened.  I did try and run the boot repair and received the URL [http://paste.ubuntu.com/8470617](http://paste.ubuntu.com/8470617).  Any help would be appreciated.

Thanks.

---

### Post by yancek on 2014-10-01
The boot repair script will usually show the grub files on whichever partition they exist.  The only partition they could be on on your system is sda1 and nothing shows.  At the bottom of the boot repair it indicates that it is unable to find the grub files.  Not knowing what happened before the reboot, it's pretty difficult to say what the resolution to the problem is.  The Grub files do not appear to be where expected, the /boot/grub directory, no /etc/fstab is found and the "/lib/grub/i386-pc/grub-install" script can't be found.

---

