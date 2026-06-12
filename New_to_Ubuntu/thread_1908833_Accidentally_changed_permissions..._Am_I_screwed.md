---
title: "Accidentally changed permissions... Am I screwed?"
date: 2012-01-14
forum: New to Ubuntu
---

### Post by WongFuChu on 2012-01-14
I had two tabs open, both where I typed in "sudo -s". In one tab, I was in a different directory where I had to execute "chmod 755 *" In the other tab, I was messing with the brightness by doing "echo 1000 > /sys/class/backlight/intel_backlight/brightness". I accidentally executed "chmod 755 *" in two this tab. I never changed directories in this tab and I didn't do it recursively or use "-R" with chmod. Did I mess up? I encrypted my home folder during installation, but would chmod affect anything or make my files more/less secure/accessible? If I did ****, is there anything I can do to fix it? I'm scared to log out now..

---

### Post by ajgreeny on 2012-01-14
The command ```
sudo -s
``` would have got you to *root@hostname*, not your home folder, so I think you could be in trouble.

However, rather to my surprise, when I used **sudo -s** and then checked the permissions of all the files/folders from there with ```
ls -l
``` it showed the permissions of the contents of my /home folder, not /root.  I am therefore  wondering if you have only changed the permissions of something in your home to 755, which will not be a problem.

I'm afraid I shall have to defer to greater minds than mine to sort this out for you.

---

### Post by KdotJ on 2012-01-14
If you didn't change directories before or after executing **sudo -s**, then you should just of been in your home folder where 775 should be fine.

Others will confirm for sure.

---

### Post by HermanAB on 2012-01-14
Howdy,

The /sys directory is not a real directory on the HDD - it is a status and configuration 'virtual' directory for kernel parameters.  So whatever you did there doesn't matter and if it did affect anything, a reboot will fix it.

---

### Post by WongFuChu on 2012-01-15
> **ajgreeny said:**
> The command ```
sudo -s
``` would have got you to *root@hostname*, not your home folder, so I think you could be in trouble.

However, rather to my surprise, when I used **sudo -s** and then checked the permissions of all the files/folders from there with ```
ls -l
``` it showed the permissions of the contents of my /home folder, not /root.  I am therefore  wondering if you have only changed the permissions of something in your home to 755, which will not be a problem.

I'm afraid I shall have to defer to greater minds than mine to sort this out for you.

I also noticed this to check if I changed permissions of anything at /. But just in case, I double checked my Ubuntu install on an older laptop I had. Didn't see any difference in permissions at / and at /home/user. I always thought sudo -s automatically changed directories to /root. Guess I was wrong and worried for nothing.

---

