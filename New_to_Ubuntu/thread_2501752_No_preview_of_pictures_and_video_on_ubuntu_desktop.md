---
title: "No preview of pictures and video on ubuntu desktop"
date: 2024-10-19
forum: New to Ubuntu
---

### Post by enigma20100 on 2024-10-19
Why is it that  neither Ubuntu 24,4 or ubuntu 24.10 shows previews of pictures and videos on the desktop anymore. ?   it worked perfectly fine on Ubuntu 23.10 so what happend.? and why hasent it been fixed?

---

### Post by Dennis N on 2024-10-19
Image thumbnails should show (see attached image of a test) when set to do so. For a video, I see a 'play' icon only. Whether to show image thumbnails is enabled in Files > Preferences, and also the on/off setting of 'show image thumbnails' in the 'Desktop Icons NG' gnome-shell extension. The extension itself must also be 'on'. 

System: Ubuntu 24.04 LTS

---

### Post by him610 on 2024-10-19
Perhaps you are thinking about iconified file settings in your files application. This is what I get using thunar (Xubuntu)- This is a jpg file....
[ATTACH=CONFIG]294394[/ATTACH]

---

### Post by enigma20100 on 2024-10-19
you sure you are on the newest version of ubuntu?   it simply doesnt work.

---

### Post by him610 on 2024-10-19
Files as icons...
```

Linux ma90x 6.8.0-45-generic #45-Ubuntu SMP PREEMPT_DYNAMIC Fri Aug 30 12:02:04 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 24.04.1 LTS
Release:	24.04
Codename:	noble
XFCE

```

---

### Post by tristanvillers on 2024-11-21
Hello. Same problem here. Except removing "cache", nothing is working. New pictures don't show thumbnails on desktop.
Ubuntu 24.04.1 on P50 Lenovo, driver Nvidia enabled.
regards

---

### Post by thetuc on 2024-11-27
hello same problem here 
tried that solution below,  found on 'ask ubuntu' which seems to work for some people but not for me 


Add "GSK_RENDERER=gl" to /etc/environment file
Run rm -rf ~/.cache/thumbnails/fail
Either restart or execute sudo systemctl restart gdm.service

---

### Post by him610 on 2024-11-28
Don't know if it will work for you or not, but try it anyway - from your in-focus file manager (whatever it may be),
*Ctrl 3, Ctrl 2, Ctrl 1*

Ctrl 1 should show iconified files

---

