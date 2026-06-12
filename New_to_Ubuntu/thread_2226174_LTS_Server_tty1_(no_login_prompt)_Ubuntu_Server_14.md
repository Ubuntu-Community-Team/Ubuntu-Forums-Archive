---
title: "LTS Server tty1 (no login prompt) Ubuntu Server 14.04"
date: 2014-05-25
forum: New to Ubuntu
---

### Post by mike196 on 2014-05-25
I'm pretty much brand new to Ubuntu/Linux, so I don't really know where to begin troubleshooting beyond a simple google search.




First, my specs:


Western Digital Caviar 500 gb WD5000AA/KS-00   
Western Digital Caviar 100 gb WD1000BB/00CA
AMD Athlon 64 X2 dual core 3600+
MSI V Class k9VGM-V
G skill pc2 6400 2 GB RAM
no video or sound card


I'm trying to install Ubuntu Server 14.04.  I think I've successfully installed it, but when I boot up, I get a black screen that says LTS Server tty1.  It doesn't ask me for my login or anything.  If I try to type commands in, it hangs there for a minute or two, then goes back to LTS Server tty1.  A google search yields nothing I really understand.  Where can I start trouble shooting this?

---

### Post by cariboo on 2014-05-28
Try starting the server with nomodeset enable, at the grub menu, press **e**, then scroll down to the line starting with linux  and add nomodeset to the end of the line, if the system boots successfully to a login prompt, you can add the option to /etc/default/grub:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```

---

### Post by mohammad_ali2 on 2014-05-28
Is it showing this from first install?

---

### Post by mastablasta on 2014-05-28
how are you connecting to the server if you have no video on it? via SSH?

how did you install it? any special/advanced options selected during install?

---

### Post by mike196 on 2014-06-18
Thread name not accurate for current problems. Starting new thread.

---

