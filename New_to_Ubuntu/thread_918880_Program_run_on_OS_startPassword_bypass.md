---
title: "Program run on OS start?/Password bypass?"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by Grimhound on 2008-09-13
Is there any way to set it so certain programs such as Pidgin run on Ubuntu loading?

Also, is there any way to make Ubuntu bypass the login screen and just load a certain account without requiring a password?

---

### Post by mcallenSchmee on 2008-09-13
> **Grimhound said:**
> Is there any way to set it so certain programs such as Pidgin run on Ubuntu loading?

Also, is there any way to make Ubuntu bypass the login screen and just load a certain account without requiring a password?

Yes to both. Go to System>Preferences>Sessions to add programs to launch at startup. Go to 'System>Administration>Login Window' and under the security tab you can choose to log in automatically to an account.

---

### Post by Jack M. on 2008-09-13
You can set up certain programs to load on startup by adding them to the 'Startup Programs' tab in System > Preferences > Sessions. For Pidgin, the command should be 'pidgin' and the 'Name' and 'Comments' fields can be whatever you want. If you like, you can also make the buddy list start up in the tray regardless of whether it was minimized before with the 'Buddy List Options' plugin that is included in the 'pidgin-plugin-pack' package (installable from Administration > Synaptic Package Manager).

You can enable automatic logging in through the System > Administration > Login Window control panel. Check the "Enable Automatic Login" checkbox in the 'Security' tab and select a user.

---

### Post by nothingspecial on 2008-09-13
> **Grimhound said:**
> Is there any way to set it so certain programs such as Pidgin run on Ubuntu loading?

Yes, in your menus goto system > preferences > sessions.
In the sart up tab, click add. Then fill in the boxes eg
Name      Pidgin
Command   pidgin
Comment   Instant messenger.

---

