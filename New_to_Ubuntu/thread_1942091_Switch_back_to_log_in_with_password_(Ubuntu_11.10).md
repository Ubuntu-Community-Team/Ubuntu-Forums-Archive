---
title: "Switch back to log in with password (Ubuntu 11.10)"
date: 2012-03-16
forum: New to Ubuntu
---

### Post by chdrappi on 2012-03-16
For a while I wanted to log in without password, and I changed my login settings so I didn't have to do that. Now, I want to switch back to logging in with a password. When I try to change it with the GUI, though, things do not work for me. I have tried making setting a new password then restarting, changing my current password and restarting, and unchanging it back to login without password and then changing it back again. So I've tried a lot of stuff.

What I want is for them to ask me for a password when I hit the login screen that
comes up when I turn on the computer. Does anyone have any suggestions? Probably
something through the terminal.

Thanks

---

### Post by Krytarik on 2012-03-16
Disable auto-login by following this guide:

[http://www.tuxgarage.com/2011/09/setting-lightdm-to-auto-login-oneiric.html](http://www.tuxgarage.com/2011/09/setting-lightdm-to-auto-login-oneiric.html)

Regards.

---

### Post by chdrappi on 2012-03-17
> **Krytarik said:**
> Disable auto-login by following this guide:

[http://www.tuxgarage.com/2011/09/setting-lightdm-to-auto-login-oneiric.html](http://www.tuxgarage.com/2011/09/setting-lightdm-to-auto-login-oneiric.html)

Regards.

I have tried this before posting. It is a guide to help you enable auto-login. Instead, I want to login with a password. Currently it just shows my user name and a "login" button, but I don't need to type in a password. I want to need to type in a password.

Thanks.

---

### Post by Krytarik on 2012-03-17
> **chdrappi said:**
> I have tried this before posting. It is a guide to help you enable auto-login. Instead, I want to login with a password.
Yeah, I should have added "..., but the other way around.", but I thought this should be obvious enough. ;-)

> **chdrappi said:**
> Currently it just shows my user name and a "login" button, but I don't need to type in a password. I want to need to type in a password.
I'm wondering how you enabled password-less login in the first place, when there is no option for that in the GUI dialog "User Accounts"!? However, just run this command to disable it, technically removing your user from the "nopasswdlogin" group:
```
sudo gpasswd -d USERNAME nopasswdlogin
```
Replace USERNAME with the name of your user, obviously. ;-)

---

### Post by critin on 2012-03-17
> **chdrappi said:**
> I have tried this before posting. It is a guide to help you enable auto-login. Instead, I want to login with a password. Currently it just shows my user name and a "login" button, but I don't need to type in a password. I want to need to type in a password.

Thanks.

It also DISables the auto-login by changing the ON/Off option.  Did you UNLOCK before trying to change it?

Click at your name in the top right corner of your screen and choose 'User Accounts':

---

### Post by critin on 2012-03-17
Reading the linked page tells me OFF is default in Oneiric.  Are you using 3D?  Full Unity 3D?  I can change mine but I'm using 2D.

---

