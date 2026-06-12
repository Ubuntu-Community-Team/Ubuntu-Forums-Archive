---
title: "Problem with Add/Remove programs"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by Elycian on 2008-05-11
My brother was interested in making an Ubuntu account and he noticed how I had a bunch of cool apps and asked where I got some of them.. and I was like go to applications>Add/Remove Programs.. but it wasn't there..

Why does my account have add/remove programs but his doesn't? I'm pretty sure we both of the same privileges - both desktop users.. Is there any way to fix this?
Thanks :]

---

### Post by smoker on 2008-05-11
if you right click at the corner of the menu bar, and select, 'edit menus' you can customise to include what you want.

best of luck

---

### Post by SunnyRabbiera on 2008-05-11
well instead direct him to synaptic, its under system> administration listed as synaptic package manager.
also most secondary accounts dont have access to add/remove, you may have to adjust permissions.

---

### Post by drs305 on 2008-05-11
Are you saying if he clicks on the System menu he doesn't see the Add/Remove Menu, or he doesn't see the specific applications in Add/Remove?

If he doesn't see Add/Remove, right click on the main system icon in the top panel and select Edit Menus. In the right hand pane, see if the Add/Remove menu is present and unchecked. If it isn't checked, click on it and the Add/Remove menu should now appear in the System menu.

---

### Post by Kevbert on 2008-05-11
> **drs305 said:**
> Are you saying if he clicks on the System menu he doesn't see the Add/Remove Menu, or he doesn't see the specific applications in Add/Remove?

If he doesn't see Add/Remove, right click on the main system icon in the top panel and select Edit Menus. In the right hand pane, see if the Add/Remove menu is present and unchecked. If it isn't checked, click on it and the Add/Remove menu should now appear in the System menu.

Yes.
In the right hand pane it's at the bottom (may be off screen).

---

### Post by unutbu on 2008-05-11
You and your brother do not have the same privileges.
In your account, go to System>Administration>Users and Groups.

Click on your brother's account name. Click the Properties button. Click on the User Privileges tab. If you click on 'Administer the System' check box, then he will have the power to Add/Remove programs from the system (I think). I think this also gives him  the power to run programs as root.

---

### Post by Elycian on 2008-05-11
> **unutbu said:**
>  I think this also gives him  the power to run programs as root.

Sooo, uhhh.. Not sure if doing that would be good.. as from everyone I've heard from says you shouldn't log into root.. however I think I did what you were talking about anyways I went to administration>users and groups>properties and clicked a little box that said "Administer the system" at first I was a little skeptical because I thought that would create a second root user.. but I clicked it anyways because I noticed my original account had that too.. But yeah, thanks guy :]

---

