---
title: "Strange Start-Up Problem"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by Jack Bonner on 2008-11-30
Recently, every time I boot up and get to the point where I need to enter my password to connect to my wireless network, aMSN opens up, Firefox opens up and so does the update manager. This is all done automatically without any intervention from me. Oddly it only seems to have started since I allowed it to do a large update a few days ago. Anyone else had this problem? Or know how to solve it?

---

### Post by LinuxGuy1234 on 2008-11-30
> **Jack Bonner said:**
> Recently, every time I boot up and get to the point where I need to enter my password to connect to my wireless network, aMSN opens up, Firefox opens up and so does the update manager. This is all done automatically without any intervention from me. Oddly it only seems to have started since I allowed it to do a large update a few days ago. Anyone else had this problem? Or know how to solve it?

I have the same problem. But was easily fixed by closing every window at the end of the session and shutting down Ubuntu like normal (I can't go the "normal" way, I need to do Ctrl-Alt-Backspace in order to get into the login manager (gdm) and shut down, this doesn't occur in KDE, I don't know what is happening, GNOME freezes when I go the normal way).

---

### Post by EdThaSlayer on 2008-11-30
> **Jack Bonner said:**
> Recently, every time I boot up and get to the point where I need to enter my password to connect to my wireless network, aMSN opens up, Firefox opens up and so does the update manager. This is all done automatically without any intervention from me. Oddly it only seems to have started since I allowed it to do a large update a few days ago. Anyone else had this problem? Or know how to solve it?

It isn't really a problem with the start-up, it's a problem with some configurations.In KDE 4.10 for example, there is a settings manager where you can tweak some settings. By default, the setting should be "restore previous settings" but you can change it so it starts with an empty session.

I guess in Xubuntu I would look into the settings, then check out the session manager, and change it to start with an "empty session"(on login).

---

### Post by Jack Bonner on 2008-11-30
> **EdThaSlayer said:**
> It isn't really a problem with the start-up, it's a problem with some configurations.In KDE 4.10 for example, there is a settings manager where you can tweak some settings. By default, the setting should be "restore previous settings" but you can change it so it starts with an empty session.

I guess in Xubuntu I would look into the settings, then check out the session manager, and change it to start with an "empty session"(on login).

Unfortunately I can't find a Session Manager anywhere. Any other ideas of where to look?

---

### Post by zika on 2008-11-30
> **Jack Bonner said:**
> Unfortunately I can't find a Session Manager anywhere. Any other ideas of where to look?

System->Preferences->Sessions->Options->Automatically remember running applications when logging out.

---

### Post by Jack Bonner on 2008-11-30
> **zika said:**
> System->Preferences->Sessions->Options->Automatically remember running applications when logging out.

I don't have a 'Preferences' under System. I'm pretty sure that's Gnome. I'm running XFCE

---

### Post by Jack Bonner on 2008-11-30
> **zika said:**
> System->Preferences->Sessions->Options->Automatically remember running applications when logging out.

A thought: Is there a way to do that through the terminal?

---

### Post by dgerwin11 on 2008-11-30
Get to Sessions and start up in xfce.  Applications>Settings>Settings Manager  Click on appropriate icon.

---

### Post by dgerwin11 on 2008-11-30
It looks like my first reply got deleted,.  Applications>Settings>Settings Manager.  Then click on apropriate icon

---

### Post by zika on 2008-11-30
> **Jack Bonner said:**
> I don't have a 'Preferences' under System. I'm pretty sure that's Gnome. I'm running XFCE

ups! sorry!

---

### Post by Jack Bonner on 2008-11-30
> **dgerwin11 said:**
> It looks like my first reply got deleted,.  Applications>Settings>Settings Manager.  Then click on apropriate icon

Under Settings Manager, the only thing I have for Sessions is 'Sessions and Startup' Under that I have two tabs with the following options:

General
-Session Chooser
Display Chooser on login

-Logout Settings
Automatically save session on logout
Prompt On Logout
Show Hibernate Button
Show Suspend Button

Advanced
-Compatibility
Launch Gnome services on startup
Launch KDE services on startup

-Security
Manage Remote Applications.

None of these help me. Surely there's someone out there familiar with XFCE that can tell me how to stop these programs loading at startup.

Please. It's really annoying me now.

---

### Post by Jack Bonner on 2008-11-30
One last bump, to see if anything turns up

---

### Post by 4Orbs on 2008-11-30
At your login screen, select Sessions and choose Xfce Session rather than Last Saved Session (or something like that), then log in. This should start you out with a clean desktop.

---

