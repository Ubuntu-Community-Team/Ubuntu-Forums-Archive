---
title: "About-dialog feezes when fired from AppIndicator (systray icon)."
date: 2011-01-15
forum: Programming Talk
---

### Post by moma on 2011-01-15
Hello,

I have a curious problem.
My audio-recorder app is using the new AppIndicator class to show an icon on the system tray (toolbar panel).

But the About-dialog freezes when it has been fired from the icon's popup-menu.

Here is an example code:
[http://www.futuredesktop.com/tmp/t10.c](http://www.futuredesktop.com/tmp/t10.c)

Compile it:
gcc $(pkg-config --cflags --libs gtk+-2.0 glib-2.0 appindicator-0.1) t10.c -o t10

Run it:
./t10 

* It should show an Ubuntu-icon on the system tray (toolbar panel).

* LEFT-click (I mean left click) the icon and choose "About" from the menu.

* Try to close the dialog. In my case the application freezes.

1) What's going on?

2) How can I replace the About-action with my very own dialog, when I RIGHT-click (I mean right click) the systray icon. Now it shows a standard about-dialog for the AppIndicator itself.

You will need the "indicator-applet" and "libappindicator-dev" (this latter has the appindicator-0.1 lib) to test this program. AFAIK, the first should be be pre-installed in Maverick/Natty.
---

BTW: The final product will be this 
[http://bildr.no/view/800342](http://bildr.no/view/800342)

Learn more about AppIndicator. It replaces the older GtkStatusIcon/GNOME 2.x)
[https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators](https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators)

My system is:
DistroRelease: Ubuntu 10.10
Uname: Linux 2.6.35-24-generic x86_64
InstallationMedia: Ubuntu 10.10 "Maverick Meerkat" - Release Candidate amd64 (20101006)

---

