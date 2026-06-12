---
title: "Get useful information, or .desktop file, regarding running application?"
date: 2008-05-16
forum: Programming Talk
---

### Post by Mr. Picklesworth on 2008-05-16
Is there a nice way to retrieve a .desktop file (as in /usr/share/applications) connected to a running application?

If not, are there any good, clean and "correct" ways to determine information such as a suitable description and icon for a running program?
Are there any projects working to implement the former? It would be quite cool ;)

---

### Post by Quikee on 2008-05-17
> **Mr. Picklesworth said:**
> Is there a nice way to retrieve a .desktop file (as in /usr/share/applications) connected to a running application?

If not, are there any good, clean and "correct" ways to determine information such as a suitable description and icon for a running program?
Are there any projects working to implement the former? It would be quite cool ;)

There is no connection between .desktop file and the actual working application as the .desktop file just provides the cmd line that is then used to start the application, but generally it doesn't even need to be an application that it start. 

It is no problem to get the icon from an running application because the window manager has it any you could use something libwnck for example - but I don't think that the application stores its description anywhere.

---

### Post by Mr. Picklesworth on 2008-05-17
Indeed, that was my concern. I think a connection could be made via a little library, though.

The reason I don't like to use the window manager for this is because that assumes windows are open and assumes they all have the same direct purpose. I believe GNOME System Monitor, and a few other applications, get icons and other information by a funny hack involving the process command line...
Thanks, though. I guess it's something I'll need to pester the GNOME guys for :)

---

