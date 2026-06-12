---
title: "First time user, bunch of graphics/mouse problems..."
date: 2008-05-02
forum: New to Ubuntu
---

### Post by ribbon on 2008-05-02
Hi guys, I just installed Ubuntu 8.04 (64bit version) for the first time yesterday. Things seemed to be going well at first, but after trying to configure some stuff and install drivers, it seems like I've gone backwards...

1. Biggest problem is my graphics drivers. I have an ATI Radeon x1900XT. My graphics card seemed to be working fine the first reboot after I installedd, my default resolution was set to 1680x1050 like I wanted. I then installed WoW using WINE which actually went surprisingly well, but there were a lot of artifacts so I tried to upgrade my drivers to the latest official ATI ones (went to ATI.com). Installation seemed to go fine, but after I rebooted, ubunbtu said my graphics card was not configured properly and it forces me to run in low-graphics mode (800x600), even though I go to System > Administration > Hardware  Drivers and it is enabled and in use. However, I can't open the ATI Catalyst Control Center, the error is "There was a problem initializing Catalyst Control Center Linux edition. No ATI graphics driver is installed, or the ATI driver is not functioning properly. Please install the ATI driver appropriate for your ATI hardware or configure using aticonfig." I've tried uninstalling, reinstalling a number of times but I'm stuck in low-graphics mode now.

2. I have a Razer Copperhead mouse. It has LED's on it and they light up when I start up my computer, but it doesn't work until I unplug it and replug it in. No idea what to do about this.

3. Really stupid problem... but there's a Facebook poker addon that I used to play but now it doesn't work anymore.. It runs in Flash, which I have installed, but when trying to connect to the main server, I get "You could not connect to the server. Your firewall may be blocking access to port 9339.", but I didn't even install a firewall...

And I haven't even tried installing my X-Fi XtremeMusic drivers yet, sigh... a lot of problems, but I really don't wanna go back to windows...

---

### Post by markekeller on 2008-05-02
I'm not sure about your mouse (seems to not be being detected on startup, or something), but I've had similar problems with screen resolutions.  They seem to often have quite random solutions. :)  Have you tried installing (or uninstalling) the ATI drivers using [Envy]("http://www.albertomilone.com/nvidia_scripts1.html")?  Or disabling it with *System > Administration > Hardware Drivers*?

---

### Post by ribbon on 2008-05-02
Okay, so I uninstalled the ATI drivers again and now I'm finally back to 1680x1050 somehow (even though this is the 3rd time I've uninstalled the drivers). System > Administrators > Hardware Drivers now shows my ATI driver as disabled and not in use, but don't want I want it to be enabled for more performance (or even better, the actual ATI drivers)?

---

### Post by ribbon on 2008-05-02
(fixed a problem.. can't figure out how to delete)

---

### Post by ribbon on 2008-05-02
yay I restarted and it's miraculously working now! ATI drivers working (I can actually open catalyst control center now)... And my mouse someone worked too.. so now I just have to fix facebook poker and sound card without rebooting somehow.. :X

---

### Post by ribbon on 2008-05-02
Fixed the facebook poker game problem by uninstalling swfdec and installing adobe flashplayer plugin

---

