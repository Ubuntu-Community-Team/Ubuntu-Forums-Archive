---
title: "[SOLVED] Having deb packages create desktop shortcuts."
date: 2008-11-02
forum: Packaging and Compiling Programs
---

### Post by Tamalin on 2008-11-02
I was wondering how to have a .deb file create a desktop shortcut to the application being installed?  Is there a good way to do this, maybe in the postinst script?

---

### Post by Pro-reason on 2008-11-02
There is no good way to do that, because it's an evil Windows thing to do.  Your app should install entries in the standard menus and nowhere else.  Even extremely popular and useful apps such as Firefox and OpenOffice.org don't get icons on the desktop, so why is your app so important that it should get priority over them?

I would delete any app that tried to take over my desktop like that.  This isn't Windows.

---

### Post by snova on 2008-11-02
We of Ubuntu are above such nonsense. :)

Yes, the postinst script would be the place to put it. But remember that the location of the desktop can be changed; it's not always ~/Desktop.

Also know that you're going to tick off a lot of people this way...

---

### Post by Tamalin on 2008-11-03
Yes, you are completely right, though I had never noticed that before, but now I appreciate it.  Let me rephrase my question, how can I get my deb files to add shortcuts on the Applications menu?

---

### Post by Tamalin on 2008-11-03
Ok, I figured it out!
I add a .desktop file to the /usr/share/applications file called application.desktop, and add an icon called application.svg to the /usr/icons/hicolor/scalable/apps directory.  gedit even does the .desktop syntax highlighting for me!

---

