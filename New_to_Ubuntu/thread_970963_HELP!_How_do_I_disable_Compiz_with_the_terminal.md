---
title: "HELP! How do I disable Compiz with the terminal???"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by bronner on 2008-11-04
Hey,

I accidentally put two conflicting settings together on Compiz, now I can't login without it bringing me back to the login screen. The only thing I can access is Terminal mode...

...how do I fix this?

---

### Post by philinux on 2008-11-04
metacity --replace

---

### Post by bronner on 2008-11-04
im running in failsafe terminal, it's not working...everytime i try to login regularly it just gives me a messed up screen then brings me back to the login

---

### Post by bronner on 2008-11-04
like, every time i try to login, i get a black screen with a few lines running down it that change colors then it takes me back to the login screen, the failsafe terminal won't let me exit it after i type in the metacity --replace and then when i close it it just takes me right back to the login... im using 8.10 on an acer aspire one

---

### Post by LowSky on 2008-11-04
as far as I know Compiz can run two conflicting things at the same time, it will make you choose one over the other.

Maybe trying to run recovery mode and repair Xorg, which is what I think you really messed up.

---

### Post by bronner on 2008-11-04
how do i repair xorg in recovery?

---

### Post by LowSky on 2008-11-04
recovery mode has changed for the old days, just choose recovery from Grub, then  I think 4 choices pop up, one will be to repair xorg, doing so will ask you to reset up all your settings, its very simple

---

### Post by bronner on 2008-11-04
ok i went into recovery mode under generic then i selected 'try to fix broken xserver' i think it said, but it didn't help, i still can't login

---

### Post by bronner on 2008-11-04
then in failsafe terminal, i type "metacity --replace" and it just hangs there....this all started happening when i was playing with the compiz advanced settings thing

---

### Post by bronner on 2008-11-04
i guess im just going to have to wipe the hard drive and start all over...i cant login

---

### Post by Separ on 2008-11-04
Before you do, try booting into a root recovery console and typing ```
dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by bronner on 2008-11-04
I FIXED IT!!!

Boot in rescue mode
select root shell prompt
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit
resume

and im back in!

---

### Post by dracayr on 2008-11-04
BTW: the 1. page that google shows when searching for "disable compiz CLI" (without the quotes):

[http://mteixeira.webset.net/blog/20071129/enablingdisabling-compiz-from-command-line/](http://mteixeira.webset.net/blog/20071129/enablingdisabling-compiz-from-command-line/)

---

