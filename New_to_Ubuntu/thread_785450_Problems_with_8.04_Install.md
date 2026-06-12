---
title: "Problems with 8.04 Install"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by Thewinch987 on 2008-05-07
Hey all,

This morning I installed Hardy on my desktop with no problems. I ran it for about 5 minutes and then started to upgrade drivers and software. After the updates I restarted and now the login screen will not come up. Grub still loads fine, but I can't get to the actual Ubuntu login screen. I am running:
2.6 ghz p4
1.25 gb ram
ATI Raedeon 2600 Pro AGP

any help would be greatly appreciated. 

Thanks

---

### Post by TeoBigusGeekus on 2008-05-07
Reboot and enter recovery mode in grub. Then type
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Perhaps it is a graphics problem...

---

### Post by Thewinch987 on 2008-05-07
We entered that in and it told us 
> sxerver-xorg postinst warning: overwriting possibly-customized cofiguration file; backup in /etc/x11/xorg.conf .20080507121129

Do we continue with normal boot now, or is there another command we should use?

Thanks

---

### Post by TeoBigusGeekus on 2008-05-07
Continue with normal boot. Type 
```
reboot
```
and post us what happened.

---

### Post by Thewinch987 on 2008-05-07
Grub still loads, and it seems like the whole startup is progressing (ie. internals blink indicating access, so does the floppy drive). ALRIGHT! it started up. Thank you so much.

Now will the graphics drivers still work for the ATI or did that undo what we had changed with the ATI drivers?

TIA

---

### Post by TeoBigusGeekus on 2008-05-07
It was probably a problem with the restricted drivers.
Try to enable them again and see what happens.

---

### Post by Thewinch987 on 2008-05-07
It freezes on a black screen before the login screen comes up for ubuntu. I did some snooping around and it seems that alot of people have to manually configure ATI cards. Should that be our next step?

---

### Post by TeoBigusGeekus on 2008-05-07
Unfortunatelly yes!!!
I can't help you on that one - when I tried to install Ubuntu on a Ati 1950Pro I finally switched to an nvidia 6600GT. And this is my only contribution to this problem: if you can get your hands on an nvidia card, DO IT!!!

Good luck...:)

---

### Post by Thewinch987 on 2008-05-07
Well thanks for all your help. It looks like a few people have gotten it to work and since I'm a poor college student I will spend the rest of the afternoon screaming and banging my head against the wall to get this to work. Thanks for the advice about the Nvidia card, though.

---

