---
title: "Downgrading failed with `GLIBC_2.36' not found"
date: 2023-08-16
forum: New to Ubuntu
---

### Post by sash5 on 2023-08-16
Hello everybody
 
 
 I was downgrading from 22.10 to 22.04 and forgot to check the disk space, resulting to some system state that I can’t login any more.  

 
 
 If I try to boot with the last kernel I have 5.19.0-46 I’m getting Failed to execute /init (error -2) and kernel panic.


   
 If I try too boot with the kernel 5.19.-43 I’m getting by GUI login

  /usr/libexec/gdm-wayland-session[3395]: bash: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.36' not found (required by bash)

 or in a console

 e2scrub_reap[1513]: /bin/bash: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.36' not found (required by /bin/bash).

 
 
 I was booting from Ubuntu USB 22.04.03 and checking what version of /lib/x86_64-linux-gnu/libc.so.6 I have on my system and it is 2.34 the same as on the USB.

 
 
 What are the possibilities I have to restore the system?  

 
 
 Or I just simply rename my home and install Ubuntu over an old system and them rename home back that I have all my files and settings. In this case I need then to reinstall all the packages manually.

---

### Post by SeijiSensei on 2023-08-16
Downgrading is always problematic because of these kinds of issues with conflicting libraries.

Back up /home to a USB drive first.

Now install 22.04 and manually partition the drive. Create separate partitions for / (the directory root) and /home and restore the latter from the backup after the installation is complete. I usually use rsync for tasks like this since it knows about hidden ("dot") files. Then you can change the OS and keep /home untouched.

Allocate about 40-50 GB to / and the rest to /home. Choose ext4 filesystems when asked.

---

### Post by ActionParsnip on 2023-08-18
From the brain of the bot in the official irc channel for Ubuntu
[https://ubottu.com/factoids.cgi?search=Downgrade](https://ubottu.com/factoids.cgi?search=Downgrade)

---

