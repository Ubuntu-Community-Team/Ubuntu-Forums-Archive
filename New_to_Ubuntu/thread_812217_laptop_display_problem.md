---
title: "laptop display problem"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by kevinorourke on 2008-05-29
Hi Everybody,
I'm new to ubuntu and have recently received the live cd, when i load ubuntu into my computer it loads alright but for one problem, my display isn't right I see about half of the screen and when i go into preferences and change screen size, my display becomes completely unreadable, i have to reboot my computer. I have tried to detect monitors but to no avail. 
My laptop is a Fujitsu Siemens amilo pro v2030 and the display is a VIA/S3G UniChrome Pro IGP could anybody guide me through getting a suitable driver from windows or a program from synaptic which will install suitable drivers or just a way to solve this problem. I have tried PClinuxOS Gnome and it picks up my monitor no problem so I know there is a driver or program that should solve this but I just don't have the knowledge.
Many Thanks Kevin O'Rourke

---

### Post by neurostu on 2008-05-29
Are you using Hardy Heron or Gutsy Gibon?
If you're using Hardy, before you boot press F4 and select safe graphics mode, then boot and try this.

If your using Gutsy look around for the option to "Force Vesa" or "Safe Graphics Mode" and then boot that way.  

After you install Ubuntu will find the correct driver for your video card and install it.  The vesa driver should work fine until then.

---

