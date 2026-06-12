---
title: "Can't seem to get the terminal to move the folder"
date: 2011-12-03
forum: New to Ubuntu
---

### Post by Tsuki561 on 2011-12-03
Hi I have been trying to move this theme folder from /home/"username" to /home/"username"/usr/share/themes but it simply just can' ind it, and I can't move it by drawing the folder from window to window.
Any commands I should use?
(Note: I used mv but it didn't work)

---

### Post by matt_symes on 2011-12-03
Hi

> **Tsuki561 said:**
> Hi I have been trying to move this theme folder from /home/"username" to /home/"username"/usr/share/themes but it simply just can' ind it, and I can't move it by drawing the folder from window to window.
Any commands I should use?
(Note: I used mv but it didn't work)

Try

```
sudo mv /home/<user_name>/<theme_folder> /usr/share/themes
```

It wants to go into the /usr/share/themes folder.

Kind regards

---

### Post by Tsuki561 on 2011-12-04
Thanks alot!
It sure worked but for some reason I needed to use "sudo" or else it would just say: Permision Denied.

---

### Post by marrabld on 2011-12-04
You needed to use <sudo> because you were trying to copy a file outside of your home folder.  You need 'elevated privileges' to do that.  Sudo briefly grants you those privileges, which is why you need to type you password.

---

