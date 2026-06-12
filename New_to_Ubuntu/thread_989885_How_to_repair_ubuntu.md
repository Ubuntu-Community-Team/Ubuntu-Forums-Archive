---
title: "How to repair ubuntu"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by navaneethan on 2008-11-22
Hi friends I installd ubuntu hardy....and i also installed some packages....unfortunately i deleted passwd files in ubuntu...so, when i booting it shows prompt login...not GUI login..so,i can't enter it...will i possible to enter (repair)ubuntu without reinstall....plz help any body.....

---

### Post by adult swim on 2008-11-22
try to login from the prompt and then type in ```
startx
```

---

### Post by mbsullivan on 2008-11-22
Hi navaneethan,

When you say you deleted "passwd files", do you mean /etc/passwd ???

You should be able to repair most any problem without reinstalling, **if** you know *exactly* what the problem is. 

Mike

---

### Post by navaneethan on 2008-11-22
> **mbsullivan said:**
> Hi navaneethan,

When you say you deleted "passwd files", do you mean /etc/passwd ???

You should be able to repair most any problem without reinstalling, **if** you know *exactly* what the problem is. 

Mike

yes friend.../etc/passwd files...

---

### Post by navaneethan on 2008-11-22
ya i used startx ...i can't enter to window manager...

---

### Post by cariboo on 2008-11-22
Restart in recovery mode and at the prompt type:

```
apt-get install ubuntu-desktop
```

You also may want to create a new user password.

```
passwd <user>
```

where <user> is your user name.

Jim

---

### Post by navaneethan on 2008-11-22
friend i can't know exactly about that...but i know the problem is in removing my passwd files....Is any solution available...

---

### Post by mbsullivan on 2008-11-22
Hi navaneethan,

Try what cariboo907 suggested. Step-by-step, here's what to do:

(1) Reboot and wait for the grub screen (it's black and lists the currently installed kernels).

(2) Press [esc] (I believe) to prevent the default kernel from being loaded.

(3) Select the kernel (probably towards the bottom) marked "recovery mode"

(4) This should bring you to a command prompt, logged in as root

(5) Create a new password for every user account with the command:

```
passwd [username]
```

This should create a new /etc/passwd, hopefully.

(6) Reboot

(7) Profit :)

Let me know if you have any problems or questions.

Mike

---

