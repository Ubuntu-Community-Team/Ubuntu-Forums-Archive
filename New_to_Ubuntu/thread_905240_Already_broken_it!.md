---
title: "Already broken it!"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by al_kaholik on 2008-08-30
Hi, 

Completely new to linux and have tried to do some tweaks to speed up my Uuntu 8.4 install.

I've changed the concurrency setting to "shell" but seem to have messed it up. The GUI will now not boot.

I was using the command sudo nano -w /etc/init.d/rc in a terminal window, but now trying to fix it from the command line am unable using the same method. I keep getting an error writing...:Read-only file system.

Have a hosed it already or is there a way to fix this?

Thanks all.

Al

---

### Post by Nepherte on 2008-08-30
A shell is more of a synonym for terminal console. So having no gui is in this case normal behaviour. This should work to fix the permission:
```
sudo nano -w /etc/init.d/rc
```

---

### Post by eru777 on 2008-08-30
Don't fix it if it ain't broke .

---

### Post by al_kaholik on 2008-08-30
> **Nepherte said:**
> A shell is more of a synonym for terminal console. So having no gui is in this case normal behaviour. This should work to fix the permission:
```
sudo nano -w /etc/init.d/rc
```


Using this command just flags up the same error message that the file system is read only

---

### Post by bumanie on 2008-08-30
Post the output of > cat /etc/fstab

---

### Post by cryptk on 2008-08-30
also, the output of this may help a little as well...


```
cat /boot/grub/menu.lst
```

---

### Post by al_kaholik on 2008-09-01
Now fixed this by doing a clean install of Ubuntu - however am now having graphics issues on my webbook

---

### Post by Alan Bell on 2008-09-01
Hi,
the graphics issue can be fixed by editing your xorg.conf file and setting the screen resolution to 1024x600. More details and an xorg.conf you can download are available [here on the webbook blog]("http://webbookblog.com/?p=171")

Alan.

---

