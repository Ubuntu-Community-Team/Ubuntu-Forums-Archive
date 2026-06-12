---
title: "Pigeon Open on Start Up"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by rocketman_dc on 2008-05-13
Hi.  I'd like Pidgeon to open on the desktop where I want it (and where I left it) every time I log in.  How do I do that?

Also, I really don't want to have to sign in every time I log in.  I'm the only person who will use this computer.  How can I just have it book all the way up to desk top?  Thanks.

---

### Post by Inxsible on 2008-05-13
If you mean Pidgin, you can simply select the option to remember the password and that will log you in automatically when Pidgin starts. To start pidgin, you can place it in the startup applications.

---

### Post by dizee on 2008-05-13
For the first question:
The easiest way is to get Xfce to remember your session when you log off. Go to the Xfce Settings Manager, click on Sessions and Startup, and under Logout Settings check the "Automatically save session on logout" option.

Now all you have to do is logout with Pidgin running on whatever workspace you want. When you log back in it'll be restored there.

There is the other way to do this, but this way will remember which desktop it was on, assuming that's what you want.

For the automatic login, click on Applications > Settings > Login Window. Click on the Security tab. Check the box next to "Enable Automatic Login" and select your username from the drop-down list.

---

### Post by cubeist on 2008-05-13
To login automatically, go to *system/admin/login window* and under the *security* tab choose auto login

Edit:
Didn't notice you were using xubuntu... disregard my instructions... follow the previous poster *dizee*

---

