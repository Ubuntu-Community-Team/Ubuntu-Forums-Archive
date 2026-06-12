---
title: "How To Fix Mounting USB Flash Drive Problem in KDE 3.5"
date: 2005-12-13
forum: Outdated Tutorials &amp; Tips
---

### Post by mamato on 2005-12-13
When I upgraded my system to KDE 3.5, i met some problems to mount my usb drive automatically. When I go to media:/ it always return no such device. 
At last, I found the solution :p 
1. Open your ```
/etc/fstab
``` using your favourite editor. 
    Ex: ```
sudo kate /etc/fstab
```
2. Add these lines into the fstab file :
    > 
sysfs		/sys 		sysfs 	defaults 	0	0
usbfs 		/proc/bus/usb 	usbfs  	defaults 	0 	0
none 		/dev/shm 	tmpfs 	defaults 	0 	0
none		/dev/pts 	devpts 	defaults 	0 	0
    
3. reboot.
4. That's all folks
Hope that's help.. :D

---

### Post by TheEHMan on 2005-12-31
You are THE MAN!!!  I added those lines to fstab and now I can r/w to my flash drive w/ no problems.  Tried unmounting, then plugging back in.....no problems.
Thanks for your help!!

---

### Post by geppy on 2006-01-25
Thank You. :)

---

