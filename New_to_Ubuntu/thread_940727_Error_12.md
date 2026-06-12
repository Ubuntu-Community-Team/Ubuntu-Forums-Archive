---
title: "Error 12"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by uppidada on 2008-10-07
I've re-installed windows  
1.I actually had 1.xp (sp2)+ 2.Ubuntu in my HDD
2.when i've re-installed windows,now when i restart,i'm jus able to directly go to windows(No grub error comes..)
3.How to get my grub back..
 I've done following steps using live cd
    Open Terminal
1.sudo grub
2.grub>find /boot/grub/stage1
(hd0,2)
3.grub>setup (hd0)
Error 12:Invalid device requested


plz help me with this problem...

---

### Post by cek on 2008-10-07
I think you have to use the root command first:

root(hd0,2)

setup(hd0)

---

### Post by HellNoire on 2008-10-07
[http://geocities.com/supergrubdisk/](http://geocities.com/supergrubdisk/)

This might be a little easier. I've yet to try it but it looks like it will work well.

---

### Post by uppidada on 2008-10-07
Thnakx that has worked fine... 
 Also do temme how do i install new graphic card...

---

### Post by HellNoire on 2008-10-07
Depends on what card. With some you can plug in and Ubuntu will get you the drivers.

---

