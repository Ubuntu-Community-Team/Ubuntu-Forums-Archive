---
title: "How to change programs running at startup?"
date: 2014-10-21
forum: New to Ubuntu
---

### Post by kyrawertho on 2014-10-21
There's this audio player Amarok that keeps starting up when I run KDE. I can't find it in /etc/init.d or in the system services in system settings. Where else can I change programs running on boot?

---

### Post by TheFu on 2014-10-21
Amarok is a GUI program. It must be started inside some userids personal login process lists. I don't use KDE, so I don't know where that is located, but I would suspect it is in your HOME under ~/.config/ somewhere.

Things in /etc/ are system-wide processes - only 1 GUI program gets started there ... the login GUI.

Boot startup programs are extremely different than login startup programs. After all, systems can be booted, but not have anyone logged in onto the console for minutes, hours, days, months, years, decades .... but those booted processes still need to run. ;) The GUI is NOT the OS.

---

### Post by buzzingrobot on 2014-10-21
You've checked KDE's startup programs, as opposed to services, in System Settings? Those launch when that user logs in.

There's also an option to toggle restoration of the previous session.

---

### Post by marco-parillo on 2014-10-21
Have you tried System Settings > Startup and Shutdown?
You can see if [COLOR=#000000]Amarok [/COLOR]is in the Autostart, or you can try Session Management > On Login > Start with an empty session

---

### Post by ibjsb4 on 2014-10-21
A search here
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=edit+startup+programs+kubuntu+kde&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=edit+startup+programs+kubuntu+kde&sa=Search&cof=FORID:9)

Came up with two possibilities:
1) /home/<user>/.kde/Autostart
2) /usr/share/autostart/amarok_autostart.desktop

---

### Post by kyrawertho on 2014-10-22
Thanks for your replies. I did check the system settings. It's not in there. It's also not in:
/home/me/.kde/Autostart
/home/me/.config/autostart
/etc/xdg/autostart
/usr/share/autostart/

Any other ideas?

---

### Post by kyrawertho on 2014-10-22
I think I fixed it by deleting it from here: ~/.kde/share/config/session. A bit confusing having 6 different locations for programs to autorun...

---

### Post by deadflowr on 2014-10-22
> **marco-parillo said:**
> Have you tried System Settings > Startup and Shutdown?
You can see if [COLOR=#000000]Amarok [/COLOR]is in the Autostart, or you can try Session Management > On Login > Start with an empty session

This is indeed the method needed.

It should be noted also that Amarok does not quit when clicking on X.
You need to go down to the panel(or up depending on your setup) and right-click on the Amarok icon and exit from there.
OR exit from Amarok menu.

The default settings for Kubuntu is to restore session, so if you had Amarok running but not fully killed, it will autostart at login.

FWIW

---

### Post by JeQhdMD on 2014-10-22
+1 for deadflowr's post . . . this has happened to me several times . . . Amarok stays persistent in the tray and if not shut down, KDE remembers all live programs at shut-down and auto restarts them.

---

### Post by buzzingrobot on 2014-10-23
> **JeQhdMD said:**
> +1 for deadflowr's post . . . this has happened to me several times . . . Amarok stays persistent in the tray and if not shut down, KDE remembers all live programs at shut-down and auto restarts them.

*Kubuntu's* default setting is to restore the previous session, and, as mentioned, that can be toggled on or off in System Settings. Other KDE's may or may not use that as the default.

---

### Post by deadflowr on 2014-10-23
> **buzzingrobot said:**
> *Kubuntu's* default setting is to restore the previous session, and, as mentioned, that can be toggled on or off in System Settings. Other KDE's may or may not use that as the default.

True, some do some don't.
The best example of those that do are when people using conky/kde and report that somehow it's gets all blurry, and the reason is because they have both the restore set and an autostart running giving them multiple conky running in the same space, albeit running out of sync.

---

