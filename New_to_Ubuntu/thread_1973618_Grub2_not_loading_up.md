---
title: "Grub2 not loading up"
date: 2012-05-05
forum: New to Ubuntu
---

### Post by aenaveen on 2012-05-05
I had Windows XP on C: 
Then I installed Windows 7 on D: but as my graphics card wasn't compatible with Windows 7 I used XP all the time using "Windows Boot Loader" which comes with Win7 which I think is on C: drive itself. 
Now, I installed Ubuntu 12.04 by deleting D: drive and creating a ext4 format. Which means my Win7 is gone, but I still have the Windows Boot Loader. 
What my problem is Ubuntu's Grub isn't showing up!, I tried reinstalling. Still not working, I searched on google there is no proper solution to this. So is there any way to open Grub2 from Windows Boot Loader, or Ubuntu itself from Windows Boot Loader. 

I am a mid-level user, I tried boot.ini editing, but don't know what to put in, so I would appreciate any help at all to get started upon Ubuntu. :)

---

### Post by 2ta8gdfte on 2012-05-05
Using a live ubuntu cd download this script extract it to your desktop and run this command and post the results.text that will appear on the desktop. This will give us info needed.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```

---

### Post by loseby on 2012-05-05
have something similar  ... would it be considered bad form to post the results of that test in this thread or should I start a new one

---

### Post by aenaveen on 2012-05-05
Its working now...  
I changed the order of boot in BIOS settings, the D: was on different hard disk. Now its working. :) 
Thanks for the help anyway.

---

