---
title: "Gnome Not working correctly"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by markbusu on 2008-05-17
Hi Guys,

Have been encountering a weird issue.. Suddenly when i attempt to use my linux box using Gnome rather then shell, the window manager does not work correctly.

That is, it takes an age to load each windows (Most of which down appear until you hover the mouse over it)

Everything loads up in triangles... slowly... (I dont know if im explaining myself correctly)

I was thinking of re installing xserver-xgl... Will this help??

If yes... how can you re install in apt-get?

Thanks!

---

### Post by FuturePilot on 2008-05-17
Are you using Compiz? What graphics card do you have? XGL may not even be needed, which may be causing the problem.

---

### Post by pytheas22 on 2008-05-17
First you should try making a new user account (System>Administration>Users and Groups).  Log in under it and see if the problem persists.  There's a good chance that the problem is the result of some local user configuration, and this will determine that.

---

### Post by markbusu on 2008-05-17
Currently im using the system remotely... however i will give it a try.

Regarding the system, i have an ATI Card

01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]

Also using Compiz..

Using Version 7.10

Note i never got compiz to work without the xglserver... that is why i had it installed... for more information, i installed compiz as follows:

1. Run this command in terminal "sudo apt-get install xserver-xgl"
2. Once the above is complete, run this also in terminal "sudo apt-get install compizconfig-settings-manager compiz compiz-core compiz-fusion-plugins-main compiz-fusion-plugins-extra compiz-gnome compiz-plugins libcompizconfig-backend-gconf libcompizconfig0"
3. Reboot
4. Log in. 3D effects should be enabled!
5. Customize Compiz Fusion.

Thanks!

---

