---
title: "Help - white screen with Gutsy since latest updates"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by mgbridges on 2008-06-21
I re-installed Gutsy a couple of weeks ago after major problems with Hardy and I've been very happy. However, the other night I installed whatever updates were offered (I think they were kernel-related) and since then I get a white screen after logging in every time.

How can I get around this so that I can uninstall whatever has caused the problem?

Cheers,

Martin

---

### Post by kwirk on 2008-06-21
I presume you have Ubuntu.

Do you have compiz or beryl installed?

If so, try pressing Alt-F2, and typing "metacity --replace" and press enter.

---

### Post by mgbridges on 2008-06-21
> **kwirk said:**
> I presume you have Ubuntu.
Yes, I'm using 7.10.

> **kwirk said:**
> Do you have compiz or beryl installed?
I have Compiz installed. I recently turned on Visual Effects, but this seemed to be working OK before the latest set of updates.

> **kwirk said:**
> If so, try pressing Alt-F2, and typing "metacity --replace" and press enter.
I tried this - nothing seemed to happen. What is it supposed to do?

Thanks,

Martin

---

### Post by kwirk on 2008-06-21
metacity --replace should 'replace' compiz with gnomes default window manager. The white screen is a common problem with compiz/beryl. Have you got GNOME or KDE, etc?

---

### Post by mgbridges on 2008-06-21
Thanks - this got me back to my standard desktop. Any ideas how I get Compiz to work properly, since it was working prior to the recent updates to the kernel?

Cheers,

Martin

---

### Post by kwirk on 2008-06-21
Good.

Open a terminal and run "compiz --replace". The screen will probably go white again, so just press Ctrl-C to stop compiz running and paste in the errors that come up in ther terminal. If you have problems with the windows just do the Alt-F2, metacity --replace, enter again.

---

### Post by mgbridges on 2008-06-21
As expected, Compiz caused a whitescreen. Errors below:

```
Checking for Xgl: not present. 
Detected PCI ID for VGA:        Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
01:05.0 0300: 1002:791e (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

Any ideas?

Martin

---

### Post by kwirk on 2008-06-22
What graphics card do you have?
Try lspci and check its listed.

And post your xorg.conf found in /etc/X11/ and Xorg.0.log found in /var/log/

---

