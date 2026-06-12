---
title: "No Close, Maximize, Minimize on Windows, and Administator Problem"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by Doommaster1994 on 2008-08-17
Hello everyone. I am new to Ubuntu. I got it on my computer today. I had to restart it and now on every window, I don't get a close, maximize, or minimize option. Also, I go to system-administration-users and groups but it says that I am not allowed to access the system configuration. And it says I am logged in as myself but it says on the top-right Users. And it doesn't let me go online. It says a window says "Starting Firefox Web..." for a few seconds and then it closes. Is there any way to format my hard disk?
Please leave responses.
Thanks and peace out (-<)
-Nick

---

### Post by Oldsoldier2003 on 2008-08-17
> **Doommaster1994 said:**
>  now on every window, I don't get a close, maximize, or minimize option.
```
metacity --replace
``` should fix this
> 
 Also, I go to system-administration-users and groups but it says that I am not allowed to access the system configuration.
-Nick

you need to readd yourself to the admin group. in order to do this you will need to reboot into recovery mode and issue ```
usermod -aG admin <your_username>
```

---

### Post by alienexplorers on 2008-08-17
If you are running compiz you should add this line to your system section of your xorg.conf:
> Option         "AddARGBGLXVisuals" "True".

---

