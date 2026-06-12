---
title: "Showing a message in tray"
date: 2010-08-01
forum: Programming Talk
---

### Post by hakermania on 2010-08-01
Hello, My application doesn't minimize to tray.
My question is, can it shows messages in the tray e.g. when pushing a button?
If yes, how?:)

---

### Post by hakermania on 2010-08-02
Any suggestion????

---

### Post by vek on 2010-08-02
A cursory search for "gtk tray icon" (Gnome/Ubuntu) or "qt tray icon" (Qt/Kubutnu) reveals source code.

[http://lmgtfy.com/?q=gtk+tray+icon](http://lmgtfy.com/?q=gtk+tray+icon)

To clarify:  A tray icon is independent of minimizing or maximizing.  Any application can have a tray icon even if it does not minimize to tray.  Bear in mind that a tray icon might not be the best place for it in a ubuntu desktop if it is audio or messaging related because thats what the new me-menu is for.  To get something to appear there is different.

If you have a tray icon showing, then your application gets notified when the user clicks on it.  Then you can show a menu or a popup or hide or minimize or maximize your app, its up to you.

---

### Post by hakermania on 2010-08-03
Thank you, but my purpose was NOT to minimize anything to tray. Just to show a message on the tray when a event is being done.

---

### Post by StephenF on 2010-08-03
If you have notify-send installed you can do this from the console. 

$ notify-send "this is how it's done"

From code the library you want to link with is called libnotify for which bindings exist for various languages.

---

### Post by hakermania on 2010-08-05
i don't want to install anything.... Is it so difficult to show a tray message???There are plenty of applications that do it!

---

### Post by StephenF on 2010-08-05
Yes and those applications generally use libnotify, which is installed already. You can of course flash up a window of your own in the general area but it would clash with the space taken up by other messages if present.

You can talk to the notification daemon directly using D-Bus as that's all libnotify does. Not sure if the protocol is frozen or not.

---

### Post by nvteighen on 2010-08-06
> **hakermania said:**
> i don't want to install anything.... Is it so difficult to show a tray message???There are plenty of applications that do it!

libnotify is what you want, really... 

btw, "I don't want to install anything" sounds like a really bad excuse to me :p

---

### Post by hakermania on 2010-08-08
> **nvteighen said:**
> libnotify is what you want, really... 

btw, "I don't want to install anything" sounds like a really bad excuse to me :p
It isn't. I am developing a program which already has a lot of dependencies, and, as there is already a way to show messages at tray (as so many programs already do) why to install an additional package?
Anyway, I will try libnotify and I'll let you know!

---

