---
title: "how to input chinese in opera9.5?"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by elliah on 2008-07-14
i installed opera9.5 from the .deb i downloaded from the opera website.
however, the shortcut ctrl+space doesn't work when i'm in opera..and i cannot input chinese using opera either.
my other applications work perfectly. i am using scim. what should i do?

---

### Post by ChameleonDave on 2008-07-14
> **elliah said:**
> i installed opera9.5 from the .deb i downloaded from the opera website.
however, the shortcut ctrl+space doesn't work when i'm in opera..and i cannot input chinese using opera either.
my other applications work perfectly. i am using scim. what should i do?
I think that the problem is that you have set up SCIM to work with Gtk apps (such as those that come with GNOME) only, but Opera is a Qt app (such as those that come with KDE).

Go back to the guide you used to set up SCIM.  Follow the instructions for enabling Chinese input for KDE/Qt.

Off the top of my head, I believe it involves adding the line "*QT_IM_MODULE="scim-bridge*" to the file located at* /etc/X11/xinit/xinput.d/scim*.

---

### Post by elliah on 2008-07-15
ok..i got it to work...another qns though...how do i make scim my default input method (right now, every time i want to use scim i have to open mousepad, right-click and change the input method from system to scim...)

---

