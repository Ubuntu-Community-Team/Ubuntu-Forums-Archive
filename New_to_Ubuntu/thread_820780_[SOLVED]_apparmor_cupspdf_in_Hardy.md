---
title: "[SOLVED] apparmor cupspdf in Hardy"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by ayu on 2008-06-06
Hello,
I just upgraded to Hardy, and cannot get my pdf printer to work anymore. I have set 

Out ${Home}/Desktop/
in /etc/cups/cups-pdf.conf

and changed PDF to Desktop in
@{HOME}/Desktop/ rw,
@{HOME}/Desktop/* rw,
in /etc/apparmor.d/usr.sbin.cupsd

Are there any other files I have to set so my default directory is my Desktop? Thanks!

---

### Post by kaibob on 2008-06-07
I followed post 12 in the following thread to change the cups-pdf directory:

[http://ubuntuforums.org/showthread.php?t=626718&page=2](http://ubuntuforums.org/showthread.php?t=626718&page=2)

Your apparmor entries differ a bit from what is shown in this post. I don't know if this makes a difference. Also, I don't have a "/" at the end of the path after Desktop. This shouldn't make any difference but you might want to try deleting it.

After changing the above files, you need to execute the following in a terminal window:

sudo invoke-rc.d apparmor reload

sudo invoke-rc.d cupsys restart

BTW, I just happened upon your post--perhaps you have this issue solved already.

---

### Post by ayu on 2008-06-08
> **kaibob said:**
> I followed post 12 in the following thread to change the cups-pdf directory:

[http://ubuntuforums.org/showthread.php?t=626718&page=2](http://ubuntuforums.org/showthread.php?t=626718&page=2)

Your apparmor entries differ a bit from what is shown in this post. I don't know if this makes a difference. Also, I don't have a "/" at the end of the path after Desktop. This shouldn't make any difference but you might want to try deleting it.

After changing the above files, you need to execute the following in a terminal window:

sudo invoke-rc.d apparmor reload

sudo invoke-rc.d cupsys restart

BTW, I just happened upon your post--perhaps you have this issue solved already.

Haha, I forgot to restart apparmor. Thank you very much!

---

