---
title: "Switch back to Unity from Notion"
date: 2015-02-14
forum: New to Ubuntu
---

### Post by kirby2 on 2015-02-14
I installed Notion (tiling window manager) to see what it's like but now I can't figure out how to exit it in order to return to Ubuntu's default Unity interface.

---

### Post by Frogs Hair on 2015-02-14
Just to get you out of Notion , restart the computer and select the Ubuntu default session from the icon on the top right of the greeter box where the password is entered. I would look up how to use Notion before entering the session again or remove it.

---

### Post by buzzingrobot on 2015-02-14
Notion is new to me. But, if you had not enabled automatic login in Unity, and if installing Notion did not replace Unity's display manager (unlikely), then open a terminal, execute "sudo reboot" and select Unity as the environment when you log in.

---

### Post by ajgreeny on 2015-02-14
You could probably just logout and in again; even if you have autologin setup for your user, a logout will require a password to login again, and there you can choose the session type, Ubuntu for unity and presumably Notion for Notion.

---

### Post by kirby2 on 2015-02-14
I actually did have autologin enabled. But thanks for the poke in the right direction. I disabled it with terminal and now I can choose which window manager I want when I log in.

---

