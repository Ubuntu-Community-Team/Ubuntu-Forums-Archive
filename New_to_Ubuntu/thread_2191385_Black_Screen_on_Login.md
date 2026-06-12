---
title: "Black Screen on Login"
date: 2013-12-02
forum: New to Ubuntu
---

### Post by gareth4 on 2013-12-02
Wondering if anyone can help me so that I can avoid doing a complete reinstall.

When my Ubuntu 13.10 desktop starts I attempt to log in as normal by typing my password but after all I see is a black screen along with my mouse pointer.  There's no disk access happening and the processor's not tied up so it's not busy doing something. I've tried creating a new user account but the same thing happens with that.  I've tried [resetting Unity and Compiz]("http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html") but to no avail.  My graphics are running on Intel.

Googling around the problem presented me with some more commands that I merrily ran but they didn't impact on the problem either.

Anybody any ideas?

---

### Post by gareth4 on 2013-12-02
The .xsession-errors file in the user directory may point to the problem.  It reads:

Xlib:  extension "GLX" missing on display ":0".
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
init: update-notifier-crash (/var/crash/_usr_bin_totem-video-thumbnailer.1000.crash) main process (2232) terminated with status 1
init: update-notifier-crash (/var/crash/_usr_sbin_unity-greeter.111.crash) main process (2234) terminated with status 1
init: update-notifier-crash (/var/crash/_usr_bin_transmission-qt.1000.crash) main process (2233) terminated with status 1

---

### Post by MikeFlint on 2013-12-31
Have you solved this yet?

I've had a similar issue but mine is (I think) caused by flipping between Cinnamon and Unity. In my case the 'black screen' was because nothing was running to handle the Desktop display. So by default Unity will use Nautilus (and Cinnamon, Nemo) and it seems that if both are enabled, Nemo wins - but Unity doesn't work with Nemo handling the desktop.

So, check that you have a nautilus-autostart.desktop file in /etc/xdg/autostart  and that the Gsettings flag it is looking for is set to true.

e.g. in mine I have:

AutostartCondition=GSettings org.gnome.desktop.background show-desktop-icons

So I'd need to have run 

gsettings set org.gnome.desktop.background show-desktop-icons true

to make that condition True and have Nautilus autostart.

You can check whether this fixes the issue by firstly opening up a terminal session (Ctrl-Alt-T) and checking if Nautilus is running:

ps -A | grep nautilus

If that's empty, try "nautilus --force-desktop"  If that brings the normal desktop up, then your issue was Nautilus not running.

My .xsession-errors looks like your ... not sure why update-notifier-crash is failing to notify of previous crashes, but those are past events you needn't worry about ... deleting the crash files will stop them from popping up at start-up.

---

