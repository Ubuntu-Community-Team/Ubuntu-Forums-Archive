---
title: "Running KOrganizer in the background?"
date: 2012-10-16
forum: New to Ubuntu
---

### Post by softappstudio on 2012-10-16
I am running KOrganizer as a PIM with e-mail alerts under Gnome: fine. I need to make it a "background service", so it does not upset the user on the PC providing this service. I have tried using {System}{Preferences}{Startup Applications} "KOrganizer -q", but I don't think it runs with a -q switch. Could I perhaps have it autorun minimized, &/or on a specified workspace? Is there a list of available switches for me to try out?
--Grahame

---

### Post by ajgreeny on 2012-10-16
Have a look at **alltray** which may work with korganizer.  It allows you to start an application minimised to a system tray icon with command eg, ```
alltray kmail
``` if that is the command normally used for kmail.

I am assuming alltray is available for 12.04, if that is what you're using, but I am running 10.04 at the moment so can't check that.

---

