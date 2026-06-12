---
title: "How to prevent menu changes"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by anlaoch on 2008-07-25
Hi.

Can anyone tell me how to prevent users from making changes to Hardy Heron menus?  I want the menus to be there, I just want to prevent the user from having access to some system preferences.  I want to keep access to these menus myself.

Thanks in advance.

---

### Post by nvteighen on 2008-07-25
Have you considered creating non-admin user accounts? It may be more effective... Even if you don't have a menu entry, you'll still be able to change system configuration through the Terminal if you are an admin. If not admin, no matter what, you won't be able.

If I recall correctly, I'm almost sure menus are defined by each user's gconf in base to a system-default. So, if someone deletes a menu, he's actually just hiding it... unless you have root privileges and are deleting the default "base".

Maybe I haven't understood you well? What kind of tweaking you want to prevent?

---

### Post by anlaoch on 2008-07-25
The account I've created for the other user is a non-admin account.  It's just a "Users" a/c.  Even so, the other user can go into "System/Preferences/Main Menu" and make changes to the "Main Menu" setting.  I didn't think they would be able to change anything unless they were admin.

Basically, I just want to stop users messing with preferences.

Thanks.

---

### Post by cariboo on 2008-07-25
I think waht you are looking for is Pessulus. Have a look at the wiki here:

[http://live.gnome.org/Pessulus](http://live.gnome.org/Pessulus)

Pessulus is available in the repositories and you can use Add/Remove Programs or Synaptic Package Manager and of course the command line to install it.

Jim

---

### Post by nvteighen on 2008-07-25
> **anlaoch said:**
> The account I've created for the other user is a non-admin account.  It's just a "Users" a/c.  Even so, the other user can go into "System/Preferences/Main Menu" and make changes to the "Main Menu" setting.  I didn't think they would be able to change anything unless they were admin.

Basically, I just want to stop users messing with preferences.

Thanks.
OK. I hardly doubt that any user could mess the other users' Main Menu preferences.

According to some research I've done: There's a "central" system menu preference which includes the common menu entries; you only can edit it being root. When a user logins, those system preferences are copied and then modified by user-specific "scripts" placed in ~/.config/menus. So, each user can only mess with his/her preferences, not anyone else's (unless writing permissions are given for those files, but that's not the default).

According to that, if you stick to defaults, you don't need any extra tool... Unless you also don't want people modify even their own configuration. Then, it's all about changing the config files ownership to root and only give read permissions to users; probably any tool you'll find will actually do something similar to that but in an automated way.

---

