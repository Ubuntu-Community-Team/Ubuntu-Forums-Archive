---
title: "General Ubuntu noob questions"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by 2LSS on 2008-05-14
Hi I'm new to Linux/ Ubuntu and I have a few problems that I need to resolve. Any help would be very very appreciated.

Just for the record I'm using a Sony Vaio vgn-fz140e and I'm dual booting Vista and Ubuntu 8.04

My first problem is that every time I boot up the computer and the desktop loads I am greeted with "Password needed for default keyring to unlock, nm-applet wants access to the default keyring but it is locked." I enter my password and everything is peachy but I'm wondering if there is some kind of auto login for that?

My second problem relates to my first problem, when trying to find the auto login I went to system/preferences/sessions/session options and clicked on the "remember currently running applications" thinking it would keep the keyring unlocked. But it didn't work and in addition to unlocking the keyring after boot up I have to close 5 different apps that it remembered were running when I clicked it. Is there any way to restore or deactivate this?

My third problem is that my laptop won't suspend or hibernate. If I try to suspend everything closes, the screen goes black and there is a blinking cursor. If I try to hibernate Ubuntu logout hangs up, and the screen goes blank, but the computer does not shut off. When I reboot I'm greeted with a message "Failed to Hibernate bla bla bla." I tried to install Uswsusp but it only worked 30% of the time with suspend and hibernate still didn't work. Is there any way to fix this?

My last problem is that my laptop has a built in webcam and mic that I want to use but I need sony vaio drivers for them. Does anyone know where I can find or install them? 

Like I said before any help would be very very appreciated, thanks.

---

### Post by macaholic on 2008-05-14
On the first two, nm-applet needs you to grant it keychain access unless you login manually. And no, doing that with session manager won't remember the keychain.

---

