---
title: "QSystemTrayIcon tooltip does not show"
date: 2019-08-07
forum: Programming Talk
---

### Post by anshah on 2019-08-07
I have setup a QSystemTrayIcon with a tool tip but it doesn't show up on mouse hover. I'm running Qt 5.8 on Ubuntu 17.04


Here is the setup code:

> [COLOR=black][FONT=Menlo]trayIconMenu = [/FONT][/COLOR][COLOR=#000088][FONT=Menlo]new[/FONT][/COLOR][COLOR=black][FONT=Menlo] QMenu(this);
[/FONT][/COLOR][COLOR=black][FONT=Menlo]trayIconMenu->addAction(quitAction);
[/FONT][/COLOR][COLOR=black][FONT=Menlo]pTrayIcon = [/FONT][/COLOR][COLOR=#000088][FONT=Menlo]new[/FONT][/COLOR][COLOR=black][FONT=Menlo] QSystemTrayIcon(this);
[/FONT][/COLOR][COLOR=black][FONT=Menlo]pTrayIcon->setIcon(QIcon([/FONT][/COLOR][COLOR=#008800][FONT=Menlo]":/Images/TrayIcon.ico"[/FONT][/COLOR][COLOR=black][FONT=Menlo]));
[/FONT][/COLOR][COLOR=black][FONT=Menlo]pTrayIcon->setVisible([/FONT][/COLOR][COLOR=#000088][FONT=Menlo]true[/FONT][/COLOR][COLOR=black][FONT=Menlo]);
[/FONT][/COLOR][COLOR=black][FONT=Menlo]pTrayIcon->showMessage([/FONT][/COLOR][COLOR=#008800][FONT=Menlo]"balloon title"[/FONT][/COLOR][COLOR=black][FONT=Menlo],[/FONT][/COLOR][COLOR=#008800][FONT=Menlo]"balloon message"[/FONT][/COLOR][COLOR=black][FONT=Menlo]);
[/FONT][/COLOR][COLOR=black][FONT=Menlo]pTrayIcon->setToolTip([/FONT][/COLOR][COLOR=#008800][FONT=Menlo]"this is the tooltip"[/FONT][/COLOR][COLOR=black][FONT=Menlo]);
[/FONT][/COLOR][COLOR=black][FONT=Menlo]pTrayIcon->setContextMenu(trayIconMenu);
[/FONT][/COLOR][COLOR=black][FONT=Menlo]pTrayIcon->show();[/FONT][/COLOR]


I do not see the tool tip show on mouse hover over the system tray icon. This works on Windows but when I try on Ubuntu I don't see the tooltip. Is there a known limitation in Ubuntu regarding QSystemTrayIcon tooltips?

---

### Post by &amp;KyT$0P# on 2019-08-07
> **anshah said:**
> I'm running Qt 5.8 on Ubuntu 17.04

Ubuntu 17.04 [died in January 2018]("https://wiki.ubuntu.com/Releases"), more than a year ago.  Do you have a specific reason to need this particular version of Ubuntu?

---

### Post by anshah on 2019-08-07
As per requirements we need to support everything from Ubuntu 14.04+ for customers.

---

