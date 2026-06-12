---
title: "How are Launcher icons managed?"
date: 2012-07-19
forum: Programming Talk
---

### Post by rg4w on 2012-07-19
I use an app in which the icon that launches the program never renders in an "open" state, and instead the launcher becomes populated with generic icons for each window the program opens.

I'm working with that team to determine how this can be corrected, so I'm here hoping to find some guidance on this.

Where might I look into the APIs to find how icons are managed in the Launcher, so that we may refine this app's behavior to have a single icon representing all of its open windows?

Thanks in advance for your help on this -

---

### Post by rg4w on 2012-07-20
To the moderators:  on further consideration, it occurs to me that perhaps this thread may be better suited if moved to "Ubuntu Application Development".  Please feel free to move if you think so.

---

### Post by rg4w on 2012-07-21
Here's a screen shot which illustrates the issue:

[IMG]http://fourthworldlabs.com/ubuntu/launchericons.png[/IMG]

---

### Post by rg4w on 2012-08-22
I found the answer:  that application uses different strings to identify itself in the WM_CLASS x Window property and in the desktop file; of course those should match to allow the WM to maintain appropriate associations.

If you encounter this and don't have access to the source for the app exhibiting this behavior, you can obtain the WM_CLASS string from wmctrl and use that to modify the desktop file accordingly.

Details here:

[https://live.gnome.org/GnomeShell/ApplicationBased](https://live.gnome.org/GnomeShell/ApplicationBased)
[http://askubuntu.com/questions/36434/how-can-i-remove-duplicate-icons-for-launched-java-programs-in-the-launcher](http://askubuntu.com/questions/36434/how-can-i-remove-duplicate-icons-for-launched-java-programs-in-the-launcher)

---

