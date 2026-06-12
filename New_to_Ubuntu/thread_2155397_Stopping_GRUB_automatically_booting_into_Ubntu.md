---
title: "Stopping GRUB automatically booting into Ubntu?"
date: 2013-06-18
forum: New to Ubuntu
---

### Post by Zenithex on 2013-06-18
Hey Guys,
Does anyone know how to stop GRUB automatically booting into Ubuntu with 5/10s?
I am currently using a TV as a monitor and it can take 15/20s to turn on and switch to PC.
All help is appreciated,
Zenithex.

---

### Post by NikTh on 2013-06-18
> **Zenithex said:**
> Hey Guys,
Does anyone know how to stop GRUB automatically booting into Ubuntu with 5/10s?
I am currently using a TV as a monitor and it can take 15/20s to turn on and switch to PC.
All help is appreciated,
Zenithex.


You can change the time that Grub waits for you to pick an Operating System. 

Open a terminal (CTRL+ALT+T) and run 

```
sudo cp /etc/default/grub /etc/default/grub.backup 
gksudo gedit /etc/default/grub
``` 

Search and find the line **GRUB_TIMEOUT=10**
and change the number  to 20 or 30. 
Keep in mind that the value counts in seconds. 

After you successfully edit the file , save it and run in terminal 
```
sudo update-grub
``` 

Regards
 NikTh

---

### Post by Impavidus on 2013-06-18
You can also set the timeout to -1. Then grub will wait until you hit enter.

---

### Post by Zenithex on 2013-06-18
Thanks for the quick replies,
Went with 30 seconds, that should be enough.
Regards,
Zenithex

---

