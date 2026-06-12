---
title: "No webcam"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by MadsRH on 2008-10-16
Can anyone tell me why I can't see my webcam in 8.10 BETA? I would like to try Cheese :-)

In the terminal *lsusb* showes:
Bus 002 Device 002: ID 041e:4053 Creative Technology, Ltd Live! Cam Video IM

[B]
//MadsRH[/B]

By the way, don't know if this matters, but the cam was disconnected when I installed Ubuntu.
I also just learned that the *gstreamer-properties* command I can select the USB as video input, but I still can't see Cheese in Nautilus

---

### Post by MadsRH on 2008-10-17
I've looked through the Cheese documentation on the Gnome webpage, but it doesn't say how to start the program :confused:

---

### Post by lswest on 2008-10-17
run it with the command 'cheese' (without the quotes) from your run application window, or the terminal.  If it's installed (and working) then you can add a launcher to it in the Applications-->Graphics menu (if it's not already there) by right-clicking the menu choosing 'edit menus' and then going to the right menu and making a new launcher.  Call it Cheese and use cheese for the command.

Ubuntu should run the right module at the start for your webcam, even if it wasn't enabled when you installed Ubuntu, if there is a module that exists for it.

---

### Post by alphacrucis2 on 2008-10-17
> **MadsRH said:**
> Can anyone tell me why I can't see my webcam in 8.10 BETA? I would like to try Cheese :-)

In the terminal *lsusb* showes:
Bus 002 Device 002: ID 041e:4053 Creative Technology, Ltd Live! Cam Video IM

[B]
//MadsRH[/B]

By the way, don't know if this matters, but the cam was disconnected when I installed Ubuntu.
I also just learned that the *gstreamer-properties* command I can select the USB as video input, but I still can't see Cheese in Nautilus

Have you got Cheese installed? Have a look under the package manager. The Camera doesn't have to be plugged in when you install. Plug the camera in then type dmesg in a terminal window. Right at the end of the output you should see the messages related to the camera being detected and an appropriate driver loaded. You should also find the camera appears as /dev/video0

---

