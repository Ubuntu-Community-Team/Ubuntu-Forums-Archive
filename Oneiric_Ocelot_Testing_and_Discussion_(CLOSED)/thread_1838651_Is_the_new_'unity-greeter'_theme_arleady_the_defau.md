---
title: "Is the new 'unity-greeter' theme arleady the default lightdm theme?"
date: 2011-09-04
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by eentonig on 2011-09-04
Just wondering, because I don't see any changing background in my login screen. And neither does it reflect my main users background.

And if it's not yet active. Is it advisable to enable it?

---

### Post by jbicha on 2011-09-04
Yes, what you see is definitely the unity-greeter if it looks like [this]("https://lh6.googleusercontent.com/-YwzBNkDW_hM/TldcxYnlckI/AAAAAAAAF5I/dT0uIJTXTo8/unity-lightdm-greeter.png").

The user-background switching feature does not work. Since it is after UI freeze, it doesn't yet appear like that will be a feature in Ubuntu 11.10 but there's still time for an exception to be approved.

---

### Post by eentonig on 2011-09-04
ok thanks,

I already thought so, but I was just wondering, since I saw all those youtube videos showing the background changing.

---

### Post by Sashin on 2011-09-04
That was such an awesome feature... alas it no longer exists...

---

### Post by kyleabaker on 2011-09-05
> **jbicha said:**
> Yes, what you see is definitely the unity-greeter if it looks like [this]("https://lh6.googleusercontent.com/-YwzBNkDW_hM/TldcxYnlckI/AAAAAAAAF5I/dT0uIJTXTo8/unity-lightdm-greeter.png").

The user-background switching feature does not work. Since it is after UI freeze, it doesn't yet appear like that will be a feature in Ubuntu 11.10 but there's still time for an exception to be approved.

My install is fully updated, but I'm not seeing the new login screen. Is there any way I can refresh/reset to get the new login screen?

---

### Post by garvinrick4 on 2011-09-05
These are two packages and versions from fresh install:
```
Package: unity-greeter                   
State: installed
Automatically installed: no
Version: 0.0.5-0ubuntu3
Priority: optional
Section: x11
Maintainer: Robert Ancell <robert.ancell@canonical.com>
Uncompressed Size: 172 k
Depends: libc6 (>= 2.4), libcairo2 (>= 1.2.4), libfreetype6 (>= 2.2.1),
         libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.26.0), libgtk-3-0
         (>= 3.0.0), libindicator3-6, liblightdm-gobject-1-0 (>= 0.9.2),
         libx11-6
Recommends: lightdm
Provides: lightdm-greeter
Description: Unity Greeter
 The greeter for the Unity desktop.
Homepage: https://launchpad.net/unity-greeter


Package: lightdm                         
State: installed
Automatically installed: no
Version: 0.9.3-0ubuntu8
Priority: optional
Section: x11
Maintainer: Robert Ancell <robert.ancell@ubuntu.com>
Uncompressed Size: 393 k
Depends: debconf (>= 0.5) | debconf-2.0, upstart-job, libc6 (>= 2.4),
         libglib2.0-0 (>= 2.28.0), libpam0g (>= 0.99.7.1), libxcb1, libxdmcp6,
         libpam-runtime (>= 0.76-14), libpam-modules, adduser, dbus
PreDepends: dpkg (>= 1.15.7.2)
Recommends: xserver-xorg, unity-greeter | lightdm-greeter
Conflicts: liblightdm-gobject-0-0, liblightdm-qt-0-0
Provides: x-display-manager
Description: Display Manager
 LightDM is a X display manager that: 
 * Has a lightweight codebase 
 * Is standards compliant (PAM, ConsoleKit, etc) 
 * Has a well defined interface between the server and user interface 
 * Cross-desktop (greeters can be written in any toolkit)
Homepage: https://launchpad.net/lightdm


```

---

### Post by kyleabaker on 2011-09-05
@garvinrick4

Thanks, looks like I was missing unity-greeter. Installed and restarted with the new login screen.

---

### Post by garvinrick4 on 2011-09-05
You are welcome please marked as Solved in Thread tools so other's with same may benefit also. Have a nice day.

---

### Post by ratcheer on 2011-09-06
garvinrick4: It is not his thread...

Tim

---

### Post by garvinrick4 on 2011-09-06
> garvinrick4: It is not his thread...yes you are correct ratcheer thanks, excuse me eentonig it was your thread.
Looks like eentonig's thread was answered in post 2 and 4.
Please mark as Solved eentonig so other users will benefit
with same also. Thank you eentonig.

---

