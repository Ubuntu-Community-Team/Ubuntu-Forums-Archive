---
title: "Invalid resolution - user error"
date: 2012-12-21
forum: New to Ubuntu
---

### Post by Crossbow on 2012-12-21
First, I am virtually computer illiterate. 

I was screwing around with my resolution settings and got one that couldn't be displayed. Apparently, somehow, I hit "apply" and now I can't get any display at all. Just a black screen saying something like "video mode can not be displayed." I assume I can fix this from the console but I don't know how. I searched the threads for other resolution problems but they were all about driver problems not operator errors. The driver must be fine because I am not having the problem on my "guest" log in. 

Ubuntu 12.04
Dell Inspiron 530
Nvidia 173

PS. I did boot in recovery mode from the grub menu. I thought I could use the failsafe graphics mode but that just gave me a screen full of error messages and terminated.

---

### Post by Crossbow on 2012-12-26
No one?

I wonder if attaching it to a television would work. Or if I removed and reinstalled the graphics driver from another log in.

---

### Post by NikTh on 2012-12-26
> **Crossbow said:**
>  I assume I can fix this from the console but I don't know how. I searched the threads for other resolution problems but they were all about driver problems not operator errors. The driver must be fine because I am not having the problem on my "guest" log in. 

Hi , 

do you have an xorg.conf file inside /etc/X11/ folder ? 

See 
```
sudo nano /etc/X11/xorg.conf
``` 

and search for modes .. 

I don't know the procedure exactly , but you can correct the problem from there..
 OR
simple, remove the xorg.conf file and create another.. 

```
sudo rm /etc/X11/xorg.conf
```
```
sudo nvidia-xconfig
```

Thanks

---

