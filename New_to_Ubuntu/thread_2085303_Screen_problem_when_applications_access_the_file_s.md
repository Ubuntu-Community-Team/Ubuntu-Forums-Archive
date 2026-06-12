---
title: "Screen problem when applications access the file system"
date: 2012-11-17
forum: New to Ubuntu
---

### Post by hans12345 on 2012-11-17
I have a problem with non-maximised windows opening that are bigger than my screen area.

For example, as I type this in gedit, the window is fine. But if I try to open or save, the new window opens and the 'open' or 'save', and 'cancel' buttons are below and to the right of the screen. If I click on 'fully maximized' all is OK. If I then un-maximise, the problem returns.

The same happens when I try to open or save in LibreOffice.

It seems to be a problem when applications access the file system.

This happens on either of my two 12.04 Ubuntu PCs, which are non-identical home built PCs, with different monitor resolutions.

Can someone help me with finding out where to look, and ideally a GUI based solution to the problem. (I am willing to use the terminal window, but prefer not to!)

Thanks

---

### Post by zombifier25 on 2012-11-18
What is your screen resolution?

Also, to resize a window without touching the borders, press Alt + F8 and use the arrow buttons to resize.

---

### Post by hans12345 on 2012-11-24
> **zombifier25 said:**
> What is your screen resolution?

Also, to resize a window without touching the borders, press Alt + F8 and use the arrow buttons to resize.

This PC's resolution is 1600 x 1200. The other Ubuntu PC has a smaller screen with different resolution. I could check, but it seems independent of the screen resolution.

Now, the problem gets interesting!

Your trick with Alt F8 works perfectly with Gedit: I fix the window size, for both open and close of files, all good. Then I close and open again, and it's still good. Problem fixed.

But LibreOffice Writer? NO! I fix the window size, for both open and close of files, all good. Then I close and open again, and it's forgotten the settings. Problem still there.

---

### Post by Wim Sturkenboom on 2012-11-24
You can drag a window using <alt>

Keep <alt> pressed and drag the window using the mouse. Possibly not a fix, but a work around.

---

