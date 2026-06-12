---
title: "access to samba server from application"
date: 2017-03-07
forum: New to Ubuntu
---

### Post by Dominik_Hartwich on 2017-03-07
hello,
i did the simple samba server (sda1) on openwrt.
From ubuntu file manager (files) there is no problem to connect to this share.
But how to do it from other application to save documents (for example) - where does ubuntu store this directory?
Checked /media and /mnt and my knowledge is really insufficient...

regards,
dOMI

---

### Post by HereInOz on 2017-03-07
Hello,

Any application which uses nautilus to open and save files should be able to connect to the samba share and save or open files on that share.  However, if an application has its own or a modified nautilus interface, such as Google Chrome, you could have a problem.

In that case, you could use nautilus to mount the samba share first, then the application may see that mounted share in its file manager, or mount the share in nautilus, then create a bookmark of it in nautilus.  Then, you may be able to see the bookmark in the application's file manager.  

Best I can offer.

---

### Post by SeijiSensei on 2017-03-07
You can "mount" the server's shares into the client's filesystem.  Then they will be available to all applications.  See [https://wiki.ubuntu.com/MountWindowsSharesPermanently#Mounting_unprotected_.28guest.29_network_folders](https://wiki.ubuntu.com/MountWindowsSharesPermanently#Mounting_unprotected_.28guest.29_network_folders) for details.

---

### Post by Dominik_Hartwich on 2017-03-12
That was the solution! Thx [**[COLOR=#000000]SeijiSensei[/COLOR]**]("https://ubuntuforums.org/member.php?u=698195")

---

### Post by SeijiSensei on 2017-03-12
You're welcome.  Please mark this thread [SOLVED] using the Thread Tools button at the top of the page.

---

