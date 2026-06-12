---
title: "How do I boot into a command prompt to edit .conf files?"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by shmoe010 on 2008-04-23
I recently upgraded to 8.04 from 7.10 and like many others my nvidia drivers failed on me. I found the fix, but all the solutions assume that I already know how to get a command prompt and what command to type, etc. Being a total noob at linux, I could use some help. My video card won't let me get past the Ubuntu boot progress bar (black screen, orange bar.)

I just need to add lines to /etc/modules and /etc/x11/xorg.conf

Thanks!

---

### Post by jakupl on 2008-04-23
```
sudo nano /etc/modules
```

```
sudo nano /etc/x11/xorg.conf
```

---

### Post by Oldsoldier2003 on 2008-04-23
> **shmoe010 said:**
> I recently upgraded to 8.04 from 7.10 and like many others my nvidia drivers failed on me. I found the fix, but all the solutions assume that I already know how to get a command prompt and what command to type, etc. Being a total noob at linux, I could use some help. My video card won't let me get past the Ubuntu boot progress bar (black screen, orange bar.)

I just need to add lines to /etc/modules and /etc/x11/xorg.conf

Thanks!

restart your computer into recovery mode and log into maintenance mode as root. you will be able to use the cli tools to edit those files.
```
nano /etc/modules
``` or vi /etc/modules (nano is more user friendly for a new user but if you are experienced with vi , go for it)

edit: if you boot into recovery mode maint mode you wont need to sudo as was referenced in the post above.

---

### Post by shmoe010 on 2008-04-23
Thanks!

---

### Post by Xiong Chiamiov on 2008-04-23
jakupl covered the commands, but to get to a prompt, just select the recovery mode option of Ubuntu at startup, rather than the normal one.

---

### Post by geoganoe on 2008-04-23
> **shmoe010 said:**
> Thanks!

When you first start the boot process, look for the screen that says something like "The highlighted entry will be start in [N] seconds".  When you see that, use the arrow key to scroll down to the option for recovery mode before the timer gets to zero, when you have the recovery mode line highlighted, hit the enter key.  In recovery mode you should get a useable display.

          George

---

