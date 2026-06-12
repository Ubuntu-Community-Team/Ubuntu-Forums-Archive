---
title: "Gtkmm and startup-notify"
date: 2009-07-06
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2009-07-06
You may know that when in a .desktop file the "StartupNotify" is set to **true** then when the program is launched(eg by nautilus) an entry in the taskbar is created which says "Starting name-of-app". Also the cursor changes to the busy state. When the program is finally loaded this message dissapears and it's place in the taskbar takes the name of the window of the app. This "dissapearance" happens because the toolkit informs the lancher that it has successfully launched.
By now, I hope that you understand what I am refering to. If you don't know what "startup-notify" is and does don't waste your time reading further. 

For those who know about startup-notify. As far as I know gtkmm automatically informs the launcher(eg nautilus) that the app has successfully been loaded when the first window is shown. My real question is how do I do it manually? And if I can do it before creating a Gtk::Main(main loop)?

Case scenario:
The app when started before creating any windows, checks(possibly via dbus) if there is another instance running. If there is, then it sends the commandline args to the other instance and exits. Now before it exits it should inform the launcher that it has been loaded successfully, otherwise(even when it exits) the cursor will remain busy and the entry in the taskbar will remain too.(for the time limit that is set by the spec).

---

### Post by SledgeHammer_999 on 2009-07-07
anyone?

---

### Post by KIAaze on 2010-04-28
Well, I can't answer your question, but you answered mine (what does StartupNotify do). So I'm bumping it up for you. :)

Related link of interest:
[http://standards.freedesktop.org/desktop-entry-spec/latest/](http://standards.freedesktop.org/desktop-entry-spec/latest/)

---

### Post by SledgeHammer_999 on 2010-04-28
Well it's a pretty old post. Anyways, I have cleared everything up. I document everything in my blog post for future reference and for the common good. here in the blog post link-->[http://hammered999.wordpress.com/2010/03/11/startup-notification-system-and-gtkmm/](http://hammered999.wordpress.com/2010/03/11/startup-notification-system-and-gtkmm/)

---

