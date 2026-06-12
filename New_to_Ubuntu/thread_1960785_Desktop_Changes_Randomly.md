---
title: "Desktop Changes Randomly"
date: 2012-04-18
forum: New to Ubuntu
---

### Post by saponempotenti on 2012-04-18
So this is not very urgent and not much of a problem, but I am very curious as to why this is happening...

When I first installed Ubuntu, it had orange folders.  Now when it is restarted, and not all of the time, it will switch the folders to a Grey color.  Another change that occurs is the window manager gets a little glitch, and the minimize and maximize buttons collide on top of each other.  These two changes change at the same time every time. This leads me to believe that it has something to do with some type of package I installed? 

(I am a beginner and installed a lot of random stuff while messing around in the first couple of days of post installation)

---

### Post by HiImTye on 2012-04-18
this is the window manager crashing and switching to a fallback. when it happens try hitting ctrl+alt+t and doing:
```
unity --replace &
```

---

### Post by saponempotenti on 2012-04-18
> **HiImTye said:**
> this is the window manager crashing and switching to a fallback. when it happens try hitting ctrl+alt+t and doing:
```
unity --replace &
```

I put that in terminal and it was fine until these lines of codes..

Completed upgrade com.canonical.unity.unity.02.upgrade
OpenGL Warning: Failed to connect to host. Make sure 3D acceleration is enabled for this VM.
Compiz (opengl) - Fatal: GLX_EXT_texture_from_pixmap is missing
Compiz (opengl) - Fatal: Software rendering detected
Compiz (bailer) - Info: Ensuring a shell for your session

(metacity:3342): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(metacity:3342): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(metacity:3342): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(metacity:3342): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Window manager warning: Received a NET_CURRENT_DESKTOP message from a broken (outdated) client who sent a 0 timestamp
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x40000e9 ([ubuntu] D)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

so looks like I would have to enable 3d acceleration, find GLX_EXT_texture_from_pixmap and put it in the right spot, and unable software rendering?

---

### Post by kazztan0325 on 2012-04-19
Hi saponempotenti,

It seems the problem which you mentioned occurs on a Virtual Machine..., do I guess right?

If so, what software are you using for virtualization?
VirtualBox?, VMware?, or other?

---

### Post by saponempotenti on 2012-04-20
> **kazztan0325 said:**
> Hi saponempotenti,

It seems the problem which you mentioned occurs on a Virtual Machine..., do I guess right?

If so, what software are you using for virtualization?
VirtualBox?, VMware?, or other?

I am using Virtual Box as a virtual machine.

---

### Post by kazztan0325 on 2012-04-20
> **saponempotenti said:**
> so looks like I would have to enable 3d acceleration, find GLX_EXT_texture_from_pixmap and put it in the right spot, and unable software rendering?

> **saponempotenti said:**
> I am using Virtual Box as a virtual machine.

- You would be able to enable 3D Acceleration with Settings dialog of Virtual Machine on VirtualBox window.

- As for "Gtk-WARNING for "pixmap"", I am not sure, but possibly you would be able to fix the problem by installing a package "gtk2-engines-pixbuf" with Synaptic Package Manager or Software Center.

- I think, Virtual Machine would be able to use software rendering with vboxvideo driver, but would not be able to use hardware rendering, so you would not be able to disable software rendering. Actually you need not worry about this, I think.

---

### Post by saponempotenti on 2012-04-20
> **kazztan0325 said:**
> - You would be able to enable 3D Acceleration with Settings dialog of Virtual Machine on VirtualBox window.

- As for "Gtk-WARNING for "pixmap"", I am not sure, but possibly you would be able to fix the problem by installing a package "gtk2-engines-pixbuf" with Synaptic Package Manager or Software Center.

- I think, Virtual Machine would be able to use software rendering with vboxvideo driver, but would not be able to use hardware rendering, so you would not be able to disable software rendering. Actually you need not worry about this, I think.


Still not working with the rendering and the gtk2 on, going to try a different virtual machine! :)

---

### Post by kazztan0325 on 2012-04-21
> **saponempotenti said:**
> ..., going to try a different virtual machine! :)

Okay, I would be waiting for your report about a different virtual machine.

Good Luck!

---

### Post by saponempotenti on 2012-05-19
> **kazztan0325 said:**
> Okay, I would be waiting for your report about a different virtual machine.

Good Luck!

I apologize for taking so long to report back.. had multiple virus attacks and had to completely wipe the computer! With school and work the 20+ hours I spent in between sure dragged it out.  Well anyways the original problem is fixed because of the clean wipe and reinstall(with Ubuntu instead of windows!).

---

